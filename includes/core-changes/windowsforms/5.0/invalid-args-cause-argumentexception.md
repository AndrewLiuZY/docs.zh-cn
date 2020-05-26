---
ms.openlocfilehash: f1fc70075ef09a4f036c69788342c07ee51d72ce
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/20/2020
ms.locfileid: "83702471"
---
### <a name="winforms-methods-now-throw-argumentexception"></a>WinForms 方法现在会引发 ArgumentException

某些 Windows 窗体方法现在将针对无效参数引发 <xref:System.ArgumentException>，之前不会这样。

#### <a name="change-description"></a>更改描述

以前，如果将异常类型或错误类型的参数传递给某些 Windows 窗体方法，会导致不确定的状态。 从 .NET 5.0 开始，在传递无效参数后，这些方法现在会引发 <xref:System.ArgumentException>。

引发 <xref:System.ArgumentException> 符合 .NET 运行时的行为。 它还通过清楚地指示具体的无效参数来改进调试体验。

下表列出了受影响的方法和参数：

| 方法 | 参数名称 | 条件 | 新增的版本 |
|-|-|-|
| <xref:System.Windows.Forms.TabControl.GetToolTipText(System.Object)?displayProperty=fullName> | `item` | 参数不属于 <xref:System.Windows.Forms.TabPage> 类型。 | 5.0 预览版 1 |

#### <a name="version-introduced"></a>引入的版本

.NET 5.0 预览版 1

#### <a name="recommended-action"></a>建议操作

- 更新代码以防止传递无效参数。
- 如有必要，请在调用方法时处理 <xref:System.ArgumentException>。

#### <a name="category"></a>类别

Windows 窗体

#### <a name="affected-apis"></a>受影响的 API

- <xref:System.Windows.Forms.TabControl.GetToolTipText(System.Object)?displayProperty=fullName>

<!-- 

#### Affected APIs

- `M:System.Windows.Forms.TabControl.GetToolTipText(System.Object)`

-->
