---
title: JsGetUndefinedValue, fonction | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: jsrt/JsGetUndefinedValue
helpviewer_keywords: JsGetUndefinedValue function
ms.assetid: e118eaf6-452c-42f2-86b8-e63c7d987cba
caps.latest.revision: "12"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3c1788f7edeeb6df1ccf7eb3b6918322a65f2db8
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="jsgetundefinedvalue-function"></a>JsGetUndefinedValue, fonction
Obtient la valeur `undefined` dans le contexte de script actuel.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
STDAPI_(JsErrorCode) JsGetUndefinedValue(  
   _Out_ JsValueRef *undefinedValue  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `undefinedValue`  
 Valeur de l'objet `undefined`.  
  
## <a name="return-value"></a>Valeur de retour  
 Le code `JsNoError` si l'opération a réussi, sinon un code d'échec.  
  
## <a name="remarks"></a>Remarques  
 Nécessite un contexte de script actif.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** jsrt.h  
  
## <a name="see-also"></a>Voir aussi  
 [Référence (JavaScript Runtime)](../chakra-hosting/reference-javascript-runtime.md)