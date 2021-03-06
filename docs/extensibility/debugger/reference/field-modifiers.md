---
title: FIELD_MODIFIERS | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- FIELD_MODIFIERS
helpviewer_keywords:
- FIELD_MODIFIERS enumeration
ms.assetid: 1e44681c-1f03-41a9-9c04-b79f231b0822
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 0040795564aa1d1d599a55928b888ec7cfcfd97e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31106774"
---
# <a name="fieldmodifiers"></a>FIELD_MODIFIERS
Spécifie les modificateurs pour un type de champ.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
enum enum_FIELD_MODIFIERS {   
   FIELD_MOD_NONE             = 0x00000000,  
  
   // Modifier of the field  
   FIELD_MOD_ACCESS_NONE      = 0x00000001,  
   FIELD_MOD_ACCESS_PUBLIC    = 0x00000002,  
   FIELD_MOD_ACCESS_PROTECTED = 0x00000004,  
   FIELD_MOD_ACCESS_PRIVATE   = 0x00000008,  
  
   // Storage modifier of the field  
   FIELD_MOD_NOMODIFIERS      = 0x00000010,  
   FIELD_MOD_STATIC           = 0x00000020,  
   FIELD_MOD_CONSTANT         = 0x00000040,  
   FIELD_MOD_TRANSIENT        = 0x00000080,  
   FIELD_MOD_VOLATILE         = 0x00000100,  
   FIELD_MOD_ABSTRACT         = 0x00000200,  
   FIELD_MOD_NATIVE           = 0x00000400,  
   FIELD_MOD_SYNCHRONIZED     = 0x00000800,  
   FIELD_MOD_VIRTUAL          = 0x00001000,  
   FIELD_MOD_INTERFACE        = 0x00002000,  
   FIELD_MOD_FINAL            = 0x00004000,  
   FIELD_MOD_SENTINEL         = 0x00008000,  
   FIELD_MOD_INNERCLASS       = 0x00010000,  
   FIELD_TYPE_OPTIONAL        = 0x00020000,  
   FIELD_MOD_BYREF            = 0x00040000,  
   FIELD_MOD_HIDDEN           = 0x00080000,  
   FIELD_MOD_MARSHALASOBJECT  = 0x00100000,  
   FIELD_MOD_SPECIAL_NAME     = 0x00200000,  
   FIELD_MOD_HIDEBYSIG        = 0x00400000,  
  
   FIELD_MOD_WRITEONLY        = 0x80000000,  
   FIELD_MOD_ACCESS_MASK      = 0x000000ff,  
   FIELD_MOD_MASK             = 0xffffff00,  
   FIELD_MOD_ALL              = 0x7fffffff  
};  
typedef DWORD FIELD_MODIFIERS;  
```  
  
```csharp  
public enum enum_FIELD_MODIFIERS {  
   FIELD_MOD_NONE             = 0x00000000,  
  
   // Modifier of the field  
   FIELD_MOD_ACCESS_NONE      = 0x00000001,  
   FIELD_MOD_ACCESS_PUBLIC    = 0x00000002,  
   FIELD_MOD_ACCESS_PROTECTED = 0x00000004,  
   FIELD_MOD_ACCESS_PRIVATE   = 0x00000008,  
  
   // Storage modifier of the field  
   FIELD_MOD_NOMODIFIERS      = 0x00000010,  
   FIELD_MOD_STATIC           = 0x00000020,  
   FIELD_MOD_CONSTANT         = 0x00000040,  
   FIELD_MOD_TRANSIENT        = 0x00000080,  
   FIELD_MOD_VOLATILE         = 0x00000100,  
   FIELD_MOD_ABSTRACT         = 0x00000200,  
   FIELD_MOD_NATIVE           = 0x00000400,  
   FIELD_MOD_SYNCHRONIZED     = 0x00000800,  
   FIELD_MOD_VIRTUAL          = 0x00001000,  
   FIELD_MOD_INTERFACE        = 0x00002000,  
   FIELD_MOD_FINAL            = 0x00004000,  
   FIELD_MOD_SENTINEL         = 0x00008000,  
   FIELD_MOD_INNERCLASS       = 0x00010000,  
   FIELD_TYPE_OPTIONAL        = 0x00020000,  
   FIELD_MOD_BYREF            = 0x00040000,  
   FIELD_MOD_HIDDEN           = 0x00080000,  
   FIELD_MOD_MARSHALASOBJECT  = 0x00100000,  
   FIELD_MOD_SPECIAL_NAME     = 0x00200000,  
   FIELD_MOD_HIDEBYSIG        = 0x00400000,  
  
