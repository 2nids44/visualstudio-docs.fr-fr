---
title: Contexte d’évaluation | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation, context
ms.assetid: 008a20c7-1b27-4013-bf96-d6a3f510da02
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 523ef45d52a81a475eca0e3560243e0eb8357bbd
ms.sourcegitcommit: 25a62c2db771f938e3baa658df8b1ae54a960e4f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2018
ms.locfileid: "39232453"
---
# <a name="evaluation-context"></a>Contexte d'évaluation
> [!IMPORTANT]
>  Dans Visual Studio 2015, ce moyen d’implémenter des évaluateurs d’expression est déconseillée. Pour plus d’informations sur l’implémentation des évaluateurs d’expression CLR, consultez [évaluateurs d’expression CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) et [exemple d’évaluateur d’expression managé](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Lorsque le moteur de débogage (dé) appelle l’évaluateur d’expression (EE), trois arguments sont passés à [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) déterminer le contexte pour rechercher et évaluer des symboles, comme indiqué dans le tableau suivant.  
  
## <a name="arguments"></a>Arguments  
  
|Argument|Description|  
|--------------|-----------------|  
|`pSymbolProvider`|Un [IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md) interface qui spécifie le Gestionnaire de symboles (es) à utiliser pour identifier le symbole.|  
|`pAddress`|Un [IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md) interface qui spécifie le point en cours d’exécution. Cette interface recherche la méthode qui contient le code en cours d’exécution.|  
|`pBinder`|Un [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md) interface qui recherche la valeur et le type d’un symbole de fonction de son nom.|  
  
 `IDebugParsedExpression::EvaluateSync` Retourne un [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) interface qui représente la valeur résultante et son type.  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces de d’évaluateur d’expression clé](../../extensibility/debugger/key-expression-evaluator-interfaces.md)   
 [Affichage des variables locales](../../extensibility/debugger/displaying-locals.md)   
 [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)   
 [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md)   
 [IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md)   
 [IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md)   
 [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md)