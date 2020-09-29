---
title: -imports
ms.date: 03/10/2018
helpviewer_keywords:
- /imports compiler option [Visual Basic]
- imports compiler option [Visual Basic]
- -imports compiler option [Visual Basic]
ms.assetid: 9a93fb53-c080-497b-bf9b-441022dbbc39
ms.openlocfilehash: 69781dff1474e42ae5f735fdefd694c6447636b5
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/23/2020
ms.locfileid: "91085255"
---
# <a name="-imports-visual-basic"></a><span data-ttu-id="8f05d-102">-imports (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8f05d-102">-imports (Visual Basic)</span></span>

<span data-ttu-id="8f05d-103">Die Option -imports importiert Namespaces aus einer angegebenen Assembly.</span><span class="sxs-lookup"><span data-stu-id="8f05d-103">Imports namespaces from a specified assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8f05d-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="8f05d-104">Syntax</span></span>  
  
```console  
-imports:namespaceList  
```  
  
## <a name="arguments"></a><span data-ttu-id="8f05d-105">Argumente</span><span class="sxs-lookup"><span data-stu-id="8f05d-105">Arguments</span></span>  
  
|<span data-ttu-id="8f05d-106">Begriff</span><span class="sxs-lookup"><span data-stu-id="8f05d-106">Term</span></span>|<span data-ttu-id="8f05d-107">Definition</span><span class="sxs-lookup"><span data-stu-id="8f05d-107">Definition</span></span>|  
|---|---|  
|`namespaceList`|<span data-ttu-id="8f05d-108">Erforderlich.</span><span class="sxs-lookup"><span data-stu-id="8f05d-108">Required.</span></span> <span data-ttu-id="8f05d-109">Liste der zu importierenden Namespaces mit Kommas als Trennzeichen</span><span class="sxs-lookup"><span data-stu-id="8f05d-109">Comma-delimited list of namespaces to be imported.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8f05d-110">Hinweise</span><span class="sxs-lookup"><span data-stu-id="8f05d-110">Remarks</span></span>  

 <span data-ttu-id="8f05d-111">Mit der Option `-imports` werden alle Namespaces importiert, die in den aktuellen Quelldateien oder einer beliebigen Assembly, auf die verwiesen wird, definiert sind.</span><span class="sxs-lookup"><span data-stu-id="8f05d-111">The `-imports` option imports any namespace defined within the current set of source files or from any referenced assembly.</span></span>  
  
 <span data-ttu-id="8f05d-112">Die Member eines Namespace, der mit `-imports` angegeben wird, sind für alle Quellcodedateien in der Kompilierung verfügbar.</span><span class="sxs-lookup"><span data-stu-id="8f05d-112">The members in a namespace specified with `-imports` are available to all source-code files in the compilation.</span></span> <span data-ttu-id="8f05d-113">Verwenden Sie die [Imports-Anweisung (.NET-Namespace und -Typ)](../../language-reference/statements/imports-statement-net-namespace-and-type.md), um einen Namespace in einer einzelnen Quellcodedatei zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="8f05d-113">Use the [Imports Statement (.NET Namespace and Type)](../../language-reference/statements/imports-statement-net-namespace-and-type.md) to use a namespace in a single source-code file.</span></span>  
  
|<span data-ttu-id="8f05d-114">So legen Sie -imports in der integrierten Visual Studio-Entwicklungsumgebung fest</span><span class="sxs-lookup"><span data-stu-id="8f05d-114">To set -imports in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="8f05d-115">1.  Ein Projekt auswählen in **Projektmappen-Explorer**.</span><span class="sxs-lookup"><span data-stu-id="8f05d-115">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="8f05d-116">Klicken Sie im Menü **Projekt** auf **Eigenschaften**.</span><span class="sxs-lookup"><span data-stu-id="8f05d-116">On the **Project** menu, click **Properties**.</span></span> <br /><span data-ttu-id="8f05d-117">2.  Klicken Sie auf die Registerkarte **Verweise**.</span><span class="sxs-lookup"><span data-stu-id="8f05d-117">2.  Click the **References** tab.</span></span><br /><span data-ttu-id="8f05d-118">3.  Geben Sie den Namespacenamen in das Feld neben der Schaltfläche **Benutzerimport hinzufügen** ein.</span><span class="sxs-lookup"><span data-stu-id="8f05d-118">3.  Enter the namespace name in the box beside the **Add User Import** button.</span></span><br /><span data-ttu-id="8f05d-119">4.  Klicken Sie auf die Schaltfläche **Benutzerimport hinzufügen**.</span><span class="sxs-lookup"><span data-stu-id="8f05d-119">4.  Click the **Add User Import** button.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="8f05d-120">Beispiel</span><span class="sxs-lookup"><span data-stu-id="8f05d-120">Example</span></span>  

 <span data-ttu-id="8f05d-121">Der folgende Code wird kompiliert, wenn `-imports:system.globalization` angegeben wird.</span><span class="sxs-lookup"><span data-stu-id="8f05d-121">The following code compiles when `-imports:system.globalization` is specified.</span></span> <span data-ttu-id="8f05d-122">Ohne diese Angabe ist für eine erfolgreiche Kompilierung entweder erforderlich, dass eine `Imports System.Globalization`-Anweisung am Anfang der Quellcodedatei enthalten ist oder dass die Eigenschaft als `System.Globalization.CultureInfo.CurrentCulture.Name` vollqualifiziert ist.</span><span class="sxs-lookup"><span data-stu-id="8f05d-122">Without it, successful compilation requires either that an `Imports System.Globalization` statement be included at the beginning of the source code file, or that the property be fully qualified as `System.Globalization.CultureInfo.CurrentCulture.Name`.</span></span>

```vb
Module Example
   Public Sub Main()
      Console.WriteLine($"The current culture is {CultureInfo.CurrentCulture.Name}")
   End Sub
End Module
```

## <a name="see-also"></a><span data-ttu-id="8f05d-123">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="8f05d-123">See also</span></span>

- [<span data-ttu-id="8f05d-124">Visual Basic-Befehlszeilencompiler</span><span class="sxs-lookup"><span data-stu-id="8f05d-124">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="8f05d-125">Verweise und die Imports-Anweisung</span><span class="sxs-lookup"><span data-stu-id="8f05d-125">References and the Imports Statement</span></span>](../../programming-guide/program-structure/references-and-the-imports-statement.md)
- [<span data-ttu-id="8f05d-126">Beispiele für Kompilierungsbefehlszeilen</span><span class="sxs-lookup"><span data-stu-id="8f05d-126">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
