---
title: Propriétés dynamiques LINQ to XML
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: 0455f47c-4a68-4f2e-a3f8-dd1d85b99012
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: abad2e8966bfc9fc2926c1ca985e1cb5450f1d68
ms.sourcegitcommit: e5a382de633156b85b292f35e3d740f817715d47
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/12/2018
ms.locfileid: "38978136"
---
# <a name="linq-to-xml-dynamic-properties"></a>Propriétés dynamiques LINQ to XML

Cette section fournit des informations de référence sur les propriétés dynamiques dans LINQ to XML. Plus spécifiquement, ces propriétés sont exposées par les classes <xref:System.Xml.Linq.XAttribute> et <xref:System.Xml.Linq.XElement>, qui sont dans l'espace de noms <xref:System.Xml.Linq>.

Comme expliqué dans la rubrique [Vue d’ensemble de la liaison de données WPF avec LINQ to XML](../designers/wpf-data-binding-with-linq-to-xml-overview.md), chacune des propriétés dynamiques est équivalente à une méthode ou propriété publique standard dans la même classe. Ces membres standard doivent être utilisés dans la plupart des cas ; des propriétés dynamiques sont fournies spécifiquement pour les scénarios de liaison de données LINQ to XML. Pour plus d'informations sur les membres standard de ces classes, consultez les rubriques de référence <xref:System.Xml.Linq.XAttribute> et <xref:System.Xml.Linq.XElement>.

En ce qui concerne leurs valeurs résolues, les propriétés dynamiques dans cette section se répartissent en deux catégories :

- Les propriétés simples, telles que les propriétés `Value` dans les classes <xref:System.Xml.Linq.XAttribute> et <xref:System.Xml.Linq.XElement>, qui sont résolues à une valeur unique.

- Les valeurs indexées, telles que les propriétés [Elements](../designers/elements-xelement-dynamic-property.md) et [Descendants](../designers/descendants-xelement-dynamic-property.md) de l’objet <xref:System.Xml.Linq.XElement>, qui sont résolues en un type d’indexeur. Pour que les types d’indexeur soient résolus à la valeur ou collection souhaitée, un paramètre de nom développé doit leur être passé.

Toutes les propriétés dynamiques qui retournent une valeur indexée de type <xref:System.Collections.Generic.IEnumerable%601> utilisent l’exécution différée. Pour plus d’informations sur l’exécution différée, consultez [Introduction aux requêtes LINQ (C#)](/dotnet/csharp/programming-guide/concepts/linq/introduction-to-linq-queries).

## <a name="reference"></a>Référence

- <xref:System.Xml.Linq>
- <xref:System.Xml.Linq.XElement?displayProperty=fullName>
- <xref:System.Xml.Linq.XAttribute?displayProperty=fullName>

## <a name="see-also"></a>Voir aussi

- [Liaison de données WPF avec LINQ to XML](../designers/wpf-data-binding-with-linq-to-xml-overview.md)
- [Vue d’ensemble de la liaison de données WPF avec LINQ to XML](../designers/wpf-data-binding-with-linq-to-xml-overview.md)
- [Introduction aux requêtes LINQ (C#)](/dotnet/csharp/programming-guide/concepts/linq/introduction-to-linq-queries)
