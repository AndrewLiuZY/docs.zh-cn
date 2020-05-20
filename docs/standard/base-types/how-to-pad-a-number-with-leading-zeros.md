---
title: 如何：用前导零填充数字
ms.date: 02/25/2019
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- numeric format strings [.NET Framework]
- formatting [.NET Framework], numbers
- number formatting [.NET Framework]
- numbers [.NET Framework], format strings
ms.assetid: 0b2c2cb5-c580-4891-8d81-cb632f5ec384
ms.openlocfilehash: bc3c4b75c484274c214141d8fbfcf8ac592b0b99
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/15/2020
ms.locfileid: "73131980"
---
# <a name="how-to-pad-a-number-with-leading-zeros"></a><span data-ttu-id="34894-102">如何：用前导零填充数字</span><span class="sxs-lookup"><span data-stu-id="34894-102">How to: Pad a Number with Leading Zeros</span></span>

<span data-ttu-id="34894-103">通过结合使用“D”[标准数字格式字符串](../../../docs/standard/base-types/standard-numeric-format-strings.md)和精度说明符，将前导零添加到整数。</span><span class="sxs-lookup"><span data-stu-id="34894-103">You can add leading zeros to an integer by using the "D" [standard numeric format string](../../../docs/standard/base-types/standard-numeric-format-strings.md) with a precision specifier.</span></span> <span data-ttu-id="34894-104">你可以通过使用[自定义数字格式字符串](../../../docs/standard/base-types/custom-numeric-format-strings.md)，将前导零添加到整数和浮点数。</span><span class="sxs-lookup"><span data-stu-id="34894-104">You can add leading zeros to both integer and floating-point numbers by using a [custom numeric format string](../../../docs/standard/base-types/custom-numeric-format-strings.md).</span></span> <span data-ttu-id="34894-105">本文介绍如何通过这两种方法用前导零填充数字。</span><span class="sxs-lookup"><span data-stu-id="34894-105">This article shows how to use both methods to pad a number with leading zeros.</span></span>

## <a name="to-pad-an-integer-with-leading-zeros-to-a-specific-length"></a><span data-ttu-id="34894-106">使用前导零将整数填充到特定的长度</span><span class="sxs-lookup"><span data-stu-id="34894-106">To pad an integer with leading zeros to a specific length</span></span>

1. <span data-ttu-id="34894-107">确定整数值要显示的最小位数。</span><span class="sxs-lookup"><span data-stu-id="34894-107">Determine the minimum number of digits you want the integer value to display.</span></span> <span data-ttu-id="34894-108">在此数字中包括任何前导位。</span><span class="sxs-lookup"><span data-stu-id="34894-108">Include any leading digits in this number.</span></span>

1. <span data-ttu-id="34894-109">确定是要将整数显示为十进制值还是十六进制值。</span><span class="sxs-lookup"><span data-stu-id="34894-109">Determine whether you want to display the integer as a decimal value or a hexadecimal value.</span></span>

    - <span data-ttu-id="34894-110">若要将整数显示为十进制值，则调用其 `ToString(String)` 方法，并传递字符串“Dn”作为 `format` 参数的值，其中 n 表示字符串的最小长度。</span><span class="sxs-lookup"><span data-stu-id="34894-110">To display the integer as a decimal value, call its `ToString(String)` method, and pass the string "D*n*" as the value of the `format` parameter, where *n* represents the minimum length of the string.</span></span>

    - <span data-ttu-id="34894-111">若要将整数显示为十六进制值，则调用其 `ToString(String)` 方法，并传递字符串“Xn  ”作为 format 参数的值，其中 n  表示字符串的最小长度。</span><span class="sxs-lookup"><span data-stu-id="34894-111">To display the integer as a hexadecimal value, call its `ToString(String)` method and pass the string "X*n*" as the value of the format parameter, where *n* represents the minimum length of the string.</span></span>

