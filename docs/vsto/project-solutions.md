---
title: Solutions Project
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- projects [Office development in Visual Studio], Project
- Office solutions [Office development in Visual Studio], Project
- Project [Office development in Visual Studio]
- templates [Office development in Visual Studio], Project
- Office projects [Office development in Visual Studio], Project
- solutions [Office development in Visual Studio], Project
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: c3364c778b8dfc290ef06b7daa5ba063ac31f3db
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34692598"
---
# <a name="project-solutions"></a>Solutions Project
  [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)] fournit des modèles de projet que vous pouvez utiliser pour créer des compléments VSTO pour Microsoft Office Project. Vous pouvez utiliser les compléments VSTO pour automatiser Project, étendre les fonctionnalités de Project ou personnaliser l’interface utilisateur de Project.  
  
 Pour plus d’informations sur les Compléments VSTO, consultez [prise en main de programmation de compléments VSTO](../vsto/getting-started-programming-vsto-add-ins.md) et [Architecture des particuliers](../vsto/architecture-of-vsto-add-ins.md). Si vous débutez en programmation avec Microsoft Office, consultez [prise en main &#40;développement Office dans Visual Studio&#41;](../vsto/getting-started-office-development-in-visual-studio.md).  
  
 [!INCLUDE[appliesto_projallapp](../vsto/includes/appliesto-projallapp-md.md)]  
  
> [!NOTE]  
>  Vous souhaitez développer des solutions qui étendent l’expérience Office sur [plusieurs plateformes](https://dev.office.com/add-in-availability)? Découvrez le nouvel [modèle des compléments Office](https://dev.office.com/docs/add-ins/overview/office-add-ins). Compléments Office ont un faible encombrement mémoire par rapport aux compléments VSTO et les solutions, et vous pouvez les créer à l’aide de presque n’importe quel web technologies, telles que HTML5, JavaScript, CSS3 et XML de programmation.  
  
## <a name="automate-project-by-using-the-project-object-model"></a>Automatisation de project à l’aide du modèle objet project  
 Le modèle objet Project expose de nombreux types que vous pouvez utiliser pour automatiser Project. Ces types vous permettent d’écrire du code pour accomplir des tâches courantes telles que la création et la modification de tâches dans un projet par programmation.  
  
 Pour accéder au modèle objet Project à partir d’un complément VSTO, utilisez le champ `Application` de la classe `ThisAddIn` dans votre projet. Le `Application` champ retourne un `Microsoft.Office.Interop.MsProject.Application` objet qui représente l’instance actuelle du projet. Pour plus d’informations, consultez [des Compléments VSTO de programme](../vsto/programming-vsto-add-ins.md).  
  
 Quand vous appelez le modèle objet Project, vous utilisez des types fournis dans l’assembly PIA (Primary Interop Assembly) pour Project. L’assembly PIA fait office de pont entre le code managé du complément VSTO et le modèle objet COM dans Project. Tous les types dans l’assembly PIA Project sont définis dans le `Microsoft.Office.Interop.MSProject` espace de noms. Pour plus d’informations sur les assemblys PIA, consultez [présentation du développement de solutions Office &#40;VSTO&#41; ](../vsto/office-solutions-development-overview-vsto.md) et [assemblys PIA Office](../vsto/office-primary-interop-assemblies.md).  
  
## <a name="use-the-project-object-model-documentation"></a>Utilisez la documentation du modèle objet project  
 Pour obtenir des informations complètes sur le modèle objet Project, vous pouvez vous reporter à la référence du modèle objet Project VBA. La documentation de référence du modèle objet VBA présente le modèle objet Project tel qu’il est exposé au code VBA (Visual Basic pour Applications). Pour plus d’informations, consultez [de référence du modèle objet Project 2010](http://go.microsoft.com/fwlink/?LinkId=199771).  
  
 Tous les objets et membres mentionnés dans la documentation de référence du modèle objet VBA correspondent aux types et aux membres de l’assembly PIA Project. Par exemple, l’objet de calendrier dans la référence du modèle objet VBA correspond à la `Microsoft.Office.Interop.MSProject.Calendar` type dans l’assembly PIA Project. Même si la documentation de référence du modèle objet VBA fournit des exemples de code pour la plupart des propriétés, méthodes et événements, vous devez traduire le code VBA fourni dans la documentation de référence en Visual Basic ou Visual C# pour pouvoir les utiliser dans un projet de complément Project VSTO créé à l’aide de Visual Studio.  
  
> [!NOTE]  
>  À l’heure actuelle, il n’existe aucune documentation de référence pour l’assembly PIA Project.  
  
### <a name="infrastructure-types-in-the-project-primary-interop-assembly"></a>Types d’infrastructure dans l’assembly PIA project  
 Lors de l’écriture de code qui utilise l’assembly PIA Project, vous remarquerez peut-être de nombreux types qui ne sont pas décrits dans la référence VBA. Ces types supplémentaires aident à convertir des objets dans le modèle objet COM de Project en code managé. Ils ne sont pas censés être utilisés directement dans votre code.  
  
 Pour plus d’informations, consultez [vue d’ensemble des classes et interfaces dans les assemblys PIA Office](http://go.microsoft.com/fwlink/?LinkId=189592).  
  
## <a name="customize-the-user-interface-of-project"></a>Personnaliser l’interface utilisateur du projet  
 Vous pouvez personnaliser l’interface utilisateur de Project de différentes façons.  
  
|Tâche|Pour plus d'informations|  
|----------|--------------------------|  
|Ajouter des onglets personnalisés au ruban dans Project|[Vue d’ensemble du ruban](../vsto/ribbon-overview.md)|  
  
 Pour plus d’informations sur la personnalisation de l’interface utilisateur de Project et d’autres applications Microsoft Office, consultez [personnalisation de l’interface utilisateur Office](../vsto/office-ui-customization.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Procédure pas à pas : Créer votre premier complément VSTO pour project](../vsto/walkthrough-creating-your-first-vsto-add-in-for-project.md)   
 [Prise en main de programmation de compléments VSTO](../vsto/getting-started-programming-vsto-add-ins.md)   
 [Présentation du développement de solutions Office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)   
 [Architecture des Compléments VSTO](../vsto/architecture-of-vsto-add-ins.md)   
 [Comment : créer des projets Office dans Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [Programmation de compléments VSTO](../vsto/programming-vsto-add-ins.md)   
 [Écrire du code dans les solutions Office](../vsto/writing-code-in-office-solutions.md)   
 [Assemblys PIA Office](../vsto/office-primary-interop-assemblies.md)   
 [Personnalisation de l’interface utilisateur Office](../vsto/office-ui-customization.md)   
 [Project 2010 et Project Server 2010 dans le développement Office](http://go.microsoft.com/fwlink/?LinkId=199016)  
  
  