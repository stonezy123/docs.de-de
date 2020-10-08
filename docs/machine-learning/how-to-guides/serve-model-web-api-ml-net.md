---
title: Bereitstellen eines Modells in einer ASP.NET Core-Web-API
description: Bereitstellen eines Machine Learning-Modells zur ML.NET-Standpunktanalyse über das Internet mithilfe der ASP.NET Core-Web-API
ms.date: 11/07/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc,how-to
ms.openlocfilehash: f588d4681ee277ad15b50d5553473b1c9e84d578
ms.sourcegitcommit: 97405ed212f69b0a32faa66a5d5fae7e76628b68
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2020
ms.locfileid: "91608763"
---
# <a name="deploy-a-model-in-an-aspnet-core-web-api"></a><span data-ttu-id="cd448-103">Bereitstellen eines Modells in einer ASP.NET Core-Web-API</span><span class="sxs-lookup"><span data-stu-id="cd448-103">Deploy a model in an ASP.NET Core Web API</span></span>

<span data-ttu-id="cd448-104">Hier erfahren Sie, wie Sie ein vorab trainiertes ML.NET-Machine Learning-Modell mithilfe einer ASP.NET Core-Web-API im Internet bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="cd448-104">Learn how to serve a pre-trained ML.NET machine learning model on the web using an ASP.NET Core Web API.</span></span> <span data-ttu-id="cd448-105">Das Bereitstellen eines Modells über eine Web-API ermöglicht Vorhersagen über HTTP-Standardmethoden.</span><span class="sxs-lookup"><span data-stu-id="cd448-105">Serving a model over a web API enables predictions via standard HTTP methods.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="cd448-106">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="cd448-106">Prerequisites</span></span>

