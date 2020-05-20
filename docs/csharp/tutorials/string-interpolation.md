---
title: C# 中的字符串内插
description: 了解如何在 C# 中使用字符串插值将有格式的表达式结果包括在结果字符串中。
author: pkulikov
ms.technology: csharp-fundamentals
ms.date: 09/02/2019
ms.openlocfilehash: b901ae661ebd4af625d9f3c999b0eb50dda1990d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/14/2020
ms.locfileid: "73039214"
---
# <a name="string-interpolation-in-c"></a><span data-ttu-id="8b68b-103">C\# 中的字符串内插</span><span class="sxs-lookup"><span data-stu-id="8b68b-103">String interpolation in C\#</span></span>

<span data-ttu-id="8b68b-104">本教程演示如何使用[字符串插值](../language-reference/tokens/interpolated.md)设置表达式结果的格式并将其包含仅结果字符串中。</span><span class="sxs-lookup"><span data-stu-id="8b68b-104">This tutorial shows you how to use [string interpolation](../language-reference/tokens/interpolated.md) to format and include expression results in a result string.</span></span> <span data-ttu-id="8b68b-105">以下示例假设阅读者熟悉基础 C# 概念和 .NET 类型格式设置。</span><span class="sxs-lookup"><span data-stu-id="8b68b-105">The examples assume that you are familiar with basic C# concepts and .NET type formatting.</span></span> <span data-ttu-id="8b68b-106">如果不熟悉字符串插值或 .NET 类型格式设置，请先参阅[交互式字符串内插教程](exploration/interpolated-strings.yml)。</span><span class="sxs-lookup"><span data-stu-id="8b68b-106">If you are new to string interpolation or .NET type formatting, check out the [interactive string interpolation tutorial](exploration/interpolated-strings.yml) first.</span></span> <span data-ttu-id="8b68b-107">有关 .NET 中设置类型格式的详细信息，请参阅[设置 .NET 中类型的格式](../../standard/base-types/formatting-types.md)主题。</span><span class="sxs-lookup"><span data-stu-id="8b68b-107">For more information about formatting types in .NET, see the [Formatting Types in .NET](../../standard/base-types/formatting-types.md) topic.</span></span>

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

## <a name="introduction"></a><span data-ttu-id="8b68b-108">介绍</span><span class="sxs-lookup"><span data-stu-id="8b68b-108">Introduction</span></span>

<span data-ttu-id="8b68b-109">[字符串插值](../language-reference/tokens/interpolated.md)功能构建在[复合格式设置](../../standard/base-types/composite-formatting.md)功能的基础之上，提供更具有可读性、更方便的语法，用于将设置了格式的表达式结果包括到结果字符串。</span><span class="sxs-lookup"><span data-stu-id="8b68b-109">The [string interpolation](../language-reference/tokens/interpolated.md) feature is built on top of the [composite formatting](../../standard/base-types/composite-formatting.md) feature and provides a more readable and convenient syntax to include formatted expression results in a result string.</span></span>

<span data-ttu-id="8b68b-110">若要将字符串标识为内插字符串，可在该字符串前面加上 `$` 符号。</span><span class="sxs-lookup"><span data-stu-id="8b68b-110">To identify a string literal as an interpolated string, prepend it with the `$` symbol.</span></span> <span data-ttu-id="8b68b-111">可嵌入任何会在内插字符串中返回值的有效 C# 表达式。</span><span class="sxs-lookup"><span data-stu-id="8b68b-111">You can embed any valid C# expression that returns a value in an interpolated string.</span></span> <span data-ttu-id="8b68b-112">在以下示例中，对某个表达式执行计算后，其结果立即转换为一个字符串并包含到结果字符串中：</span><span class="sxs-lookup"><span data-stu-id="8b68b-112">In the following example, as soon as an expression is evaluated, its result is converted into a string and included in a result string:</span></span>

