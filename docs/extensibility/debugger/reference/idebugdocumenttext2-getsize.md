---
title: IDebugDocumentText2::GetSize | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugDocumentText2::GetSize
helpviewer_keywords:
- IDebugDocumentText2::GetSize
ms.assetid: bf515a8f-dcee-4004-8f81-543d547ceaae
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: fe37c7157f96a905e52fb6656d5ebb8ff6f4971a
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31105617"
---
# <a name="idebugdocumenttext2getsize"></a>IDebugDocumentText2::GetSize
Récupère la taille du texte à cette position dans le document.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetSize(   
   ULONG* pcNumLines,  
   ULONG* pcNumChars  
);  
```  
  
```csharp  
int GetSize(   
   ref uint pcNumLines,  
   ref uint pcNumChars  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pcNumLines`  
 [out] Retourne le nombre de lignes de texte.  
  
 `pcNumChars`  
 [out] Retourne le nombre de caractères du texte.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="remarks"></a>Notes  
 (C++ uniquement) Si une valeur particulière n’est pas souhaitée, passez une valeur NULL pour le paramètre.  
  
 (C# uniquement) Les deux paramètres doivent être spécifiés.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md)