- <span data-ttu-id="cd448-107">[Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) oder höher oder Visual Studio 2017 Version 15.6 oder höher mit installierter Workload „Plattformübergreifende .NET Core-Entwicklung“.</span><span class="sxs-lookup"><span data-stu-id="cd448-107">[Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) or later or Visual Studio 2017 version 15.6 or later with the ".NET Core cross-platform development" workload installed.</span></span>
- <span data-ttu-id="cd448-108">PowerShell.</span><span class="sxs-lookup"><span data-stu-id="cd448-108">PowerShell.</span></span>
- <span data-ttu-id="cd448-109">Vorab trainiertes Modell.</span><span class="sxs-lookup"><span data-stu-id="cd448-109">Pre-trained model.</span></span> <span data-ttu-id="cd448-110">Verwenden Sie das [Tutorial für die ML.NET-Standpunktanalyse](../tutorials/sentiment-analysis.md), um Ihr eigenes Modell zu erstellen, oder laden Sie dieses [vorab trainierte Machine Learning-Modell für die Standpunktanalyse](https://github.com/dotnet/samples/blob/master/machine-learning/models/sentimentanalysis/sentiment_model.zip) herunter.</span><span class="sxs-lookup"><span data-stu-id="cd448-110">Use the [ML.NET Sentiment Analysis tutorial](../tutorials/sentiment-analysis.md) to build your own model or download this [pre-trained sentiment analysis machine learning model](https://github.com/dotnet/samples/blob/master/machine-learning/models/sentimentanalysis/sentiment_model.zip)</span></span>

## <a name="create-aspnet-core-web-api-project"></a><span data-ttu-id="cd448-111">Erstellen eines ASP.NET Core-Web-API-Projekts</span><span class="sxs-lookup"><span data-stu-id="cd448-111">Create ASP.NET Core Web API project</span></span>

1. <span data-ttu-id="cd448-112">Öffnen Sie Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="cd448-112">Open Visual Studio 2017.</span></span> <span data-ttu-id="cd448-113">Wählen Sie in der Menüleiste **Datei > Neues Projekt** aus.</span><span class="sxs-lookup"><span data-stu-id="cd448-113">Select **File > New > Project** from the menu bar.</span></span> <span data-ttu-id="cd448-114">Wählen Sie im Dialogfeld „Neues Projekt“ den Knoten **Visual C#** und anschließend den Knoten **Web** aus.</span><span class="sxs-lookup"><span data-stu-id="cd448-114">In the New Project dialog, select the **Visual C#** node followed by the **Web** node.</span></span> <span data-ttu-id="cd448-115">Wählen Sie dann die Projektvorlage **ASP.NET Core-Webanwendung** aus.</span><span class="sxs-lookup"><span data-stu-id="cd448-115">Then select the **ASP.NET Core Web Application** project template.</span></span> <span data-ttu-id="cd448-116">Geben Sie „SentimentAnalysisWebAPI“ im Textfeld **Name** ein, und wählen Sie die Schaltfläche **OK** aus.</span><span class="sxs-lookup"><span data-stu-id="cd448-116">In the **Name** text box, type "SentimentAnalysisWebAPI" and then select the **OK** button.</span></span>

1. <span data-ttu-id="cd448-117">Wählen Sie im Fenster, das die verschiedenen Typen von ASP.NET Core-Projekten anzeigt, **API** und dann die **OK**-Schaltfläche aus.</span><span class="sxs-lookup"><span data-stu-id="cd448-117">In the window that displays the different types of ASP.NET Core Projects, select **API** and the select the **OK** button.</span></span>

1. <span data-ttu-id="cd448-118">Erstellen Sie ein Verzeichnis mit dem Namen *MLModels* in Ihrem Projekt, um Ihre vorgefertigten Machine Learning-Modelldateien zu speichern:</span><span class="sxs-lookup"><span data-stu-id="cd448-118">Create a directory named *MLModels* in your project to save your pre-built machine learning model files:</span></span>

    <span data-ttu-id="cd448-119">Klicken Sie im Projektmappen-Explorer mit der rechten Maustaste auf das Projekt, und wählen Sie „Hinzufügen > Neuer Ordner“ aus.</span><span class="sxs-lookup"><span data-stu-id="cd448-119">In Solution Explorer, right-click on your project and select Add > New Folder.</span></span> <span data-ttu-id="cd448-120">Geben Sie „MLModels“ ein, und drücken Sie die EINGABETASTE.</span><span class="sxs-lookup"><span data-stu-id="cd448-120">Type "MLModels" and hit Enter.</span></span>

1. <span data-ttu-id="cd448-121">Installieren des **Microsoft.ML NuGet-Pakets**:</span><span class="sxs-lookup"><span data-stu-id="cd448-121">Install the **Microsoft.ML NuGet Package**:</span></span>

    <span data-ttu-id="cd448-122">Klicken Sie im Projektmappen-Explorer mit der rechten Maustaste auf das Projekt, und wählen Sie **NuGet-Pakete verwalten** aus.</span><span class="sxs-lookup"><span data-stu-id="cd448-122">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="cd448-123">Wählen Sie als Paketquelle „nuget.org“ aus. Wählen Sie anschließend die Registerkarte **Durchsuchen** aus, suchen Sie nach „Microsoft.ML“, und wählen Sie das Paket in der Liste und anschließend die Schaltfläche „Installieren“ aus.</span><span class="sxs-lookup"><span data-stu-id="cd448-123">Choose "nuget.org" as the Package source, select the Browse tab, search for **Microsoft.ML**, select that package in the list, and select the Install button.</span></span> <span data-ttu-id="cd448-124">Wählen Sie die Schaltfläche **OK** im Dialogfeld **Vorschau der Änderungen** und dann die Schaltfläche **Ich stimme zu** im Dialogfeld „Zustimmung zur Lizenz“ aus, wenn Sie den Lizenzbedingungen für die aufgelisteten Pakete zustimmen.</span><span class="sxs-lookup"><span data-stu-id="cd448-124">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the License Acceptance dialog if you agree with the license terms for the packages listed.</span></span>

1. <span data-ttu-id="cd448-125">Installieren Sie das NuGet-Paket **Microsoft.Extensions.ML**:</span><span class="sxs-lookup"><span data-stu-id="cd448-125">Install the **Microsoft.Extensions.ML Nuget Package**:</span></span>

    <span data-ttu-id="cd448-126">Klicken Sie im Projektmappen-Explorer mit der rechten Maustaste auf das Projekt, und wählen Sie **NuGet-Pakete verwalten** aus.</span><span class="sxs-lookup"><span data-stu-id="cd448-126">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="cd448-127">Wählen Sie als Paketquelle „nuget.org“ aus. Wählen Sie anschließend die Registerkarte **Durchsuchen** aus, suchen Sie nach „Microsoft.Extensions.ML“, und wählen Sie das Paket in der Liste und anschließend die Schaltfläche „Installieren“ aus.</span><span class="sxs-lookup"><span data-stu-id="cd448-127">Choose "nuget.org" as the Package source, select the Browse tab, search for **Microsoft.Extensions.ML**, select that package in the list, and select the Install button.</span></span> <span data-ttu-id="cd448-128">Wählen Sie die Schaltfläche **OK** im Dialogfeld **Vorschau der Änderungen** und dann die Schaltfläche **Ich stimme zu** im Dialogfeld „Zustimmung zur Lizenz“ aus, wenn Sie den Lizenzbedingungen für die aufgelisteten Pakete zustimmen.</span><span class="sxs-lookup"><span data-stu-id="cd448-128">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the License Acceptance dialog if you agree with the license terms for the packages listed.</span></span>

### <a name="add-model-to-aspnet-core-web-api-project"></a><span data-ttu-id="cd448-129">Hinzufügen eines Modells zum ASP.NET Core-Web-API-Projekt</span><span class="sxs-lookup"><span data-stu-id="cd448-129">Add model to ASP.NET Core Web API project</span></span>

1. <span data-ttu-id="cd448-130">Kopieren Sie Ihr vorbereitetes Modell in das *MLModels*-Verzeichnis.</span><span class="sxs-lookup"><span data-stu-id="cd448-130">Copy your pre-built model to the *MLModels* directory</span></span>
1. <span data-ttu-id="cd448-131">Klicken Sie im Projektmappen-Explorer mit der rechten Maustaste auf die ZIP-Datei des Modells, und wählen Sie „Eigenschaften“ aus.</span><span class="sxs-lookup"><span data-stu-id="cd448-131">In Solution Explorer, right-click the model zip file and select Properties.</span></span> <span data-ttu-id="cd448-132">Ändern Sie unter „Erweitert“ den Wert von „In Ausgabeverzeichnis kopieren“ in „Kopieren, wenn neuer“.</span><span class="sxs-lookup"><span data-stu-id="cd448-132">Under Advanced, change the value of Copy to Output Directory to Copy if newer.</span></span>

## <a name="create-data-models"></a><span data-ttu-id="cd448-133">Erstellen von Datenmodellen</span><span class="sxs-lookup"><span data-stu-id="cd448-133">Create data models</span></span>

<span data-ttu-id="cd448-134">Sie müssen einige Klassen für die Eingabedaten und Vorhersagen erstellen.</span><span class="sxs-lookup"><span data-stu-id="cd448-134">You need to create some classes for your input data and predictions.</span></span> <span data-ttu-id="cd448-135">Fügen Sie dem Projekt eine neue Klasse hinzu:</span><span class="sxs-lookup"><span data-stu-id="cd448-135">Add a new class to your project:</span></span>

1. <span data-ttu-id="cd448-136">Erstellen Sie ein Verzeichnis mit dem Namen *DataModels* in Ihrem Projekt, um Ihre Datenmodelle zu speichern:</span><span class="sxs-lookup"><span data-stu-id="cd448-136">Create a directory named *DataModels* in your project to save your data models:</span></span>

    <span data-ttu-id="cd448-137">Klicken Sie im Projektmappen-Explorer mit der rechten Maustaste auf das Projekt, und wählen Sie „Hinzufügen > Neuer Ordner“ aus.</span><span class="sxs-lookup"><span data-stu-id="cd448-137">In Solution Explorer, right-click on your project and select Add > New Folder.</span></span> <span data-ttu-id="cd448-138">Geben Sie „DataModels“ ein, und drücken Sie die **EINGABETASTE**.</span><span class="sxs-lookup"><span data-stu-id="cd448-138">Type "DataModels" and hit **Enter**.</span></span>

2. <span data-ttu-id="cd448-139">Klicken Sie im Projektmappen-Explorer mit der rechten Maustaste auf das *DataModels*-Verzeichnis, und wählen Sie „Hinzufügen > Neues Element“ aus.</span><span class="sxs-lookup"><span data-stu-id="cd448-139">In Solution Explorer, right-click the *DataModels* directory, and then select Add > New Item.</span></span>
3. <span data-ttu-id="cd448-140">Wählen Sie im Dialogfeld **Neues Element hinzufügen** die Option **Klasse** aus, und ändern Sie das Feld **Name** in *SentimentData.cs*.</span><span class="sxs-lookup"><span data-stu-id="cd448-140">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *SentimentData.cs*.</span></span> <span data-ttu-id="cd448-141">Wählen Sie dann die Schaltfläche **Hinzufügen** aus.</span><span class="sxs-lookup"><span data-stu-id="cd448-141">Then, select the **Add** button.</span></span> <span data-ttu-id="cd448-142">Die Datei *SentimentData.cs* wird im Code-Editor geöffnet.</span><span class="sxs-lookup"><span data-stu-id="cd448-142">The *SentimentData.cs* file opens in the code editor.</span></span> <span data-ttu-id="cd448-143">Fügen Sie am Anfang der Datei *SentimentData.cs* die folgende using-Anweisung hinzu:</span><span class="sxs-lookup"><span data-stu-id="cd448-143">Add the following using statement to the top of *SentimentData.cs*:</span></span>

    ```csharp
    using Microsoft.ML.Data;
    ```

    <span data-ttu-id="cd448-144">Entfernen Sie die vorhandene Klassendefinition, und fügen Sie den folgenden Code der Datei **SentimentData.cs** hinzu:</span><span class="sxs-lookup"><span data-stu-id="cd448-144">Remove the existing class definition and add the following code to the **SentimentData.cs** file:</span></span>

    ```csharp
    public class SentimentData
    {
        [LoadColumn(0)]
        public string SentimentText;

        [LoadColumn(1)]
        [ColumnName("Label")]
        public bool Sentiment;
    }
    ```

4. <span data-ttu-id="cd448-145">Klicken Sie im Projektmappen-Explorer mit der rechten Maustaste auf das *DataModels*-Verzeichnis, und wählen Sie **Hinzufügen > Neues Element** aus.</span><span class="sxs-lookup"><span data-stu-id="cd448-145">In Solution Explorer, right-click the *DataModels* directory, and then select **Add > New Item**.</span></span>
5. <span data-ttu-id="cd448-146">Wählen Sie im Dialogfeld **Neues Element hinzufügen** die Option **Klasse** aus, und ändern Sie das Feld **Name** in *SentimentPrediction.cs*.</span><span class="sxs-lookup"><span data-stu-id="cd448-146">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *SentimentPrediction.cs*.</span></span> <span data-ttu-id="cd448-147">Wählen Sie dann die Schaltfläche „Hinzufügen“ aus.</span><span class="sxs-lookup"><span data-stu-id="cd448-147">Then, select the Add button.</span></span> <span data-ttu-id="cd448-148">Die Datei *SentimentPrediction.cs* wird im Code-Editor geöffnet.</span><span class="sxs-lookup"><span data-stu-id="cd448-148">The *SentimentPrediction.cs* file opens in the code editor.</span></span> <span data-ttu-id="cd448-149">Fügen Sie am Anfang der Datei *SentimentPrediction.cs* die folgende using-Anweisung hinzu:</span><span class="sxs-lookup"><span data-stu-id="cd448-149">Add the following using statement to the top of *SentimentPrediction.cs*:</span></span>

    ```csharp
    using Microsoft.ML.Data;
    ```

    <span data-ttu-id="cd448-150">Entfernen Sie die vorhandene Klassendefinition, und fügen Sie den folgenden Code der Datei *SentimentPrediction.cs* hinzu:</span><span class="sxs-lookup"><span data-stu-id="cd448-150">Remove the existing class definition and add the following code to the *SentimentPrediction.cs* file:</span></span>

    ```csharp
    public class SentimentPrediction : SentimentData
    {

        [ColumnName("PredictedLabel")]
        public bool Prediction { get; set; }

        public float Probability { get; set; }

        public float Score { get; set; }
    }
    ```

    <span data-ttu-id="cd448-151">`SentimentPrediction` erbt von `SentimentData`.</span><span class="sxs-lookup"><span data-stu-id="cd448-151">`SentimentPrediction` inherits from `SentimentData`.</span></span> <span data-ttu-id="cd448-152">Dadurch wird es einfacher, die Originaldaten in der `SentimentText`-Eigenschaft zusammen mit der vom Modell generierten Ausgabe zu sehen.</span><span class="sxs-lookup"><span data-stu-id="cd448-152">This makes it easier to see the original data in the `SentimentText` property along with the output generated by the model.</span></span>

## <a name="register-predictionenginepool-for-use-in-the-application"></a><span data-ttu-id="cd448-153">Registrieren von PredictionEnginePool zur Verwendung in der Anwendung</span><span class="sxs-lookup"><span data-stu-id="cd448-153">Register PredictionEnginePool for use in the application</span></span>

<span data-ttu-id="cd448-154">Um eine einzelne Vorhersage zu treffen, müssen Sie eine [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) erstellen.</span><span class="sxs-lookup"><span data-stu-id="cd448-154">To make a single prediction, you have to create a [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602).</span></span> <span data-ttu-id="cd448-155">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) ist nicht threadsicher.</span><span class="sxs-lookup"><span data-stu-id="cd448-155">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) is not thread-safe.</span></span> <span data-ttu-id="cd448-156">Außerdem müssen Sie eine Instanz davon überall dort erstellen, wo diese in Ihrer Anwendung erforderlich ist.</span><span class="sxs-lookup"><span data-stu-id="cd448-156">Additionally, you have to create an instance of it everywhere it is needed within your application.</span></span> <span data-ttu-id="cd448-157">Wenn die Anwendung wächst, kann dieser Prozess ggf. nicht mehr verwaltet werden.</span><span class="sxs-lookup"><span data-stu-id="cd448-157">As your application grows, this process can become unmanageable.</span></span> <span data-ttu-id="cd448-158">Für verbesserte Leistung und Threadsicherheit verwenden Sie eine Kombination aus Abhängigkeitsinjektion (Dependency Injection, DI) und dem `PredictionEnginePool`-Dienst, der einen [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) von [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602)-Objekten für die Verwendung in Ihrer gesamten Anwendung erstellt.</span><span class="sxs-lookup"><span data-stu-id="cd448-158">For improved performance and thread safety, use a combination of dependency injection and the `PredictionEnginePool` service, which creates an [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) of [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) objects for use throughout your application.</span></span>

