---
title: Kovarianz und Kontravarianz in Generika
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- generics, covariance and contravariance
- generics, variance
- covariance and contravariance in generics
- generic type parameters
ms.assetid: 2678dc63-c7f9-4590-9ddc-0a4df684d42e
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6c50d79f402d55a2fb5e859da4d61b04eeeb6931
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/04/2018
ms.locfileid: "33579742"
---
# <a name="covariance-and-contravariance-in-generics"></a>Kovarianz und Kontravarianz in Generika
<a name="top"></a> Kovarianz und Kontravarianz sind Begriffe, die auf die Fähigkeit Bezug nehmen, einen stärker abgeleiteten (spezifischeren) oder einen weniger abgeleiteten (allgemeineren) Typ zu verwenden als ursprünglich angegeben. Generische Typparameter unterstützen Kovarianz und Kontravarianz und bieten somit mehr Flexibilität beim Zuweisen und Verwenden von generischen Typen. Wenn Sie auf ein Typsystem verweisen, haben Kovarianz, Kontravarianz und Invarianz die folgenden Definitionen. In den Beispielen wird von der Basisklasse `Base` und der abgeleiteten Klasse `Derived`ausgegangen.  
  
-   `Covariance`  
  
     Ermöglicht die Verwendung eines stärker abgeleiteten Typs als ursprünglich angegeben.  
  
     Sie können eine Instanz von `IEnumerable<Derived>` (`IEnumerable(Of Derived)` in Visual Basic) einer Variablen des Typs `IEnumerable<Base>`zuweisen.  
  
-   `Contravariance`  
  
     Ermöglicht die Verwendung eines generischeren (weniger stark abgeleiteten) Typs als ursprünglich angegeben.  
  
     Sie können eine Instanz von `IEnumerable<Base>` (`IEnumerable(Of Base)` in Visual Basic) einer Variablen des Typs `IEnumerable<Derived>`zuweisen.  
  
