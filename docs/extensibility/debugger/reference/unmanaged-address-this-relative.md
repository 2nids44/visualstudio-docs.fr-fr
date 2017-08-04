---
title: UNMANAGED_ADDRESS_THIS_RELATIVE | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- UNMANAGED_ADDRESS_THIS_RELATIVE
helpviewer_keywords:
- UNMANAGED_ADDRESS_THIS_RELATIVE structure
ms.assetid: e6a91ace-2d47-4ff9-aefb-8d8b68eab0b2
caps.latest.revision: 6
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
ms.openlocfilehash: b5b889a5901883e6dfe2f27723d5fd7a0085d1d5
ms.lasthandoff: 02/22/2017

---
# <a name="unmanagedaddressthisrelative"></a>UNMANAGED_ADDRESS_THIS_RELATIVE
Cette structure représente une adresse qui est relatif à un `this` pointeur (`Me` en Visual Basic).  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef struct _tagUNMANAGED_THIS_RELATIVE {  
   DWORD dwOffset;  
   DWORD dwBitOffset;  
   DWORD dwBitLength;  
} UNMANAGED_ADDRESS_THIS_RELATIVE;  
```  
  
```c#  
public struct UNMANAGED_THIS_RELATIVE {  
   public uint dwOffset;  
   public uint dwBitOffset;  
   public uint dwBitLength;  
}  
```  
  
## <a name="terms"></a>Termes  
 dwOffset  
 Octets de décalage à partir d’une position de base (par exemple, le début d’un vtable de la classe).  
  
 dwBitOffset  
 Décalage de bits d’une position de base (toujours 0, sauf si la référence à un champ de bits).  
  
 dwBitLength  
 Nombre de bits qui représente l’adresse (toujours 0, sauf si la référence à un champ de bits).  
  
## <a name="remarks"></a>Notes  
 Cette structure fait partie de l’union dans la [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md) lorsque la structure le `dwKind` champ la `DEBUG_ADDRESS_UNION` structure est définie sur `ADDRESS_KIND_UNMANAGED_THIS_RELATIVE` (une valeur à partir de la [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md) énumération).  
  
## <a name="requirements"></a>Spécifications  
 En-tête : sh.h  
  
 Namespace : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Structures et Unions](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md)