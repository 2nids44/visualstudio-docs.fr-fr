---
title: 'Comment : ajouter un lanceur de boîte de dialogue à un groupe de ruban'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- dialog box launcher [Office development in Visual Studio]
- Ribbon [Office development in Visual Studio], dialog box launcher
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 2513113b473341f2ed099ef0c5ff5961694acb19
ms.sourcegitcommit: 697162f54d3c4e30df702fd0289e447e211e3a85
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/25/2018
ms.locfileid: "34548386"
---
# <a name="how-to-add-a-dialog-box-launcher-to-a-ribbon-group"></a>Comment : ajouter un lanceur de boîte de dialogue à un groupe de ruban
  Vous pouvez ajouter un lanceur de boîte de dialogue à un groupe sur un ruban. Un lanceur de boîte de dialogue est une petite icône qui apparaît dans un groupe. Les utilisateurs cliquent sur cette icône pour ouvrir des boîtes de dialogue connexes ou des volets de tâches qui fournissent des options supplémentaires qui se rapportent au groupe.  
  
 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]  
  
### <a name="to-add-a-dialog-box-launcher-to-a-ribbon-group"></a>Pour ajouter un lanceur de boîte de dialogue à un groupe de ruban  
  
1.  Sélectionnez le fichier de code du ruban (*.vb* ou *.cs* fichier) dans **l’Explorateur de solutions**.  
  
2.  Sur le **vue** menu, cliquez sur **concepteur**.  
  
3.  Dans le Concepteur de ruban, avec le bouton droit n’importe quel groupe, puis cliquez sur **Ajouter DialogBoxLauncher**.  
  
     Ajoutez le code pour le <xref:Microsoft.Office.Tools.Ribbon.RibbonGroup.DialogLauncherClick> événement du groupe pour ouvrir une boîte de dialogue personnalisée ou intégrée.  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble du ruban](../vsto/ribbon-overview.md)   
 [Accéder au ruban au moment de l’exécution](../vsto/accessing-the-ribbon-at-run-time.md)   
 [Procédures pas à pas et des exemples de développement office](../vsto/office-development-samples-and-walkthroughs.md)   
 [Concepteur de ruban](../vsto/ribbon-designer.md)   
 [Présentation du modèle objet de ruban](../vsto/ribbon-object-model-overview.md)   
 [Élément XML Ribbon](../vsto/ribbon-xml.md)   
 [Comment : exporter un ruban à partir du Concepteur de ruban vers ruban XML](../vsto/how-to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml.md)   
 [Comment : modifier la position d’un onglet du ruban](../vsto/how-to-change-the-position-of-a-tab-on-the-ribbon.md)   
 [Comment : personnaliser un onglet intégré](../vsto/how-to-customize-a-built-in-tab.md)   
 [Comment : ajouter des contrôles au mode Backstage](../vsto/how-to-add-controls-to-the-backstage-view.md)   
 [Personnaliser un ruban pour Outlook](../vsto/customizing-a-ribbon-for-outlook.md)   
 [Comment : démarrer avec la personnalisation du ruban](../vsto/how-to-get-started-customizing-the-ribbon.md)   
 [Comment : ajouter dans l’affichage des erreurs d’interface utilisateur](../vsto/how-to-show-add-in-user-interface-errors.md)   
 [Procédure pas à pas : Création d’un onglet personnalisé à l’aide du Concepteur de ruban](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)   
 [Procédure pas à pas : Mise à jour les contrôles sur un ruban au moment de l’exécution](../vsto/walkthrough-updating-the-controls-on-a-ribbon-at-run-time.md)   
 [Procédure pas à pas : Créer un onglet personnalisé à l’aide de XML du ruban](../vsto/walkthrough-creating-a-custom-tab-by-using-ribbon-xml.md)  
  
  