-   `Invariance`  
  
     Bedeutet, dass nur der ursprünglich angegebene Typ verwendet werden kann. Ein invarianter generischer Typparameter ist also weder kovariant noch kontravariant.  
  
     Sie können eine Instanz von `IEnumerable<Base>` (`IEnumerable(Of Base)` in Visual Basic) nicht einer Variablen des Typs `IEnumerable<Derived>` zuweisen oder umgekehrt.  
  
 Kovariante Typparameter ermöglichen es Ihnen, Zuweisungen vorzunehmen, die normaler [Polymorphie](~/docs/csharp/programming-guide/classes-and-structs/polymorphism.md) stark ähneln, wie im folgenden Code dargestellt.  
  
 [!code-csharp[CoContraSimpleIEnum#1](../../../samples/snippets/csharp/VS_Snippets_CLR/cocontrasimpleienum/cs/example.cs#1)]
 [!code-vb[CoContraSimpleIEnum#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/cocontrasimpleienum/vb/example.vb#1)]  
  
 Die <xref:System.Collections.Generic.List%601> -Klasse implementiert die generische <xref:System.Collections.Generic.IEnumerable%601> -Schnittstelle. `List<Derived>` (`List(Of Derived)` in Visual Basic) implementiert daher `IEnumerable<Derived>`. Der kovariante Typparameter ist für den Rest zuständig.  
  
 Kontravarianz erscheint dagegen kontraintuitiv. Im folgenden Beispiel wird ein Delegat des `Action<Base>` -Typs (`Action(Of Base)` in Visual Basic) erstellt und dann einer Variable des `Action<Derived>`-Typs zugewiesen.  
  
 [!code-csharp[CoContraSimpleAction#1](../../../samples/snippets/csharp/VS_Snippets_CLR/cocontrasimpleaction/cs/example.cs#1)]
 [!code-vb[CoContraSimpleAction#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/cocontrasimpleaction/vb/example.vb#1)]  
  
 Das erscheint rückständig, ist aber typsicherer Code, der kompiliert und ausgeführt wird. Der Lambda-Ausdruck entspricht dem ihm zugewiesenen Delegaten und definiert daher eine Methode, die einen Parameter des `Base`-Typs akzeptiert und keinen Wert zurückgibt. Der resultierende Delegat kann einer Variable des `Action<Derived>` -Typs zugewiesen werden, da der Typparameter `T` des <xref:System.Action%601> -Delegaten kontravariant ist. Der Code ist typsicher, da `T` einen Parametertyp angibt. Wenn der Delegat des `Action<Base>` -Typs wie ein Delegat des `Action<Derived>`-Typs aufgerufen wird, muss sein Argument vom `Derived`-Typ sein. Dieses Argument kann immer sicher an die zugrunde liegende Methode übergeben werden, da der Parameter der Methode vom `Base`-Typ ist.  
  
 Im Allgemeinen können kovariante Typparameter als Rückgabetyp eines Delegaten und kontravariante Typparameter als Parametertypen verwendet werden. Für eine Schnittstelle können kovariante Typparameter als Rückgabetypen der Methoden der Schnittstelle verwendet werden und kontravariante Typparameter als Parametertypen der Methoden der Schnittstelle.  
  
 Kovarianz und Kontravarianz werden zusammen als *Varianz* bezeichnet. Ein generischer Typparameter, der nicht als kovariant oder kontravariant markiert ist, wird als *invariant*bezeichnet. Im Folgenden sehen Sie eine kurze Zusammenfassung der Fakten zur Varianz in der Common Language Runtime:  
  
-   In [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)]sind variante Typparameter auf generische Schnittstellen und generische Delegattypen beschränkt.  
  
-   Eine generische Schnittstelle oder ein generischer Delegattyp kann sowohl kovariante, als auch kontravariante Typparameter haben.  
  
-   Varianz gilt nur für Verweistypen. Wenn Sie für einen varianten Typparameter einen Werttyp angeben, ist dieser Typparameter für den resultierenden konstruierten Typ invariant.  
  
-   Varianz gilt nicht für eine Delegatkombination. Bei zwei Delegaten vom Typ `Action<Derived>` und `Action<Base>` (`Action(Of Derived)` und `Action(Of Base)` in Visual Basic) können Sie folglich den zweiten Delegaten nicht mit dem ersten kombinieren, obwohl das Ergebnis typsicher wäre. Bei Varianz kann der zweite Delegat einer Variable des `Action<Derived>`-Typs zugewiesen werden, Delegaten können aber nur kombiniert werden, wenn ihre Typen genau überstimmen.  
  
 In den folgenden Unterabschnitten werden Kovariante und kontravariante Typparameter ausführlich beschrieben:  
  
-   [Generische Schnittstellen mit kovarianten Typparametern](#InterfaceCovariantTypeParameters)  
  
-   [Generische Schnittstellen mit kontravarianten generischen Typparametern](#InterfaceCovariantTypeParameters)  
  
-   [Generische Delegaten mit varianten Typparametern](#DelegateVariantTypeParameters)  
  
-   [Definieren von varianten generischen Schnittstellen und Delegaten](#DefiningVariantTypeParameters)  
  
-   [Liste der varianten generischen Schnittstellen und Delegattypen](#VariantList)  
  
<a name="InterfaceCovariantTypeParameters"></a>   
## <a name="generic-interfaces-with-covariant-type-parameters"></a>Generische Schnittstellen mit kovarianten Typparametern  
 Beginnend mit [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)]verfügen mehrere generische Schnittstellen über kovariante Typparameter, z. B. <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.Generic.IEnumerator%601>, <xref:System.Linq.IQueryable%601>und <xref:System.Linq.IGrouping%602>. Alle Typparameter dieser Schnittstellen sind kovariant, sodass sie nur für die Rückgabetypen der Member verwendet werden.  
  
 Im folgenden Beispiel werden kovariante Typparameter veranschaulicht. Im Beispiel werden zwei Typen definiert: `Base` verfügt über eine statische Methode mit dem Namen `PrintBases` , die einen `IEnumerable<Base>` (`IEnumerable(Of Base)` in Visual Basic) erwartet und die Elemente ausgibt. `Derived` erbt von `Base`. Im Beispiel wird ein leerer `List<Derived>` (`List(Of Derived)` in Visual Basic) erstellt, um zu veranschaulichen, dass dieser Typ an `PrintBases` übergeben und ohne Umwandlung einer Variablen vom Typ `IEnumerable<Base>` zugewiesen werden kann. <xref:System.Collections.Generic.List%601> implementiert <xref:System.Collections.Generic.IEnumerable%601>, die über einen einzelnen kovarianten Typparameter verfügt. Aufgrund des kovarianten Typparameters kann eine Instanz von `IEnumerable<Derived>` anstelle von `IEnumerable<Base>`verwendet werden.  
  
 [!code-csharp[CoContravarianceInClrGenericI#1](../../../samples/snippets/csharp/VS_Snippets_CLR/cocontravarianceinclrgenerici/cs/example.cs#1)]
 [!code-vb[CoContravarianceInClrGenericI#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/cocontravarianceinclrgenerici/vb/example.vb#1)]  
  
 [Zurück zum Anfang](#top)  
  
<a name="InterfaceContravariantTypeParameters"></a>   
## <a name="generic-interfaces-with-contravariant-generic-type-parameters"></a>Generische Schnittstellen mit kontravarianten generischen Typparametern  
 Beginnend mit [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)]verfügen mehrere generische Schnittstellen über kontravariante Typparameter, z. B. <xref:System.Collections.Generic.IComparer%601>, <xref:System.IComparable%601>, and <xref:System.Collections.Generic.IEqualityComparer%601>. Diese Schnittstellen verfügen nur über kontravariante Typparameter. Die Typparameter werden daher nur in den Membern der Schnittstellen als Parametertypen verwendet.  
  
 Im folgenden Beispiel werden kontravariante Typparameter veranschaulicht. Im Beispiel wird eine abstrakte (`MustInherit` in Visual Basic) `Shape` -Klasse mit einer `Area` -Eigenschaft definiert. Außerdem wird eine `ShapeAreaComparer` -Klasse definiert, die `IComparer<Shape>` (`IComparer(Of Shape)` in Visual Basic) implementiert. Die Implementierung der <xref:System.Collections.Generic.IComparer%601.Compare%2A?displayProperty=nameWithType>-Methode basiert auf dem Wert der `Area`-Eigenschaft, sodass `ShapeAreaComparer` zum Sortieren von `Shape`-Objekten nach der Fläche verwendet werden kann.  
  
 Die `Circle` -Klasse erbt von `Shape` und überschreibt `Area`. Im Beispiel wird ein <xref:System.Collections.Generic.SortedSet%601> von `Circle` -Objekten erstellt, wobei ein Konstruktor verwendet wird, der `IComparer<Circle>` (`IComparer(Of Circle)` in Visual Basic) akzeptiert. Anstelle von `IComparer<Circle>` wird jedoch ein `ShapeAreaComparer`-Objekt übergeben, das `IComparer<Shape>` implementiert. Im Beispiel kann ein Vergleich eines weniger stark abgeleiteten Typs (`Shape`) übergeben werden, wenn der Code einen Vergleich eines stärker abgeleiteten Typs (`Circle`) verlangt, da der Typparameter der generischen <xref:System.Collections.Generic.IComparer%601> -Schnittstelle kontravariant ist.  
  
 Wenn `Circle` ein neues `SortedSet<Circle>`-Objekt hinzugefügt wird, wird die `IComparer<Shape>.Compare` -Methode (`IComparer(Of Shape).Compare` -Methode in Visual Basic) des `ShapeAreaComparer` -Objekts immer dann aufgerufen, wenn das neue Element mit einem vorhandenen Element verglichen wird. Der Parametertyp der Methode (`Shape`) ist weniger stark abgeleitet als der Typ, der übergeben wird (`Circle`). Deshalb ist der Aufruf typsicher. Kontravarianz ermöglicht es `ShapeAreaComparer` , eine Auflistung eines einzelnen Typs sowie eine Auflistung von gemischten Typen zu sortieren, die von `Shape`abgeleitet werden.  
  
 [!code-csharp[CoContravarianceInClrGenericI2#1](../../../samples/snippets/csharp/VS_Snippets_CLR/cocontravarianceinclrgenerici2/cs/example.cs#1)]
 [!code-vb[CoContravarianceInClrGenericI2#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/cocontravarianceinclrgenerici2/vb/example.vb#1)]  
  
 [Zurück zum Anfang](#top)  
  
<a name="DelegateVariantTypeParameters"></a>   
## <a name="generic-delegates-with-variant-type-parameters"></a>Generische Delegaten mit varianten Typparametern  
 In [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)]verfügen die generischen `Func` -Delegaten (z. B. <xref:System.Func%602>) über kovariante Rückgabetypen und über kontravariante Parametertypen. Die generischen `Action` -Delegaten, z. B. <xref:System.Action%602>, verfügen über kontravariante Parametertypen. Das bedeutet, dass die Delegaten Variablen mit weiter abgeleiteten Parametertypen und (im Fall von generischen `Func`-Delegaten) weniger abgeleiteten Rückgabetypen zugewiesen werden können.  
  
> [!NOTE]
>  Der letzte generische Typparameter der generischen `Func` -Delegaten gibt den Typ des Rückgabewerts in der Signatur des Delegaten an. Er ist kovariant (Schlüsselwort`out` ), wohingegen die anderen generischen Typparameter kontravariant sind (Schlüsselwort`in` ).  
  
 Dies wird im folgenden Code veranschaulicht. Im ersten Codeabschnitt wird eine Klasse mit dem Namen `Base`, eine Klasse mit dem Namen `Derived` , die `Base`erbt, und eine weitere Klasse mit einer `static` -Methode (`Shared` in Visual Basic) mit dem Namen `MyMethod`definiert. Die Methode akzeptiert eine Instanz von `Base` und gibt eine Instanz von `Derived` zurück. (Wenn das Argument eine Instanz von `Derived` ist, gibt `MyMethod` diese zurück. Wenn das Argument eine Instanz von `Base` ist, gibt `MyMethod` eine neue Instanz von `Derived` zurück.) Im Beispiel wird in `Main()` eine Instanz von `Func<Base, Derived>` (`Func(Of Base, Derived)` in Visual Basic) erstellt, die `MyMethod` darstellt und in der Variablen `f1` gespeichert wird.  
  
 [!code-csharp[CoContravarianceDelegates#2](../../../samples/snippets/csharp/VS_Snippets_CLR/cocontravariancedelegates/cs/example.cs#2)]
 [!code-vb[CoContravarianceDelegates#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/cocontravariancedelegates/vb/example.vb#2)]  
  
 Der zweite Codeabschnitt zeigt, dass der Delegat einer Variablen vom Typ `Func<Base, Base>` (`Func(Of Base, Base)` in Visual Basic) zugewiesen werden kann, da der Rückgabetyp kovariant ist.  
  
 [!code-csharp[CoContravarianceDelegates#3](../../../samples/snippets/csharp/VS_Snippets_CLR/cocontravariancedelegates/cs/example.cs#3)]
 [!code-vb[CoContravarianceDelegates#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/cocontravariancedelegates/vb/example.vb#3)]  
  
 Der dritte Codeabschnitt zeigt, dass der Delegat einer Variablen vom Typ `Func<Derived, Derived>` (`Func(Of Derived, Derived)` in Visual Basic) zugewiesen werden kann, da der Parametertyp kontravariant ist.  
  
 [!code-csharp[CoContravarianceDelegates#4](../../../samples/snippets/csharp/VS_Snippets_CLR/cocontravariancedelegates/cs/example.cs#4)]
 [!code-vb[CoContravarianceDelegates#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/cocontravariancedelegates/vb/example.vb#4)]  
  
 Der letzte Codeabschnitt zeigt, dass der Delegat einer Variablen vom Typ `Func<Derived, Base>` (`Func(Of Derived, Base)` in Visual Basic) zugewiesen werden kann, wobei die Auswirkungen des kontravarianten Parametertyps und des kovarianten Rückgabewerttyps kombiniert werden.  
  
 [!code-csharp[CoContravarianceDelegates#5](../../../samples/snippets/csharp/VS_Snippets_CLR/cocontravariancedelegates/cs/example.cs#5)]
 [!code-vb[CoContravarianceDelegates#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/cocontravariancedelegates/vb/example.vb#5)]  
  
### <a name="variance-in-generic-and-non-generic-delegates"></a>Varianz in generischen und nicht generischen Delegaten  
 Im obigen Code passt die Signatur von `MyMethod` exakt zur Signatur des erstellten generischen Delegaten `Func<Base, Derived>` (`Func(Of Base, Derived)` in Visual Basic). Das Beispiel zeigt, dass dieser generische Delegat in Variablen oder Methodenparametern mit weiter abgeleiteten Parametertypen und weniger abgeleiteten Rückgabetypen gespeichert werden kann, solange alle Delegattypen aus dem generischen Delegattyp <xref:System.Func%602>erstellt werden.  
  
 Dies ist ein wichtiger Punkt. Kovarianz und Kontravarianz haben in den Typparametern generischer Delegaten ähnliche Auswirkungen wie bei der normalen Delegatbindung (siehe [Varianz in Delegaten](https://msdn.microsoft.com/library/e3b98197-6c5b-4e55-9c6e-9739b60645ca)). Die Varianz bei der Delegatbindung funktioniert jedoch bei allen Delegattypen und nicht nur bei generischen Delegattypen, die über variante Typparameter verfügen. Darüber hinaus kann durch die Varianz bei der Delegatbindung eine Methode an einen beliebigen Delegaten gebunden werden, der restriktivere Parametertypen und einen weniger restriktiven Rückgabetyp verwendet, wohingegen die Zuweisung generischer Delegaten nur funktioniert, wenn beide Delegattypen aus der gleichen generischen Typdefinition erstellt wurden.  
  
 Im folgenden Beispiel werden die kombinierten Effekte von Varianz in der Delegatbindung und Varianz bei generischen Typparametern veranschaulicht. Im Beispiel wird eine Typhierarchie definiert, die drei Typen beinhaltet, vom am wenigsten abgeleiteten Typ (`Type1`) bis zum am weitesten abgeleiteten Typ (`Type3`). Bei der normalen Delegatbindung wird die Varianz verwendet, um eine Methode mit dem Parametertyp `Type1` und dem Rückgabetyp `Type3` an einen generischen Delegaten mit dem Parametertyp `Type2` und dem Rückgabetyp `Type2`zu binden. Der resultierende generische Delegat wird anschließend einer anderen Variablen zugewiesen, deren generischer Delegattyp einen Parameter vom Typ `Type3` und den Rückgabetyp `Type1`hat. Hierbei werden Kovarianz und Kontravarianz generischer Typparameter verwendet. Bei der zweiten Zuweisung müssen sowohl der Variablentyp als auch der Delegattyp mit der gleichen generischen Typdefinition erstellt werden, in diesem Fall <xref:System.Func%602>.  
  
 [!code-csharp[CoContravarianceDelegatesGenRelaxed#1](../../../samples/snippets/csharp/VS_Snippets_CLR/cocontravariancedelegatesgenrelaxed/cs/example.cs#1)]
 [!code-vb[CoContravarianceDelegatesGenRelaxed#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/cocontravariancedelegatesgenrelaxed/vb/example.vb#1)]  
  
 [Zurück zum Anfang](#top)  
  
<a name="DefiningVariantTypeParameters"></a>   
## <a name="defining-variant-generic-interfaces-and-delegates"></a>Definieren von varianten generischen Schnittstellen und Delegaten  
 Beginnend mit [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)]verfügen Visual Basic und C# über Schlüsselwörter, mit denen die generischen Typparameter von Schnittstellen und Delegaten als kovariant oder kontravariant gekennzeichnet werden können.  
  
> [!NOTE]
>  Beginnen mit .NET Framework, Version 2.0, unterstützt die Common Language Runtime Varianzkennzeichnungen für generische Typparameter. Vor [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] war Microsoft Intermediate Language (MSIL) die einzige Möglichkeit, eine generische Klasse zu definieren, die über diese Kennzeichnungen verfügt, entweder durch das Kompilieren der Klasse mit [Ilasm.exe (IL-Assembler)](../../../docs/framework/tools/ilasm-exe-il-assembler.md) oder durch das Ausgeben in einer dynamischen Assembly.  
  
 Ein kovarianter Typparameter wird mit dem `out`-Schlüsselwort (`Out`-Schlüsselwort in Visual Basic, `+` für den [MSIL-Assembler](../../../docs/framework/tools/ilasm-exe-il-assembler.md)) gekennzeichnet. Sie können einen kovarianten Typparameter als Rückgabewert einer Methode verwenden, die zu einer Schnittstelle gehört, oder als Rückgabetyp eines Delegaten. Sie können einen kovarianten Typparameter nicht als generische Typeinschränkung für Schnittstellenmethoden verwenden.  
  
> [!NOTE]
>  Wenn eine Methode einer Schnittstelle über einen Parameter verfügt, der ein generischer Delegattyp ist, kann ein kovarianter Typparameter des Schnittstellentyps verwendet werden, um einen kontravarianten Typparameter des Delegattyps anzugeben.  
  
 Ein kontravarianter Typparameter wird mit dem `in` -Schlüsselwort (`In` -Schlüsselwort in Visual Basic, `-` für den [MSIL-Assembler](../../../docs/framework/tools/ilasm-exe-il-assembler.md)) gekennzeichnet. Sie können einen kontravarianten Typparameter als Typ eines Parameters einer Methode verwenden, die zu einer Schnittstelle gehört, oder als Typ eines Parameters eines Delegaten. Sie können einen kontravarianten Typparameter als generische Typeinschränkung für Schnittstellenmethoden verwenden.  
  
 Nur Schnittstellentypen und Delegattypen können über variante Typparameter verfügen. Eine Schnittstelle oder ein Delegattyp kann sowohl kovariante, als auch kontravariante Typparameter haben.  
  
 In Visual Basic und C# müssen die Regeln zum Verwenden von kovarianten und kontravarianten Typparametern eingehalten werden, und es ist nicht möglich, Kovarianz- und Kontravarianzkennzeichnungen zu den Typparametern anderer Typen als Schnittstellen- und Delegattypen hinzuzufügen. Der [MSIL-Assembler](../../../docs/framework/tools/ilasm-exe-il-assembler.md) führt keine solchen Überprüfungen aus, es wird aber eine <xref:System.TypeLoadException> ausgelöst, wenn Sie versuchen, einen Typ zu laden, der gegen die Regeln verstößt.  
  
 Weitere Informationen und einen Beispielcode finden Sie unter [Varianz in generischen Schnittstellen](https://msdn.microsoft.com/library/e14322da-1db3-42f2-9a67-397daddd6b6a).  
  
 [Zurück zum Anfang](#top)  
  
<a name="VariantList"></a>   
## <a name="list-of-variant-generic-interface-and-delegate-types"></a>Liste der varianten generischen Schnittstellen und Delegattypen  
 In [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)]verfügen die folgenden Schnittstellen- und Delegattypen über kovariante und/oder kontravariante Typparameter.  
  
|Typ|Kovariante Typparameter|Kontravariante Typparameter|  
|----------|-------------------------------|-----------------------------------|  
|<xref:System.Action%601> bis <xref:System.Action%6016>||Ja|  
|<xref:System.Comparison%601>||Ja|  
|<xref:System.Converter%602>|Ja|Ja|  
|<xref:System.Func%601>|Ja||  
|<xref:System.Func%602> bis <xref:System.Func%6017>|Ja|Ja|  
|<xref:System.IComparable%601>||Ja|  
|<xref:System.Predicate%601>||Ja|  
|<xref:System.Collections.Generic.IComparer%601>||Ja|  
|<xref:System.Collections.Generic.IEnumerable%601>|Ja||  
|<xref:System.Collections.Generic.IEnumerator%601>|Ja||  
|<xref:System.Collections.Generic.IEqualityComparer%601>||Ja|  
|<xref:System.Linq.IGrouping%602>|Ja||  
|<xref:System.Linq.IOrderedEnumerable%601>|Ja||  
|<xref:System.Linq.IOrderedQueryable%601>|Ja||  
|<xref:System.Linq.IQueryable%601>|Ja||  
  
## <a name="see-also"></a>Siehe auch  
 [Kovarianz und Kontravarianz (C#)](../../csharp/programming-guide/concepts/covariance-contravariance/index.md)  
 [Kovarianz und Kontravarianz (Visual Basic)](../../visual-basic/programming-guide/concepts/covariance-contravariance/index.md)    
 [Varianz bei Delegaten](https://msdn.microsoft.com/library/e3b98197-6c5b-4e55-9c6e-9739b60645ca)
