---
title: 配置程序集绑定重定向
ms.date: 03/30/2017
helpviewer_keywords:
- side-by-side execution, assembly binding redirection
- assemblies [.NET Framework], binding redirection
ms.assetid: d266cbd8-bf91-41d1-baf0-afbc481a741f
ms.openlocfilehash: 5b24d99aa23358272eecd042c40001413965d7f0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/15/2020
ms.locfileid: "79181682"
---
# <a name="configuring-assembly-binding-redirection"></a><span data-ttu-id="07c44-102">配置程序集绑定重定向</span><span class="sxs-lookup"><span data-stu-id="07c44-102">Configuring Assembly Binding Redirection</span></span>
<span data-ttu-id="07c44-103">默认情况下，应用程序使用一组 .NET Framework 程序集，该程序集随用于编译该应用程序的运行时版本一起提供。</span><span class="sxs-lookup"><span data-stu-id="07c44-103">By default, applications use the set of .NET Framework assemblies that shipped with the runtime version used to compile the application.</span></span> <span data-ttu-id="07c44-104">可以使用应用程序配置文件中 [\<assemblyBinding>](../configure-apps/file-schema/runtime/assemblybinding-element-for-runtime.md) 元素上的 appliesTo 特性，将程序集绑定引用重定向到 .NET Framework 程序集的特定版本。</span><span class="sxs-lookup"><span data-stu-id="07c44-104">You can use the **appliesTo** attribute on the [\<assemblyBinding>](../configure-apps/file-schema/runtime/assemblybinding-element-for-runtime.md) element in an application configuration file to redirect assembly binding references to a specific version of the .NET Framework assemblies.</span></span> <span data-ttu-id="07c44-105">此可选特性用 .NET Framework 版本号来指示它应用于哪个版本。</span><span class="sxs-lookup"><span data-stu-id="07c44-105">This optional attribute uses a .NET Framework version number to indicate which version it applies to.</span></span> <span data-ttu-id="07c44-106">如果没有指定 appliesTo 特性，\<assemblyBinding> 元素将适用于 .NET Framework 的所有版本。</span><span class="sxs-lookup"><span data-stu-id="07c44-106">If no **appliesTo** attribute is specified, the **\<assemblyBinding>** element applies to all versions of the .NET Framework.</span></span>  
  
 <span data-ttu-id="07c44-107">在 .NET Framework 1.1 版中引入了 appliesTo 特性，而在 .NET Framework 1.0 版中则忽略了此特性  。</span><span class="sxs-lookup"><span data-stu-id="07c44-107">The **appliesTo** attribute was introduced in the .NET Framework version 1.1; it is ignored by the .NET Framework version 1.0.</span></span> <span data-ttu-id="07c44-108">这意味着，即使指定了 appliesTo 特性，在使用 .NET Framework 1.0 版时所有的 \<assemblyBinding> 元素也都适用。</span><span class="sxs-lookup"><span data-stu-id="07c44-108">This means that all **\<assemblyBinding>** elements are applied when using the .NET Framework version 1.0, even if an **appliesTo** attribute is specified.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="07c44-109">使用 appliesTo 特性来限制运行时特定版本的程序集绑定重定向  。</span><span class="sxs-lookup"><span data-stu-id="07c44-109">Use the **appliesTo** attribute to limit assembly binding redirection to a specific version of the runtime.</span></span>  
  
 <span data-ttu-id="07c44-110">例如，若要重定向 .NET Framework 1.0 版程序集的程序集绑定，应在你的应用程序配置文件中包括以下 XML 代码。</span><span class="sxs-lookup"><span data-stu-id="07c44-110">For example, to redirect assembly binding for a .NET Framework version 1.0 assembly, you would include the following XML code in your application configuration file.</span></span>  
  
