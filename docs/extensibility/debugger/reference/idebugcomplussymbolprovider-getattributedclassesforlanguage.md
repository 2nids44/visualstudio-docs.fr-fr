---
title: IDebugComPlusSymbolProvider::GetAttributedClassesForLanguage | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- GetAttributedClassesForLanguage
- IDebugComPlusSymbolProvider::GetAttributedClassesForLanguage
ms.assetid: e5b1b8b6-52a6-4ade-9a36-644abfa9f4b2
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 35db32026b122ac070e4216d9820fc7815f9c544
ms.lasthandoff: 02/22/2017

---
# <a name="idebugcomplussymbolprovidergetattributedclassesforlanguage"></a>IDebugComPlusSymbolProvider::GetAttributedClassesForLanguage
Récupère les classes qui sont implémentées dans le langage de programmation spécifié avec l’attribut spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
[C++]  
HRESULT GetAttributedClassesForLanguage (  
   GUID               guidLanguage,  
   LPOLESTR           pstrAttribute,  
   IEnumDebugFields** ppEnum  
);  
```  
  
```  
[C#]  
int GetAttributedClassesForLanguage (  
   Guid                 guidLanguage,  
   string               pstrAttribute,  
   out IEnumDebugFields ppEnum  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `guidLanguage`  
 [in] Identificateur unique de la langue.  
  
 `pstrAttribute`  
 [in] La chaîne d’attribut.  
  
 `ppEnum`  
 [out] Retourne une énumération des classes d’attributs.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment implémenter cette méthode pour un **CDebugSymbolProvider** objet qui expose les [IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md) interface.  
  
```cpp#  
HRESULT CDebugSymbolProvider::GetAttributedClassesForLanguage(  
    GUID guidLanguage,  
    __in_z LPOLESTR pstrAttribute,  
    IEnumDebugFields** ppEnum  
)  
{  
    HRESULT hr = S_OK;  
    CFieldList listFields;  
    CModIter ModIter;  
    CModule* pModule; // the iterator owns the reference  
    ULONG cClasses = 0;  
    DWORD iTypeDef = 0;  
    mdTypeDef* rgTypeDefs = NULL;  
    IDebugField** rgFields = NULL;  
    DWORD ctField = 0;  
    CEnumDebugFields* pEnumFields = NULL;  
  
    ASSERT(IsValidObjectPtr(this, CDebugSymbolProvider));  
    ASSERT(IsValidWritePtr(ppEnum, IEnumDebugFields*));  
  
    METHOD_ENTRY( CDebugSymbolProvider::GetAttributedClassesForLanguage );  
  
    IfFalseGo( ppEnum, E_INVALIDARG );  
    *ppEnum = NULL;  
  
    // For Each Module - call EnumFields  
    IfFailGo( GetModuleIter(&ModIter) );  
  
    // Find the Max number of classes  
    while (ModIter.GetNext(&pModule))  
    {  
        CComPtr<IMetaDataImport> pMetaData;  
        HCORENUM hEnum = 0;  
        ULONG cTypeDefs;  
        ULONG cEnum;  
  
        pModule->GetMetaData( &pMetaData );  
  
        IfFailGo( pMetaData->EnumTypeDefs( &hEnum,  
                                           NULL,  
                                           0,  
                                           &cTypeDefs ) );  
        IfFailGo( pMetaData->CountEnum( hEnum, &cEnum ) );  
        cClasses += cEnum;  
    }  
  
    IfNullGo( rgTypeDefs = new mdTypeDef[cClasses], E_OUTOFMEMORY );  
    IfNullGo( rgFields = new IDebugField * [cClasses], E_OUTOFMEMORY );  
  
    ModIter.Reset();  
  
    // Create the classes  
    while (ModIter.GetNext(&pModule))  
    {  
        CComPtr<IMetaDataImport> pMetaData;  
        HCORENUM hEnum = 0;  
        ULONG cTypeDefs;  
        ULONG cEnum;  
        const void* pUnused;  
        ULONG cbUnused;  
  
        pModule->GetMetaData( &pMetaData );  
  
        IfFailGo( pMetaData->EnumTypeDefs( &hEnum,  
                                           NULL,  
                                           0,  
                                           &cTypeDefs ) );  
        IfFailGo( pMetaData->CountEnum( hEnum, &cEnum ) );  
        IfFailGo( pMetaData->EnumTypeDefs( &hEnum,  
                                           rgTypeDefs,  
                                           cEnum,  
                                           &cTypeDefs ) );  
  
        pMetaData->CloseEnum(hEnum);  
        hEnum = NULL;  
  
        for ( iTypeDef = 0; iTypeDef < cTypeDefs; iTypeDef++)  
        {  
  
            if (pMetaData->GetCustomAttributeByName( rgTypeDefs[iTypeDef],  
                    pstrAttribute,  
                    &pUnused,  
                    &cbUnused ) == S_OK)  
            {  
                // Only return classes implemeted in the correct language  
  
                if (pModule->ClassImplementedInLanguage( rgTypeDefs[iTypeDef],  
                        guidLanguage) )  
                {  
                    if (CreateClassType( pModule->GetID(),  
                                         rgTypeDefs[iTypeDef],  
                                         rgFields + ctField) == S_OK)  
                    {  
                        ctField++;  
                    }  
                    else  
                    {  
                        ASSERT(!"Failed to Create Attributed Class");  
                    }  
                }  
            }  
        }  
    }  
  
    IfNullGo( pEnumFields = new CEnumDebugFields, E_OUTOFMEMORY );  
    IfFailGo( pEnumFields->Initialize(rgFields, ctField) );  
    IfFailGo( pEnumFields->QueryInterface( __uuidof(IEnumDebugFields),  
                                           (void**) ppEnum ) );  
  
Error:  
  
    METHOD_EXIT( CDebugSymbolProvider::GetAttributedClassesForLanguage, hr );  
  
    DELETERG( rgTypeDefs );  
  
    for ( iTypeDef = 0; iTypeDef < ctField; iTypeDef++)  
    {  
        RELEASE( rgFields[iTypeDef] );  
    }  
  
    DELETERG( rgFields );  
    RELEASE( pEnumFields );  
  
    return hr;  
}  
```  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md)