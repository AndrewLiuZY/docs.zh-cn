---
ms.openlocfilehash: 6fafb689af5d50b31b19f5d1fe7090a6c256ca45
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/15/2020
ms.locfileid: "67802464"
---
### <a name="wpf-printing-stack-update"></a><span data-ttu-id="9af88-101">WPF 打印堆栈更新</span><span class="sxs-lookup"><span data-stu-id="9af88-101">WPF Printing Stack Update</span></span>

|   |   |
|---|---|
|<span data-ttu-id="9af88-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="9af88-102">Details</span></span>|<span data-ttu-id="9af88-103">WPF 打印 API 现在使用 <xref:System.Printing.PrintQueue?displayProperty=name> 调用窗口的打印文档包 API，以支持现已弃用的 XPS 打印 API。</span><span class="sxs-lookup"><span data-stu-id="9af88-103">WPF's Printing APIs using <xref:System.Printing.PrintQueue?displayProperty=name> now call Window's Print Document Package API in favor of the now deprecated XPS Print API.</span></span> <span data-ttu-id="9af88-104">这一更改是基于可维护性考虑的，因此用户和开发者应该都不会看到任何行为或 API 使用变化。</span><span class="sxs-lookup"><span data-stu-id="9af88-104">The change was made with serviceability in mind; neither users nor developers should see any changes in behavior or API usage.</span></span> <span data-ttu-id="9af88-105">当在 Windows 10 创意者更新中运行时，此新打印堆栈默认情况下处于启用状态。</span><span class="sxs-lookup"><span data-stu-id="9af88-105">The new printing stack is enabled by default when running in Windows 10 Creators Update.</span></span> <span data-ttu-id="9af88-106">在旧版 Windows 中，旧打印堆栈将继续像过去一样运行。</span><span class="sxs-lookup"><span data-stu-id="9af88-106">The old printing stack will still continue to work just as before in older Windows versions.</span></span>|
|<span data-ttu-id="9af88-107">建议</span><span class="sxs-lookup"><span data-stu-id="9af88-107">Suggestion</span></span>|<span data-ttu-id="9af88-108">若要在 Windows 10 创意者更新中使用旧堆栈，请将 <code>HKEY_CURRENT_USER\Software\Microsoft\.NETFramework\Windows Presentation Foundation\Printing</code> 注册表项的 <code>UseXpsOMPrinting</code> REG_DWORD 值设置为 <code>1</code>。</span><span class="sxs-lookup"><span data-stu-id="9af88-108">To use the old stack in Windows 10 Creators Update, set the <code>UseXpsOMPrinting</code> REG_DWORD value of the <code>HKEY_CURRENT_USER\Software\Microsoft\.NETFramework\Windows Presentation Foundation\Printing</code> registry key to <code>1</code>.</span></span>|
|<span data-ttu-id="9af88-109">范围</span><span class="sxs-lookup"><span data-stu-id="9af88-109">Scope</span></span>|<span data-ttu-id="9af88-110">边缘</span><span class="sxs-lookup"><span data-stu-id="9af88-110">Edge</span></span>|
|<span data-ttu-id="9af88-111">Version</span><span class="sxs-lookup"><span data-stu-id="9af88-111">Version</span></span>|<span data-ttu-id="9af88-112">4.7</span><span class="sxs-lookup"><span data-stu-id="9af88-112">4.7</span></span>|
|<span data-ttu-id="9af88-113">类型</span><span class="sxs-lookup"><span data-stu-id="9af88-113">Type</span></span>|<span data-ttu-id="9af88-114">运行时</span><span class="sxs-lookup"><span data-stu-id="9af88-114">Runtime</span></span>|