<span data-ttu-id="34894-112">此外，你也可以在 [C#](../../csharp/language-reference/tokens/interpolated.md) 和 [Visual Basic](../../visual-basic/programming-guide/language-features/strings/interpolated-strings.md) 的内插字符串中使用格式字符串，或者可以调用一个 <xref:System.String.Format%2A?displayProperty=nameWithType> 或 <xref:System.Console.WriteLine%2A?displayProperty=nameWithType> 等使用[复合格式设置](../../../docs/standard/base-types/composite-formatting.md)的方法。</span><span class="sxs-lookup"><span data-stu-id="34894-112">You can also use the format string in an interpolated string in both [C#](../../csharp/language-reference/tokens/interpolated.md) and [Visual Basic](../../visual-basic/programming-guide/language-features/strings/interpolated-strings.md), or you can call a method, such as <xref:System.String.Format%2A?displayProperty=nameWithType> or <xref:System.Console.WriteLine%2A?displayProperty=nameWithType>, that uses [composite formatting](../../../docs/standard/base-types/composite-formatting.md).</span></span>

<span data-ttu-id="34894-113">以下示例使用前导零设置若干整数值的格式，以便格式化数字的总长度至少为八个字符。</span><span class="sxs-lookup"><span data-stu-id="34894-113">The following example formats several integer values with leading zeros so that the total length of the formatted number is at least eight characters.</span></span>

[!code-csharp[Formatting.HowTo.PadNumber#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.PadNumber/cs/Pad1.cs#1)]
[!code-vb[Formatting.HowTo.PadNumber#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.PadNumber/vb/Pad1.vb#1)]

## <a name="to-pad-an-integer-with-a-specific-number-of-leading-zeros"></a><span data-ttu-id="34894-114">使用特定数目的前导零填充整数</span><span class="sxs-lookup"><span data-stu-id="34894-114">To pad an integer with a specific number of leading zeros</span></span>

1. <span data-ttu-id="34894-115">确定希望整数值显示多少个前导零。</span><span class="sxs-lookup"><span data-stu-id="34894-115">Determine how many leading zeros you want the integer value to display.</span></span>

1. <span data-ttu-id="34894-116">确定是要将整数显示为十进制值还是十六进制值。</span><span class="sxs-lookup"><span data-stu-id="34894-116">Determine whether you want to display the integer as a decimal value or a hexadecimal value.</span></span>

    - <span data-ttu-id="34894-117">将其格式设置为十进制值需要使用“D”标准格式说明符。</span><span class="sxs-lookup"><span data-stu-id="34894-117">Formatting it as a decimal value requires that you use the "D" standard format specifier.</span></span>

    - <span data-ttu-id="34894-118">将其格式设置为十六进制值需要使用“X”标准格式说明符。</span><span class="sxs-lookup"><span data-stu-id="34894-118">Formatting it as a hexadecimal value requires that you use the "X" standard format specifier.</span></span>

1. <span data-ttu-id="34894-119">通过调用整数值的 `ToString("D").Length` 或 `ToString("X").Length` 方法，确定未填充的数字字符串的长度。</span><span class="sxs-lookup"><span data-stu-id="34894-119">Determine the length of the unpadded numeric string by calling the integer value's `ToString("D").Length` or `ToString("X").Length` method.</span></span>

1. <span data-ttu-id="34894-120">将你要在格式化字符串中包括的前导零的数目添加到未填充的数字字符串的长度上。</span><span class="sxs-lookup"><span data-stu-id="34894-120">Add the number of leading zeros that you want to include in the formatted string to the length of the unpadded numeric string.</span></span> <span data-ttu-id="34894-121">添加前导零的个数将定义填充字符串的总长度。</span><span class="sxs-lookup"><span data-stu-id="34894-121">Adding the number of leading zeros defines the total length of the padded string.</span></span>

1. <span data-ttu-id="34894-122">调用整数值的 `ToString(String)` 方法，并且对于十进制字符串传递字符串“Dn  ”，对于十六进制字符串传递“Xn  ”；其中，n  表示填充的字符串的总长度。</span><span class="sxs-lookup"><span data-stu-id="34894-122">Call the integer value's `ToString(String)` method, and pass the string "D*n*" for decimal strings and "X*n*" for hexadecimal strings, where *n* represents the total length of the padded string.</span></span> <span data-ttu-id="34894-123">也可以在支持复合格式设置的方法中使用“Dn  ”或“Xn  ”格式字符串。</span><span class="sxs-lookup"><span data-stu-id="34894-123">You can also use the "D*n*" or "X*n*" format string in a method that supports composite formatting.</span></span>

<span data-ttu-id="34894-124">下面的示例使用五个前导零来填充整数值。</span><span class="sxs-lookup"><span data-stu-id="34894-124">The following example pads an integer value with five leading zeros.</span></span>

[!code-csharp[Formatting.HowTo.PadNumber#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.PadNumber/cs/Pad1.cs#2)]
[!code-vb[Formatting.HowTo.PadNumber#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.PadNumber/vb/Pad1.vb#2)]

## <a name="to-pad-a-numeric-value-with-leading-zeros-to-a-specific-length"></a><span data-ttu-id="34894-125">使用前导零将数值填充到特定的长度</span><span class="sxs-lookup"><span data-stu-id="34894-125">To pad a numeric value with leading zeros to a specific length</span></span>

1. <span data-ttu-id="34894-126">确定数字的字符串表示形式要在小数点的左侧保留的位数。</span><span class="sxs-lookup"><span data-stu-id="34894-126">Determine how many digits to the left of the decimal you want the string representation of the number to have.</span></span> <span data-ttu-id="34894-127">在此总位数中包括任何前导零。</span><span class="sxs-lookup"><span data-stu-id="34894-127">Include any leading zeros in this total number of digits.</span></span>

1. <span data-ttu-id="34894-128">定义一个使用零占位符“0”来表示零的最小数目的自定义数字格式字符串。</span><span class="sxs-lookup"><span data-stu-id="34894-128">Define a custom numeric format string that uses the zero placeholder "0" to represent the minimum number of zeros.</span></span>

1. <span data-ttu-id="34894-129">调用数字的 `ToString(String)` 方法并向其传递自定义格式字符串。</span><span class="sxs-lookup"><span data-stu-id="34894-129">Call the number's `ToString(String)` method and pass it the custom format string.</span></span> <span data-ttu-id="34894-130">此外，你也可以将自定义格式字符串与字符串内插或与支持复合格式设置的方法一起使用。</span><span class="sxs-lookup"><span data-stu-id="34894-130">You can also use the custom format string with string interpolation or with a method that supports composite formatting.</span></span>

<span data-ttu-id="34894-131">下面的示例使用前导零设置几个数值的格式。</span><span class="sxs-lookup"><span data-stu-id="34894-131">The following example formats several numeric values with leading zeros.</span></span> <span data-ttu-id="34894-132">因此，格式化后的数字总长度是小数点左侧至少八位数字。</span><span class="sxs-lookup"><span data-stu-id="34894-132">As a result, the total length of the formatted number is at least eight digits to the left of the decimal.</span></span>

[!code-csharp[Formatting.HowTo.PadNumber#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.PadNumber/cs/Pad1.cs#3)]
[!code-vb[Formatting.HowTo.PadNumber#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.PadNumber/vb/Pad1.vb#3)]

## <a name="to-pad-a-numeric-value-with-a-specific-number-of-leading-zeros"></a><span data-ttu-id="34894-133">使用特定数目的前导零填充数值</span><span class="sxs-lookup"><span data-stu-id="34894-133">To pad a numeric value with a specific number of leading zeros</span></span>

1. <span data-ttu-id="34894-134">确定希望数值具有多少个前导零。</span><span class="sxs-lookup"><span data-stu-id="34894-134">Determine how many leading zeros you want the numeric value to have.</span></span>

1. <span data-ttu-id="34894-135">确定未填充数字字符串中小数点左侧的位数：</span><span class="sxs-lookup"><span data-stu-id="34894-135">Determine the number of digits to the left of the decimal in the unpadded numeric string:</span></span>

    1. <span data-ttu-id="34894-136">确定数字的字符串表示形式是否包括小数点符号。</span><span class="sxs-lookup"><span data-stu-id="34894-136">Determine whether the string representation of a number includes a decimal point symbol.</span></span>

    1. <span data-ttu-id="34894-137">如果它包括小数点符号，则确定小数点左侧的字符数。</span><span class="sxs-lookup"><span data-stu-id="34894-137">If it does include a decimal point symbol, determine the number of characters to the left of the decimal point.</span></span>

         <span data-ttu-id="34894-138">或</span><span class="sxs-lookup"><span data-stu-id="34894-138">-or-</span></span>

         <span data-ttu-id="34894-139">如果它不包括小数点符号，则确定字符串的长度。</span><span class="sxs-lookup"><span data-stu-id="34894-139">If it doesn't include a decimal point symbol, determine the string's length.</span></span>

1. <span data-ttu-id="34894-140">创建使用以下格式的自定义格式字符串：</span><span class="sxs-lookup"><span data-stu-id="34894-140">Create a custom format string that uses:</span></span>

    - <span data-ttu-id="34894-141">零占位符“0”表示在字符串中出现的每个前导零。</span><span class="sxs-lookup"><span data-stu-id="34894-141">The zero placeholder "0" for each of the leading zeros to appear in the string.</span></span>

    - <span data-ttu-id="34894-142">零占位符或数字占位符“#”表示默认字符串中的每个数字。</span><span class="sxs-lookup"><span data-stu-id="34894-142">Either the zero placeholder or the digit placeholder "#" to represent each digit in the default string.</span></span>

1. <span data-ttu-id="34894-143">将自定义格式字符串作为对数字的 `ToString(String)` 方法或支持复合格式设置的方法的参数提供。</span><span class="sxs-lookup"><span data-stu-id="34894-143">Supply the custom format string as a parameter either to the number's `ToString(String)` method or to a method that supports composite formatting.</span></span>

<span data-ttu-id="34894-144">下面的示例使用五个前导零来填充两个 <xref:System.Double> 值。</span><span class="sxs-lookup"><span data-stu-id="34894-144">The following example pads two <xref:System.Double> values with five leading zeros.</span></span>

[!code-csharp[Formatting.HowTo.PadNumber#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.PadNumber/cs/Pad1.cs#4)]
[!code-vb[Formatting.HowTo.PadNumber#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.PadNumber/vb/Pad1.vb#4)]

## <a name="see-also"></a><span data-ttu-id="34894-145">另请参阅</span><span class="sxs-lookup"><span data-stu-id="34894-145">See also</span></span>

- [<span data-ttu-id="34894-146">自定义数字格式字符串</span><span class="sxs-lookup"><span data-stu-id="34894-146">Custom Numeric Format Strings</span></span>](../../../docs/standard/base-types/custom-numeric-format-strings.md)
- [<span data-ttu-id="34894-147">标准数字格式字符串</span><span class="sxs-lookup"><span data-stu-id="34894-147">Standard Numeric Format Strings</span></span>](../../../docs/standard/base-types/standard-numeric-format-strings.md)
- [<span data-ttu-id="34894-148">复合格式设置</span><span class="sxs-lookup"><span data-stu-id="34894-148">Composite Formatting</span></span>](../../../docs/standard/base-types/composite-formatting.md)
