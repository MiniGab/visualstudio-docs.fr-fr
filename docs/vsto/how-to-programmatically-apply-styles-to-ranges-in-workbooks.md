---
title: 'Comment : appliquer des styles à des plages dans les classeurs par programmation'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ranges, styles
- styles, workbook ranges
- workbooks, styles
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: d19c886a7b3ae1a1976ab2a47fe139ba830a4ea5
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/06/2018
ms.locfileid: "35671189"
---
# <a name="how-to-programmatically-apply-styles-to-ranges-in-workbooks"></a>Comment : appliquer des styles à des plages dans les classeurs par programmation
  Vous pouvez appliquer des styles nommés à des zones dans les classeurs. Excel fournit différents styles prédéfinis.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 La boîte de dialogue **Format de cellule** affiche toutes les options que vous pouvez utiliser pour formater des cellules, et chacune de ces options est disponible à partir de votre code. Pour afficher cette boîte de dialogue dans Excel, cliquez sur **Cellules** dans le menu **Format** .  
  
## <a name="to-apply-a-style-to-a-named-range-in-a-document-level-customization"></a>Pour appliquer un style à une plage nommée dans une personnalisation au niveau du document  
  
1.  Créez un style et définissez ses attributs.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#53](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#53)]
     [!code-vb[Trin_VstcoreExcelAutomation#53](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#53)]  
  
2.  Créez un contrôle <xref:Microsoft.Office.Tools.Excel.NamedRange>, affectez-lui du texte, puis appliquez le nouveau style. Ce code doit être placé dans une classe Sheet et non pas dans la classe `ThisWorkbook` .  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#54](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#54)]
     [!code-vb[Trin_VstcoreExcelAutomation#54](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#54)]  
  
## <a name="to-clear-a-style-from-a-named-range-in-a-document-level-customization"></a>Pour supprimer un style d'une plage nommée dans une personnalisation au niveau du document  
  
1.  Appliquez le style Normal à la plage. Ce code doit être placé dans une classe Sheet et non pas dans la classe `ThisWorkbook` .  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#55](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#55)]
     [!code-vb[Trin_VstcoreExcelAutomation#55](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#55)]  
  
## <a name="to-apply-a-style-to-a-named-range-in-a-vsto-add-in"></a>Pour appliquer un style à une plage nommée dans un complément VSTO  
  
1.  Créez un style et définissez ses attributs.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#28](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#28)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#28](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#28)]  
  
2.  Créez <xref:Microsoft.Office.Interop.Excel.Range>, affectez-lui du texte, puis appliquez le nouveau style.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#29](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#29)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#29](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#29)]  
  
## <a name="to-clear-a-style-from-a-named-range-in-a-vsto-add-in"></a>Pour supprimer un style à partir d’une plage nommée dans un complément, VSTO  
  
1.  Appliquez le style Normal à la plage.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#56](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#56)]
     [!code-vb[Trin_VstcoreExcelAutomation#56](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#56)]  
  
## <a name="see-also"></a>Voir aussi  
 [Travailler avec des plages](../vsto/working-with-ranges.md)   
 [NamedRange (contrôle)](../vsto/namedrange-control.md)   
 [Accès global aux objets dans les projets Office](../vsto/global-access-to-objects-in-office-projects.md)   
 [Paramètres optionnels dans les solutions Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  