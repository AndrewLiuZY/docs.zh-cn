---
title: 如何一次一行地读取文本文件 - C# 编程指南
ms.date: 07/20/2015
helpviewer_keywords:
- ReadLine method [C#]
- reading text files, line by line
- text files [C#]
ms.assetid: d62e22c5-a13c-48db-af9b-f10c801b0cb1
ms.openlocfilehash: e4a9ba2da2548991f442c2f5ab09d39243137875
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/14/2020
ms.locfileid: "79167502"
---
# <a name="how-to-read-a-text-file-one-line-at-a-time-c-programming-guide"></a>如何一次一行地读取文本文件（C# 编程指南）
此示例使用 `StreamReader` 类的 `ReadLine` 方法，一次一行地将文本文件内容读入字符串。 每个文本行都存储到字符串 `line` 中并显示在屏幕上。  
  
## <a name="example"></a>示例  
  
```csharp
int counter = 0;  
string line;  
  
// Read the file and display it line by line.  
System.IO.StreamReader file =
    new System.IO.StreamReader(@"c:\test.txt");  
while((line = file.ReadLine()) != null)  
{  
    System.Console.WriteLine(line);  
    counter++;  
}  
  
file.Close();  
System.Console.WriteLine("There were {0} lines.", counter);  
// Suspend the screen.  
System.Console.ReadLine();  
```  
  
## <a name="compiling-the-code"></a>编译代码  
 复制代码，并将其粘贴到控制台应用程序的 `Main` 方法中。  
  
 将 `"c:\test.txt"` 替换为实际文件名。  
  
## <a name="robust-programming"></a>可靠编程  
 以下情况可能会导致异常：  
  
- 文件可能不存在。  
  
## <a name="net-framework-security"></a>.NET Framework 安全性  
 不要根据文件的名称来判断文件的内容。 例如，文件 `myFile.cs` 可能不是 C# 源文件。  
  
## <a name="see-also"></a>另请参阅

- <xref:System.IO?displayProperty=nameWithType>
- [C# 编程指南](../index.md)
- [文件系统和注册表（C# 编程指南）](./index.md)
