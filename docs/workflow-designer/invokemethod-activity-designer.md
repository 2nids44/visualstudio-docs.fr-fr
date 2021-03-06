---
title: Concepteur de flux de travail - Concepteur d’activités InvokeMethod
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- System.Activities.Statements.InvokeMethod.UI
ms.assetid: 15e6efdc-52ca-46d8-9c5e-063f7c8265a6
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 03c62abe30fe2ba3896885d1969a3ec2bc45cc86
ms.sourcegitcommit: 30f653d9625ba763f6b58f02fb74a24204d064ea
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2018
ms.locfileid: "36757764"
---
# <a name="invokemethod-activity-designer"></a>Concepteur d'activités InvokeMethod

**InvokeMethod** concepteur est utilisé pour créer et configurer un <xref:System.Activities.Statements.InvokeMethod> activité.

## <a name="the-invokemethod-activity"></a>L’activité InvokeMethod

<xref:System.Activities.Statements.InvokeMethod> appelle une méthode publique d'un objet ou d'un type spécifié.

### <a name="use-the-invokemethod-activity-designer"></a>Utiliser le Concepteur d’activités InvokeMethod

Accès le **InvokeMethod** Concepteur d’activités dans le **Primitives** catégorie de la **boîte à outils**. Le **InvokeMethod** Concepteur d’activités peut être déplacé de la **boîte à outils** et supprimé une session sur l’aire du Concepteur de flux de travail, quel que soit les activités sont généralement placées, par exemple dans un <xref:System.Activities.Statements.Sequence>. Suppression du Concepteur d’activités crée un <xref:System.Activities.Statements.InvokeMethod> activité avec une valeur par défaut <xref:System.Activities.Activity.DisplayName%2A> de InvokeMethod. Le <xref:System.Activities.Activity.DisplayName%2A> peuvent être modifiées dans l’en-tête de la **InvokeMethod** Concepteur d’activités ou dans le **DisplayName** case de la grille des propriétés.

### <a name="the-invokemethod-properties"></a>Les propriétés d’InvokeMethod

Le tableau suivant présente le <xref:System.Activities.Statements.InvokeMethod> propriétés et décrit leur utilisation dans le concepteur. Ces propriétés peuvent être modifiées dans la grille des propriétés et certaines peuvent être modifiés sur l’aire du Concepteur de flux de travail.

|Nom de la propriété|Obligatoire|Utilisation|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Nom convivial de l'activité <xref:System.Activities.Statements.InvokeMethod>. La valeur par défaut est InvokeMethod.<br /><br /> Bien que le <xref:System.Activities.Activity.DisplayName%2A> n’est pas strictement obligatoire, il est préférable d’utiliser un.|
|<xref:System.Activities.Statements.InvokeMethod.MethodName%2A>|True|Nom de la méthode à appeler lorsque l'activité s'exécute. La méthode appelée doit être déclarée en tant que **public**. Cette propriété peut être modifiée sur l’aire du concepteur et est obligatoire.|
|<xref:System.Activities.Statements.InvokeMethod.Parameters%2A>|False|Collection de paramètres de la méthode appelée. Les paramètres doivent être ajoutés à la collection selon leur ordre d’affichage dans la signature de méthode. Pour afficher le **paramètres** boîte de dialogue où vous pouvez définir cette propriété, cliquez sur le bouton de sélection dans le **paramètres** champ de la grille des propriétés. Cliquez sur le **créer un Argument** pour ajouter les paramètres.|
|<xref:System.Activities.Statements.InvokeMethod.Result%2A>|False|Valeur de retour de l'appel de méthode.|
|<xref:System.Activities.Statements.InvokeMethod.RunAsynchronously%2A>|True|Spécifie si la méthode est appelée de façon asynchrone. La valeur par défaut est **False**.|
|<xref:System.Activities.Statements.InvokeMethod.TargetObject%2A>|False|Objet qui contient la méthode à appeler. Cette propriété peut être modifiée dans l'aire du concepteur.<br /><br /> La propriété <xref:System.Activities.Statements.InvokeMethod.TargetObject%2A> ou <xref:System.Activities.Statements.InvokeMethod.TargetType%2A> doit obligatoirement être définie.|
|<xref:System.Activities.Statements.InvokeMethod.TargetType%2A>|False|Type d'élément <xref:System.Activities.Statements.InvokeMethod.TargetObject%2A>. Cette propriété peut être modifiée dans l'aire du concepteur. Elle doit être définie uniquement si la méthode appelée est statique.|

Pour passer des paramètres en tant que C# **out** paramètre (par exemple, `Method1(out myParam))`, utilisez **OutArgument** au lieu de **InOutArgument**

Méthodes comportant des arguments appelés **TargetObject** ou **résultat** ne peut pas être appelé à l’aide de la <xref:System.Activities.Statements.InvokeMethod> activité. En effet, l'activité <xref:System.Activities.Statements.InvokeMethod> inscrit <xref:System.Activities.Statements.InvokeMethod.GenericTypeArguments%2A>, <xref:System.Activities.Statements.InvokeMethod.TargetObject%2A> et <xref:System.Activities.Statements.InvokeMethod.Result%2A> dans <xref:System.Activities.Activity.CacheMetadata%2A>.

L'algorithme permettant d'inscrire les paramètres dans <xref:System.Activities.Activity.CacheMetadata%2A> est présenté dans la liste suivante :

1.  Inscrivez l'argument <xref:System.Activities.Statements.InvokeMethod.TargetObject%2A>.

2.  Inscrivez l'argument <xref:System.Activities.Statements.InvokeMethod.Result%2A>.

3.  Effectuez une itération au sein de la collection <xref:System.Activities.Statements.InvokeMethod.Parameters%2A> et inscrivez chaque argument.

L'exception obtenue est de type <xref:System.Activities.InvalidWorkflowException> avec le message suivant : 'InvokeMethod' : Une variable, un RuntimeArgument ou un DelegateArgument, portant le nom 'TargetObject' existe déjà. Les noms doivent être uniques au sein de la portée de l'environnement.

Cette restriction ne s’applique pas à <xref:System.Activities.Statements.InvokeMethod.TargetType%2A> et <xref:System.Activities.Statements.InvokeMethod.RunAsynchronously%2A>. Ils ne sont pas des arguments de flux de travail et par conséquent, ne sont pas inscrits dans le <xref:System.Activities.Statements.InvokeMethod.GenericTypeArguments%2A> collection de la <xref:System.Activities.Statements.InvokeMethod> activité dans le <xref:System.Activities.Activity.CacheMetadata%2A> (méthode).

## <a name="see-also"></a>Voir aussi

- [Primitives](../workflow-designer/primitives-activity-designers.md)
- [Affecter](../workflow-designer/assign-activity-designer.md)
- [Délai](../workflow-designer/delay-activity-designer.md)
- [WriteLine](../workflow-designer/writeline-activity-designer.md)