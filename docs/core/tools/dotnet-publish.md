---
title: Befehl „dotnet publish“
description: Der Befehl „dotnet publish“ dient zum Veröffentlichen eines .NET Core-Projekts oder einer .NET Core-Projektmappe in einem Verzeichnis.
ms.date: 02/24/2020
ms.openlocfilehash: 2c33f99ce652dadc6e0c1a4c5e9e78fff9f54254
ms.sourcegitcommit: 4d45bda8cd9558ea8af4be591e3d5a29360c1ece
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2020
ms.locfileid: "91654893"
---
# <a name="dotnet-publish"></a><span data-ttu-id="ecd7d-103">dotnet publish</span><span class="sxs-lookup"><span data-stu-id="ecd7d-103">dotnet publish</span></span>

<span data-ttu-id="ecd7d-104">**Dieser Artikel gilt für:** ✔️ .NET Core 2.1 SDK und neuere Versionen</span><span class="sxs-lookup"><span data-stu-id="ecd7d-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="ecd7d-105">name</span><span class="sxs-lookup"><span data-stu-id="ecd7d-105">Name</span></span>

<span data-ttu-id="ecd7d-106">`dotnet publish` veröffentlicht die Anwendung und ihre Abhängigkeiten in einem Ordner für die Bereitstellung auf einem Hostsystem.</span><span class="sxs-lookup"><span data-stu-id="ecd7d-106">`dotnet publish` - Publishes the application and its dependencies to a folder for deployment to a hosting system.</span></span>

## <a name="synopsis"></a><span data-ttu-id="ecd7d-107">Übersicht</span><span class="sxs-lookup"><span data-stu-id="ecd7d-107">Synopsis</span></span>

```dotnetcli
dotnet publish [<PROJECT>|<SOLUTION>] [-c|--configuration <CONFIGURATION>]
    [-f|--framework <FRAMEWORK>] [--force] [--interactive]
    [--manifest <PATH_TO_MANIFEST_FILE>] [--no-build] [--no-dependencies]
    [--no-restore] [--nologo] [-o|--output <OUTPUT_DIRECTORY>]
    [-p:PublishReadyToRun=true] [-p:PublishSingleFile=true] [-p:PublishTrimmed=true]
    [-r|--runtime <RUNTIME_IDENTIFIER>] [--self-contained [true|false]]
    [--no-self-contained] [-v|--verbosity <LEVEL>]
    [--version-suffix <VERSION_SUFFIX>]

dotnet publish -h|--help
```

## <a name="description"></a><span data-ttu-id="ecd7d-108">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="ecd7d-108">Description</span></span>

<span data-ttu-id="ecd7d-109">`dotnet publish` kompiliert die Anwendung, liest ihre Abhängigkeiten, die in der Projektdatei angegeben sind, und veröffentlicht die resultierenden Dateien in einem Verzeichnis.</span><span class="sxs-lookup"><span data-stu-id="ecd7d-109">`dotnet publish` compiles the application, reads through its dependencies specified in the project file, and publishes the resulting set of files to a directory.</span></span> <span data-ttu-id="ecd7d-110">Die Ausgabe umfasst die folgenden Objekte:</span><span class="sxs-lookup"><span data-stu-id="ecd7d-110">The output includes the following assets:</span></span>

- <span data-ttu-id="ecd7d-111">Intermediate Language-Code (IL) in einer Assembly mit einer *DLL*-Erweiterung.</span><span class="sxs-lookup"><span data-stu-id="ecd7d-111">Intermediate Language (IL) code in an assembly with a *dll* extension.</span></span>
- <span data-ttu-id="ecd7d-112">Die Datei *.deps.json*, die alle Abhängigkeiten des Projekts enthält</span><span class="sxs-lookup"><span data-stu-id="ecd7d-112">A *.deps.json* file that includes all of the dependencies of the project.</span></span>
- <span data-ttu-id="ecd7d-113">Die Datei *.runtimeconfig.json*, die die Shared Runtime, die von der Anwendung erwartet wird, sowie andere Konfigurationsoptionen für die Runtime festlegt (z. B. die Art der Garbage Collection).</span><span class="sxs-lookup"><span data-stu-id="ecd7d-113">A *.runtimeconfig.json* file that specifies the shared runtime that the application expects, as well as other configuration options for the runtime (for example, garbage collection type).</span></span>
- <span data-ttu-id="ecd7d-114">Die Abhängigkeiten der Anwendung, die aus dem NuGet-Cache in den Ausgabeordner kopiert werden.</span><span class="sxs-lookup"><span data-stu-id="ecd7d-114">The application's dependencies, which are copied from the NuGet cache into the output folder.</span></span>

<span data-ttu-id="ecd7d-115">Die Ausgabe des Befehls `dotnet publish` steht für die Bereitstellung zur Ausführung auf einem Hostsystem bereit (z.B. ein Server, Computer, Mac oder Laptop).</span><span class="sxs-lookup"><span data-stu-id="ecd7d-115">The `dotnet publish` command's output is ready for deployment to a hosting system (for example, a server, PC, Mac, laptop) for execution.</span></span> <span data-ttu-id="ecd7d-116">Es ist die einzige offiziell unterstützte Methode zum Vorbereiten der Anwendung für die Bereitstellung.</span><span class="sxs-lookup"><span data-stu-id="ecd7d-116">It's the only officially supported way to prepare the application for deployment.</span></span> <span data-ttu-id="ecd7d-117">Je nach Art der Bereitstellung, die im Projekt angegeben ist, hat das Hostsystem die freigegebene .NET Core-Laufzeit installiert oder nicht.</span><span class="sxs-lookup"><span data-stu-id="ecd7d-117">Depending on the type of deployment that the project specifies, the hosting system may or may not have the .NET Core shared runtime installed on it.</span></span> <span data-ttu-id="ecd7d-118">Weitere Informationen finden Sie unter [Veröffentlichen von .NET Core-Apps mit der .NET Core-CLI](../deploying/deploy-with-cli.md).</span><span class="sxs-lookup"><span data-stu-id="ecd7d-118">For more information, see [Publish .NET Core apps with the .NET Core CLI](../deploying/deploy-with-cli.md).</span></span>

