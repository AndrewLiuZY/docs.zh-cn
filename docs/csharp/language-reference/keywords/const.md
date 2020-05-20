---
title: const 关键字 - C# 参考
ms.date: 07/20/2015
f1_keywords:
- const_CSharpKeyword
- const
helpviewer_keywords:
- const keyword [C#]
ms.assetid: 79eb447c-117b-4418-933f-97c50aa472db
ms.openlocfilehash: 812aeb331b6dd333075d19076a896246ecc5b374
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/14/2020
ms.locfileid: "75713680"
---
# <a name="const-c-reference"></a><span data-ttu-id="c1a41-102">const（C# 参考）</span><span class="sxs-lookup"><span data-stu-id="c1a41-102">const (C# Reference)</span></span>

<span data-ttu-id="c1a41-103">使用 `const` 关键字来声明某个常量字段或常量局部变量。</span><span class="sxs-lookup"><span data-stu-id="c1a41-103">You use the `const` keyword to declare a constant field or a constant local.</span></span> <span data-ttu-id="c1a41-104">常量字段和常量局部变量不是变量并且不能修改。</span><span class="sxs-lookup"><span data-stu-id="c1a41-104">Constant fields and locals aren't variables and may not be modified.</span></span> <span data-ttu-id="c1a41-105">常量可以为数字、布尔值、字符串或 null 引用。</span><span class="sxs-lookup"><span data-stu-id="c1a41-105">Constants can be numbers, Boolean values, strings, or a null reference.</span></span> <span data-ttu-id="c1a41-106">不要创建常量来表示你需要随时更改的信息。</span><span class="sxs-lookup"><span data-stu-id="c1a41-106">Don’t create a constant to represent information that you expect to change at any time.</span></span> <span data-ttu-id="c1a41-107">例如，不要使用常量字段来存储服务的价格、产品版本号或公司的品牌名称。</span><span class="sxs-lookup"><span data-stu-id="c1a41-107">For example, don’t use a constant field to store the price of a service, a product version number, or the brand name of a company.</span></span> <span data-ttu-id="c1a41-108">这些值会随着时间发生变化；因为编译器会传播常量，所以必须重新编译通过库编译的其他代码以查看更改。</span><span class="sxs-lookup"><span data-stu-id="c1a41-108">These values can change over time, and because compilers propagate constants, other code compiled with your libraries will have to be recompiled to see the changes.</span></span> <span data-ttu-id="c1a41-109">另请参阅 [readonly](./readonly.md) 关键字。</span><span class="sxs-lookup"><span data-stu-id="c1a41-109">See also the [readonly](./readonly.md) keyword.</span></span> <span data-ttu-id="c1a41-110">例如:</span><span class="sxs-lookup"><span data-stu-id="c1a41-110">For example:</span></span>

```csharp
const int X = 0;
public const double GravitationalConstant = 6.673e-11;
private const string ProductName = "Visual C#";
```

## <a name="remarks"></a><span data-ttu-id="c1a41-111">备注</span><span class="sxs-lookup"><span data-stu-id="c1a41-111">Remarks</span></span>

<span data-ttu-id="c1a41-112">常数声明的类型指定声明引入的成员类型。</span><span class="sxs-lookup"><span data-stu-id="c1a41-112">The type of a constant declaration specifies the type of the members that the declaration introduces.</span></span> <span data-ttu-id="c1a41-113">常量局部变量或常量字段的初始值设定项必须是一个可以隐式转换为目标类型的常量表达式。</span><span class="sxs-lookup"><span data-stu-id="c1a41-113">The initializer of a constant local or a constant field must be a constant expression that can be implicitly converted to the target type.</span></span>

<span data-ttu-id="c1a41-114">常数表达式是在编译时可被完全计算的表达式。</span><span class="sxs-lookup"><span data-stu-id="c1a41-114">A constant expression is an expression that can be fully evaluated at compile time.</span></span> <span data-ttu-id="c1a41-115">因此，对于引用类型的常数，可能的值只能是 `string` 和 null 引用。</span><span class="sxs-lookup"><span data-stu-id="c1a41-115">Therefore, the only possible values for constants of reference types are `string` and a null reference.</span></span>

<span data-ttu-id="c1a41-116">常数声明可以声明多个常数，例如：</span><span class="sxs-lookup"><span data-stu-id="c1a41-116">The constant declaration can declare multiple constants, such as:</span></span>

```csharp
public const double X = 1.0, Y = 2.0, Z = 3.0;
```

<span data-ttu-id="c1a41-117">不允许在常数声明中使用 `static`{2}`static` 修饰符。</span><span class="sxs-lookup"><span data-stu-id="c1a41-117">The `static` modifier is not allowed in a constant declaration.</span></span>

<span data-ttu-id="c1a41-118">常数可以参与常数表达式，如下所示：</span><span class="sxs-lookup"><span data-stu-id="c1a41-118">A constant can participate in a constant expression, as follows:</span></span>

```csharp
public const int C1 = 5;
public const int C2 = C1 + 100;
```

> [!NOTE]
> <span data-ttu-id="c1a41-119">[readonly](./readonly.md) 关键字与 `const` 关键字不同。</span><span class="sxs-lookup"><span data-stu-id="c1a41-119">The [readonly](./readonly.md) keyword differs from the `const` keyword.</span></span> <span data-ttu-id="c1a41-120">`const`{2}`const` 字段只能在该字段的声明中初始化。</span><span class="sxs-lookup"><span data-stu-id="c1a41-120">A `const` field can only be initialized at the declaration of the field.</span></span> <span data-ttu-id="c1a41-121">`readonly`{2}`readonly` 字段可以在声明或构造函数中初始化。</span><span class="sxs-lookup"><span data-stu-id="c1a41-121">A `readonly` field can be initialized either at the declaration or in a constructor.</span></span> <span data-ttu-id="c1a41-122">因此，根据所使用的构造函数，`readonly`{2}`readonly` 字段可能具有不同的值。</span><span class="sxs-lookup"><span data-stu-id="c1a41-122">Therefore, `readonly` fields can have different values depending on the constructor used.</span></span> <span data-ttu-id="c1a41-123">另外，虽然 `const` 字段是编译时常量，但 `readonly` 字段可用于运行时常量，如此行所示：`public static readonly uint l1 = (uint)DateTime.Now.Ticks;`</span><span class="sxs-lookup"><span data-stu-id="c1a41-123">Also, although a `const` field is a compile-time constant, the `readonly` field can be used for run-time constants, as in this line: `public static readonly uint l1 = (uint)DateTime.Now.Ticks;`</span></span>

## <a name="example"></a><span data-ttu-id="c1a41-124">示例</span><span class="sxs-lookup"><span data-stu-id="c1a41-124">Example</span></span>

[!code-csharp[csrefKeywordsModifiers#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#5)]

## <a name="example"></a><span data-ttu-id="c1a41-125">示例</span><span class="sxs-lookup"><span data-stu-id="c1a41-125">Example</span></span>

<span data-ttu-id="c1a41-126">此示例说明如何将常数用作局部变量。</span><span class="sxs-lookup"><span data-stu-id="c1a41-126">This example demonstrates how to use constants as local variables.</span></span>

[!code-csharp[csrefKeywordsModifiers#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#6)]

## <a name="c-language-specification"></a><span data-ttu-id="c1a41-127">C# 语言规范</span><span class="sxs-lookup"><span data-stu-id="c1a41-127">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="c1a41-128">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c1a41-128">See also</span></span>

- [<span data-ttu-id="c1a41-129">C# 参考</span><span class="sxs-lookup"><span data-stu-id="c1a41-129">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="c1a41-130">C# 编程指南</span><span class="sxs-lookup"><span data-stu-id="c1a41-130">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="c1a41-131">C# 关键字</span><span class="sxs-lookup"><span data-stu-id="c1a41-131">C# Keywords</span></span>](./index.md)
- [<span data-ttu-id="c1a41-132">修饰符</span><span class="sxs-lookup"><span data-stu-id="c1a41-132">Modifiers</span></span>](index.md)
- [<span data-ttu-id="c1a41-133">readonly</span><span class="sxs-lookup"><span data-stu-id="c1a41-133">readonly</span></span>](./readonly.md)
