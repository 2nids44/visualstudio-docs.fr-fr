---
title: "Pr&#233;paration du d&#233;bogage : types de projets Visual C++ | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "C++"
helpviewer_keywords: 
  - "versions debug, paramètres de projet"
  - "déboguer (C++)"
  - "modèles de projet, débogage"
  - "projets Visual C++, débogage"
ms.assetid: 912b4ba2-7719-43d5-b087-db33e3f9329a
caps.latest.revision: 24
caps.handback.revision: 24
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Pr&#233;paration du d&#233;bogage : types de projets Visual C++
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Cette section explique le débogage de types de projets de base, créés par les modèles de projet [!INCLUDE[vcprvc](../debugger/includes/vcprvc_md.md)].  
  
 Notez que ces types de projets qui créent des DLL en tant que sortie ont été regroupés dans [Débogage de projets DLL](../debugger/debugging-dll-projects.md) à cause des fonctionnalités communes qu'ils partagent.  
  
##  <a name="BKMK_In_this_topic"></a> Dans cette rubrique  
 [Paramètres de propriété recommandés](#BKMK_Recommended_Property_Settings)  
  
 [Projets Win32](#BKMK_Win32_Projects)  
  
-   [Pour déboguer une application Win32 C ou C++](#BKMK_To_debug_a_C_or_C___Win32_application)  
  
-   [Pour définir manuellement une configuration Debug](#BKMK_To_manually_set_a_Debug_configuration)  
  
 [Applications Windows Forms (.NET)](#BKMK_Windows_Forms_Applications___NET_)  
  
##  <a name="BKMK_Recommended_Property_Settings"></a> Paramètres de propriété recommandés  
 Certaines propriétés doivent être définies de la même manière pour tous les scénarios de débogage non managé.  Les tableaux suivants présentent les paramètres de propriété recommandés.  Les paramètres qui n'y sont pas répertoriés peuvent varier parmi les différents types de projet non managés.  Pour plus d'informations, consultez [Paramètres de projet pour une configuration Debug C\+\+](../debugger/project-settings-for-a-cpp-debug-configuration.md)  
  
### Propriétés de configuration &#124; C\/C\+\+ &#124; nœud Optimisation  
  
|Nom de la propriété|Paramètre|  
|-------------------------|---------------|  
|**Optimisation**|Affectez la valeur **Désactivé \(\/0d\).** Le code optimisé est plus difficile à déboguer, car les instructions générées ne correspondent pas directement à votre code source.  Si vous trouvez que votre programme présente un bogue uniquement dans du code optimisé, vous pouvez activer ce paramètre, tout en gardant à l'esprit que le code affiché dans la fenêtre **Code machine** est généré à partir d'une source optimisée qui peut ne pas correspondre à ce que vous voyez dans vos fenêtres source.  D'autres fonctionnalités, telles que l'exécution pas à pas, peuvent ne pas se comporter comme prévu.|  
  
### Propriétés de configuration &#124; Éditeur de liens &#124; nœud Débogage  
  
|Nom de la propriété|Paramètre|  
|-------------------------|---------------|  
|**Générer des informations de débogage**|Vous devez toujours définir cette option sur **Oui \(\/DEBUG\)** pour créer les symboles et fichiers nécessaires au débogage.  Lorsque l'application passe en phase de production, vous pouvez la désactiver.|  
  
 [Dans cette rubrique](../debugger/debugging-preparation-visual-cpp-project-types.md#BKMK_In_this_topic)  
  
##  <a name="BKMK_Win32_Projects"></a> Projets Win32  
 Les applications Windows32 sont des programmes Windows traditionnels écrits en C ou C\+\+.  Le débogage de ce type d'application dans [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] est assez simple.  
  
 Les applications Win32 comprennent les applications MFC et les projets ATL.  Elles utilisent les API Windows et parfois également MFC ou ATL, mais elles n'utilisent pas le Common Language Runtime \(CLR\).  Toutefois, elles peuvent appeler du code managé qui utilise le CLR.  
  
 La procédure suivante explique comment déboguer un projet Win32 à partir de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  Une autre façon de déboguer une application Win32 consiste à démarrer l'application en dehors de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], puis de l'attacher.  Pour plus d'informations, consultez [Attacher aux processus en cours d'exécution](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).  
  
###  <a name="BKMK_To_debug_a_C_or_C___Win32_application"></a> Pour déboguer une application Win32 C ou C\+\+  
  
1.  Ouvrez le projet dans Visual Studio.  
  
2.  Dans le menu **Déboguer**, choisissez **Démarrer**.  
  
3.  Procédez au débogage à l'aide des techniques présentées dans [Principes de base du débogueur](../debugger/debugger-basics.md).  
  
###  <a name="BKMK_To_manually_set_a_Debug_configuration"></a> Pour définir manuellement une configuration Debug  
  
1.  Dans le menu **Affichage**, cliquez sur **Pages de propriétés**.  
  
2.  Cliquez sur le nœud **Propriétés de configuration** pour l'ouvrir s'il ne l'est pas déjà.  
  
3.  Sélectionnez **Général** et affectez la valeur **Debug** à la ligne **Sortie**.  
  
4.  Ouvrez le nœud **C\/C\+\+** et sélectionnez **Général**.  
  
     À la ligne **Déboguer**, spécifiez le type d'informations de débogage que le compilateur doit générer.  Vous pouvez notamment choisir **Base de données du programme \(\/Zi\)** ou **Base de données du programme pour Modifier & Continuer**.  
  
5.  Sélectionnez **Optimisation**, puis dans la ligne **Optimisation**, sélectionnez **Désactivé \(\/0d\)**  dans la liste déroulante.  
  
     Le code optimisé est plus difficile à déboguer, car les instructions générées ne correspondent pas directement à votre code source.  Si vous constatez que votre programme comporte un bogue visible uniquement dans le code optimisé, vous pouvez activer ce paramètre, mais rappelez\-vous que le code affiché dans la fenêtre Code Machine est généré à partir d'une source optimisée qui ne correspond peut\-être pas à ce que vous voyez dans vos fenêtres sources.  Certains fonctionnalités, telles que l'exécution pas à pas, peuvent afficher des points d'arrêt et un point d'exécution incorrects.  
  
6.  Ouvrez le nœud **Éditeur de liens** et sélectionnez **Débogage**.  Dans la première ligne **Générer**, sélectionnez **Oui \(\/DEBUG\)** dans la liste déroulante.  Sélectionnez toujours ce paramètre lorsque vous déboguez.  
  
 Pour plus d'informations, consultez [Paramètres de projet pour une configuration Debug C\+\+](../debugger/project-settings-for-a-cpp-debug-configuration.md).  
  
 [Dans cette rubrique](../debugger/debugging-preparation-visual-cpp-project-types.md#BKMK_In_this_topic)  
  
##  <a name="BKMK_Windows_Forms_Applications___NET_"></a> Applications Windows Forms \(.NET\)  
 Le modèle **Application Windows Forms \(.NET\)** crée une application Windows Forms [!INCLUDE[vcprvc](../debugger/includes/vcprvc_md.md)].  Pour plus d'informations, consultez [How to: Create a Windows Application Project](http://msdn.microsoft.com/fr-fr/b2f93fed-c635-4705-8d0e-cf079a264efa).  
  
 Le débogage de ce type d'application dans [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] est semblable à celui réalisé dans les applications Windows Forms managées.  
  
 Lorsque vous créez un projet Windows Forms à l'aide du modèle de projet, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] crée automatiquement les paramètres requis pour les configurations Debug et Release.  Si nécessaire, vous pouvez modifier ces paramètres dans la boîte de dialogue **Page de propriétés de \<Nom du projet\>**.  Pour plus d'informations, consultez [Configurations Debug et Release](../debugger/how-to-set-debug-and-release-configurations.md).  
  
 Pour plus d'informations, consultez [Paramètres de projet pour une configuration Debug C\+\+](../debugger/project-settings-for-a-cpp-debug-configuration.md).  
  
 Une autre façon de déboguer une application Windows Forms consiste à démarrer l'application en dehors de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] et à l'attacher à celui\-ci.  Pour plus d'informations, consultez [Attachement à un ou plusieurs programmes en cours d'exécution](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).  
  
 [Dans cette rubrique](../debugger/debugging-preparation-visual-cpp-project-types.md#BKMK_In_this_topic)  
  
## Voir aussi  
 [Principes de base du débogueur](../debugger/debugger-basics.md)   
 [Paramètres de projet pour une configuration Debug C\+\+](../debugger/project-settings-for-a-cpp-debug-configuration.md)   
 [Attachement à un ou plusieurs programmes en cours d'exécution](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)   
 [Configurations Debug et Release](../debugger/how-to-set-debug-and-release-configurations.md)   
 [How to: Create a Windows Application Project](http://msdn.microsoft.com/fr-fr/b2f93fed-c635-4705-8d0e-cf079a264efa)