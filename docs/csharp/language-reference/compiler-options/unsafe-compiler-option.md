---
title: -unsafe（C# 编译器选项）
ms.date: 04/25/2018
f1_keywords:
- /unsafe
helpviewer_keywords:
- -unsafe compiler option [C#]
- unsafe compiler option [C#]
- /unsafe compiler option [C#]
ms.openlocfilehash: 146299fda103567b111c66400c17edf36addd843
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/14/2020
ms.locfileid: "65877993"
---
# <a name="-unsafe-c-compiler-options"></a><span data-ttu-id="a32e0-102">-unsafe（C# 编译器选项）</span><span class="sxs-lookup"><span data-stu-id="a32e0-102">-unsafe (C# Compiler Options)</span></span>

<span data-ttu-id="a32e0-103">-unsafe 编译器选项允许使用[不安全](../keywords/unsafe.md)关键字进行编译的代码。</span><span class="sxs-lookup"><span data-stu-id="a32e0-103">The **-unsafe** compiler option allows code that uses the [unsafe](../keywords/unsafe.md) keyword to compile.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a32e0-104">语法</span><span class="sxs-lookup"><span data-stu-id="a32e0-104">Syntax</span></span>  
  
```console  
-unsafe  
```  
  
## <a name="remarks"></a><span data-ttu-id="a32e0-105">备注</span><span class="sxs-lookup"><span data-stu-id="a32e0-105">Remarks</span></span>

<span data-ttu-id="a32e0-106">有关不安全代码的详细信息，请参阅[不安全代码和指针](../../programming-guide/unsafe-code-pointers/index.md)。</span><span class="sxs-lookup"><span data-stu-id="a32e0-106">For more information about unsafe code, see [Unsafe Code and Pointers](../../programming-guide/unsafe-code-pointers/index.md).</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="a32e0-107">在 Visual Studio 开发环境中设置此编译器选项</span><span class="sxs-lookup"><span data-stu-id="a32e0-107">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="a32e0-108">打开项目的“属性”  页。</span><span class="sxs-lookup"><span data-stu-id="a32e0-108">Open the project's **Properties** page.</span></span>  
  
2. <span data-ttu-id="a32e0-109">单击“生成”  属性页。</span><span class="sxs-lookup"><span data-stu-id="a32e0-109">Click the **Build** property page.</span></span>  
  
3. <span data-ttu-id="a32e0-110">选中“允许不安全代码”复选框  。</span><span class="sxs-lookup"><span data-stu-id="a32e0-110">Select the **Allow Unsafe Code** check box.</span></span>  
  
### <a name="to-add-this-option-in-a-csproj-file"></a><span data-ttu-id="a32e0-111">向 csproj 文件添加此选项</span><span class="sxs-lookup"><span data-stu-id="a32e0-111">To add this option in a csproj file</span></span>

<span data-ttu-id="a32e0-112">打开项目的 csproj 文件，并添加以下元素：</span><span class="sxs-lookup"><span data-stu-id="a32e0-112">Open the .csproj file for a project, and add the following elements:</span></span>

```xml
  <PropertyGroup>
    <AllowUnsafeBlocks>true</AllowUnsafeBlocks>
  </PropertyGroup>
```

 <span data-ttu-id="a32e0-113">有关如何以编程方式设置此编译器选项的信息，请参阅 <xref:VSLangProj80.CSharpProjectConfigurationProperties3.AllowUnsafeBlocks%2A>。</span><span class="sxs-lookup"><span data-stu-id="a32e0-113">For information about how to set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.AllowUnsafeBlocks%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a32e0-114">示例</span><span class="sxs-lookup"><span data-stu-id="a32e0-114">Example</span></span>

<span data-ttu-id="a32e0-115">针对不安全模式编译 `in.cs`：</span><span class="sxs-lookup"><span data-stu-id="a32e0-115">Compile `in.cs` for unsafe mode:</span></span>  
  
```console  
csc -unsafe in.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="a32e0-116">请参阅</span><span class="sxs-lookup"><span data-stu-id="a32e0-116">See also</span></span>

- [<span data-ttu-id="a32e0-117">C# 编译器选项</span><span class="sxs-lookup"><span data-stu-id="a32e0-117">C# Compiler Options</span></span>](index.md)
- [<span data-ttu-id="a32e0-118">管理项目和解决方案属性</span><span class="sxs-lookup"><span data-stu-id="a32e0-118">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