<span data-ttu-id="cd448-159">Unter dem folgenden Link finden Sie weitere Informationen zur [Abhängigkeitsinjektion in ASP.NET Core](/aspnet/core/fundamentals/dependency-injection?view=aspnetcore-2.1).</span><span class="sxs-lookup"><span data-stu-id="cd448-159">The following link provides more information if you want to learn more about [dependency injection in ASP.NET Core](/aspnet/core/fundamentals/dependency-injection?view=aspnetcore-2.1).</span></span>

1. <span data-ttu-id="cd448-160">Öffnen Sie die *Startup.cs*-Klasse, und fügen Sie am Anfang der Datei die folgdende using-Anweisung hinzu:</span><span class="sxs-lookup"><span data-stu-id="cd448-160">Open the *Startup.cs* class and add the following using statement to the top of the file:</span></span>

    ```csharp
    using Microsoft.AspNetCore.Builder;
    using Microsoft.AspNetCore.Hosting;
    using Microsoft.AspNetCore.Mvc;
    using Microsoft.Extensions.Configuration;
    using Microsoft.Extensions.DependencyInjection;
    using Microsoft.Extensions.ML;
    using SentimentAnalysisWebAPI.DataModels;
    ```

2. <span data-ttu-id="cd448-161">Fügen Sie den folgenden Code der *ConfigureServices*-Methode hinzu:</span><span class="sxs-lookup"><span data-stu-id="cd448-161">Add the following code to the *ConfigureServices* method:</span></span>

    ```csharp
    services.AddPredictionEnginePool<SentimentData, SentimentPrediction>()
        .FromFile(modelName: "SentimentAnalysisModel", filePath:"MLModels/sentiment_model.zip", watchForChanges: true);
    ```

