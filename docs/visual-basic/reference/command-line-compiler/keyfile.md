---
title: -keyfile
ms.date: 03/10/2018
helpviewer_keywords:
- /keyfile compiler option [Visual Basic]
- keyfile compiler option [Visual Basic]
- -keyfile compiler option [Visual Basic]
ms.assetid: ffa82a4b-517a-4c6c-9889-5bae7b534bb8
ms.openlocfilehash: c81486243195f7d022bd474ef6db20d069b3a018
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/23/2020
ms.locfileid: "91085151"
---
# <a name="-keyfile"></a><span data-ttu-id="fb027-102">-keyfile</span><span class="sxs-lookup"><span data-stu-id="fb027-102">-keyfile</span></span>

<span data-ttu-id="fb027-103">Gibt eine Datei mit einem Schlüssel oder Schlüsselpaar an, um einer Assembly einen starken Namen zuzuweisen.</span><span class="sxs-lookup"><span data-stu-id="fb027-103">Specifies a file containing a key or key pair to give an assembly a strong name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fb027-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="fb027-104">Syntax</span></span>  
  
```console
-keyfile:file  
```  
  
## <a name="arguments"></a><span data-ttu-id="fb027-105">Argumente</span><span class="sxs-lookup"><span data-stu-id="fb027-105">Arguments</span></span>  

 `file`  
 <span data-ttu-id="fb027-106">Erforderlich.</span><span class="sxs-lookup"><span data-stu-id="fb027-106">Required.</span></span> <span data-ttu-id="fb027-107">Die Datei, die den Schlüssel enthält.</span><span class="sxs-lookup"><span data-stu-id="fb027-107">File that contains the key.</span></span> <span data-ttu-id="fb027-108">Wenn der Dateiname ein Leerzeichen enthält, müssen Sie diesen in Anführungszeichen (" ") einschließen.</span><span class="sxs-lookup"><span data-stu-id="fb027-108">If the file name contains a space, enclose the name in quotation marks (" ").</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fb027-109">Hinweise</span><span class="sxs-lookup"><span data-stu-id="fb027-109">Remarks</span></span>  

 <span data-ttu-id="fb027-110">Der Compiler fügt den öffentlichen Schlüssel in das Assemblymanifest ein und signiert anschließend die endgültige Assembly mit dem privaten Schlüssel.</span><span class="sxs-lookup"><span data-stu-id="fb027-110">The compiler inserts the public key into the assembly manifest and then signs the final assembly with the private key.</span></span> <span data-ttu-id="fb027-111">Geben Sie `sn -k file` in die Befehlszeile ein, um eine Schlüsseldatei zu generieren.</span><span class="sxs-lookup"><span data-stu-id="fb027-111">To generate a key file, type `sn -k file` at the command line.</span></span> <span data-ttu-id="fb027-112">Weitere Informationen finden Sie unter [Sn.exe (Strong Name-Tool)](../../../framework/tools/sn-exe-strong-name-tool.md).</span><span class="sxs-lookup"><span data-stu-id="fb027-112">For more information, see [Sn.exe (Strong Name Tool)](../../../framework/tools/sn-exe-strong-name-tool.md)).</span></span>  
  
 <span data-ttu-id="fb027-113">Wenn Sie mit der Option `-target:module` kompilieren, wird der Name der Schlüsseldatei im Modul gespeichert und in die Assembly integriert, die erstellt wird, wenn Sie eine Assembly mit [-addmodule](addmodule.md) kompilieren.</span><span class="sxs-lookup"><span data-stu-id="fb027-113">If you compile with `-target:module`, the name of the key file is held in the module and incorporated into the assembly that is created when you compile an assembly with [-addmodule](addmodule.md).</span></span>  
  
 <span data-ttu-id="fb027-114">Außerdem können Sie Ihre Verschlüsselungsinformationen mit [-keycontainer](keycontainer.md) an den Compiler übergeben.</span><span class="sxs-lookup"><span data-stu-id="fb027-114">You can also pass your encryption information to the compiler with [-keycontainer](keycontainer.md).</span></span> <span data-ttu-id="fb027-115">Verwenden Sie [-delaysign](delaysign.md), wenn die Assembly teilweise signiert werden soll.</span><span class="sxs-lookup"><span data-stu-id="fb027-115">Use [-delaysign](delaysign.md) if you want a partially signed assembly.</span></span>  
  
 <span data-ttu-id="fb027-116">Sie können diese Option auch als benutzerdefiniertes Attribut (<xref:System.Reflection.AssemblyKeyFileAttribute>) im Quellcode für ein beliebiges MSIL-Modul (Microsoft Intermediate Language) angeben.</span><span class="sxs-lookup"><span data-stu-id="fb027-116">You can also specify this option as a custom attribute (<xref:System.Reflection.AssemblyKeyFileAttribute>) in the source code for any Microsoft intermediate language module.</span></span>  
  
 <span data-ttu-id="fb027-117">Wenn für die gleiche Kompilierung sowohl `-keyfile` als auch [-keycontainer](keycontainer.md) angegeben werden (über eine Befehlszeilenoption oder ein benutzerdefiniertes Attribut), versucht der Compiler zunächst, den Schlüsselcontainer zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="fb027-117">In case both `-keyfile` and [-keycontainer](keycontainer.md) are specified (either by command-line option or by custom attribute) in the same compilation, the compiler first tries the key container.</span></span> <span data-ttu-id="fb027-118">Wenn dies erfolgreich ist, wird die Assembly mit den Informationen im Schlüsselcontainer signiert.</span><span class="sxs-lookup"><span data-stu-id="fb027-118">If that succeeds, then the assembly is signed with the information in the key container.</span></span> <span data-ttu-id="fb027-119">Wenn den Compiler den Schlüsselcontainer nicht findet, versucht er, die mit `-keyfile` angegebene Datei zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="fb027-119">If the compiler does not find the key container, it tries the file specified with `-keyfile`.</span></span> <span data-ttu-id="fb027-120">Wenn dieser Vorgang erfolgreich ist, wird die Assembly mit den Informationen in der Schlüsseldatei signiert, und die Schlüsselinformationen werden im Schlüsselcontainer installiert (vergleichbar mit `sn -i`), sodass der Schlüsselcontainer bei der nächsten Kompilierung gültig ist.</span><span class="sxs-lookup"><span data-stu-id="fb027-120">If this succeeds, the assembly is signed with the information in the key file, and the key information is installed in the key container (similar to `sn -i`) so that on the next compilation, the key container will be valid.</span></span>  
  
 <span data-ttu-id="fb027-121">Beachten Sie, dass die Schlüsseldatei möglicherweise nur den öffentlichen Schlüssel enthält.</span><span class="sxs-lookup"><span data-stu-id="fb027-121">Note that a key file might contain only the public key.</span></span>  
  
 <span data-ttu-id="fb027-122">Weitere Informationen zum Signieren von Assemblys finden Sie unter [Erstellen und Verwenden von Assemblys mit starkem Namen](../../../standard/assembly/create-use-strong-named.md).</span><span class="sxs-lookup"><span data-stu-id="fb027-122">See [Creating and Using Strong-Named Assemblies](../../../standard/assembly/create-use-strong-named.md) for more information on signing an assembly.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="fb027-123">Die Option `-keyfile` steht nicht in der Visual Studio-Entwicklungsumgebung zur Verfügung. Sie ist nur verfügbar, wenn Sie über die Befehlszeile kompilieren.</span><span class="sxs-lookup"><span data-stu-id="fb027-123">The `-keyfile` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>

