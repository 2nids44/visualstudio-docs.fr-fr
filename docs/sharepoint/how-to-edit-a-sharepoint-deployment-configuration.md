---
title: 'Comment : modifier une Configuration de déploiement SharePoint | Microsoft Docs'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.Project.DeploymentConfig
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, deploying
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 9640d98522c74fb33f8845e255511a807e03961e
ms.sourcegitcommit: d9e4ea95d0ea70827de281754067309a517205a1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/29/2018
ms.locfileid: "37118966"
---
# <a name="how-to-edit-a-sharepoint-deployment-configuration"></a>Comment : modifier une configuration de déploiement SharePoint
  Vous pouvez créer une configuration de déploiement ou modifier une configuration de déploiement existante. Par exemple, vous pourrez exécuter une seule étape ou modifier l’ordre des étapes dans le processus de déploiement. Voulez-vous créer ou modifier des configurations de déploiement, car les configurations intégrées et ajoutées par programme ne peut pas être modifiées.  
  
## <a name="create-a-sharepoint-deployment-configuration"></a>Créer une configuration de déploiement SharePoint  
  
#### <a name="to-create-a-sharepoint-deployment-configuration"></a>Pour créer une configuration de déploiement SharePoint  
  
1.  Dans **l’Explorateur de solutions**, choisissez un projet SharePoint, puis, dans la barre de menus, choisissez **projet**, * NomProjet ***propriétés**.  
  
2.  Sur le **SharePoint** , choisir le **New** bouton.  
  
     Le **ajouter une nouvelle Configuration de déploiement** boîte de dialogue s’affiche.  
  
3.  Dans le **nom** texte, entrez un nom pour la configuration de déploiement.  
  
4.  Dans le **étapes de déploiement disponibles** volet, choisissez les étapes que vous souhaitez ajouter à la configuration de déploiement, cliquez sur le (**>**) bouton, puis choisissez le **OK** bouton.  
  
    > [!NOTE]  
    >  Si vous avez configuré une commande de prédéploiement ou une commande de post-déploiement, ces étapes s’exécutent uniquement si vous les ajoutez à une configuration de déploiement personnalisé.  
  
## <a name="change-the-active-deployment-configuration"></a>Modifier la configuration de déploiement active  
  
#### <a name="to-change-the-active-deployment-configuration"></a>Pour modifier la configuration de déploiement active  
  
1.  Dans **l’Explorateur de solutions**, choisissez un projet SharePoint, puis, dans la barre de menus, choisissez **projet** > **\<*nom_projet*> Propriétés**.  
  
2.  Choisissez le **SharePoint** onglet.  
  
3.  Dans le **Configuration de déploiement Active** zone de liste, choisissez le nom de la configuration de déploiement que vous souhaitez utiliser.  
  
## <a name="see-also"></a>Voir aussi
 [Empaqueter et déployer des solutions SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
  
