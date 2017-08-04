---
title: "Vue d’ensemble de la liaison de données WPF avec LINQ to XML | Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3bf80845-891b-41de-a71b-4080b5bd3ea6
caps.latest.revision: 3
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
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
translationtype: Human Translation
ms.sourcegitcommit: 5658ecf52637a38bc3c2a5ad9e85b2edebf7d445
ms.openlocfilehash: 5a16c3321222c57f68409e4c2c414cb73e24f258
ms.lasthandoff: 02/22/2017

---
# <a name="wpf-data-binding-with-linq-to-xml-overview"></a>Vue d’ensemble de la liaison de données WPF avec LINQ to XML
Cette rubrique présente les fonctionnalités de liaison de données dynamiques dans l’espace de noms <xref:System.Xml.Linq>. Ces fonctionnalités peuvent être utilisées en tant que source de données pour des éléments d’interface utilisateur dans Windows Presentation Foundation (WPF).  
  
## <a name="xaml-and-linq-to-xml"></a>XAML et LINQ to XML  
 XAML (Extensible Application Markup Language) est un dialecte XML créé par Microsoft pour prendre en charge les technologies .NET Framework 3.0. Il est utilisé dans WPF pour représenter des éléments d’interface et fonctionnalités connexes, tels que des événements et des liaisons de données. Dans Windows Workflow Foundation, XAML est utilisé pour représenter la structure de programme, telle que le contrôle de programme (*flux de travail*). XAML permet de séparer les aspects déclaratifs d'une technologie des procédures de code connexes qui définissent le comportement plus individualisé d'un programme.  
  
 D'une manière générale, XAML et LINQ to XML peuvent interagir de deux façons :  
  
-   Les fichiers XAML étant constitués de code XML correct, ils peuvent être interrogés et manipulés par le biais de technologies XML telles que LINQ to XML.  
  
-   Étant donné que les requête LINQ to XML représentent une source de données, elles peuvent être utilisées en tant que source de données pour la liaison de données pour des éléments d'interface utilisateur WPF.  
  
 Cette documentation décrit le deuxième scénario.  
  
## <a name="data-binding-in-the-windows-presentation-foundation"></a>Liaison de données dans Windows Presentation Foundation  
 La liaison de données WPF permet à un élément d’interface utilisateur d’associer l’une de ses propriétés à une source de données. Un exemple simple est un objet <xref:System.Windows.Controls.Label> dont le texte présente la valeur d’une propriété publique dans un objet défini par l’utilisateur. La liaison de données WPF s’appuie sur les composants suivants :  
  
