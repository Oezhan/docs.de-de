---
title: 'Gewusst wie: Interaktive Verwendung der Spring-Eigenschaft in StatusStrip'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- StatusStrip control [Windows Forms]
- ToolStrip control [Windows Forms]
- status bars [Windows Forms], examples
- Spring property [Windows Forms]
ms.assetid: 18bde842-a93c-48dd-9db3-15738a1775ce
ms.openlocfilehash: e3818beb96a7c005ea02bc04e9ea740b28a54707
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/04/2018
ms.locfileid: "33533795"
---
# <a name="how-to-use-the-spring-property-interactively-in-a-statusstrip"></a>Gewusst wie: Interaktive Verwendung der Spring-Eigenschaft in StatusStrip
Sie können die Eigenschaft <xref:System.Windows.Forms.ToolStripStatusLabel.Spring%2A> verwenden, um ein <xref:System.Windows.Forms.ToolStripStatusLabel>-Steuerelement in einem <xref:System.Windows.Forms.StatusStrip>-Steuerelement zu positionieren. Die Eigenschaft <xref:System.Windows.Forms.ToolStripStatusLabel.Spring%2A> bestimmt, ob das <xref:System.Windows.Forms.ToolStripStatusLabel>-Steuerelement den verfügbaren Platz für das <xref:System.Windows.Forms.StatusStrip>-Steuerelement ausfüllt.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Codebeispiel wird veranschaulicht, wie die Eigenschaft <xref:System.Windows.Forms.ToolStripStatusLabel.Spring%2A> zum Positionieren eines <xref:System.Windows.Forms.ToolStripStatusLabel>-Steuerelements in einem <xref:System.Windows.Forms.StatusStrip>-Steuerelement verwendet wird. Der <xref:System.Windows.Forms.ToolStripItem.Click>-Ereignishandler führt einen exklusiven oder Oder-Vorgang (XOR) aus, um den Wert der Eigenschaft <xref:System.Windows.Forms.ToolStripStatusLabel.Spring%2A> zu wechseln.  
  
 Um dieses Codebeispiel zu verwenden, kompilieren und führen Sie die Anwendung, und klicken Sie dann auf **Middle (Spring)** auf die <xref:System.Windows.Forms.StatusStrip> So wechseln Sie den Wert des Steuerelements die <xref:System.Windows.Forms.ToolStripStatusLabel.Spring%2A> Eigenschaft.  
  
 [!code-csharp[System.Windows.Forms.ToolStrip.Misc#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#1)]
 [!code-vb[System.Windows.Forms.ToolStrip.Misc#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#1)]  
[!code-csharp[System.Windows.Forms.ToolStrip.Misc#50](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#50)]
[!code-vb[System.Windows.Forms.ToolStrip.Misc#50](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#50)]  
  
## <a name="compiling-the-code"></a>Kompilieren des Codes  
 Für dieses Beispiel benötigen Sie Folgendes:  
  
-   Verweise auf die Assemblys "System.Design", "System.Drawing" und "System.Windows.Forms".  
  
 Informationen zum Erstellen dieses Beispiels über die Befehlszeile für Visual Basic oder Visual c# finden Sie unter [erstellen über die Befehlszeile](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) oder [Befehlszeile mit csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Sie können auch in diesem Beispiel in Visual Studio erstellen, indem Sie den Code in ein neues Projekt einfügen.  Siehe auch [Gewusst wie: Kompilieren und Ausführen eines vollständigen Windows Forms-Codebeispiels mit Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).  
  
## <a name="see-also"></a>Siehe auch  
 <xref:System.Windows.Forms.ToolStripStatusLabel>  
 <xref:System.Windows.Forms.StatusStrip>  
 <xref:System.Windows.Forms.ToolStrip>  
 <xref:System.Windows.Forms.ToolStripItem>  
 <xref:System.Windows.Forms.ToolStripMenuItem>  
 [ToolStrip-Steuerelement](../../../../docs/framework/winforms/controls/toolstrip-control-windows-forms.md)
