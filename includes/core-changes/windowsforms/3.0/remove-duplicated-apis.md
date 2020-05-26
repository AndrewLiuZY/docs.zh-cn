---
ms.openlocfilehash: 3dfacadb5127319d4ce27f367803637cfb1ed00f
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/20/2020
ms.locfileid: "83721550"
---
### <a name="duplicated-apis-removed-from-windows-forms"></a>从 Windows 窗体中删除了重复的 API

从 .NET Core 3.0 预览版 4 开始，在 <xref:System.Windows.Forms?displayProperty=fullName> 命名空间中意外复制的许多 API 已从 .NET Core 3.0 RC1 中删除。

#### <a name="change-description"></a>更改描述

.NET Core 3.0 预览版 4 在无意中复制了 <xref:System.ComponentModel.Design?displayProperty=fullName> 命名空间中已经存在的 <xref:System.Windows.Forms?displayProperty=fullName> 命名空间中的许多类型。 从 .NET Core 3.0 RC1 开始，这些重复的类型不再可用。 下表列出了原始类型及其重复类型：

> [!div class="mx-tdCol2BreakAll"]
> |原始类型|重复类型|
> |---|---|
> |<xref:System.ComponentModel.Design.DesignerActionListsChangedEventArgs?displayProperty=fullName>|`System.Windows.Forms.DesignerActionListsChangedEventArgs`|
> |<xref:System.ComponentModel.Design.DesignerActionListsChangedEventHandler?displayProperty=fullName>|`System.Windows.Forms.DesignerActionListsChangedEventHandler`|
> |<xref:System.ComponentModel.Design.DesignerActionListsChangedType?displayProperty=fullName>|`System.Windows.Forms.DesignerActionListsChangedType`|
> |<xref:System.ComponentModel.Design.DesignerActionUIService?displayProperty=fullName>|`System.Windows.Forms.DesignerActionUIService`|
> |<xref:System.ComponentModel.Design.DesignerCommandSet?displayProperty=fullName>|`System.Windows.Forms.DesignerCommandSet`|

#### <a name="version-introduced"></a>引入的版本

3.0 RC1

#### <a name="recommended-action"></a>建议操作

更新代码以引用原始类型，如表的“原始类型”列中所示  。

#### <a name="category"></a>类别

Windows 窗体

#### <a name="affected-apis"></a>受影响的 API

- 无。

<!--

#### Affected APIs

- Not detectable via API analysis.

-->
