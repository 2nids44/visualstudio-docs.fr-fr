---
title: 'Comment : utiliser un fichier de ressources pour spécifier des noms localisés, propriétés et autorisations | Microsoft Docs'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- Business Data Connectivity service [SharePoint development in Visual Studio], localize strings
- BDC [SharePoint development in Visual Studio], localize strings
- BDC [SharePoint development in Visual Studio], resource file
- Business Data Connectivity service [SharePoint development in Visual Studio], resource strings
- BDC [SharePoint development in Visual Studio], properties
- Business Data Connectivity service [SharePoint development in Visual Studio], properties
- Business Data Connectivity service [SharePoint development in Visual Studio], resource file
- BDC [SharePoint development in Visual Studio], resource strings
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: c54aa87f09d4821f9fde5cceb95e6ec3a8e089fa
ms.sourcegitcommit: d9e4ea95d0ea70827de281754067309a517205a1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/29/2018
ms.locfileid: "37118912"
---
# <a name="how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions"></a>Comment : utiliser un fichier de ressources pour spécifier des noms localisés, propriétés et autorisations
  En utilisant un fichier de ressources, vous pouvez fournir des noms localisés, définir des propriétés et appliquer des autorisations tor objets qui sont définis dans un modèle de connectivité de données métiers (BDC). Pour spécifier ces informations, vous ajoutez un **ressource de connectivité de données métiers** élément à un projet qui contient un **modèle de connectivité de données métiers** élément. Puis vous spécifiez des noms, les propriétés et les autorisations en modifiant le code XML pour le fichier de ressources.  
  
### <a name="to-add-a-bdc-resource-file-to-a-sharepoint-project"></a>Pour ajouter un fichier de ressources BDC à un projet SharePoint  
  
1.  Dans **l’Explorateur de solutions**, développez le dossier du projet SharePoint, puis choisissez le dossier qui contient le modèle BDC.  
  
2.  Dans la barre de menus, choisissez **Projet** > **Ajouter un nouvel élément**.  
  
3.  Développez le **SharePoint** nœud, puis choisissez le **2010** nœud.  
  
4.  Dans le **ajouter un nouvel élément** boîte de dialogue, sélectionnez **élément de ressource de connectivité de données métiers**.  
  
5.  Dans le **nom** zone, spécifiez le nom du fichier de ressources, puis choisissez le **ajouter** bouton.  
  
     Un fichier de ressources qui porte l’extension .bdcr est ajouté au projet et ouvert pour modification.  
  
6.  Ajoutez le code XML pour définir les noms localisés, les propriétés et les autorisations que vous souhaitez appliquer le modèle BDC.  
  
     Pour plus d’informations sur la définition de ces éléments, consultez [modèle et les fichiers de ressources](http://go.microsoft.com/fwlink/?LinkID=169283).  
  
## <a name="see-also"></a>Voir aussi
 [Comment : ajouter un fichier de modèle BDC existant à un projet SharePoint](../sharepoint/how-to-add-an-existing-bdc-model-file-to-a-sharepoint-project.md)   
 [Créer un modèle de connectivité de données métiers](../sharepoint/creating-a-business-data-connectivity-model.md)   
 [Comment : créer un modèle BDC](../sharepoint/how-to-create-a-bdc-model.md)   
 [Comment : inclure un assembly personnalisé dans une fonctionnalité BDC](../sharepoint/how-to-include-a-custom-assembly-in-a-bdc-feature.md)   
 [Intégration de données métiers dans SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)  
  
