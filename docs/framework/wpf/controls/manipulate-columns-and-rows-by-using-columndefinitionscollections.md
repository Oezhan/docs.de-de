---
title: 'Gewusst wie: Bearbeiten von Spalten und Zeilen mithilfe von ColumnDefinitionsCollections und RowDefinitionsCollections'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [WPF], Grid class
- Grid control [WPF], ColumnDefinitionCollection class
- Grid control [WPF], RowDefinitionCollection class
ms.assetid: bfc7160a-45f2-4e17-9961-df414dfb13c5
ms.openlocfilehash: 6ff5ad4825bd9f683d895341dd084c00f68aa27b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/04/2018
ms.locfileid: "33553074"
---
# <a name="how-to-manipulate-columns-and-rows-by-using-columndefinitionscollections-and-rowdefinitionscollections"></a>Gewusst wie: Bearbeiten von Spalten und Zeilen mithilfe von ColumnDefinitionsCollections und RowDefinitionsCollections
In diesem Beispiel wird gezeigt, wie die Methoden in der <xref:System.Windows.Controls.ColumnDefinitionCollection> und <xref:System.Windows.Controls.RowDefinitionCollection> Klassen zum Durchführen von Aktionen wie das Hinzufügen, löschen oder den Inhalt der Zeilen oder Spalten zu zählen. Sie können z. B. <xref:System.Windows.Controls.ColumnDefinitionCollection.Add%2A>, <xref:System.Windows.Controls.ColumnDefinitionCollection.Clear%2A>, oder <xref:System.Windows.Controls.ColumnDefinitionCollection.Count%2A> die Elemente, die in enthaltenen eine <xref:System.Windows.Controls.ColumnDefinition> oder <xref:System.Windows.Controls.RowDefinition>.  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel erstellt eine <xref:System.Windows.Controls.Grid> Element mit einem <xref:System.Windows.FrameworkElement.Name%2A> von `grid1`. Die <xref:System.Windows.Controls.Grid> enthält eine <xref:System.Windows.Controls.StackPanel> enthält <xref:System.Windows.Controls.Button> Elemente, jeweils durch eine andere Auflistungsmethode gesteuert. Beim Klicken auf eine <xref:System.Windows.Controls.Button>, wird der Aufruf einer Methode im Code-Behind-Datei aktiviert.  
  
 [!code-xaml[ColumnDefinitionsGrid#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ColumnDefinitionsGrid/CSharp/Window1.xaml#1)]  
  
 In diesem Beispiel definiert eine Reihe von benutzerdefinierten Methoden, die jeweils entsprechenden auf eine <xref:System.Windows.Controls.Primitives.ButtonBase.Click> Ereignis in der [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] Datei. Sie können ändern, die Anzahl der Zeilen und Spalten in der <xref:System.Windows.Controls.Grid> auf verschiedene Weise einschließlich hinzufügen oder Entfernen von Zeilen und Spalten und Zählung der Gesamtanzahl der Zeilen und Spalten. Um zu verhindern, dass <xref:System.ArgumentOutOfRangeException> und <xref:System.ArgumentException> Ausnahmen können Sie die Überprüfung von Fehlern Funktionalität, die die <xref:System.Windows.Controls.ColumnDefinitionCollection.RemoveRange%2A> Methode bietet.  
  
 [!code-csharp[ColumnDefinitionsGrid#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ColumnDefinitionsGrid/CSharp/Window1.xaml.cs#2)]
 [!code-vb[ColumnDefinitionsGrid#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ColumnDefinitionsGrid/VisualBasic/Window1.xaml.vb#2)]  
  
## <a name="see-also"></a>Siehe auch  
 <xref:System.Windows.Controls.Grid>  
 <xref:System.Windows.Controls.ColumnDefinitionCollection>  
 <xref:System.Windows.Controls.RowDefinitionCollection>
