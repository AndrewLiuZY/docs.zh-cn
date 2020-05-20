---
title: -bugreport（C# 编译器选项）
ms.date: 07/20/2015
f1_keywords:
- /bugreport
helpviewer_keywords:
- /bugreport compiler option [C#]
- -bugreport compiler option [C#]
- bugreport compiler option [C#]
ms.assetid: f39665e3-4f6f-4357-88a2-3274c7bec0c1
ms.openlocfilehash: 0989678be070910c410d71717fe66679e1b70557
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/14/2020
ms.locfileid: "69603082"
---
# <a name="-bugreport-c-compiler-options"></a><span data-ttu-id="d3436-102">-bugreport（C# 编译器选项）</span><span class="sxs-lookup"><span data-stu-id="d3436-102">-bugreport (C# Compiler Options)</span></span>
<span data-ttu-id="d3436-103">指定应使调试信息置于文件中供以后分析。</span><span class="sxs-lookup"><span data-stu-id="d3436-103">Specifies that debug information should be placed in a file for later analysis.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d3436-104">语法</span><span class="sxs-lookup"><span data-stu-id="d3436-104">Syntax</span></span>  
  
```console  
-bugreport:file  
```  
  
## <a name="arguments"></a><span data-ttu-id="d3436-105">参数</span><span class="sxs-lookup"><span data-stu-id="d3436-105">Arguments</span></span>  
 `file`  
 <span data-ttu-id="d3436-106">要包含 Bug 报告的文件的名称。</span><span class="sxs-lookup"><span data-stu-id="d3436-106">The name of the file that you want to contain your bug report.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d3436-107">备注</span><span class="sxs-lookup"><span data-stu-id="d3436-107">Remarks</span></span>  
 <span data-ttu-id="d3436-108">-bugreport 选项指定以下信息应置于 `file` 中：</span><span class="sxs-lookup"><span data-stu-id="d3436-108">The **-bugreport** option specifies that the following information should be placed in `file`:</span></span>  
  
- <span data-ttu-id="d3436-109">编译中所有源代码文件副本。</span><span class="sxs-lookup"><span data-stu-id="d3436-109">A copy of all source code files in the compilation.</span></span>  
  
- <span data-ttu-id="d3436-110">编译中使用的编译器选项列表。</span><span class="sxs-lookup"><span data-stu-id="d3436-110">A listing of the compiler options used in the compilation.</span></span>  
  
- <span data-ttu-id="d3436-111">有关编译器、运行时和操作系统的版本信息。</span><span class="sxs-lookup"><span data-stu-id="d3436-111">Version information about your compiler, run time, and operating system.</span></span>  
  
- <span data-ttu-id="d3436-112">引用的程序集和模块（保存为十六进制数字），.NET Framework 和 SDK 随附的程序集除外。</span><span class="sxs-lookup"><span data-stu-id="d3436-112">Referenced assemblies and modules, saved as hexadecimal digits, except assemblies that ship with the .NET Framework and SDK.</span></span>  
  
- <span data-ttu-id="d3436-113">编译器输出（如有）。</span><span class="sxs-lookup"><span data-stu-id="d3436-113">Compiler output, if any.</span></span>  
  
- <span data-ttu-id="d3436-114">问题说明（系统会提示你提供此信息）。</span><span class="sxs-lookup"><span data-stu-id="d3436-114">A description of the problem, which you will be prompted for.</span></span>  
  
- <span data-ttu-id="d3436-115">有关你认为应如何修复问题的说明（系统会提示你提供此信息）。</span><span class="sxs-lookup"><span data-stu-id="d3436-115">A description of how you think the problem should be fixed, which you will be prompted for.</span></span>  
  
 <span data-ttu-id="d3436-116">如果此选项与 -errorreport: prompt 或 -errorreport:send 一起使用，文件中的信息将发送到 Microsoft Corporation   。</span><span class="sxs-lookup"><span data-stu-id="d3436-116">If this option is used with **-errorreport:prompt** or **-errorreport:send**, the information in the file will be sent to Microsoft Corporation.</span></span>  
  
 <span data-ttu-id="d3436-117">所有源代码文件的副本将放入 `file`，因此你可能希望在尽可能短小的程序中重现可疑代码缺陷。</span><span class="sxs-lookup"><span data-stu-id="d3436-117">Because a copy of all source code files will be placed in `file`, you might want to reproduce the suspected code defect in the shortest possible program.</span></span>  
  
 <span data-ttu-id="d3436-118">此编译器选项在 Visual Studio 中不可用，并且无法以编程方式更改。</span><span class="sxs-lookup"><span data-stu-id="d3436-118">This compiler option is unavailable in Visual Studio and cannot be changed programmatically.</span></span>  
  
 <span data-ttu-id="d3436-119">请注意，生成文件的内容会公开源代码，这可能会导致意外信息泄露。</span><span class="sxs-lookup"><span data-stu-id="d3436-119">Notice that contents of the generated file expose source code that could result in inadvertent information disclosure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d3436-120">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d3436-120">See also</span></span>

- [<span data-ttu-id="d3436-121">C# 编译器选项</span><span class="sxs-lookup"><span data-stu-id="d3436-121">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="d3436-122">-errorreport（C# 编译器选项）</span><span class="sxs-lookup"><span data-stu-id="d3436-122">-errorreport (C# Compiler Options)</span></span>](./errorreport-compiler-option.md)
- [<span data-ttu-id="d3436-123">管理项目和解决方案属性</span><span class="sxs-lookup"><span data-stu-id="d3436-123">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
