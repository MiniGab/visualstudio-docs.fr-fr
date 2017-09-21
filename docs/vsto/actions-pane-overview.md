---
title: Actions Pane Overview | Microsoft Docs
ms.custom: 
ms.date: 02/02/2017
ms.prod: visual-studio-dev14
ms.reviewer: 
ms.suite: 
ms.technology:
- office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- actions panes [Office development in Visual Studio], about actions panes
- actions panes [Office development in Visual Studio]
- smart documents [Office development in Visual Studio]
- user controls [Office development in Visual Studio], actions panes
ms.assetid: 1b9b7db5-b19f-44ea-a774-f0962ca03bd2
caps.latest.revision: 101
author: kempb
ms.author: kempb
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: eb5c9550fd29b0e98bf63a7240737da4f13f3249
ms.openlocfilehash: 89f1d8db1ebfce2fe27aa6762c6ebd95a0eacea0
ms.contentlocale: fr-fr
ms.lasthandoff: 08/30/2017

---
# <a name="actions-pane-overview"></a>Actions Pane Overview
  An actions pane is a customizable **Document Actions** task pane that is attached to a specific Microsoft Office Word document or Microsoft Office Excel workbook. It is hosted inside the Office task pane along with other built-in task panes such as the **XML Source** task pane in Excel or the **Styles and Formatting** task pane in Word. You can use Windows Forms controls or WPF controls to design the actions pane user interface.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 You can create an actions pane only in a document-level customization for Word or Excel. You cannot create an actions pane in a VSTO Add-in. For more information, see [Features Available by Office Application and Project Type](../vsto/features-available-by-office-application-and-project-type.md).  
  
