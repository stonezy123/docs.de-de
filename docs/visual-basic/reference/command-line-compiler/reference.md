---
title: -reference
ms.date: 03/13/2018
helpviewer_keywords:
- /reference compiler option [Visual Basic]
- r compiler option [Visual Basic]
- -reference compiler option [Visual Basic]
- /r compiler option [Visual Basic]
- reference compiler option [Visual Basic]
- -r compiler option [Visual Basic]
ms.assetid: 66bdfced-bbf6-43d1-a554-bc0990315737
ms.openlocfilehash: b489a164e56a5e3bdbf7e3cdf24ec330fadedf38
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/23/2020
ms.locfileid: "91097552"
---
# <a name="-reference-visual-basic"></a><span data-ttu-id="ce54d-102">-reference (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ce54d-102">-reference (Visual Basic)</span></span>

<span data-ttu-id="ce54d-103">Hiermit wird bewirkt, dass der Compiler Typinformationen in den angegebenen Assemblys des Projekts zur Verfügung stellt, das Sie aktuell kompilieren.</span><span class="sxs-lookup"><span data-stu-id="ce54d-103">Causes the compiler to make type information in the specified assemblies available to the project you are currently compiling.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ce54d-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="ce54d-104">Syntax</span></span>  
  
```console  
-reference:fileList  
```

<span data-ttu-id="ce54d-105">oder</span><span class="sxs-lookup"><span data-stu-id="ce54d-105">or</span></span>

```console
-r:fileList  
```  
  
## <a name="arguments"></a><span data-ttu-id="ce54d-106">Argumente</span><span class="sxs-lookup"><span data-stu-id="ce54d-106">Arguments</span></span>  
  
|<span data-ttu-id="ce54d-107">Begriff</span><span class="sxs-lookup"><span data-stu-id="ce54d-107">Term</span></span>|<span data-ttu-id="ce54d-108">Definition</span><span class="sxs-lookup"><span data-stu-id="ce54d-108">Definition</span></span>|  
|---|---|  
|`fileList`|<span data-ttu-id="ce54d-109">Erforderlich.</span><span class="sxs-lookup"><span data-stu-id="ce54d-109">Required.</span></span> <span data-ttu-id="ce54d-110">Durch Trennzeichen getrennte Liste von Assemblydateinamen.</span><span class="sxs-lookup"><span data-stu-id="ce54d-110">Comma-delimited list of assembly file names.</span></span> <span data-ttu-id="ce54d-111">Wenn der Dateiname ein Leerzeichen enthält, müssen Sie den Namen in Anführungszeichen einschließen.</span><span class="sxs-lookup"><span data-stu-id="ce54d-111">If the file name contains a space, enclose the name in quotation marks.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ce54d-112">Hinweise</span><span class="sxs-lookup"><span data-stu-id="ce54d-112">Remarks</span></span>  

 <span data-ttu-id="ce54d-113">Die Dateien, die Sie importieren, müssen Assemblymetadaten enthalten.</span><span class="sxs-lookup"><span data-stu-id="ce54d-113">The file(s) you import must contain assembly metadata.</span></span> <span data-ttu-id="ce54d-114">Nur öffentliche Typen sind außerhalb der Assembly sichtbar.</span><span class="sxs-lookup"><span data-stu-id="ce54d-114">Only public types are visible outside the assembly.</span></span> <span data-ttu-id="ce54d-115">Mit der Option [-addmodule](addmodule.md) werden Metadaten aus einem Modul importiert.</span><span class="sxs-lookup"><span data-stu-id="ce54d-115">The [-addmodule](addmodule.md) option imports metadata from a module.</span></span>  
  
 <span data-ttu-id="ce54d-116">Wenn Sie auf eine Assembly (Assembly A) verweisen, die selbst auf eine andere Assembly (Assembly B) verweist, müssen Sie auf Assembly B verweisen, wenn:</span><span class="sxs-lookup"><span data-stu-id="ce54d-116">If you reference an assembly (Assembly A) which itself references another assembly (Assembly B), you need to reference Assembly B if:</span></span>  
  
- <span data-ttu-id="ce54d-117">Ein Typ von Assembly A erbt von einem Typ oder implementiert eine Schnittstelle aus Assembly B.</span><span class="sxs-lookup"><span data-stu-id="ce54d-117">A type from Assembly A inherits from a type or implements an interface from Assembly B.</span></span>  
  
