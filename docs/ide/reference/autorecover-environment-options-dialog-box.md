---
title: Récupération automatique, Environnement, boîte de dialogue Options
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPag.Environment.AutoRecover
- VS.DialogAutoRestore
- VS.ToolsOptionsPages.Environment.AutoRecover
- VS.ToolsOptionsPages.Environment.Auto_Save_and_Restore
helpviewer_keywords:
- files, recovering
- AutoRecover page
- saving files, automatically
- files, saving automatically
ms.assetid: 397e5e44-4bbe-4289-94d1-642b466c9111
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3f6409e31a606fe31fa1296dc937616338f8d62c
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
ms.locfileid: "31943200"
---
# <a name="autorecover-environment-options-dialog-box"></a>Récupération automatique, Environnement, boîte de dialogue Options
Utilisez cette page de la boîte de dialogue Options pour spécifier si les fichiers sont automatiquement sauvegardés ou non. Cette page vous permet également de spécifier si les fichiers modifiés sont restaurés ou non quand l’environnement de développement intégré (IDE) s’arrête de façon inattendue. Vous pouvez accéder à cette boîte de dialogue en sélectionnant **Options** dans le menu **Outils**, puis la page **Récupération automatique** dans le dossier **Environnement**. Si cette page n’apparaît pas dans la liste, sélectionnez **Afficher tous les paramètres** dans la boîte de dialogue **Options**.

> [!NOTE]
> Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée. Pour modifier vos paramètres, choisissez Importation et exportation de paramètres dans le menu Outils. Pour plus d’informations, consultez [Personnaliser l’IDE Visual Studio](../../ide/personalizing-the-visual-studio-ide.md).

 **Enregistrer les informations de récupération automatique toutes les \<n> minutes** Utilisez cette option pour personnaliser la fréquence d’enregistrement automatique d’un fichier dans l’éditeur. Pour les fichiers déjà enregistrés, une copie du fichier est enregistrée dans \\...\Mes documents\Visual Studio \<*version*>\Fichiers de sauvegarde\\<*NomProjet*>. Si le fichier est nouveau et n’a pas été enregistré manuellement, le fichier est enregistré automatiquement à l’aide d’un nom de fichier généré de manière aléatoire.

 **Conserver les informations de récupération automatique pendant \<n> jours** Utilisez cette option pour spécifier la durée de conservation des fichiers créés pour la récupération automatique par Visual Studio.

## <a name="see-also"></a>Voir aussi

- [Options, boîte de dialogue](../../ide/reference/options-dialog-box-visual-studio.md)