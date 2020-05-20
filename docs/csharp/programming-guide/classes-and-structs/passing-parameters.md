---
title: 传递参数 - C# 编程指南
ms.date: 07/20/2015
helpviewer_keywords:
- parameters [C#], passing
- passing parameters [C#]
- arguments [C#]
- methods [C#], passing parameters
- C# language, method parameters
ms.assetid: a5c3003f-7441-4710-b8b1-c79de77e0b77
ms.openlocfilehash: 60ac7a8d982e7788f07debce114896859385c8e2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/14/2020
ms.locfileid: "75705465"
---
# <a name="passing-parameters-c-programming-guide"></a><span data-ttu-id="0e99d-102">传递参数（C# 编程指南）</span><span class="sxs-lookup"><span data-stu-id="0e99d-102">Passing Parameters (C# Programming Guide)</span></span>
<span data-ttu-id="0e99d-103">在 C# 中，实参可以按值或按引用传递给形参。</span><span class="sxs-lookup"><span data-stu-id="0e99d-103">In C#, arguments can be passed to parameters either by value or by reference.</span></span> <span data-ttu-id="0e99d-104">按引用传递使函数成员、方法、属性、索引器、运算符和构造函数可以更改参数的值，并让该更改在调用环境中保持。</span><span class="sxs-lookup"><span data-stu-id="0e99d-104">Passing by reference enables function members, methods, properties, indexers, operators, and constructors to change the value of the parameters and have that change persist in the calling environment.</span></span> <span data-ttu-id="0e99d-105">若要按引用传递参数，且具有更改值的意向，请使用 `ref` 或 `out` 关键字。</span><span class="sxs-lookup"><span data-stu-id="0e99d-105">To pass a parameter by reference with the intent of changing the value, use the `ref`, or `out` keyword.</span></span> <span data-ttu-id="0e99d-106">若要按引用传递，且只有避免复制而不更改值的意向，请使用 `in` 修饰符。</span><span class="sxs-lookup"><span data-stu-id="0e99d-106">To pass by reference with the intent of avoiding copying but not changing the value, use the `in` modifier.</span></span> <span data-ttu-id="0e99d-107">为简单起见，本主题的示例中只使用 `ref` 关键字。</span><span class="sxs-lookup"><span data-stu-id="0e99d-107">For simplicity, only the `ref` keyword is used in the examples in this topic.</span></span> <span data-ttu-id="0e99d-108">有关 `in`、`ref` 和 `out` 之间差异的详细信息，请参阅 [in](../../language-reference/keywords/in-parameter-modifier.md)、[ref](../../language-reference/keywords/ref.md) 及 [out](../../language-reference/keywords/out-parameter-modifier.md)。</span><span class="sxs-lookup"><span data-stu-id="0e99d-108">For more information about the difference between `in`, `ref`, and `out`, see [in](../../language-reference/keywords/in-parameter-modifier.md), [ref](../../language-reference/keywords/ref.md), and [out](../../language-reference/keywords/out-parameter-modifier.md).</span></span>  
  
 <span data-ttu-id="0e99d-109">以下示例演示值与引用参数之间的差异。</span><span class="sxs-lookup"><span data-stu-id="0e99d-109">The following example illustrates the difference between value and reference parameters.</span></span>  
  
 [!code-csharp[csProgGuideParameters#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideParameters/CS/Parameters.cs#10)]  
  
 <span data-ttu-id="0e99d-110">有关详细信息，请参阅下列主题：</span><span class="sxs-lookup"><span data-stu-id="0e99d-110">For more information, see the following topics:</span></span>  
  
- [<span data-ttu-id="0e99d-111">传递值类型参数</span><span class="sxs-lookup"><span data-stu-id="0e99d-111">Passing Value-Type Parameters</span></span>](./passing-value-type-parameters.md)  
  
- [<span data-ttu-id="0e99d-112">传递引用类型参数</span><span class="sxs-lookup"><span data-stu-id="0e99d-112">Passing Reference-Type Parameters</span></span>](./passing-reference-type-parameters.md)  
  
## <a name="c-language-specification"></a><span data-ttu-id="0e99d-113">C# 语言规范</span><span class="sxs-lookup"><span data-stu-id="0e99d-113">C# Language Specification</span></span>  

<span data-ttu-id="0e99d-114">有关详细信息，请参阅 [C# 语言规范](/dotnet/csharp/language-reference/language-specification/introduction)中的[参数列表](~/_csharplang/spec/expressions.md#argument-lists)。</span><span class="sxs-lookup"><span data-stu-id="0e99d-114">For more information, see [Argument lists](~/_csharplang/spec/expressions.md#argument-lists) in the [C# Language Specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span> <span data-ttu-id="0e99d-115">该语言规范是 C# 语法和用法的权威资料。</span><span class="sxs-lookup"><span data-stu-id="0e99d-115">The language specification is the definitive source for C# syntax and usage.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="0e99d-116">另请参阅</span><span class="sxs-lookup"><span data-stu-id="0e99d-116">See also</span></span>

- [<span data-ttu-id="0e99d-117">C# 编程指南</span><span class="sxs-lookup"><span data-stu-id="0e99d-117">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="0e99d-118">方法</span><span class="sxs-lookup"><span data-stu-id="0e99d-118">Methods</span></span>](./methods.md)
