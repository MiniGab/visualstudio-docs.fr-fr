---
title: Directive d'importation T4
ms.date: 11/04/2016
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 6b0479bf427930d19b12fa0de5728f26e7cdb10d
ms.sourcegitcommit: 206e738fc45ff8ec4ddac2dd484e5be37192cfbd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/03/2018
ms.locfileid: "39510176"
---
# <a name="t4-import-directive"></a>Directive d'importation T4

Dans les blocs de code d’un [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] modèle de texte T4, le `import` directive vous permet de faire référence aux éléments dans un autre espace de noms sans fournir un nom qualifié complet. Cela équivaut à `using` en C# ou à `imports` en [!INCLUDE[vb_current_short](../debugger/includes/vb_current_short_md.md)].

Pour obtenir une vue d’ensemble de l’écriture de modèles de texte T4, consultez [écriture d’un modèle de texte T4](../modeling/writing-a-t4-text-template.md).

## <a name="using-the-import-directive"></a>Utilisation de la directive d'importation

```
<#@ import namespace="namespace" #>
```

 Dans cet exemple, le code du modèle peut omettre un espace de noms explicite pour les membres de System.IO :

```
<#@ import namespace="System.IO" #>
<#
   string fileContent = File.ReadAllText("C:\x.txt"); // System.IO.File
#>
The file contains: <#=  fileContent #>
```

## <a name="standard-imports"></a>Importations standard
 L'espace de noms suivant est importé automatiquement, afin que vous n'ayez pas besoin d'écrire une directive d'importation pour lui :

-   `System`

 De plus, si vous utilisez une directive personnalisée, le processeur de directive peut importer automatiquement des espaces de noms.

 Par exemple, si vous écrivez des modèles pour un langage spécifique à un domaine (DSL), vous n’avez pas besoin d’importer des directives pour les espaces de noms suivants :

-   `Microsoft.VisualStudio.Modeling`

-   Espace de noms de votre solution DSL

## <a name="see-also"></a>Voir aussi

- [Directive d’assembly T4](../modeling/t4-assembly-directive.md)