|Composant|Description|  
|---------------|-----------------|  
|Cible de liaison|Élément d'interface utilisateur à associer à la source de données. Les éléments visuels dans WPF sont dérivés de la classe <xref:System.Windows.UIElement>.|  
|Propriété cible|*Propriété de dépendance* de la cible de liaison qui reflète la valeur de la source de liaison de données. Les propriétés de dépendance sont directement prises en charge par la classe <xref:System.Windows.DependencyObject>, de laquelle <xref:System.Windows.UIElement> dérive.|  
|Source de liaison|Objet source pour une ou plusieurs valeurs qui sont fournies à l'élément d'interface utilisateur pour la présentation. WPF prend automatiquement en charge les types suivants comme sources de liaison : objets CLR, objets de données ADO.NET, données XML (à partir de requêtes XPath ou LINQ to XML) ou un autre <xref:System.Windows.DependencyObject>.|  
|Chemin d’accès à la source|Propriété de la source de liaison qui est résolue à la valeur ou à l'ensemble de valeurs qui doit être lié(e).|  
  
 Une propriété de dépendance est un concept spécifique à WPF qui représente une propriété calculée de manière dynamique d'un élément d'interface utilisateur. Par exemple, les propriétés de dépendance ont souvent des valeurs par défaut ou des valeurs fournies par un élément parent. Ces propriétés spéciales sont secondées par des instances de la classe <xref:System.Windows.DependencyProperty> (et non par des champs, comme avec les propriétés standard). Pour plus d’informations, consultez [Vue d’ensemble des propriétés de dépendance](http://msdn.microsoft.com/Library/d119d00c-3afb-48d6-87a0-c4da4f83dee5).  
  
### <a name="dynamic-data-binding-in-wpf"></a>Liaison de données dynamiques dans WPF  
 Par défaut, la liaison de données se produit uniquement lorsque l’élément d’interface utilisateur cible est initialisé. Cela porte le nom de liaison *ponctuelle*. Ce type de liaison convient dans la plupart des cas ; en général, une solution de liaison de données exige que les modifications soient propagées de manière dynamique au moment de l’exécution de l’une des façons suivantes :  
  
-   La liaison *unidirectionnelle* fait en sorte que les modifications apportées à une extrémité soient propagées automatiquement. Le plus souvent, les modifications apportées à la source sont reflétées dans la cible, mais l'inverse peut parfois être utile.  
  
-   Dans une liaison *bidirectionnelle*, les modifications apportées à la source sont propagées automatiquement à la cible et les modifications apportées à la cible sont propagées automatiquement à la source.  
  
 Pour que la liaison unidirectionnelle ou bidirectionnelle ait lieu, la source doit implémenter un mécanisme de notification de changement, par exemple en implémentant l’interface <xref:System.ComponentModel.INotifyPropertyChanged> ou en utilisant un modèle *PropertyNameChanged* pour chaque propriété prise en charge.  
  
 Pour plus d’informations sur la liaison de données dans WPF, consultez [Liaison de données (WPF)](http://msdn.microsoft.com/Library/90f79b97-17e7-40d1-abf0-3ba600ad1d7e).  
  
## <a name="dynamic-properties-in-linq-to-xml-classes"></a>Propriétés dynamiques dans les classes LINQ to XML   
 La plupart des classes LINQ to XML ne constituent pas de réelles sources de données dynamiques WPF ; certaines des informations les plus utiles sont accessibles uniquement par le biais de méthodes (et non de propriétés) et les propriétés dans ces classes n'implémentent pas les notifications de changement. Pour prendre en charge la liaison de données WPF, LINQ to XML expose un ensemble de *propriétés dynamiques*.  
  
 Ces propriétés dynamiques sont des propriétés d’exécution spéciales qui dupliquent la fonctionnalité de méthodes et de propriétés existantes dans les classes <xref:System.Xml.Linq.XAttribute> et <xref:System.Xml.Linq.XElement>. Elles ont été ajoutées à ces classes uniquement afin de leur permettre d'assumer la fonction de sources de données dynamiques pour WPF. Pour répondre à ce besoin, toutes ces propriétés dynamiques implémentent les notifications de changement. Une référence détaillée pour ces propriétés dynamiques est fournie dans la section suivante, [Propriétés dynamiques LINQ to XML](../designers/linq-to-xml-dynamic-properties.md).  
  
> [!NOTE]
>  Une grande partie des propriétés publiques standard, qui se trouvent dans les différentes classes dans l’espace de noms <xref:System.Xml.Linq>, peuvent être utilisées pour la liaison de données ponctuelle. Cependant, n'oubliez pas que ni la source ni la cible ne seront mises à jour de manière dynamique en vertu de ce schéma.  
  
### <a name="accessing-dynamic-properties"></a>Accès aux propriétés dynamiques  
 Les propriétés dynamiques dans les classes <xref:System.Xml.Linq.XAttribute> et <xref:System.Xml.Linq.XElement> ne sont pas accessibles comme des propriétés standard. Par exemple, dans des langages compatibles avec le CLR tels que C#, elles ne peuvent pas être :  
  
-   accédées directement au moment de la compilation. Les propriétés dynamiques sont invisibles pour le compilateur et pour Visual Studio IntelliSense.  
  
-   découvertes ou accédées au moment de l'exécution à l'aide de la réflexion .NET. Même au moment de l'exécution, il ne s'agit pas de propriétés dans le sens CLR fondamental.  
  
 En langage C#, les propriétés dynamiques sont accessibles uniquement au moment de l’exécution par le biais de fonctionnalités fournies par l’espace de noms <xref:System.ComponentModel>.  
  
 En revanche, dans une source XML les propriétés dynamiques sont accessibles par le biais d'une notation simple de la forme suivante :  
  
```  
<object>.<dynamic-property>  
```  
  
 Les propriétés dynamiques pour ces deux classes sont résolues à une valeur qui peut être utilisée directement ou à un indexeur qui doit être fourni avec un index pour obtenir la valeur ou la collection de valeurs résultante. Cette dernière syntaxe prend la forme suivante :  
  
```  
<object>.<dynamic-property>[<index-value>]  
```  
  
 Pour plus d’informations, consultez [Propriétés dynamiques LINQ to XML](../designers/linq-to-xml-dynamic-properties.md).  
  
 Pour implémenter la liaison dynamique WPF, les propriétés dynamiques seront utilisées avec des fonctionnalités fournies par l’espace de noms <xref:System.Windows.Data>, notamment la classe <xref:System.Windows.Data.Binding>.  
  
## <a name="see-also"></a>Voir aussi  
 [Liaison de données WPF avec LINQ to XML](../designers/wpf-data-binding-with-linq-to-xml.md)   
 [Propriétés dynamiques LINQ to XML](../designers/linq-to-xml-dynamic-properties.md)   
 [Intégration du format XAML au format WPF](http://msdn.microsoft.com/Library/5d858575-a83b-42df-ad3f-047ed2d6e3c8)   
 [Liaison de données (WPF)](http://msdn.microsoft.com/Library/90f79b97-17e7-40d1-abf0-3ba600ad1d7e)   
 [Utilisation de la balise de workflow](http://go.microsoft.com/fwlink/?LinkId=98685)