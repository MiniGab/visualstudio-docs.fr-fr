---
title: Gérer les propriétés des projets et des solutions
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 96581fbaff9c2ddc85fbb92d73096f2a369d4c7b
ms.sourcegitcommit: 58052c29fc61c9a1ca55a64a63a7fdcde34668a4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34746310"
---
# <a name="manage-project-and-solution-properties"></a>Gérer les propriétés des projets et des solutions

Les projets ont des propriétés qui régissent de nombreux aspects de la compilation, du débogage, du test et du déploiement. Certaines propriétés sont communes à tous les types de projets, et certaines sont particulières à des langages ou des plateformes spécifiques. Pour accéder aux propriétés d’un projet, cliquez avec le bouton droit sur le nœud du projet dans **l’Explorateur de solutions** et choisissez **Propriétés** ou tapez « propriétés » dans la zone de recherche **Lancement rapide** de la barre de menus.

![Menu contextuel du projet](../ide/media/vs2015_proj_prop_menu.gif)

Les projets .NET peuvent également avoir un nœud Propriétés dans l’arborescence-même du projet.

![Nœud Propriétés dans l'arborescence de l'Explorateur de solutions](../ide/media/vs2015_props_se.png)

## <a name="project-properties"></a>Propriétés de projet

Les propriétés de projet sont organisées en groupes, et chaque groupe a sa propre page de propriétés. Les pages peuvent être différentes pour différents langages et types de projets.

### <a name="c-visual-basic-and-f-projects"></a>Projets C#, Visual Basic et F#

Dans les projets C#, Visual Basic et F#, les propriétés sont exposées dans le **Concepteur de projet**. L’illustration suivante montre la page de propriétés **Build** d’un projet WPF en C# :

![Concepteur de projet Visual Studio](../ide/media/vs2015_proppage_build.png)

Pour plus d’informations sur chacune des pages de propriétés dans le **Concepteur de projets**, consultez [Informations de référence sur les propriétés d’un projet](../ide/reference/project-properties-reference.md).

> [!TIP]
> Les solutions ont quelques propriétés, de même que les éléments des projets. Ces propriétés sont accessibles dans la [fenêtre Propriétés](../ide/reference/properties-window.md) et non pas dans le **Concepteur de projets**.

### <a name="c-and-javascript-projects"></a>Projets C++ et JavaScript

Les projets C++ et JavaScript ont une interface utilisateur différente pour la gestion des propriétés des projets. Cette illustration montre une page de propriétés d'un projet C++ (les pages pour JavaScript sont similaires) :

![Propriétés de projets Visual C&#43;&#43;](../ide/media/vs2015_projprops_cpp.png)

Pour plus d’informations sur les propriétés des projets C++, consultez [Utilisation des propriétés des projets (C++)](/cpp/ide/working-with-project-properties). Pour plus d’informations sur les propriétés JavaScript, consultez [Pages de propriétés, JavaScript](../ide/reference/property-pages-javascript.md).

## <a name="solution-properties"></a>Propriétés de la solution

Pour accéder aux propriétés sur la solution, cliquez avec le bouton droit sur le nœud de la solution dans l’**Explorateur de solutions** et choisissez **Propriétés**. Dans la boîte de dialogue, vous pouvez définir des configurations de projet pour les builds **Debug** ou **Release**, choisir les projets qui doivent être le projet de démarrage quand vous appuyez sur **F5** et définir les options d’analyse du code.

## <a name="see-also"></a>Voir aussi

- [Solutions et projets dans Visual Studio](../ide/solutions-and-projects-in-visual-studio.md)
