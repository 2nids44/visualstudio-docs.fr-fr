---
title: Sécurité et déploiement ClickOnce | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- Windows applications, ClickOnce deployment
- deploying applications [ClickOnce]
- ClickOnce deployment
- publishing, ClickOnce
ms.assetid: abab6d34-c3c2-45c1-a8b6-43c7d3131e7a
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 70c90d70af60b6bd1f2399847447c1d49785ebb0
ms.sourcegitcommit: 8ee7efb70a1bfebcb6dd9855b926a4ff043ecf35
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/17/2018
ms.locfileid: "39078424"
---
# <a name="clickonce-security-and-deployment"></a>Sécurité et déploiement ClickOnce
[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] est une technologie de déploiement qui vous permet de créer des applications Windows mise à jour automatique qui peuvent être installées et exécutées avec une intervention minime de l’utilisateur. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Fournit la prise en charge complète pour la publication et la mise à jour des applications déployées avec la technologie ClickOnce si vous avez développé vos projets avec Visual Basic et Visual c#. Pour plus d’informations sur le déploiement d’applications Visual C++, consultez [déploiement ClickOnce pour les Applications Visual C++](/cpp/ide/clickonce-deployment-for-visual-cpp-applications).  
  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] déploiement propose trois problèmes majeurs au déploiement :  
  
-   **Difficultés de mise à jour des applications.** Avec le déploiement de Microsoft Windows Installer, chaque fois qu’une application est mise à jour, l’utilisateur peut installer une mise à jour, un fichier msp et s’appliquent au produit installé ; avec [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] déploiement, vous pouvez fournir des mises à jour automatiquement. Uniquement les parties de l’application qui ont changé sont téléchargées, puis l’application complète, mise à jour est réinstallée à partir d’un nouveau dossier côte à côte.  
  
-   **Impact sur l’ordinateur de l’utilisateur.** Avec le déploiement de programme d’installation de Windows, applications dépendent souvent des composants partagés, avec le risque de conflits de versions ; avec [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] déploiement, chaque application est autonome et ne peut pas interférer avec d’autres applications.  
  
-   **Autorisations de sécurité.** Déploiement de Windows Installer requiert des autorisations administratives et autorise uniquement l’installation utilisateur limité ; [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] déploiement permet aux utilisateurs non administratifs d’installer et accorde uniquement les autorisations de sécurité d’accès du Code nécessaires à l’application.  
  
 Dans le passé, ces problèmes parfois les développeurs choisissent de créer des applications Web au lieu de Windows des applications, pour autant sacrifier une interface utilisateur élaborée pour faciliter l’installation. À l’aide des applications déployées à l’aide de [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)], vous pouvez bénéficier du meilleur des deux technologies.  
  
## <a name="what-is-a-clickonce-application"></a>Qu’est une application ClickOnce ?  
 Un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] application est n’importe quel ordinateur Windows Presentation Foundation (*.xbap*), Windows Forms (*.exe*), application console (*.exe*), ou une solution Office (*.dll*) publiée à l’aide [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] technologie. Vous pouvez publier un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] application de trois façons différentes : à partir d’une page Web, à partir d’un partage de fichiers réseau ou à partir d’un support tel qu’un CD-ROM. Un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] application peut être installée sur l’ordinateur de l’utilisateur final et exécutée localement même si l’ordinateur est hors connexion, ou il peut être exécuté en mode en ligne uniquement sans installer quoi que ce soit de façon permanente sur l’ordinateur de l’utilisateur final. Pour plus d’informations, consultez [choisir une stratégie de déploiement ClickOnce](../deployment/choosing-a-clickonce-deployment-strategy.md).  
  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] applications peuvent être mise à jour automatique ; elles peuvent vérifier les versions plus récentes dès qu’ils sont disponibles et remplacement automatiquement tous les fichiers mis à jour. Le développeur peut spécifier le comportement de mise à jour ; un administrateur réseau peut également contrôler les stratégies, par exemple, marquer une mise à jour comme étant obligatoire de mettre à jour. Mises à jour peuvent également être restaurées vers une version antérieure restaurée par l’utilisateur final ou par un administrateur. Pour plus d’informations, consultez [choisir une stratégie de mise à jour ClickOnce](../deployment/choosing-a-clickonce-update-strategy.md).  
  
 Étant donné que [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] les applications sont isolées, l’installation ou exécutant une [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] application ne peut pas arrêter des applications existantes. [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] les applications sont autonomes ; chaque [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] application est installée et exécutée à partir d’un sécurisé cache par utilisateur, par application. [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] applications s’exécutent dans les zones de sécurité Internet ou Intranet. Si nécessaire, l’application peut demander des autorisations de sécurité avec élévation de privilèges. Pour plus d’informations, consultez [applications ClickOnce Secure](../deployment/securing-clickonce-applications.md).  
  
