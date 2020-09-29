---
title: 'Vorgehensweise: Vergleichen des Inhalts von zwei Ordnern (LINQ) (C#)'
description: Dieses Beispiel zeigt drei Verfahren zum Vergleichen von Dateilisten mithilfe von LINQ-Abfragen in C#. Sie können diese Verfahren anpassen, um Sequenzen von Objekten eines beliebigen Typs zu vergleichen.
ms.date: 07/20/2015
ms.assetid: c7c4870e-c500-4de3-afa4-2c8e07f510e6
ms.openlocfilehash: 840fda1548f36d9b9ad39c2e0d1346dfc727b106
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/24/2020
ms.locfileid: "91165259"
---
# <a name="how-to-compare-the-contents-of-two-folders-linq-c"></a><span data-ttu-id="4dbbc-104">Vorgehensweise: Vergleichen des Inhalts von zwei Ordnern (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="4dbbc-104">How to compare the contents of two folders (LINQ) (C#)</span></span>

<span data-ttu-id="4dbbc-105">Dieses Beispiel zeigt drei Verfahren zum Vergleichen von zwei Dateilisten:</span><span class="sxs-lookup"><span data-stu-id="4dbbc-105">This example demonstrates three ways to compare two file listings:</span></span>  
  
- <span data-ttu-id="4dbbc-106">Durch Abfragen eines booleschen Werts, der angibt, ob die zwei Dateilisten identisch sind.</span><span class="sxs-lookup"><span data-stu-id="4dbbc-106">By querying for a Boolean value that specifies whether the two file lists are identical.</span></span>  
  
- <span data-ttu-id="4dbbc-107">Durch Abfragen der Schnittmenge, um die Dateien abzurufen, die sich in beiden Ordnern befinden.</span><span class="sxs-lookup"><span data-stu-id="4dbbc-107">By querying for the intersection to retrieve the files that are in both folders.</span></span>  
  
- <span data-ttu-id="4dbbc-108">Durch Abfragen der Unterschiedsmenge, um die Dateien abzurufen, die sich in einem Ordner befinden, aber nicht im anderen.</span><span class="sxs-lookup"><span data-stu-id="4dbbc-108">By querying for the set difference to retrieve the files that are in one folder but not the other.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="4dbbc-109">Die hier gezeigten Verfahren können zum Vergleichen von Sequenzen von Objekten eines beliebigen Typs angepasst werden.</span><span class="sxs-lookup"><span data-stu-id="4dbbc-109">The techniques shown here can be adapted to compare sequences of objects of any type.</span></span>  
  
 <span data-ttu-id="4dbbc-110">Die hier gezeigte `FileComparer`-Klasse veranschaulicht, wie eine benutzerdefinierte Vergleichsklasse zusammen mit den Standardabfrageoperatoren verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="4dbbc-110">The `FileComparer` class shown here demonstrates how to use a custom comparer class together with the Standard Query Operators.</span></span> <span data-ttu-id="4dbbc-111">Die Klasse ist nicht für die Verwendung in realen Szenarios vorgesehen.</span><span class="sxs-lookup"><span data-stu-id="4dbbc-111">The class is not intended for use in real-world scenarios.</span></span> <span data-ttu-id="4dbbc-112">Sie verwendet nur den Namen und die Länge jeder Datei in Bytes, um zu bestimmen, ob die Inhalte der einzelnen Ordner identisch sind.</span><span class="sxs-lookup"><span data-stu-id="4dbbc-112">It just uses the name and length in bytes of each file to determine whether the contents of each folder are identical or not.</span></span> <span data-ttu-id="4dbbc-113">In einem realen Szenario sollten Sie diese Vergleichsklasse ändern, um eine gründlichere Überprüfung auf Gleichheit durchzuführen.</span><span class="sxs-lookup"><span data-stu-id="4dbbc-113">In a real-world scenario, you should modify this comparer to perform a more rigorous equality check.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4dbbc-114">Beispiel</span><span class="sxs-lookup"><span data-stu-id="4dbbc-114">Example</span></span>  
  