   FIELD_MOD_WRITEONLY        = 0x80000000,  
   FIELD_MOD_ACCESS_MASK      = 0x000000ff,  
   FIELD_MOD_MASK             = 0xffffff00,  
   FIELD_MOD_ALL              = 0x7fffffff  
};  
```  
  
## <a name="members"></a>Membres  
 FIELD_MOD_ACCESS_TYPE  
 Indique que le champ ne sont pas accessibles.  
  
 FIELD_MOD_ACCESS_PUBLIC  
 Indique que le champ possède un accès public.  
  
 FIELD_MOD_ACCESS_PROTECTED  
 Indique que le champ possède un accès protégé.  
  
 FIELD_MOD_ACCESS_PRIVATE  
 Indique que le champ possède un accès privé.  
  
 FIELD_MOD_NOMODIFIERS  
 Indique que le champ possède pas de modificateurs.  
  
 FIELD_MOD_STATIC  
 Indique que le champ est statique.  
  
 FIELD_MOD_CONSTANT  
 Indique que le champ est une constante.  
  
 FIELD_MOD_TRANSIENT  
 Indique que le champ est temporaire.  
  
 FIELD_MOD_VOLATILE  
 Indique que le champ est volatile.  
  
 FIELD_MOD_ABSTRACT  
 Indique que le champ est abstrait.  
  
 FIELD_MOD_NATIVE  
 Indique que le champ est natif.  
  
 FIELD_MOD_SYNCHRONIZED  
 Indique que le champ est synchronisé.  
  
 FIELD_MOD_VIRTUAL  
 Indique que le champ est virtuel.  
  
 FIELD_MOD_INTERFACE  
 Indique que le champ est une interface.  
  
 FIELD_MOD_FINAL  
 Indique que le champ est définitive.  
  
 FIELD_MOD_SENTINEL  
 Indique que le champ est sentinelle.  
  
 FIELD_MOD_INNERCLASS  
 Indique que le champ est une classe interne.  
  
 FIELD_TYPE_OPTIONAL  
 Indique que le champ est facultatif.  
  
 FIELD_MOD_BYREF  
 Indique que le champ est un argument de référence. Il s’agit en particulier pour les arguments de méthode.  
  
 FIELD_MOD_HIDDEN  
 Indique que le champ doit être masqué ou présenté dans un autre contexte. par exemple, [!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)] variables locales statiques.  
  
 FIELD_MOD_MARSHALASOBJECT  
 Indique que le champ représente un objet avec un `IUnknown` interface.  
  
 FIELD_MOD_SPECIAL_NAME  
 Indique que le champ a un nom spécial, par exemple, `.ctor` un constructeur ([!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)] uniquement).  
  
 FIELD_MOD_HIDEBYSIG  
 Indique que le champ a le `Overloads` mot clé appliqué ([!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)] uniquement).  
  
 FIELD_MOD_WRITEONLY  
 Indique que le champ est en écriture seule. Cette valeur n’est pas incluse dans `FIELD_MOD_ALL`, comme la seule utilisation de ces champs en écriture seule pour l’évaluation de fonction. Un utilisateur doit demander explicitement `FIELD_MOD_WRITEONLY` champs.  
  
 FIELD_MOD_ACCESS_MASK  
 Indique un masque d’accès au champ.  
  
 FIELD_MOD_MASK  
 Indique un masque pour les modificateurs de champ.  
  
## <a name="remarks"></a>Notes  
 Utilisé pour le `dwModifiers` membre de la [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md) structure.  
  
 Ces valeurs sont également transmis à la [EnumFields](../../../extensibility/debugger/reference/idebugcontainerfield-enumfields.md) méthode pour filtrer les champs spécifiques.  
  
## <a name="requirements"></a>Spécifications  
 En-tête : sh.h  
  
 Namespace : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md)   
 [EnumFields](../../../extensibility/debugger/reference/idebugcontainerfield-enumfields.md)