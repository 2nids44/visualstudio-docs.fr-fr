---
title: Référence des API (débogage de Visual Studio) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], API reference
ms.assetid: e4e429da-3667-41f7-9158-a8207d13e91a
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 3c9007d679e36e2aa6dbab41074338395434be42
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31103238"
---
# <a name="api-reference-visual-studio-debugging"></a>Référence des API (débogage de Visual Studio)
La section de référence inclut une vue d’ensemble conceptuelle de l’API, un guide qui montre la syntaxe et l’utilisation pour tous les éléments d’API et un assortiment d’exemples de code. Toutes les références sont répertoriées par ordre alphabétique par catégorie.  
  
 Le tableau suivant présente le common `HRESULT` valeurs retournées par les méthodes.  
  
|Name|Description|Value|  
|----------|-----------------|-----------|  
|S_OK|Opération réussie.|0x00000000|  
|E_UNEXPECTED|Erreur inattendue.|0x8000ffff|  
|E_NOTIMPL|Non implémenté.|0 x 80004001|  
|E_OUTOFMEMORY|Mémoire insuffisante pour terminer l’opération.|0x8007000E|  
|E_INVALIDARG|Un ou plusieurs arguments ne sont pas valide.|0 x 80070057|  
|E_NOINTERFACE|Interface non pris en charge.|0 x 80004002|  
|E_POINTER|Pointeur non valide.|0 x 80004003|  
|E_HANDLE|Handle non valide.|0x80070006|  
|E_ABORT|Opération abandonnée.|0x80004004|  
|E_FAIL|Erreur inattendue.|0 x 80004005|  
|E_ACCESSDENIED|Erreur accès général refusé.|0 x 80070005|  
  
> [!NOTE]
>  Lorsqu’un [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] déboguer la méthode retourne `S_OK`, il est supposé que toutes les pointeurs de paramètre sont valides, autrement dit, aucune validation n’est effectuée sur les pointeurs de paramètre lorsque `S_OK` est retourné.  
  
> [!NOTE]
>  Non valide ou `NULL` [paramètres out] peut entraîner l’IDE à se bloquer.  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces](../../../extensibility/debugger/reference/interfaces-visual-studio-debugging.md)   
 [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [Structures et Unions](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [Programmes d’assistance du Kit de développement logiciel pour le débogage](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)   
 [Extensibilité du débogueur de Visual Studio](../../../extensibility/debugger/visual-studio-debugger-extensibility.md)