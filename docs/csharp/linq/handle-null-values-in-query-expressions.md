---
title: Behandeln von NULL-Werten in Abfrageausdrücken
description: 'Vorgehensweise: Behandeln von NULL-Werten in Abfrageausdrücken'
ms.date: 12/1/2016
ms.assetid: ac63ae8b-724d-4251-9334-528f4e884ae7
ms.openlocfilehash: ecd174462ef51a6dd7b7696abb9e111fc32d9ec7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/04/2018
ms.locfileid: "33272386"
---
# <a name="handle-null-values-in-query-expressions"></a>Behandeln von NULL-Werten in Abfrageausdrücken

Dieses Beispiel zeigt, wie mögliche NULL-Werte in Quellauflistungen behandelt werden. Eine Objektauflistung wie z.B. <xref:System.Collections.Generic.IEnumerable%601> kann Elemente enthalten, deren Wert [NULL](../language-reference/keywords/null.md) ist. Wenn eine Quellauflistung NULL ist oder ein Element enthält, dessen Wert NULL ist, und die Abfrage keine NULL-Werte verarbeitet, wird eine <xref:System.NullReferenceException> ausgelöst, wenn Sie die Abfrage ausführen.  
  
## <a name="example"></a>Beispiel

 Sie können defensiv codieren, um eine Nullverweisausnahme wie im folgenden Beispiel dargestellt zu vermeiden:  
  
 [!code-csharp[csProgGuideLINQ#82](../../../samples/snippets/csharp/concepts/linq/how-to-handle-null-values-in-query-expressions_1.cs)]  
  
 Im vorherigen Beispiel filtert die `where`-Klausel alle NULL-Elemente in der Reihenfolge der Kategorien heraus. Diese Technik ist unabhängig von der NULL-Überprüfung in der join-Klausel. Der bedingte Ausdruck mit NULL in diesem Beispiel funktioniert, da `Products.CategoryID` vom Typ `int?` ist, was eine Abkürzung für `Nullable<int>` ist.  
  
## <a name="example"></a>Beispiel

 Wenn in einer join-Klausel nur einer der Vergleichsschlüssel ein Nullable-Werttyp ist, können Sie den anderen im Abfrageausdruck in einen Nullable-Typ umwandeln. Im folgenden Beispiel wird angenommen, dass `EmployeeID` eine Spalte mit Werten vom Typ `int?` ist:  
  
 [!code-csharp[csProgGuideLINQ#83](../../../samples/snippets/csharp/concepts/linq/how-to-handle-null-values-in-query-expressions_2.cs)]  
  
## <a name="see-also"></a>Siehe auch  
 <xref:System.Nullable%601>  
 [LINQ-Abfrageausdrücke](index.md)  
 [Nullable-Typen](../programming-guide/nullable-types/index.md)
