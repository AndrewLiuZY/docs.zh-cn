---
ms.openlocfilehash: dd850e83540ffed4dc95b00f807f49b0dd3725e9
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/20/2020
ms.locfileid: "83720896"
---
### <a name="domainupdownuselegacyscrolling-compatibility-switch-not-supported"></a><span data-ttu-id="22758-101">不支持 DomainUpDown.UseLegacyScrolling 兼容性开关</span><span class="sxs-lookup"><span data-stu-id="22758-101">DomainUpDown.UseLegacyScrolling compatibility switch not supported</span></span>

<span data-ttu-id="22758-102">已在 .NET Framework 4.7.1 中引入 `Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling` 兼容性开关，但它在 .NET Core 3.0 上的 Windows 窗体中尚不受支持。</span><span class="sxs-lookup"><span data-stu-id="22758-102">The `Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling` compatibility switch, which was introduced in .NET Framework 4.7.1, is not supported in Windows Forms on .NET Core 3.0.</span></span>

#### <a name="change-description"></a><span data-ttu-id="22758-103">更改描述</span><span class="sxs-lookup"><span data-stu-id="22758-103">Change description</span></span>

<span data-ttu-id="22758-104">自 .NET Framework 4.7.1 起，开发人员可使用 `Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling` 兼容性开关选择不执行独立 <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType> 和 <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> 操作。</span><span class="sxs-lookup"><span data-stu-id="22758-104">Starting with the .NET Framework 4.7.1, the `Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling` compatibility switch allowed developers to opt-out of independent <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType> and <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> actions.</span></span> <span data-ttu-id="22758-105">该开关会还原旧行为，也就是说如果存在上下文文本，则忽略 <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType>而且开发人员需要先在控件上执行 <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType> 操作，然后才能执行 <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> 操作。</span><span class="sxs-lookup"><span data-stu-id="22758-105">The switch restored the legacy behavior, in which the <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> is ignored if context text is present, and the developer is required to use <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType> action on the control before the <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> action.</span></span> <span data-ttu-id="22758-106">有关详细信息，请参阅 [\<AppContextSwitchOverrides> 元素](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md)。</span><span class="sxs-lookup"><span data-stu-id="22758-106">For more information, see [\<AppContextSwitchOverrides> element](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md).</span></span>

<span data-ttu-id="22758-107">.NET Core 中尚不支持 `Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling` 开关。</span><span class="sxs-lookup"><span data-stu-id="22758-107">In .NET Core, the `Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling` switch is not supported.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="22758-108">引入的版本</span><span class="sxs-lookup"><span data-stu-id="22758-108">Version introduced</span></span>

<span data-ttu-id="22758-109">3.0 预览版 9</span><span class="sxs-lookup"><span data-stu-id="22758-109">3.0 Preview 9</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="22758-110">建议操作</span><span class="sxs-lookup"><span data-stu-id="22758-110">Recommended action</span></span>

<span data-ttu-id="22758-111">删除此开关。</span><span class="sxs-lookup"><span data-stu-id="22758-111">Remove the switch.</span></span> <span data-ttu-id="22758-112">此开关不受支持，且未提供替代功能。</span><span class="sxs-lookup"><span data-stu-id="22758-112">The switch is not supported, and no alternative functionality is available.</span></span>

#### <a name="category"></a><span data-ttu-id="22758-113">类别</span><span class="sxs-lookup"><span data-stu-id="22758-113">Category</span></span>

<span data-ttu-id="22758-114">Windows 窗体</span><span class="sxs-lookup"><span data-stu-id="22758-114">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="22758-115">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="22758-115">Affected APIs</span></span>

- <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType>

<!-- 

#### Affected APIs

- `M:System.Windows.Forms.DomainUpDown.DownButton`
- `M:System.Windows.Forms.DomainUpDown.UpButton`

-->
