---
title: 'Vorgehensweise: Kopieren, Löschen und Verschieben von Dateien und Ordnern (C#-Programmierleitfaden)'
description: Erfahren Sie, wie Sie Dateien und Ordner mithilfe der Klassen „File“, „Directory“, „FileInfo“ und „DirectoryInfo“ kopieren, löschen und verschieben.
ms.date: 07/20/2015
helpviewer_keywords:
- I/O [C#]
ms.assetid: 62e52cd7-9597-4e4a-acf9-1315f5cdbf05
ms.openlocfilehash: 24595c9f5c75b70afb0ff079b6b93e35502f7fb5
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/24/2020
ms.locfileid: "91202512"
---
# <a name="how-to-copy-delete-and-move-files-and-folders-c-programming-guide"></a><span data-ttu-id="3aca8-103">Vorgehensweise: Kopieren, Löschen und Verschieben von Dateien und Ordnern (C#-Programmierleitfaden)</span><span class="sxs-lookup"><span data-stu-id="3aca8-103">How to copy, delete, and move files and folders (C# Programming Guide)</span></span>

<span data-ttu-id="3aca8-104">Die folgenden Beispiele veranschaulichen, wie Dateien und Ordner mithilfe der Klassen <xref:System.IO.File?displayProperty=nameWithType>, <xref:System.IO.Directory?displayProperty=nameWithType>, <xref:System.IO.FileInfo?displayProperty=nameWithType> und <xref:System.IO.DirectoryInfo?displayProperty=nameWithType> aus dem Namespace <xref:System.IO?displayProperty=nameWithType> synchron kopiert, verschoben und gelöscht werden können.</span><span class="sxs-lookup"><span data-stu-id="3aca8-104">The following examples show how to copy, move, and delete files and folders in a synchronous manner by using the <xref:System.IO.File?displayProperty=nameWithType>, <xref:System.IO.Directory?displayProperty=nameWithType>, <xref:System.IO.FileInfo?displayProperty=nameWithType>, and <xref:System.IO.DirectoryInfo?displayProperty=nameWithType> classes from the <xref:System.IO?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="3aca8-105">Diese Beispiele stellen keine Statusanzeige oder irgendeine andere Benutzeroberfläche bereit.</span><span class="sxs-lookup"><span data-stu-id="3aca8-105">These examples do not provide a progress bar or any other user interface.</span></span> <span data-ttu-id="3aca8-106">Informationen zur Bereitstellung eines standardmäßigen Fortschrittsdialogfelds finden Sie unter [Vorgehensweise: Bereitstellen eines Statusdialogfelds für Dateioperationen](how-to-provide-a-progress-dialog-box-for-file-operations.md).</span><span class="sxs-lookup"><span data-stu-id="3aca8-106">If you want to provide a standard progress dialog box, see [How to provide a progress dialog box for file operations](how-to-provide-a-progress-dialog-box-for-file-operations.md).</span></span>  
  
 <span data-ttu-id="3aca8-107">Verwenden Sie <xref:System.IO.FileSystemWatcher?displayProperty=nameWithType> zum Bereitstellen von Ereignissen, mit denen Sie bei Vorgängen auf mehreren Dateien den Status berechnen können.</span><span class="sxs-lookup"><span data-stu-id="3aca8-107">Use <xref:System.IO.FileSystemWatcher?displayProperty=nameWithType> to provide events that will enable you to calculate the progress when operating on multiple files.</span></span> <span data-ttu-id="3aca8-108">Eine weitere Möglichkeit ist die Verwendung eines Plattformaufrufs, um die relevanten dateibezogenen Methoden in der Windows-Shell aufzurufen.</span><span class="sxs-lookup"><span data-stu-id="3aca8-108">Another approach is to use platform invoke to call the relevant file-related methods in the Windows Shell.</span></span> <span data-ttu-id="3aca8-109">Weitere Informationen dazu, wie Sie diese Dateivorgänge asynchron ausführen, finden Sie unter [Asynchrone Datei-E/A](../../../standard/io/asynchronous-file-i-o.md).</span><span class="sxs-lookup"><span data-stu-id="3aca8-109">For information about how to perform these file operations asynchronously, see [Asynchronous File I/O](../../../standard/io/asynchronous-file-i-o.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="3aca8-110">Beispiel</span><span class="sxs-lookup"><span data-stu-id="3aca8-110">Example</span></span>  

 <span data-ttu-id="3aca8-111">Im folgenden Beispiel wird gezeigt, wie Sie Dateien und Verzeichnisse kopieren.</span><span class="sxs-lookup"><span data-stu-id="3aca8-111">The following example shows how to copy files and directories.</span></span>  
  
 [!code-csharp[csFilesandFolders#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csFilesAndFolders/CS/FileIteration.cs#7)]  
  
## <a name="example"></a><span data-ttu-id="3aca8-112">Beispiel</span><span class="sxs-lookup"><span data-stu-id="3aca8-112">Example</span></span>  

 <span data-ttu-id="3aca8-113">Im folgenden Beispiel wird gezeigt, wie Sie Dateien und Verzeichnisse verschieben.</span><span class="sxs-lookup"><span data-stu-id="3aca8-113">The following example shows how to move files and directories.</span></span>  
  
 [!code-csharp[csFilesandFolders#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csFilesAndFolders/CS/FileIteration.cs#8)]  
  
## <a name="example"></a><span data-ttu-id="3aca8-114">Beispiel</span><span class="sxs-lookup"><span data-stu-id="3aca8-114">Example</span></span>  

 <span data-ttu-id="3aca8-115">Im folgenden Beispiel wird gezeigt, wie Sie Dateien und Verzeichnisse löschen.</span><span class="sxs-lookup"><span data-stu-id="3aca8-115">The following example shows how to delete files and directories.</span></span>  
  
 [!code-csharp[csFilesandFolders#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csFilesAndFolders/CS/FileIteration.cs#9)]  
  
## <a name="see-also"></a><span data-ttu-id="3aca8-116">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="3aca8-116">See also</span></span>

- <xref:System.IO?displayProperty=nameWithType>
- [<span data-ttu-id="3aca8-117">C#-Programmierhandbuch</span><span class="sxs-lookup"><span data-stu-id="3aca8-117">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="3aca8-118">Das Dateisystem und die Registrierung (C#-Programmierhandbuch)</span><span class="sxs-lookup"><span data-stu-id="3aca8-118">File System and the Registry (C# Programming Guide)</span></span>](index.md)
- [<span data-ttu-id="3aca8-119">Bereitstellen eines Statusdialogfelds für Dateioperationen</span><span class="sxs-lookup"><span data-stu-id="3aca8-119">How to provide a progress dialog box for file operations</span></span>](how-to-provide-a-progress-dialog-box-for-file-operations.md)
- [<span data-ttu-id="3aca8-120">Datei- und Stream-E/A</span><span class="sxs-lookup"><span data-stu-id="3aca8-120">File and Stream I/O</span></span>](../../../standard/io/index.md)
- [<span data-ttu-id="3aca8-121">Allgemeine E/A-Aufgaben</span><span class="sxs-lookup"><span data-stu-id="3aca8-121">Common I/O Tasks</span></span>](../../../standard/io/common-i-o-tasks.md)