```csharp  
namespace QueryCompareTwoDirs  
{  
    class CompareDirs  
    {  
  
        static void Main(string[] args)  
        {  
  
            // Create two identical or different temporary folders
            // on a local drive and change these file paths.  
            string pathA = @"C:\TestDir";  
            string pathB = @"C:\TestDir2";  
  
            System.IO.DirectoryInfo dir1 = new System.IO.DirectoryInfo(pathA);  
            System.IO.DirectoryInfo dir2 = new System.IO.DirectoryInfo(pathB);  
  
            // Take a snapshot of the file system.  
            IEnumerable<System.IO.FileInfo> list1 = dir1.GetFiles("*.*", System.IO.SearchOption.AllDirectories);  
            IEnumerable<System.IO.FileInfo> list2 = dir2.GetFiles("*.*", System.IO.SearchOption.AllDirectories);  
  
            //A custom file comparer defined below  
            FileCompare myFileCompare = new FileCompare();  
  
            // This query determines whether the two folders contain  
            // identical file lists, based on the custom file comparer  
            // that is defined in the FileCompare class.  
            // The query executes immediately because it returns a bool.  
            bool areIdentical = list1.SequenceEqual(list2, myFileCompare);  
  
            if (areIdentical == true)  
            {  
                Console.WriteLine("the two folders are the same");  
            }  
            else  
            {  
                Console.WriteLine("The two folders are not the same");  
            }  
  
            // Find the common files. It produces a sequence and doesn't
            // execute until the foreach statement.  
            var queryCommonFiles = list1.Intersect(list2, myFileCompare);  
  
            if (queryCommonFiles.Any())  
            {  
                Console.WriteLine("The following files are in both folders:");  
                foreach (var v in queryCommonFiles)  
                {  
                    Console.WriteLine(v.FullName); //shows which items end up in result list  
                }  
            }  
            else  
            {  
                Console.WriteLine("There are no common files in the two folders.");  
            }  
  
            // Find the set difference between the two folders.  
            // For this example we only check one way.  
            var queryList1Only = (from file in list1  
                                  select file).Except(list2, myFileCompare);  
  
            Console.WriteLine("The following files are in list1 but not list2:");  
            foreach (var v in queryList1Only)  
            {  
                Console.WriteLine(v.FullName);  
            }  
  
            // Keep the console window open in debug mode.  
            Console.WriteLine("Press any key to exit.");  
            Console.ReadKey();  
        }  
    }  
  
    // This implementation defines a very simple comparison  
    // between two FileInfo objects. It only compares the name  
    // of the files being compared and their length in bytes.  
    class FileCompare : System.Collections.Generic.IEqualityComparer<System.IO.FileInfo>  
    {  
        public FileCompare() { }  
  
        public bool Equals(System.IO.FileInfo f1, System.IO.FileInfo f2)  
        {  
            return (f1.Name == f2.Name &&  
                    f1.Length == f2.Length);  
        }  
  
        // Return a hash that reflects the comparison criteria. According to the
        // rules for IEqualityComparer<T>, if Equals is true, then the hash codes must  
        // also be equal. Because equality as defined here is a simple value equality, not  
        // reference identity, it is possible that two or more objects will produce the same  
        // hash code.  
        public int GetHashCode(System.IO.FileInfo fi)  
        {  
            string s = $"{fi.Name}{fi.Length}";
            return s.GetHashCode();  
        }  
    }  
}  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="4dbbc-115">Kompilieren des Codes</span><span class="sxs-lookup"><span data-stu-id="4dbbc-115">Compiling the Code</span></span>  

 <span data-ttu-id="4dbbc-116">Erstellen Sie ein C#-Konsolenanwendungsprojekt mit `using`-Anweisungen für die Namespaces „System.Linq“ und „System.IO“.</span><span class="sxs-lookup"><span data-stu-id="4dbbc-116">Create a C# console application project, with `using` directives for the System.Linq and System.IO namespaces.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4dbbc-117">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="4dbbc-117">See also</span></span>

- [<span data-ttu-id="4dbbc-118">LINQ to Objects (C#)</span><span class="sxs-lookup"><span data-stu-id="4dbbc-118">LINQ to Objects (C#)</span></span>](./linq-to-objects.md)
- [<span data-ttu-id="4dbbc-119">LINQ und Dateiverzeichnisse (C#)</span><span class="sxs-lookup"><span data-stu-id="4dbbc-119">LINQ and File Directories (C#)</span></span>](./linq-and-file-directories.md)
