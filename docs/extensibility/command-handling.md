---
title: Gestion des commandes | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - command handling
ms.assetid: 78f67d92-77f7-45cb-ad75-6e3346379cc3
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: a155927bb69c55c15a06cb058692038c8b309a30
ms.sourcegitcommit: 25a62c2db771f938e3baa658df8b1ae54a960e4f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2018
ms.locfileid: "39230867"
---
# <a name="command-handling"></a>Gestion des commandes
Votre éditeur peut définir de nouvelles commandes. Commandes sont généralement affichés dans un menu, une barre d’outils ou dans un menu contextuel.  
  
 Pour plus d’informations sur la définition des menus et commandes, consultez [commandes, menus et barres d’outils](../extensibility/internals/commands-menus-and-toolbars.md).  
  
 Un service de langage peut contrôler les menus contextuels sont affichés dans l’éditeur, en interceptant le <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> énumération. Alternativement, vous pouvez contrôler le menu contextuel sur une base par marqueur. Pour plus d’informations, consultez [commandes importantes pour les filtres de Service de langage](../extensibility/internals/important-commands-for-language-service-filters.md).  
  
## <a name="add-commands-to-the-editor-context-menu"></a>Ajouter des commandes au menu contextuel Éditeur  
 Pour ajouter une commande au menu contextuel, vous devez d’abord définir un ensemble de commandes de menu qui appartiennent à un groupe spécifique. L’exemple suivant provient de la *.vsct* fichier généré dans le cadre de la procédure pas à pas [procédure pas à pas : ajout de fonctionnalités à un éditeur personnalisé](../extensibility/walkthrough-adding-features-to-a-custom-editor.md):  
  
 \<Guid du menu = « guidCustomEditorCmdSet » id = « IDMX_RTF » priorité = « 0 x 0000 » type = « Contexte » >  
  
 \<Guid du parent = « guidCustomEditorCmdSet » id = « 0 » / >  
  
 \<Chaînes >  
  
 \<ButtonText > Menu contextuel de CustomEditor\</ButtonText >  
  
 \<CommandName > CustomEditorContextMenu\</CommandName >  
  
 \</ Chaînes >  
  
 \</ Menu >  
  
 \</ Menus >  
  
 Le texte ci-dessus ajoute une commande de menu contextuel avec le texte **Menu contextuel de CustomEditor**. Le GUID du Menu fait partie du jeu de commandes qui est créé avec cet éditeur. Le type est « Contexte ».  
  
 Vous pouvez également utiliser des commandes prédéfinies qui ne doivent être définis dans le *.vsct* fichier. Par exemple, examinez le *EditorPane.cs* fichier généré par le modèle de Package Visual Studio. Vous constaterez qu’un ensemble de commandes prédéfinies, telles que <xref:Microsoft.VisualStudio.VSConstants.VSStd97CmdID> défini par <xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97>, sont gérées dans les gestionnaires de commandes telles que le `onSelectAll` (méthode).  
  
## <a name="see-also"></a>Voir aussi  
 [Commandes, menus et barres d’outils](../extensibility/internals/commands-menus-and-toolbars.md)