<span data-ttu-id="cd448-162">Auf der höchsten Stufe initialisiert dieser Code die Objekte und Dienste bei Anforderung automatisch für eine spätere Verwendung, sodass dies nicht manuell durchgeführt werden muss.</span><span class="sxs-lookup"><span data-stu-id="cd448-162">At a high level, this code initializes the objects and services automatically for later use when requested by the application instead of having to manually do it.</span></span>

<span data-ttu-id="cd448-163">Machine Learning-Modelle sind nicht statisch.</span><span class="sxs-lookup"><span data-stu-id="cd448-163">Machine learning models are not static.</span></span> <span data-ttu-id="cd448-164">Wenn neue Trainingsdaten verfügbar werden, wird das Modell erneut trainiert und erneut bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="cd448-164">As new training data becomes available, the model is retrained and redeployed.</span></span> <span data-ttu-id="cd448-165">Eine Möglichkeit, die neueste Version des Modells in Ihre Anwendung zu integrieren, besteht darin, die gesamte Anwendung erneut bereitzustellen.</span><span class="sxs-lookup"><span data-stu-id="cd448-165">One way to get the latest version of the model into your application is to redeploy the entire application.</span></span> <span data-ttu-id="cd448-166">Dies führt jedoch zu Ausfallzeiten der Anwendung.</span><span class="sxs-lookup"><span data-stu-id="cd448-166">However, this introduces application downtime.</span></span> <span data-ttu-id="cd448-167">Der `PredictionEnginePool`-Dienst bietet einen Mechanismus zum erneuten Laden eines aktualisierten Modells, ohne dass die Anwendung ausfällt.</span><span class="sxs-lookup"><span data-stu-id="cd448-167">The `PredictionEnginePool` service provides a mechanism to reload an updated model without taking your application down.</span></span>

