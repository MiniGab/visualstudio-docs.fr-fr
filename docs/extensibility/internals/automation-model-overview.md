---
title: Vue d’ensemble du modèle Automation | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- automation [Visual Studio SDK], about automation
- extensibility
ms.assetid: 12b6d6db-0d22-4aaa-aa7d-1365f759b7b0
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 661c870b19760b8a91c0e9e9e162076c641864a3
ms.sourcegitcommit: 3dd15e019cba7d35dbabc1aa3bf55842a59f5278
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46370694"
---
# <a name="automation-model-overview"></a>Vue d’ensemble du modèle Automation
Le modèle automation se compose d’un ensemble d’objets par rapport à laquelle vous pouvez écrire un complément Visual Studio ou une extension. Un complément est une application qui peut manipuler l’environnement Visual Studio et automatiser les tâches courantes. Une extension Visual Studio peut créer des composants personnalisés de Visual Studio ou ajouter des fonctionnalités de composants standard tels que l’éditeur de texte.  
  
## <a name="objects-in-the-automation-model"></a>Objets dans le modèle automation  
 Le modèle automation se compose de groupes connexes d’objets qui contrôlent les aspects de l’environnement du common. Le diagramme suivant illustre l’ensemble complet d’objets de Visual Studio qui composent le modèle automation.  
  
 ![Le graphique d’objet automation Visual Studio](../../extensibility/internals/media/vsvisualstudioautomationobjectchart.gif "vsVisualStudioAutomationObjectChart")  
  
 Pour plus d’informations, consultez [étendre l’environnement Visual Studio](https://msdn.microsoft.com/Library/4173a963-7ac7-4966-9bb7-e28a9d9f6792).  
  
 L’environnement fournit un modèle pour les différentes zones fonctionnelles. Par exemple, il est un modèle de code pour divers éléments que vous pouvez trouver dans le code. Il existe un modèle de document pour différents éléments de document. Une zone, la zone de projet est un intérêt particulier pour les fournisseurs de VSPackage. Il est probable que vos nouveaux types de projet pour contribuer au modèle automation dans la même façon que [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] et [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] contribuer au modèle automation. Que le processus est décrit dans [fournir l’automatisation pour VSPackages](../../extensibility/internals/providing-automation-for-vspackages.md).  
  
 Endroits où vous pouvez envisager d’extension du modèle automation de l’environnement :  
  
-   Projet  
  
-   Document  
  
-   Code  
  
-   Build  

  
Pour plus d’informations sur l’automatisation, consultez [automatisation et extensibilité pour Visual Studio](../extensibility-in-visual-studio.md). Ce document et les documents, il fournit des liens pour vous aider à prendre des décisions concernant la façon dont vous devez fournir l’automation pour votre VSPackage.  
  
## <a name="see-also"></a>Voir aussi  
 [Comment : créer un complément](https://msdn.microsoft.com/Library/50be56d2-e3a5-4cd2-8569-2a0666b268ce)