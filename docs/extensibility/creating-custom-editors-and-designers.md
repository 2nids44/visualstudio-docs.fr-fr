---
title: Création de concepteurs et éditeurs personnalisés | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- designers [Visual Studio SDK]
- editors [Visual Studio SDK], custom
ms.assetid: b6a5e8b2-0ae1-4fc3-812d-09d40051b435
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 56d191d8019b4b87cc31e0e383637515a10f4147
ms.sourcegitcommit: 1c2ed640512ba613b3bbbc9ce348e28be6ca3e45
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/03/2018
ms.locfileid: "39497610"
---
# <a name="create-custom-editors-and-designers"></a>Créer des concepteurs et éditeurs personnalisés
L’environnement de développement intégré (IDE) Visual Studio peut héberger différents types de l’éditeur :  
  
-   L’éditeur principal de Visual Studio  
  
-   Éditeurs personnalisés  
  
-   Éditeurs externes  
  
-   Concepteurs  
  
 Les informations suivantes vous permettent de choisir le type d’éditeur que vous avez besoin.  
  
## <a name="types-of-editor"></a>Types de l’éditeur  
 Pour plus d’informations sur l’éditeur principal de Visual Studio, consultez [étendre les services de l’éditeur et la langue](../extensibility/extending-the-editor-and-language-services.md).  
  
### <a name="custom-editors"></a>Éditeurs personnalisés  
 Un éditeur personnalisé est celle qui est conçu pour fonctionner dans des circonstances particulières. Par exemple, vous pouvez créer un éditeur dont la fonction consiste à lire et écrire des données dans un référentiel spécifique, tel qu’un serveur Microsoft Exchange. Choisissez un éditeur personnalisé si vous souhaitez un éditeur qui fonctionne avec votre type de projet uniquement ou si vous souhaitez un éditeur qui a uniquement quelques commandes spécifiques. Notez, cependant, que les utilisateurs ne seront pas en mesure d’utiliser un éditeur personnalisé pour modifier standard [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] projets.  
  
 Un éditeur personnalisé peut utiliser une fabrique d’éditeur et ajouter des informations sur l’éditeur dans le Registre. Toutefois, le type de projet associé à l’éditeur personnalisé peut instancier l’éditeur personnalisé par d’autres moyens.  
  
 Un éditeur personnalisé peut utiliser l’activation sur place ou l’incorporation simplifiée pour implémenter une vue.  
  
### <a name="external-editors"></a>Éditeurs externes  
 Éditeurs externes sont des éditeurs qui ne sont pas intégrés à Visual Studio, tels que Microsoft Word, le bloc-notes ou Microsoft FrontPage. Vous pouvez appeler un éditeur de ce type si, par exemple, vous sont texte en lui passant à partir de votre VSPackage. Éditeurs externes s’enregistrent et peuvent être utilisées en dehors de Visual Studio. Lorsque vous appelez un éditeur externe, et elle peut être incorporée dans une fenêtre hôte, il apparaît dans une fenêtre dans l’IDE. Si ce n’est pas le cas, l’IDE crée ensuite une fenêtre distincte pour elle.  
  
 Le <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A> méthode définit la priorité du document à l’aide de la <xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY> énumération. Si le `DP_External` valeur est spécifiée, le fichier peut être ouvert par un éditeur externe.  
  
## <a name="editor-design-decisions"></a>Décisions de conception de l’éditeur  
 Les questions de conception suivantes vous aideront à choisir le type de l’éditeur de meilleures adapté à votre application :  
  
-   Votre application enregistrera ses données dans des fichiers ou pas ? Si elle enregistrera ses données dans les fichiers, ils seront dans un format standard ou personnalisé ?  
  
     Si vous utilisez un format de fichier standard, les autres types de projet en plus de votre projet sera capable d’ouvrir et lire/écrire des données leur. Toutefois, si vous utilisez un format de fichier personnalisé, uniquement le type de votre projet sera capable d’ouvrir et lire/écrire des données leur.  
  
     Si votre projet utilise des fichiers, vous devez personnaliser l’éditeur standard. Si votre projet n’utilise pas de fichiers, mais utilise plutôt des éléments dans une base de données ou autre référentiel, vous devez créer un éditeur personnalisé.  
  
