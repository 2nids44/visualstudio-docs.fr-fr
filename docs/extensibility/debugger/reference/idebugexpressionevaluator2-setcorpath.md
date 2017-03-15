---
title: "IDebugExpressionEvaluator2::SetCorPath | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "SetCorPath"
  - "IDebugExpressionEvaluator2::SetCorPath"
ms.assetid: 27b614ff-7325-4f9b-8da4-61ee020c9410
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugExpressionEvaluator2::SetCorPath
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Définit le chemin d'accès au common \(CLR\) langage runtime chargé dans le débogueur.  
  
## Syntaxe  
  
```cpp#  
HRESULT SetCorPath(  
   LPCOLESTR pcstrCorPath  
);  
```  
  
```c#  
int SetCorPath(  
   string pcstrCorPath  
);  
```  
  
#### Paramètres  
 `pcstrCorPath`  
 \[in\]  Le chemin d'accès au CLR chargé dans le débogueur.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
## Exemple  
 L'exemple suivant indique comment appliquer cette méthode d'un objet **d'ExpressionEvaluatorPackage** qui expose l'interface d' [IDebugExpressionEvaluator2](../../../extensibility/debugger/reference/idebugexpressionevaluator2.md) .  
  
```cpp#  
STDMETHODIMP ExpressionEvaluatorPackage::SetCorPath(LPCOLESTR pcstrCorPath)  
{  
    VerifyInPtr(pcstrCorPath);  
    HRESULT hr = E_FAIL;  
  
    VBEECompilerSingleton *pVBEECompilerSingleton = VBEECompilerSingleton::Instance();  
  
    if (pVBEECompilerSingleton)  
    {  
        pVBEECompilerSingleton->LockEECompiler();  
  
        try  
        {  
            if (!m_pCompiler->FindEECompilerHost(pcstrCorPath, &m_pCompilerHost))  
            {  
                CComObject<CVBEECompilerHost> *pEECompilerHost;  
  
                if (SUCCEEDED(CComObject<CVBEECompilerHost>::CreateInstance(&pEECompilerHost)))  
                {  
                    pEECompilerHost->AddRef();  
                    pEECompilerHost->Init(pcstrCorPath);  
  
                    CComPtr<IVbCompilerHost> srpVBHost;  
                    HRESULT hr2 = pEECompilerHost->QueryInterface(IID_IVbCompilerHost, (void **)&srpVBHost);  
  
                    pEECompilerHost->Release();  
  
                    if (SUCCEEDED(hr2))  
                    {  
                        m_pCompiler->RegisterEECompilerHost(srpVBHost);  
                    }  
                }  
            }  
            else  
            {  
                hr = S_OK;  
            }  
  
            if (m_pCompiler->FindEECompilerHost(pcstrCorPath, &m_pCompilerHost))  
            {  
                ULONG cErrors = 0;  
                ULONG cWarnings = 0;  
  
                m_pCompiler->CompileToBound(m_pCompilerHost, &cErrors, &cWarnings, NULL);  
  
                // This needs to happen after bound  
                if (m_pCompilerHost->GetVbLibraryType() == TLB_AutoDetect)  
                {  
                    m_pCompilerHost->AutoSetVbLibraryType();  
                }  
  
                VSASSERT(m_pCompiler && m_pCompilerHost && m_pCompilerHost->GetIntrinsicSymbol(t_i4) != NULL, "Invalid state");  
  
                if (cErrors + cWarnings > 0)  
                {  
                    VSFAIL("Errors from mscorlib.dll and vb runtime!");                 
                    __leave;  
                }  
  
                hr = S_OK;  
            }  
            else  
            {  
                VSFAIL("FindCompilerHost shouldn't have failed!");  
            }  
        }  
        catch_hresult;  
  
        VSASSERT(m_pCompilerHost->GetComPlusProject()->GetCompState() >= CS_Bound, "Debugger mscorlib not in bound state");  
  
        pVBEECompilerSingleton->UnlockEECompiler();  
    }  
  
    return hr;  
}  
```  
  
## Voir aussi  
 [IDebugExpressionEvaluator2](../../../extensibility/debugger/reference/idebugexpressionevaluator2.md)