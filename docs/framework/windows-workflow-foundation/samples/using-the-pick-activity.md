---
title: Verwenden der Pick-Aktivität
ms.date: 03/30/2017
ms.assetid: b89be812-a247-4025-b0e3-ffb20db027a6
ms.openlocfilehash: 7ca4527cc1d5bc90ed1ec4df3eef6cf2d8b93b4e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/12/2020
ms.locfileid: "79142614"
---
# <a name="using-the-pick-activity"></a>Verwenden der Pick-Aktivität
In diesem Beispiel wird veranschaulicht, wie die <xref:System.Activities.Statements.Pick>-Aktivität verwendet wird.

 Die <xref:System.Activities.Statements.Pick>-Aktivität stellt eine ereignisbasierte Modellierung bereit. Sie weist ein ähnliches Verhalten wie die `switch`-Anweisung in C# auf, die nur eine der Verzweigungen in der `switch`-Anweisung ausführt. Im Gegensatz zur `switch`-Anweisung, in dem ein Branch basierend auf einem Wert ausgeführt wird, führt die <xref:System.Activities.Statements.Pick>-Aktivität einen Branch basierend darauf aus, wie eine Aktivität abgeschlossen wird.

 In diesem Beispiel wird ein Benutzer aufgefordert, seinen Namen in der Konsole innerhalb eines bestimmten Zeitraums einzugeben. Die <xref:System.Activities.Statements.Pick>-Aktivität im Beispiel verfügt über zwei Branches, die basierend darauf ausgeführt werden, ob der Benutzer seinen Namen innerhalb von 5 Sekunden eingibt oder nicht. Wenn der Benutzer seinen Namen innerhalb von 5 Sekunden eingibt, wird die erste Verzweigung ausgeführt, die eine benutzerdefinierte `ReadLine`-Aktivität enthält; andernfalls wird die andere Verzweigung ausgeführt, die eine <xref:System.Activities.Statements.Delay>-Aktivität enthält. Sobald der Name eines Benutzers in der Konsole eingegeben wird, wird der Name des Benutzers in der Konsole gedruckt. Wenn eine Eingabe nicht innerhalb von 5 Sekunden erfolgt, tritt ein Timeout für den Vorgang auf.

## <a name="demonstrates"></a>Zeigt
 <xref:System.Activities.Statements.Pick>-Aktivität

## <a name="discussion"></a>Diskussion
 Das Beispiel umfasst einen Designerworkflow und einen codierten Workflow.

 Designer-Workflow Die Designer-Version des Beispiels veranschaulicht, wie ein Workflow im Designer erstellt wird. Die folgenden Dateien sind enthalten:

- Program.cs: schließt die `Main`-Funktion ein, die den Beispielworkflow ausführt.

- ReadString.cs: eine benutzerdefinierte Aktivität, die Eingaben aus der Konsole liest.

- Sequence1.xaml: ein Workflow, der mit dem Designer erstellt wurde, der Pick verwendet.

 Codierter Workflow Die codierte Version des Beispiels veranschaulicht, wie ein Workflow im Designer erstellt wird. Die folgenden Dateien sind enthalten:

- Program.cs: schließt die `Main`-Funktion ein, die den Beispielworkflow ausführt.

- ReadString.cs: eine benutzerdefinierte Aktivität, die Eingaben aus der Konsole liest.

#### <a name="to-use-this-sample"></a>So verwenden Sie dieses Beispiel

1. Öffnen Sie mit Visual Studio 2010 die Lösungsdatei Pick.sln.

2. Drücken Sie STRG+UMSCHALT+B, um die Projektmappe zu erstellen.

3. Drücken Sie F5, um die Projektmappe auszuführen.

> [!IMPORTANT]
> Die Beispiele sind möglicherweise bereits auf dem Computer installiert. Suchen Sie nach dem folgenden Verzeichnis (Standardverzeichnis), bevor Sie fortfahren.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Wenn dieses Verzeichnis nicht vorhanden ist, wechseln Sie zu [Windows Communication Foundation (WCF) und Windows Workflow Foundation (WF) Samples for .NET Framework 4,](https://www.microsoft.com/download/details.aspx?id=21459) um alle Windows Communication Foundation (WCF) und [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Beispiele herunterzuladen. Dieses Beispiel befindet sich im folgenden Verzeichnis.  
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\Pick`
