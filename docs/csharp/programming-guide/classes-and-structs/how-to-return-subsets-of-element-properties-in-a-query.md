---
title: 如何在查询中返回元素属性的子集 - C# 编程指南
ms.date: 07/20/2015
helpviewer_keywords:
- anonymous types [C#], for subsets of element properties
ms.assetid: fabdf349-f443-4e3f-8368-6c471be1dd7b
ms.openlocfilehash: 27a2626fc46307a7195040adf746d8d8757d2f82
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/14/2020
ms.locfileid: "75714861"
---
# <a name="how-to-return-subsets-of-element-properties-in-a-query-c-programming-guide"></a>如何在查询中返回元素属性的子集（C# 编程指南）
当下列两个条件都满足时，可在查询表达式中使用匿名类型：  
  
- 只想返回每个源元素的某些属性。  
  
- 无需在执行查询的方法的范围之外存储查询结果。  
  
 如果只想从每个源元素中返回一个属性或字段，则只需在 `select` 子句中使用点运算符。 例如，若要只返回每个 `student` 的 `ID`，可以按如下方式编写 `select` 子句：  
  
```csharp  
select student.ID;  
```  
  
## <a name="example"></a>示例  
 下面的示例演示如何使用匿名类型只返回每个源元素的符合指定条件的属性子集。  
  
 [!code-csharp[csProgGuideLINQ#31](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csRef30LangFeatures_2.cs#31)]  
  
 请注意，如果未指定名称，匿名类型会使用源元素的名称作为其属性名称。 若要为匿名类型中的属性指定新名称，请按如下方式编写 `select` 语句：  
  
```csharp  
select new { First = student.FirstName, Last = student.LastName };  
```  
  
 如果在上一个示例中这样做，则 `Console.WriteLine` 语句也必须更改：  
  
```csharp  
Console.WriteLine(student.First + " " + student.Last);  
```  
  
## <a name="compiling-the-code"></a>编译代码  
  
要运行此代码，请使用 System.Linq 的 `using` 指令将该类复制并粘贴到 C# 控制台应用程序中。
  
## <a name="see-also"></a>另请参阅

- [C# 编程指南](../index.md)
- [匿名类型](./anonymous-types.md)
- [C# 中的 LINQ](../../linq/index.md)
