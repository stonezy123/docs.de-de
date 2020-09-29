---
title: 'Vorgehensweise: Verbinden und Vergleichen von Zeichenfolgenauflistungen (LINQ) (C#)'
description: In diesem Beispiel werden Dateien zusammengeführt, die Textzeilen enthalten. In diesem Artikel erfahren Sie, wie Sie eine einfache Verkettung, eine Vereinigung und eine Schnittmenge für die Zeilen in LINQ in C# durchführen.
ms.date: 07/20/2015
ms.assetid: 25926e5b-fde2-4dc1-86a0-16ead7aa13d2
ms.openlocfilehash: 7bc2b2fbc6a6ce09305f870275f2f0ea5379d4fc
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/24/2020
ms.locfileid: "91167599"
---
# <a name="how-to-combine-and-compare-string-collections-linq-c"></a><span data-ttu-id="c03a8-104">Vorgehensweise: Verbinden und Vergleichen von Zeichenfolgenauflistungen (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="c03a8-104">How to combine and compare string collections (LINQ) (C#)</span></span>

<span data-ttu-id="c03a8-105">In diesem Beispiel wird veranschaulicht, wie Sie Dateien mit Textzeilen zusammenführen und die Ergebnisse anschließend sortieren.</span><span class="sxs-lookup"><span data-stu-id="c03a8-105">This example shows how to merge files that contain lines of text and then sort the results.</span></span> <span data-ttu-id="c03a8-106">Insbesondere wird gezeigt, wie eine einfache Verkettung, eine Vereinigung und eine Schnittmenge von zwei Gruppen von Textzeilen ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="c03a8-106">Specifically, it shows how to perform a simple concatenation, a union, and an intersection on the two sets of text lines.</span></span>  
  
### <a name="to-set-up-the-project-and-the-text-files"></a><span data-ttu-id="c03a8-107">So richten Sie das Projekt und die Textdateien ein</span><span class="sxs-lookup"><span data-stu-id="c03a8-107">To set up the project and the text files</span></span>  
  
1. <span data-ttu-id="c03a8-108">Kopieren Sie diese Namen in eine Textdatei namens „names1.txt“, und speichern Sie sie in Ihrem Projektordner:</span><span class="sxs-lookup"><span data-stu-id="c03a8-108">Copy these names into a text file that is named names1.txt and save it in your project folder:</span></span>  
  
    ```text  
    Bankov, Peter  
    Holm, Michael  
    Garcia, Hugo  
    Potra, Cristina  
    Noriega, Fabricio  
    Aw, Kam Foo  
    Beebe, Ann  
    Toyoshima, Tim  
    Guy, Wey Yuan  
    Garcia, Debra  
    ```  
  
2. <span data-ttu-id="c03a8-109">Kopieren Sie diese Namen in eine Textdatei namens „names2.txt“, und speichern Sie sie in Ihrem Projektordner.</span><span class="sxs-lookup"><span data-stu-id="c03a8-109">Copy these names into a text file that is named names2.txt and save it in your project folder.</span></span> <span data-ttu-id="c03a8-110">Beachten Sie, dass die zwei Dateien einige Namen gemeinsam haben.</span><span class="sxs-lookup"><span data-stu-id="c03a8-110">Note that the two files have some names in common.</span></span>  
  
    ```text  
    Liu, Jinghao  
    Bankov, Peter  
    Holm, Michael  
    Garcia, Hugo  
    Beebe, Ann  
    Gilchrist, Beth  
    Myrcha, Jacek  
    Giakoumakis, Leo  
    McLin, Nkenge  
    El Yassir, Mehdi  
    ```  
  
## <a name="example"></a><span data-ttu-id="c03a8-111">Beispiel</span><span class="sxs-lookup"><span data-stu-id="c03a8-111">Example</span></span>  
  
