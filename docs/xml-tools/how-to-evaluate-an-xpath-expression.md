---
title: 'Procédure : évaluer une expression XPath'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 159ba4ef-75e4-4ac8-80dc-e064e0bec345
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 02492f2e1760df3ce5cd6751808303bae75577e2
ms.sourcegitcommit: 697162f54d3c4e30df702fd0289e447e211e3a85
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/25/2018
ms.locfileid: "34549049"
---
# <a name="how-to-evaluate-an-xpath-expression"></a>Procédure : évaluer une expression XPath

Vous pouvez évaluer des expressions XPath avec le **Espion express** boîte de dialogue. L’expression XPath doit être valide par rapport à la recommandation du W3C sur XPath 1.0. Le contexte XSLT actuel, autrement dit, le `self::node()` nœud dans le **variables locales** fenêtre — fournit le contexte d’évaluation de l’expression XPath.

 La liste suivante décrit les fonctions prises en charge lors de l’évaluation d’une expression XPath :

-   Les fonctions XPath intégrées sont prises en charge.

-   Les fonctions XSLT intégrées ne sont pas prises en charge.

-   Les fonctions définies par l'utilisateur ne sont pas prises en charge.

> [!NOTE]
> La procédure suivante utilise le *belowAvg.xsl* et *books.xml* fichiers à partir de la [procédure pas à pas : déboguer une feuille de style XSLT](../xml-tools/walkthrough-debug-an-xslt-style-sheet.md) rubrique.

## <a name="to-evaluate-an-xpath-expression"></a>Pour évaluer une expression XPath

1.  Insérez un point d'arrêt à la balise de début `xsl:if`.

2.  Cliquez sur le **débogage XSLT** dans la barre d’outils de l’éditeur XML.

     Le débogueur démarre et s'arrête à la balise `xsl:if`.

3.  Avec le bouton droit et sélectionnez **Espion express**.

     Le **Espion express** boîte de dialogue s’affiche.

4.  Entrez `./price/text()` dans les **Expression** champ le **Espion express** boîte de dialogue et cliquez sur **réévaluer**.

     Le prix du nœud book actuel s’affiche dans le **valeur** boîte.

5.  Modifier l’expression XPath en `./price/text() < $bookAverage` et cliquez sur **réévaluer**.

     Le **valeur** boîte indique que l’expression XPath donne la valeur `true`.

## <a name="see-also"></a>Voir aussi

- [Débogage XSLT](../xml-tools/debugging-xslt.md)