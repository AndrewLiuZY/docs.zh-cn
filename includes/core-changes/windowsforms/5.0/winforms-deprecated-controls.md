---
ms.openlocfilehash: c9720f51e40ada4cd2cf6997ba7006a232893553
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/20/2020
ms.locfileid: "83702460"
---
### <a name="removed-status-bar-controls"></a><span data-ttu-id="22c8a-101">已删除的状态栏控件</span><span class="sxs-lookup"><span data-stu-id="22c8a-101">Removed status bar controls</span></span>

<span data-ttu-id="22c8a-102">从 .NET 5.0 预览版 1 开始，某些 Windows 窗体控件不再可用。</span><span class="sxs-lookup"><span data-stu-id="22c8a-102">Starting in .NET 5.0 Preview 1, some Windows Forms controls are no longer available.</span></span>

#### <a name="change-description"></a><span data-ttu-id="22c8a-103">更改描述</span><span class="sxs-lookup"><span data-stu-id="22c8a-103">Change description</span></span>

<span data-ttu-id="22c8a-104">从 .NET 5.0 预览版 1 开始，一些与状态栏相关的 Windows 窗体控件不再可用。</span><span class="sxs-lookup"><span data-stu-id="22c8a-104">Starting with .NET 5.0 Preview 1, some of the status bar-related Windows Forms controls are no longer available.</span></span> <span data-ttu-id="22c8a-105">.NET Framework 2.0 中引入改进了设计和支持的替换控件。</span><span class="sxs-lookup"><span data-stu-id="22c8a-105">Replacement controls that have better design and support were introduced in .NET Framework 2.0.</span></span> <span data-ttu-id="22c8a-106">弃用的控件之前已从设计器工具箱中删除，但仍可供使用。</span><span class="sxs-lookup"><span data-stu-id="22c8a-106">The deprecated controls were previously removed from designer toolboxes but were still available to be used.</span></span> <span data-ttu-id="22c8a-107">现在，已完全删除这些控件。</span><span class="sxs-lookup"><span data-stu-id="22c8a-107">Now, they have been completely removed.</span></span>

<span data-ttu-id="22c8a-108">以下类型不再可用：</span><span class="sxs-lookup"><span data-stu-id="22c8a-108">The following types are no longer available:</span></span>

* `StatusBar`
* `StatusBarDrawItemEventArgs`
* `StatusBarDrawItemEventHandler`
* `StatusBarPanel`
* `StatusBarPanelAutoSize`
* `StatusBarPanelBorderStyle`
* `StatusBarPanelClickEventArgs`
* `StatusBarPanelClickEventHandler`
* `StatusBarPanelStyle`

#### <a name="version-introduced"></a><span data-ttu-id="22c8a-109">引入的版本</span><span class="sxs-lookup"><span data-stu-id="22c8a-109">Version introduced</span></span>

<span data-ttu-id="22c8a-110">5.0 预览版 1</span><span class="sxs-lookup"><span data-stu-id="22c8a-110">5.0 Preview 1</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="22c8a-111">建议操作</span><span class="sxs-lookup"><span data-stu-id="22c8a-111">Recommended action</span></span>

<span data-ttu-id="22c8a-112">转到这些控件及其应用场景的替代 API：</span><span class="sxs-lookup"><span data-stu-id="22c8a-112">Move to the replacement APIs for these controls and their scenarios:</span></span>

| <span data-ttu-id="22c8a-113">旧控件 (API)</span><span class="sxs-lookup"><span data-stu-id="22c8a-113">Old Control (API)</span></span> | <span data-ttu-id="22c8a-114">推荐的替换控件</span><span class="sxs-lookup"><span data-stu-id="22c8a-114">Recommended Replacement</span></span>                          |
|-------------------|--------------------------------------------------|
| <span data-ttu-id="22c8a-115">StatusBar</span><span class="sxs-lookup"><span data-stu-id="22c8a-115">StatusBar</span></span>         | <xref:System.Windows.Forms.StatusStrip>          |
| <span data-ttu-id="22c8a-116">StatusBarPanel</span><span class="sxs-lookup"><span data-stu-id="22c8a-116">StatusBarPanel</span></span>    | <xref:System.Windows.Forms.ToolStripStatusLabel> |

#### <a name="category"></a><span data-ttu-id="22c8a-117">类别</span><span class="sxs-lookup"><span data-stu-id="22c8a-117">Category</span></span>

<span data-ttu-id="22c8a-118">Windows 窗体</span><span class="sxs-lookup"><span data-stu-id="22c8a-118">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="22c8a-119">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="22c8a-119">Affected APIs</span></span>

- <xref:System.Windows.Forms.StatusBar?displayProperty=fullName>
- <xref:System.Windows.Forms.StatusBarDrawItemEventArgs?displayProperty=fullName>
- <xref:System.Windows.Forms.StatusBarDrawItemEventHandler?displayProperty=fullName>
- <xref:System.Windows.Forms.StatusBarPanel?displayProperty=fullName>
- <xref:System.Windows.Forms.StatusBarPanelAutoSize?displayProperty=fullName>
- <xref:System.Windows.Forms.StatusBarPanelBorderStyle?displayProperty=fullName>
- <xref:System.Windows.Forms.StatusBarPanelClickEventArgs?displayProperty=fullName>
- <xref:System.Windows.Forms.StatusBarPanelClickEventHandler?displayProperty=fullName>
- <xref:System.Windows.Forms.StatusBarPanelStyle?displayProperty=fullName>

<!-- 

#### Affected APIs

- `T:System.Windows.Forms.StatusBar`
- `T:System.Windows.Forms.StatusBarDrawItemEventArgs`
- `T:System.Windows.Forms.StatusBarDrawItemEventHandler`
- `T:System.Windows.Forms.StatusBarPanel`
- `T:System.Windows.Forms.StatusBarPanelAutoSize`
- `T:System.Windows.Forms.StatusBarPanelBorderStyle`
- `T:System.Windows.Forms.StatusBarPanelClickEventArgs`
- `T:System.Windows.Forms.StatusBarPanelClickEventHandler`
- `T:System.Windows.Forms.StatusBarPanelStyle` 

-->