<span data-ttu-id="cd448-168">Legen Sie den `watchForChanges`-Parameter auf `true` fest. Der `PredictionEnginePool` startet dann einen [`FileSystemWatcher`](xref:System.IO.FileSystemWatcher), der auf Änderungsbenachrichtigungen des Dateisystems lauscht und Ereignisse auslöst, wenn die Datei geändert wird.</span><span class="sxs-lookup"><span data-stu-id="cd448-168">Set the `watchForChanges` parameter to `true`, and the `PredictionEnginePool` starts a [`FileSystemWatcher`](xref:System.IO.FileSystemWatcher) that listens to the file system change notifications and raises events when there is a change to the file.</span></span> <span data-ttu-id="cd448-169">Dadurch wird der `PredictionEnginePool` aufgefordert, das Modell automatisch erneut zu laden.</span><span class="sxs-lookup"><span data-stu-id="cd448-169">This prompts the `PredictionEnginePool` to automatically reload the model.</span></span>

<span data-ttu-id="cd448-170">Das Modell wird durch den Parameter `modelName` identifiziert, sodass bei der Änderung mehrere Modelle pro Anwendung erneut geladen werden können.</span><span class="sxs-lookup"><span data-stu-id="cd448-170">The model is identified by the `modelName` parameter so that more than one model per application can be reloaded upon change.</span></span>