## <a name="how-clickonce-security-works"></a>Fonctionne de la sécurité ClickOnce  
 Le cœur [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] est basée sur les certificats, les stratégies de sécurité d’accès au code et l’invite d’approbation ClickOnce.  
  
### <a name="certificates"></a>Certificats  
 Certificats Authenticode sont utilisés pour vérifier l’authenticité du serveur de publication de l’application. En utilisant Authenticode pour le déploiement d’applications, ClickOnce permet d’empêcher un programme nuisible préjudiciable se présente comme un programme légitime provenant d’une source digne de confiance connue. Si vous le souhaitez, les certificats peuvent également être utilisés pour signer l’application et manifestes de déploiement afin de prouver que les fichiers n’ont pas été falsifiés. Pour plus d’informations, consultez [ClickOnce et Authenticode](../deployment/clickonce-and-authenticode.md). Certificats peuvent également être utilisés pour configurer des ordinateurs clients pour avoir une liste des éditeurs approuvés. Si une application provient d’un éditeur approuvé, il peut être installé sans aucune interaction utilisateur. Pour plus d’informations, consultez [vue d’ensemble du déploiement d’application approuvé](../deployment/trusted-application-deployment-overview.md).  
  
### <a name="code-access-security"></a>Sécurité d'accès du code  
 Sécurité d’accès de code permet de limiter l’accès dont dispose le code aux ressources protégées. Dans la plupart des cas, vous pouvez choisir les zones Internet ou Intranet Local pour limiter les autorisations. Utilisez le **sécurité** page dans le **ProjectDesigner** pour demander la zone appropriée pour l’application. Vous pouvez également déboguer des applications avec des autorisations restreintes pour émuler l’expérience utilisateur final. Pour plus d’informations, consultez [Sécurité d’accès du code pour les applications ClickOnce](../deployment/code-access-security-for-clickonce-applications.md).  
  
### <a name="clickonce-trust-prompt"></a>Invite d’approbation ClickOnce  
 Si l’application demande plus d’autorisations que vous permet de la zone, l’utilisateur final peut être invité à prendre une décision d’approbation. L’utilisateur final peut décider si les applications ClickOnce telles que les applications Windows Forms, les applications Windows Presentation Foundation, les applications de console, les applications de navigateur XAML et les solutions Office sont approuvées pour exécution. Pour plus d’informations, consultez [Comment : configurer le comportement invite d’approbation ClickOnce](../deployment/how-to-configure-the-clickonce-trust-prompt-behavior.md).  
  
## <a name="how-clickonce-deployment-works"></a>Fonctionnement du déploiement de ClickOnce  
 Le cœur [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] architecture de déploiement repose sur deux fichiers manifeste XML : un manifeste d’application et un manifeste de déploiement. Les fichiers sont utilisés pour décrire dans lequel les applications ClickOnce sont installées à partir de, comment ils sont mis à jour, et lorsqu’ils sont mis à jour.  
  
### <a name="publish-clickonce-applications"></a>Publier des applications ClickOnce  
 Le manifeste d’application décrit l’application elle-même. Cela inclut les assemblys, les dépendances et les fichiers qui composent l’application, les autorisations requises et l’emplacement où les mises à jour seront disponibles. Le développeur d’applications crée le manifeste d’application en utilisant l’Assistant Publication dans Visual Studio ou Manifest Generation and Editing Tool (*Mage.exe*) dans le [!INCLUDE[winsdklong](../deployment/includes/winsdklong_md.md)]. Pour plus d’informations, consultez [Comment : publier une application ClickOnce à l’aide de l’Assistant Publication](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md).  
  
 Le manifeste de déploiement décrit comment l’application est déployée. Cela inclut l’emplacement du manifeste d’application et la version de l’application que les clients doivent exécuter.  
  
