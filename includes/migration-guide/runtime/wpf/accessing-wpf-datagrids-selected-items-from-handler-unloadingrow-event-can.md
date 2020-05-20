---
ms.openlocfilehash: cda5df4b673412a7c8c59f80f89c19c13dc81dc1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/15/2020
ms.locfileid: "67858542"
---
### <a name="accessing-a-wpf-datagrids-selected-items-from-a-handler-of-the-datagrids-unloadingrow-event-can-cause-a-nullreferenceexception"></a><span data-ttu-id="e5367-101">从 DataGrid 的 UnloadingRow 事件的处理程序访问 WPF DataGrid 的选定项可能会导致 NullReferenceException</span><span class="sxs-lookup"><span data-stu-id="e5367-101">Accessing a WPF DataGrid's selected items from a handler of the DataGrid's UnloadingRow event can cause a NullReferenceException</span></span>

|   |   |
|---|---|
|<span data-ttu-id="e5367-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="e5367-102">Details</span></span>|<span data-ttu-id="e5367-103">由于 .NET Framework 4.5 中的 bug，涉及删除行的 <xref:System.Windows.Controls.DataGrid> 事件的事件处理程序如果访问 <xref:System.Windows.Controls.DataGrid> 的 <xref:System.Windows.Controls.Primitives.Selector.SelectedItem?displayProperty=name> 或 <xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems?displayProperty=name> 属性，可能会导致引发 <xref:System.NullReferenceException?displayProperty=name>。</span><span class="sxs-lookup"><span data-stu-id="e5367-103">Due to a bug in the .NET Framework 4.5, event handlers for <xref:System.Windows.Controls.DataGrid> events involving the removal of a row can cause a <xref:System.NullReferenceException?displayProperty=name> to be thrown if they access the <xref:System.Windows.Controls.DataGrid>'s <xref:System.Windows.Controls.Primitives.Selector.SelectedItem?displayProperty=name> or <xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems?displayProperty=name> properties.</span></span>|
|<span data-ttu-id="e5367-104">建议</span><span class="sxs-lookup"><span data-stu-id="e5367-104">Suggestion</span></span>|<span data-ttu-id="e5367-105">此问题已在 .NET Framework 4.6 中解决，因此升级到该版本的 .NET Framework 即可解决该问题。</span><span class="sxs-lookup"><span data-stu-id="e5367-105">This issue has been fixed in the .NET Framework 4.6 and may be addressed by upgrading to that version of the .NET Framework.</span></span>|
|<span data-ttu-id="e5367-106">范围</span><span class="sxs-lookup"><span data-stu-id="e5367-106">Scope</span></span>|<span data-ttu-id="e5367-107">次要</span><span class="sxs-lookup"><span data-stu-id="e5367-107">Minor</span></span>|
|<span data-ttu-id="e5367-108">Version</span><span class="sxs-lookup"><span data-stu-id="e5367-108">Version</span></span>|<span data-ttu-id="e5367-109">4.5</span><span class="sxs-lookup"><span data-stu-id="e5367-109">4.5</span></span>|
|<span data-ttu-id="e5367-110">类型</span><span class="sxs-lookup"><span data-stu-id="e5367-110">Type</span></span>|<span data-ttu-id="e5367-111">运行时</span><span class="sxs-lookup"><span data-stu-id="e5367-111">Runtime</span></span>|
|<span data-ttu-id="e5367-112">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="e5367-112">Affected APIs</span></span>|<ul><li><xref:System.Windows.Controls.DataGrid.UnloadingRow?displayProperty=nameWithType></li><li><xref:System.Windows.Controls.DataGrid.UnloadingRowDetails?displayProperty=nameWithType></li></ul>|
