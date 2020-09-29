---
title: -keycontainer
ms.date: 03/10/2018
helpviewer_keywords:
- -keycontainer compiler option [Visual Basic]
- keycontainer compiler option [Visual Basic]
- /keycontainer compiler option [Visual Basic]
ms.assetid: 6a9bc861-1752-4db1-9f64-b5252f0482cc
ms.openlocfilehash: 243583e55dcf278f951b813cca8384246d2d6db9
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/23/2020
ms.locfileid: "91085229"
---
# <a name="-keycontainer"></a><span data-ttu-id="fba45-102">-keycontainer</span><span class="sxs-lookup"><span data-stu-id="fba45-102">-keycontainer</span></span>

<span data-ttu-id="fba45-103">Gibt einen Schlüsselcontainernamen für ein Schlüsselpaar an, um einer Assembly einen starken Namen zuzuweisen.</span><span class="sxs-lookup"><span data-stu-id="fba45-103">Specifies a key container name for a key pair to give an assembly a strong name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fba45-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="fba45-104">Syntax</span></span>  
  
```console  
-keycontainer:container  
```  
  
## <a name="arguments"></a><span data-ttu-id="fba45-105">Argumente</span><span class="sxs-lookup"><span data-stu-id="fba45-105">Arguments</span></span>  
  
|<span data-ttu-id="fba45-106">Begriff</span><span class="sxs-lookup"><span data-stu-id="fba45-106">Term</span></span>|<span data-ttu-id="fba45-107">Definition</span><span class="sxs-lookup"><span data-stu-id="fba45-107">Definition</span></span>|  
|---|---|  
|`container`|<span data-ttu-id="fba45-108">Erforderlich.</span><span class="sxs-lookup"><span data-stu-id="fba45-108">Required.</span></span> <span data-ttu-id="fba45-109">Die Containerdatei, die den Schlüssel enthält.</span><span class="sxs-lookup"><span data-stu-id="fba45-109">Container file that contains the key.</span></span> <span data-ttu-id="fba45-110">Wenn der Name ein Leerzeichen enthält, müssen Sie den Dateinamen in Anführungszeichen einschließen (" ").</span><span class="sxs-lookup"><span data-stu-id="fba45-110">Enclose the file name in quotation marks ("") if the name contains a space.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fba45-111">Hinweise</span><span class="sxs-lookup"><span data-stu-id="fba45-111">Remarks</span></span>  

 <span data-ttu-id="fba45-112">Der Compiler erstellt eine teilbare Komponente, indem er einen öffentlichen Schlüssel in das Assemblymanifest einfügt und die endgültige Assembly mit dem privaten Schlüssel signiert.</span><span class="sxs-lookup"><span data-stu-id="fba45-112">The compiler creates the sharable component by inserting a public key into the assembly manifest and by signing the final assembly with the private key.</span></span> <span data-ttu-id="fba45-113">Geben Sie `sn -k file` in die Befehlszeile ein, um eine Schlüsseldatei zu generieren.</span><span class="sxs-lookup"><span data-stu-id="fba45-113">To generate a key file, type `sn -k file` at the command line.</span></span> <span data-ttu-id="fba45-114">Die Option `-i` installiert das Schlüsselpaar im Container.</span><span class="sxs-lookup"><span data-stu-id="fba45-114">The `-i` option installs the key pair into a container.</span></span> <span data-ttu-id="fba45-115">Weitere Informationen finden Sie unter [Sn.exe (Strong Name-Tool)](../../../framework/tools/sn-exe-strong-name-tool.md).</span><span class="sxs-lookup"><span data-stu-id="fba45-115">For more information, see [Sn.exe (Strong Name Tool)](../../../framework/tools/sn-exe-strong-name-tool.md)).</span></span>  
  
 <span data-ttu-id="fba45-116">Wenn Sie mit der Option `-target:module` kompilieren, wird der Name der Schlüsseldatei im Modul gespeichert und in die Assembly integriert, die erstellt wird, wenn Sie eine Assembly mit [-addmodule](addmodule.md) kompilieren.</span><span class="sxs-lookup"><span data-stu-id="fba45-116">If you compile with `-target:module`, the name of the key file is held in the module and incorporated into the assembly that is created when you compile an assembly with [-addmodule](addmodule.md).</span></span>  
  
 <span data-ttu-id="fba45-117">Sie können diese Option auch als benutzerdefiniertes Attribut (<xref:System.Reflection.AssemblyKeyNameAttribute>) im Quellcode für ein beliebiges MSIL-Modul (Microsoft Intermediate Language) angeben.</span><span class="sxs-lookup"><span data-stu-id="fba45-117">You can also specify this option as a custom attribute (<xref:System.Reflection.AssemblyKeyNameAttribute>) in the source code for any Microsoft intermediate language (MSIL) module.</span></span>  
  
 <span data-ttu-id="fba45-118">Außerdem können Sie Ihre Verschlüsselungsinformationen mit [-keyfile](keyfile.md) an den Compiler übergeben.</span><span class="sxs-lookup"><span data-stu-id="fba45-118">You can also pass your encryption information to the compiler with [-keyfile](keyfile.md).</span></span> <span data-ttu-id="fba45-119">Verwenden Sie [-delaysign](delaysign.md), wenn die Assembly teilweise signiert werden soll.</span><span class="sxs-lookup"><span data-stu-id="fba45-119">Use [-delaysign](delaysign.md) if you want a partially signed assembly.</span></span>  
  
 <span data-ttu-id="fba45-120">Weitere Informationen zum Signieren von Assemblys finden Sie unter [Erstellen und Verwenden von Assemblys mit starkem Namen](../../../standard/assembly/create-use-strong-named.md).</span><span class="sxs-lookup"><span data-stu-id="fba45-120">See [Creating and Using Strong-Named Assemblies](../../../standard/assembly/create-use-strong-named.md) for more information on signing an assembly.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="fba45-121">Diese Option `-keycontainer` steht nicht in der Visual Studio-Entwicklungsumgebung zur Verfügung. Sie ist nur verfügbar, wenn Sie über die Befehlszeile kompilieren.</span><span class="sxs-lookup"><span data-stu-id="fba45-121">The `-keycontainer` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fba45-122">Beispiel</span><span class="sxs-lookup"><span data-stu-id="fba45-122">Example</span></span>  

 <span data-ttu-id="fba45-123">Der folgende Code kompiliert die Quelldatei `Input.vb` und gibt einen Schlüsselcontainer an.</span><span class="sxs-lookup"><span data-stu-id="fba45-123">The following code compiles source file `Input.vb` and specifies a key container.</span></span>  
  
```console  
vbc -keycontainer:key1 input.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="fba45-124">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="fba45-124">See also</span></span>

- [<span data-ttu-id="fba45-125">Assemblys in .NET</span><span class="sxs-lookup"><span data-stu-id="fba45-125">Assemblies in .NET</span></span>](../../../standard/assembly/index.md)
- [<span data-ttu-id="fba45-126">Visual Basic-Befehlszeilencompiler</span><span class="sxs-lookup"><span data-stu-id="fba45-126">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="fba45-127">-keyfile</span><span class="sxs-lookup"><span data-stu-id="fba45-127">-keyfile</span></span>](keyfile.md)
- [<span data-ttu-id="fba45-128">Beispiele für Kompilierungsbefehlszeilen</span><span class="sxs-lookup"><span data-stu-id="fba45-128">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