### <a name="implicit-restore"></a><span data-ttu-id="ecd7d-119">Implizite Wiederherstellung</span><span class="sxs-lookup"><span data-stu-id="ecd7d-119">Implicit restore</span></span>

[!INCLUDE[dotnet restore note](~/includes/dotnet-restore-note.md)]

### <a name="msbuild"></a><span data-ttu-id="ecd7d-120">MSBuild</span><span class="sxs-lookup"><span data-stu-id="ecd7d-120">MSBuild</span></span>

<span data-ttu-id="ecd7d-121">Der Befehl `dotnet publish` ruft MSBuild auf, welches das `Publish`-Ziel aufruft.</span><span class="sxs-lookup"><span data-stu-id="ecd7d-121">The `dotnet publish` command calls MSBuild, which invokes the `Publish` target.</span></span> <span data-ttu-id="ecd7d-122">Alle Parameter, die an `dotnet publish` übergeben werden, werden an MSBuild übergeben.</span><span class="sxs-lookup"><span data-stu-id="ecd7d-122">Any parameters passed to `dotnet publish` are passed to MSBuild.</span></span> <span data-ttu-id="ecd7d-123">Die Parameter `-c` und `-o` verweisen auf die MSBuild-Eigenschaften `Configuration` bzw. `PublishDir`.</span><span class="sxs-lookup"><span data-stu-id="ecd7d-123">The `-c` and `-o` parameters map to MSBuild's `Configuration` and `PublishDir` properties, respectively.</span></span>

<span data-ttu-id="ecd7d-124">Der `dotnet publish`-Befehl akzeptiert MSBuild-Optionen, z. B. `-p` zum Festlegen von Eigenschaften oder `-l` zum Definieren eines Protokolls.</span><span class="sxs-lookup"><span data-stu-id="ecd7d-124">The `dotnet publish` command accepts MSBuild options, such as `-p` for setting properties and `-l` to define a logger.</span></span> <span data-ttu-id="ecd7d-125">Beispielsweise können Sie eine MSBuild-Eigenschaft mit dem folgenden Format festlegen: `-p:<NAME>=<VALUE>`.</span><span class="sxs-lookup"><span data-stu-id="ecd7d-125">For example, you can set an MSBuild property by using the format: `-p:<NAME>=<VALUE>`.</span></span>

<span data-ttu-id="ecd7d-126">Sie können auch auf die Veröffentlichung bezogene Eigenschaften festlegen, indem Sie auf eine *PUBXML*-Datei verweisen (seit dem .NET Core 3.1 SDK verfügbar).</span><span class="sxs-lookup"><span data-stu-id="ecd7d-126">You can also set publish-related properties by referring to a *.pubxml* file (available since .NET Core 3.1 SDK).</span></span> <span data-ttu-id="ecd7d-127">Beispiel:</span><span class="sxs-lookup"><span data-stu-id="ecd7d-127">For example:</span></span>

```dotnetcli
dotnet publish -p:PublishProfile=FolderProfile
```

<span data-ttu-id="ecd7d-128">Im vorherigen Beispiel wird die Datei *FolderProfile.pubxml* verwendet, die sich im Ordner *\<project_folder>/Properties/PublishProfiles* befindet.</span><span class="sxs-lookup"><span data-stu-id="ecd7d-128">The preceding example uses the *FolderProfile.pubxml* file that is found in the *\<project_folder>/Properties/PublishProfiles* folder.</span></span> <span data-ttu-id="ecd7d-129">Wenn Sie beim Festlegen der `PublishProfile`-Eigenschaft einen Pfad und eine Dateierweiterung angeben, werden diese ignoriert.</span><span class="sxs-lookup"><span data-stu-id="ecd7d-129">If you specify a path and file extension when setting the `PublishProfile` property, they are ignored.</span></span> <span data-ttu-id="ecd7d-130">MSBuild sucht standardmäßig im Ordner *Properties/PublishProfiles* und übernimmt die *PUBXML*-Dateierweiterung.</span><span class="sxs-lookup"><span data-stu-id="ecd7d-130">MSBuild by default looks in the *Properties/PublishProfiles* folder and assumes the *pubxml* file extension.</span></span> <span data-ttu-id="ecd7d-131">Um den Pfad und den Dateinamen einschließlich der Erweiterung anzugeben, legen Sie die `PublishProfileFullPath`-Eigenschaft anstelle der `PublishProfile`-Eigenschaft fest.</span><span class="sxs-lookup"><span data-stu-id="ecd7d-131">To specify the path and filename including extension, set the `PublishProfileFullPath` property instead of the `PublishProfile` property.</span></span>

<span data-ttu-id="ecd7d-132">Weitere Informationen finden Sie in den folgenden Ressourcen:</span><span class="sxs-lookup"><span data-stu-id="ecd7d-132">For more information, see the following resources:</span></span>

