---
title: Page Application, Concepteur de projet (Visual Basic)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- vb.ProjectPropertiesApplicationWPF
- vb.ProjectPropertiesApplication
helpviewer_keywords:
- Project Designer, Application page
- Application page in Project Designer
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 62cbae6115b8268adbb1e2f9d6c27df8bf94a28b
ms.sourcegitcommit: c57ae28181ffe14a30731736661bf59c3eff1211
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/11/2018
ms.locfileid: "38800731"
---
# <a name="application-page-project-designer-visual-basic"></a>Page Application, Concepteur de projet (Visual Basic)

Utilisez la page **Application** du Concepteur de projet pour spécifier les paramètres d’application et les propriétés du projet.

Pour accéder à la page **Application**, choisissez un nœud de projet (pas le nœud **Solution**) dans l’**Explorateur de solutions**. Ensuite, choisissez **Projet** > **Propriétés** dans la barre de menus. À l’affichage du Concepteur de projet, sélectionnez l’onglet **Application**.

[!INCLUDE[note_settings_general](../../data-tools/includes/note_settings_general_md.md)]

## <a name="general-application-settings"></a>Paramètres d’application généraux

Les options suivantes permettent de configurer les paramètres généraux d’une application.

### <a name="assembly-name"></a>Nom de l'assembly

Spécifie le nom du fichier de sortie qui contient le manifeste de l’assembly. La modification de cette propriété modifie également la propriété **Nom de sortie**. Vous pouvez aussi spécifier le nom du fichier de sortie dans une invite de commandes, à l’aide du commutateur de compilateur [/out (Visual Basic)](/dotnet/visual-basic/reference/command-line-compiler/out). Pour plus d’informations sur la façon d’accéder à cette propriété par programmation, consultez <xref:VSLangProj.ProjectProperties.AssemblyName%2A>.

### <a name="root-namespace"></a>Espace de noms racine

Spécifie l’espace de noms de base pour tous les fichiers du projet. Par exemple, si vous définissez l’**espace de noms racine** sur `Project1` et que vous avez un `Class1` en dehors des espaces de noms dans votre code, son espace de noms est `Project1.Class1`. Si vous avez un `Class2` dans un espace de noms `Order` dans le code, son espace de noms est `Project1.Order.Class2`.

Si vous effacez l’**espace de noms racine**, vous pouvez spécifier la structure de l’espace de noms de votre projet dans le code.

> [!NOTE]
> Si vous utilisez le mot clé Global dans une [instruction Namespace](/dotnet/visual-basic/language-reference/statements/namespace-statement), vous pouvez définir un espace de noms en dehors de l’espace de noms racine de votre projet. Si vous effacez l’**espace de noms racine**, `Global` devient l’espace de noms de niveau supérieur et vous n’avez plus besoin du mot clé `Global` dans une instruction `Namespace`. Pour plus d’informations, consultez « Mot clé Global dans les instructions Namespace » dans [Espaces de noms dans Visual Basic](/dotnet/visual-basic/programming-guide/program-structure/namespaces).

Pour plus d’informations sur la création d’espaces de noms dans votre code, consultez [Instruction Namespace](/dotnet/visual-basic/language-reference/statements/namespace-statement).

Pour plus d’informations sur la propriété d’espace de noms racine, consultez [/rootnamespace](/dotnet/visual-basic/reference/command-line-compiler/rootnamespace).

Pour plus d’informations sur la façon d’accéder à cette propriété par programmation, consultez <xref:VSLangProj.ProjectProperties.RootNamespace%2A>.

### <a name="target-framework-all-configurations"></a>Version cible de .NET Framework (toutes les configurations)

Spécifie la version du .NET Framework ciblée par l’application. Cette option peut avoir des valeurs différentes selon les versions du .NET Framework installées sur votre ordinateur.

Par défaut, la valeur est le framework cible que vous avez spécifié dans la boîte de dialogue **Nouveau projet**.

> [!NOTE]
> Les packages de prérequis répertoriés dans la [boîte de dialogue Composants requis](../../ide/reference/prerequisites-dialog-box.md) sont définis automatiquement la première fois que vous ouvrez la boîte de dialogue. Si vous modifiez par la suite le framework cible du projet, vous devez spécifier manuellement les prérequis pour qu’ils correspondent au nouveau framework cible.

