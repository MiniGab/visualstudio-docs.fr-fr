---
title: Fichiers .Targets MSBuild | Microsoft Docs
ms.custom: ''
ms.date: 02/24/2017
ms.technology: msbuild
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- .Targets files
- MSBuild, .Targets files
ms.assetid: f6d98eb4-d2fa-49b7-8e3c-bae1ca3cf596
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 835d6e80c650a18b3e595d1c6dc0c8bafd6b958a
ms.sourcegitcommit: 8ee7efb70a1bfebcb6dd9855b926a4ff043ecf35
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/17/2018
ms.locfileid: "39080010"
---
# <a name="msbuild-targets-files"></a>Fichiers .targets MSBuild
[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] inclut plusieurs fichiers *.targets* contenant des éléments, des propriétés, des cibles et des tâches pour les scénarios courants. Ces fichiers sont importés automatiquement dans la plupart des fichiers projet [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] pour en simplifier la maintenance et la lisibilité.  

 Les projets importent généralement un ou plusieurs fichiers *.targets* pour définir leur processus de génération. Par exemple, un projet [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] créé par [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] importera *Microsoft.CSharp.targets*, qui importe *Microsoft.Common.targets*. Le projet [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] lui-même définit les éléments et les propriétés propres à ce projet, mais les règles de génération standard d’un projet [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] sont définies dans les fichiers *.targets* importés.  

 La valeur `$(MSBuildToolsPath)` spécifie le chemin de ces fichiers *.targets* courants. Si la `ToolsVersion` est égale à 4.0, les fichiers se trouvent à l’emplacement suivant : *\<WindowsInstallationPath>\Microsoft.NET\Framework\v4.0.30319\\*  

> [!NOTE]
>  Pour plus d’informations sur la création de vos propres cibles, consultez l’article [Targets (Cibles MSBuild)](../msbuild/msbuild-targets.md). Pour plus d’informations sur l’utilisation de l’élément `Import` pour insérer un fichier projet dans un autre fichier projet, consultez les articles [Import, élément (MSBuild)](../msbuild/import-element-msbuild.md) et [Guide pratique pour utiliser la même cible dans plusieurs fichiers projet](../msbuild/how-to-use-the-same-target-in-multiple-project-files.md).  

## <a name="common-targets-files"></a>Fichiers .targets communs  

|Fichier *.targets*|Description|  
|-------------------|-----------------|  
|*Microsoft.Common.targets*|Définit les étapes du processus de génération standard pour les projets [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] et [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)].<br /><br /> Importé par les fichiers *Microsoft.CSharp.targets* et *Microsoft.VisualBasic.targets*, qui incluent l’instruction suivante : `<Import Project="Microsoft.Common.targets" />`|  
|*Microsoft.CSharp.targets*|Définit les étapes du processus de génération standard pour les projets Visual C#.<br /><br /> Importé par les fichiers projet Visual C# (*.csproj*), qui incluent l’instruction suivante: `<Import Project="$(MSBuildToolsPath)\Microsoft.CSharp.targets" />`|  
|*Microsoft.VisualBasic.targets*|Définit les étapes du processus de génération standard pour les projets Visual Basic.<br /><br /> Importé par les fichiers projet Visual Basic (*.vbproj*), qui incluent l’instruction suivante : `<Import Project="$(MSBuildToolsPath)\Microsoft.VisualBasic.targets" />`|

## <a name="directorybuildtargets"></a>Directory.Build.targets
*Directory.Build.targets* est un fichier défini par l’utilisateur qui fournit des personnalisations aux projets situés dans un répertoire. Ce fichier est automatiquement importé depuis *Microsoft.Common.targets*, sauf si la propriété **ImportDirectoryBuildTargets** a la valeur **false**.

## <a name="see-also"></a>Voir aussi  
 [Import, élément (MSBuild)](../msbuild/import-element-msbuild.md)   
 [Informations de référence sur MSBuild](../msbuild/msbuild-reference.md)  
 [MSBuild](../msbuild/msbuild.md)
