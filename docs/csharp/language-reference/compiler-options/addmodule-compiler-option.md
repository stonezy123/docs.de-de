---
description: -addmodule (C#-Compileroptionen)
title: -addmodule (C#-Compileroptionen)
ms.date: 07/20/2015
f1_keywords:
- /addmodule
helpviewer_keywords:
- /addmodule compiler option [C#]
- -addmodule compiler option [C#]
- addmodule compiler option [C#]
ms.assetid: ed604546-0dc2-4bd4-9a3e-610a8d973e58
ms.openlocfilehash: ec72fc76b3d550029b1286f64b8f86e69e721468
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/24/2020
ms.locfileid: "91150569"
---
# <a name="-addmodule-c-compiler-options"></a><span data-ttu-id="3c96f-103">-addmodule (C#-Compileroptionen)</span><span class="sxs-lookup"><span data-stu-id="3c96f-103">-addmodule (C# Compiler Options)</span></span>

<span data-ttu-id="3c96f-104">Mit dieser Option wird ein Modul hinzugefügt, das mit dem Schalter „target:mocule“ in der aktuellen Kompilierung erstellt wurde.</span><span class="sxs-lookup"><span data-stu-id="3c96f-104">This option adds a module that was created with the target:module switch to the current compilation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3c96f-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="3c96f-105">Syntax</span></span>  
  
```console  
-addmodule:file[;file2]  
```  
  
## <a name="arguments"></a><span data-ttu-id="3c96f-106">Argumente</span><span class="sxs-lookup"><span data-stu-id="3c96f-106">Arguments</span></span>  

 <span data-ttu-id="3c96f-107">`file`, `file2`</span><span class="sxs-lookup"><span data-stu-id="3c96f-107">`file`, `file2`</span></span>  
 <span data-ttu-id="3c96f-108">Eine Ausgabedatei, die Metadaten enthält.</span><span class="sxs-lookup"><span data-stu-id="3c96f-108">An output file that contains metadata.</span></span> <span data-ttu-id="3c96f-109">Die Datei kann kein Assemblymanifest enthalten.</span><span class="sxs-lookup"><span data-stu-id="3c96f-109">The file cannot contain an assembly manifest.</span></span> <span data-ttu-id="3c96f-110">Trennen Sie die Dateinamen entweder mit einem Komma oder einem Semikolon, um mehr als eine Datei zu importieren.</span><span class="sxs-lookup"><span data-stu-id="3c96f-110">To import more than one file, separate file names with either a comma or a semicolon.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3c96f-111">Bemerkungen</span><span class="sxs-lookup"><span data-stu-id="3c96f-111">Remarks</span></span>  

 <span data-ttu-id="3c96f-112">Alle Module, die mit **-addmodule** hinzugefügt werden, müssen sich zur Laufzeit im gleichen Verzeichnis wie die Ausgabedatei befinden.</span><span class="sxs-lookup"><span data-stu-id="3c96f-112">All modules added with **-addmodule** must be in the same directory as the output file at run time.</span></span> <span data-ttu-id="3c96f-113">Das bedeutet, dass Sie zur Kompilierzeit ein beliebiges Modul in einem Verzeichnis angeben können, sich das Modul aber zur Laufzeit im Anwendungsverzeichnis befinden muss.</span><span class="sxs-lookup"><span data-stu-id="3c96f-113">That is, you can specify a module in any directory at compile time but the module must be in the application directory at run time.</span></span> <span data-ttu-id="3c96f-114">Wenn sich das Modul zur Laufzeit nicht im Anwendungsverzeichnis befindet, wird eine <xref:System.TypeLoadException> ausgelöst.</span><span class="sxs-lookup"><span data-stu-id="3c96f-114">If the module is not in the application directory at run time, you will get a <xref:System.TypeLoadException>.</span></span>  
  
 <span data-ttu-id="3c96f-115">`file` kann keine Assembly enthalten.</span><span class="sxs-lookup"><span data-stu-id="3c96f-115">`file` cannot contain an assembly.</span></span> <span data-ttu-id="3c96f-116">Wenn die Ausgabedatei z.B. mit [-target:module](./target-module-compiler-option.md) erstellt wurde, können die Metadaten mit **-addmodule** importiert werden.</span><span class="sxs-lookup"><span data-stu-id="3c96f-116">For example, if the output file was created with [-target:module](./target-module-compiler-option.md), its metadata can be imported with **-addmodule**.</span></span>  
  
 <span data-ttu-id="3c96f-117">Wenn die Ausgabedatei mit einer anderen **-target**-Option als **-target:module** erstellt wurde, können die Metadaten nicht mit **-addmodule** importiert werden. Stattdessen werden sie mit [-reference](./reference-compiler-option.md) importiert.</span><span class="sxs-lookup"><span data-stu-id="3c96f-117">If the output file was created with a **-target** option other than **-target:module**, its metadata cannot be imported with **-addmodule** but can be imported with [-reference](./reference-compiler-option.md).</span></span>  
  
 <span data-ttu-id="3c96f-118">Diese Compileroption steht in Visual Studio nicht zur Verfügung, da ein Projekt nicht auf ein Modul verweisen kann.</span><span class="sxs-lookup"><span data-stu-id="3c96f-118">This compiler option is unavailable in Visual Studio; a project cannot reference a module.</span></span> <span data-ttu-id="3c96f-119">Des Weiteren kann diese Compileroption nicht programmgesteuert geändert werden.</span><span class="sxs-lookup"><span data-stu-id="3c96f-119">In addition, this compiler option cannot be changed programmatically.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3c96f-120">Beispiel</span><span class="sxs-lookup"><span data-stu-id="3c96f-120">Example</span></span>  

 <span data-ttu-id="3c96f-121">Kompilieren Sie die Quelldatei `input.cs`, und fügen Sie Metadaten aus `metad1.netmodule` und `metad2.netmodule` hinzu, um `out.exe` zu erstellen:</span><span class="sxs-lookup"><span data-stu-id="3c96f-121">Compile source file `input.cs` and add metadata from `metad1.netmodule` and `metad2.netmodule` to produce `out.exe`:</span></span>  
  
```console  
csc -addmodule:metad1.netmodule;metad2.netmodule -out:out.exe input.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="3c96f-122">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="3c96f-122">See also</span></span>

- [<span data-ttu-id="3c96f-123">C#-Compileroptionen</span><span class="sxs-lookup"><span data-stu-id="3c96f-123">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="3c96f-124">Verwalten von Projekt- und Projektmappeneigenschaften</span><span class="sxs-lookup"><span data-stu-id="3c96f-124">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
- [<span data-ttu-id="3c96f-125">Mehrfachdateiassemblys</span><span class="sxs-lookup"><span data-stu-id="3c96f-125">Multifile Assemblies</span></span>](../../../framework/app-domains/multifile-assemblies.md)
- [<span data-ttu-id="3c96f-126">How to: Erstellen einer Mehrfachdateiassembly</span><span class="sxs-lookup"><span data-stu-id="3c96f-126">How to: Build a Multifile Assembly</span></span>](../../../framework/app-domains/build-multifile-assembly.md)
