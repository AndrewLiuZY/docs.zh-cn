---
title: .NET 正则表达式中的字符类
description: 了解如何使用字符类表示 .NET 正则表达式中的一组字符。
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- character classes
- regular expressions, character classes
- characters, matching syntax
- .NET Framework regular expressions, character classes
ms.assetid: 0f8bffab-ee0d-4e0e-9a96-2b4a252bb7e4
ms.openlocfilehash: 07bd63c90bc8d78c9831e2007695a232a85111b1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/15/2020
ms.locfileid: "78159333"
---
# <a name="character-classes-in-regular-expressions"></a><span data-ttu-id="7e8f8-103">正则表达式中的字符类</span><span class="sxs-lookup"><span data-stu-id="7e8f8-103">Character classes in regular expressions</span></span>

<span data-ttu-id="7e8f8-104">一个字符类定义一组字符，其中的任一字符均可出现在输入字符串中以便成功匹配。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-104">A character class defines a set of characters, any one of which can occur in an input string for a match to succeed.</span></span> <span data-ttu-id="7e8f8-105">.NET 中的正则表达式语言支持以下字符类：</span><span class="sxs-lookup"><span data-stu-id="7e8f8-105">The regular expression language in .NET supports the following character classes:</span></span>  
  
- <span data-ttu-id="7e8f8-106">正字符组。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-106">Positive character groups.</span></span> <span data-ttu-id="7e8f8-107">输入字符串中的字符必须匹配一组指定的字符中的某个字符。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-107">A character in the input string must match one of a specified set of characters.</span></span> <span data-ttu-id="7e8f8-108">有关详细信息，请参阅[正字符组](#PositiveGroup)。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-108">For more information, see [Positive Character Group](#PositiveGroup).</span></span>  
  
- <span data-ttu-id="7e8f8-109">负字符组。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-109">Negative character groups.</span></span> <span data-ttu-id="7e8f8-110">输入字符串中的字符不得匹配一组指定的字符中的某个字符。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-110">A character in the input string must not match one of a specified set of characters.</span></span> <span data-ttu-id="7e8f8-111">有关详细信息，请参阅[负字符组](#NegativeGroup)。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-111">For more information, see [Negative Character Group](#NegativeGroup).</span></span>  
  
- <span data-ttu-id="7e8f8-112">任意字符。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-112">Any character.</span></span> <span data-ttu-id="7e8f8-113">正则表达式中的 `.`（圆点或句点）字符是匹配除 `\n` 之外的任何字符的通配符字符。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-113">The `.` (dot or period) character in a regular expression is a wildcard character that matches any character except `\n`.</span></span> <span data-ttu-id="7e8f8-114">有关详细信息，请参阅[任意字符](#AnyCharacter)。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-114">For more information, see [Any Character](#AnyCharacter).</span></span>  
  
- <span data-ttu-id="7e8f8-115">通用 Unicode 类别或命名块。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-115">A general Unicode category or named block.</span></span> <span data-ttu-id="7e8f8-116">输入字符串中的字符必须为特定 Unicode 类别的成员，或必须位于一系列连续的 Unicode 字符中才能成功匹配。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-116">A character in the input string must be a member of a particular Unicode category or must fall within a contiguous range of Unicode characters for a match to succeed.</span></span> <span data-ttu-id="7e8f8-117">有关详细信息，请参阅 [Unicode 类别或 Unicode 块](#CategoryOrBlock)。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-117">For more information, see [Unicode Category or Unicode Block](#CategoryOrBlock).</span></span>  
  
- <span data-ttu-id="7e8f8-118">负通用 Unicode 类别或命名块。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-118">A negative general Unicode category or named block.</span></span> <span data-ttu-id="7e8f8-119">输入字符串中的字符不得为特定 Unicode 类别的成员，也不得位于一系列连续的 Unicode 字符中以便成功匹配。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-119">A character in the input string must not be a member of a particular Unicode category or must not fall within a contiguous range of Unicode characters for a match to succeed.</span></span> <span data-ttu-id="7e8f8-120">有关详细信息，请参阅[负 Unicode 类别或 Unicode 块](#NegativeCategoryOrBlock)。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-120">For more information, see [Negative Unicode Category or Unicode Block](#NegativeCategoryOrBlock).</span></span>  
  
- <span data-ttu-id="7e8f8-121">单词字符。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-121">A word character.</span></span> <span data-ttu-id="7e8f8-122">输入字符串中的字符可以属于适合单词中字符的任何 Unicode 类别。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-122">A character in the input string can belong to any of the Unicode categories that are appropriate for characters in words.</span></span> <span data-ttu-id="7e8f8-123">有关详细信息，请参阅[单词字符](#WordCharacter)。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-123">For more information, see [Word Character](#WordCharacter).</span></span>  
  
- <span data-ttu-id="7e8f8-124">非单词字符。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-124">A non-word character.</span></span> <span data-ttu-id="7e8f8-125">输入字符串中的字符可以属于作为非单词字符的任何 Unicode 类别。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-125">A character in the input string can belong to any Unicode category that is not a word character.</span></span> <span data-ttu-id="7e8f8-126">有关详细信息，请参阅[非单词字符](#NonWordCharacter)。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-126">For more information, see [Non-Word Character](#NonWordCharacter).</span></span>  
  
- <span data-ttu-id="7e8f8-127">空白字符。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-127">A white-space character.</span></span> <span data-ttu-id="7e8f8-128">输入字符串中的字符可以是任何 Unicode 分隔符字符以及众多控制字符中的任一字符。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-128">A character in the input string can be any Unicode separator character, as well as any one of a number of control characters.</span></span> <span data-ttu-id="7e8f8-129">有关详细信息，请参阅[空白字符](#WhitespaceCharacter)。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-129">For more information, see [White-Space Character](#WhitespaceCharacter).</span></span>  
  
- <span data-ttu-id="7e8f8-130">非空白字符。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-130">A non-white-space character.</span></span> <span data-ttu-id="7e8f8-131">输入字符串中的字符可以是作为非空白字符的任何字符。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-131">A character in the input string can be any character that is not a white-space character.</span></span> <span data-ttu-id="7e8f8-132">有关详细信息，请参阅[非空白字符](#NonWhitespaceCharacter)。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-132">For more information, see [Non-White-Space Character](#NonWhitespaceCharacter).</span></span>  
  
- <span data-ttu-id="7e8f8-133">十进制数字。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-133">A decimal digit.</span></span> <span data-ttu-id="7e8f8-134">输入字符串中的字符可以是归类为 Unicode 十进制数字的众多字符中的任一字符。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-134">A character in the input string can be any of a number of characters classified as Unicode decimal digits.</span></span> <span data-ttu-id="7e8f8-135">有关详细信息，请参阅[十进制数字字符](#DigitCharacter)。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-135">For more information, see [Decimal Digit Character](#DigitCharacter).</span></span>  
  
- <span data-ttu-id="7e8f8-136">非十进制数字。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-136">A non-decimal digit.</span></span> <span data-ttu-id="7e8f8-137">输入字符串中的字符可以是任何非 Unicode 十进制数字。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-137">A character in the input string can be anything other than a Unicode decimal digit.</span></span> <span data-ttu-id="7e8f8-138">有关详细信息，请参阅[十进制数字字符](#NonDigitCharacter)。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-138">For more information, see [Decimal Digit Character](#NonDigitCharacter).</span></span>  
  
 <span data-ttu-id="7e8f8-139">.NET 支持字符类减法表达式，通过该表达式可以定义一组字符作为从一个字符类中排除另一字符类的结果。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-139">.NET supports character class subtraction expressions, which enables you to define a set of characters as the result of excluding one character class from another character class.</span></span> <span data-ttu-id="7e8f8-140">有关详细信息，请参阅[字符类减法](#CharacterClassSubtraction)。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-140">For more information, see [Character Class Subtraction](#CharacterClassSubtraction).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7e8f8-141">按类别匹配字符的字符类（如用于匹配字词字符的 [\w](#WordCharacter)，或用于匹配 Unicode 类别的 [\p{}](#CategoryOrBlock)）依赖 <xref:System.Globalization.CharUnicodeInfo> 类提供字符类别信息。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-141">Character classes that match characters by category, such as [\w](#WordCharacter) to match word characters or [\p{}](#CategoryOrBlock) to match a Unicode category, rely on the <xref:System.Globalization.CharUnicodeInfo> class to provide information about character categories.</span></span>  <span data-ttu-id="7e8f8-142">从 .NET Framework 4.6.2 开始，字符类别基于 [Unicode 标准 8.0.0 版](https://www.unicode.org/versions/Unicode8.0.0/)。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-142">Starting with the .NET Framework 4.6.2, character categories are based on [The Unicode Standard, Version 8.0.0](https://www.unicode.org/versions/Unicode8.0.0/).</span></span> <span data-ttu-id="7e8f8-143">从 .NET Framework 4 到 .NET Framework 4.6.1，字符类别基于 [Unicode 标准 6.3.0 版](https://www.unicode.org/versions/Unicode6.3.0/)。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-143">In the .NET Framework 4 through the .NET Framework 4.6.1, they are based on [The Unicode Standard, Version 6.3.0](https://www.unicode.org/versions/Unicode6.3.0/).</span></span>  
  
<a name="PositiveGroup"></a>
## <a name="positive-character-group--"></a><span data-ttu-id="7e8f8-144">正字符组：[ ]</span><span class="sxs-lookup"><span data-stu-id="7e8f8-144">Positive character group: [ ]</span></span>  
 <span data-ttu-id="7e8f8-145">正字符组指定一个字符列表，其中的任何一个字符可出现在输入字符串中以便进行匹配。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-145">A positive character group specifies a list of characters, any one of which may appear in an input string for a match to occur.</span></span> <span data-ttu-id="7e8f8-146">此字符列表可以单独指定和/或作为范围指定。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-146">This list of characters may be specified individually, as a range, or both.</span></span>  
  
 <span data-ttu-id="7e8f8-147">用于指定各个字符列表的语法如下所示：</span><span class="sxs-lookup"><span data-stu-id="7e8f8-147">The syntax for specifying a list of individual characters is as follows:</span></span>  

`[*character_group*]`

 <span data-ttu-id="7e8f8-148">其中，*character_group* 是单个字符的列表，这些字符可出现在输入字符串中以便成功匹配。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-148">where *character_group* is a list of the individual characters that can appear in the input string for a match to succeed.</span></span> <span data-ttu-id="7e8f8-149">character  _group 可以包含一个或多个文本字符、[转义字符](../../../docs/standard/base-types/character-escapes-in-regular-expressions.md)或字符类的任意组合。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-149">*character_group* can consist of any combination of one or more literal characters, [escape characters](../../../docs/standard/base-types/character-escapes-in-regular-expressions.md), or character classes.</span></span>  
  
 <span data-ttu-id="7e8f8-150">用于指定字符范围的语法如下：</span><span class="sxs-lookup"><span data-stu-id="7e8f8-150">The syntax for specifying a range of characters is as follows:</span></span>  
  
`[firstCharacter-lastCharacter]`  
  
 <span data-ttu-id="7e8f8-151">其中，*firstCharacter* 是范围的开始字符，*lastCharacter* 是范围的结束字符。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-151">where *firstCharacter* is the character that begins the range and *lastCharacter* is the character that ends the range.</span></span> <span data-ttu-id="7e8f8-152">字符范围是通过以下方式定义的一系列连续字符：指定系列中的第一个字符，连字符 (-)，然后指定系列中的最后一个字符。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-152">A character range is a contiguous series of characters defined by specifying the first character in the series, a hyphen (-), and then the last character in the series.</span></span> <span data-ttu-id="7e8f8-153">如果两个字符具有相邻的 Unicode 码位，则这两个字符是连续的。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-153">Two characters are contiguous if they have adjacent Unicode code points.</span></span> <span data-ttu-id="7e8f8-154">firstCharacter 必须是码位较低的字符，而 lastCharacter 必须是码位较高的字符   。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-154">*firstCharacter* must be the character with the lower code point, and *lastCharacter* must be the character with the higher code point.</span></span>

> [!NOTE]
> <span data-ttu-id="7e8f8-155">由于正字符组可以包含一组字符和一个字符范围，因此连字符 (`-`) 始终被解释为范围分隔符，除非它是该组的第一个或最后一个字符。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-155">Because a positive character group can include both a set of characters and a character range, a hyphen character (`-`) is always interpreted as the range separator unless it is the first or last character of the group.</span></span>

<span data-ttu-id="7e8f8-156">下表列出了一些常见的包含正字符类的正则表达式模式。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-156">Some common regular expression patterns that contain positive character classes are listed in the following table.</span></span>  
  
|<span data-ttu-id="7e8f8-157">模式</span><span class="sxs-lookup"><span data-stu-id="7e8f8-157">Pattern</span></span>|<span data-ttu-id="7e8f8-158">描述</span><span class="sxs-lookup"><span data-stu-id="7e8f8-158">Description</span></span>|  
|-------------|-----------------|  
|`[aeiou]`|<span data-ttu-id="7e8f8-159">匹配所有元音。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-159">Match all vowels.</span></span>|  
|`[\p{P}\d]`|<span data-ttu-id="7e8f8-160">匹配所有标点符号和十进制数字字符。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-160">Match all punctuation and decimal digit characters.</span></span>|  
|`[\s\p{P}]`|<span data-ttu-id="7e8f8-161">匹配所有空白和标点符号。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-161">Match all white space and punctuation.</span></span>|  
  
 <span data-ttu-id="7e8f8-162">下面的示例定义包含字符“a”和“e”的正字符组，以使输入字符串必须包含单词“grey”或“gray”且后跟另一个单词以便进行匹配。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-162">The following example defines a positive character group that contains the characters "a" and "e" so that the input string must contain the words "grey" or "gray" followed by another word for a match to occur.</span></span>  
  
 [!code-csharp[Conceptual.RegEx.Language.CharacterClasses#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.characterclasses/cs/positivecharclasses.cs#1)]
 [!code-vb[Conceptual.RegEx.Language.CharacterClasses#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.characterclasses/vb/positivecharclasses.vb#1)]  
  
 <span data-ttu-id="7e8f8-163">按以下方式定义正则表达式 `gr[ae]y\s\S+?[\s|\p{P}]`：</span><span class="sxs-lookup"><span data-stu-id="7e8f8-163">The regular expression `gr[ae]y\s\S+?[\s|\p{P}]` is defined as follows:</span></span>  
  
|<span data-ttu-id="7e8f8-164">模式</span><span class="sxs-lookup"><span data-stu-id="7e8f8-164">Pattern</span></span>|<span data-ttu-id="7e8f8-165">描述</span><span class="sxs-lookup"><span data-stu-id="7e8f8-165">Description</span></span>|  
|-------------|-----------------|  
|`gr`|<span data-ttu-id="7e8f8-166">匹配文本字符“gr”。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-166">Match the literal characters "gr".</span></span>|  
|`[ae]`|<span data-ttu-id="7e8f8-167">匹配“a”或“e”。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-167">Match either an "a" or an "e".</span></span>|  
|`y\s`|<span data-ttu-id="7e8f8-168">匹配后跟空白字符的文本字符“y”。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-168">Match the literal character "y" followed by a white-space character.</span></span>|  
|`\S+?`|<span data-ttu-id="7e8f8-169">匹配一个或多个非空白字符（但尽可能少）。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-169">Match one or more non-white-space characters, but as few as possible.</span></span>|  
|`[\s\p{P}]`|<span data-ttu-id="7e8f8-170">匹配空白字符或标点符号。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-170">Match either a white-space character or a punctuation mark.</span></span>|  
  
 <span data-ttu-id="7e8f8-171">下面的示例匹配以任何大写字母开头的单词。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-171">The following example matches words that begin with any capital letter.</span></span> <span data-ttu-id="7e8f8-172">它使用子表达式 `[A-Z]` 表示从 A 到 Z 的大写字母范围。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-172">It uses the subexpression `[A-Z]` to represent the range of capital letters from A to Z.</span></span>  
  
 [!code-csharp[Conceptual.RegEx.Language.CharacterClasses#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.characterclasses/cs/range.cs#3)]
 [!code-vb[Conceptual.RegEx.Language.CharacterClasses#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.characterclasses/vb/range.vb#3)]  
  
 <span data-ttu-id="7e8f8-173">正则表达式 `\b[A-Z]\w*\b` 的定义如下表所示。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-173">The regular expression `\b[A-Z]\w*\b` is defined as shown in the following table.</span></span>  
  
|<span data-ttu-id="7e8f8-174">模式</span><span class="sxs-lookup"><span data-stu-id="7e8f8-174">Pattern</span></span>|<span data-ttu-id="7e8f8-175">描述</span><span class="sxs-lookup"><span data-stu-id="7e8f8-175">Description</span></span>|  
|-------------|-----------------|  
|`\b`|<span data-ttu-id="7e8f8-176">在单词边界处开始。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-176">Start at a word boundary.</span></span>|  
|`[A-Z]`|<span data-ttu-id="7e8f8-177">匹配从 A 到 Z 的所有大写字符。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-177">Match any uppercase character from A to Z.</span></span>|  
|`\w*`|<span data-ttu-id="7e8f8-178">匹配零个或多个单词字符。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-178">Match zero or more word characters.</span></span>|  
|`\b`|<span data-ttu-id="7e8f8-179">与字边界匹配。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-179">Match a word boundary.</span></span>|  
  
<a name="NegativeGroup"></a>
## <a name="negative-character-group-"></a><span data-ttu-id="7e8f8-180">负字符组：[^]</span><span class="sxs-lookup"><span data-stu-id="7e8f8-180">Negative character group: [^]</span></span>  
 <span data-ttu-id="7e8f8-181">负字符组指定一个字符列表，这些字符不得出现在输入字符串中以便进行匹配。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-181">A negative character group specifies a list of characters that must not appear in an input string for a match to occur.</span></span> <span data-ttu-id="7e8f8-182">此字符列表可以单独指定和/或作为范围指定。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-182">The list of characters may be specified individually, as a range, or both.</span></span>  
  
<span data-ttu-id="7e8f8-183">用于指定各个字符列表的语法如下所示：</span><span class="sxs-lookup"><span data-stu-id="7e8f8-183">The syntax for specifying a list of individual characters is as follows:</span></span>  

`[*^character_group*]`

 <span data-ttu-id="7e8f8-184">其中，*character_group* 是单个字符的列表，这些字符不可出现在输入字符串中以便成功匹配。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-184">where *character_group* is a list of the individual characters that cannot appear in the input string for a match to succeed.</span></span> <span data-ttu-id="7e8f8-185">character  _group 可以包含一个或多个文本字符、[转义字符](../../../docs/standard/base-types/character-escapes-in-regular-expressions.md)或字符类的任意组合。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-185">*character_group* can consist of any combination of one or more literal characters, [escape characters](../../../docs/standard/base-types/character-escapes-in-regular-expressions.md), or character classes.</span></span>  
  
 <span data-ttu-id="7e8f8-186">用于指定字符范围的语法如下：</span><span class="sxs-lookup"><span data-stu-id="7e8f8-186">The syntax for specifying a range of characters is as follows:</span></span>  

`[^*firstCharacter*-*lastCharacter*]`

<span data-ttu-id="7e8f8-187">其中，*firstCharacter* 是范围的开始字符，*lastCharacter* 是范围的结束字符。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-187">where *firstCharacter* is the character that begins the range and *lastCharacter* is the character that ends the range.</span></span> <span data-ttu-id="7e8f8-188">字符范围是通过以下方式定义的一系列连续字符：指定系列中的第一个字符，连字符 (-)，然后指定系列中的最后一个字符。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-188">A character range is a contiguous series of characters defined by specifying the first character in the series, a hyphen (-), and then the last character in the series.</span></span> <span data-ttu-id="7e8f8-189">如果两个字符具有相邻的 Unicode 码位，则这两个字符是连续的。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-189">Two characters are contiguous if they have adjacent Unicode code points.</span></span> <span data-ttu-id="7e8f8-190">firstCharacter 必须是码位较低的字符，而 lastCharacter 必须是码位较高的字符   。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-190">*firstCharacter* must be the character with the lower code point, and *lastCharacter* must be the character with the higher code point.</span></span>

> [!NOTE]
> <span data-ttu-id="7e8f8-191">由于负字符组可以包含一组字符和一个字符范围，因此连字符 (`-`) 始终被解释为范围分隔符，除非它是该组的第一个或最后一个字符。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-191">Because a negative character group can include both a set of characters and a character range, a hyphen character (`-`) is always interpreted as the range separator unless it is the first or last character of the group.</span></span>
  
 <span data-ttu-id="7e8f8-192">可以连接两个或更多字符范围。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-192">Two or more character ranges can be concatenated.</span></span> <span data-ttu-id="7e8f8-193">例如，若要指定从“0”至“9”的十进制数范围、从“a”至“f”的小写字母范围，以及从“A”至“F”的大写字母范围，请使用 `[0-9a-fA-F]`。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-193">For example, to specify the range of decimal digits from "0" through "9", the range of lowercase letters from "a" through "f", and the range of uppercase letters from "A" through "F", use `[0-9a-fA-F]`.</span></span>  
  
 <span data-ttu-id="7e8f8-194">负字符组中的前导符 (`^`) 是强制的，指示字符组为负字符组，而不是正字符组。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-194">The leading caret character (`^`) in a negative character group is mandatory and indicates the character group is a negative character group instead of a positive character group.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="7e8f8-195">较大正则表达式模式中的负字符组不是零宽度断言。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-195">A negative character group in a larger regular expression pattern is not a zero-width assertion.</span></span> <span data-ttu-id="7e8f8-196">也就是说，在评估负字符组后，正则表达式引擎会在输入字符串中提升一个字符。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-196">That is, after evaluating the negative character group, the regular expression engine advances one character in the input string.</span></span>  
  
 <span data-ttu-id="7e8f8-197">下表列出了一些常见的包含负字符组的正则表达式模式。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-197">Some common regular expression patterns that contain negative character groups are listed in the following table.</span></span>  
  
|<span data-ttu-id="7e8f8-198">模式</span><span class="sxs-lookup"><span data-stu-id="7e8f8-198">Pattern</span></span>|<span data-ttu-id="7e8f8-199">描述</span><span class="sxs-lookup"><span data-stu-id="7e8f8-199">Description</span></span>|  
|-------------|-----------------|  
|`[^aeiou]`|<span data-ttu-id="7e8f8-200">匹配除元音以外的所有字符。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-200">Match all characters except vowels.</span></span>|  
|`[^\p{P}\d]`|<span data-ttu-id="7e8f8-201">匹配标点符号和十进制数字字符以外的所有字符。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-201">Match all characters except punctuation and decimal digit characters.</span></span>|  
  
 <span data-ttu-id="7e8f8-202">下面的示例匹配以字符“th”开头且后面不跟“o”的任何单词。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-202">The following example matches any word that begins with the characters "th" and is not followed by an "o".</span></span>  
  
 [!code-csharp[Conceptual.RegEx.Language.CharacterClasses#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.characterclasses/cs/negativecharclasses.cs#2)]
 [!code-vb[Conceptual.RegEx.Language.CharacterClasses#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.characterclasses/vb/negativecharclasses.vb#2)]  
  
 <span data-ttu-id="7e8f8-203">正则表达式 `\bth[^o]\w+\b` 的定义如下表所示。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-203">The regular expression `\bth[^o]\w+\b` is defined as shown in the following table.</span></span>  
  
|<span data-ttu-id="7e8f8-204">模式</span><span class="sxs-lookup"><span data-stu-id="7e8f8-204">Pattern</span></span>|<span data-ttu-id="7e8f8-205">描述</span><span class="sxs-lookup"><span data-stu-id="7e8f8-205">Description</span></span>|  
|-------------|-----------------|  
|`\b`|<span data-ttu-id="7e8f8-206">在单词边界处开始。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-206">Start at a word boundary.</span></span>|  
|`th`|<span data-ttu-id="7e8f8-207">匹配文本字符“th”。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-207">Match the literal characters "th".</span></span>|  
|`[^o]`|<span data-ttu-id="7e8f8-208">与不是“o”的任何字符匹配。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-208">Match any character that is not an "o".</span></span>|  
|`\w+`|<span data-ttu-id="7e8f8-209">匹配一个或多个单词字符。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-209">Match one or more word characters.</span></span>|  
|`\b`|<span data-ttu-id="7e8f8-210">在字边界结束。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-210">End at a word boundary.</span></span>|  
  
<a name="AnyCharacter"></a>
## <a name="any-character-"></a><span data-ttu-id="7e8f8-211">任意字符：.</span><span class="sxs-lookup"><span data-stu-id="7e8f8-211">Any character: .</span></span>  
 <span data-ttu-id="7e8f8-212">句点字符 (.) 匹配除 `\n`（换行符 \u000A）之外的任何字符，有以下两个限制：</span><span class="sxs-lookup"><span data-stu-id="7e8f8-212">The period character (.) matches any character except `\n` (the newline character, \u000A), with the following two qualifications:</span></span>  
  
- <span data-ttu-id="7e8f8-213">如果通过 <xref:System.Text.RegularExpressions.RegexOptions.Singleline?displayProperty=nameWithType> 选项修改正则表达式模式，或者通过 `.` 选项修改包含 `s` 字符类的模式的部分，则 `.` 可匹配任何字符。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-213">If a regular expression pattern is modified by the <xref:System.Text.RegularExpressions.RegexOptions.Singleline?displayProperty=nameWithType> option, or if the portion of the pattern that contains the `.` character class is modified by the `s` option, `.` matches any character.</span></span> <span data-ttu-id="7e8f8-214">有关详细信息，请参阅 [正则表达式选项](../../../docs/standard/base-types/regular-expression-options.md)。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-214">For more information, see [Regular Expression Options](../../../docs/standard/base-types/regular-expression-options.md).</span></span>  
  
     <span data-ttu-id="7e8f8-215">下面的示例阐释了默认情况下以及使用 `.` 选项的情况下 <xref:System.Text.RegularExpressions.RegexOptions.Singleline?displayProperty=nameWithType> 字符类的不同的行为。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-215">The following example illustrates the different behavior of the `.` character class by default and with the <xref:System.Text.RegularExpressions.RegexOptions.Singleline?displayProperty=nameWithType> option.</span></span> <span data-ttu-id="7e8f8-216">正则表达式 `^.+` 在字符串开头开始并匹配每个字符。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-216">The regular expression `^.+` starts at the beginning of the string and matches every character.</span></span> <span data-ttu-id="7e8f8-217">默认情况下，匹配在第一行的结尾结束；正则表达式模式匹配回车符、`\r` 或 \u000D，但不匹配 `\n`。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-217">By default, the match ends at the end of the first line; the regular expression pattern matches the carriage return character, `\r` or \u000D, but it does not match `\n`.</span></span> <span data-ttu-id="7e8f8-218">由于 <xref:System.Text.RegularExpressions.RegexOptions.Singleline?displayProperty=nameWithType> 选项将整个输入字符串解释为单行，因此它匹配输入字符串中的每个字符，包括 `\n`。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-218">Because the <xref:System.Text.RegularExpressions.RegexOptions.Singleline?displayProperty=nameWithType> option interprets the entire input string as a single line, it matches every character in the input string, including `\n`.</span></span>  
  
     [!code-csharp[Conceptual.Regex.Language.CharacterClasses#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.characterclasses/cs/any2.cs#5)]
     [!code-vb[Conceptual.Regex.Language.CharacterClasses#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.characterclasses/vb/any2.vb#5)]  
  
> [!NOTE]
> <span data-ttu-id="7e8f8-219">由于它匹配除 `\n` 之外的任何字符，因此 `.` 字符类也匹配 `\r`（回车符 \u000D）。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-219">Because it matches any character except `\n`, the `.` character class also matches `\r` (the carriage return character, \u000D).</span></span>  
  
- <span data-ttu-id="7e8f8-220">正字符组或负字符组中的句点字符将被视为原义句点字符，而非字符类。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-220">In a positive or negative character group, a period is treated as a literal period character, and not as a character class.</span></span> <span data-ttu-id="7e8f8-221">有关详细信息，请参阅本主题前面部分的[正字符组](#PositiveGroup)和[负字符组](#NegativeGroup)。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-221">For more information, see [Positive Character Group](#PositiveGroup) and [Negative Character Group](#NegativeGroup) earlier in this topic.</span></span> <span data-ttu-id="7e8f8-222">下面的示例通过定义包括句点字符 (`.`) 的正则表达式作为字符类和正字符组的成员来进行这方面的演示。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-222">The following example provides an illustration by defining a regular expression that includes the period character (`.`) both as a character class and as a member of a positive character group.</span></span> <span data-ttu-id="7e8f8-223">正则表达式 `\b.*[.?!;:](\s|\z)` 在字边界处开始，匹配任何字符直到遇到五个标点符号标记之一（包括句点），然后匹配空白字符或字符串的末尾。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-223">The regular expression `\b.*[.?!;:](\s|\z)` begins at a word boundary, matches any character until it encounters one of five punctuation marks, including a period, and then matches either a white-space character or the end of the string.</span></span>  
  
     [!code-csharp[Conceptual.RegEx.Language.CharacterClasses#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.characterclasses/cs/any1.cs#4)]
     [!code-vb[Conceptual.RegEx.Language.CharacterClasses#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.characterclasses/vb/any1.vb#4)]  
  
> [!NOTE]
> <span data-ttu-id="7e8f8-224">由于它匹配任何字符，因此当正则表达式模式尝试多次匹配任何字符时，`.` 语言元素通常会与惰性限定符一起使用。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-224">Because it matches any character, the `.` language element is often used with a lazy quantifier if a regular expression pattern attempts to match any character multiple times.</span></span> <span data-ttu-id="7e8f8-225">有关更多信息，请参见 [数量词](../../../docs/standard/base-types/quantifiers-in-regular-expressions.md)。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-225">For more information, see [Quantifiers](../../../docs/standard/base-types/quantifiers-in-regular-expressions.md).</span></span>  
  
<a name="CategoryOrBlock"></a>
## <a name="unicode-category-or-unicode-block-p"></a><span data-ttu-id="7e8f8-226">Unicode 类别或 Unicode 块：\p{}</span><span class="sxs-lookup"><span data-stu-id="7e8f8-226">Unicode category or Unicode block: \p{}</span></span>  
 <span data-ttu-id="7e8f8-227">Unicode 标准为每个常规类别分配一个字符。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-227">The Unicode standard assigns each character a general category.</span></span> <span data-ttu-id="7e8f8-228">例如，特定字符可以是大写字母（由 `Lu` 类别表示），十进制数字（`Nd` 类别）、数学符号（`Sm` 类别）或段落分隔符（`Zl` 类别）。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-228">For example, a particular character can be an uppercase letter (represented by the `Lu` category), a decimal digit (the `Nd` category), a math symbol (the `Sm` category), or a paragraph separator (the `Zl` category).</span></span> <span data-ttu-id="7e8f8-229">Unicode 标准中的特定字符集也占据连续码位的特定区域或块。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-229">Specific character sets in the Unicode standard also occupy a specific range or block of consecutive code points.</span></span> <span data-ttu-id="7e8f8-230">例如，可在 \u0000 和 \u007F 之间找到基本拉丁字符集，并可在 \u0600 和 \u06FF 之间找到阿拉伯语字符集。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-230">For example, the basic Latin character set is found from \u0000 through \u007F, while the Arabic character set is found from \u0600 through \u06FF.</span></span>  
  
 <span data-ttu-id="7e8f8-231">正则表达式构造</span><span class="sxs-lookup"><span data-stu-id="7e8f8-231">The regular expression construct</span></span>  
  
 <span data-ttu-id="7e8f8-232">`\p{` *name* `}`</span><span class="sxs-lookup"><span data-stu-id="7e8f8-232">`\p{` *name* `}`</span></span>  
  
 <span data-ttu-id="7e8f8-233">匹配属于 Unicode 常规类别或命名块的任何字符，其中，name  是类别缩写或命名块的名称。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-233">matches any character that belongs to a Unicode general category or named block, where *name* is the category abbreviation or named block name.</span></span> <span data-ttu-id="7e8f8-234">有关类别缩写的列表，请参阅本主题稍后的[支持的 Unicode 常规类别](#SupportedUnicodeGeneralCategories)部分。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-234">For a list of category abbreviations, see the [Supported Unicode General Categories](#SupportedUnicodeGeneralCategories) section later in this topic.</span></span> <span data-ttu-id="7e8f8-235">有关命名块的列表，请参阅本主题稍后的[支持的命名块](#SupportedNamedBlocks)部分。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-235">For a list of named blocks, see the [Supported Named Blocks](#SupportedNamedBlocks) section later in this topic.</span></span>  
  
 <span data-ttu-id="7e8f8-236">下面的示例使用 `\p{`名称`}` 构造以匹配 Unicode 常规类别（在该示例中为 `Pd` 或“标点，短划线”类别）和命名块（`IsGreek` 和 `IsBasicLatin` 命名块）。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-236">The following example uses the `\p{`*name*`}` construct to match both a Unicode general category (in this case, the `Pd`, or Punctuation, Dash category) and a named block (the `IsGreek` and `IsBasicLatin` named blocks).</span></span>  
  
 [!code-csharp[Conceptual.RegEx.Language.CharacterClasses#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.characterclasses/cs/category1.cs#6)]
 [!code-vb[Conceptual.RegEx.Language.CharacterClasses#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.characterclasses/vb/category1.vb#6)]  
  
 <span data-ttu-id="7e8f8-237">正则表达式 `\b(\p{IsGreek}+(\s)?)+\p{Pd}\s(\p{IsBasicLatin}+(\s)?)+` 的定义如下表所示。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-237">The regular expression `\b(\p{IsGreek}+(\s)?)+\p{Pd}\s(\p{IsBasicLatin}+(\s)?)+` is defined as shown in the following table.</span></span>  
  
|<span data-ttu-id="7e8f8-238">模式</span><span class="sxs-lookup"><span data-stu-id="7e8f8-238">Pattern</span></span>|<span data-ttu-id="7e8f8-239">描述</span><span class="sxs-lookup"><span data-stu-id="7e8f8-239">Description</span></span>|  
|-------------|-----------------|  
|`\b`|<span data-ttu-id="7e8f8-240">在单词边界处开始。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-240">Start at a word boundary.</span></span>|  
|`\p{IsGreek}+`|<span data-ttu-id="7e8f8-241">匹配一个或多个希腊语字符。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-241">Match one or more Greek characters.</span></span>|  
|`(\s)?`|<span data-ttu-id="7e8f8-242">匹配零个或一个空白字符。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-242">Match zero or one white-space character.</span></span>|  
|`(\p{IsGreek}+(\s)?)+`|<span data-ttu-id="7e8f8-243">匹配一个或多个希腊语字符后跟零个或一个空白字符的模式一次或多次。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-243">Match the pattern of one or more Greek characters followed by zero or one white-space characters one or more times.</span></span>|  
|`\p{Pd}`|<span data-ttu-id="7e8f8-244">匹配“标点，短划线”字符。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-244">Match a Punctuation, Dash character.</span></span>|  
|`\s`|<span data-ttu-id="7e8f8-245">与空白字符匹配。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-245">Match a white-space character.</span></span>|  
|`\p{IsBasicLatin}+`|<span data-ttu-id="7e8f8-246">匹配一个或多个基本拉丁字符。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-246">Match one or more basic Latin characters.</span></span>|  
|`(\s)?`|<span data-ttu-id="7e8f8-247">匹配零个或一个空白字符。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-247">Match zero or one white-space character.</span></span>|  
|`(\p{IsBasicLatin}+(\s)?)+`|<span data-ttu-id="7e8f8-248">匹配一个或多个基本拉丁字符后跟零个或一个空白字符的模式一次或多次。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-248">Match the pattern of one or more basic Latin characters followed by zero or one white-space characters one or more times.</span></span>|  
  
<a name="NegativeCategoryOrBlock"></a>
## <a name="negative-unicode-category-or-unicode-block-p"></a><span data-ttu-id="7e8f8-249">负 Unicode 类别或 Unicode 块：\P{}</span><span class="sxs-lookup"><span data-stu-id="7e8f8-249">Negative Unicode category or Unicode block: \P{}</span></span>  
 <span data-ttu-id="7e8f8-250">Unicode 标准为每个常规类别分配一个字符。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-250">The Unicode standard assigns each character a general category.</span></span> <span data-ttu-id="7e8f8-251">例如，特定字符可以是大写字母（由 `Lu` 类别表示），十进制数字（`Nd` 类别）、数学符号（`Sm` 类别）或段落分隔符（`Zl` 类别）。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-251">For example, a particular character can be an uppercase letter (represented by the `Lu` category), a decimal digit (the `Nd` category), a math symbol (the `Sm` category), or a paragraph separator (the `Zl` category).</span></span> <span data-ttu-id="7e8f8-252">Unicode 标准中的特定字符集也占据连续码位的特定区域或块。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-252">Specific character sets in the Unicode standard also occupy a specific range or block of consecutive code points.</span></span> <span data-ttu-id="7e8f8-253">例如，可在 \u0000 和 \u007F 之间找到基本拉丁字符集，并可在 \u0600 和 \u06FF 之间找到阿拉伯语字符集。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-253">For example, the basic Latin character set is found from \u0000 through \u007F, while the Arabic character set is found from \u0600 through \u06FF.</span></span>  
  
 <span data-ttu-id="7e8f8-254">正则表达式构造</span><span class="sxs-lookup"><span data-stu-id="7e8f8-254">The regular expression construct</span></span>  
  
 <span data-ttu-id="7e8f8-255">`\P{` *name* `}`</span><span class="sxs-lookup"><span data-stu-id="7e8f8-255">`\P{` *name* `}`</span></span>  
  
 <span data-ttu-id="7e8f8-256">匹配不属于 Unicode 常规类别或命名块的任何字符，其中，name  是类别缩写或命名块的名称。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-256">matches any character that does not belong to a Unicode general category or named block, where *name* is the category abbreviation or named block name.</span></span> <span data-ttu-id="7e8f8-257">有关类别缩写的列表，请参阅本主题稍后的[支持的 Unicode 常规类别](#SupportedUnicodeGeneralCategories)部分。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-257">For a list of category abbreviations, see the [Supported Unicode General Categories](#SupportedUnicodeGeneralCategories) section later in this topic.</span></span> <span data-ttu-id="7e8f8-258">有关命名块的列表，请参阅本主题稍后的[支持的命名块](#SupportedNamedBlocks)部分。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-258">For a list of named blocks, see the [Supported Named Blocks](#SupportedNamedBlocks) section later in this topic.</span></span>  
  
 <span data-ttu-id="7e8f8-259">下面的示例使用 `\P{`name  `}`构造来删除数字字符串中的任何货币符号（在该示例中为 `Sc` 或“符号，货币”类别）。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-259">The following example uses the `\P{`*name*`}` construct to remove any currency symbols (in this case, the `Sc`, or Symbol, Currency category) from numeric strings.</span></span>  
  
 [!code-csharp[Conceptual.RegEx.Language.CharacterClasses#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.characterclasses/cs/notcategory1.cs#7)]
 [!code-vb[Conceptual.RegEx.Language.CharacterClasses#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.characterclasses/vb/notcategory1.vb#7)]  
  
 <span data-ttu-id="7e8f8-260">正则表达式模式 `(\P{Sc})+` 匹配不为货币符号的一个或多个字符；它有效地从结果字符串中抽出任何货币符号。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-260">The regular expression pattern `(\P{Sc})+` matches one or more characters that are not currency symbols; it effectively strips any currency symbol from the result string.</span></span>  
  
<a name="WordCharacter"></a>
## <a name="word-character-w"></a><span data-ttu-id="7e8f8-261">单词字符：\w</span><span class="sxs-lookup"><span data-stu-id="7e8f8-261">Word character: \w</span></span>  
 <span data-ttu-id="7e8f8-262">`\w` 与任何单词字符匹配。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-262">`\w` matches any word character.</span></span> <span data-ttu-id="7e8f8-263">单词字符是下表中列出的任何 Unicode 类别的成员。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-263">A word character is a member of any of the Unicode categories listed in the following table.</span></span>  
  
|<span data-ttu-id="7e8f8-264">类别</span><span class="sxs-lookup"><span data-stu-id="7e8f8-264">Category</span></span>|<span data-ttu-id="7e8f8-265">描述</span><span class="sxs-lookup"><span data-stu-id="7e8f8-265">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="7e8f8-266">Ll</span><span class="sxs-lookup"><span data-stu-id="7e8f8-266">Ll</span></span>|<span data-ttu-id="7e8f8-267">字母，小写</span><span class="sxs-lookup"><span data-stu-id="7e8f8-267">Letter, Lowercase</span></span>|  
|<span data-ttu-id="7e8f8-268">Lu</span><span class="sxs-lookup"><span data-stu-id="7e8f8-268">Lu</span></span>|<span data-ttu-id="7e8f8-269">字母，大写</span><span class="sxs-lookup"><span data-stu-id="7e8f8-269">Letter, Uppercase</span></span>|  
|<span data-ttu-id="7e8f8-270">Lt</span><span class="sxs-lookup"><span data-stu-id="7e8f8-270">Lt</span></span>|<span data-ttu-id="7e8f8-271">字母，首字母大写</span><span class="sxs-lookup"><span data-stu-id="7e8f8-271">Letter, Titlecase</span></span>|  
|<span data-ttu-id="7e8f8-272">Lo</span><span class="sxs-lookup"><span data-stu-id="7e8f8-272">Lo</span></span>|<span data-ttu-id="7e8f8-273">字母，其他</span><span class="sxs-lookup"><span data-stu-id="7e8f8-273">Letter, Other</span></span>|  
|<span data-ttu-id="7e8f8-274">Lm</span><span class="sxs-lookup"><span data-stu-id="7e8f8-274">Lm</span></span>|<span data-ttu-id="7e8f8-275">字母，修饰符</span><span class="sxs-lookup"><span data-stu-id="7e8f8-275">Letter, Modifier</span></span>|  
|<span data-ttu-id="7e8f8-276">Mn</span><span class="sxs-lookup"><span data-stu-id="7e8f8-276">Mn</span></span>|<span data-ttu-id="7e8f8-277">标记，非间距</span><span class="sxs-lookup"><span data-stu-id="7e8f8-277">Mark, Nonspacing</span></span>|  
|<span data-ttu-id="7e8f8-278">Nd</span><span class="sxs-lookup"><span data-stu-id="7e8f8-278">Nd</span></span>|<span data-ttu-id="7e8f8-279">数字，十进制数</span><span class="sxs-lookup"><span data-stu-id="7e8f8-279">Number, Decimal Digit</span></span>|  
|<span data-ttu-id="7e8f8-280">Pc</span><span class="sxs-lookup"><span data-stu-id="7e8f8-280">Pc</span></span>|<span data-ttu-id="7e8f8-281">标点，连接符。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-281">Punctuation, Connector.</span></span> <span data-ttu-id="7e8f8-282">此类别包含 10 个字符，最常用的字符是 LOWLINE 字符 (_)，u+005F。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-282">This category includes ten characters, the most commonly used of which is the LOWLINE character (_), u+005F.</span></span>|  
  
 <span data-ttu-id="7e8f8-283">如果指定了符合 ECMAScript 的行为，则 `\w` 等效于 `[a-zA-Z_0-9]`。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-283">If ECMAScript-compliant behavior is specified, `\w` is equivalent to `[a-zA-Z_0-9]`.</span></span> <span data-ttu-id="7e8f8-284">有关 ECMAScript 正则表达式的信息，请参阅[正则表达式选项](../../../docs/standard/base-types/regular-expression-options.md)中的“ECMAScript 匹配行为”部分。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-284">For information on ECMAScript regular expressions, see the "ECMAScript Matching Behavior" section in [Regular Expression Options](../../../docs/standard/base-types/regular-expression-options.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7e8f8-285">由于它匹配任何单词字符，因此当正则表达式模式尝试多次匹配任何单词字符且后跟特定单词字符时，`\w` 语言元素通常会与惰性限定符一起使用。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-285">Because it matches any word character, the `\w` language element is often used with a lazy quantifier if a regular expression pattern attempts to match any word character multiple times, followed by a specific word character.</span></span> <span data-ttu-id="7e8f8-286">有关更多信息，请参见 [数量词](../../../docs/standard/base-types/quantifiers-in-regular-expressions.md)。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-286">For more information, see [Quantifiers](../../../docs/standard/base-types/quantifiers-in-regular-expressions.md).</span></span>  
  
 <span data-ttu-id="7e8f8-287">下面的示例使用 `\w` 语言元素来匹配单词中的重复字符。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-287">The following example uses the `\w` language element to match duplicate characters in a word.</span></span> <span data-ttu-id="7e8f8-288">该示例定义可按如下方式解释的正则表达式模式 `(\w)\1`。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-288">The example defines a regular expression pattern, `(\w)\1`, which can be interpreted as follows.</span></span>  
  
|<span data-ttu-id="7e8f8-289">元素</span><span class="sxs-lookup"><span data-stu-id="7e8f8-289">Element</span></span>|<span data-ttu-id="7e8f8-290">描述</span><span class="sxs-lookup"><span data-stu-id="7e8f8-290">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="7e8f8-291">(\w)</span><span class="sxs-lookup"><span data-stu-id="7e8f8-291">(\w)</span></span>|<span data-ttu-id="7e8f8-292">匹配单词字符。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-292">Match a word character.</span></span> <span data-ttu-id="7e8f8-293">这是第一个捕获组。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-293">This is the first capturing group.</span></span>|  
|<span data-ttu-id="7e8f8-294">\1</span><span class="sxs-lookup"><span data-stu-id="7e8f8-294">\1</span></span>|<span data-ttu-id="7e8f8-295">匹配第一次捕获的值。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-295">Match the value of the first capture.</span></span>|  
  
 [!code-csharp[Conceptual.RegEx.Language.CharacterClasses#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.characterclasses/cs/wordchar1.cs#8)]
 [!code-vb[Conceptual.RegEx.Language.CharacterClasses#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.characterclasses/vb/wordchar1.vb#8)]  
  
<a name="NonWordCharacter"></a>
## <a name="non-word-character-w"></a><span data-ttu-id="7e8f8-296">非单词字符：\W</span><span class="sxs-lookup"><span data-stu-id="7e8f8-296">Non-word character: \W</span></span>  
 <span data-ttu-id="7e8f8-297">`\W` 匹配任何非单词字符。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-297">`\W` matches any non-word character.</span></span> <span data-ttu-id="7e8f8-298">\W 语言元素等效于以下字符类：</span><span class="sxs-lookup"><span data-stu-id="7e8f8-298">The \W language element is equivalent to the following character class:</span></span>  
  
`[^\p{Ll}\p{Lu}\p{Lt}\p{Lo}\p{Nd}\p{Pc}\p{Lm}]`  
  
 <span data-ttu-id="7e8f8-299">换言之，它与下表列出的 Unicode 类别中的字符以外的任何字符匹配。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-299">In other words, it matches any character except for those in the Unicode categories listed in the following table.</span></span>  
  
|<span data-ttu-id="7e8f8-300">类别</span><span class="sxs-lookup"><span data-stu-id="7e8f8-300">Category</span></span>|<span data-ttu-id="7e8f8-301">描述</span><span class="sxs-lookup"><span data-stu-id="7e8f8-301">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="7e8f8-302">Ll</span><span class="sxs-lookup"><span data-stu-id="7e8f8-302">Ll</span></span>|<span data-ttu-id="7e8f8-303">字母，小写</span><span class="sxs-lookup"><span data-stu-id="7e8f8-303">Letter, Lowercase</span></span>|  
|<span data-ttu-id="7e8f8-304">Lu</span><span class="sxs-lookup"><span data-stu-id="7e8f8-304">Lu</span></span>|<span data-ttu-id="7e8f8-305">字母，大写</span><span class="sxs-lookup"><span data-stu-id="7e8f8-305">Letter, Uppercase</span></span>|  
|<span data-ttu-id="7e8f8-306">Lt</span><span class="sxs-lookup"><span data-stu-id="7e8f8-306">Lt</span></span>|<span data-ttu-id="7e8f8-307">字母，首字母大写</span><span class="sxs-lookup"><span data-stu-id="7e8f8-307">Letter, Titlecase</span></span>|  
|<span data-ttu-id="7e8f8-308">Lo</span><span class="sxs-lookup"><span data-stu-id="7e8f8-308">Lo</span></span>|<span data-ttu-id="7e8f8-309">字母，其他</span><span class="sxs-lookup"><span data-stu-id="7e8f8-309">Letter, Other</span></span>|  
|<span data-ttu-id="7e8f8-310">Lm</span><span class="sxs-lookup"><span data-stu-id="7e8f8-310">Lm</span></span>|<span data-ttu-id="7e8f8-311">字母，修饰符</span><span class="sxs-lookup"><span data-stu-id="7e8f8-311">Letter, Modifier</span></span>|  
|<span data-ttu-id="7e8f8-312">Mn</span><span class="sxs-lookup"><span data-stu-id="7e8f8-312">Mn</span></span>|<span data-ttu-id="7e8f8-313">标记，非间距</span><span class="sxs-lookup"><span data-stu-id="7e8f8-313">Mark, Nonspacing</span></span>|  
|<span data-ttu-id="7e8f8-314">Nd</span><span class="sxs-lookup"><span data-stu-id="7e8f8-314">Nd</span></span>|<span data-ttu-id="7e8f8-315">数字，十进制数</span><span class="sxs-lookup"><span data-stu-id="7e8f8-315">Number, Decimal Digit</span></span>|  
|<span data-ttu-id="7e8f8-316">Pc</span><span class="sxs-lookup"><span data-stu-id="7e8f8-316">Pc</span></span>|<span data-ttu-id="7e8f8-317">标点，连接符。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-317">Punctuation, Connector.</span></span> <span data-ttu-id="7e8f8-318">此类别包含 10 个字符，最常用的字符是 LOWLINE 字符 (_)，u+005F。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-318">This category includes ten characters, the most commonly used of which is the LOWLINE character (_), u+005F.</span></span>|  
  
 <span data-ttu-id="7e8f8-319">如果指定了符合 ECMAScript 的行为，则 `\W` 等效于 `[^a-zA-Z_0-9]`。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-319">If ECMAScript-compliant behavior is specified, `\W` is equivalent to `[^a-zA-Z_0-9]`.</span></span> <span data-ttu-id="7e8f8-320">有关 ECMAScript 正则表达式的信息，请参阅[正则表达式选项](../../../docs/standard/base-types/regular-expression-options.md)中的“ECMAScript 匹配行为”部分。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-320">For information on ECMAScript regular expressions, see the "ECMAScript Matching Behavior" section in [Regular Expression Options](../../../docs/standard/base-types/regular-expression-options.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7e8f8-321">由于它匹配任何非单词字符，因此当正则表达式模式尝试多次匹配任何非单词字符且后跟特定非单词字符时，`\W` 语言元素通常会与惰性限定符一起使用。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-321">Because it matches any non-word character, the `\W` language element is often used with a lazy quantifier if a regular expression pattern attempts to match any non-word character multiple times followed by a specific non-word character.</span></span> <span data-ttu-id="7e8f8-322">有关更多信息，请参见 [数量词](../../../docs/standard/base-types/quantifiers-in-regular-expressions.md)。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-322">For more information, see [Quantifiers](../../../docs/standard/base-types/quantifiers-in-regular-expressions.md).</span></span>  
  
 <span data-ttu-id="7e8f8-323">下面的示例阐释 `\W` 字符类。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-323">The following example illustrates the `\W` character class.</span></span>  <span data-ttu-id="7e8f8-324">它定义正则表达式模式 `\b(\w+)(\W){1,2}`，该模式匹配后跟一个或两个非单词字符（例如，空白或标点符号）的单词。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-324">It defines a regular expression pattern, `\b(\w+)(\W){1,2}`, that matches a word followed by one or two non-word characters, such as white space or punctuation.</span></span> <span data-ttu-id="7e8f8-325">正则表达式模式可以解释为下表中所示内容。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-325">The regular expression is interpreted as shown in the following table.</span></span>  
  
|<span data-ttu-id="7e8f8-326">元素</span><span class="sxs-lookup"><span data-stu-id="7e8f8-326">Element</span></span>|<span data-ttu-id="7e8f8-327">描述</span><span class="sxs-lookup"><span data-stu-id="7e8f8-327">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="7e8f8-328">\b</span><span class="sxs-lookup"><span data-stu-id="7e8f8-328">\b</span></span>|<span data-ttu-id="7e8f8-329">在单词边界处开始匹配。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-329">Begin the match at a word boundary.</span></span>|  
|<span data-ttu-id="7e8f8-330">(\w+)</span><span class="sxs-lookup"><span data-stu-id="7e8f8-330">(\w+)</span></span>|<span data-ttu-id="7e8f8-331">匹配一个或多个单词字符。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-331">Match one or more word characters.</span></span> <span data-ttu-id="7e8f8-332">这是第一个捕获组。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-332">This is the first capturing group.</span></span>|  
|<span data-ttu-id="7e8f8-333">(\W){1,2}</span><span class="sxs-lookup"><span data-stu-id="7e8f8-333">(\W){1,2}</span></span>|<span data-ttu-id="7e8f8-334">匹配非单词字符一次或两次。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-334">Match a non-word character either one or two times.</span></span> <span data-ttu-id="7e8f8-335">这是第二个捕获组。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-335">This is the second capturing group.</span></span>|  
  
 [!code-csharp[Conceptual.RegEx.Language.CharacterClasses#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.characterclasses/cs/nonwordchar1.cs#9)]
 [!code-vb[Conceptual.RegEx.Language.CharacterClasses#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.characterclasses/vb/nonwordchar1.vb#9)]  
  
 <span data-ttu-id="7e8f8-336">由于第二个捕获组的 <xref:System.Text.RegularExpressions.Group> 对象仅包含单个捕获的非单词字符，因此该示例将从 <xref:System.Text.RegularExpressions.CaptureCollection> 属性返回的 <xref:System.Text.RegularExpressions.Group.Captures%2A?displayProperty=nameWithType> 对象中检索所有捕获的非单词字符。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-336">Because the <xref:System.Text.RegularExpressions.Group> object for the second capturing group contains only a single captured non-word character, the example retrieves all captured non-word characters from the <xref:System.Text.RegularExpressions.CaptureCollection> object that is returned by the <xref:System.Text.RegularExpressions.Group.Captures%2A?displayProperty=nameWithType> property.</span></span>  
  
<a name="WhitespaceCharacter"></a>
## <a name="whitespace-character-s"></a><span data-ttu-id="7e8f8-337">空格字符：\s</span><span class="sxs-lookup"><span data-stu-id="7e8f8-337">Whitespace character: \s</span></span>  
 <span data-ttu-id="7e8f8-338">`\s` 匹配任意空格字符。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-338">`\s` matches any whitespace character.</span></span> <span data-ttu-id="7e8f8-339">它等效于下表中列出的转义序列和 Unicode 类别。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-339">It is equivalent to the escape sequences and Unicode categories listed in the following table.</span></span>  
  
|<span data-ttu-id="7e8f8-340">类别</span><span class="sxs-lookup"><span data-stu-id="7e8f8-340">Category</span></span>|<span data-ttu-id="7e8f8-341">描述</span><span class="sxs-lookup"><span data-stu-id="7e8f8-341">Description</span></span>|  
|--------------|-----------------|  
|`\f`|<span data-ttu-id="7e8f8-342">窗体换页符，\u000C。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-342">The form feed character, \u000C.</span></span>|  
|`\n`|<span data-ttu-id="7e8f8-343">换行符，\u000A。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-343">The newline character, \u000A.</span></span>|  
|`\r`|<span data-ttu-id="7e8f8-344">回车符，\u000D。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-344">The carriage return character, \u000D.</span></span>|  
|`\t`|<span data-ttu-id="7e8f8-345">制表符，\u0009。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-345">The tab character, \u0009.</span></span>|  
|`\v`|<span data-ttu-id="7e8f8-346">垂直制表符，\u000B。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-346">The vertical tab character, \u000B.</span></span>|  
|`\x85`|<span data-ttu-id="7e8f8-347">省略号或 NEXT LINE (NEL) 字符 (…)，\u0085。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-347">The ellipsis or NEXT LINE (NEL) character (…), \u0085.</span></span>|  
|`\p{Z}`|<span data-ttu-id="7e8f8-348">匹配任何分隔符。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-348">Matches any separator character.</span></span>|  
  
 <span data-ttu-id="7e8f8-349">如果指定了符合 ECMAScript 的行为，则 `\s` 等效于 `[ \f\n\r\t\v]`。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-349">If ECMAScript-compliant behavior is specified, `\s` is equivalent to `[ \f\n\r\t\v]`.</span></span> <span data-ttu-id="7e8f8-350">有关 ECMAScript 正则表达式的信息，请参阅[正则表达式选项](../../../docs/standard/base-types/regular-expression-options.md)中的“ECMAScript 匹配行为”部分。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-350">For information on ECMAScript regular expressions, see the "ECMAScript Matching Behavior" section in [Regular Expression Options](../../../docs/standard/base-types/regular-expression-options.md).</span></span>  
  
 <span data-ttu-id="7e8f8-351">下面的示例阐释 `\s` 字符类。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-351">The following example illustrates the `\s` character class.</span></span> <span data-ttu-id="7e8f8-352">它定义正则表达式模式 `\b\w+(e)?s(\s|$)`，该模式匹配以“s”或“es”结尾且后跟一个空白字符或输入字符串末尾的单词。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-352">It defines a regular expression pattern, `\b\w+(e)?s(\s|$)`, that matches a word ending in either "s" or "es" followed by either a white-space character or the end of the input string.</span></span> <span data-ttu-id="7e8f8-353">正则表达式模式可以解释为下表中所示内容。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-353">The regular expression is interpreted as shown in the following table.</span></span>  
  
|<span data-ttu-id="7e8f8-354">元素</span><span class="sxs-lookup"><span data-stu-id="7e8f8-354">Element</span></span>|<span data-ttu-id="7e8f8-355">描述</span><span class="sxs-lookup"><span data-stu-id="7e8f8-355">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="7e8f8-356">\b</span><span class="sxs-lookup"><span data-stu-id="7e8f8-356">\b</span></span>|<span data-ttu-id="7e8f8-357">在单词边界处开始匹配。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-357">Begin the match at a word boundary.</span></span>|  
|<span data-ttu-id="7e8f8-358">\w+</span><span class="sxs-lookup"><span data-stu-id="7e8f8-358">\w+</span></span>|<span data-ttu-id="7e8f8-359">匹配一个或多个单词字符。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-359">Match one or more word characters.</span></span>|  
|<span data-ttu-id="7e8f8-360">(e)?</span><span class="sxs-lookup"><span data-stu-id="7e8f8-360">(e)?</span></span>|<span data-ttu-id="7e8f8-361">匹配“e”零次或一次。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-361">Match an "e" either zero or one time.</span></span>|  
|<span data-ttu-id="7e8f8-362">s</span><span class="sxs-lookup"><span data-stu-id="7e8f8-362">s</span></span>|<span data-ttu-id="7e8f8-363">匹配“s”。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-363">Match an "s".</span></span>|  
|<span data-ttu-id="7e8f8-364">(\s&#124;$)</span><span class="sxs-lookup"><span data-stu-id="7e8f8-364">(\s&#124;$)</span></span>|<span data-ttu-id="7e8f8-365">匹配空白字符或输入字符串的末尾。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-365">Match either a white-space character or the end of the input string.</span></span>|  
  
 [!code-csharp[Conceptual.RegEx.Language.CharacterClasses#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.characterclasses/cs/whitespace1.cs#10)]
 [!code-vb[Conceptual.RegEx.Language.CharacterClasses#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.characterclasses/vb/whitespace1.vb#10)]  
  
<a name="NonWhitespaceCharacter"></a>
## <a name="non-whitespace-character-s"></a><span data-ttu-id="7e8f8-366">非空格字符：\S</span><span class="sxs-lookup"><span data-stu-id="7e8f8-366">Non-whitespace character: \S</span></span>  
 <span data-ttu-id="7e8f8-367">`\S` 匹配任何非空白字符。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-367">`\S` matches any non-white-space character.</span></span> <span data-ttu-id="7e8f8-368">它等效于 `[^\f\n\r\t\v\x85\p{Z}]` 正则表达式模式或与等效于 `\s` 的正则表达式模式（与空白字符匹配）相反。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-368">It is equivalent to the `[^\f\n\r\t\v\x85\p{Z}]` regular expression pattern, or the opposite of the regular expression pattern that is equivalent to `\s`, which matches white-space characters.</span></span> <span data-ttu-id="7e8f8-369">有关详细信息，请参阅[空白字符：\s](#WhitespaceCharacter)。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-369">For more information, see [White-Space Character: \s](#WhitespaceCharacter).</span></span>  
  
 <span data-ttu-id="7e8f8-370">如果指定了符合 ECMAScript 的行为，则 `\S` 等效于 `[^ \f\n\r\t\v]`。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-370">If ECMAScript-compliant behavior is specified, `\S` is equivalent to  `[^ \f\n\r\t\v]`.</span></span> <span data-ttu-id="7e8f8-371">有关 ECMAScript 正则表达式的信息，请参阅[正则表达式选项](../../../docs/standard/base-types/regular-expression-options.md)中的“ECMAScript 匹配行为”部分。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-371">For information on ECMAScript regular expressions, see the "ECMAScript Matching Behavior" section in [Regular Expression Options](../../../docs/standard/base-types/regular-expression-options.md).</span></span>  
  
 <span data-ttu-id="7e8f8-372">下面的示例阐释 `\S` 语言元素。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-372">The following example illustrates the `\S` language element.</span></span> <span data-ttu-id="7e8f8-373">正则表达式模式 `\b(\S+)\s?` 匹配由空白字符分隔的字符串。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-373">The regular expression pattern `\b(\S+)\s?` matches strings that are delimited by white-space characters.</span></span> <span data-ttu-id="7e8f8-374">匹配项的 <xref:System.Text.RegularExpressions.GroupCollection> 对象中的第二个元素包含匹配的字符串。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-374">The second element in the match's <xref:System.Text.RegularExpressions.GroupCollection> object contains the matched string.</span></span> <span data-ttu-id="7e8f8-375">正则表达式可按下表中的方式解释。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-375">The regular expression can be interpreted as shown in the following table.</span></span>  
  
|<span data-ttu-id="7e8f8-376">元素</span><span class="sxs-lookup"><span data-stu-id="7e8f8-376">Element</span></span>|<span data-ttu-id="7e8f8-377">描述</span><span class="sxs-lookup"><span data-stu-id="7e8f8-377">Description</span></span>|  
|-------------|-----------------|  
|`\b`|<span data-ttu-id="7e8f8-378">在单词边界处开始匹配。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-378">Begin the match at a word boundary.</span></span>|  
|`(\S+)`|<span data-ttu-id="7e8f8-379">匹配一个或多个非空白字符。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-379">Match one or more non-white-space characters.</span></span> <span data-ttu-id="7e8f8-380">这是第一个捕获组。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-380">This is the first capturing group.</span></span>|  
|`\s?`|<span data-ttu-id="7e8f8-381">匹配零个或一个空白字符。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-381">Match zero or one white-space character.</span></span>|  
  
 [!code-csharp[Conceptual.RegEx.Language.CharacterClasses#11](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.characterclasses/cs/nonwhitespace1.cs#11)]
 [!code-vb[Conceptual.RegEx.Language.CharacterClasses#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.characterclasses/vb/nonwhitespace1.vb#11)]  
  
<a name="DigitCharacter"></a>
## <a name="decimal-digit-character-d"></a><span data-ttu-id="7e8f8-382">十进制数字字符：\d</span><span class="sxs-lookup"><span data-stu-id="7e8f8-382">Decimal digit character: \d</span></span>  
 <span data-ttu-id="7e8f8-383">`\d` 匹配任何十进制数字。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-383">`\d` matches any decimal digit.</span></span> <span data-ttu-id="7e8f8-384">它等效于 `\p{Nd}` 正则表达式模式，该模式包含标准的十进制数字 0-9 以及众多其他字符集的十进制数字。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-384">It is equivalent to the `\p{Nd}` regular expression pattern, which includes the standard decimal digits 0-9 as well as the decimal digits of a number of other character sets.</span></span>  
  
 <span data-ttu-id="7e8f8-385">如果指定了符合 ECMAScript 的行为，则 `\d` 等效于 `[0-9]`。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-385">If ECMAScript-compliant behavior is specified, `\d` is equivalent to  `[0-9]`.</span></span> <span data-ttu-id="7e8f8-386">有关 ECMAScript 正则表达式的信息，请参阅[正则表达式选项](../../../docs/standard/base-types/regular-expression-options.md)中的“ECMAScript 匹配行为”部分。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-386">For information on ECMAScript regular expressions, see the "ECMAScript Matching Behavior" section in [Regular Expression Options](../../../docs/standard/base-types/regular-expression-options.md).</span></span>  
  
 <span data-ttu-id="7e8f8-387">下面的示例阐释 `\d` 语言元素。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-387">The following example illustrates the `\d` language element.</span></span> <span data-ttu-id="7e8f8-388">它测试输入字符串是否表示美国和加拿大的有效电话号码。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-388">It tests whether an input string represents a valid telephone number in the United States and Canada.</span></span> <span data-ttu-id="7e8f8-389">正则表达式模式 `^(\(?\d{3}\)?[\s-])?\d{3}-\d{4}$` 的定义如下表所示。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-389">The regular expression pattern `^(\(?\d{3}\)?[\s-])?\d{3}-\d{4}$` is defined as shown in the following table.</span></span>  
  
|<span data-ttu-id="7e8f8-390">元素</span><span class="sxs-lookup"><span data-stu-id="7e8f8-390">Element</span></span>|<span data-ttu-id="7e8f8-391">描述</span><span class="sxs-lookup"><span data-stu-id="7e8f8-391">Description</span></span>|  
|-------------|-----------------|  
|`^`|<span data-ttu-id="7e8f8-392">从输入字符串的开头部分开始匹配。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-392">Begin the match at the beginning of the input string.</span></span>|  
|`\(?`|<span data-ttu-id="7e8f8-393">匹配零个或一个“(”文本字符。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-393">Match zero or one literal "(" character.</span></span>|  
|`\d{3}`|<span data-ttu-id="7e8f8-394">匹配三个十进制数字。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-394">Match three decimal digits.</span></span>|  
|`\)?`|<span data-ttu-id="7e8f8-395">匹配零个或一个“)”文本字符。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-395">Match zero or one literal ")" character.</span></span>|  
|`[\s-]`|<span data-ttu-id="7e8f8-396">匹配连字符或空白字符。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-396">Match a hyphen or a white-space character.</span></span>|  
|`(\(?\d{3}\)?[\s-])?`|<span data-ttu-id="7e8f8-397">匹配后跟三个十进制数字的可选左括号、可选右括号和空白字符或连字符零次或一次。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-397">Match an optional opening parenthesis followed by three decimal digits, an optional closing parenthesis, and either a white-space character or a hyphen zero or one time.</span></span> <span data-ttu-id="7e8f8-398">这是第一个捕获组。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-398">This is the first capturing group.</span></span>|  
|`\d{3}-\d{4}`|<span data-ttu-id="7e8f8-399">匹配后跟连字符和四个以上的十进制数字的三个十进制数字。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-399">Match three decimal digits followed by a hyphen and four more decimal digits.</span></span>|  
|`$`|<span data-ttu-id="7e8f8-400">匹配输入字符串的末尾部分。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-400">Match the end of the input string.</span></span>|  
  
 [!code-csharp[Conceptual.RegEx.Language.CharacterClasses#12](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.characterclasses/cs/digit1.cs#12)]
 [!code-vb[Conceptual.RegEx.Language.CharacterClasses#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.characterclasses/vb/digit1.vb#12)]  
  
<a name="NonDigitCharacter"></a>
## <a name="non-digit-character-d"></a><span data-ttu-id="7e8f8-401">非数字字符：\D</span><span class="sxs-lookup"><span data-stu-id="7e8f8-401">Non-digit character: \D</span></span>  
 <span data-ttu-id="7e8f8-402">`\D` 匹配任何非数字字符。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-402">`\D` matches any non-digit character.</span></span> <span data-ttu-id="7e8f8-403">它等效于 `\P{Nd}` 正则表达式模式。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-403">It is equivalent to the `\P{Nd}` regular expression pattern.</span></span>  
  
 <span data-ttu-id="7e8f8-404">如果指定了符合 ECMAScript 的行为，则 `\D` 等效于 `[^0-9]`。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-404">If ECMAScript-compliant behavior is specified, `\D` is equivalent to  `[^0-9]`.</span></span> <span data-ttu-id="7e8f8-405">有关 ECMAScript 正则表达式的信息，请参阅[正则表达式选项](../../../docs/standard/base-types/regular-expression-options.md)中的“ECMAScript 匹配行为”部分。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-405">For information on ECMAScript regular expressions, see the "ECMAScript Matching Behavior" section in [Regular Expression Options](../../../docs/standard/base-types/regular-expression-options.md).</span></span>  
  
 <span data-ttu-id="7e8f8-406">下面的示例阐释了 \D 语言元素。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-406">The following example illustrates the \D language element.</span></span> <span data-ttu-id="7e8f8-407">它测试部件号等字符串是否包含适当的十进制和非十进制数字字符的组合。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-407">It tests whether a string such as a part number consists of the appropriate combination of decimal and non-decimal characters.</span></span> <span data-ttu-id="7e8f8-408">正则表达式模式 `^\D\d{1,5}\D*$` 的定义如下表所示。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-408">The regular expression pattern `^\D\d{1,5}\D*$` is defined as shown in the following table.</span></span>  
  
|<span data-ttu-id="7e8f8-409">元素</span><span class="sxs-lookup"><span data-stu-id="7e8f8-409">Element</span></span>|<span data-ttu-id="7e8f8-410">描述</span><span class="sxs-lookup"><span data-stu-id="7e8f8-410">Description</span></span>|  
|-------------|-----------------|  
|`^`|<span data-ttu-id="7e8f8-411">从输入字符串的开头部分开始匹配。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-411">Begin the match at the beginning of the input string.</span></span>|  
|`\D`|<span data-ttu-id="7e8f8-412">匹配非数字字符。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-412">Match a non-digit character.</span></span>|  
|`\d{1,5}`|<span data-ttu-id="7e8f8-413">匹配一到五个十进制数字。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-413">Match from one to five decimal digits.</span></span>|  
|`\D*`|<span data-ttu-id="7e8f8-414">匹配零个、一个或多个非十进制字符。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-414">Match zero, one, or more non-decimal characters.</span></span>|  
|`$`|<span data-ttu-id="7e8f8-415">匹配输入字符串的末尾部分。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-415">Match the end of the input string.</span></span>|  
  
 [!code-csharp[Conceptual.RegEx.Language.CharacterClasses#13](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.characterclasses/cs/nondigit1.cs#13)]
 [!code-vb[Conceptual.RegEx.Language.CharacterClasses#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.characterclasses/vb/nondigit1.vb#13)]  
  
<a name="SupportedUnicodeGeneralCategories"></a>
## <a name="supported-unicode-general-categories"></a><span data-ttu-id="7e8f8-416">支持的 Unicode 常规类别</span><span class="sxs-lookup"><span data-stu-id="7e8f8-416">Supported Unicode general categories</span></span>  
 <span data-ttu-id="7e8f8-417">Unicode 定义下表列出的常规类别。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-417">Unicode defines the general categories listed in the following table.</span></span> <span data-ttu-id="7e8f8-418">有关详细信息，请参阅 [Unicode 字符数据库](https://www.unicode.org/reports/tr44/)中的“UCD 文件格式”和“常规类别值”子主题。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-418">For more information, see the "UCD File Format" and "General Category Values" subtopics at the [Unicode Character Database](https://www.unicode.org/reports/tr44/).</span></span>  
  
|<span data-ttu-id="7e8f8-419">类别</span><span class="sxs-lookup"><span data-stu-id="7e8f8-419">Category</span></span>|<span data-ttu-id="7e8f8-420">描述</span><span class="sxs-lookup"><span data-stu-id="7e8f8-420">Description</span></span>|  
|--------------|-----------------|  
|`Lu`|<span data-ttu-id="7e8f8-421">字母，大写</span><span class="sxs-lookup"><span data-stu-id="7e8f8-421">Letter, Uppercase</span></span>|  
|`Ll`|<span data-ttu-id="7e8f8-422">字母，小写</span><span class="sxs-lookup"><span data-stu-id="7e8f8-422">Letter, Lowercase</span></span>|  
|`Lt`|<span data-ttu-id="7e8f8-423">字母，首字母大写</span><span class="sxs-lookup"><span data-stu-id="7e8f8-423">Letter, Titlecase</span></span>|  
|`Lm`|<span data-ttu-id="7e8f8-424">字母，修饰符</span><span class="sxs-lookup"><span data-stu-id="7e8f8-424">Letter, Modifier</span></span>|  
|`Lo`|<span data-ttu-id="7e8f8-425">字母，其他</span><span class="sxs-lookup"><span data-stu-id="7e8f8-425">Letter, Other</span></span>|  
|`L`|<span data-ttu-id="7e8f8-426">所有字母字符。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-426">All letter characters.</span></span> <span data-ttu-id="7e8f8-427">这包括 `Lu`、`Ll`、`Lt`、`Lm` 和 `Lo` 字符。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-427">This includes the `Lu`, `Ll`, `Lt`, `Lm`, and `Lo` characters.</span></span>|  
|`Mn`|<span data-ttu-id="7e8f8-428">标记，非间距</span><span class="sxs-lookup"><span data-stu-id="7e8f8-428">Mark, Nonspacing</span></span>|  
|`Mc`|<span data-ttu-id="7e8f8-429">标记，间距组合</span><span class="sxs-lookup"><span data-stu-id="7e8f8-429">Mark, Spacing Combining</span></span>|  
|`Me`|<span data-ttu-id="7e8f8-430">标记，封闭</span><span class="sxs-lookup"><span data-stu-id="7e8f8-430">Mark, Enclosing</span></span>|  
|`M`|<span data-ttu-id="7e8f8-431">所有音调符号标记。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-431">All diacritic marks.</span></span> <span data-ttu-id="7e8f8-432">这包括 `Mn`、`Mc` 和 `Me` 类别。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-432">This includes the `Mn`, `Mc`, and `Me` categories.</span></span>|  
|`Nd`|<span data-ttu-id="7e8f8-433">数字，十进制数</span><span class="sxs-lookup"><span data-stu-id="7e8f8-433">Number, Decimal Digit</span></span>|  
|`Nl`|<span data-ttu-id="7e8f8-434">数字，字母</span><span class="sxs-lookup"><span data-stu-id="7e8f8-434">Number, Letter</span></span>|  
|`No`|<span data-ttu-id="7e8f8-435">数字，其他</span><span class="sxs-lookup"><span data-stu-id="7e8f8-435">Number, Other</span></span>|  
|`N`|<span data-ttu-id="7e8f8-436">所有数字。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-436">All numbers.</span></span> <span data-ttu-id="7e8f8-437">这包括 `Nd`、`Nl` 和 `No` 类别。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-437">This includes the `Nd`, `Nl`, and `No` categories.</span></span>|  
|`Pc`|<span data-ttu-id="7e8f8-438">标点，连接符</span><span class="sxs-lookup"><span data-stu-id="7e8f8-438">Punctuation, Connector</span></span>|  
|`Pd`|<span data-ttu-id="7e8f8-439">标点，短划线</span><span class="sxs-lookup"><span data-stu-id="7e8f8-439">Punctuation, Dash</span></span>|  
|`Ps`|<span data-ttu-id="7e8f8-440">标点，开始</span><span class="sxs-lookup"><span data-stu-id="7e8f8-440">Punctuation, Open</span></span>|  
|`Pe`|<span data-ttu-id="7e8f8-441">标点，结束</span><span class="sxs-lookup"><span data-stu-id="7e8f8-441">Punctuation, Close</span></span>|  
|`Pi`|<span data-ttu-id="7e8f8-442">标点，前引号（根据具体使用情况，作用可能像 Ps 或 Pe）</span><span class="sxs-lookup"><span data-stu-id="7e8f8-442">Punctuation, Initial quote (may behave like Ps or Pe depending on usage)</span></span>|  
|`Pf`|<span data-ttu-id="7e8f8-443">标点，后引号（根据具体使用情况，作用可能像 Ps 或 Pe）</span><span class="sxs-lookup"><span data-stu-id="7e8f8-443">Punctuation, Final quote (may behave like Ps or Pe depending on usage)</span></span>|  
|`Po`|<span data-ttu-id="7e8f8-444">标点，其他</span><span class="sxs-lookup"><span data-stu-id="7e8f8-444">Punctuation, Other</span></span>|  
|`P`|<span data-ttu-id="7e8f8-445">所有标点字符。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-445">All punctuation characters.</span></span> <span data-ttu-id="7e8f8-446">这包括 `Pc`、`Pd`、`Ps`, `Pe`、`Pi`、`Pf` 和 `Po` 类别。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-446">This includes the `Pc`, `Pd`, `Ps`, `Pe`, `Pi`, `Pf`, and `Po` categories.</span></span>|  
|`Sm`|<span data-ttu-id="7e8f8-447">符号，数学</span><span class="sxs-lookup"><span data-stu-id="7e8f8-447">Symbol, Math</span></span>|  
|`Sc`|<span data-ttu-id="7e8f8-448">符号，货币</span><span class="sxs-lookup"><span data-stu-id="7e8f8-448">Symbol, Currency</span></span>|  
|`Sk`|<span data-ttu-id="7e8f8-449">符号，修饰符</span><span class="sxs-lookup"><span data-stu-id="7e8f8-449">Symbol, Modifier</span></span>|  
|`So`|<span data-ttu-id="7e8f8-450">符号，其他</span><span class="sxs-lookup"><span data-stu-id="7e8f8-450">Symbol, Other</span></span>|  
|`S`|<span data-ttu-id="7e8f8-451">所有符号。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-451">All symbols.</span></span> <span data-ttu-id="7e8f8-452">这包括 `Sm`、`Sc`、`Sk` 和 `So` 类别。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-452">This includes the `Sm`, `Sc`, `Sk`, and `So` categories.</span></span>|  
|`Zs`|<span data-ttu-id="7e8f8-453">分隔符，空白</span><span class="sxs-lookup"><span data-stu-id="7e8f8-453">Separator, Space</span></span>|  
|`Zl`|<span data-ttu-id="7e8f8-454">分隔符，行</span><span class="sxs-lookup"><span data-stu-id="7e8f8-454">Separator, Line</span></span>|  
|`Zp`|<span data-ttu-id="7e8f8-455">分隔符，段落</span><span class="sxs-lookup"><span data-stu-id="7e8f8-455">Separator, Paragraph</span></span>|  
|`Z`|<span data-ttu-id="7e8f8-456">所有分隔符字符。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-456">All separator characters.</span></span> <span data-ttu-id="7e8f8-457">这包括 `Zs`、`Zl` 和 `Zp` 类别。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-457">This includes the `Zs`, `Zl`, and `Zp` categories.</span></span>|  
|`Cc`|<span data-ttu-id="7e8f8-458">其他，控制</span><span class="sxs-lookup"><span data-stu-id="7e8f8-458">Other, Control</span></span>|  
|`Cf`|<span data-ttu-id="7e8f8-459">其他，格式</span><span class="sxs-lookup"><span data-stu-id="7e8f8-459">Other, Format</span></span>|  
|`Cs`|<span data-ttu-id="7e8f8-460">其他，代理项</span><span class="sxs-lookup"><span data-stu-id="7e8f8-460">Other, Surrogate</span></span>|  
|`Co`|<span data-ttu-id="7e8f8-461">其他，私用</span><span class="sxs-lookup"><span data-stu-id="7e8f8-461">Other, Private Use</span></span>|  
|`Cn`|<span data-ttu-id="7e8f8-462">其他，未赋值（任何字符都不具有此属性）</span><span class="sxs-lookup"><span data-stu-id="7e8f8-462">Other, Not Assigned (no characters have this property)</span></span>|  
|`C`|<span data-ttu-id="7e8f8-463">所有控制字符。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-463">All control characters.</span></span> <span data-ttu-id="7e8f8-464">这包括 `Cc`、`Cf`、`Cs`、`Co` 和 `Cn` 类别。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-464">This includes the `Cc`, `Cf`, `Cs`, `Co`, and `Cn` categories.</span></span>|  
  
 <span data-ttu-id="7e8f8-465">可以通过将任何特定字符传递到 <xref:System.Char.GetUnicodeCategory%2A> 方法来确定该字符的 Unicode 类别。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-465">You can determine the Unicode category of any particular character by passing that character to the <xref:System.Char.GetUnicodeCategory%2A> method.</span></span> <span data-ttu-id="7e8f8-466">下面的示例使用 <xref:System.Char.GetUnicodeCategory%2A> 方法来确定包含所选拉丁字符的数组中的每个元素的类别。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-466">The following example uses the <xref:System.Char.GetUnicodeCategory%2A> method to determine the category of each element in an array that contains selected Latin characters.</span></span>  
  
 [!code-csharp[Conceptual.RegEx.Language.CharacterClasses#14](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.characterclasses/cs/getunicodecategory1.cs#14)]
 [!code-vb[Conceptual.RegEx.Language.CharacterClasses#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.characterclasses/vb/getunicodecategory1.vb#14)]  
  
<a name="SupportedNamedBlocks"></a>
## <a name="supported-named-blocks"></a><span data-ttu-id="7e8f8-467">支持的命名块</span><span class="sxs-lookup"><span data-stu-id="7e8f8-467">Supported named blocks</span></span>

<span data-ttu-id="7e8f8-468">.NET 提供下表中所列的命名块。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-468">.NET provides the named blocks listed in the following table.</span></span> <span data-ttu-id="7e8f8-469">该组支持的命名块基于 Unicode 4.0 和 Perl 5.6。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-469">The set of supported named blocks is based on Unicode 4.0 and Perl 5.6.</span></span> <span data-ttu-id="7e8f8-470">有关正则表达式使用命名块，请参阅 [Unicode 类别或 Unicode 块： \\p{}](#unicode-category-or-unicode-block-p) 部分。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-470">For a regular expression that uses named blocks, see the [Unicode category or Unicode block: \\p{}](#unicode-category-or-unicode-block-p) section.</span></span>  
  
|<span data-ttu-id="7e8f8-471">码位范围</span><span class="sxs-lookup"><span data-stu-id="7e8f8-471">Code point range</span></span>|<span data-ttu-id="7e8f8-472">块名称</span><span class="sxs-lookup"><span data-stu-id="7e8f8-472">Block name</span></span>|  
|----------------------|----------------|  
|<span data-ttu-id="7e8f8-473">0000 - 007F</span><span class="sxs-lookup"><span data-stu-id="7e8f8-473">0000 - 007F</span></span>|`IsBasicLatin`|  
|<span data-ttu-id="7e8f8-474">0080 - 00FF</span><span class="sxs-lookup"><span data-stu-id="7e8f8-474">0080 - 00FF</span></span>|`IsLatin-1Supplement`|  
|<span data-ttu-id="7e8f8-475">0100 - 017F</span><span class="sxs-lookup"><span data-stu-id="7e8f8-475">0100 - 017F</span></span>|`IsLatinExtended-A`|  
|<span data-ttu-id="7e8f8-476">0180 - 024F</span><span class="sxs-lookup"><span data-stu-id="7e8f8-476">0180 - 024F</span></span>|`IsLatinExtended-B`|  
|<span data-ttu-id="7e8f8-477">0250 - 02AF</span><span class="sxs-lookup"><span data-stu-id="7e8f8-477">0250 - 02AF</span></span>|`IsIPAExtensions`|  
|<span data-ttu-id="7e8f8-478">02B0 - 02FF</span><span class="sxs-lookup"><span data-stu-id="7e8f8-478">02B0 - 02FF</span></span>|`IsSpacingModifierLetters`|  
|<span data-ttu-id="7e8f8-479">0300 - 036F</span><span class="sxs-lookup"><span data-stu-id="7e8f8-479">0300 - 036F</span></span>|`IsCombiningDiacriticalMarks`|  
|<span data-ttu-id="7e8f8-480">0370 - 03FF</span><span class="sxs-lookup"><span data-stu-id="7e8f8-480">0370 - 03FF</span></span>|`IsGreek`<br /><br /> <span data-ttu-id="7e8f8-481">\- 或 -</span><span class="sxs-lookup"><span data-stu-id="7e8f8-481">-or-</span></span><br /><br /> `IsGreekandCoptic`|  
|<span data-ttu-id="7e8f8-482">0400 - 04FF</span><span class="sxs-lookup"><span data-stu-id="7e8f8-482">0400 - 04FF</span></span>|`IsCyrillic`|  
|<span data-ttu-id="7e8f8-483">0500 - 052F</span><span class="sxs-lookup"><span data-stu-id="7e8f8-483">0500 - 052F</span></span>|`IsCyrillicSupplement`|  
|<span data-ttu-id="7e8f8-484">0530 - 058F</span><span class="sxs-lookup"><span data-stu-id="7e8f8-484">0530 - 058F</span></span>|`IsArmenian`|  
|<span data-ttu-id="7e8f8-485">0590 - 05FF</span><span class="sxs-lookup"><span data-stu-id="7e8f8-485">0590 - 05FF</span></span>|`IsHebrew`|  
|<span data-ttu-id="7e8f8-486">0600 - 06FF</span><span class="sxs-lookup"><span data-stu-id="7e8f8-486">0600 - 06FF</span></span>|`IsArabic`|  
|<span data-ttu-id="7e8f8-487">0700 - 074F</span><span class="sxs-lookup"><span data-stu-id="7e8f8-487">0700 - 074F</span></span>|`IsSyriac`|  
|<span data-ttu-id="7e8f8-488">0780 - 07BF</span><span class="sxs-lookup"><span data-stu-id="7e8f8-488">0780 - 07BF</span></span>|`IsThaana`|  
|<span data-ttu-id="7e8f8-489">0900 - 097F</span><span class="sxs-lookup"><span data-stu-id="7e8f8-489">0900 - 097F</span></span>|`IsDevanagari`|  
|<span data-ttu-id="7e8f8-490">0980 - 09FF</span><span class="sxs-lookup"><span data-stu-id="7e8f8-490">0980 - 09FF</span></span>|`IsBengali`|  
|<span data-ttu-id="7e8f8-491">0A00 - 0A7F</span><span class="sxs-lookup"><span data-stu-id="7e8f8-491">0A00 - 0A7F</span></span>|`IsGurmukhi`|  
|<span data-ttu-id="7e8f8-492">0A80 - 0AFF</span><span class="sxs-lookup"><span data-stu-id="7e8f8-492">0A80 - 0AFF</span></span>|`IsGujarati`|  
|<span data-ttu-id="7e8f8-493">0B00 - 0B7F</span><span class="sxs-lookup"><span data-stu-id="7e8f8-493">0B00 - 0B7F</span></span>|`IsOriya`|  
|<span data-ttu-id="7e8f8-494">0B80 - 0BFF</span><span class="sxs-lookup"><span data-stu-id="7e8f8-494">0B80 - 0BFF</span></span>|`IsTamil`|  
|<span data-ttu-id="7e8f8-495">0C00 - 0C7F</span><span class="sxs-lookup"><span data-stu-id="7e8f8-495">0C00 - 0C7F</span></span>|`IsTelugu`|  
|<span data-ttu-id="7e8f8-496">0C80 - 0CFF</span><span class="sxs-lookup"><span data-stu-id="7e8f8-496">0C80 - 0CFF</span></span>|`IsKannada`|  
|<span data-ttu-id="7e8f8-497">0D00 - 0D7F</span><span class="sxs-lookup"><span data-stu-id="7e8f8-497">0D00 - 0D7F</span></span>|`IsMalayalam`|  
|<span data-ttu-id="7e8f8-498">0D80 - 0DFF</span><span class="sxs-lookup"><span data-stu-id="7e8f8-498">0D80 - 0DFF</span></span>|`IsSinhala`|  
|<span data-ttu-id="7e8f8-499">0E00 - 0E7F</span><span class="sxs-lookup"><span data-stu-id="7e8f8-499">0E00 - 0E7F</span></span>|`IsThai`|  
|<span data-ttu-id="7e8f8-500">0E80 - 0EFF</span><span class="sxs-lookup"><span data-stu-id="7e8f8-500">0E80 - 0EFF</span></span>|`IsLao`|  
|<span data-ttu-id="7e8f8-501">0F00 - 0FFF</span><span class="sxs-lookup"><span data-stu-id="7e8f8-501">0F00 - 0FFF</span></span>|`IsTibetan`|  
|<span data-ttu-id="7e8f8-502">1000 - 109F</span><span class="sxs-lookup"><span data-stu-id="7e8f8-502">1000 - 109F</span></span>|`IsMyanmar`|  
|<span data-ttu-id="7e8f8-503">10A0 - 10FF</span><span class="sxs-lookup"><span data-stu-id="7e8f8-503">10A0 - 10FF</span></span>|`IsGeorgian`|  
|<span data-ttu-id="7e8f8-504">1100 - 11FF</span><span class="sxs-lookup"><span data-stu-id="7e8f8-504">1100 - 11FF</span></span>|`IsHangulJamo`|  
|<span data-ttu-id="7e8f8-505">1200 - 137F</span><span class="sxs-lookup"><span data-stu-id="7e8f8-505">1200 - 137F</span></span>|`IsEthiopic`|  
|<span data-ttu-id="7e8f8-506">13A0 - 13FF</span><span class="sxs-lookup"><span data-stu-id="7e8f8-506">13A0 - 13FF</span></span>|`IsCherokee`|  
|<span data-ttu-id="7e8f8-507">1400 - 167F</span><span class="sxs-lookup"><span data-stu-id="7e8f8-507">1400 - 167F</span></span>|`IsUnifiedCanadianAboriginalSyllabics`|  
|<span data-ttu-id="7e8f8-508">1680 - 169F</span><span class="sxs-lookup"><span data-stu-id="7e8f8-508">1680 - 169F</span></span>|`IsOgham`|  
|<span data-ttu-id="7e8f8-509">16A0 - 16FF</span><span class="sxs-lookup"><span data-stu-id="7e8f8-509">16A0 - 16FF</span></span>|`IsRunic`|  
|<span data-ttu-id="7e8f8-510">1700 - 171F</span><span class="sxs-lookup"><span data-stu-id="7e8f8-510">1700 - 171F</span></span>|`IsTagalog`|  
|<span data-ttu-id="7e8f8-511">1720 - 173F</span><span class="sxs-lookup"><span data-stu-id="7e8f8-511">1720 - 173F</span></span>|`IsHanunoo`|  
|<span data-ttu-id="7e8f8-512">1740 - 175F</span><span class="sxs-lookup"><span data-stu-id="7e8f8-512">1740 - 175F</span></span>|`IsBuhid`|  
|<span data-ttu-id="7e8f8-513">1760 - 177F</span><span class="sxs-lookup"><span data-stu-id="7e8f8-513">1760 - 177F</span></span>|`IsTagbanwa`|  
|<span data-ttu-id="7e8f8-514">1780 - 17FF</span><span class="sxs-lookup"><span data-stu-id="7e8f8-514">1780 - 17FF</span></span>|`IsKhmer`|  
|<span data-ttu-id="7e8f8-515">1800 - 18AF</span><span class="sxs-lookup"><span data-stu-id="7e8f8-515">1800 - 18AF</span></span>|`IsMongolian`|  
|<span data-ttu-id="7e8f8-516">1900 - 194F</span><span class="sxs-lookup"><span data-stu-id="7e8f8-516">1900 - 194F</span></span>|`IsLimbu`|  
|<span data-ttu-id="7e8f8-517">1950 - 197F</span><span class="sxs-lookup"><span data-stu-id="7e8f8-517">1950 - 197F</span></span>|`IsTaiLe`|  
|<span data-ttu-id="7e8f8-518">19E0 - 19FF</span><span class="sxs-lookup"><span data-stu-id="7e8f8-518">19E0 - 19FF</span></span>|`IsKhmerSymbols`|  
|<span data-ttu-id="7e8f8-519">1D00 - 1D7F</span><span class="sxs-lookup"><span data-stu-id="7e8f8-519">1D00 - 1D7F</span></span>|`IsPhoneticExtensions`|  
|<span data-ttu-id="7e8f8-520">1E00 - 1EFF</span><span class="sxs-lookup"><span data-stu-id="7e8f8-520">1E00 - 1EFF</span></span>|`IsLatinExtendedAdditional`|  
|<span data-ttu-id="7e8f8-521">1F00 - 1FFF</span><span class="sxs-lookup"><span data-stu-id="7e8f8-521">1F00 - 1FFF</span></span>|`IsGreekExtended`|  
|<span data-ttu-id="7e8f8-522">2000 - 206F</span><span class="sxs-lookup"><span data-stu-id="7e8f8-522">2000 - 206F</span></span>|`IsGeneralPunctuation`|  
|<span data-ttu-id="7e8f8-523">2070 - 209F</span><span class="sxs-lookup"><span data-stu-id="7e8f8-523">2070 - 209F</span></span>|`IsSuperscriptsandSubscripts`|  
|<span data-ttu-id="7e8f8-524">20A0 - 20CF</span><span class="sxs-lookup"><span data-stu-id="7e8f8-524">20A0 - 20CF</span></span>|`IsCurrencySymbols`|  
|<span data-ttu-id="7e8f8-525">20D0 - 20FF</span><span class="sxs-lookup"><span data-stu-id="7e8f8-525">20D0 - 20FF</span></span>|`IsCombiningDiacriticalMarksforSymbols`<br /><br /> <span data-ttu-id="7e8f8-526">\- 或 -</span><span class="sxs-lookup"><span data-stu-id="7e8f8-526">-or-</span></span><br /><br /> `IsCombiningMarksforSymbols`|  
|<span data-ttu-id="7e8f8-527">2100 - 214F</span><span class="sxs-lookup"><span data-stu-id="7e8f8-527">2100 - 214F</span></span>|`IsLetterlikeSymbols`|  
|<span data-ttu-id="7e8f8-528">2150 - 218F</span><span class="sxs-lookup"><span data-stu-id="7e8f8-528">2150 - 218F</span></span>|`IsNumberForms`|  
|<span data-ttu-id="7e8f8-529">2190 - 21FF</span><span class="sxs-lookup"><span data-stu-id="7e8f8-529">2190 - 21FF</span></span>|`IsArrows`|  
|<span data-ttu-id="7e8f8-530">2200 - 22FF</span><span class="sxs-lookup"><span data-stu-id="7e8f8-530">2200 - 22FF</span></span>|`IsMathematicalOperators`|  
|<span data-ttu-id="7e8f8-531">2300 - 23FF</span><span class="sxs-lookup"><span data-stu-id="7e8f8-531">2300 - 23FF</span></span>|`IsMiscellaneousTechnical`|  
|<span data-ttu-id="7e8f8-532">2400 - 243F</span><span class="sxs-lookup"><span data-stu-id="7e8f8-532">2400 - 243F</span></span>|`IsControlPictures`|  
|<span data-ttu-id="7e8f8-533">2440 - 245F</span><span class="sxs-lookup"><span data-stu-id="7e8f8-533">2440 - 245F</span></span>|`IsOpticalCharacterRecognition`|  
|<span data-ttu-id="7e8f8-534">2460 - 24FF</span><span class="sxs-lookup"><span data-stu-id="7e8f8-534">2460 - 24FF</span></span>|`IsEnclosedAlphanumerics`|  
|<span data-ttu-id="7e8f8-535">2500 - 257F</span><span class="sxs-lookup"><span data-stu-id="7e8f8-535">2500 - 257F</span></span>|`IsBoxDrawing`|  
|<span data-ttu-id="7e8f8-536">2580 - 259F</span><span class="sxs-lookup"><span data-stu-id="7e8f8-536">2580 - 259F</span></span>|`IsBlockElements`|  
|<span data-ttu-id="7e8f8-537">25A0 - 25FF</span><span class="sxs-lookup"><span data-stu-id="7e8f8-537">25A0 - 25FF</span></span>|`IsGeometricShapes`|  
|<span data-ttu-id="7e8f8-538">2600 - 26FF</span><span class="sxs-lookup"><span data-stu-id="7e8f8-538">2600 - 26FF</span></span>|`IsMiscellaneousSymbols`|  
|<span data-ttu-id="7e8f8-539">2700 - 27BF</span><span class="sxs-lookup"><span data-stu-id="7e8f8-539">2700 - 27BF</span></span>|`IsDingbats`|  
|<span data-ttu-id="7e8f8-540">27C0 - 27EF</span><span class="sxs-lookup"><span data-stu-id="7e8f8-540">27C0 - 27EF</span></span>|`IsMiscellaneousMathematicalSymbols-A`|  
|<span data-ttu-id="7e8f8-541">27F0 - 27FF</span><span class="sxs-lookup"><span data-stu-id="7e8f8-541">27F0 - 27FF</span></span>|`IsSupplementalArrows-A`|  
|<span data-ttu-id="7e8f8-542">2800 - 28FF</span><span class="sxs-lookup"><span data-stu-id="7e8f8-542">2800 - 28FF</span></span>|`IsBraillePatterns`|  
|<span data-ttu-id="7e8f8-543">2900 - 297F</span><span class="sxs-lookup"><span data-stu-id="7e8f8-543">2900 - 297F</span></span>|`IsSupplementalArrows-B`|  
|<span data-ttu-id="7e8f8-544">2980 - 29FF</span><span class="sxs-lookup"><span data-stu-id="7e8f8-544">2980 - 29FF</span></span>|`IsMiscellaneousMathematicalSymbols-B`|  
|<span data-ttu-id="7e8f8-545">2A00 - 2AFF</span><span class="sxs-lookup"><span data-stu-id="7e8f8-545">2A00 - 2AFF</span></span>|`IsSupplementalMathematicalOperators`|  
|<span data-ttu-id="7e8f8-546">2B00 - 2BFF</span><span class="sxs-lookup"><span data-stu-id="7e8f8-546">2B00 - 2BFF</span></span>|`IsMiscellaneousSymbolsandArrows`|  
|<span data-ttu-id="7e8f8-547">2E80 - 2EFF</span><span class="sxs-lookup"><span data-stu-id="7e8f8-547">2E80 - 2EFF</span></span>|`IsCJKRadicalsSupplement`|  
|<span data-ttu-id="7e8f8-548">2F00 - 2FDF</span><span class="sxs-lookup"><span data-stu-id="7e8f8-548">2F00 - 2FDF</span></span>|`IsKangxiRadicals`|  
|<span data-ttu-id="7e8f8-549">2FF0 - 2FFF</span><span class="sxs-lookup"><span data-stu-id="7e8f8-549">2FF0 - 2FFF</span></span>|`IsIdeographicDescriptionCharacters`|  
|<span data-ttu-id="7e8f8-550">3000 - 303F</span><span class="sxs-lookup"><span data-stu-id="7e8f8-550">3000 - 303F</span></span>|`IsCJKSymbolsandPunctuation`|  
|<span data-ttu-id="7e8f8-551">3040 - 309F</span><span class="sxs-lookup"><span data-stu-id="7e8f8-551">3040 - 309F</span></span>|`IsHiragana`|  
|<span data-ttu-id="7e8f8-552">30A0 - 30FF</span><span class="sxs-lookup"><span data-stu-id="7e8f8-552">30A0 - 30FF</span></span>|`IsKatakana`|  
|<span data-ttu-id="7e8f8-553">3100 - 312F</span><span class="sxs-lookup"><span data-stu-id="7e8f8-553">3100 - 312F</span></span>|`IsBopomofo`|  
|<span data-ttu-id="7e8f8-554">3130 - 318F</span><span class="sxs-lookup"><span data-stu-id="7e8f8-554">3130 - 318F</span></span>|`IsHangulCompatibilityJamo`|  
|<span data-ttu-id="7e8f8-555">3190 - 319F</span><span class="sxs-lookup"><span data-stu-id="7e8f8-555">3190 - 319F</span></span>|`IsKanbun`|  
|<span data-ttu-id="7e8f8-556">31A0 - 31BF</span><span class="sxs-lookup"><span data-stu-id="7e8f8-556">31A0 - 31BF</span></span>|`IsBopomofoExtended`|  
|<span data-ttu-id="7e8f8-557">31F0 - 31FF</span><span class="sxs-lookup"><span data-stu-id="7e8f8-557">31F0 - 31FF</span></span>|`IsKatakanaPhoneticExtensions`|  
|<span data-ttu-id="7e8f8-558">3200 - 32FF</span><span class="sxs-lookup"><span data-stu-id="7e8f8-558">3200 - 32FF</span></span>|`IsEnclosedCJKLettersandMonths`|  
|<span data-ttu-id="7e8f8-559">3300 - 33FF</span><span class="sxs-lookup"><span data-stu-id="7e8f8-559">3300 - 33FF</span></span>|`IsCJKCompatibility`|  
|<span data-ttu-id="7e8f8-560">3400 - 4DBF</span><span class="sxs-lookup"><span data-stu-id="7e8f8-560">3400 - 4DBF</span></span>|`IsCJKUnifiedIdeographsExtensionA`|  
|<span data-ttu-id="7e8f8-561">4DC0 - 4DFF</span><span class="sxs-lookup"><span data-stu-id="7e8f8-561">4DC0 - 4DFF</span></span>|`IsYijingHexagramSymbols`|  
|<span data-ttu-id="7e8f8-562">4E00 - 9FFF</span><span class="sxs-lookup"><span data-stu-id="7e8f8-562">4E00 - 9FFF</span></span>|`IsCJKUnifiedIdeographs`|  
|<span data-ttu-id="7e8f8-563">A000 - A48F</span><span class="sxs-lookup"><span data-stu-id="7e8f8-563">A000 - A48F</span></span>|`IsYiSyllables`|  
|<span data-ttu-id="7e8f8-564">A490 - A4CF</span><span class="sxs-lookup"><span data-stu-id="7e8f8-564">A490 - A4CF</span></span>|`IsYiRadicals`|  
|<span data-ttu-id="7e8f8-565">AC00 - D7AF</span><span class="sxs-lookup"><span data-stu-id="7e8f8-565">AC00 - D7AF</span></span>|`IsHangulSyllables`|  
|<span data-ttu-id="7e8f8-566">D800 - DB7F</span><span class="sxs-lookup"><span data-stu-id="7e8f8-566">D800 - DB7F</span></span>|`IsHighSurrogates`|  
|<span data-ttu-id="7e8f8-567">DB80 - DBFF</span><span class="sxs-lookup"><span data-stu-id="7e8f8-567">DB80 - DBFF</span></span>|`IsHighPrivateUseSurrogates`|  
|<span data-ttu-id="7e8f8-568">DC00 - DFFF</span><span class="sxs-lookup"><span data-stu-id="7e8f8-568">DC00 - DFFF</span></span>|`IsLowSurrogates`|  
|<span data-ttu-id="7e8f8-569">E000 - F8FF</span><span class="sxs-lookup"><span data-stu-id="7e8f8-569">E000 - F8FF</span></span>|<span data-ttu-id="7e8f8-570">`IsPrivateUse` 或 `IsPrivateUseArea`</span><span class="sxs-lookup"><span data-stu-id="7e8f8-570">`IsPrivateUse` or `IsPrivateUseArea`</span></span>|  
|<span data-ttu-id="7e8f8-571">F900 - FAFF</span><span class="sxs-lookup"><span data-stu-id="7e8f8-571">F900 - FAFF</span></span>|`IsCJKCompatibilityIdeographs`|  
|<span data-ttu-id="7e8f8-572">FB00 - FB4F</span><span class="sxs-lookup"><span data-stu-id="7e8f8-572">FB00 - FB4F</span></span>|`IsAlphabeticPresentationForms`|  
|<span data-ttu-id="7e8f8-573">FB50 - FDFF</span><span class="sxs-lookup"><span data-stu-id="7e8f8-573">FB50 - FDFF</span></span>|`IsArabicPresentationForms-A`|  
|<span data-ttu-id="7e8f8-574">FE00 - FE0F</span><span class="sxs-lookup"><span data-stu-id="7e8f8-574">FE00 - FE0F</span></span>|`IsVariationSelectors`|  
|<span data-ttu-id="7e8f8-575">FE20 - FE2F</span><span class="sxs-lookup"><span data-stu-id="7e8f8-575">FE20 - FE2F</span></span>|`IsCombiningHalfMarks`|  
|<span data-ttu-id="7e8f8-576">FE30 - FE4F</span><span class="sxs-lookup"><span data-stu-id="7e8f8-576">FE30 - FE4F</span></span>|`IsCJKCompatibilityForms`|  
|<span data-ttu-id="7e8f8-577">FE50 - FE6F</span><span class="sxs-lookup"><span data-stu-id="7e8f8-577">FE50 - FE6F</span></span>|`IsSmallFormVariants`|  
|<span data-ttu-id="7e8f8-578">FE70 - FEFF</span><span class="sxs-lookup"><span data-stu-id="7e8f8-578">FE70 - FEFF</span></span>|`IsArabicPresentationForms-B`|  
|<span data-ttu-id="7e8f8-579">FF00 - FFEF</span><span class="sxs-lookup"><span data-stu-id="7e8f8-579">FF00 - FFEF</span></span>|`IsHalfwidthandFullwidthForms`|  
|<span data-ttu-id="7e8f8-580">FFF0 - FFFF</span><span class="sxs-lookup"><span data-stu-id="7e8f8-580">FFF0 - FFFF</span></span>|`IsSpecials`|  
  
<a name="CharacterClassSubtraction"></a>
## <a name="character-class-subtraction-base_group---excluded_group"></a><span data-ttu-id="7e8f8-581">字符类减法：[base_group - [excluded_group]]</span><span class="sxs-lookup"><span data-stu-id="7e8f8-581">Character class subtraction: [base_group - [excluded_group]]</span></span>  
 <span data-ttu-id="7e8f8-582">一个字符类定义一组字符。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-582">A character class defines a set of characters.</span></span> <span data-ttu-id="7e8f8-583">字符类减法将产生一组字符，该组字符是从一个字符类中排除另一个字符类中的字符的结果。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-583">Character class subtraction yields a set of characters that is the result of excluding the characters in one character class from another character class.</span></span>  
  
 <span data-ttu-id="7e8f8-584">字符类减法表达式具有以下形式：</span><span class="sxs-lookup"><span data-stu-id="7e8f8-584">A character class subtraction expression has the following form:</span></span>  
  
 <span data-ttu-id="7e8f8-585">`[` *base_group* `-[` *excluded_group* `]]`</span><span class="sxs-lookup"><span data-stu-id="7e8f8-585">`[` *base_group* `-[` *excluded_group* `]]`</span></span>  
  
 <span data-ttu-id="7e8f8-586">方括号 (`[]`) 和连字符 (`-`) 是强制的。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-586">The square brackets (`[]`) and hyphen (`-`) are mandatory.</span></span> <span data-ttu-id="7e8f8-587">base_group  是[正字符组](#PositiveGroup)或[负字符组](#NegativeGroup)。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-587">The *base_group* is a [positive character group](#PositiveGroup) or a [negative character group](#NegativeGroup).</span></span> <span data-ttu-id="7e8f8-588">*excluded_group* 部分是另一个正字符组或负字符组，或者是另一个字符类减法表达式（即，可以嵌套字符类减法表达式）。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-588">The *excluded_group* component is another positive or negative character group, or another character class subtraction expression (that is, you can nest character class subtraction expressions).</span></span>  
  
 <span data-ttu-id="7e8f8-589">例如，假设你有一个由从“a”至“z”范围内的字符组成的基本组。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-589">For example, suppose you have a base group that consists of the character range from "a" through "z".</span></span> <span data-ttu-id="7e8f8-590">若要定义由除字符“m”之外的基本组组成的字符集，请使用 `[a-z-[m]]`。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-590">To define the set of characters that consists of the base group except for the character "m", use `[a-z-[m]]`.</span></span> <span data-ttu-id="7e8f8-591">若要定义由除字符集“d”、“j”和“p”之外的基本组组成的字符集，请使用 `[a-z-[djp]]`。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-591">To define the set of characters that consists of the base group except for the set of characters "d", "j", and "p", use `[a-z-[djp]]`.</span></span> <span data-ttu-id="7e8f8-592">若要定义由除从“m”至“p”字符范围之外的基本组组成的字符集，请使用 `[a-z-[m-p]]`。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-592">To define the set of characters that consists of the base group except for the character range from "m" through "p", use `[a-z-[m-p]]`.</span></span>  
  
 <span data-ttu-id="7e8f8-593">可考虑使用嵌套字符类减法表达式 `[a-z-[d-w-[m-o]]]`。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-593">Consider the nested character class subtraction expression, `[a-z-[d-w-[m-o]]]`.</span></span> <span data-ttu-id="7e8f8-594">该表达式由最里面的字符范围向外计算。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-594">The expression is evaluated from the innermost character range outward.</span></span> <span data-ttu-id="7e8f8-595">首先，在从“d”至“w”的字符范围中减去从“m”至“o”的字符范围，这将产生从“d”至“l”和从“p”至“w”的字符集。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-595">First, the character range from "m" through "o" is subtracted from the character range "d" through "w", which yields the set of characters from "d" through "l" and "p" through "w".</span></span> <span data-ttu-id="7e8f8-596">然后，在从“a”至“z”的字符范围中减去该集合，这将产生字符集 `[abcmnoxyz]`。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-596">That set is then subtracted from the character range from "a" through "z", which yields the set of characters `[abcmnoxyz]`.</span></span>  
  
 <span data-ttu-id="7e8f8-597">可以将任何字符类用于字符类减法。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-597">You can use any character class with character class subtraction.</span></span> <span data-ttu-id="7e8f8-598">若要定义字符集，且该字符集包括除空白字符 (`\s`)、标点通用类别中的字符 (`\p{P}`)、`IsGreek` 命名块中的字符 (`\p{IsGreek}`) 以及 Unicode NEXT LINE 控制字符 (\x85) 之外的所有从 \u0000 至 \uFFFF 的 Unicode 字符，请使用 `[\u0000-\uFFFF-[\s\p{P}\p{IsGreek}\x85]]`。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-598">To define the set of characters that consists of all Unicode characters from \u0000 through \uFFFF except white-space characters (`\s`), the characters in the punctuation general category (`\p{P}`), the characters in the `IsGreek` named block (`\p{IsGreek}`), and the Unicode NEXT LINE control character (\x85), use `[\u0000-\uFFFF-[\s\p{P}\p{IsGreek}\x85]]`.</span></span>  
  
 <span data-ttu-id="7e8f8-599">为字符类减法表达式选择将会产生有用结果的字符类。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-599">Choose character classes for a character class subtraction expression that will yield useful results.</span></span> <span data-ttu-id="7e8f8-600">避免使用产生空字符集的表达式，这将无法匹配任何内容，同时避免使用等效于初始基本组的表达式。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-600">Avoid an expression that yields an empty set of characters, which cannot match anything, or an expression that is equivalent to the original base group.</span></span> <span data-ttu-id="7e8f8-601">例如，表达式 `[\p{IsBasicLatin}-[\x00-\x7F]]` 从 `IsBasicLatin` 常规类别中减去 `IsBasicLatin` 字符范围内的所有字符，其结果为空集合。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-601">For example, the empty set is the result of the expression `[\p{IsBasicLatin}-[\x00-\x7F]]`, which subtracts all characters in the `IsBasicLatin` character range from the `IsBasicLatin` general category.</span></span> <span data-ttu-id="7e8f8-602">类似地，表达式 `[a-z-[0-9]]` 的结果为初始基本组。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-602">Similarly, the original base group is the result of the expression `[a-z-[0-9]]`.</span></span>  <span data-ttu-id="7e8f8-603">这是因为，基本组（它是从“a”至“z”的字母组成的字符范围）不包含排除组（它是从“0”至“9”的十进制数组成的字符范围）中的任何字符。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-603">This is because the base group, which is the character range of letters from "a" through "z", does not contain any characters in the excluded group, which is the character range of decimal digits from "0" through "9".</span></span>  
  
 <span data-ttu-id="7e8f8-604">下面的示例定义正则表达式 `^[0-9-[2468]]+$`，该表达式匹配输入字符串中的零和奇数。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-604">The following example defines a regular expression, `^[0-9-[2468]]+$`, that matches zero and odd digits in an input string.</span></span>  <span data-ttu-id="7e8f8-605">正则表达式模式可以解释为下表中所示内容。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-605">The regular expression is interpreted as shown in the following table.</span></span>  
  
|<span data-ttu-id="7e8f8-606">元素</span><span class="sxs-lookup"><span data-stu-id="7e8f8-606">Element</span></span>|<span data-ttu-id="7e8f8-607">描述</span><span class="sxs-lookup"><span data-stu-id="7e8f8-607">Description</span></span>|  
|-------------|-----------------|  
|^|<span data-ttu-id="7e8f8-608">从输入字符串的开头处开始进行匹配。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-608">Begin the match at the start of the input string.</span></span>|  
|`[0-9-[2468]]+`|<span data-ttu-id="7e8f8-609">匹配任意字符（从 0 到 9，除了 2、4、6 和 8 之外）的一个或多个匹配项。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-609">Match one or more occurrences of any character from 0 to 9 except for 2, 4, 6, and 8.</span></span> <span data-ttu-id="7e8f8-610">换句话说，匹配零或奇数的一个或多个匹配项。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-610">In other words, match one or more occurrences of zero or an odd digit.</span></span>|  
|$|<span data-ttu-id="7e8f8-611">在输入字符串末尾结束匹配。</span><span class="sxs-lookup"><span data-stu-id="7e8f8-611">End the match at the end of the input string.</span></span>|  
  
 [!code-csharp[Conceptual.RegEx.Language.CharacterClasses#15](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.characterclasses/cs/classsubtraction1.cs#15)]
 [!code-vb[Conceptual.RegEx.Language.CharacterClasses#15](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.characterclasses/vb/classsubtraction1.vb#15)]  
  
## <a name="see-also"></a><span data-ttu-id="7e8f8-612">请参阅</span><span class="sxs-lookup"><span data-stu-id="7e8f8-612">See also</span></span>

- <xref:System.Char.GetUnicodeCategory%2A>
- [<span data-ttu-id="7e8f8-613">正则表达式语言 - 快速参考</span><span class="sxs-lookup"><span data-stu-id="7e8f8-613">Regular Expression Language - Quick Reference</span></span>](../../../docs/standard/base-types/regular-expression-language-quick-reference.md)
- [<span data-ttu-id="7e8f8-614">正则表达式选项</span><span class="sxs-lookup"><span data-stu-id="7e8f8-614">Regular Expression Options</span></span>](../../../docs/standard/base-types/regular-expression-options.md)
