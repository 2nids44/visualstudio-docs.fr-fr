---
title: marker_series::is_enabled, méthode | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- cvmarkersobj/Concurrency::diagnostic::marker_series::is_enabled
helpviewer_keywords:
- Concurrency::diagnostic::marker_series::is_enabled method
ms.assetid: 8ce4dd50-ca29-4c72-98d6-582693f7d501
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0d7889fc8b02bcaa09ca1fb33efbd84e524695c0
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/19/2018
---
# <a name="markerseriesisenabled-method"></a>marker_series::is_enabled, méthode
Détermine si une session a activé le fournisseur.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
bool is_enabled();  
bool is_enabled(  
   marker_importance _Importance,  
   int _Category  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `_Importance`  
 Niveau d’importance.  
  
 `_Category`  
 Catégorie.  
  
## <a name="return-value"></a>Valeur de retour  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête** : cvmarkersobj.h  
  
 **Espace de noms** : Concurrency::diagnostic  
  
## <a name="see-also"></a>Voir aussi  
 [marker_series, classe](../profiling/marker-series-class.md)