- <span data-ttu-id="ce54d-118">Es wird ein Feld, eine Eigenschaft, ein Ereignis oder eine Methode aufgerufen, das/die über einen Rückgabetyp oder Parametertyp von Assembly B verfügt.</span><span class="sxs-lookup"><span data-stu-id="ce54d-118">A field, property, event, or method that has a return type or parameter type from Assembly B is invoked.</span></span>  
  
 <span data-ttu-id="ce54d-119">Verwenden Sie [-libpath](libpath.md), um das Verzeichnis anzugeben, in dem sich einer oder mehrere der Assemblyverweise befinden.</span><span class="sxs-lookup"><span data-stu-id="ce54d-119">Use [-libpath](libpath.md) to specify the directory in which one or more of your assembly references is located.</span></span>  
  
 <span data-ttu-id="ce54d-120">Damit der Compiler einen Typ in einer Assembly (nicht in einem Modul) erkennen kann, muss er gezwungen werden, den Typ aufzulösen.</span><span class="sxs-lookup"><span data-stu-id="ce54d-120">For the compiler to recognize a type in an assembly (not a module), it must be forced to resolve the type.</span></span> <span data-ttu-id="ce54d-121">Ein Beispiel hierfür ist das Definieren einer Instanz des Typs.</span><span class="sxs-lookup"><span data-stu-id="ce54d-121">One example of how you can do this is to define an instance of the type.</span></span> <span data-ttu-id="ce54d-122">Es stehen andere Möglichkeiten zum Auflösen von Typnamen in einer Assembly für den Compiler zur Verfügung.</span><span class="sxs-lookup"><span data-stu-id="ce54d-122">Other ways are available to resolve type names in an assembly for the compiler.</span></span> <span data-ttu-id="ce54d-123">Wenn z. B. von einem Typ in einer Assembly geerbt wird, wird dem Compiler der Typname mitgeteilt.</span><span class="sxs-lookup"><span data-stu-id="ce54d-123">For example, if you inherit from a type in an assembly, the type name then becomes known to the compiler.</span></span>  
  
 <span data-ttu-id="ce54d-124">Die Vbc.rsp-Antwortdatei, die auf häufig verwendete .NET Framework-Assemblys verweist, wird standardmäßig verwendet.</span><span class="sxs-lookup"><span data-stu-id="ce54d-124">The Vbc.rsp response file, which references commonly used .NET Framework assemblies, is used by default.</span></span> <span data-ttu-id="ce54d-125">Verwenden Sie `-noconfig`, wenn der Compiler „Vbc.rsp“ nicht verwenden soll.</span><span class="sxs-lookup"><span data-stu-id="ce54d-125">Use `-noconfig` if you do not want the compiler to use Vbc.rsp.</span></span>  
  
 <span data-ttu-id="ce54d-126">Die Kurzform von `-reference` ist `-r`.</span><span class="sxs-lookup"><span data-stu-id="ce54d-126">The short form of `-reference` is `-r`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ce54d-127">Beispiel</span><span class="sxs-lookup"><span data-stu-id="ce54d-127">Example</span></span>  

 <span data-ttu-id="ce54d-128">Mit dem folgenden Befehl werden die Quelldatei `Input.vb` und Verweisassemblys aus `Metad1.dll` und `Metad2.dll` kompiliert, um `Out.exe` zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="ce54d-128">The following command compiles source file `Input.vb` and reference assemblies from `Metad1.dll` and `Metad2.dll` to produce `Out.exe`.</span></span>  
  
```console
vbc -reference:metad1.dll,metad2.dll -out:out.exe input.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="ce54d-129">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="ce54d-129">See also</span></span>

- [<span data-ttu-id="ce54d-130">Visual Basic-Befehlszeilencompiler</span><span class="sxs-lookup"><span data-stu-id="ce54d-130">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="ce54d-131">-noconfig</span><span class="sxs-lookup"><span data-stu-id="ce54d-131">-noconfig</span></span>](noconfig.md)
- [<span data-ttu-id="ce54d-132">-target (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ce54d-132">-target (Visual Basic)</span></span>](target.md)
- [<span data-ttu-id="ce54d-133">Public</span><span class="sxs-lookup"><span data-stu-id="ce54d-133">Public</span></span>](../../language-reference/modifiers/public.md)
- [<span data-ttu-id="ce54d-134">Beispiele für Kompilierungsbefehlszeilen</span><span class="sxs-lookup"><span data-stu-id="ce54d-134">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
