---
title: Déboguer du code utilisateur avec uniquement mon Code | Microsoft Docs
ms.custom: ''
ms.date: 05/18/2017
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 0f0df097-bbaf-46ad-9ad1-ef5f40435079
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3a2873f691fdaa1251a5562e21e2bbd0467eb2e2
ms.sourcegitcommit: 7bb0225e1fd45999ce09e0b49c2cfae515c27e11
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/14/2018
ms.locfileid: "45612751"
---
# <a name="specify-whether-to-debug-only-user-code-using-just-my-code-in-visual-studio"></a>Indiquez si vous souhaitez déboguer uniquement le code utilisateur à l’aide d’uniquement mon Code dans Visual Studio
Vous pouvez configurer Visual Studio pour effectuer un survol de système, d’infrastructure et d’autres appels de non-utilisateur automatiquement et de réduire ces appels dans la fenêtre Pile des appels. La fonctionnalité qui active ou désactive ce comportement est appelée *uniquement mon Code*. Cette rubrique décrit comment utiliser uniquement mon Code dans les projets c#, Visual Basic, C++ et JavaScript.

Pour la plupart des langages de programmation, uniquement mon Code est activé par défaut.
  
##  <a name="BKMK_Enable_or_disable_Just_My_Code"></a> Activer ou désactiver uniquement mon Code  
 Pour activer ou désactiver uniquement mon Code, choisissez la **Outils > Options** menu dans Visual Studio. Dans le **débogage** > **général** nœud, activez ou désactivez **activer uniquement mon Code**.
  
 ![Activer uniquement mon Code dans la boîte de dialogue Options](../debugger/media/dbg_justmycode_options.png "DBG_JustMyCode_Options")  
  
> [!NOTE]
>  Le **activer uniquement mon Code** paramètre est un paramètre global qui est appliqué à tous les projets Visual Studio dans toutes les langues.  
  
###  <a name="BKMK_Override_call_stack_filtering"></a> Afficher le code non-utilisateur dans les vues de pile des appels  
 Dans les vues qui affichent la pile des appels, telles que la **pile des appels** et **tâches** windows, uniquement mon Code réduit le code non-utilisateur dans un cadre annoté intitulé `[External Code]`. Pour afficher les cadres réduits, choisissez **afficher le Code externe** dans le menu contextuel de la pile des appels affiche.

 ![Afficher le Code externe dans la fenêtre Pile des appels](../debugger/media/dbg_justmycode_showexternalcode.png "DBG_JustMyCode_ShowExternalCode")
  
> [!NOTE]
>  Le **afficher le Code externe** paramètre est enregistré dans le Générateur de profils de l’utilisateur actuel. Il est appliqué à tous les projets dans tous les langages qui sont ouverts par l'utilisateur.

##  <a name="identify-user-code-while-debugging"></a>Identifier le code de l’utilisateur pendant le débogage 

