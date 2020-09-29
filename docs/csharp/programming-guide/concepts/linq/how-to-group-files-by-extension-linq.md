---
title: 'Vorgehensweise: Gruppieren von Dateien nach Erweiterung (LINQ) (C#)'
description: In diesem Artikel erfahren Sie, wie Sie LINQ verwenden, um erweiterte Gruppierungs- und Sortierungsvorgänge für Listen mit Dateien oder Ordnern in C# durchzuführen. In diesem Beispiel wird zeigt, wie Sie Ausgaben in der Konsole in Seiten einteilen können.
ms.date: 07/20/2015
ms.assetid: 21a98320-a5a1-4981-82d8-6a637e7d9018
ms.openlocfilehash: c17328980c20dd6ec32e8d0ce176081122443344
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/24/2020
ms.locfileid: "91159045"
---
# <a name="how-to-group-files-by-extension-linq-c"></a>Vorgehensweise: Gruppieren von Dateien nach Erweiterung (LINQ) (C#)

In dieses Beispiel wird veranschaulicht, wie Sie mithilfe von LINQ erweiterte Gruppierungs- und Sortiervorgänge mit Datei- oder Ordnerlisten ausführen können. Es zeigt auch, wie der Bildlauf für die Ausgabe im Konsolenfenster mithilfe der Methoden <xref:System.Linq.Enumerable.Skip%2A> und <xref:System.Linq.Enumerable.Take%2A> durchgeführt wird.  
  
## <a name="example"></a>Beispiel  

 Die folgende Abfrage zeigt, wie Sie den Inhalt einer angegebenen Verzeichnisstruktur nach der Dateierweiterung gruppieren.  
  
```csharp  
class GroupByExtension  
{  
    // This query will sort all the files under the specified folder  
    //  and subfolder into groups keyed by the file extension.  
    private static void Main()  
    {  
        // Take a snapshot of the file system.  
        string startFolder = @"c:\program files\Microsoft Visual Studio 9.0\Common7";  
  
        // Used in WriteLine to trim output lines.  
        int trimLength = startFolder.Length;  
  
        // Take a snapshot of the file system.  
        System.IO.DirectoryInfo dir = new System.IO.DirectoryInfo(startFolder);  
  
        // This method assumes that the application has discovery permissions  
        // for all folders under the specified path.  
        IEnumerable<System.IO.FileInfo> fileList = dir.GetFiles("*.*", System.IO.SearchOption.AllDirectories);  
  
        // Create the query.  
        var queryGroupByExt =  
            from file in fileList  
            group file by file.Extension.ToLower() into fileGroup  
            orderby fileGroup.Key  
            select fileGroup;  
  
        // Display one group at a time. If the number of
        // entries is greater than the number of lines  
        // in the console window, then page the output.  
        PageOutput(trimLength, queryGroupByExt);  
    }  
  
    // This method specifically handles group queries of FileInfo objects with string keys.  
    // It can be modified to work for any long listings of data. Note that explicit typing  
    // must be used in method signatures. The groupbyExtList parameter is a query that produces  
    // groups of FileInfo objects with string keys.  
    private static void PageOutput(int rootLength,  
                                    IEnumerable<System.Linq.IGrouping<string, System.IO.FileInfo>> groupByExtList)  
    {  
        // Flag to break out of paging loop.  
        bool goAgain = true;  
  
        // "3" = 1 line for extension + 1 for "Press any key" + 1 for input cursor.  
        int numLines = Console.WindowHeight - 3;  
  
        // Iterate through the outer collection of groups.  
        foreach (var filegroup in groupByExtList)  
        {  
            // Start a new extension at the top of a page.  
            int currentLine = 0;  
  
            // Output only as many lines of the current group as will fit in the window.  
            do  
            {  
                Console.Clear();  
                Console.WriteLine(filegroup.Key == String.Empty ? "[none]" : filegroup.Key);  
  
                // Get 'numLines' number of items starting at number 'currentLine'.  
                var resultPage = filegroup.Skip(currentLine).Take(numLines);  
  
                //Execute the resultPage query  
                foreach (var f in resultPage)  
                {  
                    Console.WriteLine("\t{0}", f.FullName.Substring(rootLength));  
                }  
  
                // Increment the line counter.  
                currentLine += numLines;  
  
                // Give the user a chance to escape.  
                Console.WriteLine("Press any key to continue or the 'End' key to break...");  
                ConsoleKey key = Console.ReadKey().Key;  
                if (key == ConsoleKey.End)  
                {  
                    goAgain = false;  
                    break;  
                }  
            } while (currentLine < filegroup.Count());  
  
            if (goAgain == false)  
                break;  
        }  
    }  
}  
```  
  
 Die Ausgabe dieses Programms kann je nach den Details des lokalen Dateisystems und der Einstellung für `startFolder` lang sein. Um alle Ergebnisse anzuzeigen, wird in diesem Beispiel gezeigt, wie Sie Ergebnisse seitenweise anzeigen. Die gleichen Techniken können auf Windows- und Webanwendungen angewendet werden. Beachten Sie, dass eine geschachtelte `foreach`-Schleife erforderlich ist, da der Code die Elemente in einer Gruppe seitenweise anzeigt. Es ist auch sinnvoll, die aktuelle Position in der Liste berechnen zu können und es dem Benutzer zu ermöglichen, das seitenweise Anzeigen anzuhalten und das Programm zu beenden. In diesem speziellen Fall wird die Abfrage zum seitenweise Anzeigen gegen die zwischengespeicherten Ergebnisse aus der ursprünglichen Abfrage ausgeführt. In anderen Kontexten wie LINQ to SQL ist ein solches Zwischenspeichern nicht erforderlich.  
  
## <a name="compiling-the-code"></a>Kompilieren des Codes  

 Erstellen Sie ein C#-Konsolenanwendungsprojekt mit `using`-Anweisungen für die Namespaces „System.Linq“ und „System.IO“.  
  
## <a name="see-also"></a>Siehe auch

- [LINQ to Objects (C#)](./linq-to-objects.md)
- [LINQ und Dateiverzeichnisse (C#)](./linq-and-file-directories.md)
