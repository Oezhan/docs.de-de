---
title: -delaysign (C#-Compileroptionen)
ms.date: 05/15/2018
f1_keywords:
- /delaysign
helpviewer_keywords:
- -delaysign compiler option [C#]
- delaysign compiler option [C#]
- /delaysign compiler option [C#]
ms.assetid: bcb058eb-2933-4e7f-b356-5c941db4de75
ms.openlocfilehash: 72dcba3b506dae42f67f0421ba92efee18274c37
ms.sourcegitcommit: 77d9a94dac4c05827ed0663d95e0f9ad35d6682e
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/24/2018
ms.locfileid: "34472645"
---
# <a name="-delaysign-c-compiler-options"></a>-delaysign (C#-Compileroptionen)

Durch diese Option reserviert der Compiler Speicherplatz in der Ausgabedatei, damit digitale Signaturen später hinzugefügt werden können.

## <a name="syntax"></a>Syntax

```console
-delaysign[ + | - ]
```

## <a name="arguments"></a>Argumente

`+` &#124; `-`

Verwenden Sie **-delaysign-**, wenn die Assembly vollständig signiert werden soll. Verwenden Sie **-delaysign+**, wenn Sie nur den öffentlichen Schlüssel in der Assembly platzieren möchten. Der Standardwert ist **-delaysign-**.

## <a name="remarks"></a>Hinweise

Die Option **-delaysign** hat keine Auswirkung, wenn Sie nicht mit [-keyfile](../../../csharp/language-reference/compiler-options/keyfile-compiler-option.md) oder [-keycontainer](../../../csharp/language-reference/compiler-options/keycontainer-compiler-option.md) verwendet wird.

Die Optionen **-delaysign** und **-publicsign** schließen sich gegenseitig aus.

Wenn Sie eine vollständig signierte Assembly anfordern, wird vom Compiler der Hash der Datei mit dem Manifest (Assemblymetadaten) erstellt und mit dem privaten Schlüssel signiert. Dadurch wird eine digitale Signatur erstellt, die in der Datei mit dem Manifest gespeichert wird. Wenn eine Assembly mit Verzögerung signiert wird, wird die Signatur vom Compiler nicht berechnet und gespeichert, sondern lediglich ein Bereich in der Datei reserviert, damit die Signatur zu einem späteren Zeitpunkt hinzugefügt werden kann.

Mit **-delaysign+** können Tester die Assembly beispielsweise im globalen Cache ablegen. Nach dem Testen können Sie die Assembly vollständig signieren, indem Sie den privaten Schlüssel der Assembly mithilfe des Hilfsprogramms [Assembly Linker](../../../framework/tools/al-exe-assembly-linker.md) platzieren.

Weitere Informationen finden Sie unter [Erstellen und Verwenden von Assemblys mit starkem Namen](../../../framework/app-domains/create-and-use-strong-named-assemblies.md) und [Verzögertes Signieren einer Assembly](../../../framework/app-domains/delay-sign-assembly.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>So legen Sie diese Compileroption in der Visual Studio-Entwicklungsumgebung fest

1. Öffnen Sie die Seite **Eigenschaften** für das Projekt.
1. Bearbeiten Sie die Eigenschaft **Nur verzögerte Signierung**.

Informationen zum programmgesteuerten Festlegen dieser Compileroption finden Sie unter <xref:VSLangProj80.ProjectProperties3.DelaySign%2A>.

## <a name="see-also"></a>Siehe auch

 [C#-Option -publicsign](publicsign-compiler-option.md)  
 [C#-Compileroptionen](index.md)  
 [Verwalten von Projekt- und Projektmappeneigenschaften](/visualstudio/ide/managing-project-and-solution-properties)
