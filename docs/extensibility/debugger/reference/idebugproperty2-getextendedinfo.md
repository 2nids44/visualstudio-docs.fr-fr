---
title: IDebugProperty2::GetExtendedInfo | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugProperty2::GetExtendedInfo
helpviewer_keywords:
- IDebugProperty2::GetExtendedInfo
ms.assetid: 0c9c0b2b-7540-4424-adb5-fce7aa37a026
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: e6865361ac0b518f4fa78a3521973d756e6ab780
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31119346"
---
# <a name="idebugproperty2getextendedinfo"></a>IDebugProperty2::GetExtendedInfo
Obtient les informations étendues pour la propriété.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetExtendedInfo (   
   REFGUID* guidExtendedInfo,  
   VARIANT* pExtendedInfo  
);  
```  
  
```csharp  
int GetExtendedInfo (   
   ref Guid guidExtendedInfo,  
   out object pExtendedInfo  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `guidExtendedInfo`  
 [in] GUID qui détermine le type d’informations étendues à récupérer. Pour plus d’informations, consultez la section Notes.  
  
 `pExtendedInfo`  
 [out] Retourne un `VARIANT` (C++) ou un objet (c#) qui peut être utilisé pour récupérer les informations de propriété étendue. Par exemple, ce paramètre peut retourner un `IUnknown` interface qui peut être interrogé pour une [IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md) interface. Pour plus d’informations, consultez la section Notes.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon retourne le code d’erreur. Retourne `S_GETEXTENDEDINFO_NO_EXTENDEDINFO` s’il n’existe aucune informations étendues à récupérer.  
  
## <a name="remarks"></a>Notes  
 Cette méthode existe à des fins de récupération des informations qui ne se prêtent pas à être récupéré en appelant le [GetPropertyInfo](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) (méthode).  
  
 Les GUID suivants sont généralement reconnus par cette méthode (les valeurs GUID sont spécifiés pour c#, car le nom n’est pas disponible dans n’importe quel assembly). GUID supplémentaires peut être créés pour un usage interne.  
  
|Name|GUID|Description|  
|----------|----------|-----------------|  
|guidDocument|{3f98de84-fee9-11d0-b47f-00a0244a1dd2}|Retourne un `IUnknown` interface au document. En règle générale, les [IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md) interface peut être obtenue à partir de ce `IUnknown` interface.|  
|guidCodeContext|{1-b528-00aax004a8797 e2fc65e 56ce - 11d}|Retourne un `IUnknown` interface pour le contexte de document. En règle générale, les [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) interface peut être obtenue à partir de ce `IUnknown` interface.|  
|guidCustomViewerSupported|{d9c9da31-ffbe-4eeb-9186-23121e3c088c}|Retourne une chaîne contenant le CLSID d’une visionneuse personnalisée, généralement implémentée par un évaluateur d’expression.|  
|guidExtendedInfoSlot|{6df235ad-82c6-4292-9c97-7389770bc42f}|Retourne un nombre 32 bits qui représente le numéro d’emplacement souhaité si cette propriété représente une adresse locale du code managé.|  
|guidExtendedInfoSignature|{b5fb6d46-f805-417f-96a3-8ba737073ffd}|Retourne une chaîne contenant la signature de la variable associée à l’objet de propriété.|  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md)   
 [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)