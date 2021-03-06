---
title: Inscrivez une fenêtre outil | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- tool windows, registering managed
- tool windows, registering
ms.assetid: 8c8c4a24-3da4-497b-9db2-0ddd7cfbfdd2
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 17c9233d3df0bb7101b374fd1990536d2341fa49
ms.sourcegitcommit: 06db1892fff22572f0b0a11994dc547c2b7e2a48
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/08/2018
ms.locfileid: "39638327"
---
# <a name="register-a-tool-window"></a>Inscrire une fenêtre outil
Vous pouvez inscrire vos fenêtres Outil à l’aide de <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowAttribute> et <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowVisibilityAttribute>.  
  
## <a name="example"></a>Exemple  
  
```csharp
  
[ProvideToolWindow(typeof(PersistedWindowPane), Style = MsVsShell.VsDockStyle.Tabbed, Window = "3ae79031-e1bc-11d0-8f78-00a0c9110057")]
[ProvideToolWindow(typeof(DynamicWindowPane), PositionX=250, PositionY=250, Width=160, Height=180, Transient=true)]
[ProvideToolWindowVisibility(typeof(DynamicWindowPane), /*UICONTEXT_SolutionExists*/"f1536ef8-92ec-443c-9ed7-fdadf150da82")]  
[ProvideMenuResource(1000, 1)]  
[PackageRegistration(UseManagedResourcesOnly = true)]  
[Guid("01069CDD-95CE-4620-AC21-DDFF6C57F012")]  
public class PackageToolWindow : Package  
{  
```
  
 Dans le code ci-dessus, le <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowAttribute> inscrit le `PersistedWindowPane` et `DynamicWindowPane` outil windows avec Visual Studio. La fenêtre outil persistante est ancrée et à onglets avec **l’Explorateur de solutions**, et la fenêtre dynamique est donnée à partir de la position et la taille par défaut. La fenêtre dynamique est effectuée temporaire, ce qui indique qu’il n’est pas créé au démarrage. Écrit un `DontForceCreate` valeur dans le `ToolWindows` clé dans le Registre système. Pour plus d’informations, consultez [affichage configuration de la fenêtre outil](../extensibility/tool-window-display-configuration.md).
