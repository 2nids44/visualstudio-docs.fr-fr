---
title: Modèles Visual Studio pour les projets et les fichiers
ms.date: 01/02/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- templates [Visual Studio], project
- templates [Visual Studio], item
- item templates [Visual Studio]
- project templates [Visual Studio]
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 62e51a5a03011874acc723eaf159e3f7130d1340
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/01/2018
ms.locfileid: "34573256"
---
# <a name="project-and-item-templates"></a>Modèles de projet et d’élément

Les modèles de projet et d’élément offrent aux utilisateurs, via des stubs réutilisables, du code de base et des structures qu’ils peuvent personnaliser selon leurs propres besoins.

## <a name="visual-studio-templates"></a>modèles Visual Studio

L’installation de Visual Studio inclut également un certain nombre de modèles prédéfinis pour des projets et des éléments. Par exemple, les modèles **Application Windows Forms** et **Bibliothèque de classes**, figurant dans la boîte de dialogue **Nouveau projet**, sont des modèles de projet. Les modèles d’éléments figurent dans la boîte de dialogue **Ajouter un nouvel élément** et incluent des éléments tels que des fichiers de code, des fichiers XML, des pages HTML et des feuilles de style.

Ces modèles fournissent un point de départ aux utilisateurs pour commencer à créer des projets ou à développer des projets existants. Les modèles de projet fournissent les fichiers nécessaires à un type de projet particulier, incluent des références d'assembly standard et définissent les propriétés de projet ainsi que les options du compilateur par défaut. La complexité des modèles d’éléments peut aller d’un fichier unique vide ayant une extension de fichier particulière à plusieurs fichiers de code source contenant du code stub, des fichiers d’informations sur le concepteur et des ressources incorporées.

Vous pouvez utiliser les modèles installés dans les boîtes de dialogue **Nouveau projet** et **Ajouter un nouvel élément**. Vous pouvez également créer vos propres modèles, ou bien télécharger et utiliser des modèles créés par la communauté. Pour plus d’informations, consultez [Guide pratique pour créer des modèles de projet](../ide/how-to-create-project-templates.md) et [Guide pratique pour créer des modèles d’élément](../ide/how-to-create-item-templates.md).

## <a name="contents-of-a-template"></a>Contenu d’un modèle

Tous les modèles de projet et d’élément, qu’ils soient installés avec Visual Studio ou créés par vous, fonctionnent selon les mêmes principes et ont les mêmes contenus. Tous les modèles contiennent les éléments suivants :

- Les fichiers à créer lors de l'utilisation du modèle. Il s’agit des fichiers de code source, des ressources incorporées, des fichiers projet, etc.

- Un fichier *.vstemplate* contenant les métadonnées nécessaires pour afficher le modèle dans les boîtes de dialogue **Nouveau projet** et **Ajouter un nouvel élément**, ainsi que créer un projet ou un élément à partir du modèle. Pour plus d’informations sur les fichiers *.vstemplate*, consultez [Paramètres de modèle](../ide/template-parameters.md).

Quand ces fichiers sont compressés dans un fichier *.zip* et placés dans le dossier approprié, Visual Studio les affiche automatiquement aux emplacements suivants :

- Les modèles de projet s’affichent dans la boîte de dialogue **Nouveau projet**.

- Les modèles d’élément s’affichent dans la boîte de dialogue **Ajouter un nouvel élément**.

Pour plus d’informations sur les dossiers de modèles, consultez [Guide pratique pour localiser et organiser les modèles](../ide/how-to-locate-and-organize-project-and-item-templates.md).

## <a name="see-also"></a>Voir aussi

- [Guide pratique pour créer des modèles de projet](../ide/how-to-create-project-templates.md)
- [Guide pratique pour créer des modèles d’élément](../ide/how-to-create-item-templates.md)
- [Paramètres de modèle](../ide/template-parameters.md)
- [Personnaliser les modèles](../ide/customizing-project-and-item-templates.md)
- [Packages NuGet dans les modèles Visual Studio](/nuget/visual-studio-extensibility/visual-studio-templates)