---
title: Essentials du Type de projet | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- project types [Visual Studio SDK]
ms.assetid: 09991589-2300-430e-b6a4-7f2b95fe676f
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: aff6cc669d7df46acaa2cbcb129a6b13b7261d9b
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31134419"
---
# <a name="project-type-essentials"></a>Essentials de Type de projet
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] inclut plusieurs types de projets pour les langues telles que [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] ou [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] vous permet également de créer vos propres types de projet.  
  
 Si vous souhaitez simplement ajouter des commandes personnalisées, des éditeurs ou des fenêtres Outil pour [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], vous pouvez le faire sans créer un nouveau type de projet. Pour plus d’informations, consultez les rubriques suivantes :  
  
-   [Commandes, menus et barres d’outils](../../extensibility/internals/commands-menus-and-toolbars.md)  
  
-   [Extensions de l’éditeur et du service de langage](../../extensibility/editor-and-language-service-extensions.md)  
  
-   [Extension et personnalisation des fenêtres d’outils](../../extensibility/extending-and-customizing-tool-windows.md)  
  
 De même, si vous souhaitez personnaliser le comportement de l’élément [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] et [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] des types de projets, vous pouvez effectuer à l’aide de sous-types de projet. Pour plus d’informations, consultez [sous-types de projet](../../extensibility/internals/project-subtypes.md).  
  
 Vous devez créer un nouveau type de projet pour les projets qui sont basés sur une langue autre que [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] et [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] si vous souhaitez prendre en charge un ou plusieurs des opérations suivantes :  
  
-   Générer  
  
-   Déploiement  
  
-   Plusieurs configurations  
  
-   Contrôle de code source  
  
-   Débogage  
  
-   Éléments de projet dans l’Explorateur de solutions  
  
-   Le **ouvrir le projet** ou **nouveau projet** boîtes de dialogue  
  
-   Imbrication de projet  
  
-   Pour plus d’informations sur les fonctionnalités des types de projets, consultez les rubriques suivantes :  
  
-   Types de projets sont des objets dans un VSPackage qui implémentent l’ensemble d’interfaces [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] attend. Si vous utilisez c# pour développer un type de projet, les classes du projet Managed Package Framework implémentent les interfaces nécessaires pour vous et vous permettent d’hériter de cette implémentation. Pour plus d’informations, consultez [à l’aide de Managed Package Framework pour implémenter un Type de projet (c#)](../../extensibility/internals/using-the-managed-package-framework-to-implement-a-project-type-csharp.md).  
  
-   Pour les développeurs C++, les classes dans la bibliothèque HierUtil fonctionnent de la même manière. Pour plus d’informations, consultez [pas dans la Build : utilisation de Classes de projet HierUtil7 pour implémenter un Type de projet (C++)](http://msdn.microsoft.com/en-us/a5c16a09-94a2-46ef-87b5-35b815e2f346).  
  
-   Types de projets peuvent prendre en charge des données autres que des fichiers de code source typique générer dans un assembly .exe ou .dll. Par exemple, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] des projets de base de données contiennent des références aux fichiers de script et de requête stockés sur le disque et ajouter des commandes à **l’Explorateur de solutions** pour exécuter les scripts et les requêtes sur une base de données, mais les projets ne gèrent pas générer un comportement. Pour plus d’informations, consultez [d’ouverture et de l’enregistrement des éléments de projet](../../extensibility/internals/opening-and-saving-project-items.md).  
  
-   Un type de projet n’a pas d’utiliser les fichiers du tout. Par exemple, un type de projet peut stocker toutes ses données dans une base de données. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] fournit les types de projets un contrôle complet sur la persistance de données pour les projets et éléments de projet. Pour plus d’informations, consultez [décisions de conception de Type de projet](../../extensibility/internals/project-type-design-decisions.md).  
  
-   Doivent fournir des types de projets un *fabrique de projet*, qui est un objet qui crée une instance du projet de type chaque fois que [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] est signalé pour ouvrir ou créer un projet basé sur ce type de projet. Pour plus d’informations, consultez [création de projet d’Instances par à l’aide de projet fabriques](../../extensibility/internals/creating-project-instances-by-using-project-factories.md).  
  
-   Types de projets doivent fournir des modèles de projets et des éléments de projet. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] utilise les modèles lorsque les utilisateurs, créer des projets et ajouter de nouveaux éléments à des projets existants. Pour plus d’informations, consultez [Ajout d’un projet et modèles d’élément de projet](../../extensibility/internals/adding-project-and-project-item-templates.md).  
  
-   Types de projets peuvent prendre en charge plusieurs configurations, par exemple Debug et Release. Les utilisateurs peuvent modifier les différentes configurations d’un projet à l’aide des pages de propriétés que vous fournissez. Pour plus d’informations, consultez [la gestion des Options de Configuration](../../extensibility/internals/managing-configuration-options.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Déploiement des types de projets](../../extensibility/internals/deploying-project-types.md)