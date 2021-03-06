---
title: Contextes de fichier d’espace de travail dans Visual Studio | Documents Microsoft
ms.custom: ''
ms.date: 02/21/2018
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: 7aaa0e65-f492-49ea-a845-35bd14910ca7
author: vukelich
ms.author: svukel
manager: viveis
ms.workload:
- vssdk
ms.openlocfilehash: cdb013bb10c72041b03fce43e115806ecb3faeac
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31146349"
---
# <a name="workspace-file-contexts"></a>Contextes de fichier d’espace de travail

Toutes les analyses en [ouvrir le dossier](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md) espaces de travail sont produites par des « fichier contexte fournisseurs » qui implémentent la <xref:Microsoft.VisualStudio.Workspace.IFileContextProvider> interface. Ces extensions peuvent rechercher des séquences dans les dossiers ou fichiers, lire les fichiers de MSBuild et makefiles, détectent les dépendances du package, etc. afin de s’accumuler les analyses, qu'ils ont besoin de définir un contexte de fichier. Un contexte de fichier par lui-même n’effectue aucune action, mais fournit une autre extension pouvez ensuite agir sur les données.

Chaque <xref:Microsoft.VisualStudio.Workspace.FileContext> a un `Guid` associé qui identifie le type de données qu’il exécute. Un espace de travail utilise cette `Guid` ultérieurement pour associer les extensions qui consomment les données via le <xref:Microsoft.VisualStudio.Workspace.FileContext.Context> propriété. Un fournisseur de contexte du fichier exporté avec les métadonnées qui identifie le contexte du fichier `Guid`s’il peut produire des données pour.

Une fois défini, un contexte de fichier peut être associé à n’importe quel nombre de fichiers ou dossiers dans l’espace de travail. Un dossier ou fichier donné peut être associé à n’importe quel nombre de contextes de fichier. Il s’agit d’une relation plusieurs-à-plusieurs.

Les scénarios les plus courants pour les contextes de fichier sont liées à la génération, débogage et les services de langage. Pour plus d’informations, consultez les autres rubriques relatives à ces scénarios.

## <a name="file-context-lifecycle"></a>Contexte du cycle de vie du fichier

Cycles de vie pour un `FileContext` sont non déterministes. À tout moment, un composant peut demander de manière asynchrone pour un jeu de types de contexte. Les fournisseurs qui prennent en charge un sous-ensemble des types de contexte de requête seront interrogés. Le `IWorkspace` instance joue le rôle du milieu-man entre le client et les fournisseurs à l’aide du <xref:Microsoft.VisualStudio.Workspace.IWorkspace.GetFileContextsAsync%2A> (méthode). Consommateurs peuvent demander un contexte et effectuent certaines actions à court terme, en fonction du contexte, tandis que d’autres utilisateurs peuvent demander un contexte et conserver une référence de longue durée. 

Modifications peuvent se produire dans des fichiers qui provoquent un contexte de fichier devenir obsolète. Le fournisseur peut déclencher un événement sur le `FileContext` pour informer les utilisateurs des mises à jour. Par exemple, si un contexte de génération est fourni pour un fichier, mais une modification sur disque invalide ce contexte, le producteur d’origine peut appeler l’événement. Les consommateurs qui référence encore `FileContext` pouvez actualiser un nouveau `FileContext`.

>[!NOTE]
>Il n’existe aucun modèle d’émission aux consommateurs. Consommateurs ne sera pas informés d’un fournisseur de nouveau `FileContext` après leur demande.

## <a name="expensive-file-context-computations"></a>Calculs de contexte de fichiers coûteux

Contenu du fichier lors de la lecture à partir du disque peut être coûteuse, en particulier lorsqu’un fournisseur doit résoudre la relation entre les fichiers. Par exemple, un fournisseur peut-être être interrogé pour le contexte du fichier d’un fichier source, mais le contexte du fichier dépend de métadonnées à partir d’un fichier de projet. L’analyse du fichier de projet ou l’évaluer avec MSBuild est coûteuse. Au lieu de cela, l’extension peut exporter un `IFileScanner` créer `FileDataValue` les données lors de l’indexation de l’espace de travail. Maintenant lorsque vous êtes invité pour les contextes de fichier, le `IFileContextProvider` peuvent interroger rapidement pour que les données indexées. Pour plus d’informations sur l’indexation, consultez le [indexation de l’espace de travail](workspace-indexing.md) rubrique.

>[!WARNING]
>Soyez prudent d’autres moyens votre `FileContext` peut être coûteux à calculer. Certaines interactions de l’interface utilisateur sont synchrones et s’appuient sur un volume élevé de `FileContext` demandes. Ouverture d’un onglet de l’éditeur et l’ouverture des exemples un **l’Explorateur de solutions** menu contextuel. Ces actions rendre contexte de génération de nombreuses demandes de type.

## <a name="file-context-related-apis"></a>API associée au contexte de fichier

- <xref:Microsoft.VisualStudio.Workspace.FileContext> contient les données et métadonnées.
- <xref:Microsoft.VisualStudio.Workspace.IFileContextProvider> et <xref:Microsoft.VisualStudio.Workspace.IFileContextProvider`1> créer le contexte du fichier.
- <xref:Microsoft.VisualStudio.Workspace.ExportFileContextProviderAttribute> Exporte un fournisseur de contexte du fichier.
- <xref:Microsoft.VisualStudio.Workspace.IWorkspace.GetFileContextsAsync%2A> est utilisé pour les consommateurs pour obtenir des contextes de fichier.
- <xref:Microsoft.VisualStudio.Workspace.Build.BuildContextTypes> définit les types de contexte de build qui consommera d’ouvrir le dossier.

## <a name="file-context-actions"></a>Actions de contexte de fichiers

Pendant un `FileContext` lui-même est seulement les données sur un ou plusieurs fichiers, un <xref:Microsoft.VisualStudio.Workspace.IFileContextAction> est un moyen d’express et d’agir sur ces données. `IFileContextAction` est flexible dans son utilisation. Deux de ses scénarios les plus courants sont de génération et de débogage.

## <a name="reporting-progress"></a>Signaler la progression

Le <xref:Microsoft.VisualStudio.Workspace.IFileContextActionBase.ExecuteAsync%2A> passé de la méthode `IProgress<IFileContextActionProgressUpdate>`, mais l’argument ne doit pas être utilisé en tant que type. `IFileContextActionProgressUpdate` est une interface vide et l’appel de `IProgress<IFileContextActionProgressUpdate>.Report(IFileContextActionProgressUpdate)` peut lever `NotImplementedException`. Au lieu de cela, la `IFileContextAction` doit convertir l’argument en un autre type que nécessaire pour le scénario.

Pour plus d’informations sur les types fournis par Visual Studio, consultez documentation du scénario respectif.

## <a name="file-context-action-related-apis"></a>API associées à action de contexte de fichiers

- <xref:Microsoft.VisualStudio.Workspace.IFileContextAction> exécute un comportement basé sur un `FileContext`.
- <xref:Microsoft.VisualStudio.Workspace.IFileContextActionProvider> crée des instances de `IFileContextAction`.
- <xref:Microsoft.VisualStudio.Workspace.ExportFileContextActionProviderAttribute> Exporte le type `IWorkspaceProviderFactory<IFileContextActionProvider>`.

## <a name="file-watching"></a>Surveillance des fichiers

Un espace de travail à l’écoute des notifications de modification de fichier et fournit le <xref:Microsoft.VisualStudio.Workspace.IFileWatcherService> via <xref:Microsoft.VisualStudio.Workspace.WorkspaceServiceHelper.GetFileWatcherService%2A>. Fichiers correspond au paramètre « Eléments exclus » ne produisent pas les événements de notification de fichier. Un seuil entre des événements est utilisé pour la simplification de la notification et de réduction en double. Lorsque vous avez besoin réagir à une modification de fichier, vous devez vous abonner à ce service.

>[!TIP]
>Un espace de travail [service d’indexation](workspace-indexing.md) s’abonne aux événements de fichier par défaut. Ajouts de fichiers et des modifications entraîne pertinentes `IFileScanner`événements s à appeler pour les nouvelles données pour ce fichier. Les suppressions de fichiers supprimera les données indexées. Vous n’avez pas besoin de s’abonner votre `IFileScanner` pour le service de l’Observateur de fichier.

## <a name="next-steps"></a>Étapes suivantes

* [L’indexation](workspace-indexing.md) -indexation de l’espace de travail de collecte et conserve les informations sur l’espace de travail.
* [Espaces de travail](workspaces.md) -passez en revue les concepts de l’espace de travail et de stockage des paramètres.
