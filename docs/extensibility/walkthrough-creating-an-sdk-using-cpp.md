---
title: 'Procédure pas à pas : Création d’un kit de développement à l’aide de C++ | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: 36ea793b-3832-41a1-b906-69e680ad5e1d
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: c320400ee7337ec3f4ac3b6a77f1863b732c99c5
ms.sourcegitcommit: 1c2ed640512ba613b3bbbc9ce348e28be6ca3e45
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/03/2018
ms.locfileid: "39499963"
---
# <a name="walkthrough-create-an-sdk-using-c"></a>Procédure pas à pas : Créer un kit de développement à l’aide de C++
Cette procédure pas à pas montre comment créer une bibliothèque C++ native mathématiques SDK, package le Kit de développement logiciel comme un Visual Studio Extension (VSIX) et ensuite l’utiliser pour créer une application. La procédure pas à pas est divisée en ces étapes :  
  
-   [Pour créer le natif et les bibliothèques Windows Runtime](../extensibility/walkthrough-creating-an-sdk-using-cpp.md#createClassLibrary)  
  
-   [Pour créer le projet d’extension NativeMathVSIX](../extensibility/walkthrough-creating-an-sdk-using-cpp.md#createVSIX)  
  
-   [Pour créer un exemple d’application qui utilise la bibliothèque de classes](../extensibility/walkthrough-creating-an-sdk-using-cpp.md#createSample)  
  
## <a name="prerequisites"></a>Prérequis  
 Pour suivre cette procédure pas à pas, vous devez installer le Kit de développement logiciel (SDK) Visual Studio. Pour plus d’informations, consultez [Visual Studio SDK](../extensibility/visual-studio-sdk.md).  
  
##  <a name="createClassLibrary"></a> Pour créer le natif et les bibliothèques Windows Runtime  
  
1.  Dans la barre de menus, choisissez **Fichier** > **Nouveau** > **Projet**.  
  
2.  Dans la liste des modèles, développez **Visual C++** > **Windows universel**, puis sélectionnez le **DLL (applications Windows universelles)** modèle. Dans le **nom** , spécifiez `NativeMath`, puis choisissez le **OK** bouton.  
  
3.  Mise à jour *NativeMath.h* pour faire correspondre le code suivant.  
  
     [!code-cpp[CreatingAnSDKUsingCpp#1](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_1.h)]  
  
4.  Mise à jour *NativeMath.cpp* pour correspondre à ce code :  
  
     [!code-cpp[CreatingAnSDKUsingCpp#2](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_2.cpp)]  
  
5.  Dans **l’Explorateur de solutions**, ouvrez le menu contextuel pour **Solution 'NativeMath'**, puis choisissez **ajouter** > **nouveau projet**.  
  
6.  Dans la liste des modèles, développez **Visual C++**, puis sélectionnez le **composant d’exécution Windows** modèle. Dans le **nom** , spécifiez `NativeMathWRT`, puis choisissez le **OK** bouton.  
  
7.  Mise à jour *Class1.h* pour correspondre à ce code :  
  
     [!code-cpp[CreatingAnSDKUsingCpp#3](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_3.h)]  
  
8.  Mise à jour *Class1.cpp* pour correspondre à ce code :  
  
     [!code-cpp[CreatingAnSDKUsingCpp#4](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_4.cpp)]  
  
9. Dans la barre de menus, choisissez **Générer**  >  **Générer la solution**.  
  
##  <a name="createVSIX"></a> Pour créer le projet d’extension NativeMathVSIX  
  
1.  Dans **l’Explorateur de solutions**, ouvrez le menu contextuel pour **Solution 'NativeMath'**, puis choisissez **ajouter** > **nouveau projet**.  
  
2.  Dans la liste des modèles, développez **Visual C#** > **extensibilité**, puis sélectionnez **projet VSIX**. Dans le **nom** , spécifiez **NativeMathVSIX**, puis choisissez le **OK** bouton.
  
3.  Dans **l’Explorateur de solutions**, ouvrez le menu contextuel pour **source.extension.vsixmanifest**, puis choisissez **afficher le Code**.  
  
4.  Utilisez le code XML suivant pour remplacer le document XML.  
  
    [!code-xml[CreatingAnSDKUsingCpp#6](../extensibility/codesnippet/XML/walkthrough-creating-an-sdk-using-cpp_6.xml)]

5.  Dans **l’Explorateur de solutions**, ouvrez le menu contextuel pour le **NativeMathVSIX** de projet, puis choisissez **ajouter** > **unnouvelélément**.  
  
6.  Dans la liste des **éléments Visual c#**, développez **données**, puis sélectionnez **fichier XML**. Dans le **nom** , spécifiez `SDKManifest.xml`, puis choisissez le **OK** bouton.  
  
7.  Utilisez le code XML pour remplacer le contenu du fichier :  
  
     [!code-xml[CreatingAnSDKUsingCpp#5](../extensibility/codesnippet/XML/walkthrough-creating-an-sdk-using-cpp_5.xml)]  
  
8. Dans **l’Explorateur de solutions**, sous le **NativeMathVSIX** projet d’équipe, de créer cette structure de dossiers :  
  
    ```xml  
    \DesignTime  
          \CommonConfiguration  
                \Neutral  
                      \Include  
          \Debug  
                \x86  
    \Redist  
          \Debug  
                \x86  
    \References  
          \CommonConfiguration  
                \Neutral  
    ```  
  
9. Dans **l’Explorateur de solutions**, ouvrez le menu contextuel pour **Solution 'NativeMath'**, puis choisissez **ouvrir le dossier dans l’Explorateur de fichiers**.  
  
10. Dans **Explorateur de fichiers**, copie *$SolutionRoot$\NativeMath\NativeMath.h*, puis dans **l’Explorateur de solutions**, sous le **NativeMathVSIX**project, collez-le dans le *$SolutionRoot$ \NativeMathVSIX\DesignTime\CommonConfiguration\Neutral\Include\\*  dossier.  
  
     Copie *$SolutionRoot$\Debug\NativeMath\NativeMath.lib*, puis collez-la dans la *$SolutionRoot$ \NativeMathVSIX\DesignTime\Debug\x86\\*  dossier.  
  
     Copie *$SolutionRoot$\Debug\NativeMath\NativeMath.dll* et collez-la dans la *$SolutionRoot$ \NativeMathVSIX\Redist\Debug\x86\\*  dossier.  
  
     Copie *$SolutionRoot$\Debug\NativeMathWRT\NativeMathWRT.dll* et collez-la dans la *$SolutionRoot$ \NativeMathVSIX\Redist\Debug\x86* dossier.  
     Copie *$SolutionRoot$\Debug\NativeMathWRT\NativeMathWRT.winmd* et collez-la dans la *$SolutionRoot$ \NativeMathVSIX\References\CommonConfiguration\Neutral* dossier.  
  
     Copie *$SolutionRoot$\Debug\NativeMathWRT\NativeMathWRT.pri* et collez-la dans la *$SolutionRoot$ \NativeMathVSIX\References\CommonConfiguration\Neutral* dossier.  
  
11. Dans le *$SolutionRoot$ \NativeMathVSIX\DesignTime\Debug\x86\\*  dossier, créez un fichier texte nommé *NativeMathSDK.props*, puis collez le contenu suivant dans celui-ci :  
  
    [!code-xml[CreatingAnSDKUsingCpp#7](../extensibility/codesnippet/XML/walkthrough-creating-an-sdk-using-cpp_7.xml)]  
  
12. Dans la barre de menus, choisissez **vue** > **Windows autres** > **fenêtre Propriétés** (clavier : choisissez le **F4**clé).  
  
13. Dans **l’Explorateur de solutions**, sélectionnez le **NativeMathWRT.winmd** fichier. Dans le **propriétés** fenêtre, la modification la **Action de génération** propriété **contenu**, puis modifiez le **inclure dans VSIX** propriété  **True**.  
  
     Répétez ce processus pour le **NativeMath.h** fichier.  
  
     Répétez ce processus pour le **NativeMathWRT.pri** fichier.  
  
     Répétez ce processus pour le **NativeMath.Lib** fichier.  
  
     Répétez ce processus pour le **NativeMathSDK.props** fichier.  
  
14. Dans **l’Explorateur de solutions**, sélectionnez le **NativeMath.h** fichier. Dans le **propriétés** fenêtre, de modifier le **inclure dans VSIX** propriété **True**.  
  
     Répétez ce processus pour le **NativeMath.dll** fichier.  
  
     Répétez ce processus pour le **NativeMathWRT.dll** fichier.  
  
     Répétez ce processus pour le **SDKManifest.xml** fichier.  
  
15. Dans la barre de menus, choisissez **Générer**  >  **Générer la solution**.  
  
16. Dans **l’Explorateur de solutions**, ouvrez le menu contextuel pour le **NativeMathVSIX** de projet, puis choisissez **ouvrir le dossier dans l’Explorateur de fichiers**.  
  
17. Dans **Explorateur de fichiers**, accédez à la *$SolutionRoot$ \NativeMathVSIX\bin\Debug* dossier, puis exécutez *NativeMathVSIX.vsix* pour commencer l’installation.  
  
18. Choisissez le **installer** bouton, attendez que l’installation se termine, puis démarrez Visual Studio.  
  
##  <a name="createSample"></a> Pour créer un exemple d’application qui utilise la bibliothèque de classes  
  
1.  Dans la barre de menus, choisissez **Fichier** > **Nouveau** > **Projet**.  
  
2.  Dans la liste des modèles, développez **Visual C++** > **Windows universel** , puis sélectionnez **application vide**. Dans le **nom** , spécifiez **NativeMathSDKSample**, puis choisissez le **OK** bouton.  
  
3.  Dans **l’Explorateur de solutions**, ouvrez le menu contextuel pour le **NativeMathSDKSample** de projet, puis choisissez **ajouter** > **référence**.  
  
4.  Dans le **ajouter une référence** boîte de dialogue, dans la liste des types référence, développez **Windows universel**, puis sélectionnez **Extensions**. Enfin, sélectionnez le **natif mathématiques SDK** case à cocher, puis choisissez le **OK** bouton.
  
5.  Afficher les propriétés du projet pour NativeMathSDKSample.  
  
     Les propriétés que vous avez défini dans *NativeMathSDK.props* ont été appliqués lors de l’ajout de la référence. Vous pouvez vérifier les propriétés ont été appliquées en examinant le **répertoires VC ++** propriété du projet **propriétés de Configuration**.  
  
6.  Dans **l’Explorateur de solutions**, ouvrez **MainPage.xaml**, puis utilisez le XAML suivant pour remplacer son contenu :  
  
     [!code-xml[CreatingAnSDKUsingCppDemoApp#1](../extensibility/codesnippet/Xaml/walkthrough-creating-an-sdk-using-cpp_8.xaml)]  
  
7.  Mise à jour *Mainpage.xaml.h* pour correspondre à ce code :  
  
     [!code-cpp[CreatingAnSDKUsingCppDemoApp#2](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_9.h)]  
  
8. Mise à jour *MainPage.xaml.cpp* pour correspondre à ce code :  
  
     [!code-cpp[CreatingAnSDKUsingCppDemoApp#3](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_10.cpp)]  
  
9. Choisissez le **F5** touche pour exécuter l’application.  
  
10. Dans l’application, entrez tous les deux nombres, sélectionnez une opération, puis choisissez le **=** bouton.  
  
     Le résultat correct apparaît.  
  
 Cette procédure pas à pas vous a montré comment créer et utiliser un SDK d’Extension pour appeler un [!INCLUDE[wrt](../extensibility/includes/wrt_md.md)] bibliothèque et non -[!INCLUDE[wrt](../extensibility/includes/wrt_md.md)] bibliothèque.  
  
## <a name="next-steps"></a>Étapes suivantes  
  
## <a name="see-also"></a>Voir aussi  
 [Procédure pas à pas : Créer un kit de développement à l’aide de c# ou Visual Basic](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md)   
 [Création d’un kit de développement logiciel](../extensibility/creating-a-software-development-kit.md)
