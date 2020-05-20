---
title: protected 关键字 - C# 参考
ms.date: 07/20/2015
f1_keywords:
- protected
- protected_CSharpKeyword
helpviewer_keywords:
- protected keyword [C#]
ms.assetid: 05ce3794-6675-4025-bddb-eaaa0ec22892
ms.openlocfilehash: bec619d4f49bd26daa742c18c830909c14948adf
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/14/2020
ms.locfileid: "75713178"
---
# <a name="protected-c-reference"></a><span data-ttu-id="8c82a-102">protected（C# 参考）</span><span class="sxs-lookup"><span data-stu-id="8c82a-102">protected (C# Reference)</span></span>

<span data-ttu-id="8c82a-103">`protected` 关键字是一个成员访问修饰符。</span><span class="sxs-lookup"><span data-stu-id="8c82a-103">The `protected` keyword is a member access modifier.</span></span>

 > <span data-ttu-id="8c82a-104">本页涵盖 `protected` 访问。</span><span class="sxs-lookup"><span data-stu-id="8c82a-104">This page covers `protected` access.</span></span> <span data-ttu-id="8c82a-105">`protected` 关键字也属于 [`protected internal`](protected-internal.md) 和 [`private protected`](private-protected.md) 访问修饰符。</span><span class="sxs-lookup"><span data-stu-id="8c82a-105">The `protected` keyword is also part of the [`protected internal`](protected-internal.md) and [`private protected`](private-protected.md) access modifiers.</span></span>

<span data-ttu-id="8c82a-106">受保护成员在其所在的类中可由派生类实例访问。</span><span class="sxs-lookup"><span data-stu-id="8c82a-106">A protected member is accessible within its class and by derived class instances.</span></span>

<span data-ttu-id="8c82a-107">有关 `protected` 和其他访问修饰符的比较，请参阅[可访问性级别](accessibility-levels.md)。</span><span class="sxs-lookup"><span data-stu-id="8c82a-107">For a comparison of `protected` with the other access modifiers, see [Accessibility Levels](accessibility-levels.md).</span></span>

## <a name="example"></a><span data-ttu-id="8c82a-108">示例</span><span class="sxs-lookup"><span data-stu-id="8c82a-108">Example</span></span>

<span data-ttu-id="8c82a-109">只有在通过派生类类型进行访问时，基类的受保护成员在派生类中才是可访问的。</span><span class="sxs-lookup"><span data-stu-id="8c82a-109">A protected member of a base class is accessible in a derived class only if the access occurs through the derived class type.</span></span> <span data-ttu-id="8c82a-110">以下面的代码段为例：</span><span class="sxs-lookup"><span data-stu-id="8c82a-110">For example, consider the following code segment:</span></span>

[!code-csharp[csrefKeywordsModifiers#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#11)]

<span data-ttu-id="8c82a-111">语句 `a.x = 10` 生成错误，因为它是在静态方法 Main 中生成的，而不是类 B 的实例。</span><span class="sxs-lookup"><span data-stu-id="8c82a-111">The statement `a.x = 10` generates an error because it is made within the static method Main, and not an instance of class B.</span></span>

<span data-ttu-id="8c82a-112">无法保护结构成员，因为无法继承结构。</span><span class="sxs-lookup"><span data-stu-id="8c82a-112">Struct members cannot be protected because the struct cannot be inherited.</span></span>

## <a name="example"></a><span data-ttu-id="8c82a-113">示例</span><span class="sxs-lookup"><span data-stu-id="8c82a-113">Example</span></span>

<span data-ttu-id="8c82a-114">在此示例中，`DerivedPoint` 类是从 `Point` 派生的。</span><span class="sxs-lookup"><span data-stu-id="8c82a-114">In this example, the class `DerivedPoint` is derived from `Point`.</span></span> <span data-ttu-id="8c82a-115">因此，可以从派生类直接访问基类的受保护成员。</span><span class="sxs-lookup"><span data-stu-id="8c82a-115">Therefore, you can access the protected members of the base class directly from the derived class.</span></span>

[!code-csharp[csrefKeywordsModifiers#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#12)]  

<span data-ttu-id="8c82a-116">如果将 `x` 和 `y` 的访问级别更改为 [private](private.md)，编译器将发出错误消息：</span><span class="sxs-lookup"><span data-stu-id="8c82a-116">If you change the access levels of `x` and `y` to [private](private.md), the compiler will issue the error messages:</span></span>

`'Point.y' is inaccessible due to its protection level.`

`'Point.x' is inaccessible due to its protection level.`

## <a name="c-language-specification"></a><span data-ttu-id="8c82a-117">C# 语言规范</span><span class="sxs-lookup"><span data-stu-id="8c82a-117">C# language specification</span></span>  

<span data-ttu-id="8c82a-118">有关详细信息，请参阅 [C# 语言规范](/dotnet/csharp/language-reference/language-specification/introduction)中的[声明的可访问性](~/_csharplang/spec/basic-concepts.md#declared-accessibility)。</span><span class="sxs-lookup"><span data-stu-id="8c82a-118">For more information, see [Declared accessibility](~/_csharplang/spec/basic-concepts.md#declared-accessibility) in the [C# Language Specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span> <span data-ttu-id="8c82a-119">该语言规范是 C# 语法和用法的权威资料。</span><span class="sxs-lookup"><span data-stu-id="8c82a-119">The language specification is the definitive source for C# syntax and usage.</span></span>

## <a name="see-also"></a><span data-ttu-id="8c82a-120">另请参阅</span><span class="sxs-lookup"><span data-stu-id="8c82a-120">See also</span></span>

- [<span data-ttu-id="8c82a-121">C# 参考</span><span class="sxs-lookup"><span data-stu-id="8c82a-121">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="8c82a-122">C# 编程指南</span><span class="sxs-lookup"><span data-stu-id="8c82a-122">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="8c82a-123">C# 关键字</span><span class="sxs-lookup"><span data-stu-id="8c82a-123">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="8c82a-124">访问修饰符</span><span class="sxs-lookup"><span data-stu-id="8c82a-124">Access Modifiers</span></span>](access-modifiers.md)
- [<span data-ttu-id="8c82a-125">可访问性级别</span><span class="sxs-lookup"><span data-stu-id="8c82a-125">Accessibility Levels</span></span>](accessibility-levels.md)
- [<span data-ttu-id="8c82a-126">修饰符</span><span class="sxs-lookup"><span data-stu-id="8c82a-126">Modifiers</span></span>](index.md)
- [<span data-ttu-id="8c82a-127">public</span><span class="sxs-lookup"><span data-stu-id="8c82a-127">public</span></span>](public.md)
- [<span data-ttu-id="8c82a-128">private</span><span class="sxs-lookup"><span data-stu-id="8c82a-128">private</span></span>](private.md)
- [<span data-ttu-id="8c82a-129">内部</span><span class="sxs-lookup"><span data-stu-id="8c82a-129">internal</span></span>](internal.md)
- <span data-ttu-id="8c82a-130">[Internal Virtual 关键字的安全问题](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/heyd8kky(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="8c82a-130">[Security concerns for internal virtual keywords](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/heyd8kky(v=vs.100))</span></span>