> [!TIP]
> <span data-ttu-id="cd448-171">Alternativ können Sie beim Arbeiten mit Modellen, die remote gespeichert sind, die `FromUri`-Methode verwenden.</span><span class="sxs-lookup"><span data-stu-id="cd448-171">Alternatively, you can use the `FromUri` method when working with models stored remotely.</span></span> <span data-ttu-id="cd448-172">Anstatt auf Dateiänderungsereignisse zu warten, fragt `FromUri` den Remotespeicherort nach Änderungen ab.</span><span class="sxs-lookup"><span data-stu-id="cd448-172">Rather than watching for file changed events, `FromUri` polls the remote location for changes.</span></span> <span data-ttu-id="cd448-173">Das Abruf Intervall beträgt standardmäßig 5 Minuten.</span><span class="sxs-lookup"><span data-stu-id="cd448-173">The polling interval defaults to 5 minutes.</span></span> <span data-ttu-id="cd448-174">Sie können das Abrufintervall basierend auf den Anforderungen Ihrer Anwendung vergrößern oder verkleinern.</span><span class="sxs-lookup"><span data-stu-id="cd448-174">You can increase or decrease the polling interval based on your application's requirements.</span></span> <span data-ttu-id="cd448-175">Im folgenden Codebeispiel fragt der `PredictionEnginePool` das am angegebenen URI gespeicherte Modell jede Minute ab.</span><span class="sxs-lookup"><span data-stu-id="cd448-175">In the code sample below, the `PredictionEnginePool` polls the model stored at the specified URI every minute.</span></span>
>
>```csharp
>services.AddPredictionEnginePool<SentimentData, SentimentPrediction>()
>   .FromUri(
>       modelName: "SentimentAnalysisModel",
>       uri:"https://github.com/dotnet/samples/raw/master/machine-learning/models/sentimentanalysis/sentiment_model.zip",
>       period: TimeSpan.FromMinutes(1));
>```

