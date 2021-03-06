---
title: 'Concepteur de flux de travail - Comment : déboguer XAML avec Workflow Designer'
ms.date: 11/04/2016
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
ms.assetid: d9305dbc-af62-4bdd-b03f-c54e3fe9ecc7
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- uwp
ms.openlocfilehash: f965a7ba94242b44fc83317bf0d152de540e0a90
ms.sourcegitcommit: 30f653d9625ba763f6b58f02fb74a24204d064ea
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2018
ms.locfileid: "36758180"
---
# <a name="how-to-debug-xaml-with-the-workflow-designer"></a>Procédure : déboguer du code XAML avec Workflow Designer

Les workflows sont définis en code XAML. La représentation de l’interface utilisateur du workflow est construite sur l’arborescence XAML définissant le workflow. L’expérience de débogage est semblable au débogage de flux de travail dans le Concepteur de Workflow. Par exemple, pendant le débogage de XAML, les variables locales, Espion et threads windows fonctionnent la même façon comme ils le font dans le Concepteur de flux de travail de débogage. De plus, la vue de la pile des appels pendant le débogage de code XAML est une vue hiérarchique basée sur les lignes du flux d'exécution pour le workflow.

> [!NOTE]
> Si le code XAML pour un workflow se trouve dans le même assembly que les activités, la partie d'assembly des noms de classe n'est pas incluse. Sans cette partie des noms de classe (activité), le code XAML ne peut pas être chargé au moment de l'exécution. Il n'est pas recommandé de définir des activités dans le même espace de noms que le projet principal ; sinon, le code XAML doit être modifié manuellement après avoir été modifié dans le concepteur.

## <a name="to-debug-workflow-xaml"></a>Pour déboguer le code XAML du workflow

1.  Dans Visual Studio, ouvrez un projet de flux de travail ou d’activité.

2.  Définir un point d’arrêt sur l’activité ou les activités que vous souhaitez déboguer, comme décrit dans [Comment : définir des points d’arrêt dans les Workflows](../workflow-designer/how-to-set-breakpoints-in-workflows.md).

3.  Cliquez sur le fichier .xaml qui contient votre définition de flux de travail, puis sélectionnez **afficher le Code**. Vous verrez un point d'arrêt affiché sur la même ligne que la déclaration d'élément XAML de l'activité sur laquelle vous définissez le point d'arrêt en mode Design.

4.  Appelez le débogueur, comme décrit dans [Comment : appeler le débogueur de flux de travail](../workflow-designer/how-to-invoke-the-workflow-debugger.md).

5.  Lorsque l'exécution du code atteint l'un de vos points d'arrêt, l'élément XAML associé à ce point d'arrêt est mis en surbrillance. Pour déplacer le point d’arrêt suivant, utilisez le **F10** ou **F11** clé.

## <a name="see-also"></a>Voir aussi

- [Guide pratique pour définir des points d’arrêt dans les flux de travail](../workflow-designer/how-to-set-breakpoints-in-workflows.md)
- [Guide pratique pour appeler le débogueur de flux de travail](../workflow-designer/how-to-invoke-the-workflow-debugger.md)