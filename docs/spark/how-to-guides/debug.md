---
title: Debuggen einer .NET für Apache Spark-Anwendung unter Windows
description: Erfahren Sie, wie Sie eine .NET für Apache Spark-Anwendung unter Windows debuggen.
ms.date: 10/09/2020
ms.topic: conceptual
ms.custom: mvc,how-to
ms.openlocfilehash: 43531e6b2f9a79658f89b804dfa2bb97d6e9645b
ms.sourcegitcommit: b59237ca4ec763969a0dd775a3f8f39f8c59fe24
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2020
ms.locfileid: "91954983"
---
# <a name="debug-a-net-for-apache-spark-application"></a><span data-ttu-id="50a9b-103">Debuggen einer .NET für Apache Spark-Anwendung</span><span class="sxs-lookup"><span data-stu-id="50a9b-103">Debug a .NET for Apache Spark application</span></span>

<span data-ttu-id="50a9b-104">Diese Anleitung zeigt die Schritte, die Sie zum Debuggen einer .NET für Apache Spark-Anwendung unter Windows ausführen müssen.</span><span class="sxs-lookup"><span data-stu-id="50a9b-104">This how-to provides the steps to debug your .NET for Apache Spark application on Windows.</span></span>

## <a name="debug-your-application"></a><span data-ttu-id="50a9b-105">Debuggen einer Anwendung</span><span class="sxs-lookup"><span data-stu-id="50a9b-105">Debug your application</span></span>

<span data-ttu-id="50a9b-106">Öffnen Sie ein neues Eingabeaufforderungsfenster, und führen Sie den folgenden Befehl aus:</span><span class="sxs-lookup"><span data-stu-id="50a9b-106">Open a new command prompt window and run the following command:</span></span>

```shell
spark-submit \
  --class org.apache.spark.deploy.dotnet.DotnetRunner \
  --master local \
  <path-to-microsoft-spark-jar> \
  debug
```

<span data-ttu-id="50a9b-107">Beim Ausführen des Befehls wird die folgende Ausgabe angezeigt:</span><span class="sxs-lookup"><span data-stu-id="50a9b-107">When you run the command, you see the following output:</span></span>

```console
***********************************************************************
* .NET Backend running debug mode. Press enter to exit *
***********************************************************************
```

<span data-ttu-id="50a9b-108">Im Debugmodus startet DotnetRunner die .NET-Anwendung nicht, sondern wartet darauf, dass Sie diese starten.</span><span class="sxs-lookup"><span data-stu-id="50a9b-108">In debug mode, DotnetRunner does not launch the .NET application, but instead waits for you to start the .NET app.</span></span> <span data-ttu-id="50a9b-109">Lassen Sie die Eingabeaufforderung offen, und starten Sie die .NET-Anwendung über den C#-Debugger, um sie zu debuggen.</span><span class="sxs-lookup"><span data-stu-id="50a9b-109">Leave this command prompt window open and start your .NET application through C# debugger to debug your application.</span></span> <span data-ttu-id="50a9b-110">Starten Sie Ihre .NET-Anwendung mit einem C#-Debugger ([Visual Studio-Debugger für Windows/macOS](https://visualstudio.microsoft.com/vs/) oder [C#-Debuggererweiterung in Visual Studio Code](https://code.visualstudio.com/Docs/editor/debugging)), um sie zu debuggen.</span><span class="sxs-lookup"><span data-stu-id="50a9b-110">Start your .NET application with a C# debugger ([Visual Studio Debugger for Windows/macOS](https://visualstudio.microsoft.com/vs/) or [C# Debugger Extension in Visual Studio Code](https://code.visualstudio.com/Docs/editor/debugging)) to debug your application.</span></span>

## <a name="debug-a-user-defined-function-udf"></a><span data-ttu-id="50a9b-111">Debuggen einer benutzerdefinierten Funktion (User-Defined Function, UDF)</span><span class="sxs-lookup"><span data-stu-id="50a9b-111">Debug a user-defined function (UDF)</span></span>

