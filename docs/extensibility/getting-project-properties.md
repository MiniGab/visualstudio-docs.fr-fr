---
title: Obtention des propriétés de projet | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- project properties, displaying in tool window
- tool windows, displaying project propeties
ms.assetid: 96ba07ca-0811-4013-8602-12550ac4ba79
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 58967c87b86eff8ab00e343ee872637e18ee57ed
ms.sourcegitcommit: 1c2ed640512ba613b3bbbc9ce348e28be6ca3e45
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/03/2018
ms.locfileid: "39497753"
---
# <a name="get-project-properties"></a>Obtenir les propriétés du projet
Cette procédure pas à pas montre comment affiche les propriétés de projet dans une fenêtre outil.  
  
## <a name="prerequisites"></a>Prérequis  
 À partir de Visual Studio 2015, vous n’installez pas le Kit de développement logiciel Visual Studio à partir du centre de téléchargement. Il est inclus comme fonctionnalité facultative dans le programme d’installation de Visual Studio. Vous pouvez également installer le kit SDK VS par la suite. Pour plus d’informations, consultez [installer le SDK Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
### <a name="to-create-a-vsix-project-and-add-a-tool-window"></a>Pour créer un projet VSIX et ajouter une fenêtre outil  
  
1.  Chaque extension de Visual Studio commence par un projet de déploiement VSIX qui contiendra les ressources de l’extension. Créer un [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] projet VSIX nommé `ProjectPropertiesExtension`. Vous pouvez trouver le modèle de projet VSIX dans le **nouveau projet** boîte de dialogue sous **Visual C#** > **extensibilité**.  
  
2.  Ajouter une fenêtre outil en ajoutant un modèle d’élément de fenêtre d’outil personnalisé nommé `ProjectPropertiesToolWindow`. Dans le **l’Explorateur de solutions**, cliquez sur le nœud du projet et sélectionnez **ajouter** > **un nouvel élément**. Dans le **boîte de dialogue Ajouter un nouvel élément**, accédez à **éléments Visual c#** > **extensibilité** et sélectionnez **fenêtre d’outil personnalisé**. Dans le **nom** en bas de la boîte de dialogue, modifiez le nom de fichier à `ProjectPropertiesToolWindow.cs`. Pour plus d’informations sur la création d’une fenêtre Outil personnalisée, consultez [créer une extension avec une fenêtre outil](../extensibility/creating-an-extension-with-a-tool-window.md).  
  
3.  Générez la solution et vérifiez qu’elle est compilée sans erreur.  
  
### <a name="to-display-project-properties-in-a-tool-window"></a>Pour afficher les propriétés de projet dans une fenêtre outil  
  
1.  Dans le fichier ProjectPropertiesToolWindowCommand.cs, ajoutez le code suivant à l’aide d’instructions.  
  
    ```csharp  
    using EnvDTE;  
    using System.Windows.Controls;  
  
    ```  
  
2.  Dans *ProjectPropertiesToolWindowControl.xaml*, supprimez le bouton existant et ajouter un contrôle TreeView de la boîte à outils. Vous pouvez également supprimer le Gestionnaire d’événements click à partir de la *ProjectPropertiesToolWindowControl.xaml.cs* fichier.  
  
3.  Dans *ProjectPropertiesToolWindowCommand.cs*, utilisez le `ShowToolWindow()` méthode pour ouvrir le projet et lire ses propriétés, puis ajoutez les propriétés pour le contrôle TreeView. Le code pour ShowToolWindow doit se présenter comme suit :  
  
    ```csharp  
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
  
6.  Dans le **vue** > **Windows autres** cliquez sur **ProjectPropertiesToolWindow**.  
  
     Vous devriez voir le contrôle d’arborescence dans la fenêtre outil avec le nom du premier projet et de toutes ses propriétés de projet.