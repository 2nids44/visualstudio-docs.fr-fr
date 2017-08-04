---
title: "Obtention des propriétés du projet | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- project properties, displaying in tool window
- tool windows, displaying project propeties
ms.assetid: 96ba07ca-0811-4013-8602-12550ac4ba79
caps.latest.revision: 29
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 09a811a3bb42f5de9406ec85038579b5545619ae
ms.lasthandoff: 02/22/2017

---
# <a name="getting-project-properties"></a>Obtention des propriétés de projet
Cette procédure pas à pas montre comment les propriétés du projet s’affiche dans une fenêtre outil.  
  
## <a name="prerequisites"></a>Conditions préalables  
 À partir de Visual Studio 2015, vous n’installez pas Visual Studio SDK à partir du centre de téléchargement. Il est inclus comme fonctionnalité facultative dans le programme d’installation de Visual Studio. Vous pouvez également installer le Kit de développement logiciel Visual Studio plus tard. Pour plus d’informations, consultez [l’installation du Kit de développement logiciel Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
### <a name="to-create-a-vsix-project-and-add-a-tool-window"></a>Pour créer un projet VSIX et ajouter une fenêtre outil  
  
1.  Chaque extension de Visual Studio démarre avec un projet de déploiement VSIX qui contient les composants d’extension. Créer un [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] projet VSIX nommé `ProjectPropertiesExtension`. Vous pouvez trouver le modèle de projet VSIX dans le **nouveau projet** boîte de dialogue sous **Visual C# / extensibilité**.  
  
2.  Ajouter une fenêtre outil en ajoutant un modèle d’élément de fenêtre de l’outil personnalisé nommé `ProjectPropertiesToolWindow`. Dans le **l’Explorateur de solutions**, cliquez sur le nœud du projet et sélectionnez **Ajouter / nouvel élément**. Dans le **boîte de dialogue Ajouter un nouvel élément**, accédez à **éléments Visual C# / extensibilité** et sélectionnez **fenêtre de l’outil personnalisé**. Dans le **nom** en bas de la boîte de dialogue, modifiez le nom du fichier à `ProjectPropertiesToolWindow.cs`. Pour plus d’informations sur la création d’une fenêtre Outil personnalisée, consultez [création d’une Extension avec une fenêtre outil](../extensibility/creating-an-extension-with-a-tool-window.md).  
  
3.  Générez la solution et vérifiez qu’elle est compilée sans erreur.  
  
### <a name="to-display-project-properties-in-a-tool-window"></a>Pour afficher les propriétés de projet dans une fenêtre outil  
  
1.  Dans le fichier ProjectPropertiesToolWindowCommand.cs, ajoutez le code suivant à l’aide d’instructions.  
  
    ```c#  
    using EnvDTE;  
    using System.Windows.Controls;  
  
    ```  
  
2.  Dans ProjectPropertiesToolWindowControl.xaml, supprimer du bouton existant et ajouter un contrôle TreeView de la boîte à outils. Vous pouvez également supprimer le Gestionnaire d’événements click à partir du fichier ProjectPropertiesToolWindowControl.xaml.cs.  
  
3.  Dans ProjectPropertiesToolWindowCommand.cs, utilisez la méthode ShowToolWindow() pour ouvrir le projet et lire ses propriétés, puis ajoutez les propriétés pour le contrôle TreeView. Le code de ShowToolWindow doit se présenter comme suit :  
  
    ```c#  
    private void ShowToolWindow(object sender, EventArgs e)  
    {  
        ToolWindowPane window = this.package.FindToolWindow(typeof(ProjectPropertiesToolWindow), 0, true);  
        if ((null == window) || (null == window.Frame))  
        {  
            throw new NotSupportedException("Cannot create window.");  
        }  
        IVsWindowFrame windowFrame = (IVsWindowFrame)window.Frame;  
        Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure(windowFrame.Show());  
  
        // Get the tree view and populate it if there is a project open.  
        ProjectPropertiesToolWindowControl control = (ProjectPropertiesToolWindowControl)window.Content;  
        TreeView treeView = control.treeView;  
  
        // Reset the TreeView to 0 items.  
        treeView.Items.Clear();  
  
        DTE dte = (DTE)this.ServiceProvider.GetService(typeof(DTE));  
        Projects projects = dte.Solution.Projects;  
        if (projects.Count == 0)   // no project is open  
        {  
            TreeViewItem item = new TreeViewItem();  
            item.Name = "Projects";  
            item.ItemsSource = new string[]{ "no projects are open." };  
            item.IsExpanded = true;  
            treeView.Items.Add(item);  
            return;  
        }  
  
        Project project = projects.Item(1);  
        TreeViewItem item1 = new TreeViewItem();  
        item1.Header = project.Name + "Properties";  
        treeView.Items.Add(item1);  
  
        foreach (Property property in project.Properties)  
        {  
            TreeViewItem item = new TreeViewItem();  
            item.ItemsSource = new string[] { property.Name };  
            item.IsExpanded = true;  
            treeView.Items.Add(item);  
        }  
    }  
    ```  
  
4.  Générez le projet et commencez le débogage. L’instance expérimentale doit apparaître.  
  
5.  Dans l’instance expérimentale, ouvrez un projet.  
  
6.  Dans le **affichage / autres fenêtres** cliquez sur **ProjectPropertiesToolWindow**.  
  
     Vous devez voir le contrôle d’arborescence dans la fenêtre outil, ainsi que le nom du premier projet et de toutes ses propriétés de projet.