### <a name="deploy-clickonce-applications"></a>Déployer des applications ClickOnce  
 Après sa création, le manifeste de déploiement est copié vers l’emplacement de déploiement. Cela peut être un serveur Web, partage de fichiers réseau ou un support tel qu’un CD. Le manifeste d’application et tous les fichiers d’application sont également copiés vers un emplacement de déploiement qui est spécifié dans le manifeste de déploiement. Cela peut être le même que l’emplacement de déploiement, ou il peut être un autre emplacement. Lorsque vous utilisez le **Assistant Publication** dans Visual Studio, les opérations de copie sont exécutées automatiquement.  
  
### <a name="install-clickonce-applications"></a>Installer des applications ClickOnce  
 Après que qu’il est déployé à l’emplacement de déploiement, les utilisateurs finaux peuvent télécharger et installer l’application en cliquant sur une icône représentant le fichier manifeste de déploiement sur une page Web ou dans un dossier. Dans la plupart des cas, l’utilisateur final est présenté avec une simple boîte de dialogue invitant l’utilisateur à confirmer l’installation, après quoi l’installation continue et l’application est lancée sans autre intervention. Dans les cas où l’application nécessite des autorisations élevées ou si l’application n’est pas signée par un certificat approuvé, la boîte de dialogue demande également à l’utilisateur pour accorder l’autorisation avant de poursuivre l’installation. Bien que les installations ClickOnce soient par utilisateur, l’élévation d’autorisations peut être nécessaire s’il existe des conditions préalables qui nécessitent des privilèges d’administrateur. Pour plus d’informations sur les autorisations élevées, consultez [ClickOnce de sécurisation des applications](../deployment/securing-clickonce-applications.md).  
  
 Les certificats peuvent être approuvés au niveau de l’ordinateur ou d’entreprise, afin que les applications ClickOnce signées avec un certificat approuvé puissent installer en mode silencieux. Pour plus d’informations sur les certificats de confiance, consultez [vue d’ensemble du déploiement d’application approuvé](../deployment/trusted-application-deployment-overview.md).  
  
 L’application peut être ajoutée à l’utilisateur **Démarrer** menu et à la **Ajout / Suppression de programmes** groupe dans le **le panneau de configuration**. Contrairement à d’autres technologies de déploiement, rien n’est ajouté à la **Program Files** dossier ou le Registre et aucun droit d’administrateur est requis pour l’installation  
  
> [!NOTE]
>  Il est également possible d’empêcher l’application d’être ajouté à la **Démarrer** menu et **Ajout / Suppression de programmes** groupe en vigueur se comportent comme une application Web. Pour plus d’informations, consultez [choisir une stratégie de déploiement ClickOnce](../deployment/choosing-a-clickonce-deployment-strategy.md).  
  
### <a name="update-clickonce-applications"></a>Mettre à jour des applications ClickOnce  
 Lorsque les développeurs d’applications créent une version mise à jour de l’application, ils génèrent un manifeste d’application et que vous copiez des fichiers vers un emplacement de déploiement, généralement un dossier frère au dossier de déploiement de l’application d’origine. L’administrateur met à jour le manifeste de déploiement pour pointer vers l’emplacement de la nouvelle version de l’application.  
  
> [!NOTE]
>  Le **Assistant Publication** dans Visual Studio peut être utilisé pour effectuer ces étapes.  
  
 Outre l’emplacement de déploiement, le manifeste de déploiement contient également un emplacement de mise à jour (une page Web ou réseau partage de fichiers) où l’application vérifie les versions mises à jour. [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] **Publier** propriétés sont utilisées pour spécifier quand et à quelle fréquence l’application doit vérifier les mises à jour. Comportement de mise à jour peut être spécifié dans le manifeste de déploiement, ou il peut être présenté en tant que choix de l’utilisateur dans l’interface utilisateur de l’application par le biais de la [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] API. En outre, **publier** propriétés peuvent être employées pour mettre à jour obligatoire ou restaurer une version antérieure. Pour plus d’informations, consultez [choix d’une stratégie de mise à jour ClickOnce](../deployment/choosing-a-clickonce-update-strategy.md).  
  