- [<span data-ttu-id="ecd7d-133">MSBuild-Befehlszeilenreferenz</span><span class="sxs-lookup"><span data-stu-id="ecd7d-133">MSBuild command-line reference</span></span>](/visualstudio/msbuild/msbuild-command-line-reference)
- [<span data-ttu-id="ecd7d-134">Visual Studio-Veröffentlichungsprofile (PUBXML) für die Bereitstellung von ASP.NET Core-Apps</span><span class="sxs-lookup"><span data-stu-id="ecd7d-134">Visual Studio publish profiles (.pubxml) for ASP.NET Core app deployment</span></span>](/aspnet/core/host-and-deploy/visual-studio-publish-profiles)
- [<span data-ttu-id="ecd7d-135">dotnet msbuild</span><span class="sxs-lookup"><span data-stu-id="ecd7d-135">dotnet msbuild</span></span>](dotnet-msbuild.md)

## <a name="arguments"></a><span data-ttu-id="ecd7d-136">Argumente</span><span class="sxs-lookup"><span data-stu-id="ecd7d-136">Arguments</span></span>

- **`PROJECT|SOLUTION`**

  <span data-ttu-id="ecd7d-137">Das Projekt bzw. die Projektmappe, die veröffentlicht werden soll.</span><span class="sxs-lookup"><span data-stu-id="ecd7d-137">The project or solution to publish.</span></span>
  
  * <span data-ttu-id="ecd7d-138">`PROJECT` ist der Pfad und Dateiname einer [C#](csproj.md)-, F#- oder Visual Basic-Projektdatei, oder der Pfad zu einem Verzeichnis, das eine C#-, F#- oder Visual Basic-Projektdatei enthält.</span><span class="sxs-lookup"><span data-stu-id="ecd7d-138">`PROJECT` is the path and filename of a [C#](csproj.md), F#, or Visual Basic project file, or the path to a directory that contains a C#, F#, or Visual Basic project file.</span></span> <span data-ttu-id="ecd7d-139">Wenn das Verzeichnis nicht angegeben wird, wird standardmäßig das aktuelle Verzeichnis verwendet.</span><span class="sxs-lookup"><span data-stu-id="ecd7d-139">If the directory is not specified, it defaults to the current directory.</span></span>

  * <span data-ttu-id="ecd7d-140">`SOLUTION` ist der Pfad und Dateiname einer Projektmappendatei (mit der Erweiterung *.sln*), oder der Pfad zu einem Verzeichnis, das eine Projektmappendatei enthält.</span><span class="sxs-lookup"><span data-stu-id="ecd7d-140">`SOLUTION` is the path and filename of a solution file (*.sln* extension), or the path to a directory that contains a solution file.</span></span> <span data-ttu-id="ecd7d-141">Wenn das Verzeichnis nicht angegeben wird, wird standardmäßig das aktuelle Verzeichnis verwendet.</span><span class="sxs-lookup"><span data-stu-id="ecd7d-141">If the directory is not specified, it defaults to the current directory.</span></span> <span data-ttu-id="ecd7d-142">Verfügbar seit .NET Core 3.0 SDK.</span><span class="sxs-lookup"><span data-stu-id="ecd7d-142">Available since .NET Core 3.0 SDK.</span></span>

## <a name="options"></a><span data-ttu-id="ecd7d-143">Optionen</span><span class="sxs-lookup"><span data-stu-id="ecd7d-143">Options</span></span>

- **`-c|--configuration <CONFIGURATION>`**

  <span data-ttu-id="ecd7d-144">Legt die Buildkonfiguration fest.</span><span class="sxs-lookup"><span data-stu-id="ecd7d-144">Defines the build configuration.</span></span> <span data-ttu-id="ecd7d-145">Der Standardwert für die meisten Projekte ist `Debug`, aber Sie können die Buildkonfigurationseinstellungen in Ihrem Projekt überschreiben.</span><span class="sxs-lookup"><span data-stu-id="ecd7d-145">The default for most projects is `Debug`, but you can override the build configuration settings in your project.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="ecd7d-146">Veröffentlicht die Anwendung für das angegebene [Zielframework](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="ecd7d-146">Publishes the application for the specified [target framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="ecd7d-147">Sie müssen das Zielframework in der Projektdatei angeben.</span><span class="sxs-lookup"><span data-stu-id="ecd7d-147">You must specify the target framework in the project file.</span></span>

- **`--force`**

  <span data-ttu-id="ecd7d-148">Erzwingt das Auflösen aller Abhängigkeiten, auch wenn die letzte Wiederherstellung erfolgreich war.</span><span class="sxs-lookup"><span data-stu-id="ecd7d-148">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="ecd7d-149">Dieses Flag anzugeben, entspricht dem Löschen der Datei *project.assets.json*.</span><span class="sxs-lookup"><span data-stu-id="ecd7d-149">Specifying this flag is the same as deleting the *project.assets.json* file.</span></span>

- **`-h|--help`**

  <span data-ttu-id="ecd7d-150">Druckt eine kurze Hilfe für den Befehl.</span><span class="sxs-lookup"><span data-stu-id="ecd7d-150">Prints out a short help for the command.</span></span>

- **`--interactive`**

  <span data-ttu-id="ecd7d-151">Ermöglicht dem Befehl, anzuhalten und auf Benutzereingaben oder Aktionen zu warten.</span><span class="sxs-lookup"><span data-stu-id="ecd7d-151">Allows the command to stop and wait for user input or action.</span></span> <span data-ttu-id="ecd7d-152">Beispielsweise, um die Authentifizierung abzuschließen.</span><span class="sxs-lookup"><span data-stu-id="ecd7d-152">For example, to complete authentication.</span></span> <span data-ttu-id="ecd7d-153">Verfügbar seit .NET Core 3.0 SDK.</span><span class="sxs-lookup"><span data-stu-id="ecd7d-153">Available since .NET Core 3.0 SDK.</span></span>

- **`--manifest <PATH_TO_MANIFEST_FILE>`**

  <span data-ttu-id="ecd7d-154">Gibt mindestens ein [Zielmanifest](../deploying/runtime-store.md) an, das verwendet wird, um die Menge an mit der App veröffentlichten Paketen zu senken.</span><span class="sxs-lookup"><span data-stu-id="ecd7d-154">Specifies one or several [target manifests](../deploying/runtime-store.md) to use to trim the set of packages published with the app.</span></span> <span data-ttu-id="ecd7d-155">Die Manifestdatei ist Teil der Ausgabe des [`dotnet store`-Befehls](dotnet-store.md).</span><span class="sxs-lookup"><span data-stu-id="ecd7d-155">The manifest file is part of the output of the [`dotnet store` command](dotnet-store.md).</span></span> <span data-ttu-id="ecd7d-156">Um mehrere Manifeste anzugeben, fügen Sie die `--manifest`-Option für jedes Manifest hinzu.</span><span class="sxs-lookup"><span data-stu-id="ecd7d-156">To specify multiple manifests, add a `--manifest` option for each manifest.</span></span>

- **`--no-build`**

  <span data-ttu-id="ecd7d-157">Erstellt das Projekt nicht vor der Veröffentlichung.</span><span class="sxs-lookup"><span data-stu-id="ecd7d-157">Doesn't build the project before publishing.</span></span> <span data-ttu-id="ecd7d-158">Zudem wird das Flag `--no-restore` implizit festgelegt.</span><span class="sxs-lookup"><span data-stu-id="ecd7d-158">It also implicitly sets the `--no-restore` flag.</span></span>

- **`--no-dependencies`**

  <span data-ttu-id="ecd7d-159">Ignoriert Verweise zwischen Projekten und stellt nur das zum Erstellen angegebene Stammprojekt wieder her.</span><span class="sxs-lookup"><span data-stu-id="ecd7d-159">Ignores project-to-project references and only restores the root project.</span></span>

- **`--nologo`**

  <span data-ttu-id="ecd7d-160">Unterdrückt die Anzeige von Startbanner und Copyrightmeldung.</span><span class="sxs-lookup"><span data-stu-id="ecd7d-160">Doesn't display the startup banner or the copyright message.</span></span> <span data-ttu-id="ecd7d-161">Verfügbar seit .NET Core 3.0 SDK.</span><span class="sxs-lookup"><span data-stu-id="ecd7d-161">Available since .NET Core 3.0 SDK.</span></span>

- **`--no-restore`**

  <span data-ttu-id="ecd7d-162">Führt keine implizite Wiederherstellung aus, wenn der Befehl ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="ecd7d-162">Doesn't execute an implicit restore when running the command.</span></span>

- **`-o|--output <OUTPUT_DIRECTORY>`**

  <span data-ttu-id="ecd7d-163">Gibt den Pfad für das Ausgabeverzeichnis an.</span><span class="sxs-lookup"><span data-stu-id="ecd7d-163">Specifies the path for the output directory.</span></span>
  
  <span data-ttu-id="ecd7d-164">Wenn diese Option nicht angegeben wird, wird für frameworkabhängige ausführbare Dateien und plattformübergreifende Binärdateien standardmäßig *[Projektdateiordner]/bin/[Konfiguration]/[Framework]/publish/* verwendet.</span><span class="sxs-lookup"><span data-stu-id="ecd7d-164">If not specified, it defaults to *[project_file_folder]/bin/[configuration]/[framework]/publish/* for a framework-dependent executable and cross-platform binaries.</span></span> <span data-ttu-id="ecd7d-165">Für eigenständige ausführbare Dateien wird standardmäßig *[Projektdateiordner]./bin/[Konfiguration]/[Framework]/[Runtime]/publish/* verwendet.</span><span class="sxs-lookup"><span data-stu-id="ecd7d-165">It defaults to *[project_file_folder]/bin/[configuration]/[framework]/[runtime]/publish/* for a self-contained executable.</span></span>

  <span data-ttu-id="ecd7d-166">In einem Webprojekt führen aufeinanderfolgende `dotnet publish`-Befehle zu geschachtelten Ausgabeordnern, wenn sich der Ausgabeordner im Projektordner befindet.</span><span class="sxs-lookup"><span data-stu-id="ecd7d-166">In a web project, if the output folder is in the project folder, successive `dotnet publish` commands result in nested output folders.</span></span> <span data-ttu-id="ecd7d-167">Wenn der Projektordner beispielsweise *MeinProjekt* lautet und als Ausgabeordner *MeinProjekt/publish* festgelegt ist, werden bei zweimaliger Ausführung von `dotnet publish` die Inhaltsdateien (beispielsweise die *CONFIG*- und *JSON*-Dateien) der zweiten Ausführung in *MeinProjekt/publish/publish* platziert.</span><span class="sxs-lookup"><span data-stu-id="ecd7d-167">For example, if the project folder is *myproject*, and the publish output folder is *myproject/publish*, and you run `dotnet publish` twice, the second run puts content files such as *.config* and *.json* files in *myproject/publish/publish*.</span></span> <span data-ttu-id="ecd7d-168">Um eine Schachtelung der Veröffentlichungsordner zu vermeiden, geben Sie einen Ordner für die Veröffentlichung an, der sich nicht **direkt** unter dem Projektordner befindet. Alternativ können Sie den Veröffentlichungsordner aus dem Projekt ausschließen.</span><span class="sxs-lookup"><span data-stu-id="ecd7d-168">To avoid nesting publish folders, specify a publish folder that is not **directly** under the project folder, or exclude the publish folder from the project.</span></span> <span data-ttu-id="ecd7d-169">Um einen Veröffentlichungsordner namens *publishoutput* auszuschließen, fügen Sie das folgende Element einem `PropertyGroup`-Element in der *CSPROJ*-Datei hinzu:</span><span class="sxs-lookup"><span data-stu-id="ecd7d-169">To exclude a publish folder named *publishoutput*, add the following element to a `PropertyGroup` element in the *.csproj* file:</span></span>

  ```xml
  <DefaultItemExcludes>$(DefaultItemExcludes);publishoutput**</DefaultItemExcludes>
  ```

  - <span data-ttu-id="ecd7d-170">.NET Core 3. x SDK und höher</span><span class="sxs-lookup"><span data-stu-id="ecd7d-170">.NET Core 3.x SDK and later</span></span>
  
    <span data-ttu-id="ecd7d-171">Wenn beim Veröffentlichen eines Projekts ein relativer Pfad angegeben wird, ist das generierte Ausgabeverzeichnis relativ zum aktuellen Arbeitsverzeichnis statt zum Speicherort der Projektdatei.</span><span class="sxs-lookup"><span data-stu-id="ecd7d-171">If a relative path is specified when publishing a project, the output directory generated is relative to the current working directory, not to the project file location.</span></span>

    <span data-ttu-id="ecd7d-172">Wenn beim Veröffentlichen einer Projektmappe ein relativer Pfad angegeben wird, werden alle Ausgaben für sämtliche Projekte im angegebenen Ordner relativ zum aktuellen Arbeitsverzeichnis gespeichert.</span><span class="sxs-lookup"><span data-stu-id="ecd7d-172">If a relative path is specified when publishing a solution, all output for all projects goes into the specified folder relative to the current working directory.</span></span> <span data-ttu-id="ecd7d-173">Um die Veröffentlichungsausgabe in eigenen Ordnern für jedes Projekt zu speichern, geben Sie einen relativen Pfad an, indem Sie die MSBuild-`PublishDir`-Eigenschaft anstelle der `--output`-Option verwenden.</span><span class="sxs-lookup"><span data-stu-id="ecd7d-173">To make publish output go to separate folders for each project, specify a relative path by using the msbuild `PublishDir` property instead of the `--output` option.</span></span> <span data-ttu-id="ecd7d-174">Beispielsweise wird mit `dotnet publish -p:PublishDir=.\publish` die Veröffentlichungsausgabe für jedes Projekt an den Ordner `publish` unter dem Ordner gesendet, der die Projektdatei enthält.</span><span class="sxs-lookup"><span data-stu-id="ecd7d-174">For example, `dotnet publish -p:PublishDir=.\publish` sends publish output for each project to a `publish` folder under the folder that contains the project file.</span></span>

  - <span data-ttu-id="ecd7d-175">.NET Core 2.x SDK</span><span class="sxs-lookup"><span data-stu-id="ecd7d-175">.NET Core 2.x SDK</span></span>
  
    <span data-ttu-id="ecd7d-176">Wenn beim Veröffentlichen eines Projekts ein relativer Pfad angegeben wird, ist das generierte Ausgabeverzeichnis relativ zum Speicherort der Projektdatei statt zum aktuellen Arbeitsverzeichnis.</span><span class="sxs-lookup"><span data-stu-id="ecd7d-176">If a relative path is specified when publishing a project, the output directory generated is relative to the project file location, not to the current working directory.</span></span>

    <span data-ttu-id="ecd7d-177">Wenn beim Veröffentlichen einer Projektmappe ein relativer Pfad angegeben wird, wird die Ausgabe jedes Projekts in einem eigenen Ordner relativ zum Speicherort der Projektdatei gespeichert.</span><span class="sxs-lookup"><span data-stu-id="ecd7d-177">If a relative path is specified when publishing a solution, each project's output goes into a separate folder relative to the project file location.</span></span> <span data-ttu-id="ecd7d-178">Wenn beim Veröffentlichen einer Projektmappe ein absoluter Pfad angegeben wird, werden alle Veröffentlichungsausgaben für alle Projekte im angegebenen Ordner gespeichert.</span><span class="sxs-lookup"><span data-stu-id="ecd7d-178">If an absolute path is specified when publishing a solution, all publish output for all projects goes into the specified folder.</span></span>

- **`-p:PublishReadyToRun=true`**

  <span data-ttu-id="ecd7d-179">Kompiliert Anwendungsassemblys im R2R-Format (ReadyToRun).</span><span class="sxs-lookup"><span data-stu-id="ecd7d-179">Compiles application assemblies as ReadyToRun (R2R) format.</span></span> <span data-ttu-id="ecd7d-180">R2R ist eine Form der AOT-Kompilierung (Ahead-Of-Time).</span><span class="sxs-lookup"><span data-stu-id="ecd7d-180">R2R is a form of ahead-of-time (AOT) compilation.</span></span> <span data-ttu-id="ecd7d-181">Weitere Informationen finden Sie unter [ReadyToRun-Images](../deploying/ready-to-run.md).</span><span class="sxs-lookup"><span data-stu-id="ecd7d-181">For more information, see [ReadyToRun images](../deploying/ready-to-run.md).</span></span> <span data-ttu-id="ecd7d-182">Verfügbar seit .NET Core 3.0 SDK.</span><span class="sxs-lookup"><span data-stu-id="ecd7d-182">Available since .NET Core 3.0 SDK.</span></span>

  <span data-ttu-id="ecd7d-183">Es wird empfohlen, diese Option nicht auf der Befehlszeile, sondern in einem Veröffentlichungsprofil anzugeben.</span><span class="sxs-lookup"><span data-stu-id="ecd7d-183">We recommend that you specify this option in a publish profile rather than on the command line.</span></span> <span data-ttu-id="ecd7d-184">Weitere Informationen finden Sie unter [MSBuild](#msbuild).</span><span class="sxs-lookup"><span data-stu-id="ecd7d-184">For more information, see [MSBuild](#msbuild).</span></span>

- **`-p:PublishSingleFile=true`**

  <span data-ttu-id="ecd7d-185">Packt die App in einer plattformspezifischen ausführbaren Einzeldatei.</span><span class="sxs-lookup"><span data-stu-id="ecd7d-185">Packages the app into a platform-specific single-file executable.</span></span> <span data-ttu-id="ecd7d-186">Die ausführbare Datei ist selbstextrahierend und enthält alle Abhängigkeiten (einschließlich der nativen), die zum Ausführen der App erforderlich sind.</span><span class="sxs-lookup"><span data-stu-id="ecd7d-186">The executable is self-extracting and contains all dependencies (including native) that are required to run the app.</span></span> <span data-ttu-id="ecd7d-187">Beim ersten Ausführen der App wird die Anwendung in ein Verzeichnis extrahiert, das auf dem Namen und dem Buildbezeichner der App basiert.</span><span class="sxs-lookup"><span data-stu-id="ecd7d-187">When the app is first run, the application is extracted to a directory based on the app name and build identifier.</span></span> <span data-ttu-id="ecd7d-188">Der Start ist beim erneuten Ausführen der App schneller.</span><span class="sxs-lookup"><span data-stu-id="ecd7d-188">Startup is faster when the application is run again.</span></span> <span data-ttu-id="ecd7d-189">Die Anwendung muss sich nicht selbst ein zweites Mal extrahieren, sofern keine neue Version verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="ecd7d-189">The application doesn't need to extract itself a second time unless a new version is used.</span></span> <span data-ttu-id="ecd7d-190">Verfügbar seit .NET Core 3.0 SDK.</span><span class="sxs-lookup"><span data-stu-id="ecd7d-190">Available since .NET Core 3.0 SDK.</span></span>

  <span data-ttu-id="ecd7d-191">Weitere Informationen zum Veröffentlichen einzelner Dateien finden Sie im [Einzeldatei-Bundler-Entwurfsdokument](https://github.com/dotnet/designs/blob/master/accepted/2020/single-file/design.md).</span><span class="sxs-lookup"><span data-stu-id="ecd7d-191">For more information about single-file publishing, see the [single-file bundler design document](https://github.com/dotnet/designs/blob/master/accepted/2020/single-file/design.md).</span></span>

  <span data-ttu-id="ecd7d-192">Es wird empfohlen, diese Option nicht auf der Befehlszeile, sondern in einem Veröffentlichungsprofil anzugeben.</span><span class="sxs-lookup"><span data-stu-id="ecd7d-192">We recommend that you specify this option in a publish profile rather than on the command line.</span></span> <span data-ttu-id="ecd7d-193">Weitere Informationen finden Sie unter [MSBuild](#msbuild).</span><span class="sxs-lookup"><span data-stu-id="ecd7d-193">For more information, see [MSBuild](#msbuild).</span></span>

- **`-p:PublishTrimmed=true`**

  <span data-ttu-id="ecd7d-194">Kürzt nicht verwendete Bibliotheken, um die Bereitstellungsgröße einer App zu verringern, wenn diese als selbstextrahierende ausführbare Datei veröffentlicht wird.</span><span class="sxs-lookup"><span data-stu-id="ecd7d-194">Trims unused libraries to reduce the deployment size of an app when publishing a self-contained executable.</span></span> <span data-ttu-id="ecd7d-195">Weitere Informationen finden Sie unter [Kürzen eigenständiger Bereitstellungen und ausführbarer Dateien](../deploying/trim-self-contained.md).</span><span class="sxs-lookup"><span data-stu-id="ecd7d-195">For more information, see [Trim self-contained deployments and executables](../deploying/trim-self-contained.md).</span></span> <span data-ttu-id="ecd7d-196">Diese Option ist seit dem .NET Core SDK 3.0 als Previewfunktion verfügbar.</span><span class="sxs-lookup"><span data-stu-id="ecd7d-196">Available since .NET Core 3.0 SDK as a preview feature.</span></span>

  <span data-ttu-id="ecd7d-197">Es wird empfohlen, diese Option nicht auf der Befehlszeile, sondern in einem Veröffentlichungsprofil anzugeben.</span><span class="sxs-lookup"><span data-stu-id="ecd7d-197">We recommend that you specify this option in a publish profile rather than on the command line.</span></span> <span data-ttu-id="ecd7d-198">Weitere Informationen finden Sie unter [MSBuild](#msbuild).</span><span class="sxs-lookup"><span data-stu-id="ecd7d-198">For more information, see [MSBuild](#msbuild).</span></span>

- **`--self-contained [true|false]`**

  <span data-ttu-id="ecd7d-199">Veröffentlicht die .NET Core-Runtime mit Ihrer Anwendung, sodass die Runtime nicht auf dem Zielcomputer installiert werden muss.</span><span class="sxs-lookup"><span data-stu-id="ecd7d-199">Publishes the .NET Core runtime with your application so the runtime doesn't need to be installed on the target machine.</span></span> <span data-ttu-id="ecd7d-200">Der Standardwert ist `true`, wenn ein Laufzeitbezeichner angegeben wird und das Projekt ein ausführbares Projekt (kein Bibliotheksprojekt) ist.</span><span class="sxs-lookup"><span data-stu-id="ecd7d-200">Default is `true` if a runtime identifier is specified and the project is an executable project (not a library project).</span></span> <span data-ttu-id="ecd7d-201">Weitere Informationen finden Sie unter [Veröffentlichen von .NET Core-Anwendungen](../deploying/index.md) und [Veröffentlichen von .NET Core-Apps mit der .NET Core-CLI](../deploying/deploy-with-cli.md).</span><span class="sxs-lookup"><span data-stu-id="ecd7d-201">For more information, see [.NET Core application publishing](../deploying/index.md) and [Publish .NET Core apps with the .NET Core CLI](../deploying/deploy-with-cli.md).</span></span>

  <span data-ttu-id="ecd7d-202">Wenn diese Option verwendet wird, ohne `true` oder `false` anzugeben, ist der Standardwert `true`.</span><span class="sxs-lookup"><span data-stu-id="ecd7d-202">If this option is used without specifying `true` or `false`, the default is `true`.</span></span> <span data-ttu-id="ecd7d-203">Fügen Sie in diesem Fall das Projektmappen- oder Projektargument nicht unmittelbar nach `--self-contained` ein, da an dieser Position `true` oder `false` erwartet wird.</span><span class="sxs-lookup"><span data-stu-id="ecd7d-203">In that case, don't put the solution or project argument immediately after `--self-contained`, because `true` or `false` is expected in that position.</span></span>

- **`--no-self-contained`**

  <span data-ttu-id="ecd7d-204">Entspricht `--self-contained false`.</span><span class="sxs-lookup"><span data-stu-id="ecd7d-204">Equivalent to `--self-contained false`.</span></span> <span data-ttu-id="ecd7d-205">Verfügbar seit .NET Core 3.0 SDK.</span><span class="sxs-lookup"><span data-stu-id="ecd7d-205">Available since .NET Core 3.0 SDK.</span></span>

- **`-r|--runtime <RUNTIME_IDENTIFIER>`**

  <span data-ttu-id="ecd7d-206">Veröffentlicht die Anwendung für eine bestimmte Laufzeit.</span><span class="sxs-lookup"><span data-stu-id="ecd7d-206">Publishes the application for a given runtime.</span></span> <span data-ttu-id="ecd7d-207">Eine Liste der Runtime-IDs (RIDs) finden Sie unter [RID-Katalog](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="ecd7d-207">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span> <span data-ttu-id="ecd7d-208">Weitere Informationen finden Sie unter [Veröffentlichen von .NET Core-Anwendungen](../deploying/index.md) und [Veröffentlichen von .NET Core-Apps mit der .NET Core-CLI](../deploying/deploy-with-cli.md).</span><span class="sxs-lookup"><span data-stu-id="ecd7d-208">For more information, see [.NET Core application publishing](../deploying/index.md) and [Publish .NET Core apps with the .NET Core CLI](../deploying/deploy-with-cli.md).</span></span>

- **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="ecd7d-209">Legt den Ausführlichkeitsgrad für den Befehl fest.</span><span class="sxs-lookup"><span data-stu-id="ecd7d-209">Sets the verbosity level of the command.</span></span> <span data-ttu-id="ecd7d-210">Zulässige Werte sind `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` und `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="ecd7d-210">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="ecd7d-211">Der Standardwert ist `minimal`sein.</span><span class="sxs-lookup"><span data-stu-id="ecd7d-211">Default value is `minimal`.</span></span>

- **`--version-suffix <VERSION_SUFFIX>`**

  <span data-ttu-id="ecd7d-212">Definiert das Versionssuffix zum Ersetzen des Sternchens (`*`) im Versionsfeld der Projektdatei.</span><span class="sxs-lookup"><span data-stu-id="ecd7d-212">Defines the version suffix to replace the asterisk (`*`) in the version field of the project file.</span></span>

## <a name="examples"></a><span data-ttu-id="ecd7d-213">Beispiele</span><span class="sxs-lookup"><span data-stu-id="ecd7d-213">Examples</span></span>

- <span data-ttu-id="ecd7d-214">Erstellen Sie eine [frameworkabhängige plattformübergreifende Binärdatei](../deploying/index.md#produce-a-cross-platform-binary) für das Projekt im aktuellen Verzeichnis:</span><span class="sxs-lookup"><span data-stu-id="ecd7d-214">Create a [framework-dependent cross-platform binary](../deploying/index.md#produce-a-cross-platform-binary) for the project in the current directory:</span></span>

  ```dotnetcli
  dotnet publish
  ```

  <span data-ttu-id="ecd7d-215">Ab dem .NET Core SDK 3.0 wird mit diesem Beispielbefehl eine [frameworkabhängige ausführbare Datei](../deploying/index.md#publish-framework-dependent) für die aktuelle Plattform erstellt.</span><span class="sxs-lookup"><span data-stu-id="ecd7d-215">Starting with .NET Core 3.0 SDK, this example also creates a [framework-dependent executable](../deploying/index.md#publish-framework-dependent) for the current platform.</span></span>

- <span data-ttu-id="ecd7d-216">Erstellen Sie für das Projekt im aktuellen Verzeichnis eine [eigenständige ausführbare Datei](../deploying/index.md#publish-self-contained) für eine spezifische Runtime:</span><span class="sxs-lookup"><span data-stu-id="ecd7d-216">Create a [self-contained executable](../deploying/index.md#publish-self-contained) for the project in the current directory, for a specific runtime:</span></span>

  ```dotnetcli
  dotnet publish --runtime osx.10.11-x64
  ```

  <span data-ttu-id="ecd7d-217">Die RID muss in der Projektdatei enthalten sein.</span><span class="sxs-lookup"><span data-stu-id="ecd7d-217">The RID must be in the project file.</span></span>

- <span data-ttu-id="ecd7d-218">Erstellen Sie für das Projekt im aktuellen Verzeichnis eine [frameworkabhängige ausführbare Datei](../deploying/index.md#publish-framework-dependent) für eine spezifische Plattform:</span><span class="sxs-lookup"><span data-stu-id="ecd7d-218">Create a [framework-dependent executable](../deploying/index.md#publish-framework-dependent) for the project in the current directory, for a specific platform:</span></span>

  ```dotnetcli
  dotnet publish --runtime osx.10.11-x64 --self-contained false
  ```

  <span data-ttu-id="ecd7d-219">Die RID muss in der Projektdatei enthalten sein.</span><span class="sxs-lookup"><span data-stu-id="ecd7d-219">The RID must be in the project file.</span></span> <span data-ttu-id="ecd7d-220">Dieses Beispiel gilt für .NET Core 3.0 SDK und höher.</span><span class="sxs-lookup"><span data-stu-id="ecd7d-220">This example applies to .NET Core 3.0 SDK and later versions.</span></span>

- <span data-ttu-id="ecd7d-221">Veröffentlichen Sie das Projekt im aktuellen Verzeichnis für eine spezifische Runtime und ein spezifisches Zielframework:</span><span class="sxs-lookup"><span data-stu-id="ecd7d-221">Publish the project in the current directory, for a specific runtime and target framework:</span></span>

  ```dotnetcli
  dotnet publish --framework netcoreapp3.1 --runtime osx.10.11-x64
  ```

- <span data-ttu-id="ecd7d-222">Veröffentlichen Sie die angegebene Projektdatei:</span><span class="sxs-lookup"><span data-stu-id="ecd7d-222">Publish the specified project file:</span></span>

  ```dotnetcli
  dotnet publish ~/projects/app1/app1.csproj
  ```

- <span data-ttu-id="ecd7d-223">Veröffentlichen sie die aktuelle Anwendung, aber fügen Sie während der Wiederherstellung keine Projekt-zu-Projekt-Verweise hinzu, sondern nur das Stammprojekt:</span><span class="sxs-lookup"><span data-stu-id="ecd7d-223">Publish the current application but don't restore project-to-project (P2P) references, just the root project during the restore operation:</span></span>

  ```dotnetcli
  dotnet publish --no-dependencies
  ```

## <a name="see-also"></a><span data-ttu-id="ecd7d-224">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="ecd7d-224">See also</span></span>

- [<span data-ttu-id="ecd7d-225">Übersicht über die .NET Core-Anwendungsveröffentlichung</span><span class="sxs-lookup"><span data-stu-id="ecd7d-225">.NET Core application publishing overview</span></span>](../deploying/index.md)
- [<span data-ttu-id="ecd7d-226">Veröffentlichen von .NET Core-Apps mit der .NET Core-CLI</span><span class="sxs-lookup"><span data-stu-id="ecd7d-226">Publish .NET Core apps with the .NET Core CLI</span></span>](../deploying/deploy-with-cli.md)
- [<span data-ttu-id="ecd7d-227">Zielframeworks</span><span class="sxs-lookup"><span data-stu-id="ecd7d-227">Target frameworks</span></span>](../../standard/frameworks.md)
- [<span data-ttu-id="ecd7d-228">Runtime-ID-Katalog (RID)</span><span class="sxs-lookup"><span data-stu-id="ecd7d-228">Runtime Identifier (RID) catalog</span></span>](../rid-catalog.md)
- [<span data-ttu-id="ecd7d-229">Verwenden der macOS Catalina-Notarisierung</span><span class="sxs-lookup"><span data-stu-id="ecd7d-229">Working with macOS Catalina Notarization</span></span>](../install/macos-notarization-issues.md)
- [<span data-ttu-id="ecd7d-230">Verzeichnisstruktur einer veröffentlichten Anwendung</span><span class="sxs-lookup"><span data-stu-id="ecd7d-230">Directory structure of a published application</span></span>](/aspnet/core/hosting/directory-structure)
- [<span data-ttu-id="ecd7d-231">MSBuild-Befehlszeilenreferenz</span><span class="sxs-lookup"><span data-stu-id="ecd7d-231">MSBuild command-line reference</span></span>](/visualstudio/msbuild/msbuild-command-line-reference)
- [<span data-ttu-id="ecd7d-232">Visual Studio-Veröffentlichungsprofile (PUBXML) für die Bereitstellung von ASP.NET Core-Apps</span><span class="sxs-lookup"><span data-stu-id="ecd7d-232">Visual Studio publish profiles (.pubxml) for ASP.NET Core app deployment</span></span>](/aspnet/core/host-and-deploy/visual-studio-publish-profiles)
- [<span data-ttu-id="ecd7d-233">dotnet msbuild</span><span class="sxs-lookup"><span data-stu-id="ecd7d-233">dotnet msbuild</span></span>](dotnet-msbuild.md)
- [<span data-ttu-id="ecd7d-234">ILLInk.Tasks</span><span class="sxs-lookup"><span data-stu-id="ecd7d-234">ILLInk.Tasks</span></span>](../deploying/trim-self-contained.md)