> [!NOTE]
> <span data-ttu-id="50a9b-112">Benutzerdefinierte Funktionen werden mit dem Visual Studio-Debugger nur unter Windows unterstützt.</span><span class="sxs-lookup"><span data-stu-id="50a9b-112">User-defined functions are supported only on Windows with Visual Studio Debugger.</span></span>

<span data-ttu-id="50a9b-113">Bevor Sie `spark-submit` ausführen, legen Sie die folgende Umgebungsvariable fest:</span><span class="sxs-lookup"><span data-stu-id="50a9b-113">Before running `spark-submit`, set the following environment variable:</span></span>

```bat
set DOTNET_WORKER_DEBUG=1
```

<span data-ttu-id="50a9b-114">Wenn Sie Ihre Spark-Anwendung ausführen, wird das Fenster `Choose Just-In-Time Debugger` geöffnet.</span><span class="sxs-lookup"><span data-stu-id="50a9b-114">When you run your Spark application, a `Choose Just-In-Time Debugger` window will pop up.</span></span> <span data-ttu-id="50a9b-115">Wählen Sie einen Visual Studio-Debugger aus.</span><span class="sxs-lookup"><span data-stu-id="50a9b-115">Choose a Visual Studio debugger.</span></span>

<span data-ttu-id="50a9b-116">Der Debugger unterbricht die Ausführung in [TaskRunner.cs](https://github.com/dotnet/spark/blob/5e9c08b430b4bc56b5f42252c4b73437377afaed/src/csharp/Microsoft.Spark.Worker/TaskRunner.cs#L52) an der folgenden Stelle:</span><span class="sxs-lookup"><span data-stu-id="50a9b-116">The debugger will break at the following location in [TaskRunner.cs](https://github.com/dotnet/spark/blob/5e9c08b430b4bc56b5f42252c4b73437377afaed/src/csharp/Microsoft.Spark.Worker/TaskRunner.cs#L52):</span></span>

```csharp
if (EnvironmentUtils.GetEnvironmentVariableAsBool("DOTNET_WORKER_DEBUG"))
{
    Debugger.Launch(); // <-- The debugger will break here.
}
```

<span data-ttu-id="50a9b-117">Navigieren Sie zu der *.cs*-Datei mit der benutzerdefinierten Funktion, die Sie debuggen möchten, und [legen Sie einen Breakpoint fest](/visualstudio/debugger/using-breakpoints?view=vs-2019).</span><span class="sxs-lookup"><span data-stu-id="50a9b-117">Navigate to the *.cs* file that contains the UDF that you plan to debug, and [set a breakpoint](/visualstudio/debugger/using-breakpoints?view=vs-2019).</span></span> <span data-ttu-id="50a9b-118">Der Breakpoint zeigt die Meldung `The breakpoint will not currently be hit` an, weil der Worker die Assembly mit der benutzerdefinierten Funktion noch nicht geladen hat.</span><span class="sxs-lookup"><span data-stu-id="50a9b-118">The breakpoint will say `The breakpoint will not currently be hit` because the worker hasn't loaded the assembly that contains UDF yet.</span></span>

<span data-ttu-id="50a9b-119">Drücken Sie `F5`, um die Anwendung fortzusetzen. Der Breakpoint wird schließlich erreicht.</span><span class="sxs-lookup"><span data-stu-id="50a9b-119">Hit `F5` to continue your application and the breakpoint will eventually be hit.</span></span>

> [!NOTE]
> <span data-ttu-id="50a9b-120">Das Fenster zur Auswahl eines Just-In-Time-Debuggers wird für jeden Task angezeigt.</span><span class="sxs-lookup"><span data-stu-id="50a9b-120">The Choose Just-In-Time Debugger window pops up for each task.</span></span> <span data-ttu-id="50a9b-121">Um eine übermäßige Anzeige von Popupfenstern zu vermeiden, legen Sie eine niedrige Anzahl von Executors fest.</span><span class="sxs-lookup"><span data-stu-id="50a9b-121">To avoid excessive pop-ups, set the number of executors to a low number.</span></span> <span data-ttu-id="50a9b-122">Sie können beispielsweise die Option **--master local[1]** für „spark-submit“ verwenden, um die Anzahl von Tasks auf 1 festzulegen. Damit wird eine einzelne Debuggerinstanz gestartet.</span><span class="sxs-lookup"><span data-stu-id="50a9b-122">For example, you can use the **--master local[1]** option for spark-submit to set the number of tasks to 1, which launches a single debugger instance.</span></span>

## <a name="debug-scala-code"></a><span data-ttu-id="50a9b-123">Debuggen von Scala-Code</span><span class="sxs-lookup"><span data-stu-id="50a9b-123">Debug Scala code</span></span>

<span data-ttu-id="50a9b-124">Wenn Sie den Scala-seitigen Code (`DotnetRunner`, `DotnetBackendHandler` usw.) debuggen müssen, können Sie den folgenden Befehl verwenden und mithilfe von [IntelliJ](https://www.jetbrains.com/help/idea/attaching-to-local-process.html) einen Debugger an den ausgeführten Prozess anfügen:</span><span class="sxs-lookup"><span data-stu-id="50a9b-124">If you need to debug the Scala-side code (`DotnetRunner`, `DotnetBackendHandler`, etc.), you can use the following command and attach a debugger to the running process using [IntelliJ](https://www.jetbrains.com/help/idea/attaching-to-local-process.html):</span></span>

```shell
spark-submit \
  --driver-java-options -agentlib:jdwp=transport=dt_socket,server=y,suspend=n,address=5005 \
  --class org.apache.spark.deploy.dotnet.DotnetRunner \
  --master local \
  <path-to-microsoft-spark-jar> \
  <path-to-your-app-exe> <argument(s)-to-your-app>
```

<span data-ttu-id="50a9b-125">Fügen Sie anschließend mit [IntelliJ](https://www.jetbrains.com/help/idea/attaching-to-local-process.html) dem laufenden Prozess einen Debugger an.</span><span class="sxs-lookup"><span data-stu-id="50a9b-125">After you run the command, attach a debugger to the running process using [Intellij](https://www.jetbrains.com/help/idea/attaching-to-local-process.html).</span></span>

## <a name="next-steps"></a><span data-ttu-id="50a9b-126">Nächste Schritte</span><span class="sxs-lookup"><span data-stu-id="50a9b-126">Next steps</span></span>

* [<span data-ttu-id="50a9b-127">Erste Schritte mit .NET für Apache Spark</span><span class="sxs-lookup"><span data-stu-id="50a9b-127">Get started with .NET for Apache Spark</span></span>](../tutorials/get-started.md)
* [<span data-ttu-id="50a9b-128">Bereitstellen einer .NET für Apache Spark-Anwendung in Azure HDInsight</span><span class="sxs-lookup"><span data-stu-id="50a9b-128">Deploy a .NET for Apache Spark application to Azure HDInsight</span></span>](../tutorials/hdinsight-deployment.md)
* [<span data-ttu-id="50a9b-129">Bereitstellen einer .NET für Apache Spark-Anwendung in Databricks</span><span class="sxs-lookup"><span data-stu-id="50a9b-129">Deploy a .NET for Apache Spark application to Databricks</span></span>](../tutorials/databricks-deployment.md)
* [<span data-ttu-id="50a9b-130">Bereitstellen einer .NET für Apache Spark-Anwendung in Amazon EMR Spark</span><span class="sxs-lookup"><span data-stu-id="50a9b-130">Deploy a .NET for Apache Spark application to Amazon EMR Spark</span></span>](../tutorials/amazon-emr-spark-deployment.md)
