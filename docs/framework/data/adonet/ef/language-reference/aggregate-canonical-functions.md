---
title: Aggregieren kanonischer Funktionen
ms.date: 03/30/2017
ms.assetid: 3bcff826-ca90-41b3-a791-04d6ff0e5085
ms.openlocfilehash: 04b7d9c20373a465c073d55a090f1c2fd7fc6e07
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/03/2018
ms.locfileid: "32761934"
---
# <a name="aggregate-canonical-functions"></a>Aggregieren kanonischer Funktionen

Aggregate sind Ausdrücke, die eine Folge von Eingabewerten beispielsweise auf einen einzigen Wert reduzieren. Aggregate werden normalerweise zusammen mit der GROUP BY-Klausel des SELECT-Ausdrucks verwendet, und für ihre Verwendung gelten Einschränkungen.

In der folgenden Tabelle sind die kanonischen [!INCLUDE[esql](../../../../../../includes/esql-md.md)]-Aggregatfunktionen aufgeführt.

| Funktion | Beschreibung |
| -------- | ----------- |
| `Avg(expression)` | Gibt den Durchschnitt der von NULL verschiedenen Werte zurück.<br><br>**Argumente**<br><br>Ein `Int32`, `Int64`, `Double`, und `Decimal`.<br><br>**Rückgabewert**<br><br>Der `expression`-Typ. `Null`, wenn alle Eingabewerte `null`-Werte sind.<br><br>**Beispiel**[!code-csharp[DP EntityServices Concepts#EDM_AVG](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_avg)] [!code-sql[DP EntityServices Concepts#EDM_AVG](../../../../../../samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_avg)] |
| `BigCount(expression)` | Gibt die Größe des Aggregats, einschließlich null-Werte und doppelter Werte zurück.<br><br>**Argumente**<br><br>Beliebiger Typ.<br><br>**Rückgabewert**<br><br>Eine `Int64`.<br><br>**Beispiel**[!code-csharp[DP EntityServices Concepts#EDM_BIGCOUNT](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_bigcount)] [!code-sql[DP EntityServices Concepts#EDM_BIGCOUNT](../../../../../../samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_bigcount)] |
| `Count(expression)` | Gibt die Größe des Aggregats, einschließlich null-Werte und doppelter Werte zurück.<br><br>**Argumente**<br><br>Beliebiger Typ.<br><br>**Rückgabewert**<br><br>Eine `Int32`.<br><br>**Beispiel**[!code-csharp[DP EntityServices Concepts#EDM_COUNT](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_count)] [!code-sql[DP EntityServices Concepts#EDM_COUNT](../../../../../../samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_count)] |
| `Max(expression)` | Gibt den Höchstwert der von null verschiedenen Werte zurück.<br><br>**Argumente**<br><br>`Int16``Byte`    `Int64`, `Int32``Single`, `Byte``Decimal`, `Double``DateTimeOffset`, `DateTime``String`, `Time`, `Binary`, , , , , , .<br><br>**Rückgabewert**<br><br>Der `expression`-Typ. `Null`, wenn alle Eingabewerte `null`-Werte sind.<br><br>**Beispiel**[!code-csharp[DP EntityServices Concepts#EDM_MAX](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_max)] [!code-sql[DP EntityServices Concepts#EDM_MAX](../../../../../../samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_max)] |
| `Min(expression)` | Gibt den geringsten Wert der von NULL verschiedenen Werte zurück.<br><br>**Argumente**<br><br>`Int16``Byte`    `Int64`, `Int32``Single`, `Byte``Decimal`, `Double``DateTimeOffset`, `DateTime``String`, `Time`, `Binary`, , , , , , .<br><br>**Rückgabewert**<br><br>Der `expression`-Typ. `Null`, wenn alle Eingabewerte `null`-Werte sind.<br><br>**Beispiel**[!code-csharp[DP EntityServices Concepts#EDM_MIN](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_min)] [!code-sql[DP EntityServices Concepts#EDM_MIN](../../../../../../samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_min)] |
| `StDev(expression)` | Gibt die Standardabweichung der von NULL verschiedenen Werte zurück.<br><br>**Argumente**<br><br>`Int32`, `Int64`, `Double`, `Decimal`.<br><br>**Rückgabewert**<br><br>Ein `Double`. `Null`, wenn alle Eingabewerte `null`-Werte sind.<br><br>**Beispiel**[!code-csharp[DP EntityServices Concepts#EDM_STDEV](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_stdev)] [!code-sql[DP EntityServices Concepts#EDM_STDEV](../../../../../../samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_stdev)] |
| `StDevP(expression)` | Gibt die Standardabweichung zum Ausfüllen aller Werte zurück.<br><br>**Argumente**<br><br>`Int32`, `Int64`, `Double`, `Decimal`.<br><br>**Rückgabewert**<br><br>Ein `Double`. `Null`, wenn alle Eingabewerte `null`-Werte sind.<br><br>**Beispiel**[!code-csharp[DP EntityServices Concepts#EDM_STDEVP](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_stdevp)] [!code-sql[DP EntityServices Concepts#EDM_STDEVP](../../../../../../samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_stdevp)] |
| `Sum(expression)` | Gibt die Summe der von null verschiedenen Werte zurück.<br><br>**Argumente**<br><br>`Int32`, `Int64`, `Double`, `Decimal`.<br><br>**Rückgabewert**<br><br>Ein `Double`. `Null`, wenn alle Eingabewerte `null`-Werte sind.<br><br>**Beispiel**[!code-csharp[DP EntityServices Concepts#EDM_SUM](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_sum)] [!code-sql[DP EntityServices Concepts#EDM_SUM](../../../../../../samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_sum)] |
| `Var(expression)` | Gibt die Varianz aller Werte zurück, die keine Null-Werte sind.<br><br>**Argumente**<br><br>`Int32`, `Int64`, `Double`, `Decimal`.<br><br>**Rückgabewert**<br><br>Ein `Double`. `Null`, wenn alle Eingabewerte `null`-Werte sind.<br><br>**Beispiel**[!code-csharp[DP EntityServices Concepts#EDM_VAR](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_var)] [!code-sql[DP EntityServices Concepts#EDM_VAR](../../../../../../samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_var)] |
| `VarP(expression)` | Gibt die Varianz für die Auffüllung aller Werte zurück, die keine Null-Werte sind.<br><br>**Argumente**<br><br>`Int32`, `Int64`, `Double`, `Decimal`.<br><br>**Rückgabewert**<br><br>Ein `Double`. `Null`, wenn alle Eingabewerte `null`-Werte sind.<br><br>**Beispiel**[!code-csharp[DP EntityServices Concepts#EDM_VARP](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_varp)] [!code-sql[DP EntityServices Concepts#EDM_VARP](../../../../../../samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_varp)] |

Entsprechende Funktionen sind für den verwalteten Anbieter des Microsoft SQL-Clients verfügbar. Weitere Informationen finden Sie unter [SqlClient für Entity Framework-Funktionen](../../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-functions.md).

## <a name="collection-based-aggregates"></a>Auflistungsbasierte Aggregate

Auflistungsbasierte Aggregate (Auflistungsfunktionen) verarbeiten Auflistungen und geben einen Wert zurück. Zum Beispiel wenn ORDERS ist eine Auflistung aller Bestellungen, können Sie das früheste Lieferdatum mit dem folgenden Ausdruck berechnen:

```sql
min(select value o.ShipDate from LOB.Orders as o)
```

Ausdrücke in auflistungsbasierten Aggregaten werden innerhalb des aktuellen umgebenden Namensauflösungsbereichs ausgewertet.

## <a name="group-based-aggregates"></a>Gruppenbasierte Aggregate

Gruppenbasierte Aggregate werden für eine Gruppe berechnet, die mit einer GROUP BY-Klausel definiert wurde. Für jede Gruppe im Ergebnis wird ein separates Aggregat berechnet, indem die Elemente in jeder Gruppe als Eingabe zur Aggregatberechnung verwendet werden. Wenn eine GROUP BY-Klausel in einem SELECT-Ausdruck verwendet wird, können sich in der Projektion oder ORDER BY-Klausel nur die Namen von Gruppierungsausdrücken, Aggregate oder konstante Ausdrücke befinden.

Im folgenden Beispiel wird die durchschnittlich bestellte Anzahl für jedes Produkt berechnet:

```sql
select p, avg(ol.Quantity) from LOB.OrderLines as ol 
  group by ol.Product as p
```

Es ist ein gruppenbasiertes Aggregat ohne explizite Group by-Klausel in der SELECT-Ausdruck enthalten sein. In diesem Fall werden alle Elemente als eine einzelne Gruppe behandelt. Dies entspricht der Angabe einer Gruppe auf Grundlage einer Konstante. Betrachten Sie beispielsweise folgenden Ausdruck:

```sql
select avg(ol.Quantity) from LOB.OrderLines as ol
```

Dieser Ausdruck ist äquivalent zu Folgendem:

```sql
select avg(ol.Quantity) from LOB.OrderLines as ol group by 1
```

Ausdrücke in gruppenbasierten Aggregaten werden innerhalb des Namensauflösungsbereichs ausgewertet, der für den WHERE-Klauselausdruck sichtbar wäre.

Wie in [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)], Gruppenbasierte Aggregate können auch angeben, ALL oder DISTINCT-Modifizierer. Wenn der DISTINCT-Modifizierer angegeben ist, werden Duplikate vor der Berechnung des Aggregats aus der Aggregateingabeauflistung gelöscht. Wenn der ALL-Modifizierer oder kein Modifizierer angegeben wird, werden Duplikate nicht gelöscht.  

## <a name="see-also"></a>Siehe auch

[Canonical Functions (Kanonische Funktionen)](../../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md)
