---
title: 'Vorgehensweise: Abfragen des Inhalts von Textdateien in einem Ordner (LINQ) (C#)'
description: Hier erfahren Sie, wie Sie mithilfe von LINQ in C# die Abfrage über alle Dateien in einer angegebenen Verzeichnisstruktur durchführen, jede Datei öffnen, und ihre Inhalte überprüfen.
ms.date: 07/20/2015
ms.assetid: f5b4dce7-1a34-4eb4-9bf1-60d5bdda264c
ms.openlocfilehash: a1f3e29751cd91ac1fd8e6601aa078d967776f5a
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/24/2020
ms.locfileid: "91159019"
---
# <a name="how-to-query-the-contents-of-text-files-in-a-folder-linq-c"></a><span data-ttu-id="e24e7-103">Vorgehensweise: Abfragen des Inhalts von Textdateien in einem Ordner (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="e24e7-103">How to query the contents of text files in a folder (LINQ) (C#)</span></span>

<span data-ttu-id="e24e7-104">Dieses Beispiel zeigt, wie Sie die Abfrage über alle Dateien in einer angegebenen Verzeichnisstruktur durchführen, jede Datei öffnen, und ihre Inhalte überprüfen.</span><span class="sxs-lookup"><span data-stu-id="e24e7-104">This example shows how to query over all the files in a specified directory tree, open each file, and inspect its contents.</span></span> <span data-ttu-id="e24e7-105">Diese Technik kann zum Erstellen von Indizes oder umgekehrten Indizes des Inhalts einer Verzeichnisstruktur verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="e24e7-105">This type of technique could be used to create indexes or reverse indexes of the contents of a directory tree.</span></span> <span data-ttu-id="e24e7-106">In diesem Beispiel wird eine einfache Zeichenfolgensuche ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="e24e7-106">A simple string search is performed in this example.</span></span> <span data-ttu-id="e24e7-107">Komplexere Formen des Mustervergleichs können jedoch mit einem regulären Ausdruck ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="e24e7-107">However, more complex types of pattern matching can be performed with a regular expression.</span></span> <span data-ttu-id="e24e7-108">Weitere Informationen finden Sie unter [Vorgehensweise: Verbinden von LINQ-Abfragen mit regulären Ausdrücken (C#)](./how-to-combine-linq-queries-with-regular-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="e24e7-108">For more information, see [How to combine LINQ queries with regular expressions (C#)](./how-to-combine-linq-queries-with-regular-expressions.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="e24e7-109">Beispiel</span><span class="sxs-lookup"><span data-stu-id="e24e7-109">Example</span></span>  
  
```csharp  
class QueryContents  
{  
    public static void Main()  
    {  
        // Modify this path as necessary.  
        string startFolder = @"c:\program files\Microsoft Visual Studio 9.0\";  
  
        // Take a snapshot of the file system.  
        System.IO.DirectoryInfo dir = new System.IO.DirectoryInfo(startFolder);  
  
        // This method assumes that the application has discovery permissions  
        // for all folders under the specified path.  
        IEnumerable<System.IO.FileInfo> fileList = dir.GetFiles("*.*", System.IO.SearchOption.AllDirectories);  
  
        string searchTerm = @"Visual Studio";  
  
        // Search the contents of each file.  
        // A regular expression created with the RegEx class  
        // could be used instead of the Contains method.  
        // queryMatchingFiles is an IEnumerable<string>.  
        var queryMatchingFiles =  
            from file in fileList  
            where file.Extension == ".htm"  
            let fileText = GetFileText(file.FullName)  
            where fileText.Contains(searchTerm)  
            select file.FullName;  
  
        // Execute the query.  
        Console.WriteLine("The term \"{0}\" was found in:", searchTerm);  
        foreach (string filename in queryMatchingFiles)  
        {  
            Console.WriteLine(filename);  
        }  
  
        // Keep the console window open in debug mode.  
        Console.WriteLine("Press any key to exit");  
        Console.ReadKey();  
    }  
  
    // Read the contents of the file.  
    static string GetFileText(string name)  
    {  
        string fileContents = String.Empty;  
  
        // If the file has been deleted since we took
        // the snapshot, ignore it and return the empty string.  
        if (System.IO.File.Exists(name))  
        {  
            fileContents = System.IO.File.ReadAllText(name);  
        }  
        return fileContents;  
    }  
}  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="e24e7-110">Kompilieren des Codes</span><span class="sxs-lookup"><span data-stu-id="e24e7-110">Compiling the Code</span></span>  

<span data-ttu-id="e24e7-111">Erstellen Sie ein C#-Konsolenanwendungsprojekt mit `using`-Anweisungen für die Namespaces „System.Linq“ und „System.IO“.</span><span class="sxs-lookup"><span data-stu-id="e24e7-111">Create a C# console application project, with `using` directives for the System.Linq and System.IO namespaces.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="e24e7-112">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="e24e7-112">See also</span></span>

- [<span data-ttu-id="e24e7-113">LINQ und Dateiverzeichnisse (C#)</span><span class="sxs-lookup"><span data-stu-id="e24e7-113">LINQ and File Directories (C#)</span></span>](./linq-and-file-directories.md)
- [<span data-ttu-id="e24e7-114">LINQ to Objects (C#)</span><span class="sxs-lookup"><span data-stu-id="e24e7-114">LINQ to Objects (C#)</span></span>](./linq-to-objects.md)