-   Votre éditeur n’a besoin pour héberger des contrôles ActiveX ?  
  
     Si votre éditeur héberge des contrôles ActiveX, puis implémenter un éditeur d’activation sur place, comme indiqué dans [In situ d’activation](../extensibility/in-place-activation.md). Si elle n’héberge pas de contrôles ActiveX, puis utilisez un éditeur d’incorporation simplifié, ou personnaliser la [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] éditeur par défaut.  
  
-   Votre éditeur prendra en charge plusieurs vues ? Si vous souhaitez que les vues de votre éditeur soient visibles en même temps que l’éditeur par défaut, vous devez prendre en charge plusieurs vues.  
  
     Si votre éditeur doit prendre en charge plusieurs vues, les données de document et les objets de vue de document pour l’éditeur doivent être des objets distincts. Pour plus d’informations, consultez [prendre en charge plusieurs vues de document](../extensibility/supporting-multiple-document-views.md).  
  
     Si votre éditeur prend en charge plusieurs vues, vous prévoyez d’utiliser le [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] implémentation de mémoire tampon de texte de l’éditeur de base (<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> objet) pour votre objet de données de document ? Autrement dit, vous souhaitez prendre en charge de votre éditeur vue côte à côte avec la [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] éditeur principal ? La possibilité de procéder est la base du Concepteur de formulaires...  
  
-   Si vous avez besoin pour héberger un éditeur externe, l’éditeur incorporable dans [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]?  
  
     Si elle peut être incorporée, vous devez créer une fenêtre hôte pour l’éditeur externe et appelez ensuite la <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A> (méthode) et définissez le <xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY> valeur d’énumération à `DP_External`. Si l’éditeur ne peut pas être incorporé, l’IDE crée automatiquement une fenêtre distincte pour celui-ci.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Procédure pas à pas : Créer un éditeur personnalisé](../extensibility/walkthrough-creating-a-custom-editor.md)  
 Explique comment créer un éditeur personnalisé.  
  
 [Procédure pas à pas : Ajout de fonctionnalités à un éditeur personnalisé](../extensibility/walkthrough-adding-features-to-a-custom-editor.md)  
 Explique comment ajouter des fonctionnalités à un éditeur personnalisé.  
  
 [Configuration de l’initialisation et de métadonnées de concepteur](../extensibility/designer-initialization-and-metadata-configuration.md)  
 Explique comment initialiser un concepteur.  
  
 [Annulation prise en charge pour les concepteurs](../extensibility/supplying-undo-support-to-designers.md)  
 Explique comment fournir la prise en charge de l’annulation pour les concepteurs.  
  
 [Couleurs de syntaxe dans les éditeurs personnalisés](../extensibility/syntax-coloring-in-custom-editors.md)  
 Explique la différence entre les couleurs dans l’éditeur principal et dans les éditeurs personnalisés de syntaxe.  
  
 [Données de document et les vues de document dans les éditeurs personnalisés](../extensibility/document-data-and-document-view-in-custom-editors.md)  
 Explique comment implémenter des données de documents et vues de document dans les éditeurs personnalisés.  
  
## <a name="related-sections"></a>Rubriques connexes  
 [Interfaces héritées dans l’éditeur](../extensibility/legacy-interfaces-in-the-editor.md)  
 Explique comment accéder à l’éditeur principal au moyen de l’API héritée.  
  
 [Développer un service de langage hérité](../extensibility/internals/developing-a-legacy-language-service.md)  
 Explique comment implémenter un service de langage.  
  
 [Étendre d’autres parties de Visual Studio](../extensibility/extending-other-parts-of-visual-studio.md)  
 Explique comment créer des éléments d’interface utilisateur qui correspondent au reste de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
## <a name="see-also"></a>Voir aussi  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory>