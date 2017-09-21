---
title: "ID de composant et de charge de travail de Visual Studio Build Tools 2017 | Microsoft Docs"
description: "ID de composant et de charge de travail Visual Studio pour créer des applications Windows classiques"
keywords: 
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.date: 08/30/2017
ms.topic: article
helpviewer_keywords:
- workload ID, Visual Studio
- component ID, Visual Studio
- install Visual Studio, administrator guide
ms.prod: visual-studio-dev15
ms.service: 
ms.technology:
- vs-ide-install
ms.assetid: b99298df-0280-47fc-af73-44cd7a8ac553
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 96018963278cd1d53b226473baade41da1e98111
ms.openlocfilehash: 86ac70e66b581a2e70dc8efa185b1e61d7d0204c
ms.contentlocale: fr-fr
ms.lasthandoff: 09/06/2017

---

# <a name="visual-studio-build-tools-2017-component-directory"></a>Répertoire de composants Visual Studio Build Tools 2017

Les tableaux de cette page listent les ID que vous pouvez utiliser pour installer Visual Studio à l’aide de la ligne de commande. Notez que nous ajouterons des composants supplémentaires lors de la publication de mises à jour de Visual Studio.

En outre, notez ce qui suit concernant cette page :

* Chaque charge de travail possède sa propre section, suivie de l’ID de charge de travail et d’un tableau des composants disponibles pour cette charge de travail.
* Par défaut, les composants **requis** sont installés lorsque vous installez la charge de travail. Si vous le souhaitez, vous pouvez également installer les composants **recommandés** et **facultatifs**.
* Nous avons également ajouté une section qui répertorie les composants supplémentaires qui ne sont affiliés à aucune charge de travail.

Pour plus d’informations sur l’utilisation de ces ID, consultez la page [Utiliser les paramètres de ligne de commande pour installer Visual Studio 2017 RC](use-command-line-parameters-to-install-visual-studio.md). Pour obtenir la liste des ID de charge de travail et de composant triés des autres produits, consultez la page [ID de composant et de charge de travail de Visual Studio 2017](workload-and-component-ids.md).

## <a name="msbuild-tools"></a>MSBuild Tools

**ID :** Microsoft.VisualStudio.Workload.MSBuildTools

**Description :** fournit les outils nécessaires pour générer des applications MSBuild.

### <a name="components-included-by-this-workload"></a>Composants inclus par cette charge de travail

ID de composant | Nom | Version | Type de dépendance
--- | --- | --- | ---
Microsoft.Component.MSBuild | MSBuild | 15.0.26208.0 | Obligatoire
Microsoft.VisualStudio.Component.CoreBuildTools | Visual Studio Build Tools Core | 15.0.26711.1 | Obligatoire
Microsoft.VisualStudio.Component.Roslyn.Compiler | Compilateurs Roslyn C# et Visual Basic | 15.0.26208.0 | Obligatoire
Microsoft.VisualStudio.Component.FSharp.MSBuild | compilateur F# | 15.0.26606.0 | Facultatif

## <a name="net-core-build-tools"></a>Outils de génération .NET Core

**ID :** Microsoft.VisualStudio.Workload.NetCoreBuildTools

**Description :** outils pour créer des applications .NET Core.

### <a name="components-included-by-this-workload"></a>Composants inclus par cette charge de travail

ID de composant | Nom | Version | Type de dépendance
--- | --- | --- | ---
Microsoft.Net.Core.Component.SDK | Outils de développement .NET Core 1.0 - 1.1 | 15.0.26606.0 | Obligatoire

## <a name="visual-c-build-tools"></a>Outils de génération Visual C++

**ID :** Microsoft.VisualStudio.Workload.VCTools

**Description :** créez des applications Windows classiques en vous aidant de la puissance de l’ensemble d’outils Visual C++, ATL et des fonctionnalités facultatives, telles que MFC et C + c++ / CLI.

### <a name="components-included-by-this-workload"></a>Composants inclus par cette charge de travail