Le **Modules** fenêtre peut vous indiquer quels modules de code le débogueur va traiter en tant que code utilisateur ou mon Code, ainsi que des informations telles que le symbole de chargement de l’état du module. Pour plus d’informations, consultez [vous familiariser avec la façon dont le débogueur s’attache à votre application](../debugger/debugger-tips-and-tricks.md#modules_window).
  
##  <a name="BKMK__NET_Framework_Just_My_Code"></a> Uniquement mon Code .NET framework  
  
###  <a name="BKMK_NET_User_and_non_user_code"></a> Code utilisateur et non-utilisateur  
 Pour distinguer le code utilisateur du code non-utilisateur, uniquement mon Code examine les fichiers de symboles (.pdb) et les optimisations de programme. Le débogueur considère le code comme du code non-utilisateur quand le fichier binaire est optimisé ou quand le fichier .pdb n'est pas disponible.
  
 Trois attributs affectent également ce que le débogueur considère comme étant du code MyCode :  
  
-   <xref:System.Diagnostics.DebuggerNonUserCodeAttribute> indique au débogueur que le code auquel il est appliqué n'est pas du code MyCode.  
  
-   <xref:System.Diagnostics.DebuggerHiddenAttribute> masque le code au débogueur, même si l'option Uniquement mon code est désactivée.  
  
-   <xref:System.Diagnostics.DebuggerStepThroughAttribute> indique au débogueur de passer pas à pas dans le code auquel il s'applique, plutôt que d'effectuer un pas à pas détaillé du code.  
  
 Tout le reste du code est considéré comme du code utilisateur.  
  
###  <a name="BKMK_NET_Stepping_behavior"></a> Comportement d’exécution pas à pas  
 Lorsque vous **pas à pas détaillé** (raccourci clavier : F11) code non-utilisateur, le débogueur exécute le code à l’instruction utilisateur suivante. Lorsque vous **pas à pas sortant** (clavier : MAJ + F11), le débogueur s’exécute à la ligne suivante du code utilisateur. Si aucun code utilisateur n’est rencontrée, l’exécution se poursuit jusqu'à ce que l’application se ferme, un point d’arrêt est atteint, ou une exception se produit.  
  
###  <a name="BKMK_NET_Breakpoint_behavior"></a> Comportement de point d’arrêt  
 Lorsque uniquement mon Code est activé, vous pouvez choisir **interrompre tout** (clavier : Ctrl + Alt + Attn) et d’arrêter l’exécution à un emplacement où il n’existe aucun code utilisateur à afficher. Dans ce cas, la fenêtre Pas de code source s'affiche. Si vous choisissez ensuite une commande d'étape, le débogueur vous amène à la ligne de code utilisateur suivante.  
  
###  <a name="BKMK_NET_Exception_behavior"></a> Comportement d’exception  
 Si une exception non gérée se produit dans du code non-utilisateur, le débogueur s'arrête à la ligne de code utilisateur où lequel l'exception a été générée.  
  
 Si les exceptions de première chance sont activées pour l'exception, la ligne de code utilisateur est mise en surbrillance en vert. La pile des appels affiche un cadre annoté intitulé **[Code externe]**.  
  
##  <a name="BKMK_C___Just_My_Code"></a> Uniquement mon Code C++  
  
###  <a name="BKMK_CPP_User_and_non_user_code"></a> Code utilisateur et non-utilisateur  
Uniquement mon Code C++ est différent d'Uniquement mon code .NET Framework et JavaScript, car le comportement d'exécution pas à pas est indépendant du comportement de la pile des appels.  

À compter de 15.8 de 2017 Visual Studio, vous pouvez spécifier s’il faut activer uniquement mon Code pour l’utilisation de C++ **outils** > **Options** > **débogage**  >  **Général** > **activer uniquement mon Code** (il est activé par défaut). Cela équivaut à utiliser le [/JMC (débogage uniquement mon code)](/cpp/build/reference/jmc) commutateur de compilateur.
  
 **Les piles d’appels**  
  
 Par défaut, le débogueur considère les fonctions suivantes comme étant du code non-utilisateur dans les fenêtres de pile des appels :  
  
-   Fonctions avec des informations sources supprimées dans leur fichier de symboles.  
  
-   Fonctions où les fichiers de symboles indiquent qu'il n'existe pas de fichier source correspondant au frame de pile.  
  
-   Fonctions spécifiées dans des fichiers `*.natjmc` du dossier `%VsInstallDirectory%\Common7\Packages\Debugger\Visualizers`.  
  
 **Exécution pas à pas**  
  
 Par défaut, seules les fonctions spécifiées dans des fichiers `*.natstepfilter` du dossier `%VsInstallDirectory%\Common7\Packages\Debugger\Visualizers` sont considérées comme du code non-utilisateur.  
  
 Vous pouvez créer vos propres fichiers `.natstepfilter` et `.natjmc` pour personnaliser le comportement de l'exécution pas à pas et de la fenêtre de pile des appels, et les placer dans le dossier `%USERPROFILE%\My Documents\Visual Studio 2017\Visualizers`.  
  
###  <a name="BKMK_CPP_Stepping_behavior"></a> Comportement d’exécution pas à pas  
 Lorsque vous **pas à pas détaillé** (raccourci clavier : F11) code de non-utilisateur depuis du code utilisateur, le débogueur exécute le code à la ligne suivante de code utilisateur. Lorsque vous **pas à pas sortant** (clavier : MAJ + F11), le débogueur s’exécute à la ligne suivante du code utilisateur. Si aucun code utilisateur n’est rencontrée, l’exécution se poursuit jusqu'à ce que l’application se ferme, un point d’arrêt est atteint, ou une exception se produit.  
  
 Si le débogueur s'arrête dans du code non-utilisateur (par exemple si une commande Interrompre tout s'arrête dans du code non-utilisateur), l'exécution pas à pas continue dans le code non-utilisateur.
  
###  <a name="BKMK_CPP_Exception_behavior"></a> Comportement d’exception  
 Lorsque le débogueur rencontre une exception, il s’arrête sur l’exception qu’il s’agisse de l’utilisateur ou le code non-utilisateur. Le **User-unhandled** options dans le **Exceptions** boîte de dialogue sont ignorés.  
  