## <a name="example"></a><span data-ttu-id="fb027-124">Beispiel</span><span class="sxs-lookup"><span data-stu-id="fb027-124">Example</span></span>

<span data-ttu-id="fb027-125">Der folgende Code kompiliert die Quelldatei `Input.vb` und gibt eine Schlüsseldatei an.</span><span class="sxs-lookup"><span data-stu-id="fb027-125">The following code compiles source file `Input.vb` and specifies a key file.</span></span>

```console
vbc -keyfile:myfile.sn input.vb
```

## <a name="see-also"></a><span data-ttu-id="fb027-126">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="fb027-126">See also</span></span>

- [<span data-ttu-id="fb027-127">Assemblys in .NET</span><span class="sxs-lookup"><span data-stu-id="fb027-127">Assemblies in .NET</span></span>](../../../standard/assembly/index.md)
- [<span data-ttu-id="fb027-128">Visual Basic-Befehlszeilencompiler</span><span class="sxs-lookup"><span data-stu-id="fb027-128">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="fb027-129">-reference (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fb027-129">-reference (Visual Basic)</span></span>](reference.md)
- [<span data-ttu-id="fb027-130">Beispiele für Kompilierungsbefehlszeilen</span><span class="sxs-lookup"><span data-stu-id="fb027-130">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