ID de composant | Nom | Version | Type de dépendance
--- | --- | --- | ---
Microsoft.VisualStudio.Component.VC.CoreBuildTools | Fonctionnalités de base des outils de génération Visual C++ | 15.0.26208.0 | Obligatoire
Microsoft.VisualStudio.Component.VC.Redist.14.Latest | Mise à jour redistribuable Visual C++ 2017 | 15.0.26606.0 | Obligatoire
Microsoft.VisualStudio.Component.Windows10SDK | Runtime C Windows universel | 15.0.26621.2 | Obligatoire
Component.Microsoft.VisualStudio.RazorExtension | Services de langage Razor | 15.0.26720.2 | Recommandé
Microsoft.VisualStudio.Component.Roslyn.Compiler | Compilateurs Roslyn C# et Visual Basic | 15.0.26208.0 | Recommandé
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# et Visual Basic | 15.0.26711.1 | Recommandé
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Outils d’analyse statique | 15.0.26208.0 | Recommandé
Microsoft.VisualStudio.Component.VC.CMake.Project | Outils Visual C++ pour CMake | 15.0.26621.2 | Recommandé
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | Ensemble d’outils VC++ 2017 v141 (x86, x64) | 15.0.26621.2 | Recommandé
Microsoft.VisualStudio.Component.Windows10SDK.15063.Desktop | SDK Windows 10 (10.0.15063.0) pour plateforme desktop C++ x86 et x64 | 15.0.26621.2 | Recommandé
Microsoft.VisualStudio.Component.Windows10SDK.15063.UWP | SDK Windows 10 (10.0.15063.0) pour UWP : C#, VB, JS | 15.0.26621.2 | Recommandé
Microsoft.VisualStudio.Component.Windows10SDK.15063.UWP.Native | SDK Windows 10 (10.0.15063.0) pour UWP : C++ | 15.0.26621.2 | Recommandé
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | Développement web et ASP.NET | 15.0.26606.0 | Recommandé
Microsoft.Component.VC.Runtime.UCRTSDK | SDK CRT (runtime C) universel pour Windows | 15.0.26208.0 | Facultatif
Microsoft.Net.Component.4.6.1.SDK | SDK .NET Framework 4.6.1 | 15.0.26621.2 | Facultatif
Microsoft.Net.Component.4.6.1.TargetingPack | Pack de ciblage .NET Framework 4.6.1 | 15.0.26621.2 | Facultatif
Microsoft.VisualStudio.Component.VC.140 | Ensemble d’outils VC ++ 2015.3 v140 pour le bureau (x86, x64) | 15.0.26720.2 | Facultatif
Microsoft.VisualStudio.Component.VC.ATL | Prise en charge de Visual C++ ATL | 15.0.26621.2 | Facultatif
Microsoft.VisualStudio.Component.VC.ATLMFC | Prise en charge de MFC et d’ATL (x86 et x64) | 15.0.26621.2 | Facultatif
Microsoft.VisualStudio.Component.VC.ClangC2 | Clang/C2 (expérimental) | 15.0.26724.1 | Facultatif
Microsoft.VisualStudio.Component.VC.CLI.Support | Prise en charge de C++/CLI | 15.0.26621.2 | Facultatif
Microsoft.VisualStudio.Component.VC.Modules.x86.x64 | Modules de la bibliothèque Standard (expérimental) | 15.0.26720.2 | Facultatif
Microsoft.VisualStudio.Component.Windows10SDK.10240 | SDK Windows 10 (10.0.10240.0) | 15.0.26208.0 | Facultatif
Microsoft.VisualStudio.Component.Windows10SDK.10586 | SDK Windows 10 (10.0.10586.0) | 15.0.26208.0 | Facultatif
Microsoft.VisualStudio.Component.Windows10SDK.14393 | SDK Windows 10 (10.0.14393.0) | 15.0.26208.0 | Facultatif
Microsoft.VisualStudio.Component.Windows81SDK | SDK Windows 8.1 | 15.0.26208.0 | Facultatif
Microsoft.VisualStudio.ComponentGroup.NativeDesktop.Win81 | SDK Windows 8.1 et SDK UCRT | 15.0.26208.0 | Facultatif

