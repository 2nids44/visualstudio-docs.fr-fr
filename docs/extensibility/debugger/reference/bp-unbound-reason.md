---
title: BP_UNBOUND_REASON | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- BP_UNBOUND_REASON
helpviewer_keywords:
- BP_UNBOUND_REASON enumeration
ms.assetid: 939b6f9c-113b-471d-9f30-b03871af6285
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 65398ac0c4bde18dc772d75ceea203bdbfe3b189
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31109001"
---
# <a name="bpunboundreason"></a>BP_UNBOUND_REASON
Donne la raison pour laquelle qu'un point d’arrêt a été séparé.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
enum enum_BP_UNBOUND_REASON {   
   BPUR_UNKNOWN           = 0x0000,  
   BPUR_CODE_UNLOADED     = 0x0002,  
   BPUR_BREAKPOINT_REBIND = 0x0003,  
   BPUR_BREAKPOINT_ERROR  = 0x0004  
};  
typedef DWORD BP_UNBOUND_REASON;  
```  
  
```csharp  
public enum enum_BP_UNBOUND_REASON {   
   BPUR_UNKNOWN           = 0x0000,  
   BPUR_CODE_UNLOADED     = 0x0002,  
   BPUR_BREAKPOINT_REBIND = 0x0003,  
   BPUR_BREAKPOINT_ERROR  = 0x0004  
};  
```  
  
## <a name="members"></a>Membres  
 BPUR_UNKNOWN  
 La raison est inconnue.  
  
 BPUR_CODE_UNLOADED  
 Le code qui contient le point d’arrêt a été déchargé.  
  
 BPUR_BREAKPOINT_REBIND  
 Le point d’arrêt a été reliée à un autre emplacement. Cela peut se produire après la modification et poursuivre vos opérations lorsque le point d’arrêt se déplace, ou lorsque le point d’arrêt est lié à un fichier avec un chemin d’accès qui n’est plus valide.  
  
 BPUR_ BREAKPOINT_ERROR  
 Le point d’arrêt est déterminé comme étant dans l’erreur après que qu’il est lié. Cela se produit au point d’arrêt managé dont les conditions ne sont plus valides.  
  
## <a name="remarks"></a>Notes  
 Retourné par la [GetReason](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2-getreason.md) (méthode).  
  
## <a name="requirements"></a>Spécifications  
 En-tête : msdbg.h  
  
 Namespace : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetReason](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2-getreason.md)