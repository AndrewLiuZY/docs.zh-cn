---
title: 如何将 LINQ 查询与正则表达式合并 (C#)
ms.date: 07/20/2015
ms.assetid: 6b003b65-20a4-4ca2-929e-2ee3f215aecc
ms.openlocfilehash: 104e63adb9c07a75077b92654afd791b6c82d8de
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/14/2020
ms.locfileid: "79169424"
---
# <a name="how-to-combine-linq-queries-with-regular-expressions-c"></a><span data-ttu-id="90457-102">如何将 LINQ 查询与正则表达式合并 (C#)</span><span class="sxs-lookup"><span data-stu-id="90457-102">How to combine LINQ queries with regular expressions (C#)</span></span>
<span data-ttu-id="90457-103">此示例演示如何使用 <xref:System.Text.RegularExpressions.Regex> 类在文本字符串中为更复杂的匹配创建正则表达式。</span><span class="sxs-lookup"><span data-stu-id="90457-103">This example shows how to use the <xref:System.Text.RegularExpressions.Regex> class to create a regular expression for more complex matching in text strings.</span></span> <span data-ttu-id="90457-104">通过 LINQ 查询可以轻松地准确筛选要用正则表达式搜索的文件，并对结果进行改良。</span><span class="sxs-lookup"><span data-stu-id="90457-104">The LINQ query makes it easy to filter on exactly the files that you want to search with the regular expression, and to shape the results.</span></span>  
  
## <a name="example"></a><span data-ttu-id="90457-105">示例</span><span class="sxs-lookup"><span data-stu-id="90457-105">Example</span></span>  
  
```csharp  
class QueryWithRegEx  
{  
    public static void Main()  
    {  
        // Modify this path as necessary so that it accesses your version of Visual Studio.  
        string startFolder = @"C:\Program Files (x86)\Microsoft Visual Studio 14.0\";  
        // One of the following paths may be more appropriate on your computer.  
        //string startFolder = @"C:\Program Files (x86)\Microsoft Visual Studio\2017\";  
  
        // Take a snapshot of the file system.  
        IEnumerable<System.IO.FileInfo> fileList = GetFiles(startFolder);  
  
        // Create the regular expression to find all things "Visual".  
        System.Text.RegularExpressions.Regex searchTerm =  
            new System.Text.RegularExpressions.Regex(@"Visual (Basic|C#|C\+\+|Studio)");  
  
        // Search the contents of each .htm file.  
        // Remove the where clause to find even more matchedValues!  
        // This query produces a list of files where a match  
        // was found, and a list of the matchedValues in that file.  
        // Note: Explicit typing of "Match" in select clause.  
        // This is required because MatchCollection is not a
        // generic IEnumerable collection.  
        var queryMatchingFiles =  
            from file in fileList  
            where file.Extension == ".htm"  
            let fileText = System.IO.File.ReadAllText(file.FullName)  
            let matches = searchTerm.Matches(fileText)  
            where matches.Count > 0  
            select new  
            {  
                name = file.FullName,  
                matchedValues = from System.Text.RegularExpressions.Match match in matches  
                                select match.Value  
            };  
  
        // Execute the query.  
        Console.WriteLine("The term \"{0}\" was found in:", searchTerm.ToString());  
  
        foreach (var v in queryMatchingFiles)  
        {  
            // Trim the path a bit, then write
            // the file name in which a match was found.  
            string s = v.name.Substring(startFolder.Length - 1);  
            Console.WriteLine(s);  
  
            // For this file, write out all the matching strings  
            foreach (var v2 in v.matchedValues)  
            {  
                Console.WriteLine("  " + v2);  
            }  
        }  
  
        // Keep the console window open in debug mode  
        Console.WriteLine("Press any key to exit");  
        Console.ReadKey();  
    }  
  
    // This method assumes that the application has discovery
    // permissions for all folders under the specified path.  
    static IEnumerable<System.IO.FileInfo> GetFiles(string path)  
    {  
        if (!System.IO.Directory.Exists(path))  
            throw new System.IO.DirectoryNotFoundException();  
  
        string[] fileNames = null;  
        List<System.IO.FileInfo> files = new List<System.IO.FileInfo>();  
  
        fileNames = System.IO.Directory.GetFiles(path, "*.*", System.IO.SearchOption.AllDirectories);  
        foreach (string name in fileNames)  
        {  
            files.Add(new System.IO.FileInfo(name));  
        }  
        return files;  
    }  
}  
```  
  
 <span data-ttu-id="90457-106">请注意，还可以查询 `RegEx` 搜索返回的 <xref:System.Text.RegularExpressions.MatchCollection> 对象。</span><span class="sxs-lookup"><span data-stu-id="90457-106">Note that you can also query the <xref:System.Text.RegularExpressions.MatchCollection> object that is returned by a `RegEx` search.</span></span> <span data-ttu-id="90457-107">在本例中，只在结果中生成每个匹配项的值。</span><span class="sxs-lookup"><span data-stu-id="90457-107">In this example only the value of each match is produced in the results.</span></span> <span data-ttu-id="90457-108">但是，也可以使用 LINQ 对集合执行筛选、排序和分组等各种操作。</span><span class="sxs-lookup"><span data-stu-id="90457-108">However, it is also possible to use LINQ to perform all kinds of filtering, sorting, and grouping on that collection.</span></span> <span data-ttu-id="90457-109">由于 <xref:System.Text.RegularExpressions.MatchCollection> 为非泛型 <xref:System.Collections.IEnumerable> 集合，所以必须显式声明查询中范围变量的类型。</span><span class="sxs-lookup"><span data-stu-id="90457-109">Because <xref:System.Text.RegularExpressions.MatchCollection> is a non-generic <xref:System.Collections.IEnumerable> collection, you have to explicitly state the type of the range variable in the query.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="90457-110">编译代码</span><span class="sxs-lookup"><span data-stu-id="90457-110">Compiling the Code</span></span>  
 <span data-ttu-id="90457-111">使用 System.Linq 和 System.IO 命名空间的 `using` 指令创建 C# 控制台应用程序项目。</span><span class="sxs-lookup"><span data-stu-id="90457-111">Create a C# console application project with `using` directives for the System.Linq and System.IO namespaces.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="90457-112">另请参阅</span><span class="sxs-lookup"><span data-stu-id="90457-112">See also</span></span>

- [<span data-ttu-id="90457-113">LINQ 和字符串 (C#)</span><span class="sxs-lookup"><span data-stu-id="90457-113">LINQ and Strings (C#)</span></span>](./linq-and-strings.md)
- [<span data-ttu-id="90457-114">LINQ 和文件目录 (C#)</span><span class="sxs-lookup"><span data-stu-id="90457-114">LINQ and File Directories (C#)</span></span>](./linq-and-file-directories.md)