###  <a name="BKMK_CPP_Customize_stepping_behavior"></a> Personnaliser le comportement de l’exécution pas à pas  
 Vous pouvez spécifier des fonctions que l'exécution pas à pas doit ignorer en les répertoriant comme étant du code non-utilisateur dans des fichiers `*.natstepfilter`.  
  
-   Pour spécifier le code non-utilisateur pour tous les utilisateurs de l’ordinateur Visual Studio, ajoutez le fichier .natstepfilter à la `%VsInstallDirectory%\Common7\Packages\Debugger\Visualizers` dossier.  
  
-   Pour spécifier le code non-utilisateur pour un utilisateur individuel, ajoutez le fichier .natstepfilter à la `%USERPROFILE%\My Documents\Visual Studio 2017\Visualizers` dossier.  
  
 .natstepfilter sont des fichiers xml avec la syntaxe suivante :  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<StepFilter xmlns="http://schemas.microsoft.com/vstudio/debugger/natstepfilter/2010">  
    <Function>  
        <Name>FunctionSpec</Name>  
        <Action>StepAction</Action>  
    </Function>  
    <Function>  
        <Name>FunctionSpec</Name>  
        <Module>ModuleSpec</Module>  
        <Action>StepAction</Action>  
    </Function>  
</StepFilter>  
  
```  
  
|Élément|Description|  
|-------------|-----------------|  
|Fonction|Obligatoire. Spécifie une ou plusieurs fonctions comme fonctions non-utilisateur.|  
|`Name`|Obligatoire. Une expression régulière mise en forme selon ECMA-262 spécifiant le nom complet de la fonction concernée. Exemple :<br /><br /> `<Name>MyNS::MyClass.*</Name>`<br /><br /> indique au débogueur que toutes les méthodes de `MyNS::MyClass` doivent être considérées comme du code non-utilisateur. La recherche de correspondance respecte la casse.|  
|`Module`|Facultatif. Une expression régulière mise en forme selon ECMA-262 spécifiant le chemin d'accès complet au module contenant la fonction. La recherche de correspondance ne respecte pas la casse.|  
|`Action`|Obligatoire. Une des valeurs suivantes (respectant la casse) :<br /><br /> -   `NoStepInto`  -Indique au débogueur d’ignorer la fonction concernée.<br />-   `StepInto`  -Indique au débogueur d’ignorer les fonctions concernées, substitution de n’importe quel autre `NoStepInto` pour les fonctions de mise en correspondance.|  
  
###  <a name="BKMK_CPP_Customize_call_stack_behavior"></a> Personnaliser le comportement de pile d’appel  
 Vous pouvez spécifier des modules, des fichiers sources et des fonctions à traiter comme du code non-utilisateur dans les piles des appels en les spécifiant dans des fichiers `*.natjmc`.  
  
-   Pour spécifier le code non-utilisateur pour tous les utilisateurs de l’ordinateur Visual Studio, ajoutez le fichier .natjmc à la `%VsInstallDirectory%\Common7\Packages\Debugger\Visualizers` dossier.  
  
-   Pour spécifier le code non-utilisateur pour un utilisateur individuel, ajoutez le fichier .natjmc à la `%USERPROFILE%\My Documents\Visual Studio 2017\Visualizers` dossier.  
  
 .natjmc sont des fichiers xml avec la syntaxe suivante :  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<NonUserCode xmlns="http://schemas.microsoft.com/vstudio/debugger/jmc/2015">  
  
  <!-- Modules -->  
  <Module Name="ModuleSpec" />  
  <Module Name="ModuleSpec" Company="CompanyName" />  
  
  <!-- Files -->  
  <File Name="FileSpec"/>  
  
  <!-- Functions -->  
  <Function Name="FunctionSpec" />  
  <Function Name="FunctionSpec" Module ="ModuleSpec" />  
  <Function Name="FunctionSpec" Module ="ModuleSpec" ExceptionImplementation="true" />  
  
</NonUserCode>  
  
```  
  
 **Attributs d’élément de module**  
  
|Attribut|Description|  
|---------------|-----------------|  
|`Name`|Obligatoire. Chemin d’accès complet du ou des modules. Vous pouvez utiliser les caractères génériques Windows `?` (zéro ou un caractère) et `*` (zéro ou plusieurs caractères). Par exemple :<br /><br /> `<Module Name="?:\3rdParty\UtilLibs\*" />`<br /><br /> indique au débogueur de traiter tous les modules de `\3rdParty\UtilLibs` sur n'importe quel lecteur comme du code externe.|  
|`Company`|Facultatif. Le nom de la société qui publie le module incorporé dans le fichier exécutable. Vous pouvez utiliser cet attribut pour lever l'ambiguïté entre les modules.|  
  
 **Attributs de l’élément de fichier**  
  
