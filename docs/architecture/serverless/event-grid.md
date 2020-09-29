---
title: 'Azure Event Grid: Serverlose Apps'
description: Azure Event Grid ist eine serverlose Lösung für die zuverlässige Bereitstellung und Weiterleitung von Ereignissen in großem Maßstab mit einem ereignisbasierten Zahlungsmodell.
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 04/06/2020
ms.openlocfilehash: 30937bafd8069eb4508dce18351964103421373a
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/24/2020
ms.locfileid: "91171883"
---
# <a name="event-grid"></a>Event Grid

[Azure Event Grid](/azure/event-grid/overview) stellt serverlose Infrastruktur für ereignisbasierte Anwendungen bereit. Sie können Ereignisse aus beliebigen Quellen in Event Grid veröffentlichen und Nachrichten von beliebigen Plattformen verarbeiten. Event Grid bietet auch integrierte Unterstützung für Ereignisse von Azure-Ressourcen, um die Integration in Ihre Anwendungen zu optimieren. Beispielsweise können Sie Blobspeicherereignisse abonnieren, um die App zu benachrichtigen, wenn eine Datei hochgeladen wird. Die Anwendung kann dann eine benutzerdefinierte Event Grid-Nachricht veröffentlichen, die von anderen cloudbasierten oder lokalen Anwendungen genutzt wird. Event Grid wurde für die zuverlässige Bewältigung massiver Skalierung konzipiert. Sie profitieren von den Vorteilen der Veröffentlichung und dem Abonnieren von Nachrichten ohne den Mehraufwand für die Einrichtung der erforderlichen Infrastruktur.

![Event Grid-Logo](./media/event-grid-logo.png)

Zu den wichtigsten Features von Event Grid gehören:

- Vollständig verwaltetes Ereignisrouting.
- Bereitstellung von Ereignissen nahezu in Echtzeit.
- Umfassende Abdeckung sowohl innerhalb als auch außerhalb von Azure.

## <a name="scenarios"></a>Szenarien

Event Grid deckt mehrere verschiedene Szenarien ab. In diesem Abschnitt werden drei der gängigsten Szenarien behandelt.

### <a name="ops-automation"></a>Betriebsautomatisierung

![Betriebsautomatisierung](./media/ops-automation.png)

Event Grid kann zur Beschleunigung der Automatisierung und Vereinfachung der Richtliniendurchsetzung beitragen, indem [Azure Automation](/azure/automation) benachrichtigt wird, wenn Infrastruktur bereitgestellt wird.

### <a name="application-integration"></a>Anwendungsintegration

![Anwendungsintegration](./media/app-integration.png)

Sie können Event Grid verwenden, um Ihre App mit anderen Diensten zu verbinden. Mithilfe von HTTP-Standardprotokollen können auch Legacy-Apps problemlos geändert werden, um Event Grid-Nachrichten zu veröffentlichen. Webhooks stehen für andere Dienste und Plattformen zur Verfügung, um Event Grid-Nachrichten zu verarbeiten.

### <a name="serverless-apps"></a>Serverlose Apps

![Serverlose Apps](./media/serverless-apps.png)

Event Grid kann Azure Functions-, Logic Apps- oder ihren eigenen benutzerdefinierten Code auslösen. Ein großer Vorteil der Verwendung von Event Grid besteht darin, dass ein *Pushmechanismus* verwendet wird, um Nachrichten zu senden, wenn Ereignisse auftreten. Die Pusharchitektur beansprucht weniger Ressourcen und lässt sich besser als *Abrufmechanismen* skalieren. Der Abruf muss in regelmäßigen Abständen auf Updates prüfen.

## <a name="event-grid-vs-other-azure-messaging-services"></a>Event Grid im Vergleich zu anderen Azure-Messagingdiensten

Azure bietet mehrere Messagingdienste, einschließlich [Event Hubs](/azure/event-hubs) und [Service Bus](/azure/service-bus-messaging). Jeder dieser Dienste ist so konzipiert, dass ein bestimmter Satz von Anwendungsfällen berücksichtigt wird. Die folgende Abbildung gibt einen Überblick über die Unterschiede zwischen den Diensten.

![Azure-Messaging im Vergleich](./media/azure-messaging-services.png)

