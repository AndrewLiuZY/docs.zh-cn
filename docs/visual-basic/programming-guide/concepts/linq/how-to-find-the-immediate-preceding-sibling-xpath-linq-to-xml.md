---
title: 如何：查找前面紧邻的同级 (XPath-LINQ to XML)
ms.date: 07/20/2015
ms.assetid: ec046283-9fe2-4440-b295-860bf700099d
ms.openlocfilehash: 8b0071b2f39b8debdd52083718fe928c1f9fb6f3
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84364521"
---
# <a name="how-to-find-the-immediate-preceding-sibling-xpath-linq-to-xml-visual-basic"></a>如何：查找紧前面的同级（XPath LINQ to XML）（Visual Basic）

有时，您需要查找某一节点的前面紧邻同级。 由于与 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 相比，XPath 中前面紧邻轴的位置谓词的语义同，因此这是一个更值得关注的比较。

## <a name="example"></a>示例

在本示例中，[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 查询使用 <xref:System.Linq.Enumerable.Last%2A> 运算符查找由 <xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A> 返回的集合中的最后一个节点。 相比之下，XPath 表达式使用值为 1 的谓词来查找前面紧邻的元素。

```vb
Dim root As XElement = _
    <Root>
        <Child1/>
        <Child2/>
        <Child3/>
        <Child4/>
    </Root>
Dim child4 As XElement = root.Element("Child4")

' LINQ to XML query
Dim el1 As XElement = child4.ElementsBeforeSelf().Last()

' XPath expression
Dim el2 As XElement = _
    DirectCast(child4.XPathEvaluate("preceding-sibling::*[1]"),  _
    IEnumerable).Cast(Of XElement)().First()

If el1 Is el2 Then
    Console.WriteLine("Results are identical")
Else
    Console.WriteLine("Results differ")
End If
Console.WriteLine(el1)
```

该示例产生下面的输出：

```console
Results are identical
<Child3 />
```

## <a name="see-also"></a>请参阅

- [XPath 用户的 LINQ to XML （Visual Basic）](linq-to-xml-for-xpath-users.md)
