---
title: 'Gewusst wie: Bestimmen des Bezugs zwischen zwei Objekten (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- inheritance [Visual Basic], Visual Basic objects
- objects [Visual Basic], inheritance
- object variables [Visual Basic], determining relation
ms.assetid: da002e3f-6616-4bad-a229-f842d06652bb
ms.openlocfilehash: 2041f89ffd954e479046eb85c6dd82de1f8793ca
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/04/2018
ms.locfileid: "33649824"
---
# <a name="how-to-determine-whether-two-objects-are-related-visual-basic"></a>Gewusst wie: Bestimmen des Bezugs zwischen zwei Objekten (Visual Basic)
Sie können vergleichen zwei Objekte, um die Beziehung zwischen den Klassen ggf. zu bestimmen, von denen sie erstellt werden. Die <xref:System.Type.IsInstanceOfType%2A> Methode der <xref:System.Type?displayProperty=nameWithType> zurück `True` , wenn die angegebene Klasse von der aktuellen Klasse erbt oder der aktuelle Typ eine Schnittstelle, die von der angegebenen Klasse unterstützt wird.  
  
### <a name="to-determine-if-one-object-inherits-from-another-objects-class-or-interface"></a>Um festzustellen, ob ein Objekt von einem anderen Objekt Klasse oder Schnittstelle erbt.  
  
1.  Für das Objekt, das Sie vorstellen des Basistyps sein kann, rufen die <xref:System.Object.GetType%2A> Methode.  
  
2.  Auf der <xref:System.Type?displayProperty=nameWithType> zurückgegebenes Objekt <xref:System.Object.GetType%2A>, rufen die <xref:System.Type.IsInstanceOfType%2A> Methode.  
  
3.  In der Argumentliste für <xref:System.Type.IsInstanceOfType%2A>, geben Sie das Objekt, das Sie denken möglicherweise des abgeleiteten Typs.  
  
     <xref:System.Type.IsInstanceOfType%2A> Gibt `True` wenn dessen Argumenttyp erbt die <xref:System.Type?displayProperty=nameWithType> Objekttyp.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird bestimmt, ob ein Objekt von einem anderen Objekt Klasse abgeleitete Klasse darstellt.  
  
```  
Public Class baseClass  
End Class  
Public Class derivedClass : Inherits baseClass  
End Class  
Public Class testTheseClasses  
    Public Sub seeIfRelated()  
        Dim baseObj As Object = New baseClass()  
        Dim derivedObj As Object = New derivedClass()  
        Dim related As Boolean  
        related = baseObj.GetType().IsInstanceOfType(derivedObj)  
        MsgBox(CStr(related))  
    End Sub  
End Class  
```  
  
 Beachten Sie die unerwartete Platzierung der beiden Objektvariablen im Aufruf von <xref:System.Type.IsInstanceOfType%2A>. Der angenommene Basistyp zum Generieren der <xref:System.Type?displayProperty=nameWithType> Klasse und der angenommene abgeleitete Typ wird als Argument übergeben der <xref:System.Type.IsInstanceOfType%2A> Methode.  
  
## <a name="see-also"></a>Siehe auch  
 <xref:System.Object.GetType%2A>  
 <xref:System.Type?displayProperty=nameWithType>  
 <xref:System.Type.IsInstanceOfType%2A>  
 [Object-Datentyp](../../../../visual-basic/language-reference/data-types/object-data-type.md)  
 [Objektvariablen](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)  
 [Werte von Objektvariablen](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md)  
 [Gewusst wie: Bestimmen der Gleichheit zweier Objekte](../../../../visual-basic/programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-identical.md)