```xml  
<runtime>  
        <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1" appliesTo="v1.0.3705">  
            <dependentAssembly>
               * assembly information goes here *  
            </dependentAssembly>  
       </assemblyBinding>  
</runtime>  
```  
  
 <span data-ttu-id="07c44-111">\<assemblyBinding> 元素要区分顺序。</span><span class="sxs-lookup"><span data-stu-id="07c44-111">The **\<assemblyBinding>** elements are order-sensitive.</span></span> <span data-ttu-id="07c44-112">应首先输入任何 .NET Framework 1.0 版程序集的程序集绑定重定向信息，再输入任何 .NET Framework 1.1 版程序集的程序集绑定重定向信息。</span><span class="sxs-lookup"><span data-stu-id="07c44-112">You should enter assembly binding redirection information for any .NET Framework version 1.0 assemblies first, followed by assembly binding redirection information for any .NET Framework version 1.1 assemblies.</span></span> <span data-ttu-id="07c44-113">最后，输入任何因不使用 **appliesTo** 特性而适用于所有版本的 .NET Framework 的.NET Framework 程序集重定向的程序集绑定重定向信息。</span><span class="sxs-lookup"><span data-stu-id="07c44-113">Finally, enter assembly binding redirection information for any .NET Framework assembly redirection that does not use the **appliesTo** attribute and therefore applies to all versions of the .NET Framework.</span></span> <span data-ttu-id="07c44-114">如果发生重定向冲突，请使用配置文件中的第一个匹配的重定向语句。</span><span class="sxs-lookup"><span data-stu-id="07c44-114">In case of a conflict in redirection, the first matching redirection statement in the configuration file is used.</span></span>  
  
 <span data-ttu-id="07c44-115">例如，若要将一个引用重定向到 .NET Framework 1.0 版程序集，而将另一个引用重定向到 .NET Framework 1.1 版程序集，将使用以下伪代码中所示的模式。</span><span class="sxs-lookup"><span data-stu-id="07c44-115">For example, to redirect one reference to a .NET Framework version 1.0 assembly and another reference to a .NET Framework version 1.1 assembly, you would use the pattern shown in the following pseudocode.</span></span>  
  
```xml  
<assemblyBinding xmlns="..." appliesTo="v1.0.3705">
  <!-- .NET Framework version 1.0 redirects here. -->
</assemblyBinding>
  
<assemblyBinding xmlns="..." appliesTo="v1.1.4322">
  <!-- .NET Framework version 1.1 redirects here. -->
</assemblyBinding>
  
<assemblyBinding xmlns="...">
  <!-- Redirects meant for all versions of the .NET Framework. -->
</assemblyBinding>  
```  
  
## <a name="debugging-configuration-file-errors"></a><span data-ttu-id="07c44-116">调试配置文件错误</span><span class="sxs-lookup"><span data-stu-id="07c44-116">Debugging Configuration File Errors</span></span>  
 <span data-ttu-id="07c44-117">一旦创建了应用程序域，运行时就会分析配置文件并将代码加载到该应用程序域中。</span><span class="sxs-lookup"><span data-stu-id="07c44-117">The runtime parses configuration files once when an application domain is created, and loads code into that application domain.</span></span> <span data-ttu-id="07c44-118">公共语言运行时通过忽略条目来处理配置文件中的错误。</span><span class="sxs-lookup"><span data-stu-id="07c44-118">The common language runtime handles errors in a configuration file by ignoring the entry.</span></span> <span data-ttu-id="07c44-119">如果配置文件含有格式不正确的 XML，则运行时将忽略整个配置文件。</span><span class="sxs-lookup"><span data-stu-id="07c44-119">The runtime ignores the entire configuration file if it contains malformed XML.</span></span> <span data-ttu-id="07c44-120">对于无效的 XML，仅忽略无效的部分。</span><span class="sxs-lookup"><span data-stu-id="07c44-120">For invalid XML, only the invalid sections are ignored.</span></span>  
  
 <span data-ttu-id="07c44-121">可以通过确定是否正在发生程序集绑定重定向来确定是否正在使用某个配置文件。</span><span class="sxs-lookup"><span data-stu-id="07c44-121">You can determine whether a configuration file is being used by determining whether assembly binding redirects are occurring.</span></span> <span data-ttu-id="07c44-122">使用[程序集绑定日志查看器 (Fuslogvw.exe)](../tools/fuslogvw-exe-assembly-binding-log-viewer.md) 查看正在加载哪些程序集。</span><span class="sxs-lookup"><span data-stu-id="07c44-122">Use the [Assembly Binding Log Viewer (Fuslogvw.exe)](../tools/fuslogvw-exe-assembly-binding-log-viewer.md) to see which assemblies are being loaded.</span></span> <span data-ttu-id="07c44-123">若要查看所有的程序集绑定，必须在注册表中设置 ForceLog 的条目  。</span><span class="sxs-lookup"><span data-stu-id="07c44-123">To see all assembly binds, you must set an entry for **ForceLog** in the registry.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="07c44-124">另请参阅</span><span class="sxs-lookup"><span data-stu-id="07c44-124">See also</span></span>

- [<span data-ttu-id="07c44-125">如何：启用和禁用自动绑定重定向</span><span class="sxs-lookup"><span data-stu-id="07c44-125">How to: Enable and Disable Automatic Binding Redirection</span></span>](../configure-apps/how-to-enable-and-disable-automatic-binding-redirection.md)