> [!NOTE]  
>  The actions pane differs from custom task panes. Custom task panes are associated with the application, not a specific document. You can create custom task panes in VSTO Add-ins for some Microsoft Office applications. For more information, see [Custom Task Panes](../vsto/custom-task-panes.md).  
  
 ![link to video](../vsto/media/playvideo.gif "link to video") For a related video demonstration, see [How Do I: Use WPF Controls Inside an Excel Actions Pane?](http://go.microsoft.com/fwlink/?LinkId=132763).  
  
## <a name="displaying-the-actions-pane"></a>Displaying the Actions Pane  
 The actions pane is represented by the <xref:Microsoft.Office.Tools.ActionsPane> class. When you create a document-level project, an instance of this class is available to your code by using the `ActionsPane` field of the `ThisWorkbook` (for Excel) or `ThisDocument` (for Word) class in your project. To display the actions pane, add a Windows Forms control to the <xref:Microsoft.Office.Tools.ActionsPane.Controls%2A> property of the `ActionsPane` field. The following code example adds a control named `actions` to the actions pane.  
  
 [!code-csharp[Trin_VstcoreActionsPaneWord#7](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#7)] [!code-vb[Trin_VstcoreActionsPaneWord#7](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#7)]  
  
 The actions pane becomes visible at run time as soon as you explicitly add a control to it. After the actions pane is displayed, you can dynamically add or remove controls in response to the user's actions. Typically, you add the code to display the actions pane in the `Startup` event handler of `ThisDocument` or `ThisWorkbook` so that the actions pane is visible when the user first opens the document. However, you might want to display the actions pane only in response to a user's action in the document. For example, you might add the code to the `Click` event of a control on the document.  
  
### <a name="adding-multiple-controls-to-the-actions-pane"></a>Adding Multiple Controls to the Actions Pane  
 If you are adding multiple controls to the actions pane, in most cases you should group the controls in a user control, and then add the user control to the <xref:Microsoft.Office.Tools.ActionsPane.Controls%2A> property. This process includes the following steps:  
  
1.  Create the user interface (UI) of the actions pane by adding an **Actions Pane Control** or **User Control** item to your project. Both of these items include a custom Windows Forms <xref:System.Windows.Forms.UserControl> class. The **Actions Pane Control** and **User Control** items are equivalent; the only difference is their name.  
  
2.  Add Windows Forms controls to the <xref:System.Windows.Forms.UserControl> by using the designer, or by writing code.  
  
    > [!NOTE]  
    >  You can also add WPF controls to the actions pane by adding a WPF <xref:System.Windows.Controls.UserControl> to the Windows Forms <xref:System.Windows.Forms.UserControl>. For more information, see [Using WPF Controls in Office Solutions](../vsto/using-wpf-controls-in-office-solutions.md).  
  
3.  Add an instance of the custom user control to the controls that are contained in the `ActionsPane` field of the `ThisWorkbook` (for Excel) or `ThisDocument` (for Word) class in your project.  
  
 For examples that demonstrate this process in more detail, see [How to: Add an Actions Pane to Word Documents or Excel Workbooks](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md).  
  
## <a name="hiding-the-actions-pane"></a>Hiding the Actions Pane  
 Although the <xref:Microsoft.Office.Tools.ActionsPane> class has a <xref:Microsoft.Office.Tools.ActionsPane.Hide%2A> method and a <xref:Microsoft.Office.Tools.ActionsPane.Visible%2A> property, you cannot remove the actions pane from the user interface by using any members of the <xref:Microsoft.Office.Tools.ActionsPane> class itself. Calling the <xref:Microsoft.Office.Tools.ActionsPane.Hide%2A> method or setting the <xref:Microsoft.Office.Tools.ActionsPane.Visible%2A> property to **false** hides only the controls on the actions pane; it does not hide the task pane.  
  
 To hide the task pane in your solution, you have several options:  
  
-   For Word, set the <xref:Microsoft.Office.Interop.Word.TaskPane.Visible%2A> property of the <xref:Microsoft.Office.Interop.Word.TaskPane> object that represents the Document Actions task pane to **false**. The following code example is intended to be run from the `ThisDocument` class in your project.  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#34](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#34)]  [!code-vb[Trin_VstcoreActionsPaneWord#34](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#34)]  
  
-   For Excel, set the <xref:Microsoft.Office.Interop.Excel._Application.DisplayDocumentActionTaskPane%2A> property of the <xref:Microsoft.Office.Tools.Excel.Workbook.Application%2A> object to **false**. The following code example is intended to be run from the `ThisWorkbook` class in your project.  
  
     [!code-csharp[Trin_VstcoreActionsPaneExcel#11](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneExcelCS/ThisWorkbook.cs#11)]  [!code-vb[Trin_VstcoreActionsPaneExcel#11](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneExcelVB/ThisWorkbook.vb#11)]  
  
-   For Word or Excel, you can alternatively set the <xref:Microsoft.Office.Core.CommandBar.Visible%2A> property of the command bar that represents the task pane to **false**. The following code example is intended to be run from the `ThisDocument` or `ThisWorkbook` class in your project.  
  
     [!code-csharp[Trin_VstcoreActionsPaneExcel#9](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneExcelCS/ThisWorkbook.cs#9)]  [!code-vb[Trin_VstcoreActionsPaneExcel#9](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneExcelVB/ThisWorkbook.vb#9)]  
  
### <a name="clearing-the-actions-pane-when-the-document-is-opened"></a>Clearing the Actions Pane When the Document is Opened  
 If the user saves the document while the actions pane is visible, the actions pane is visible every time the document is opened, whether or not the actions pane contains any controls. If you want to control when it appears, call the <xref:Microsoft.Office.Tools.ActionsPane.Clear%2A> method of the `ActionsPane` field in the `Startup` event handler of `ThisDocument` or `ThisWorkbook` to ensure that the actions pane is not visible when the document is opened.  
  
### <a name="determining-when-the-actions-pane-is-closed"></a>Determining When the Actions Pane is Closed  
 There is no event that is raised when the actions pane is closed. Although the <xref:Microsoft.Office.Tools.ActionsPane> class has a <xref:Microsoft.Office.Tools.ActionsPane.VisibleChanged> event, this event is not raised when the end user closes the actions pane. Instead, this event is raised when the controls on the actions pane are hidden by calling the <xref:Microsoft.Office.Tools.ActionsPane.Hide%2A> method or by setting the <xref:Microsoft.Office.Tools.ActionsPane.Visible%2A> property to **false**.  
  
 If the end user closes the actions pane, the user can display it again by performing one of the following procedures in the user interface (UI) of the application.  
  
##### <a name="to-display-the-actions-pane-by-using-the-ui-of-word-or-excel"></a>To display the actions pane by using the UI of Word or Excel  
  
1.  On the Ribbon, click the **View** tab.  
  
2.  In the **Show/Hide** group, click the **Document Actions** toggle button.  
  
## <a name="programming-actions-pane-events"></a>Programming Actions Pane Events  
 You can add multiple user controls to the actions pane and then write code to respond to events on the document by showing and hiding the user controls. If you map XML schema elements to your document, you can show certain user controls in the actions pane whenever the insertion point is inside one of the XML elements. For more information, see [How to: Map Schemas to Word Documents Inside Visual Studio](../vsto/how-to-map-schemas-to-word-documents-inside-visual-studio.md) and [How to: Map Schemas to Worksheets Inside Visual Studio](../vsto/how-to-map-schemas-to-worksheets-inside-visual-studio.md).  
  
 You can also write code to respond to the events of any object, including host control, application, or document events. For more information see [Walkthrough: Programming Against Events of a NamedRange Control](../vsto/walkthrough-programming-against-events-of-a-namedrange-control.md).  
  
## <a name="binding-data-to-controls-on-the-actions-pane"></a>Binding Data to Controls on the Actions Pane  
 The controls on the actions pane have the same data binding capabilities as controls on Windows Forms. You can bind the controls to data sources such as data sets, typed data sets, and XML. For more information, see [Data Binding and Windows Forms](/dotnet/framework/winforms/data-binding-and-windows-forms).  
  
 You can bind controls on the actions pane and controls on the document to the same dataset. For example, you can create a master/detail relation between the controls on the actions pane and the controls on the worksheet. For more information, see [Walkthrough: Binding Data to Controls on an Excel Actions Pane](../vsto/walkthrough-binding-data-to-controls-on-an-excel-actions-pane.md).  
  
## <a name="validating-data-in-actions-pane-controls"></a>Validating Data in Actions Pane Controls  
 If you display a message box in the <xref:System.Windows.Forms.Control.Validating> event handler of a control on the actions pane, the event might be raised a second time when focus moves from the control to the message box. To prevent this issue, use an <xref:System.Windows.Forms.ErrorProvider> control to display any validation error messages.  
  
## <a name="user-control-stacking-order"></a>User Control Stacking Order  
 If you are using multiple user controls, you can write code to properly stack the user controls on the actions pane whether it is docked vertically or horizontally. You can set the stacking order of the user controls on the actions pane by using the <xref:Microsoft.Office.Tools.StackStyle> enumeration of the <xref:Microsoft.Office.Tools.ActionsPane.StackOrder%2A> property. For more information, see [How to: Manage Control Layout on Actions Panes](../vsto/how-to-manage-control-layout-on-actions-panes.md)  
  
 The <xref:Microsoft.Office.Tools.ActionsPane.StackOrder%2A> property can take the following <xref:Microsoft.Office.Tools.StackStyle> enumeration values.  
  
|Stacking style|Definition|  
|--------------------|----------------|  
|FromBottom|Stack from the bottom of the actions pane.|  
|FromLeft|Stack from the left of the actions pane.|  
|FromRight|Stack from the right of the actions pane.|  
|FromTop|Stack from the top of the actions pane.|  
|None|No stacking order defined; order is controlled by the developer.|  
  
 The following code sets the <xref:Microsoft.Office.Tools.ActionsPane.StackOrder%2A> property to stack the user controls from the top of the actions pane.  
  
 [!code-csharp[Trin_VstcoreActionsPaneExcel#10](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneExcelCS/ThisWorkbook.cs#10)] [!code-vb[Trin_VstcoreActionsPaneExcel#10](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneExcelVB/ThisWorkbook.vb#10)]  
  
## <a name="anchoring-controls"></a>Anchoring Controls  
 If the user resizes the actions pane at run time, the controls can resize with the actions pane. You can use the <xref:System.Windows.Forms.Control.Anchor%2A> property of a Windows Forms control to anchor controls to the actions pane. You can also anchor the Windows Forms controls onto the user control in the same manner. For more information, see [How to: Anchor Controls on Windows Forms](/dotnet/framework/winforms/controls/how-to-anchor-controls-on-windows-forms).  
  
## <a name="resizing-the-actions-pane"></a>Resizing the Actions Pane  
 You cannot directly change the size of an <xref:Microsoft.Office.Tools.ActionsPane> because the <xref:Microsoft.Office.Tools.ActionsPane> is embedded in the task pane. However, you can programmatically change the width of the task pane by setting the <xref:Microsoft.Office.Core.CommandBar.Width%2A> property of the <xref:Microsoft.Office.Core.CommandBar> that represents the task pane. You can change the height of the task pane if it is docked horizontally or is floating.  
  
 Programmatically resizing the task pane is generally not recommended because the user should be able to select the task pane size that best suits his or her needs. However, if you must resize the width of the task pane, you could use the following code to achieve this task.  
  
 [!code-csharp[Trin_VstcoreActionsPaneWord#102](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#102)] [!code-vb[Trin_VstcoreActionsPaneWord#102](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#102)]  
  
## <a name="repositioning-the-actions-pane"></a>Repositioning the Actions Pane  
 You cannot directly reposition the <xref:Microsoft.Office.Tools.ActionsPane> because it is embedded in the task pane. However, you can programmatically move the task pane by setting the <xref:Microsoft.Office.Core.CommandBar.Position%2A> property of the <xref:Microsoft.Office.Core.CommandBar> that represents the task pane.  
  
 Programmatically repositioning the task pane is generally not recommended because the user should be able to choose the task pane position on the screen that best suits his or her needs. However, if you must move the task pane to a particular position, you could use the following code to achieve this task.  
  
 [!code-csharp[Trin_VstcoreActionsPaneWord#100](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#100)] [!code-vb[Trin_VstcoreActionsPaneWord#100](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#100)]  
  
> [!NOTE]  
>  End users can manually reposition the task pane at any time. There is no way to ensure that the task pane will remain docked at the position you indicate programmatically. However, you can check for orientation changes and ensure that the controls on the actions pane are stacked in the correct direction. For more information, see [How to: Manage Control Layout on Actions Panes](../vsto/how-to-manage-control-layout-on-actions-panes.md).  
  
 Setting the <xref:Microsoft.Office.Tools.ActionsPane.Top%2A> and <xref:Microsoft.Office.Tools.ActionsPane.Left%2A> properties of the <xref:Microsoft.Office.Tools.ActionsPane> does not change its position because the <xref:Microsoft.Office.Tools.ActionsPane> object is embedded in the task pane.  
  
 If the task pane is not docked, you can set the <xref:Microsoft.Office.Core.CommandBar.Top%2A> and <xref:Microsoft.Office.Core.CommandBar.Left%2A> properties of the <xref:Microsoft.Office.Core.CommandBar> that represents the task pane. The following code moves an undocked task pane to the upper-left corner of the document.  
  
 [!code-csharp[Trin_VstcoreActionsPaneWord#101](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#101)] [!code-vb[Trin_VstcoreActionsPaneWord#101](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#101)]  
  
## <a name="see-also"></a>See Also  
 [Using WPF Controls in Office Solutions](../vsto/using-wpf-controls-in-office-solutions.md)   
 [Office UI Customization](../vsto/office-ui-customization.md)   
 [Global Access to Objects in Office Projects](../vsto/global-access-to-objects-in-office-projects.md)   
 [How to: Add an Actions Pane to Word Documents or Excel Workbooks](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)   
 [Walkthrough: Inserting Text into a Document from an Actions Pane](../vsto/walkthrough-inserting-text-into-a-document-from-an-actions-pane.md)   
 [Walkthrough: Binding Data to Controls on a Word Actions Pane](../vsto/walkthrough-binding-data-to-controls-on-a-word-actions-pane.md)   
 [Walkthrough: Binding Data to Controls on an Excel Actions Pane](../vsto/walkthrough-binding-data-to-controls-on-an-excel-actions-pane.md)   
 [How to: Manage Control Layout on Actions Panes](../vsto/how-to-manage-control-layout-on-actions-panes.md)   
 [Walkthrough: Inserting Text into a Document from an Actions Pane](../vsto/walkthrough-inserting-text-into-a-document-from-an-actions-pane.md)  
  
  