|Attribut|Description|  
|---------------|-----------------|  
|`Name`|Obligatoire. Chemin d'accès complet du ou des fichiers sources à traiter comme du code externe. Vous pouvez utiliser les caractères génériques Windows `?` et `*` quand vous spécifiez le chemin d'accès.|  
  
 **Attributs de l’élément (fonction)**  
  
|Attribut|Description|  
|---------------|-----------------|  
|`Name`|Obligatoire. Le nom complet de la fonction à traiter comme du code externe.|  
|`Module`|Facultatif. Le nom ou le chemin d'accès complet au module qui contient la fonction. Vous pouvez utiliser cet attribut pour lever l'ambiguïté entre des fonctions du même nom.|  
|`ExceptionImplementation`|Quand la valeur est définie sur `true`, la pile des appels affiche la fonction qui a levé l'exception, au lieu de cette fonction.|  
  
##  <a name="BKMK_JavaScript_Just_My_Code"></a> Uniquement mon Code JavaScript  
  
###  <a name="BKMK_JS_User_and_non_user_code"></a> Code utilisateur et non-utilisateur  
 **Classification du code**  
  
 Uniquement mon Code JavaScript contrôle l'exécution pas à pas et l'affichage de la pile des appels en catégorisant le code selon la classification suivante :  
  
|||  
|-|-|  
|**MyCode**|Code utilisateur dont vous êtes propriétaire et que vous contrôlez.|  
|**LibraryCode**|Code non-utilisateur provenant de bibliothèques que vous utilisez régulièrement et sur lequel votre application s'appuie pour fonctionner correctement (par exemple WinJS ou jQuery).|  
|**UnrelatedCode**|Code non-utilisateur qui peut s’exécuter dans votre application, mais vous ne possédez pas, et votre application ne s’appuie pour fonctionner correctement. (Par exemple, cela peut inclure une Kit de développement logiciel qui affiche des publicités de publicité). Dans les projets UWP, tout code qui est chargé dans votre application à partir d’un URI HTTP ou HTTPS est également considéré comme UnrelatedCode.|  
  
 Le débogueur JavaScript classe automatiquement ces types de code :  
  
-   Script qui est exécuté en passant une chaîne pour le fourni par l’hôte `eval` fonction est classifiée comme **MyCode**.  
  
-   Script qui est exécuté en passant une chaîne pour le `Function` constructeur est classé comme **LibraryCode**.  
  
-   Le script qui est contenue dans une référence de framework, comme WinJS ou le Kit de développement, est classé comme **LibraryCode**.  
  
-   Script qui est exécuté en passant une chaîne pour le `setTimeout`, `setImmediate`, ou `setInterval` est classé comme **UnrelatedCode**.  
  
-   Le fichier `%VSInstallDirectory%\JavaScript\JustMyCode\mycode.default.wwa.json` spécifie d'autres codes utilisateur et non-utilisateur pour tous les projets JavaScript Visual Studio.  
  
 Vous pouvez modifier les classifications par défaut et classer des fichiers et des URL spécifiques en ajoutant un fichier .json nommé `mycode.json` au dossier racine d'un projet.  
  
 Reste du code est classé comme **MyCode**.  
  
###  <a name="BKMK_JS_Stepping_behavior"></a> Comportement d’exécution pas à pas  
  
-   Si une fonction n’est pas un utilisateur (**MyCode**) code, **pas à pas détaillé** (raccourci clavier : F11) se comporte comme **pas à pas principal** (clavier : F10).  
  
-   Si une étape commence dans non-utilisateur (**LibraryCode** ou **UnrelatedCode**) de code, pas à pas détaillé temporairement se comporte comme si uniquement mon Code n’est pas activé. Quand vous passez au code utilisateur, uniquement mon Code pas à pas est réactivé.  
  
-   Quand une étape dans du code utilisateur aboutit à quitter le contexte d'exécution actuel (par exemple effectuer une étape dans la dernière ligne d'un gestionnaire d'événements), le débogueur s'arrête à la ligne de code utilisateur exécutée qui suit. Par exemple, si un rappel s’exécute dans **LibraryCode** code le débogueur continue jusqu'à ce que la ligne suivante du code utilisateur s’exécute.
  
-   **Pas à pas sortant** (clavier : MAJ + F11) s’arrête sur la ligne suivante du code utilisateur. Si aucun code utilisateur n’est rencontrée, l’exécution se poursuit jusqu'à ce que l’application se ferme, un point d’arrêt est atteint, ou une exception se produit.  
  
