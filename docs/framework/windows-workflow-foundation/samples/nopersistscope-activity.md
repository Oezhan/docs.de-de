---
title: NoPersistScope-Aktivität
ms.date: 03/30/2017
ms.assetid: 9a0baeb7-a05c-4fac-b905-252758cb71bb
ms.openlocfilehash: e4779bf28fc2fc1341cce5134a872b108278611c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/04/2018
ms.locfileid: "33516438"
---
# <a name="nopersistscope-activity"></a>NoPersistScope-Aktivität
In diesem Beispiel wird gezeigt, wie ein nicht serialisierbarer und verwerfbarer Zustand innerhalb eines Workflows bearbeitet wird. Es ist wichtig, dass Workflows nicht versuchen, den nicht serialisierbaren Zustand beizubehalten, und dass verwerfbare Objekte bereinigt werden, nachdem sie im Workflow verwendet wurden.  
  
## <a name="demonstrates"></a>Veranschaulicht  
 Benutzerdefinierte Aktivität `NoPersistScope` und Designer.  
  
## <a name="using-the-nopersistzone-activity"></a>Verwenden der NoPersistZone-Aktivität  
 Wenn der Beispielworkflow ausgeführt wird, erstellt eine benutzerdefinierte Aktivität mit dem Namen `CreateTextWriter` ein Objekt des Typs <xref:System.IO.TextWriter> und speichert es in einer Workflowvariablen. <xref:System.IO.TextWriter> ist ein <xref:System.IDisposable>-Objekt. Dieser <xref:System.IO.TextWriter>, der zum Schreiben in eine Datei mit dem Namen 'out.txt' in dem Verzeichnis, in dem das Beispiel ausgeführt wird, konfiguriert ist, wird von einer <xref:System.Activities.Statements.WriteLine>-Aktivität verwendet, da sie jeden an der Konsole eingegebenen Text wiederholt.  
  
 Die Wiederholungslogik wird in einer `NoPersistScope`-Aktivität ausgeführt (deren Code ebenfalls Teil dieses Beispiels ist), wodurch der Workflow an der Beibehaltung gehindert wird. Wenn die Eingabe im `unload` an der Konsole der Host versucht, um die Workflowinstanz beizubehalten, aber dieser Vorgang ein Timeout eintritt, da der Workflow innerhalb bleibt ein `NoPersistScope`. Der Workflow verwendet außerdem eine benutzerdefinierte Aktivität mit dem Namen `Dispose`, um das <xref:System.IO.TextWriter>-Objekt zu verwerfen, sobald der Workflow es nicht mehr verwendet. Die `Dispose`-Aktivität wird innerhalb des <xref:System.Activities.Statements.TryCatch.Finally%2A>-Blocks der <xref:System.Activities.Statements.TryCatch>-Aktivität platziert, in dem die <xref:System.IO.TextWriter>-Variable deklariert wird. Auf diese Weise wird sichergestellt, dass sie auch dann ausgeführt wird, falls während der Ausführung des Try-Blocks eine Ausnahme auftreten sollte.  
  
 Sie können eingeben `exit` an die Workflowinstanz abzuschließen und das Programm zu beenden.  
  
#### <a name="to-run-the-sample"></a>So führen Sie das Beispiel aus  
  
1.  Öffnen Sie die NoPersistZone.sln-Projektmappe in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Um die Projektmappe zu erstellen, drücken Sie STRG + UMSCHALT + B, oder wählen Sie **Projektmappe** aus der **erstellen** Menü.  
  
3.  Sobald die Erstellung erfolgreich war, drücken Sie F5, oder wählen Sie **Debuggen starten** aus der **Debuggen** Menü Alternativ können Sie STRG + F5 oder wählen Sie **Starten ohne Debugging** aus der **Debuggen** -Menü, um ohne Debuggen auszuführen.  
  
#### <a name="to-cleanup-optional"></a>So führen Sie eine (optionale) Bereinigung durch  
  
1.  Führen Sie zum Entfernen des SQL-Instanzspeichers Cleanup.cmd aus.  
  
> [!IMPORTANT]
>  Die Beispiele sind möglicherweise bereits auf dem Computer installiert. Suchen Sie nach dem folgenden Verzeichnis (Standardverzeichnis), bevor Sie fortfahren.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Wenn dieses Verzeichnis nicht vorhanden ist, fahren Sie mit [Windows Communication Foundation (WCF) und Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) aller Windows Communication Foundation (WCF) herunterladen und [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Beispiele. Dieses Beispiel befindet sich im folgenden Verzeichnis.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\NoPersistScope`