```csharp  
class MergeStrings  
    {  
        static void Main(string[] args)  
        {  
            //Put text files in your solution folder  
            string[] fileA = System.IO.File.ReadAllLines(@"../../../names1.txt");  
            string[] fileB = System.IO.File.ReadAllLines(@"../../../names2.txt");  
  
            //Simple concatenation and sort. Duplicates are preserved.  
            IEnumerable<string> concatQuery =  
                fileA.Concat(fileB).OrderBy(s => s);  
  
            // Pass the query variable to another function for execution.  
            OutputQueryResults(concatQuery, "Simple concatenate and sort. Duplicates are preserved:");  
  
            // Concatenate and remove duplicate names based on  
            // default string comparer.  
            IEnumerable<string> uniqueNamesQuery =  
                fileA.Union(fileB).OrderBy(s => s);  
            OutputQueryResults(uniqueNamesQuery, "Union removes duplicate names:");  
  
            // Find the names that occur in both files (based on  
            // default string comparer).  
            IEnumerable<string> commonNamesQuery =  
                fileA.Intersect(fileB);  
            OutputQueryResults(commonNamesQuery, "Merge based on intersect:");  
  
            // Find the matching fields in each list. Merge the two
            // results by using Concat, and then  
            // sort using the default string comparer.  
            string nameMatch = "Garcia";  
  
            IEnumerable<String> tempQuery1 =  
                from name in fileA  
                let n = name.Split(',')  
                where n[0] == nameMatch  
                select name;  
  
            IEnumerable<string> tempQuery2 =  
                from name2 in fileB  
                let n2 = name2.Split(',')  
                where n2[0] == nameMatch  
                select name2;  
  
            IEnumerable<string> nameMatchQuery =  
                tempQuery1.Concat(tempQuery2).OrderBy(s => s);  
            OutputQueryResults(nameMatchQuery, $"Concat based on partial name match \"{nameMatch}\":");
  
            // Keep the console window open in debug mode.  
            Console.WriteLine("Press any key to exit");  
            Console.ReadKey();  
        }  
  
        static void OutputQueryResults(IEnumerable<string> query, string message)  
        {  
            Console.WriteLine(System.Environment.NewLine + message);  
            foreach (string item in query)  
            {  
                Console.WriteLine(item);  
            }  
            Console.WriteLine("{0} total names in list", query.Count());  
        }  
    }  
    /* Output:  
        Simple concatenate and sort. Duplicates are preserved:  
        Aw, Kam Foo  
        Bankov, Peter  
        Bankov, Peter  
        Beebe, Ann  
        Beebe, Ann  
        El Yassir, Mehdi  
        Garcia, Debra  
        Garcia, Hugo  
        Garcia, Hugo  
        Giakoumakis, Leo  
        Gilchrist, Beth  
        Guy, Wey Yuan  
        Holm, Michael  
        Holm, Michael  
        Liu, Jinghao  
        McLin, Nkenge  
        Myrcha, Jacek  
        Noriega, Fabricio  
        Potra, Cristina  
        Toyoshima, Tim  
        20 total names in list  
  
        Union removes duplicate names:  
        Aw, Kam Foo  
        Bankov, Peter  
        Beebe, Ann  
        El Yassir, Mehdi  
        Garcia, Debra  
        Garcia, Hugo  
        Giakoumakis, Leo  
        Gilchrist, Beth  
        Guy, Wey Yuan  
        Holm, Michael  
        Liu, Jinghao  
        McLin, Nkenge  
        Myrcha, Jacek  
        Noriega, Fabricio  
        Potra, Cristina  
        Toyoshima, Tim  
        16 total names in list  
  
        Merge based on intersect:  
        Bankov, Peter  
        Holm, Michael  
        Garcia, Hugo  
        Beebe, Ann  
        4 total names in list  
  
        Concat based on partial name match "Garcia":  
        Garcia, Debra  
        Garcia, Hugo  
        Garcia, Hugo  
        3 total names in list  
*/  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="c03a8-112">Kompilieren des Codes</span><span class="sxs-lookup"><span data-stu-id="c03a8-112">Compiling the Code</span></span>  

 <span data-ttu-id="c03a8-113">Erstellen Sie ein C#-Konsolenanwendungsprojekt mit `using`-Anweisungen für die Namespaces „System.Linq“ und „System.IO“.</span><span class="sxs-lookup"><span data-stu-id="c03a8-113">Create a C# console application project, with `using` directives for the System.Linq and System.IO namespaces.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c03a8-114">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="c03a8-114">See also</span></span>

- [<span data-ttu-id="c03a8-115">LINQ und Zeichenfolgen (C#)</span><span class="sxs-lookup"><span data-stu-id="c03a8-115">LINQ and Strings (C#)</span></span>](./linq-and-strings.md)
- [<span data-ttu-id="c03a8-116">LINQ und Dateiverzeichnisse (C#)</span><span class="sxs-lookup"><span data-stu-id="c03a8-116">LINQ and File Directories (C#)</span></span>](./linq-and-file-directories.md)