Pour plus d’informations, consultez [Guide pratique pour cibler une version du .NET Framework](../../ide/how-to-target-a-version-of-the-dotnet-framework.md) et [Présentation du multiciblage Visual Studio](../../ide/visual-studio-multi-targeting-overview.md).

### <a name="application-type"></a>Type d'application

Spécifie le type d’application à générer. Pour les applications Windows 8.x, vous pouvez spécifier **Application du Windows Store**, **Bibliothèque de classes** ou **Fichier WinMD**. Pour la plupart des autres types d’applications, vous pouvez spécifier **Application Windows**, **Application console**, **Bibliothèque de classes**, **Service Windows** ou **Bibliothèque de contrôles web**.

Pour un projet d’application web, vous devez spécifier **Bibliothèque de classes**.

Si vous spécifiez l’option **Fichier WinMD**, les types peuvent être projetés dans n’importe quel langage de programmation de Windows Runtime. En plaçant la sortie du projet dans un fichier WinMD, vous pouvez coder une application dans plusieurs langages et faire interagir le code comme si vous l’aviez écrit dans le même langage. Vous pouvez utiliser l’option **Fichier WinMD** pour les solutions qui ciblent les bibliothèques Windows Runtime, y compris les applications [!INCLUDE[win8_appname_long](../../debugger/includes/win8_appname_long_md.md)]. Pour plus d’informations, consultez [Création de composants Windows Runtime en C# et Visual Basic](/windows/uwp/winrt-components/creating-windows-runtime-components-in-csharp-and-visual-basic).

> [!NOTE]
> Le Windows Runtime peut projeter des types pour qu’ils apparaissent comme des objets natifs dans le langage qui les utilise. Par exemple, les applications JavaScript qui interagissent avec Windows Runtime l’utilisent comme un ensemble d’objets JavaScript, et les applications C# utilisent la bibliothèque comme une collection d’objets .NET. En plaçant la sortie du projet dans un fichier WinMD, vous tirez parti de la même technologie que celle utilisée par Windows Runtime.

Pour plus d’informations sur la propriété **Type d’application**, consultez [/target (Visual Basic)](/dotnet/visual-basic/reference/command-line-compiler/target). Pour plus d’informations sur la façon d’accéder à cette propriété par programmation, consultez <xref:VSLangProj.ProjectProperties.OutputType%2A>.

### <a name="icon"></a>Icône

Définit le fichier .ico à utiliser comme icône de votre programme. Sélectionnez **\<Parcourir...>** pour rechercher un graphique existant. Pour plus d’informations, consultez [/win32icon](/dotnet/visual-basic/reference/command-line-compiler/win32icon) (ou [/win32icon (Options du compilateur C#)](/dotnet/csharp/language-reference/compiler-options/win32icon-compiler-option). Pour accéder à cette propriété par programmation, consultez <xref:VSLangProj.ProjectProperties.ApplicationIcon%2A>.

### <a name="startup-form--startup-object--startup-uri"></a>Formulaire de démarrage / Objet de démarrage / URI de démarrage

Spécifie le formulaire de démarrage ou le point d’entrée de l’application.

Si **Activer l’infrastructure de l’application** est sélectionné (par défaut), cette liste est intitulée **Formulaire de démarrage** et affiche uniquement des formulaires, car le framework d’application ne prend en charge que les formulaires de démarrage, et non les objets.

Si le projet est une application de navigateur WPF, cette liste est intitulée **URI de démarrage** et la valeur par défaut est **Page1.xaml**. La liste **URI de démarrage** permet de spécifier la ressource d’interface utilisateur (un élément XAML) que l’application affiche au démarrage. Pour plus d'informations, consultez <xref:System.Windows.Application.StartupUri%2A>.

Si **Activer l’infrastructure de l’application** n’est pas sélectionné, cette liste devient **Objet de démarrage**, et affiche des formulaires et des classes ou des modules avec un `Sub Main`.

L’**objet de démarrage** définit le point d’entrée à appeler quand l’application se charge. Cet objet est généralement défini sur le formulaire principal de votre application ou sur la procédure `Sub Main` qui s’exécute quand l’application démarre. Comme les bibliothèques de classes n’ont pas de point d’entrée, la seule option disponible pour cette propriété est **(Aucun)**. Pour plus d’informations, consultez [/main](/dotnet/visual-basic/reference/command-line-compiler/main). Pour accéder à cette propriété par programmation, consultez <xref:VSLangProj.ProjectProperties.StartupObject%2A>.

### <a name="assembly-information"></a>Informations de l’assembly

Cliquez sur ce bouton pour afficher la [boîte de dialogue Informations de l’assembly](../../ide/reference/assembly-information-dialog-box.md).

### <a name="enable-application-framework"></a>Activer l’infrastructure d’application

Spécifie si un projet utilise le framework d’application. Le paramètre de cette option affecte les options disponibles dans **Formulaire de démarrage**/**Objet de démarrage**.

Si cette case est cochée, votre application utilise le `Sub Main` standard. En cochant cette case, vous activez les fonctionnalités de la section **Propriétés de l’infrastructure d’application Windows** et vous êtes invité à sélectionner un formulaire de démarrage.

Si cette case est décochée, votre application utilise le `Sub Main` personnalisé que vous avez spécifié dans le **Formulaire de démarrage**. Dans ce cas, vous pouvez spécifier un objet de démarrage (un `Sub Main` personnalisé dans une méthode ou une classe) ou un formulaire. Par ailleurs, les options de la section **Propriétés de l’infrastructure d’application Windows** deviennent indisponibles.

### <a name="view-windows-settings"></a>Afficher les paramètres Windows

Cliquez sur ce bouton pour générer et ouvrir le fichier app.manifest. Visual Studio utilise ce fichier pour générer des données de manifeste pour l’application. Ensuite, définissez le niveau d’exécution demandé par le contrôle de compte d’utilisateur en modifiant la balise `<requestedExecutionLevel>` dans app.manifest comme suit :

`<requestedExecutionLevel level="asInvoker" />`

ClickOnce fonctionne avec le niveau `asInvoker` ou en mode virtualisé (aucune génération de manifeste). Pour spécifier le mode virtualisé, supprimez l’intégralité de la balise dans app.manifest.

Pour plus d’informations sur la génération du manifeste, consultez [Déploiement ClickOnce sur Windows Vista](../../deployment/clickonce-deployment-on-windows-vista.md).

## <a name="windows-application-framework-properties"></a>Propriétés de l’infrastructure d’application Windows

Les paramètres suivants sont disponibles dans la section **Propriétés de l’infrastructure d’application Windows**. Ces options sont disponibles uniquement si la case **Activer l’infrastructure de l’application** est cochée. La section suivante décrit les paramètres des **Propriétés de l’infrastructure d’application Windows** pour les applications Windows Presentation Foundation (WPF).

### <a name="enable-xp-visual-styles"></a>Activer les styles visuels XP

Active ou désactive les styles visuels Windows XP, également appelés *Thèmes Windows XP*. Les styles visuels Windows XP activent, par exemple, les contrôles avec des angles arrondis et des couleurs dynamiques. Les styles sont activés par défaut.

### <a name="make-single-instance-application"></a>Créer une application à instance unique

Cochez cette case pour empêcher les utilisateurs d’exécuter plusieurs instances de l’application. Le paramètre par défaut de cette case à cocher est *désactivé*, ce qui permet à plusieurs instances de l’application de s’exécuter. Pour plus d'informations, consultez l'événement <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.StartupNextInstance>.

### <a name="save-mysettings-on-shutdown"></a>Enregistrer My.Settings à l’arrêt

Cochez cette case pour spécifier que les paramètres `My.Settings` de l’application sont enregistrés quand les utilisateurs éteignent leur ordinateur. La case est cochée par défaut. Si cette option est désactivée, vous pouvez enregistrer manuellement les paramètres de l’application en appelant `My.Settings.Save`.

### <a name="authentication-mode"></a>Mode d’authentification

Sélectionnez **Windows** (la valeur par défaut) pour spécifier l’utilisation de l’authentification Windows afin d’identifier l’utilisateur actuellement connecté. Vous pouvez récupérer ces informations au moment de l’exécution à l’aide de l’objet `My.User`. Sélectionnez **Défini par l’application** si vous fournissez votre propre code pour authentifier les utilisateurs au lieu d’utiliser les méthodes d’authentification Windows par défaut.

### <a name="shutdown-mode"></a>Mode d’arrêt

Sélectionnez **À la fermeture du formulaire de démarrage** (valeur par défaut) pour spécifier que l’application doit se fermer à la fermeture du formulaire de démarrage défini, même si d’autres formulaires sont ouverts. Sélectionnez **À la fermeture du dernier formulaire** pour spécifier que l’application doit se fermer à la fermeture du dernier formulaire, ou quand `My.Application.Exit` ou l’instruction `End` est explicitement appelée.

Sélectionnez **Lors de l’arrêt explicite** pour spécifier que l’application doit se fermer quand vous appelez explicitement `Shutdown`.

Sélectionnez **Lors de la fermeture de la dernière fenêtre** pour spécifier que l’application doit se fermer à la fermeture de la dernière fenêtre ou quand vous appelez explicitement `Shutdown`. Il s'agit du paramètre par défaut.

Sélectionnez **Lors de la fermeture de la fenêtre principale** pour spécifier que l’application doit se fermer à la fermeture de la fenêtre principale ou quand vous appelez explicitement `Shutdown`.

### <a name="splash-screen"></a>Écran de démarrage

Sélectionnez le formulaire à utiliser comme écran de démarrage. Vous devez déjà avoir créé un écran de démarrage à l’aide d’un formulaire ou d’un modèle. La valeur par défaut est **(Aucun)**.

### <a name="view-application-events"></a>Afficher les événements de l’application

Cliquez sur ce bouton pour afficher un fichier de code d’événements dans lequel vous pouvez écrire des événements du framework d’application `Startup`, `Shutdown`, `UnhandledException`, `StartupNextInstance` et `NetworkAvailabilityChanged`. Vous pouvez également remplacer certaines méthodes du framework d’application. Par exemple, vous pouvez modifier le comportement d’affichage de l’écran de démarrage en remplaçant `OnInitialize`.

## <a name="windows-application-framework-properties-for-windows-presentation-foundation-wpf-applications"></a>Propriétés de l’infrastructure d’application Windows pour les applications Windows Presentation Foundation (WPF)

Les paramètres suivants sont disponibles dans la section **Propriétés de l’infrastructure d’application Windows** quand le projet est une application Windows Presentation Foundation. Ces options sont disponibles uniquement si la case **Activer l’infrastructure de l’application** est cochée. Les options répertoriées dans ce tableau sont disponibles uniquement pour les applications WPF ou les applications de navigateur WPF. Elles ne sont pas disponibles pour les bibliothèques de contrôles personnalisés ou de contrôles utilisateur WPF.

### <a name="shutdown-mode"></a>Mode d’arrêt

Cette propriété s’applique uniquement aux applications Windows Presentation Foundation.

Sélectionnez **Lors de l’arrêt explicite** pour spécifier que l’application doit se fermer quand vous appelez explicitement <xref:System.Windows.Application.Shutdown%2A>.

Sélectionnez **Lors de la fermeture de la dernière fenêtre** pour spécifier que l’application doit se fermer à la fermeture de la dernière fenêtre ou quand vous appelez explicitement <xref:System.Windows.Application.Shutdown%2A>. Il s'agit du paramètre par défaut.

Sélectionnez **Lors de la fermeture de la fenêtre principale** pour spécifier que l’application doit se fermer à la fermeture de la fenêtre principale ou quand vous appelez explicitement <xref:System.Windows.Application.Shutdown%2A>.

Pour plus d’informations sur l’utilisation de ce paramètre, consultez <xref:System.Windows.Application.Shutdown%2A>

### <a name="edit-xaml"></a>Modifier XAML

Cliquez sur ce bouton pour ouvrir et modifier le fichier de définition d’application (Application.xaml) dans l’éditeur XAML. Quand vous cliquez sur ce bouton, Application.xaml s’ouvre au niveau du nœud de définition de l’application. Vous devez peut-être modifier ce fichier pour effectuer certaines tâches, comme la définition des ressources. Si le fichier de définition d’application n’existe pas, le Concepteur de projet en crée un.

### <a name="view-application-events"></a>Afficher les événements de l’application

Cliquez sur ce bouton pour afficher le fichier de classe partielle `Application` (Application.xaml.vb) dans un éditeur de code. Si le fichier n’existe pas, le Concepteur de projet en crée un avec le nom de classe et l’espace de noms appropriés.

L’objet <xref:System.Windows.Application> déclenche des événements quand certaines modifications de l’état de l’application se produisent (par exemple, au démarrage ou à l’arrêt de l’application). Pour obtenir la liste complète des événements exposés par cette classe, consultez <xref:System.Windows.Application>. Ces événements sont traités dans la section de code utilisateur de la classe partielle `Application`.