## <a name="create-predict-controller"></a><span data-ttu-id="cd448-176">Erstellen des Vorhersagecontrollers</span><span class="sxs-lookup"><span data-stu-id="cd448-176">Create Predict controller</span></span>

<span data-ttu-id="cd448-177">Um die eingehenden HTTP-Anforderungen zu verarbeiten, erstellen Sie einen Controller.</span><span class="sxs-lookup"><span data-stu-id="cd448-177">To process your incoming HTTP requests, create a controller.</span></span>

1. <span data-ttu-id="cd448-178">Klicken Sie im Projektmappen-Explorer mit der rechten Maustaste auf das *Controllers*-Verzeichnis, und wählen Sie **Hinzufügen > Controller** aus.</span><span class="sxs-lookup"><span data-stu-id="cd448-178">In Solution Explorer, right-click the *Controllers* directory, and then select **Add > Controller**.</span></span>
1. <span data-ttu-id="cd448-179">Wählen Sie im Dialogfeld **Neues Element hinzufügen** die Option **API-Controller – Leer**  und dann **Hinzufügen** aus.</span><span class="sxs-lookup"><span data-stu-id="cd448-179">In the **Add New Item** dialog box, select **API Controller Empty** and select **Add**.</span></span>
1. <span data-ttu-id="cd448-180">Ändern Sie in der Eingabeaufforderung das Feld **Controllername** in *PredictController.cs*.</span><span class="sxs-lookup"><span data-stu-id="cd448-180">In the prompt change the **Controller Name** field to *PredictController.cs*.</span></span> <span data-ttu-id="cd448-181">Wählen Sie dann die Schaltfläche „Hinzufügen“ aus.</span><span class="sxs-lookup"><span data-stu-id="cd448-181">Then, select the Add button.</span></span> <span data-ttu-id="cd448-182">Die Datei *PredictController.cs* wird im Code-Editor geöffnet.</span><span class="sxs-lookup"><span data-stu-id="cd448-182">The *PredictController.cs* file opens in the code editor.</span></span> <span data-ttu-id="cd448-183">Fügen Sie am Anfang der Datei *PredictController.cs* die folgende using-Anweisung hinzu:</span><span class="sxs-lookup"><span data-stu-id="cd448-183">Add the following using statement to the top of *PredictController.cs*:</span></span>

    ```csharp
    using System;
    using Microsoft.AspNetCore.Mvc;
    using Microsoft.Extensions.ML;
    using SentimentAnalysisWebAPI.DataModels;
    ```

    <span data-ttu-id="cd448-184">Entfernen Sie die vorhandene Klassendefinition, und fügen Sie den folgenden Code der Datei *PredictController.cs* hinzu:</span><span class="sxs-lookup"><span data-stu-id="cd448-184">Remove the existing class definition and add the following code to the *PredictController.cs* file:</span></span>

    ```csharp
    public class PredictController : ControllerBase
    {
        private readonly PredictionEnginePool<SentimentData, SentimentPrediction> _predictionEnginePool;

        public PredictController(PredictionEnginePool<SentimentData,SentimentPrediction> predictionEnginePool)
        {
            _predictionEnginePool = predictionEnginePool;
        }

        [HttpPost]
        public ActionResult<string> Post([FromBody] SentimentData input)
        {
            if(!ModelState.IsValid)
            {
                return BadRequest();
            }

            SentimentPrediction prediction = _predictionEnginePool.Predict(modelName: "SentimentAnalysisModel", example: input);

            string sentiment = Convert.ToBoolean(prediction.Prediction) ? "Positive" : "Negative";

            return Ok(sentiment);
        }
    }
    ```