###  <a name="BKMK_JS_Breakpoint_behavior"></a> Comportement de point d’arrêt  
  
-   Points d’arrêt définis dans le code seront toujours atteints, quel que soit la classification de ce code  
  
-   Si le mot clé `debugger` est rencontré dans :  
  
    -   **LibraryCode** code, le débogueur s’arrête toujours.  
  
    -   **UnrelatedCode** code, le débogueur ne s’arrête.  
  
###  <a name="BKMK_JS_Exception_behavior"></a> Comportement d’exception  
 Si une exception non gérée se produit dans :  
  
-   **MyCode** ou **LibraryCode** code, le débogueur s’arrête toujours.  
  
-   **UnrelatedCode** code, et **MyCode** ou **LibraryCode** code se trouve sur la pile des appels, le débogueur s’arrête.  
  
 Si les exceptions de première chance sont activées pour l’exception dans la boîte de dialogue Exceptions et l’exception est levée **LibraryCode** ou **UnrelatedCode** code :  
  
-   Si l’exception est gérée, le débogueur ne s’arrête.  
  
-   Si l'exception n'est pas gérée, le débogueur s'arrête.  
  
###  <a name="BKMK_JS_Customize_Just_My_Code"></a> Personnaliser uniquement mon Code  
 Pour classer par catégorie du code utilisateur et non-utilisateur pour un seul projet Visual Studio, ajoutez un fichier .json nommé `mycode.json` dans le dossier racine du projet.  
  
 Les classifications sont effectuées dans cet ordre :  
  
1.  Classifications par défaut  
  
2.  Classifications du fichier `%VSInstallDirectory%\JavaScript\JustMyCode\mycode.default.wwa.json`  
  
3.  Classifications du fichier `mycode. json` du projet actuel  
  
 Chaque étape de classification remplace les étapes précédentes. Un fichier .json n’a pas besoin répertorier toutes les paires clé / valeur et le **MyCode**, **bibliothèques**, et **Unrelated** valeurs peuvent être des tableaux vides.  
  
 Les fichiers .json My Code utilisent cette syntaxe :  
  
```json  
{  
    "Eval" : "Classification",  
    "Function" : "Classification",  
    "ScriptBlock" : "Classification",  
    "MyCode" : [  
        "UrlOrFileSpec",  
        . . .  
        "UrlOrFileSpec"  
    ],  
    "Libraries" : [  
        "UrlOrFileSpec",  
        . .  
        "UrlOrFileSpec"  
    ],  
    "Unrelated" : [  
        "UrlOrFileSpec",  
        . . .  
        "UrlOrFileSpec"  
    ]  
}  
  
```  
  
 **Eval, Function et ScriptBlock**  
  
 Le **Eval**, **fonction**, et **ScriptBlock** Déterminez comment dynamiquement les paires clé / valeur code généré est classé.  
  
|||  
|-|-|  
|**Eval**|un script qui est exécuté en passant une chaîne à la fonction `eval` fournie par l'hôte. Par défaut, le script Eval est classé comme **MyCode**.|  
|**Function**|un script qui est exécuté en passant une chaîne au constructeur `Function`. Par défaut, le script Function est classé en tant que **LibraryCode**.|  
|**ScriptBlock**|un script qui est exécuté en passant une chaîne aux fonctions `setTimeout`, `setImmediate` ou `setInterval`. Par défaut, le script ScriptBlock est classé en tant que **UnrelatedCode**.|  
  
 Vous pouvez changer la valeur en un de ces mots clés :  
  
-   `MyCode`  classe le script en tant que **MyCode**.  
  
-   `Library`  classe le script en tant que **LibraryCode**.  
  
-   `Unrelated`  classe le script en tant que **UnrelatedCode**.  
  
 **MyCode, Libraries et Unrelated**  
  
 Le **MyCode**, **bibliothèques**, et **Unrelated** paires clé / valeur spécifier les URL ou les fichiers que vous souhaitez inclure dans une classification :  
  
|||  
|-|-|  
|**MyCode**|Un tableau d’URL ou de fichiers qui sont classés comme **MyCode**.|  
|**Bibliothèques**|Un tableau d’URL ou de fichiers qui sont classés comme **LibraryCode**.|  
|**Non liées**|Un tableau d’URL ou de fichiers qui sont classés comme **UnrelatedCode**.|  
  
 La chaîne d'URL ou de fichiers peut contenir un ou plusieurs caractères `*`, qui correspondent à zéro ou plusieurs caractères. `*` est l'équivalent de l'expression régulière `.*`.
