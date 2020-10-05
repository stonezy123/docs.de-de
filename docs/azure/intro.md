---
title: Erste Schritte mit Azure und .NET
description: Lernen Sie die erforderlichen Grundlagen von Azure und .NET kennen.
ms.date: 06/20/2020
ms.openlocfilehash: e4a071e302247332cdc98c1aabf595cb4f8e2eff
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/24/2020
ms.locfileid: "91171571"
---
# <a name="introduction-to-azure-and-net"></a>Einführung in Azure und .NET

Dieses Dokument bietet eine Übersicht über wichtige Konzepte und Dienste, mit denen .NET-Entwickler für den Einstieg in die Entwicklung von Apps mit Azure-Diensten vertraut sein müssen.

## <a name="key-concepts"></a>Grundbegriffe

**Azure-Konto:** Mit Ihrem Azure-Konto melden Sie sich bei Azure-Diensten wie dem [Azure-Portal](https://portal.azure.com) oder [Cloud Shell](https://shell.azure.com) an. Falls Sie kein Azure-Konto besitzen, können Sie [kostenlos eines erstellen](https://azure.microsoft.com/free/dotnet/).

**Azure-Abonnement**: Ein Abonnement ist der Abrechnungsplan, in dem Azure-Ressourcen erstellt werden. Bei Abonnements kann es sich um einzelne Abonnements oder um Enterprise-Abonnements handeln, die von Ihrem Unternehmen verwaltet werden. Ihr Azure-Konto kann mehreren Abonnements zugeordnet sein. Achten Sie in diesem Fall beim Erstellen von Ressourcen auf die Auswahl des richtigen Abonnements. Weitere Informationen finden Sie unter [Grundlegendes zu Konten, Abonnements und Abrechnung](/azure/guides/developer/azure-developer-guide#understanding-accounts-subscriptions-and-billing).

> [!TIP]
> Wenn Sie ein Visual Studio-Abonnement haben, [verfügen Sie über monatliche Azure-Gutschriften, die zur Aktivierung bereit sind](https://azure.microsoft.com/pricing/member-offers/credit-for-visual-studio-subscribers/).

**Ressourcengruppe**: Ressourcengruppen sind eine Möglichkeit zum Organisieren Ihrer Azure-Ressourcen in Gruppen für die Verwaltung. In Azure erstellte Ressourcen werden in einer Ressourcengruppe gespeichert, ähnlich wie beim Speichern einer Datei in einem Ordner auf einem Computer.

**Hosting**: Zum Ausführen von Code in Azure muss dieser in einem Dienst gehostet sein, der vom Benutzer bereitgestellten Code unterstützt.

**Verwaltete Dienste**: Azure bietet einige Dienste, mit denen Sie Daten oder Informationen in Azure bereitstellen und die Azure Implementierung die entsprechende Aktion ausführt. Ein Beispiel dafür ist der Azure Blob Storage-Dienst, in dem Sie Dateien bereitstellen, die von Azure gelesen, geschrieben und gespeichert werden.

Der Begriff **Azure SDK für .NET** bezieht sich auf die [NuGet-Pakete](packages.md), die Sie in Ihrem Projekt installieren und die verschiedene Interaktionen und Funktionen mit Azure-Diensten bereitstellen. Diese Pakete umfassen auch Verwaltungsbibliotheken, die zur Bereitstellung und Verwaltung der Ressourcen verwendet werden.

## <a name="choosing-a-hosting-option"></a>Auswählen einer Hostingoption

Hosting in Azure lässt sich in drei Kategorien unterteilen.

* **Infrastructure-as-a-Service (IaaS)** : Bei IaaS stellen Sie die benötigten VMs zusammen mit den zugeordneten Netzwerk- und Speicherkomponenten bereit. Anschließend stellen Sie die Software und Anwendungen bereit, die für diese virtuellen Computer jeweils vorgesehen sind. Dieses Modell weist die größte Ähnlichkeit mit einer herkömmlichen lokalen Umgebung auf – mit der Ausnahme, dass die Infrastruktur von Microsoft verwaltet wird. Sie verwalten weiterhin die einzelnen virtuellen Computer, einschließlich Betriebssystem, benutzerdefinierte Software und Sicherheitsupdates.

* **Platform-as-a-Service (PaaS)** : Bei PaaS ist eine verwaltete Hostingumgebung vorhanden, in der Sie Ihre Anwendung bereitstellen, ohne virtuelle Computer oder Netzwerkressourcen verwalten zu müssen. Anstatt beispielsweise einzelne VMs zu erstellen, geben Sie eine Instanzanzahl an, und der Dienst übernimmt das Bereitstellen, Konfigurieren und Verwalten der erforderlichen Ressourcen. Azure App Service ist ein Beispiel für einen PaaS-Dienst.
  
* **Functions-as-a-Service (FaaS)** : FaaS wird gemeinhin als „serverloses Computing“ bezeichnet und geht beim Abstrahieren der Aspekte der Hostingumgebung sogar noch weiter als PaaS. Anstatt Computeinstanzen zu erstellen und dann Code auf diesen Instanzen bereitzustellen, stellen Sie Ihren Code bereit, der vom Dienst dann automatisch ausgeführt wird. Sie müssen die Computeressourcen nicht verwalten. Die Plattform skaliert Ihren Code nahtlos auf die jeweilige Ebene herauf oder herunter, die zum Verarbeiten des Datenverkehrs erforderlich ist, und Sie bezahlen nur, wenn Ihr Code ausgeführt wird. Azure Functions ist ein FaaS-Dienst.

Allgemein gilt: Je mehr Ihre Anwendung FaaS- und PaaS-Modelle begünstigt, desto mehr Vorteile der Ausführung in der Cloud bemerken Sie. Nachstehend finden Sie eine Zusammenfassung dreier gängiger Hostingoptionen in Azure und erfahren, wann Sie diese auswählen sollten.

* [Azure App Service](/azure/app-service/app-service-value-prop-what-is): Wenn Sie eine Webanwendung oder einen Dienst hosten möchten, sehen Sie sich zuerst App Service an. Informationen zum Einstieg in App Service und ASP.NET, WCF und ASP.NET Core-Apps finden Sie unter [Erstellen von ASP.NET Core-Web-Apps in Azure](/azure/app-service/app-service-web-get-started-dotnet).

* [Azure Functions](/azure/azure-functions/functions-overview): Azure Functions eignet sich hervorragend für ereignisgesteuerte Workflows. Beispiele hierfür sind das Antworten auf Webhooks, die Verarbeitung von Elementen in Warteschlangen oder im Blobspeicher sowie Zeitgeber. Informationen zum Einstieg in Azure Functions finden Sie unter [Erstellen Ihrer ersten Funktion mit Visual Studio](/azure/azure-functions/functions-create-your-first-function-visual-studio).

* [Azure Virtual Machines](/azure/virtual-machines/): Wenn App Service Ihren Anforderungen für das Hosten einer vorhandenen Anwendung aufgrund von bestimmten Abhängigkeiten nicht entspricht, ist Virtual Machines für den Anfang am besten geeignet. Informationen zu den ersten Schritten mit Virtual Machines und ASP.NET oder WCF finden Sie unter [Deploy an ASP.NET app to an Azure virtual machine](https://tutorials.visualstudio.com/aspnet-vm/intro) (Bereitstellen einer ASP.NET-App auf einem virtuellen Azure-Computer).

> [!TIP]
> Weitere Informationen zur Auswahl eines Diensts finden Sie unter [Auswählen eines Azure-Computediensts für Ihre Anwendung](/azure/architecture/guide/technology-choices/compute-decision-tree).

## <a name="choose-a-data-storage-service"></a>Auswählen eines Datenspeicherdiensts

Azure bietet je nach Ihren Anforderungen verschiedene Dienste zum Speichern von Daten. Die am häufigsten verwendeten Datendienste für .NET-Entwickler sind:

* [Azure SQL-Datenbank](/azure/sql-database/): Wenn Sie eine Anwendung in die Cloud migrieren möchten, die bereits SQL Server verwendet, bietet sich natürlich Azure SQL-Datenbank als Ausgangspunkt an. Informationen zu den ersten Schritten finden Sie unter [Tutorial: Erstellen einer ASP.NET-App in Azure mit SQL-Datenbank](/azure/app-service/app-service-web-tutorial-dotnet-sqldatabase).

* [Azure Cosmos DB](/azure/cosmos-db/): Azure Cosmos DB ist eine moderne Datenbank, die für die Cloud entwickelt wurde. Wenn Sie eine neue Anwendung starten, die noch keine bestimmte Datenbankabhängigkeit aufweist, sollten Sie sich Azure Cosmos DB ansehen. Cosmos DB ist eine gute Wahl für neue Web-, Mobil-, Gaming- und IoT-Anwendungen, bei denen Dinge wie automatische Skalierung, vorhersagbare Leistung, kurze Reaktionszeiten und die Möglichkeit zum Abfragen von schemafreien Daten wichtig sind. Informationen zu den ersten Schritten finden Sie unter [Schnellstart: Erstellen einer .NET-Web-App mit Azure Cosmos DB unter Verwendung der SQL-API und des Azure-Portals](/azure/cosmos-db/create-sql-api-dotnet).

* [Azure Blob Storage](/azure/storage/): Azure Blob Storage ist für das Speichern und Abrufen großer binärer Objekte wie Bilder, Dateien und Streams optimiert. Objektspeicher ermöglichen die Verwaltung extrem großer Mengen unstrukturierter Daten. Informationen zu den ersten Schritten finden Sie unter [Schnellstart: Verwenden von .NET zum Erstellen eines Blobs im Objektspeicher](/azure/storage/blobs/storage-quickstart-blobs-dotnet).

> [!TIP]
> Informationen finden Sie unter [Auswählen des richtigen Datenspeichers](/azure/architecture/guide/technology-choices/data-store-overview).

## <a name="connect-to-azure-services"></a>Herstellen einer Verbindung mit Azure-Diensten

Wenn Sie Visual Studio verwenden, können Sie Ihren Projekten Unterstützung für bestimmte Azure-Dienste hinzufügen. Über das Dialogfeld **Verbundene Dienste** in Visual Studio können Ihren Projekten ganz einfach alle erforderlichen Verweise, Verbindungscode und Konfigurationseinstellungen hinzugefügt werden. Einige häufig verwendete Azure-Dienste werden standardmäßig unterstützt, etwa [Storage](/azure/vs-azure-tools-connected-services-storage), [Azure Active Directory](/azure/active-directory/develop/vs-active-directory-add-connected-service)-Authentifizierung, [Azure Key Vault](/azure/key-vault/vs-key-vault-add-connected-service) und [Cognitive Services](/azure/cognitive-services/) (beispielsweise [Maschinelles Sehen](/azure/cognitive-services/computer-vision/vs-computer-vision-connected-service)). Weitere Dienste, einschließlich Dienste von Drittanbietern, sind als Erweiterungen im [Visual Studio Marketplace](https://marketplace.visualstudio.com/search?term=connected%20service&target=VS&category=Tools&vsVersion=&subCategory=All&sortBy=Relevance) verfügbar.

## <a name="using-the-azure-sdk-for-net"></a>Verwenden des Azure SDK für .NET

Wenn Sie das Azure SDK für .NET verwenden, um auf Ihre Azure-Ressourcen zuzugreifen oder diese zu verwalten, beachten Sie Folgendes:

* **Authentifizierung:** Viele Bibliotheken im SDK verwenden eine gemeinsame Authentifizierungsinfrastruktur, während einige Bibliotheken Authentifizierungsmechanismen verwenden, die spezifisch für den von ihnen genutzten Dienst sind. Weitere Informationen finden Sie unter [Authentifizierung mit dem Azure SDK für .NET](authentication.md).
* **Protokollierung:** Falls unterstützt, bieten die Clientbibliotheken die Möglichkeit, Clientbibliotheksvorgänge zu protokollieren. Weitere Informationen finden Sie unter [Protokollierung mit dem Azure SDK für .NET](logging.md).
* **REST-API**: Das Azure SDK für .NET ist eine Abstraktion, die auf der [Azure-REST-API](/rest/api/azure/) basiert. Falls gewünscht, kann die Azure-REST-API anstelle des oder zusammen mit dem Azure SDK für .NET verwendet werden.

## <a name="diagnosing-problems-in-the-cloud"></a>Diagnostizieren von Problemen in der Cloud

Beim Bereitstellen Ihrer Anwendung in Azure kann es vorkommen, dass Dinge nicht mehr funktionieren, die in der Entwicklung keine Probleme bereitet haben. Nachstehend finden Sie zwei gute Einstiegspunkte in das Diagnostizieren von Probleme:

* **Remotedebuggen von Visual Studio aus**: Die meisten Azure-Computedienste (einschließlich der in diesem Dokument behandelten Dienste) unterstützen Remotedebuggen mit Visual Studio and das Abrufen von Protokollen. Zum Erkunden der Funktionen von Visual Studio mit Ihrer Anwendung öffnen Sie das Toolfenster „Cloud-Explorer“, indem Sie „Cloud-Explorer“ in die Schnellstart-Symbolleiste (rechts oben) von Visual Studio eingeben und dann in der Struktur Ihre Anwendung auswählen. Ausführliche Informationen finden Sie unter [Problembehandlung von Web-Apps in Azure App Service in Visual Studio](/azure/app-service/web-sites-dotnet-troubleshoot-visual-studio#remotedebug).

* **Application Insights**: [Application Insights](/azure/application-insights/) ist eine umfassende Lösung zur Überwachung der Leistung einer Anwendung (Application Performance Monitoring, APM), die Diagnose-, Telemetrie- und Leistungsdaten von Anwendungen automatisch erfasst. Informationen zum Einstieg das Sammeln von Diagnosedaten für Ihre App finden Sie unter [Starten der Überwachung Ihrer ASP.NET-Webanwendung](/azure/application-insights/quick-monitor-portal).

## <a name="next-steps"></a>Nächste Schritte

* [Bereitstellen Ihrer ersten ASP.NET Core-Web-App in Azure](/azure/app-service/app-service-web-get-started-dotnet)
* [Informationen zur Authentifizierung im Azure SDK für .NET](authentication.md)
* [Diagnostizieren von Fehlern in Ihren Cloud-Apps](https://devblogs.microsoft.com/aspnet/diagnosing-errors-on-your-cloud-apps/)
* Kostenloses E-Book [Azure-Schnellstarthandbuch für .NET-Entwickler](https://www.microsoft.com/net/download/thank-you/azure-quick-start-ebook) herunterladen