[!code-csharp-interactive[string interpolation example](~/samples/snippets/csharp/tutorials/string-interpolation/Program.cs#1)]

<span data-ttu-id="8b68b-113">如示例所示，通过将表达式用大括号括起来，可将表达式包含到内插字符串中：</span><span class="sxs-lookup"><span data-stu-id="8b68b-113">As the example shows, you include an expression in an interpolated string by enclosing it with braces:</span></span>

```csharp
{<interpolationExpression>}
```

<span data-ttu-id="8b68b-114">内插字符串支持[字符串复合格式设置](../../standard/base-types/composite-formatting.md)功能的所有功能。</span><span class="sxs-lookup"><span data-stu-id="8b68b-114">Interpolated strings support all the capabilities of the [string composite formatting](../../standard/base-types/composite-formatting.md) feature.</span></span> <span data-ttu-id="8b68b-115">这使得它们成为 <xref:System.String.Format%2A?displayProperty=nameWithType> 方法的更具可读性的替代选项。</span><span class="sxs-lookup"><span data-stu-id="8b68b-115">That makes them a more readable alternative to the use of the <xref:System.String.Format%2A?displayProperty=nameWithType> method.</span></span>

## <a name="how-to-specify-a-format-string-for-an-interpolation-expression"></a><span data-ttu-id="8b68b-116">如何为内插表达式指定格式字符串</span><span class="sxs-lookup"><span data-stu-id="8b68b-116">How to specify a format string for an interpolation expression</span></span>

<span data-ttu-id="8b68b-117">可通过在内插表达式后接冒号（“:”）和格式字符串来指定受表达式结果类型支持的格式字符串：</span><span class="sxs-lookup"><span data-stu-id="8b68b-117">You specify a format string that is supported by the type of the expression result by following the interpolation expression with a colon (":") and the format string:</span></span>

```csharp
{<interpolationExpression>:<formatString>}
```

<span data-ttu-id="8b68b-118">以下示例演示如何为生成日期和时间或数值结果的表达式指定标准和自定义格式字符串：</span><span class="sxs-lookup"><span data-stu-id="8b68b-118">The following example shows how to specify standard and custom format strings for expressions that produce date and time or numeric results:</span></span>

[!code-csharp-interactive[format string example](~/samples/snippets/csharp/tutorials/string-interpolation/Program.cs#2)]

<span data-ttu-id="8b68b-119">有关详细信息，请参阅[复合格式设置](../../standard/base-types/composite-formatting.md)主题的[格式字符串组件](../../standard/base-types/composite-formatting.md#format-string-component)章节。</span><span class="sxs-lookup"><span data-stu-id="8b68b-119">For more information, see the [Format String Component](../../standard/base-types/composite-formatting.md#format-string-component) section of the [Composite Formatting](../../standard/base-types/composite-formatting.md) topic.</span></span> <span data-ttu-id="8b68b-120">该部分提供主题链接，这些主题介绍 .NET 基类型支持的标准和自定义格式字符串。</span><span class="sxs-lookup"><span data-stu-id="8b68b-120">That section provides links to the topics that describe standard and custom format strings supported by .NET base types.</span></span>

## <a name="how-to-control-the-field-width-and-alignment-of-the-formatted-interpolation-expression"></a><span data-ttu-id="8b68b-121">如何控制设置了格式的内插表达式的字段宽度和对齐方式</span><span class="sxs-lookup"><span data-stu-id="8b68b-121">How to control the field width and alignment of the formatted interpolation expression</span></span>

<span data-ttu-id="8b68b-122">通过在内插表达式后添加逗号（“,”）和常数表达式来指定设置了格式的表达式结果的最小字段宽度和对齐方式：</span><span class="sxs-lookup"><span data-stu-id="8b68b-122">You specify the minimum field width and the alignment of the formatted expression result by following the interpolation expression with a comma (",") and the constant expression:</span></span>

```csharp
{<interpolationExpression>,<alignment>}
```

<span data-ttu-id="8b68b-123">如果对齐方式值为正，则设置了格式的表达式结果为右对齐，如果为负，则为左对齐  。</span><span class="sxs-lookup"><span data-stu-id="8b68b-123">If the *alignment* value is positive, the formatted expression result is right-aligned; if negative, it's left-aligned.</span></span>

<span data-ttu-id="8b68b-124">如果需要同时指定对齐方式和格式字符串，则先从对齐方式组件开始：</span><span class="sxs-lookup"><span data-stu-id="8b68b-124">If you need to specify both alignment and a format string, start with the alignment component:</span></span>

```csharp
{<interpolationExpression>,<alignment>:<formatString>}
```

<span data-ttu-id="8b68b-125">以下示例演示如何指定对齐方式并使用管道字符 ("|") 分隔文本字段：</span><span class="sxs-lookup"><span data-stu-id="8b68b-125">The following example shows how to specify alignment and uses pipe characters ("|") to delimit text fields:</span></span>

[!code-csharp-interactive[alignment example](~/samples/snippets/csharp/tutorials/string-interpolation/Program.cs#3)]

<span data-ttu-id="8b68b-126">如示例输出所示，如果已设置格式的表达式结果长度超出指定字段宽度，则忽略对齐方式值  。</span><span class="sxs-lookup"><span data-stu-id="8b68b-126">As the example output shows, if the length of the formatted expression result exceeds specified field width, the *alignment* value is ignored.</span></span>

<span data-ttu-id="8b68b-127">有关详细信息，请参阅[复合格式设置](../../standard/base-types/composite-formatting.md)主题的[对齐方式组件](../../standard/base-types/composite-formatting.md#alignment-component)部分。</span><span class="sxs-lookup"><span data-stu-id="8b68b-127">For more information, see the [Alignment Component](../../standard/base-types/composite-formatting.md#alignment-component) section of the [Composite Formatting](../../standard/base-types/composite-formatting.md) topic.</span></span>

## <a name="how-to-use-escape-sequences-in-an-interpolated-string"></a><span data-ttu-id="8b68b-128">如何在内插字符串中使用转义序列</span><span class="sxs-lookup"><span data-stu-id="8b68b-128">How to use escape sequences in an interpolated string</span></span>

<span data-ttu-id="8b68b-129">内插字符串支持所有可在普通字符串文本中使用的转义序列。</span><span class="sxs-lookup"><span data-stu-id="8b68b-129">Interpolated strings support all escape sequences that can be used in ordinary string literals.</span></span> <span data-ttu-id="8b68b-130">有关详细信息，请参阅[字符串转义序列](../programming-guide/strings/index.md#string-escape-sequences)。</span><span class="sxs-lookup"><span data-stu-id="8b68b-130">For more information, see [String escape sequences](../programming-guide/strings/index.md#string-escape-sequences).</span></span>

<span data-ttu-id="8b68b-131">若要逐字解释转义序列，可使用[逐字](../language-reference/tokens/verbatim.md)字符串文本。</span><span class="sxs-lookup"><span data-stu-id="8b68b-131">To interpret escape sequences literally, use a [verbatim](../language-reference/tokens/verbatim.md) string literal.</span></span> <span data-ttu-id="8b68b-132">内插逐字字符串以 `$` 字符开头，后跟 `@` 字符。</span><span class="sxs-lookup"><span data-stu-id="8b68b-132">An interpolated verbatim string starts with the `$` character followed by the `@` character.</span></span> <span data-ttu-id="8b68b-133">从 C# 8.0 开始，可以按任意顺序使用 `$` 和 `@` 标记：`$@"..."` 和 `@$"..."` 均为有效的内插逐字字符串。</span><span class="sxs-lookup"><span data-stu-id="8b68b-133">Starting with C# 8.0, you can use the `$` and `@` tokens in any order: both `$@"..."` and `@$"..."` are valid interpolated verbatim strings.</span></span>

<span data-ttu-id="8b68b-134">若要在结果字符串中包含大括号 "{" 或 "}"，请使用两个大括号 "{{" 或 "}}"。</span><span class="sxs-lookup"><span data-stu-id="8b68b-134">To include a brace, "{" or "}", in a result string, use two braces, "{{" or "}}".</span></span> <span data-ttu-id="8b68b-135">有关详细信息，请参阅[复合格式设置](../../standard/base-types/composite-formatting.md)主题的[转义括号](../../standard/base-types/composite-formatting.md#escaping-braces)部分。</span><span class="sxs-lookup"><span data-stu-id="8b68b-135">For more information, see the [Escaping Braces](../../standard/base-types/composite-formatting.md#escaping-braces) section of the [Composite Formatting](../../standard/base-types/composite-formatting.md) topic.</span></span>

<span data-ttu-id="8b68b-136">以下示例演示如何在结果字符串中包含大括号并构造逐字内插字符串：</span><span class="sxs-lookup"><span data-stu-id="8b68b-136">The following example shows how to include braces in a result string and construct a verbatim interpolated string:</span></span>

[!code-csharp-interactive[escape sequence example](~/samples/snippets/csharp/tutorials/string-interpolation/Program.cs#4)]

## <a name="how-to-use-a-ternary-conditional-operator--in-an-interpolation-expression"></a><span data-ttu-id="8b68b-137">如何在内插表达式中使用三元条件运算符 `?:`</span><span class="sxs-lookup"><span data-stu-id="8b68b-137">How to use a ternary conditional operator `?:` in an interpolation expression</span></span>

<span data-ttu-id="8b68b-138">因为冒号 (:) 在具有内插表达式的项中具有特殊含义，为了在表达式中使用[条件运算符](../language-reference/operators/conditional-operator.md)，请将表达式放在括号内，如下例所示：</span><span class="sxs-lookup"><span data-stu-id="8b68b-138">As the colon (":") has special meaning in an item with an interpolation expression, in order to use a [conditional operator](../language-reference/operators/conditional-operator.md) in an expression, enclose it in parentheses, as the following example shows:</span></span>

[!code-csharp-interactive[conditional operator example](~/samples/snippets/csharp/tutorials/string-interpolation/Program.cs#5)]

## <a name="how-to-create-a-culture-specific-result-string-with-string-interpolation"></a><span data-ttu-id="8b68b-139">如何使用字符串插值创建区域性特定的结果字符串</span><span class="sxs-lookup"><span data-stu-id="8b68b-139">How to create a culture-specific result string with string interpolation</span></span>

<span data-ttu-id="8b68b-140">默认情况下，内插字符串将 <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=nameWithType> 属性定义的当前区域性用于所有格式设置操作。</span><span class="sxs-lookup"><span data-stu-id="8b68b-140">By default, an interpolated string uses the current culture defined by the <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=nameWithType> property for all formatting operations.</span></span> <span data-ttu-id="8b68b-141">使用内插字符串到 <xref:System.FormattableString?displayProperty=nameWithType> 实例的隐式转换，并调用它的 <xref:System.FormattableString.ToString(System.IFormatProvider)> 方法来创建区域性特定的结果字符串。</span><span class="sxs-lookup"><span data-stu-id="8b68b-141">Use implicit conversion of an interpolated string to a <xref:System.FormattableString?displayProperty=nameWithType> instance and call its <xref:System.FormattableString.ToString(System.IFormatProvider)> method to create a culture-specific result string.</span></span> <span data-ttu-id="8b68b-142">下面的示例演示如何执行此操作：</span><span class="sxs-lookup"><span data-stu-id="8b68b-142">The following example shows how to do that:</span></span>

[!code-csharp-interactive[specify different cultures](~/samples/snippets/csharp/tutorials/string-interpolation/Program.cs#6)]

<span data-ttu-id="8b68b-143">如示例所示，可使用某个 <xref:System.FormattableString> 实例为各种区域性生成多个结果字符串。</span><span class="sxs-lookup"><span data-stu-id="8b68b-143">As the example shows, you can use one <xref:System.FormattableString> instance to generate multiple result strings for various cultures.</span></span>

## <a name="how-to-create-a-result-string-using-the-invariant-culture"></a><span data-ttu-id="8b68b-144">如何使用固定区域性创建结果字符串</span><span class="sxs-lookup"><span data-stu-id="8b68b-144">How to create a result string using the invariant culture</span></span>

<span data-ttu-id="8b68b-145">可配合 <xref:System.FormattableString.ToString(System.IFormatProvider)?displayProperty=nameWithType> 方法使用静态 <xref:System.FormattableString.Invariant%2A?displayProperty=nameWithType> 方法将内插字符串解析为 <xref:System.Globalization.CultureInfo.InvariantCulture> 的结果字符串。</span><span class="sxs-lookup"><span data-stu-id="8b68b-145">Along with the <xref:System.FormattableString.ToString(System.IFormatProvider)?displayProperty=nameWithType> method, you can use the static <xref:System.FormattableString.Invariant%2A?displayProperty=nameWithType> method to resolve an interpolated string to a result string for the <xref:System.Globalization.CultureInfo.InvariantCulture>.</span></span> <span data-ttu-id="8b68b-146">下面的示例演示如何执行此操作：</span><span class="sxs-lookup"><span data-stu-id="8b68b-146">The following example shows how to do that:</span></span>

[!code-csharp-interactive[format with invariant culture](~/samples/snippets/csharp/tutorials/string-interpolation/Program.cs#7)]

## <a name="conclusion"></a><span data-ttu-id="8b68b-147">结束语</span><span class="sxs-lookup"><span data-stu-id="8b68b-147">Conclusion</span></span>

<span data-ttu-id="8b68b-148">本教程介绍字符串插值用法的常见方案。</span><span class="sxs-lookup"><span data-stu-id="8b68b-148">This tutorial describes common scenarios of string interpolation usage.</span></span> <span data-ttu-id="8b68b-149">有关字符串插值的详细信息，请参阅[字符串插值](../language-reference/tokens/interpolated.md)主题。</span><span class="sxs-lookup"><span data-stu-id="8b68b-149">For more information about string interpolation, see the [String interpolation](../language-reference/tokens/interpolated.md) topic.</span></span> <span data-ttu-id="8b68b-150">有关 .NET 中设置类型格式的详细信息，请参阅[设置 .NET 中类型的格式](../../standard/base-types/formatting-types.md)和[复合格式设置](../../standard/base-types/composite-formatting.md)主题。</span><span class="sxs-lookup"><span data-stu-id="8b68b-150">For more information about formatting types in .NET, see the [Formatting Types in .NET](../../standard/base-types/formatting-types.md) and [Composite formatting](../../standard/base-types/composite-formatting.md) topics.</span></span>

## <a name="see-also"></a><span data-ttu-id="8b68b-151">另请参阅</span><span class="sxs-lookup"><span data-stu-id="8b68b-151">See also</span></span>

- <xref:System.String.Format%2A?displayProperty=nameWithType>
- <xref:System.FormattableString?displayProperty=nameWithType>
- <xref:System.IFormattable?displayProperty=nameWithType>
- [<span data-ttu-id="8b68b-152">字符串</span><span class="sxs-lookup"><span data-stu-id="8b68b-152">Strings</span></span>](../programming-guide/strings/index.md)