Einen ausführlicheren Vergleich finden Sie unter [Messagingdienste im Vergleich](/azure/event-grid/compare-messaging-services).

## <a name="performance-targets"></a>Leistungsziele

Mithilfe von Event Grid können Sie die folgenden Leistungsgarantien nutzen:

- End-to-End-Latenz unter einer Sekunde im 99. Perzentil.
- Verfügbarkeit von 99,99%.
- 10 Millionen Ereignisse pro Sekunde pro Region.
- 100 Millionen Abonnements pro Region.
- Herausgeberlatenz von 50 ms.
- 24-Stunden-Wiederholung mit exponentiellem Backoff für garantierte Übermittlung im 1-Tage-Fenster.
- Transparentes regionales Failover.

## <a name="event-grid-schema"></a>Event Grid-Schema

Event Grid verwendet ein Standardschema, um benutzerdefinierte Ereignisse zu umschließen. Das Schema ist wie ein Umschlag, der das benutzerdefinierte Datenelement umschließt. Dies ist ein Beispiel für eine Event Grid-Nachricht:

```json
[{
    "id": "03e24f21-a955-43cc-8921-1f61a6081ce0",
    "eventType": "myCustomEvent",
    "subject": "foo/bar/12",
    "eventTime": "2018-09-22T10:36:01+00:00",
    "data": {
        "favoriteColor": "blue",
        "favoriteAnimal": "panther",
        "favoritePlanet": "Jupiter"
    },
    "dataVersion": "1.0"
}]
```

Alles bei dieser Nachricht ist mit Ausnahme der `data`-Eigenschaft standardmäßig. Sie können die Meldung untersuchen und `eventType` und `dataVersion` verwenden, um den benutzerdefinierten Teil der Nutzlast zu deserialisieren.

## <a name="azure-resources"></a>Azure-Ressourcen

Ein großer Vorteil der Verwendung von Event Grid sind die von Azure generierten automatischen Nachrichten. In Azure veröffentlichen Ressourcen Ereignisse automatisch in einem *Thema*, mit dem Sie verschiedene Ereignisse abonnieren können. In der folgenden Tabelle werden die Ressourcentypen, Nachrichtentypen und Ereignisse aufgelistet, die automatisch verfügbar sind.

| Azure-Ressource | Ereignistyp | Beschreibung |
| -------------- | ---------- | ----------- |
| Azure-Abonnement | Microsoft.Resources.ResourceWriteSuccess | Wird ausgelöst, wenn ein Vorgang zum Erstellen oder Aktualisieren einer Ressource erfolgreich ist. |
| | Microsoft.Resources.ResourceWriteFailure | Wird ausgelöst, wenn ein Vorgang zum Erstellen oder Aktualisieren einer Ressource fehlschlägt. |
| | Microsoft.Resources.ResourceWriteCancel | Wird ausgelöst, wenn ein Vorgang zum Erstellen oder Aktualisieren einer Ressource abgebrochen wird. |
|  | Microsoft.Resources.ResourceDeleteSuccess | Wird ausgelöst, wenn ein Vorgang zum Löschen einer Ressource erfolgreich ist. |
|  | Microsoft.Resources.ResourceDeleteFailure | Wird ausgelöst, wenn ein Vorgang zum Löschen einer Ressource fehlschlägt. |
| | Microsoft.Resources.ResourceDeleteCancel | Wird ausgelöst, wenn ein Vorgang zum Löschen einer Ressource abgebrochen wird. Dieses Ereignis tritt ein, wenn eine Vorlagenbereitstellung abgebrochen wird. |
| Blobspeicher | Microsoft.Storage.BlobCreated | Wird ausgelöst, wenn ein Blob erstellt wird. |
| | Microsoft.Storage.BlobDeleted | Wird ausgelöst, wenn ein Blob gelöscht wird. |
| Event Hubs | Microsoft.EventHub.CaptureFileCreated | Wird ausgelöst, wenn eine Erfassungsdatei erstellt wird.
| IoT Hub | Microsoft.Devices.DeviceCreated | Wird ausgelöst, wenn ein Gerät bei einem IoT Hub registriert wird. |
| | Microsoft.Devices.DeviceDeleted | Wird ausgelöst, wenn ein Gerät aus einem IoT Hub gelöscht wird. |
| Ressourcengruppen | Microsoft.Resources.ResourceWriteSuccess | Wird ausgelöst, wenn ein Vorgang zum Erstellen oder Aktualisieren einer Ressource erfolgreich ist. |
| | Microsoft.Resources.ResourceWriteFailure | Wird ausgelöst, wenn ein Vorgang zum Erstellen oder Aktualisieren einer Ressource fehlschlägt. |
| | Microsoft.Resources.ResourceWriteCancel | Wird ausgelöst, wenn ein Vorgang zum Erstellen oder Aktualisieren einer Ressource abgebrochen wird. |
| | Microsoft.Resources.ResourceDeleteSuccess | Wird ausgelöst, wenn ein Vorgang zum Löschen einer Ressource erfolgreich ist. |
| | Microsoft.Resources.ResourceDeleteFailure | Wird ausgelöst, wenn ein Vorgang zum Löschen einer Ressource fehlschlägt. |
| | Microsoft.Resources.ResourceDeleteCancel | Wird ausgelöst, wenn ein Vorgang zum Löschen einer Ressource abgebrochen wird. Dieses Ereignis tritt ein, wenn eine Vorlagenbereitstellung abgebrochen wird. |

