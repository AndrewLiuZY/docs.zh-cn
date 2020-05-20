---
title: -keyfile（C# 编译器选项）
ms.date: 07/20/2015
f1_keywords:
- /keyfile
helpviewer_keywords:
- /keyfile compiler option [C#]
- -keyfile compiler option [C#]
- keyfile compiler option [C#]
ms.assetid: 0815f9de-ace4-4e98-b4c6-13c55dea40c2
ms.openlocfilehash: bf271cc6b6887e930911071d4603b51daed55e61
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/14/2020
ms.locfileid: "70970263"
---
# <a name="-keyfile-c-compiler-options"></a><span data-ttu-id="5844d-102">-keyfile（C# 编译器选项）</span><span class="sxs-lookup"><span data-stu-id="5844d-102">-keyfile (C# Compiler Options)</span></span>
<span data-ttu-id="5844d-103">指定包含加密密钥的文件名。</span><span class="sxs-lookup"><span data-stu-id="5844d-103">Specifies the filename containing the cryptographic key.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5844d-104">语法</span><span class="sxs-lookup"><span data-stu-id="5844d-104">Syntax</span></span>  
  
```console  
-keyfile:file  
```  
  
## <a name="arguments"></a><span data-ttu-id="5844d-105">自变量</span><span class="sxs-lookup"><span data-stu-id="5844d-105">Arguments</span></span>  
  
|<span data-ttu-id="5844d-106">术语</span><span class="sxs-lookup"><span data-stu-id="5844d-106">Term</span></span>|<span data-ttu-id="5844d-107">定义</span><span class="sxs-lookup"><span data-stu-id="5844d-107">Definition</span></span>|  
|----------|----------------|  
|`file`|<span data-ttu-id="5844d-108">含有强名称密钥的文件的名称。</span><span class="sxs-lookup"><span data-stu-id="5844d-108">The name of the file containing the strong name key.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5844d-109">备注</span><span class="sxs-lookup"><span data-stu-id="5844d-109">Remarks</span></span>  
 <span data-ttu-id="5844d-110">使用此选项时，编译器在程序集清单中插入指定字段的公钥，然后使用私钥对最终的程序集进行签名。</span><span class="sxs-lookup"><span data-stu-id="5844d-110">When this option is used, the compiler inserts the public key from the specified file into the assembly manifest and then signs the final assembly with the private key.</span></span> <span data-ttu-id="5844d-111">若要生成密钥文件，请在命令行键入 sn-k `file`。</span><span class="sxs-lookup"><span data-stu-id="5844d-111">To generate a key file, type sn -k `file` at the command line.</span></span>  
  
 <span data-ttu-id="5844d-112">如果使用 -target:module 进行编译，密钥文件的名称将保存在模块中，并在使用 [-addmodule](./addmodule-compiler-option.md) 编译程序集时包含到创建的程序集中。</span><span class="sxs-lookup"><span data-stu-id="5844d-112">If you compile with **-target:module**, the name of the key file is held in the module and incorporated into the assembly that is created when you compile an assembly with [-addmodule](./addmodule-compiler-option.md).</span></span>  
  
 <span data-ttu-id="5844d-113">也可以使用 [-keycontainer](./keycontainer-compiler-option.md) 将加密信息传递给编译器。</span><span class="sxs-lookup"><span data-stu-id="5844d-113">You can also pass your encryption information to the compiler with [-keycontainer](./keycontainer-compiler-option.md).</span></span> <span data-ttu-id="5844d-114">如果需要部分签名的程序集，请使用 [-delaysign](./delaysign-compiler-option.md)。</span><span class="sxs-lookup"><span data-stu-id="5844d-114">Use [-delaysign](./delaysign-compiler-option.md) if you want a partially signed assembly.</span></span>  
  
 <span data-ttu-id="5844d-115">如果在同一编译中同时指定 -keyfile 和 -keycontainer（通过命令行选项或通过自定义特性），则 Al.exe 将首先尝试用密钥容器。</span><span class="sxs-lookup"><span data-stu-id="5844d-115">In case both -keyfile and -keycontainer are specified (either by command line option or by custom attribute) in the same compilation, the compiler will first try the key container.</span></span> <span data-ttu-id="5844d-116">如果成功，则使用密钥容器中的信息对程序集签名。</span><span class="sxs-lookup"><span data-stu-id="5844d-116">If that succeeds, then the assembly is signed with the information in the key container.</span></span> <span data-ttu-id="5844d-117">如果编译器没有找到密钥容器，它将尝试用 -keyfile 指定的文件。</span><span class="sxs-lookup"><span data-stu-id="5844d-117">If the compiler does not find the key container, it will try the file specified with -keyfile.</span></span> <span data-ttu-id="5844d-118">如果成功，则使用密钥文件中的信息对程序集签名，并且将密钥信息安装到密钥容器中（类似于 sn -i），以便在下一次编译中，密钥容器选项将生效。</span><span class="sxs-lookup"><span data-stu-id="5844d-118">If that succeeds, the assembly is signed with the information in the key file and the key information will be installed in the key container (similar to sn -i) so that on the next compilation, the key container will be valid.</span></span>  
  
 <span data-ttu-id="5844d-119">请注意，密钥文件可能仅包含公钥。</span><span class="sxs-lookup"><span data-stu-id="5844d-119">Note that a key file might contain only the public key.</span></span>  
  
 <span data-ttu-id="5844d-120">有关详细信息，请参阅[创建和使用具有强名称的程序集](../../../standard/assembly/create-use-strong-named.md)和[延迟为程序集签名](../../../standard/assembly/delay-sign.md)。</span><span class="sxs-lookup"><span data-stu-id="5844d-120">For more information, see [Creating and Using Strong-Named Assemblies](../../../standard/assembly/create-use-strong-named.md) and [Delay Signing an Assembly](../../../standard/assembly/delay-sign.md).</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="5844d-121">在 Visual Studio 开发环境中设置此编译器选项</span><span class="sxs-lookup"><span data-stu-id="5844d-121">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="5844d-122">打开项目的“属性”  页。</span><span class="sxs-lookup"><span data-stu-id="5844d-122">Open the **Properties** page for the project.</span></span>  
  
2. <span data-ttu-id="5844d-123">单击“签名”  属性页。</span><span class="sxs-lookup"><span data-stu-id="5844d-123">Click the **Signing** property page.</span></span>  
  
3. <span data-ttu-id="5844d-124">修改“选择强名称密钥文件”  属性。</span><span class="sxs-lookup"><span data-stu-id="5844d-124">Modify the **Choose a strong name key file** property.</span></span>  
  
 <span data-ttu-id="5844d-125">可通过 <xref:VSLangProj.ProjectProperties.AssemblyOriginatorKeyFile%2A> 以编程方式访问此编译器选项。</span><span class="sxs-lookup"><span data-stu-id="5844d-125">You can programmatically access this compiler option with <xref:VSLangProj.ProjectProperties.AssemblyOriginatorKeyFile%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5844d-126">请参阅</span><span class="sxs-lookup"><span data-stu-id="5844d-126">See also</span></span>

- [<span data-ttu-id="5844d-127">C# 编译器选项</span><span class="sxs-lookup"><span data-stu-id="5844d-127">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="5844d-128">管理项目和解决方案属性</span><span class="sxs-lookup"><span data-stu-id="5844d-128">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
