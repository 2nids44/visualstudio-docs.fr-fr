---
title: 'CA1001 : Les types qui possèdent des champs supprimables doivent être supprimables'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1001
- TypesThatOwnDisposableFieldsShouldBeDisposable
helpviewer_keywords:
- CA1001
- TypesThatOwnDisposableFieldsShouldBeDisposable
ms.assetid: c85c126c-2b16-4505-940a-b5ddf873fb22
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d14fe8bcf21b3ad55b8a1e80591caff60f14f7d2
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
ms.locfileid: "31898809"
---
# <a name="ca1001-types-that-own-disposable-fields-should-be-disposable"></a>CA1001 : Les types qui possèdent des champs supprimables doivent être supprimables
|||
|-|-|
|TypeName|TypesThatOwnDisposableFieldsShouldBeDisposable|
|CheckId|CA1001|
|Category|Microsoft.Design|
|Modification avec rupture|Sans rupture - Si le type n’est pas visible à l’extérieur de l’assembly.<br /><br /> Avec rupture - Si le type est visible à l’extérieur de l’assembly.|

## <a name="cause"></a>Cause
 Une classe déclare et implémente un champ d’instance qui est un <xref:System.IDisposable?displayProperty=fullName> type et la classe n’implémente pas <xref:System.IDisposable>.

## <a name="rule-description"></a>Description de la règle
 Une classe qui implémente le <xref:System.IDisposable> interface à libérer des ressources non managées qu’il détient. Un champ d’instance qui est un <xref:System.IDisposable> type indique que le champ possède une ressource non managée. Une classe qui déclare un <xref:System.IDisposable> champ indirectement possède une ressource non managée et doit implémenter la <xref:System.IDisposable> interface. Si la classe ne possède pas directement les ressources non managées, il ne doit pas implémenter un finaliseur.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, implémentez <xref:System.IDisposable> et à partir de la <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> appel de méthode le <xref:System.IDisposable.Dispose%2A> méthode du champ.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Ne supprimez aucun avertissement de cette règle.

## <a name="example"></a>Exemple
 L’exemple suivant montre une classe qui enfreint la règle et une classe qui satisfait la règle en implémentant <xref:System.IDisposable>. La classe n’implémente pas de finaliseur, car la classe ne possède pas directement les ressources non managées.

 [!code-vb[FxCop.Design.DisposableFields#1](../code-quality/codesnippet/VisualBasic/ca1001-types-that-own-disposable-fields-should-be-disposable_1.vb)]
 [!code-csharp[FxCop.Design.DisposableFields#1](../code-quality/codesnippet/CSharp/ca1001-types-that-own-disposable-fields-should-be-disposable_1.cs)]

## <a name="related-rules"></a>Règles associées
 [CA2213 : Les champs pouvant être supprimés doivent l’être](../code-quality/ca2213-disposable-fields-should-be-disposed.md)

 [CA2216 : Les types supprimables doivent déclarer un finaliseur](../code-quality/ca2216-disposable-types-should-declare-finalizer.md)

 [CA2215 : Les méthodes Dispose doivent appeler la méthode Dispose de la classe de base](../code-quality/ca2215-dispose-methods-should-call-base-class-dispose.md)

 [CA1049 : Les types qui ont des ressources natives doivent être supprimables](../code-quality/ca1049-types-that-own-native-resources-should-be-disposable.md)