### <a name="third-party-installers"></a>Programmes d’installation tiers  
 Vous pouvez personnaliser votre programme d’installation ClickOnce pour installer les composants tiers, ainsi que votre application. Vous devez disposer du package redistribuable (fichier .exe ou .msi) et décrire le package avec un manifeste de produit de linguistiquement neutre et un manifeste de package de langage spécifique. Pour plus d’informations, consultez [création de packages de programme d’amorçage](../deployment/creating-bootstrapper-packages.md).  
  
## <a name="clickonce-tools"></a>Outils ClickOnce  
 Le tableau suivant montre les outils que vous pouvez utiliser pour générer, modifier, signer et signer à nouveau les manifestes d’application et de déploiement.  
  
|Tool|Description|  
|----------|-----------------|  
|[Page Sécurité, Concepteur de projet](../ide/reference/security-page-project-designer.md)|Signe les manifestes d’application et de déploiement.|  
|[Page Publier, Concepteur de projets](../ide/reference/publish-page-project-designer.md)|Génère et modifie les manifestes d’application et de déploiement pour les applications Visual Basic et Visual c#.|  
|[*Mage.exe* (Manifest Generation and Editing outil)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool)|Génère les manifestes d’application et de déploiement pour les applications Visual Basic, Visual c# et Visual C++.<br /><br /> Signe et signe à nouveau les manifestes d’application et de déploiement.<br /><br /> Peut être exécuté à partir de scripts de commandes et de l’invite de commandes.|  
|[*MageUI.exe* (Manifest Generation and Editing Tool, Graphical Client)](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client)|Génère et modifie les manifestes d’application et de déploiement.<br /><br /> Signe et signe à nouveau les manifestes d’application et de déploiement.|  
|[GenerateApplicationManifest, tâche](../msbuild/generateapplicationmanifest-task.md)|Génère le manifeste d’application.<br /><br /> Peut être exécuté à partir de MSBuild. Pour plus d’informations, consultez [référence MSBuild](../msbuild/msbuild-reference.md).|  
|[GenerateDeploymentManifest, tâche](../msbuild/generatedeploymentmanifest-task.md)|Génère le manifeste de déploiement.<br /><br /> Peut être exécuté à partir de MSBuild. Pour plus d’informations, consultez [référence MSBuild](../msbuild/msbuild-reference.md).|  
|[Signfile, tâche](../msbuild/signfile-task.md)|Signe les manifestes d’application et de déploiement.<br /><br /> Peut être exécuté à partir de MSBuild. Pour plus d’informations, consultez [référence MSBuild](../msbuild/msbuild-reference.md).|  
|<xref:Microsoft.Build.Tasks.Deployment.ManifestUtilities>|Développer votre propre application pour générer les manifestes d’application et de déploiement.|  
  
 Le tableau suivant présente la version de .NET Framework requise pour prendre en charge des applications ClickOnce dans ces navigateurs.  
  
|Visiteur|Version du .NET Framework|  
|-------------|----------------------------|  
|Internet Explorer|2.0, 3.0, 3.5, 3.5 SP1, 4|  
|Firefox|2.0 SP1, 3.5 SP1, 4|  
  
## <a name="see-also"></a>Voir aussi  
 [Déploiement ClickOnce sur Windows Vista](../deployment/clickonce-deployment-on-windows-vista.md)   
 [Publier des applications ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [Sécuriser les applications ClickOnce](../deployment/securing-clickonce-applications.md)   
 [Déployer des composants COM avec ClickOnce](../deployment/deploying-com-components-with-clickonce.md)   
 [Générer des applications ClickOnce à partir de la ligne de commande](../deployment/building-clickonce-applications-from-the-command-line.md)   
 [Déboguer des applications ClickOnce qui utilisent System.Deployment.Application](../deployment/debugging-clickonce-applications-that-use-system-deployment-application.md)