<span data-ttu-id="cd448-185">Mit diesem Code wird die `PredictionEnginePool` durch Übergabe an den Konstruktor des Controllers zugewiesen, den Sie über die Abhängigkeitsinjektion erhalten.</span><span class="sxs-lookup"><span data-stu-id="cd448-185">This code assigns the `PredictionEnginePool` by passing it to the controller's constructor which you get via dependency injection.</span></span> <span data-ttu-id="cd448-186">Dann verwendet die `Post`-Methode des `Predict`-Controllers den `PredictionEnginePool`, um mithilfe des in der `Startup`-Klasse registrierten `SentimentAnalysisModel` Vorhersagen zu treffen und bei Erfolg die Ergebnisse an den Benutzer zurückzugeben.</span><span class="sxs-lookup"><span data-stu-id="cd448-186">Then, the `Predict` controller's `Post` method uses the `PredictionEnginePool` to make predictions using the `SentimentAnalysisModel` registered in the `Startup` class and returns the results back to the user if successful.</span></span>

## <a name="test-web-api-locally"></a><span data-ttu-id="cd448-187">Lokales Testen der Web-API</span><span class="sxs-lookup"><span data-stu-id="cd448-187">Test web API locally</span></span>

<span data-ttu-id="cd448-188">Nachdem alles eingerichtet ist, ist es Zeit, die Anwendung zu testen.</span><span class="sxs-lookup"><span data-stu-id="cd448-188">Once everything is set up, it's time to test the application.</span></span>

1. <span data-ttu-id="cd448-189">Führen Sie die Anwendung aus.</span><span class="sxs-lookup"><span data-stu-id="cd448-189">Run the application.</span></span>
1. <span data-ttu-id="cd448-190">Öffnen Sie PowerShell, und geben Sie den folgenden Code ein, wobei PORT der Port ist, auf dem Ihre Anwendung lauscht.</span><span class="sxs-lookup"><span data-stu-id="cd448-190">Open PowerShell and enter the following code where PORT is the port your application is listening on.</span></span>

    ```powershell
    Invoke-RestMethod "https://localhost:<PORT>/api/predict" -Method Post -Body (@{SentimentText="This was a very bad steak"} | ConvertTo-Json) -ContentType "application/json"
    ```

    <span data-ttu-id="cd448-191">Bei erfolgreicher Ausführung sollte die Ausgabe dem folgenden Text ähneln:</span><span class="sxs-lookup"><span data-stu-id="cd448-191">If successful, the output should look similar to the text below:</span></span>

    ```powershell
    Negative
    ```

<span data-ttu-id="cd448-192">Herzlichen Glückwunsch!</span><span class="sxs-lookup"><span data-stu-id="cd448-192">Congratulations!</span></span> <span data-ttu-id="cd448-193">Sie haben Ihr Modell erfolgreich bereitgestellt, um mit einer ASP.NET Core-Web-API Vorhersagen über das Internet zu treffen.</span><span class="sxs-lookup"><span data-stu-id="cd448-193">You have successfully served your model to make predictions over the internet using an ASP.NET Core Web API.</span></span>

## <a name="next-steps"></a><span data-ttu-id="cd448-194">Nächste Schritte</span><span class="sxs-lookup"><span data-stu-id="cd448-194">Next Steps</span></span>

- [<span data-ttu-id="cd448-195">Bereitstellung in Azure</span><span class="sxs-lookup"><span data-stu-id="cd448-195">Deploy to Azure</span></span>](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs#deploy-the-app-to-azure)
