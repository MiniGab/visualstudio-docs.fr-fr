---
title: 'Comment : ouvrir des classeurs par programmation'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- workbooks, opening
- Excel [Office development in Visual Studio], opening workbooks
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: cd8f6786bd2f7b54ce6b50f2493ebd5d45bba51e
ms.sourcegitcommit: 34f7d23ce3bd140dcae875b602d5719bb4363ed1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/11/2018
ms.locfileid: "35257356"
---
# <a name="how-to-programmatically-open-workbooks"></a>Comment : ouvrir des classeurs par programmation
  Le <xref:Microsoft.Office.Interop.Excel.Workbooks> collection dans Microsoft Office Excel permet de travailler avec tous les classeurs ouverts et d’ouvrir des classeurs.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## <a name="to-open-an-existing-workbook"></a>Pour ouvrir un classeur existant  
  
1.  Utilisez le <xref:Microsoft.Office.Interop.Excel.Workbooks.Open%2A> méthode de la <xref:Microsoft.Office.Interop.Excel.Workbooks> collection, en passant le chemin d’accès au classeur.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#2](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#2)]
     [!code-vb[Trin_VstcoreExcelAutomation#2](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#2)]  
  
## <a name="compile-the-code"></a>Compiler le code  
 Cet exemple de code doit respecter la condition suivante :  
  
-   Un classeur nommé `YourWorkbook.xls` doit exister dans un répertoire nommé `Test` sur le lecteur C.  
  
## <a name="see-also"></a>Voir aussi  
 [Travailler avec des classeurs](../vsto/working-with-workbooks.md)   
 [Comment : ouvrir des fichiers texte en tant que classeurs par programmation](../vsto/how-to-programmatically-open-text-files-as-workbooks.md)   
 [Comment : créer par programmation des classeurs](../vsto/how-to-programmatically-create-new-workbooks.md)   
 [Comment : enregistrer des classeurs par programmation](../vsto/how-to-programmatically-save-workbooks.md)   
 [Comment : fermer des classeurs par programmation](../vsto/how-to-programmatically-close-workbooks.md)   
 [Limitations de programmation des éléments hôtes et contrôles hôtes](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Paramètres optionnels dans les solutions Office](../vsto/optional-parameters-in-office-solutions.md)   
 [Éléments hôtes et la vue d’ensemble des contrôles hôtes](../vsto/host-items-and-host-controls-overview.md)  
  
  