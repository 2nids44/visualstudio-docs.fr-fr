---
title: CONTEXT_COMPARE | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- CONTEXT_COMPARE
helpviewer_keywords:
- CONTEXT_COMPARE enumeration
ms.assetid: 701ed61c-a320-4c20-a335-0b840024abc0
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 0563f037f77c18cc5e686c1ea6acf429c91ad06d
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31108581"
---
# <a name="contextcompare"></a>CONTEXT_COMPARE
Spécifie les critères pour la comparaison de deux contextes de mémoire.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
enum enum_CONTEXT_COMPARE {   
   CONTEXT_EQUAL                 = 0x0001,  
   CONTEXT_LESS_THAN             = 0x0002,  
   CONTEXT_GREATER_THAN          = 0x0003,  
   CONTEXT_LESS_THAN_OR_EQUAL    = 0x0004,  
   CONTEXT_GREATER_THAN_OR_EQUAL = 0x0005,  
   CONTEXT_SAME_SCOPE            = 0x0006,  
   CONTEXT_SAME_FUNCTION         = 0x0007,  
   CONTEXT_SAME_MODULE           = 0x0008,  
   CONTEXT_SAME_PROCESS          = 0x0009  
};  
typedef DWORD CONTEXT_COMPARE;  
```  
  
```csharp  
public enum enum_CONTEXT_COMPARE {   
   CONTEXT_EQUAL                 = 0x0001,  
   CONTEXT_LESS_THAN             = 0x0002,  
   CONTEXT_GREATER_THAN          = 0x0003,  
   CONTEXT_LESS_THAN_OR_EQUAL    = 0x0004,  
   CONTEXT_GREATER_THAN_OR_EQUAL = 0x0005,  
   CONTEXT_SAME_SCOPE            = 0x0006,  
   CONTEXT_SAME_FUNCTION         = 0x0007,  
   CONTEXT_SAME_MODULE           = 0x0008,  
   CONTEXT_SAME_PROCESS          = 0x0009  
};  
```  
  
## <a name="members"></a>Membres  
 CONTEXT_EQUAL  
 Recherche le premier contexte de la mémoire dans la liste qui est égale au contexte cible de mémoire.  
  
 CONTEXT_LESS_THAN  
 Recherche le premier contexte de la mémoire dans la liste qui est inférieur au contexte de la mémoire cible.  
  
 CONTEXT_GREATER_THAN  
 Recherche le premier contexte de la mémoire dans la liste supérieure dans le contexte de la mémoire cible.  
  
 CONTEXT_LESS_THAN_OR_EQUAL  
 Recherche le premier contexte de la mémoire dans la liste qui est inférieur ou égal au contexte cible de mémoire.  
  
 CONTEXT_GREATER_THAN_OR_EQUAL  
 Recherche le premier contexte de la mémoire dans la liste qui est supérieur ou égal au contexte de la mémoire cible.  
  
 CONTEXT_SAME_SCOPE  
 Recherche le premier contexte de la mémoire dans la liste qui se trouve dans la même étendue que le contexte de la mémoire cible.  
  
 CONTEXT_SAME_FUNCTION  
 Recherche le premier contexte de la mémoire dans la liste qui se trouve dans la même fonction que l’étendue de la mémoire cible.  
  
 CONTEXT_SAME_MODULE  
 Recherche le premier contexte de la mémoire dans la liste qui se trouve dans le même module que le contexte de la mémoire cible.  
  
 CONTEXT_SAME_PROCESS  
 Recherche le premier contexte de la mémoire dans la liste qui se trouve dans le même processus que le contexte de la mémoire cible.  
  
## <a name="remarks"></a>Notes  
 Est passé comme argument à la [comparer](../../../extensibility/debugger/reference/idebugmemorycontext2-compare.md) (méthode).  
  
 Ces valeurs sont utilisées pour rechercher le premier contexte de la mémoire dans une liste qui satisfait aux critères de comparaison spécifiés. Un contexte de la mémoire reçoit une liste de contextes de mémoire à comparer lui-même, par rapport à la `IDebugMemoryContext2::Compare` (méthode). Le premier contexte de la mémoire dans la liste pour laquelle l’opérateur de comparaison est `true` est alors retournée.  
  
## <a name="requirements"></a>Spécifications  
 En-tête : msdbg.h  
  
 Namespace : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [Compare](../../../extensibility/debugger/reference/idebugmemorycontext2-compare.md)