## <a name="web-development-build-tools"></a>Outils de génération de développement web

**ID :** Microsoft.VisualStudio.Workload.WebBuildTools

**Description :** tâches et cibles MSBuild pour la création d’applications web.

### <a name="components-included-by-this-workload"></a>Composants inclus par cette charge de travail

ID de composant | Nom | Version | Type de dépendance
--- | --- | --- | ---
Microsoft.Net.Component.4.6.1.SDK | SDK .NET Framework 4.6.1 | 15.0.26621.2 | Obligatoire
Microsoft.Net.Component.4.6.1.TargetingPack | Pack de ciblage .NET Framework 4.6.1 | 15.0.26621.2 | Obligatoire
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Outils de développement .NET Framework 4.6.1 | 15.0.26606.0 | Obligatoire
Microsoft.VisualStudio.Web.BuildTools.ComponentGroup | Outils de génération de développement web | 15.0.26323.1 | Obligatoire
Microsoft.Net.Component.4.5.1.TargetingPack | Pack de ciblage .NET Framework 4.5.1 | 15.0.26621.2 | Recommandé
Microsoft.Net.Component.4.5.2.TargetingPack | Pack de ciblage .NET Framework 4.5.2 | 15.0.26621.2 | Recommandé
Microsoft.Net.Component.4.5.TargetingPack | Pack de ciblage .NET Framework 4.5 | 15.0.26621.2 | Recommandé
Microsoft.Net.Component.4.6.TargetingPack | Pack de ciblage .NET Framework 4.6 | 15.0.26621.2 | Recommandé
Microsoft.Net.Component.4.TargetingPack | Pack de ciblage .NET Framework 4 | 15.0.26621.2 | Recommandé
Microsoft.Net.ComponentGroup.TargetingPacks.Common | Outils de développement .NET Framework 4 - 4.6 | 15.0.26606.0 | Recommandé
Microsoft.Net.Core.Component.SDK | Outils de développement .NET Core 1.0 - 1.1 | 15.0.26606.0 | Recommandé
Microsoft.Net.Component.3.5.DeveloperTools | Outils de développement .NET Framework 3.5 | 15.0.26621.2 | Facultatif
Microsoft.Net.Component.4.6.2.SDK | SDK .NET Framework 4.6.2 | 15.0.26208.0 | Facultatif
Microsoft.Net.Component.4.6.2.TargetingPack | Pack de ciblage .NET Framework 4.6.2 | 15.0.26208.0 | Facultatif
Microsoft.Net.Component.4.7.SDK | SDK .NET Framework 4.7 | 15.0.26419.1 | Facultatif
Microsoft.Net.Component.4.7.TargetingPack | Pack de ciblage .NET Framework 4.7 | 15.0.26621.2 | Facultatif
Microsoft.Net.ComponentGroup.4.6.2.DeveloperTools | Outils de développement .NET Framework 4.6.2 | 15.0.26621.2 | Facultatif
Microsoft.Net.ComponentGroup.4.7.DeveloperTools | Outils de développement .NET Framework 4.7 | 15.0.26606.0 | Facultatif

## <a name="unaffiliated-components"></a>Composants non affiliés

Il s’agit de composants qui ne sont inclus dans aucune charge de travail, mais qui peuvent être sélectionnés de manière individuelle.

ID de composant | Nom | Version
--- | --- | ---
N/A | N/A | N/A

## <a name="see-also"></a>Voir aussi

* [ID de charge de travail et de composant Visual Studio](workload-and-component-ids.md)
* [Guide de l’administrateur Visual Studio](visual-studio-administrator-guide.md)
* [Utiliser les paramètres de ligne de commande pour installer Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
  * [Exemples de paramètres de ligne de commande](command-line-parameter-examples.md)
* [Créer une installation hors connexion de Visual Studio](create-an-offline-installation-of-visual-studio.md)