Weitere Informationen finden Sie unter [Azure Event Grid-Ereignisschema](/azure/event-grid/event-schema).

Sie können von jedem Anwendungstyp aus auf Event Grid zugreifen, selbst über einen lokal ausgeführten.

## <a name="conclusion"></a>Schlussbemerkung

In diesem Kapitel haben Sie die serverlose Azure-Plattform kennengelernt, die aus Azure Functions, Logic Apps und Event Grid besteht. Sie können diese Ressourcen verwenden, um eine vollständig serverlose App-Architektur oder eine Hybridlösung zu erstellen, die mit anderen Cloudressourcen und lokalen Servern interagiert. In Kombination mit einer serverlosen Datenplattform wie [Azure SQL](/azure/sql-database) oder [CosmosDB](/azure/cosmos-db/introduction) können Sie vollständig verwaltete, cloudnative Anwendungen erstellen.

## <a name="recommended-resources"></a>Empfohlene Ressourcen

- [App Service-Pläne](/azure/app-service/azure-web-sites-web-hosting-plans-in-depth-overview)
- [Application Insights](/azure/application-insights)
- [Application Insights Analytics](/azure/application-insights/app-insights-analytics)
- [Azure: Migrieren einer App zur Cloud mit serverlosen Azure Functions](https://channel9.msdn.com/events/Connect/2017/E102)
- [Azure Event Grid](/azure/event-grid/overview)
- [Azure Event Grid-Ereignisschema](/azure/event-grid/event-schema)
- [Azure Event Hubs](/azure/event-hubs)
- [Dokumentation zu Azure Functions](/azure/azure-functions)
- [Konzepte für Azure Functions-Trigger und -Bindungen](/azure/azure-functions/functions-triggers-bindings)
- [Azure Logic Apps](/azure/logic-apps)
- [Azure Service Bus](/azure/service-bus-messaging)
- [Azure Table Storage](/azure/cosmos-db/table-storage-overview)
- [Herstellen einer Verbindung mit lokalen Datenquellen mit dem lokalen Azure-Datengateway](/azure/analysis-services/analysis-services-gateway)
- [Erstellen Ihrer ersten Funktion im Azure-Portal](/azure/azure-functions/functions-create-first-azure-function)
- [Create your first function using the Azure CLI (Erstellen Ihrer ersten Funktion mit der Azure-Befehlszeilenschnittstelle)](/azure/azure-functions/functions-create-first-azure-function-azure-cli)
- [Erstellen Ihrer ersten Funktion mit Visual Studio](/azure/azure-functions/functions-create-your-first-function-visual-studio)
- [Von Functions unterstützte Sprachen](/azure/azure-functions/supported-languages)
- [Überwachen von Azure Functions](/azure/azure-functions/functions-monitoring)

>[!div class="step-by-step"]
>[Zurück](logic-apps.md)
>[Weiter](durable-azure-functions.md)
