---
title: 文档标记分隔符 - C# 编程指南
ms.date: 07/20/2015
helpviewer_keywords:
- XML [C#], delimiters
- /** */ delimiters for C# documentation tags
- /// delimiter for C# documentation
ms.assetid: 9b2bdd18-4f5c-4c0b-988e-fb992e0d233e
ms.openlocfilehash: dd4ddb3b324bd6d235efb541c90875dbe9ed4c2d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/14/2020
ms.locfileid: "76789822"
---
# <a name="delimiters-for-documentation-tags-c-programming-guide"></a><span data-ttu-id="dfb1b-102">文档标记分隔符（C# 编程指南）</span><span class="sxs-lookup"><span data-stu-id="dfb1b-102">Delimiters for documentation tags (C# programming guide)</span></span>

<span data-ttu-id="dfb1b-103">XML 文档注释需要使用分隔符，用来向编译器指示文档注释开始和结束的位置。</span><span class="sxs-lookup"><span data-stu-id="dfb1b-103">The use of XML doc comments requires delimiters, which indicate to the compiler where a documentation comment begins and ends.</span></span> <span data-ttu-id="dfb1b-104">可以使用以下采用 XML 文档标记的分隔符：</span><span class="sxs-lookup"><span data-stu-id="dfb1b-104">You can use the following kinds of delimiters with the XML documentation tags:</span></span>

- `///`

  <span data-ttu-id="dfb1b-105">单行分隔符。</span><span class="sxs-lookup"><span data-stu-id="dfb1b-105">Single-line delimiter.</span></span> <span data-ttu-id="dfb1b-106">这是在文档示例中显示的格式，由 Visual C# 项目模板使用。</span><span class="sxs-lookup"><span data-stu-id="dfb1b-106">This is the form that is shown in documentation examples and used by the Visual C# project templates.</span></span> <span data-ttu-id="dfb1b-107">如果在分隔符后面有一个空格字符，那么此字符不会包括在 XML 输出中。</span><span class="sxs-lookup"><span data-stu-id="dfb1b-107">If there is a white space character following the delimiter, that character is not included in the XML output.</span></span>

  > [!NOTE]
  > <span data-ttu-id="dfb1b-108">Visual Studio IDE 具有一种称为智能注释编辑的功能，在代码编辑器中键入 `///` 分隔符后，此功能可自动插入 \<summary> 和 \</summary> 标记，并在此标记中移动游标。</span><span class="sxs-lookup"><span data-stu-id="dfb1b-108">The Visual Studio IDE has a feature called Smart Comment Editing that automatically inserts the \<summary> and \</summary> tags and moves your cursor within these tags after you type the `///` delimiter in the Code Editor.</span></span> <span data-ttu-id="dfb1b-109">可以在[“选项”对话框](/visualstudio/ide/reference/options-text-editor-csharp-advanced)中打开/关闭此功能。</span><span class="sxs-lookup"><span data-stu-id="dfb1b-109">You can turn this feature on or off in the [Options dialog box](/visualstudio/ide/reference/options-text-editor-csharp-advanced).</span></span>
  
- `/** */`

  <span data-ttu-id="dfb1b-110">多行分隔符。</span><span class="sxs-lookup"><span data-stu-id="dfb1b-110">Multiline delimiters.</span></span>

  <span data-ttu-id="dfb1b-111">使用 `/** */` 分隔符时需遵守一些格式设置规则：</span><span class="sxs-lookup"><span data-stu-id="dfb1b-111">There are some formatting rules to follow when you use the `/** */` delimiters:</span></span>
  
  - <span data-ttu-id="dfb1b-112">在包含 `/**` 分隔符的行上，如果行的其余部分为空格，则不将此行作为注释处理。</span><span class="sxs-lookup"><span data-stu-id="dfb1b-112">On the line that contains the `/**` delimiter, if the remainder of the line is white space, the line is not processed for comments.</span></span> <span data-ttu-id="dfb1b-113">如果 `/**` 分隔符后面的第一个字符为空格，则忽略此空格字符，并处理行的其余部分。</span><span class="sxs-lookup"><span data-stu-id="dfb1b-113">If the first character after the `/**` delimiter is white space, that white space character is ignored and the rest of the line is processed.</span></span> <span data-ttu-id="dfb1b-114">否则，将 `/**` 分隔符后面的行的所有文本作为注释的一部分进行处理。</span><span class="sxs-lookup"><span data-stu-id="dfb1b-114">Otherwise, the entire text of the line after the `/**` delimiter is processed as part of the comment.</span></span>

  - <span data-ttu-id="dfb1b-115">在包含 `*/` 分隔符的行中，如果 `*/` 分隔符前面只有空格，此行将被忽略。</span><span class="sxs-lookup"><span data-stu-id="dfb1b-115">On the line that contains the `*/` delimiter, if there is only white space up to the `*/` delimiter, that line is ignored.</span></span> <span data-ttu-id="dfb1b-116">否则，`*/` 分隔符前面的行的文本被处理为注释的一部分，并且需符合后面的项目符号所描述的模式匹配规则。</span><span class="sxs-lookup"><span data-stu-id="dfb1b-116">Otherwise, the text on the line up to the `*/` delimiter is processed as part of the comment, subject to the pattern-matching rules described in the following bullet.</span></span>
  
  - <span data-ttu-id="dfb1b-117">对于以 `/**` 分隔符开头的行后面的行，编译器在各行的开头寻找共同模式。</span><span class="sxs-lookup"><span data-stu-id="dfb1b-117">For the lines after the one that begins with the `/**` delimiter, the compiler looks for a common pattern at the beginning of each line.</span></span> <span data-ttu-id="dfb1b-118">此模式可以包含空格和星号 (`*`)，后面跟更多空格。</span><span class="sxs-lookup"><span data-stu-id="dfb1b-118">The pattern can consist of optional white space and an asterisk (`*`), followed by more optional white space.</span></span> <span data-ttu-id="dfb1b-119">如果编译器在不以 `/**` 分隔符或 `*/` 分隔符开头的各行开头找到共同模式，则忽略此每个行的模式。</span><span class="sxs-lookup"><span data-stu-id="dfb1b-119">If the compiler finds a common pattern at the beginning of each line that does not begin with the `/**` delimiter or the `*/` delimiter, it ignores that pattern for each line.</span></span>

  <span data-ttu-id="dfb1b-120">以下示例说明了这些规则。</span><span class="sxs-lookup"><span data-stu-id="dfb1b-120">The following examples illustrate these rules.</span></span>

  - <span data-ttu-id="dfb1b-121">以下注释中将被处理的唯一部分是以 `<summary>` 开头的行。</span><span class="sxs-lookup"><span data-stu-id="dfb1b-121">The only part of the following comment that will be processed is the line that begins with `<summary>`.</span></span> <span data-ttu-id="dfb1b-122">三种标记格式产生的注释相同。</span><span class="sxs-lookup"><span data-stu-id="dfb1b-122">The three tag formats produce the same comments.</span></span>

    ```csharp
    /** <summary>text</summary> */

    /**
    <summary>text</summary>
    */

    /**
     * <summary>text</summary>
    */
    ```

  - <span data-ttu-id="dfb1b-123">编译器识别出第二和第三行开头的共同模式“\*”。</span><span class="sxs-lookup"><span data-stu-id="dfb1b-123">The compiler identifies a common pattern of " \* " at the beginning of the second and third lines.</span></span> <span data-ttu-id="dfb1b-124">此模式不包括在输出中。</span><span class="sxs-lookup"><span data-stu-id="dfb1b-124">The pattern is not included in the output.</span></span>

    ```csharp
    /**
     * <summary>
     * text </summary>*/
    ```

  - <span data-ttu-id="dfb1b-125">编译器在下面的注释中未找到共同模式，因为第三行的第二个字符不是一个星号。</span><span class="sxs-lookup"><span data-stu-id="dfb1b-125">The compiler finds no common pattern in the following comment because the second character on the third line is not an asterisk.</span></span> <span data-ttu-id="dfb1b-126">因此，第二和第三行上的所有文本将处理为注释的一部分。</span><span class="sxs-lookup"><span data-stu-id="dfb1b-126">Therefore, all text on the second and third lines is processed as part of the comment.</span></span>

    ```csharp
    /**
     * <summary>
       text </summary>
    */
    ```

  - <span data-ttu-id="dfb1b-127">编译器在以下注释中未找到模式，原因有两个。</span><span class="sxs-lookup"><span data-stu-id="dfb1b-127">The compiler finds no pattern in the following comment for two reasons.</span></span> <span data-ttu-id="dfb1b-128">首先，星号前的空格数不一致。</span><span class="sxs-lookup"><span data-stu-id="dfb1b-128">First, the number of spaces before the asterisk is not consistent.</span></span> <span data-ttu-id="dfb1b-129">其次，第 5 行以制表符开头，这与空格不匹配。</span><span class="sxs-lookup"><span data-stu-id="dfb1b-129">Second, the fifth line begins with a tab, which does not match spaces.</span></span> <span data-ttu-id="dfb1b-130">因此，第二到第五行的所有文本都作为注释的一部分进行处理。</span><span class="sxs-lookup"><span data-stu-id="dfb1b-130">Therefore, all text from lines two through five is processed as part of the comment.</span></span>

    <!-- markdownlint-disable MD010 -->
    ```csharp
    /**
      * <summary>
      * text
     *  text2
        *  </summary>
    */
    ```
    <!-- markdownlint-enable MD010 -->

## <a name="see-also"></a><span data-ttu-id="dfb1b-131">另请参阅</span><span class="sxs-lookup"><span data-stu-id="dfb1b-131">See also</span></span>

- [<span data-ttu-id="dfb1b-132">C# 编程指南</span><span class="sxs-lookup"><span data-stu-id="dfb1b-132">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="dfb1b-133">XML 文档注释</span><span class="sxs-lookup"><span data-stu-id="dfb1b-133">XML documentation comments</span></span>](./index.md)
- [<span data-ttu-id="dfb1b-134">-doc（C# 编译器选项）</span><span class="sxs-lookup"><span data-stu-id="dfb1b-134">-doc (C# compiler options)</span></span>](../../language-reference/compiler-options/doc-compiler-option.md)
