---
title: -ProjectConfig (devenv.exe) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- /projectconfig Devenv switch
- configurations, rebuilding
- deployment projects, creating
- configurations, cleaning
- deployment projects, specifying
- deployment projects, adding
- build configurations, specifying
- Devenv, /projectconfig switch
- projectconfig Devenv switch (/projectconfig)
- projects [Visual Studio], build configuration
- projects [Visual Studio], cleaning
ms.assetid: 6b54ef59-ffed-4f62-a645-1279ede97ebf
caps.latest.revision: 11
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
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
translationtype: Human Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 02fd2a046b7b4070fa4e1903bd13772c518a7207
ms.lasthandoff: 02/22/2017

---
# <a name="projectconfig-devenvexe"></a>/ProjectConfig (devenv.exe)
Spécifie une configuration de build de projet à appliquer quand vous générez, nettoyez, régénérez ou déployez le projet nommé dans l’argument `/project`.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
devenv SolutionName {/build|/clean|/rebuild|/deploy} SolnConfigName [/project ProjName] [/projectconfig ProjConfigName]  
```  
  
## <a name="arguments"></a>Arguments  
 /build  
 Génère le projet spécifié par `/project` `ProjName`.  
  
 /clean  
 Nettoie tous les fichiers intermédiaires et répertoires de sortie créés pendant une génération.  
  
 /rebuild  
 Nettoie puis génère le projet spécifié par `/project` `ProjName`.  
  
 /deploy  
 Spécifie que le projet doit être déployé après une génération ou une régénération.  
  
 `SolnConfigName`  
 Obligatoire. Nom de la configuration de solution à appliquer à la solution nommée dans `SolutionName`.  
  
 `SolutionName`  
 Obligatoire. Chemin complet et nom du fichier solution.  
  
 /project `ProjName`  
 Facultatif. Chemin et nom d’un fichier projet dans la solution. Vous pouvez entrer un chemin relatif allant du dossier `SolutionName` au fichier projet, le nom d’affichage du projet ou le chemin complet et le nom du fichier projet.  
  
 /projectconfig `ProjConfigName`  
 Facultatif. Nom d’une configuration de build de projet à appliquer au `/project` nommé.  
  
## <a name="remarks"></a>Remarques  
  
-   Doit être utilisé avec le commutateur `/project` dans le cadre d’une commande `devenv /build`, /`clean`, `/rebuild` ou `/deploy`.  
  
-   Placez entre guillemets doubles les chaînes contenant des espaces.  
  
-   Vous pouvez afficher des informations récapitulatives sur les builds, y compris sur les erreurs, dans la fenêtre **Commande** ou dans tout fichier journal spécifié avec le commutateur `/out`.  
  
## <a name="example"></a>Exemple  
 Cet exemple génère le projet `CSharpConsoleApp`, à l’aide la configuration de build de projet `Debug` au sein de la configuration de solution `Debug` de `MySolution`.  
  
```  
devenv "C:\Documents and Settings\someuser\My Documents\Visual Studio\Projects\MySolution\MySolution.sln" /build Debug /project "CSharpWinApp\CSharpWinApp.csproj" /projectconfig Debug   
```  
  
## <a name="see-also"></a>Voir aussi  
 [Commutateurs de la ligne de commande Devenv](../../ide/reference/devenv-command-line-switches.md)   
 [/Project (devenv.exe)](../../ide/reference/project-devenv-exe.md)   
 [/Build (devenv.exe)](../../ide/reference/build-devenv-exe.md)   
 [/Clean (devenv.exe)](../../ide/reference/clean-devenv-exe.md)   
 [/Rebuild (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md)   
 [/Deploy (devenv.exe)](../../ide/reference/deploy-devenv-exe.md)   
 [/Out (devenv.exe)](../../ide/reference/out-devenv-exe.md)