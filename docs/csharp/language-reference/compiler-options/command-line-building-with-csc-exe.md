---
title: 使用 csc.exe 实现命令行生成
ms.date: 04/19/2017
helpviewer_keywords:
- builds [C#]
- command line [C#]
ms.assetid: 66e70056-dd20-453c-a9b3-507e0478b015
ms.openlocfilehash: f692e66672b1804a309c6ac04c158af948a1b1ab
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/14/2020
ms.locfileid: "76789860"
---
# <a name="command-line-build-with-cscexe"></a><span data-ttu-id="6f6ad-102">使用 csc.exe 实现命令行生成</span><span class="sxs-lookup"><span data-stu-id="6f6ad-102">Command-line build with csc.exe</span></span>

<span data-ttu-id="6f6ad-103">通过在命令提示符处键入 C# 编译器的可执行文件名称 (csc.exe  )，可调用该编译器。</span><span class="sxs-lookup"><span data-stu-id="6f6ad-103">You can invoke the C# compiler by typing the name of its executable file (*csc.exe*) at a command prompt.</span></span>

<span data-ttu-id="6f6ad-104">如果使用“Visual Studio 开发人员命令提示”  窗口，系统将设置所有必需的环境变量。</span><span class="sxs-lookup"><span data-stu-id="6f6ad-104">If you use the **Developer Command Prompt for Visual Studio** window, all the necessary environment variables are set for you.</span></span> <span data-ttu-id="6f6ad-105">有关如何访问此工具的信息，请参阅 [Visual Studio 开发人员命令提示](../../../framework/tools/developer-command-prompt-for-vs.md)主题。</span><span class="sxs-lookup"><span data-stu-id="6f6ad-105">For information on how to access this tool, see the [Developer Command Prompt for Visual Studio](../../../framework/tools/developer-command-prompt-for-vs.md) topic.</span></span>

<span data-ttu-id="6f6ad-106">如果使用标准命令提示符窗口，则必须调整路径，然后才能从计算机的任意子目录调用 csc.exe  。</span><span class="sxs-lookup"><span data-stu-id="6f6ad-106">If you use a standard Command Prompt window, you must adjust your path before you can invoke *csc.exe* from any subdirectory on your computer.</span></span> <span data-ttu-id="6f6ad-107">还必须运行 vsvars32.bat  来设置适当的环境变量以支持命令行生成操作。</span><span class="sxs-lookup"><span data-stu-id="6f6ad-107">You also must run *vsvars32.bat* to set the appropriate environment variables to support command-line builds.</span></span> <span data-ttu-id="6f6ad-108">有关 vsvars32.bat  的详细信息，包括如何查找和运行它的说明，请参阅[如何为 Visual Studio 命令行设置环境变量](./how-to-set-environment-variables-for-the-visual-studio-command-line.md)。</span><span class="sxs-lookup"><span data-stu-id="6f6ad-108">For more information about *vsvars32.bat*, including instructions for how to find and run it, see [How to set environment variables for the Visual Studio Command Line](./how-to-set-environment-variables-for-the-visual-studio-command-line.md).</span></span>

<span data-ttu-id="6f6ad-109">如果你使用的计算机只安装有 Windows 软件开发工具包 (SDK)，则可以在“SDK 命令提示符”  处使用 C# 编译器，该窗口可通过“Microsoft .NET Framework SDK”  菜单选项打开。</span><span class="sxs-lookup"><span data-stu-id="6f6ad-109">If you're working on a computer that has only the Windows Software Development Kit (SDK), you can use the C# compiler at the **SDK Command Prompt**, which you open from the **Microsoft .NET Framework SDK** menu option.</span></span>

<span data-ttu-id="6f6ad-110">也可以使用 MSBuild 以编程方式生成 C# 程序。</span><span class="sxs-lookup"><span data-stu-id="6f6ad-110">You can also use MSBuild to build C# programs programmatically.</span></span> <span data-ttu-id="6f6ad-111">有关详细信息，请参阅 [MSBuild](/visualstudio/msbuild/msbuild)。</span><span class="sxs-lookup"><span data-stu-id="6f6ad-111">For more information, see [MSBuild](/visualstudio/msbuild/msbuild).</span></span>

<span data-ttu-id="6f6ad-112">csc.exe 可执行文件通常位于 Windows 目录下的 Microsoft.NET\Framework\\\<Version> 文件夹中。</span><span class="sxs-lookup"><span data-stu-id="6f6ad-112">The *csc.exe* executable file usually is located in the Microsoft.NET\Framework\\*\<Version>* folder under the *Windows* directory.</span></span> <span data-ttu-id="6f6ad-113">根据每台计算机上的具体配置，此位置可能有所不同。</span><span class="sxs-lookup"><span data-stu-id="6f6ad-113">Its location might vary depending on the exact configuration of a particular computer.</span></span> <span data-ttu-id="6f6ad-114">如果计算机上安装了不止一个版本的 .NET Framework，您将发现此文件的多个版本。</span><span class="sxs-lookup"><span data-stu-id="6f6ad-114">If more than one version of the .NET Framework is installed on your computer, you'll find multiple versions of this file.</span></span> <span data-ttu-id="6f6ad-115">有关此类安装的详细信息，请参阅[如何：确定安装的 .NET Framework 版本](../../../framework/migration-guide/how-to-determine-which-versions-are-installed.md)。</span><span class="sxs-lookup"><span data-stu-id="6f6ad-115">For more information about such installations, see [How to: determine which versions of the .NET Framework are installed](../../../framework/migration-guide/how-to-determine-which-versions-are-installed.md).</span></span>

> [!TIP]
> <span data-ttu-id="6f6ad-116">使用 Visual Studio IDE 生成项目时，可以在 **“输出”** 窗口显示 **“csc”** 命令以及与之关联的编译器选项。</span><span class="sxs-lookup"><span data-stu-id="6f6ad-116">When you build a project by using the Visual Studio IDE, you can display the **csc** command and its associated compiler options in the **Output** window.</span></span> <span data-ttu-id="6f6ad-117">若要显示此信息，请按照[如何：查看、保存和配置生成日志文件](/visualstudio/ide/how-to-view-save-and-configure-build-log-files#to-change-the-amount-of-information-included-in-the-build-log)中的说明将日志数据的详细级别更改为 **“常规”** 或 **“详细”** 。</span><span class="sxs-lookup"><span data-stu-id="6f6ad-117">To display this information, follow the instructions in [How to: View, Save, and Configure Build Log Files](/visualstudio/ide/how-to-view-save-and-configure-build-log-files#to-change-the-amount-of-information-included-in-the-build-log) to change the verbosity level of the log data to **Normal** or **Detailed**.</span></span> <span data-ttu-id="6f6ad-118">重新生成项目之后，在 **“输出”** 窗口中搜索 **“csc”** 即可找到所调用的 C# 编译器。</span><span class="sxs-lookup"><span data-stu-id="6f6ad-118">After you rebuild your project, search the **Output** window for **csc** to find the invocation of the C# compiler.</span></span>

 <span data-ttu-id="6f6ad-119">**在本主题中**</span><span class="sxs-lookup"><span data-stu-id="6f6ad-119">**In this topic**</span></span>

- [<span data-ttu-id="6f6ad-120">命令行语法规则</span><span class="sxs-lookup"><span data-stu-id="6f6ad-120">Rules for command-line syntax</span></span>](#rules-for-command-line-syntax-for-the-c-compiler)

- [<span data-ttu-id="6f6ad-121">示例命令行</span><span class="sxs-lookup"><span data-stu-id="6f6ad-121">Sample command lines</span></span>](#sample-command-lines-for-the-c-compiler)

- [<span data-ttu-id="6f6ad-122">C# 编译器和 C++ 编译器输出之间的差异</span><span class="sxs-lookup"><span data-stu-id="6f6ad-122">Differences between C# compiler and C++ compiler output</span></span>](#differences-between-c-compiler-and-c-compiler-output)

## <a name="rules-for-command-line-syntax-for-the-c-compiler"></a><span data-ttu-id="6f6ad-123">C# 编译器的命令行语法规则</span><span class="sxs-lookup"><span data-stu-id="6f6ad-123">Rules for command-line syntax for the C# compiler</span></span>

<span data-ttu-id="6f6ad-124">在解释操作系统命令行上给出的参数时，C# 编译器使用下列规则：</span><span class="sxs-lookup"><span data-stu-id="6f6ad-124">The C# compiler uses the following rules when it interprets arguments given on the operating system command line:</span></span>

- <span data-ttu-id="6f6ad-125">参数用空白分隔，空白可以是一个空格或制表符。</span><span class="sxs-lookup"><span data-stu-id="6f6ad-125">Arguments are delimited by white space, which is either a space or a tab.</span></span>

- <span data-ttu-id="6f6ad-126">插入符号 (^) 未被识别为转义符或者分隔符。</span><span class="sxs-lookup"><span data-stu-id="6f6ad-126">The caret character (^) is not recognized as an escape character or delimiter.</span></span> <span data-ttu-id="6f6ad-127">在传递给程序中的 `argv` 数组之前，该字符由操作系统中的命令行分析器处理。</span><span class="sxs-lookup"><span data-stu-id="6f6ad-127">The character is handled by the command-line parser in the operating system before it's passed to the `argv` array in the program.</span></span>

- <span data-ttu-id="6f6ad-128">无论其中有无空白，包含在双引号 ("string") 中的字符串均被解释为单个参数。</span><span class="sxs-lookup"><span data-stu-id="6f6ad-128">A string enclosed in double quotation marks ("string") is interpreted as a single argument, regardless of white space that is contained within.</span></span> <span data-ttu-id="6f6ad-129">带引号的字符串可以嵌入在自变量内。</span><span class="sxs-lookup"><span data-stu-id="6f6ad-129">A quoted string can be embedded in an argument.</span></span>

- <span data-ttu-id="6f6ad-130">前面有反斜杠的双引号 (\\") 被解释为原义双引号字符 (")。</span><span class="sxs-lookup"><span data-stu-id="6f6ad-130">A double quotation mark preceded by a backslash (\\") is interpreted as a literal double quotation mark character (").</span></span>

- <span data-ttu-id="6f6ad-131">反斜杠按其原义解释，除非它们紧位于双引号之前。</span><span class="sxs-lookup"><span data-stu-id="6f6ad-131">Backslashes are interpreted literally, unless they immediately precede a double quotation mark.</span></span>

- <span data-ttu-id="6f6ad-132">如果偶数个反斜杠后跟双引号，则每对反斜杠中有一个反斜杠被置于 `argv` 数组中，而双引号被解释为字符串分隔符。</span><span class="sxs-lookup"><span data-stu-id="6f6ad-132">If an even number of backslashes is followed by a double quotation mark, one backslash is put in the `argv` array for every pair of backslashes, and the double quotation mark is interpreted as a string delimiter.</span></span>

- <span data-ttu-id="6f6ad-133">如果奇数个反斜杠后跟双引号，则每对反斜杠中有一个反斜杠被置于 `argv` 数组中，而双引号由剩余反斜杠进行“转义”。</span><span class="sxs-lookup"><span data-stu-id="6f6ad-133">If an odd number of backslashes is followed by a double quotation mark, one backslash is put in the `argv` array for every pair of backslashes, and the double quotation mark is "escaped" by the remaining backslash.</span></span> <span data-ttu-id="6f6ad-134">这将在 `argv` 中添加一个原义双引号 (")。</span><span class="sxs-lookup"><span data-stu-id="6f6ad-134">This causes a literal double quotation mark (") to be added in `argv`.</span></span>

## <a name="sample-command-lines-for-the-c-compiler"></a><span data-ttu-id="6f6ad-135">C# 编译器的示例命令行</span><span class="sxs-lookup"><span data-stu-id="6f6ad-135">Sample command lines for the C# compiler</span></span>

- <span data-ttu-id="6f6ad-136">编译生成 File.exe 的 File.cs：</span><span class="sxs-lookup"><span data-stu-id="6f6ad-136">Compiles *File.cs* producing *File.exe*:</span></span>

  ```console
  csc File.cs
  ```

- <span data-ttu-id="6f6ad-137">编译生成 File.dll 的 File.cs：</span><span class="sxs-lookup"><span data-stu-id="6f6ad-137">Compiles *File.cs* producing *File.dll*:</span></span>

  ```console
  csc -target:library File.cs
  ```

- <span data-ttu-id="6f6ad-138">编译 File.cs  并创建 My.exe  ：</span><span class="sxs-lookup"><span data-stu-id="6f6ad-138">Compiles *File.cs* and creates *My.exe*:</span></span>

  ```console
  csc -out:My.exe File.cs
  ```

- <span data-ttu-id="6f6ad-139">编译当前目录中的所有 C# 文件，对其进行优化并定义 DEBUG 符号。</span><span class="sxs-lookup"><span data-stu-id="6f6ad-139">Compiles all the C# files in the current directory with optimizations enabled and defines the DEBUG symbol.</span></span> <span data-ttu-id="6f6ad-140">输出为 File2.exe  ：</span><span class="sxs-lookup"><span data-stu-id="6f6ad-140">The output is *File2.exe*:</span></span>

  ```console
  csc -define:DEBUG -optimize -out:File2.exe *.cs
  ```

- <span data-ttu-id="6f6ad-141">编译当前目录中的所有 C# 文件，生成 File2.dll  的调试版本。</span><span class="sxs-lookup"><span data-stu-id="6f6ad-141">Compiles all the C# files in the current directory producing a debug version of *File2.dll*.</span></span> <span data-ttu-id="6f6ad-142">不显示徽标和警告：</span><span class="sxs-lookup"><span data-stu-id="6f6ad-142">No logo and no warnings are displayed:</span></span>

  ```console
  csc -target:library -out:File2.dll -warn:0 -nologo -debug *.cs
  ```

- <span data-ttu-id="6f6ad-143">将当前目录中的所有 C# 文件编译为 Something.xyz  (DLL)：</span><span class="sxs-lookup"><span data-stu-id="6f6ad-143">Compiles all the C# files in the current directory to *Something.xyz* (a DLL):</span></span>

  ```console
  csc -target:library -out:Something.xyz *.cs
  ```

## <a name="differences-between-c-compiler-and-c-compiler-output"></a><span data-ttu-id="6f6ad-144">C# 编译器和 C++ 编译器输出之间的差异</span><span class="sxs-lookup"><span data-stu-id="6f6ad-144">Differences between C# compiler and C++ compiler output</span></span>

<span data-ttu-id="6f6ad-145">调用 C# 编译器时，不会创建任何对象 (.obj)  文件，而是直接创建输出文件。</span><span class="sxs-lookup"><span data-stu-id="6f6ad-145">There are no object (*.obj*) files created as a result of invoking the C# compiler; output files are created directly.</span></span> <span data-ttu-id="6f6ad-146">因此，C# 编译器不需要链接器。</span><span class="sxs-lookup"><span data-stu-id="6f6ad-146">As a result of this, the C# compiler does not need a linker.</span></span>

## <a name="see-also"></a><span data-ttu-id="6f6ad-147">另请参阅</span><span class="sxs-lookup"><span data-stu-id="6f6ad-147">See also</span></span>

- [<span data-ttu-id="6f6ad-148">C# 编译器选项</span><span class="sxs-lookup"><span data-stu-id="6f6ad-148">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="6f6ad-149">按字母顺序列出的 C# 编译器选项</span><span class="sxs-lookup"><span data-stu-id="6f6ad-149">C# Compiler Options Listed Alphabetically</span></span>](./listed-alphabetically.md)
- [<span data-ttu-id="6f6ad-150">按类别列出的 C# 编译器选项</span><span class="sxs-lookup"><span data-stu-id="6f6ad-150">C# Compiler Options Listed by Category</span></span>](./listed-by-category.md)
- [<span data-ttu-id="6f6ad-151">Main() 和命令行参数</span><span class="sxs-lookup"><span data-stu-id="6f6ad-151">Main() and Command-Line Arguments</span></span>](../../programming-guide/main-and-command-args/index.md)
- [<span data-ttu-id="6f6ad-152">命令行参数</span><span class="sxs-lookup"><span data-stu-id="6f6ad-152">Command-Line Arguments</span></span>](../../programming-guide/main-and-command-args/command-line-arguments.md)
- [<span data-ttu-id="6f6ad-153">如何显示命令行参数</span><span class="sxs-lookup"><span data-stu-id="6f6ad-153">How to display command-line arguments</span></span>](../../programming-guide/main-and-command-args/how-to-display-command-line-arguments.md)
- [<span data-ttu-id="6f6ad-154">Main() 返回值</span><span class="sxs-lookup"><span data-stu-id="6f6ad-154">Main() Return Values</span></span>](../../programming-guide/main-and-command-args/main-return-values.md)
