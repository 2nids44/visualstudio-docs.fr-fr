---
title: IDebugPortNotify2 | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugPortNotify2
helpviewer_keywords:
- IDebugPortNotify2 interface
ms.assetid: 43278b79-bf16-4c08-bcf1-6f7f7a17feab
caps.latest.revision: 11
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
ms.sourcegitcommit: ca7c86466fa23fb21a932f26dc24e37c71cf29b4
ms.openlocfilehash: de163fdf55052ff4cc2f1599bc8ddfd162d03df3
ms.lasthandoff: 04/05/2017

---
# <a name="idebugportnotify2"></a>IDebugPortNotify2
Cette interface inscrit ou annule l’inscription d’un programme qui peut être débogué avec le port, sur qu'il est en cours d’exécution.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IDebugPortNotify2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notes pour les implémenteurs  
 Un fournisseur de port personnalisé implémente cette interface pour prendre en charge d’ajout et suppression de programmes à partir du port. Il est généralement implémentée sur le même objet qui implémente le [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) interface.  
  
## <a name="notes-for-callers"></a>Remarques pour les appelants  
 Un appel à [QueryInterface](/cpp/atl/queryinterface) sur la `IDebugPort2` interface retourne cette interface. En outre, un appel à [GetPortNotify](../../../extensibility/debugger/reference/idebugdefaultport2-getportnotify.md) retourne cette interface. Un moteur de débogage permettre voir cette interface en tant que paramètre à [WatchForProviderEvents](../../../extensibility/debugger/reference/idebugprogramprovider2-watchforproviderevents.md).  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable  
 Le tableau suivant présente les méthodes de `IDebugPortNotify2`.  
  
|Méthode|Description|  
|------------|-----------------|  
|[AddProgramNode](../../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)|Enregistre un programme qui peut être débogué avec le port, sur qu'il est en cours d’exécution.|  
|[RemoveProgramNode](../../../extensibility/debugger/reference/idebugportnotify2-removeprogramnode.md)|Annule l’inscription d’un programme qui peut être débogué à partir du port, sur qu'il est en cours d’exécution.|  
  
## <a name="remarks"></a>Remarques  
 Sauf si un port de débogage est un moyen de savoir quand les programmes sont chargés ou déchargés, un fournisseur de port personnalisé doit implémenter cette interface. Tous les programmes qui sont chargés pour le débogage via un port particulier sont suivies à l’aide de cette interface.  
  
## <a name="requirements"></a>Spécifications  
 En-tête : msdbg.h  
  
 Namespace : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces de base](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)