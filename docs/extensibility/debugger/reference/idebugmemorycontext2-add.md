---
title: IDebugMemoryContext2::Add | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugMemoryContext2::Add
helpviewer_keywords:
- IDebugMemoryContext2::Add method
- Add method
ms.assetid: 3c47e646-ce9e-4dd3-8f1a-6dbd3827d407
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ad55b81c1c4126efd69779e929521cfb94235ccc
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31111932"
---
# <a name="idebugmemorycontext2add"></a>IDebugMemoryContext2::Add
Ajoute la valeur spécifiée pour le contexte actuel et retourne un nouveau contexte.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT Add(   
   UINT64                 dwCount,  
   IDebugMemoryContext2** ppMemCxt  
);  
```  
  
```csharp  
int Add(  
   ulong                    dwCount,   
   out IDebugMemoryContext2 ppMemCxt  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `dwCount`  
 [in] Valeur à ajouter au contexte actuel.  
  
 `ppMemCxt`  
 [out] Retourne un nouveau [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) objet.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="remarks"></a>Notes  
 Un contexte de la mémoire est une adresse, afin de l’ajout d’une valeur à une adresse génère une nouvelle adresse qui requiert une nouvelle interface de contexte.  
  
 Cette méthode doit produire toujours d’un nouveau contexte, même si l’adresse obtenue est en dehors de l’espace de mémoire associé à ce contexte. La seule exception est si aucune mémoire ne pouvant être allouée pour le nouveau contexte ou si `ppMemCxt` est une valeur null (qui est une erreur).  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)