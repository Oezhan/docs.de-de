---
title: Leitfaden für F#
description: Dieses Handbuch enthält einen Überblick über die verschiedenen Lernmaterialien für F#, funktionalen Programmiersprachen, die auf .NET ausgeführt wird.
author: jackfoxy
ms.date: 03/19/2018
ms.openlocfilehash: cb829e904c006467e1470752b4fe8757ca694b05
ms.sourcegitcommit: 895c7602386a6dfe7ca4facce3d965b27e5c6e87
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2018
ms.locfileid: "34312000"
---
# <a name="f-guide"></a>Leitfaden für F#

F# ist eine funktionale Programmiersprache, die auf .NET ausgeführt wird. Dank vollständiger Unterstützung von Objekten können Sie für pragmatische Lösungen zu jedem Problem die funktionale und die objektorientierte Programmierung miteinander kombinieren.

```fsharp
open System // Get access to functionality in System namespace.

// Function: takes a name and produces a greeting.
let getGreeting name =
    sprintf "Hello, %s! Isn't F# great?" name

// Use the EntryPoint attribute to run the program.
[<EntryPoint>]
let main args =
    // Define a list of names
    let names = [| "Don"; "Julia"; "Xi" |]
    
    // Print a fun greeting for each name!
    names
    |> Array.map getGreeting
    |> Array.iter (fun greeting -> printfn "%s" greeting)

    0
```

Im Fokus von F# steht die Steigerung der Produktivität. F# bietet eine umfassende Toolunterstützung mit zahlreichen modernen Features.

## <a name="learning-f"></a>Learning [F#] #

Die [Tour durch F#](tour.md) bietet einen Überblick über die wichtigsten Sprachfeatures und viele Codebeispiele. Sie wird für den Einstieg in F# empfohlen, um sich mit der Funktionsweise der Sprache vertraut zu machen.

Lesen Sie [Erste Schritte mit F# in Visual Studio](get-started/get-started-visual-studio.md), wenn Sie für Windows entwickeln und die vollständige Visual Studio-IDE (Integraded Development Environment) nutzen möchten.

Lesen Sie [Erste Schritte mit F# in Visual Studio für Mac](get-started/get-started-with-visual-studio-for-mac.md), wenn Sie MacOS nutzen und eine Visual Studio-IDE verwenden möchten.

Lesen Sie [Erste Schritte mit F# in Visual Studio Code](get-started/get-started-vscode.md), wenn Sie eine schlanke, plattformübergreifende und leistungsstarke IDE nutzen möchten.

[Erste Schritte mit F# mit der .NET Core-CL](get-started/get-started-command-line.md), wenn Sie die Befehlszeilentools verwenden möchten.

[Erste Schritte mit F#- und Xamarin](https://docs.microsoft.com/xamarin/cross-platform/platform/fsharp/) für die mobile-Programmierung mit F#.

[F# for Azure Notebooks](https://notebooks.azure.com/Microsoft/libraries/samples/html/FSharp%20for%20Azure%20Notebooks.ipynb) (in englischer Sprache) ist ein Tutorial zum Erlernen von F# in einem kostenlosen gehosteten Jupyter Notebook.

## <a name="references"></a>Verweise

Die [F#-Sprachreferenz](language-reference/index.md) ist die offizielle, umfassende Referenz zu allen F#-Funktionen. Jeder Artikel erklärt die Syntax und zeigt Codebeispiele. Nutzen Sie die Filterleiste im Inhaltsverzeichnis, um nach bestimmten Artikeln zu suchen.

Die [Referenz zur F#-Kernbibliothek](https://msdn.microsoft.com/visualfsharpdocs/conceptual/fsharp-core-library-reference) (in englischer Sprache) ist die API-Referenz für die F#-Kernbibliothek.


## <a name="additional-guides"></a>Zusätzliche Anleitungen

[F# for Fun and Profit](https://swlaschin.gitbooks.io/fsharpforfunandprofit/content/) (in englischer Sprache) ist ein umfassendes und sehr detailliertes Buch zum Erlernen von F#. Inhalt und Autor werden von der F#-Community hoch geschätzt. Die Zielgruppe sind in erster Linie Entwickler aus dem Bereich der objektorientierten Programmierung.

Das [Wikibook zur F#-Programmierung](https://en.wikibooks.org/wiki/F_Sharp_Programming) (in englischer Sprache) ist ein Wikibook zum Erlernen von F# und ebenfalls ein Produkt der F#-Community. Zielgruppe sind Neueinsteiger in F#, die bereits über ein wenig Erfahrung mit der objektorientierten Programmierung verfügen.

## <a name="learn-f-through-videos"></a>F#-Lernvideos

Das [Tutorial zu F# auf YouTube](https://www.youtube.com/watch?v=c7eNDJN758U) (in englischer Sprache) ist eine hervorragende Einführung in F#. Anhand von Visual Studio und zahlreichen guten Beispielen erhalten Sie hier innerhalb von 1,5 Stunden einen Einblick in F#. Die Zielgruppe sind Visual Studio-Entwickler, die neu in F# einsteigen.

[Einführung in die Programmierung mit F#](https://www.youtube.com/watch?v=Teak30_pXHk&list=PLEoMzSkcN8oNiJ67Hd7oRGgD1d4YBxYGC) (in englischer Sprache) ist eine hervorragende Videoreihe, in der Visual Studio Code als Haupt-Editor verwendet wird. Die Videoreihe startet von Grund auf und endet mit der Erstellung eines textbasierten RPG-Videospiels. Die Zielgruppe sind Entwickler, die Visual Studio Code (oder eine einfache IDE) nutzen möchten und neu in F# einsteigen.

[What's New in Visual Studio 2017 for F# For Developers](https://www.linkedin.com/learning/what-s-new-in-visual-studio-2017-for-f-sharp-for-developers) (in englischer Sprache) ist ein Videkours, der die neueren Funktionen von F# in Visual Studio 2017 zeigt. Die Zielgruppe sind Visual Studio-Entwickler, die neu in F# einsteigen.

## <a name="other-useful-resources"></a>Andere nützliche Ressourcen

Auf der [Website mit F#-Codeausschnitten](http://www.fssnip.net) (in englischer Sprache) werden vielfältige Codeausschnitte zu allen Aspekten von F# bereitgestellt. Interessant sowohl für F#-Einsteiger als auch für Fortgeschrittene.

Die [F# Software Foundation Slack](http://fsharp.org/guides/slack/) (in englischer Sprache) ist für Einsteiger und Experten gleichermaßen hervorragend geeignet. Sie ist sehr aktiv und bietet die Möglichkeit zum Chat mit einigen der weltweit besten F#-Programmierer. Teilnahme dringend empfohlen!

## <a name="the-f-software-foundation"></a>Die F# Software Foundation

Wenngleich die Programmiersprache F# und alle zugehörigen Tools in Visual Studio primär durch Microsoft entwickelt werden, wird F# durch die F# Software Foundation (FSSF) auch von unabhängiger Seite gestützt.

Das Ziel der F# Software Foundation ist, die Programmiersprache F# zu fördern, zu schützen und weiterzuentwickeln sowie das Wachstum einer vielfältigen und internationalen Community von F#-Programmierern zu unterstützen.

Um mehr zu erfahren und mitzumachen, besuchen Sie [fsharp.org](http://fsharp.org). Mitmachen ist kostenlos, und das Netzwerk der F#-Entwickler der Foundation ist etwas, das Sie garantiert nicht verpassen möchten!
