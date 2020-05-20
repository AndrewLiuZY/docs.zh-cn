---
ms.openlocfilehash: c9c46793a0f66894649796d960547848ff5ebf8c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/15/2020
ms.locfileid: "67858549"
---
### <a name="gridviews-with-allowcustompaging-set-to-true-may-fire-the-pageindexchanging-event-when-leaving-the-final-page-of-the-view"></a>AllowCustomPaging 设为 true 的 GridViews 可能在离开视图最后一页时触发 PageIndexChanging 事件

|   |   |
|---|---|
|详细信息|.NET Framework 4.5 中的 bug 导致 <xref:System.Web.UI.WebControls.GridView.PageIndexChanging?displayProperty=name> 有时在遇到已启用 <xref:System.Web.UI.WebControls.GridView.AllowCustomPaging?displayProperty=name> 的 <xref:System.Web.UI.WebControls.GridView?displayProperty=name> 时不会触发。|
|建议|此问题已在 .NET Framework 4.6 中解决，因此升级到该版本的 .NET Framework 即可解决该问题。 作为解决方法，应用可以对任何满足以下条件的 <code>Page_Load</code> 执行显式 BindGrid（<xref:System.Web.UI.WebControls.GridView?displayProperty=name> 在最后一页且 Last<xref:System.Web.UI.WebControls.GridView.PageSize?displayProperty=name> 不同于 <xref:System.Web.UI.WebControls.GridView.PageSize?displayProperty=name>）。 或者，可以将应用修改为允许分页（不是自定义分页），因为该方案不演示此问题。|
|范围|次要|
|Version|4.5|
|类型|运行时|
|受影响的 API|<ul><li><xref:System.Web.UI.WebControls.GridView.AllowCustomPaging?displayProperty=nameWithType></li></ul>|
