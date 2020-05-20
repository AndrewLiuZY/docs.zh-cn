---
title: unsafe 关键字 - C# 参考
ms.date: 07/20/2015
f1_keywords:
- unsafe_CSharpKeyword
- unsafe
helpviewer_keywords:
- unsafe keyword [C#]
ms.assetid: 7e818009-1c6e-4b9e-b769-3728a01586a0
ms.openlocfilehash: ef98809eae0329c028dfb318c4a437aae4736db1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/14/2020
ms.locfileid: "75712983"
---
# <a name="unsafe-c-reference"></a><span data-ttu-id="31fe7-102">unsafe（C# 参考）</span><span class="sxs-lookup"><span data-stu-id="31fe7-102">unsafe (C# Reference)</span></span>

<span data-ttu-id="31fe7-103">`unsafe` 关键字表示不安全上下文，该上下文是任何涉及指针的操作所必需的。</span><span class="sxs-lookup"><span data-stu-id="31fe7-103">The `unsafe` keyword denotes an unsafe context, which is required for any operation involving pointers.</span></span> <span data-ttu-id="31fe7-104">有关详细信息，请参阅[不安全代码和指针](../../programming-guide/unsafe-code-pointers/index.md)。</span><span class="sxs-lookup"><span data-stu-id="31fe7-104">For more information, see [Unsafe Code and Pointers](../../programming-guide/unsafe-code-pointers/index.md).</span></span>

<span data-ttu-id="31fe7-105">可在类型或成员的声明中使用 `unsafe` 修饰符。</span><span class="sxs-lookup"><span data-stu-id="31fe7-105">You can use the `unsafe` modifier in the declaration of a type or a member.</span></span> <span data-ttu-id="31fe7-106">因此，类型或成员的整个正文范围均被视为不安全上下文。</span><span class="sxs-lookup"><span data-stu-id="31fe7-106">The entire textual extent of the type or member is therefore considered an unsafe context.</span></span> <span data-ttu-id="31fe7-107">以下面使用 `unsafe` 修饰符声明的方法为例：</span><span class="sxs-lookup"><span data-stu-id="31fe7-107">For example, the following is a method declared with the `unsafe` modifier:</span></span>

```csharp
unsafe static void FastCopy(byte[] src, byte[] dst, int count)
{
    // Unsafe context: can use pointers here.
}
```

<span data-ttu-id="31fe7-108">不安全上下文的范围从参数列表扩展到方法的结尾，因此也可在以下参数列表中使用指针：</span><span class="sxs-lookup"><span data-stu-id="31fe7-108">The scope of the unsafe context extends from the parameter list to the end of the method, so pointers can also be used in the parameter list:</span></span>

```csharp
unsafe static void FastCopy ( byte* ps, byte* pd, int count ) {...}
```

<span data-ttu-id="31fe7-109">还可以使用不安全块从而能够使用该块内的不安全代码。</span><span class="sxs-lookup"><span data-stu-id="31fe7-109">You can also use an unsafe block to enable the use of an unsafe code inside this block.</span></span> <span data-ttu-id="31fe7-110">例如:</span><span class="sxs-lookup"><span data-stu-id="31fe7-110">For example:</span></span>

```csharp
unsafe
{
    // Unsafe context: can use pointers here.
}
```

<span data-ttu-id="31fe7-111">要编译不安全代码，必须指定 [`-unsafe`](../compiler-options/unsafe-compiler-option.md) 编译器选项。</span><span class="sxs-lookup"><span data-stu-id="31fe7-111">To compile unsafe code, you must specify the [`-unsafe`](../compiler-options/unsafe-compiler-option.md) compiler option.</span></span> <span data-ttu-id="31fe7-112">不能通过公共语言运行时验证不安全代码。</span><span class="sxs-lookup"><span data-stu-id="31fe7-112">Unsafe code is not verifiable by the common language runtime.</span></span>

## <a name="example"></a><span data-ttu-id="31fe7-113">示例</span><span class="sxs-lookup"><span data-stu-id="31fe7-113">Example</span></span>

[!code-csharp[csrefKeywordsModifiers#22](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#22)]

## <a name="c-language-specification"></a><span data-ttu-id="31fe7-114">C# 语言规范</span><span class="sxs-lookup"><span data-stu-id="31fe7-114">C# language specification</span></span>

<span data-ttu-id="31fe7-115">有关详细信息，请参阅 [C# 语言规范](/dotnet/csharp/language-reference/language-specification/introduction)中的[不安全代码](~/_csharplang/spec/unsafe-code.md)。</span><span class="sxs-lookup"><span data-stu-id="31fe7-115">For more information, see [Unsafe code](~/_csharplang/spec/unsafe-code.md) in the [C# Language Specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span> <span data-ttu-id="31fe7-116">该语言规范是 C# 语法和用法的权威资料。</span><span class="sxs-lookup"><span data-stu-id="31fe7-116">The language specification is the definitive source for C# syntax and usage.</span></span>

## <a name="see-also"></a><span data-ttu-id="31fe7-117">另请参阅</span><span class="sxs-lookup"><span data-stu-id="31fe7-117">See also</span></span>

- [<span data-ttu-id="31fe7-118">C# 参考</span><span class="sxs-lookup"><span data-stu-id="31fe7-118">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="31fe7-119">C# 编程指南</span><span class="sxs-lookup"><span data-stu-id="31fe7-119">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="31fe7-120">C# 关键字</span><span class="sxs-lookup"><span data-stu-id="31fe7-120">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="31fe7-121">fixed 语句</span><span class="sxs-lookup"><span data-stu-id="31fe7-121">fixed Statement</span></span>](fixed-statement.md)
- [<span data-ttu-id="31fe7-122">不安全代码和指针</span><span class="sxs-lookup"><span data-stu-id="31fe7-122">Unsafe Code and Pointers</span></span>](../../programming-guide/unsafe-code-pointers/index.md)
- [<span data-ttu-id="31fe7-123">固定大小的缓冲区</span><span class="sxs-lookup"><span data-stu-id="31fe7-123">Fixed Size Buffers</span></span>](../../programming-guide/unsafe-code-pointers/fixed-size-buffers.md)
