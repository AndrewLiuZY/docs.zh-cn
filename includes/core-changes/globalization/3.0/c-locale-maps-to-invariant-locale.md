---
ms.openlocfilehash: c0551fa086644497c631cd9b6d7058398ff9ccfa
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/20/2020
ms.locfileid: "83702279"
---
### <a name="c-locale-maps-to-the-invariant-locale"></a><span data-ttu-id="03f3a-101">“C”区域设置映射到固定区域设置</span><span class="sxs-lookup"><span data-stu-id="03f3a-101">"C" locale maps to the invariant locale</span></span>

<span data-ttu-id="03f3a-102">.NET Core 2.2 及更早版本依赖于默认 ICU 行为，该行为将“C”区域设置映射到 en_US_POSIX 区域设置。</span><span class="sxs-lookup"><span data-stu-id="03f3a-102">.NET Core 2.2 and earlier versions depend on the default ICU behavior, which maps the "C" locale to the en_US_POSIX locale.</span></span> <span data-ttu-id="03f3a-103">En_US_POSIX 区域设置的排序行为并不可取，因为它不支持不区分大小写的字符串比较。</span><span class="sxs-lookup"><span data-stu-id="03f3a-103">The en_US_POSIX locale has an undesirable collation behavior, because it doesn't support case-insensitive string comparisons.</span></span> <span data-ttu-id="03f3a-104">用户会遇到意外行为是因为部分 Linux 分发版将“C”区域设置设置为了默认区域设置。</span><span class="sxs-lookup"><span data-stu-id="03f3a-104">Because some Linux distributions set the "C" locale as the default locale, users were experiencing unexpected behavior.</span></span>

#### <a name="change-description"></a><span data-ttu-id="03f3a-105">更改描述</span><span class="sxs-lookup"><span data-stu-id="03f3a-105">Change description</span></span>

<span data-ttu-id="03f3a-106">从 .NET Core 3.0 开始，“C”区域设置映射已更改为使用固定区域设置，而不是 en_US_POSIX。</span><span class="sxs-lookup"><span data-stu-id="03f3a-106">Starting with .NET Core 3.0, the "C" locale mapping has changed to use the Invariant locale instead of en_US_POSIX.</span></span> <span data-ttu-id="03f3a-107">“C”区域设置到固定的映射还应用于 Windows，以实现一致性。</span><span class="sxs-lookup"><span data-stu-id="03f3a-107">The "C" locale to Invariant mapping is also applied to Windows for consistency.</span></span>

<span data-ttu-id="03f3a-108">将“C”映射到 en_US_POSIX 区域性会导致客户混乱，因为 en_US_POSIX 不支持不区分大小写的字符串排序/搜索操作。</span><span class="sxs-lookup"><span data-stu-id="03f3a-108">Mapping "C" to en_US_POSIX culture caused customer confusion, because en_US_POSIX doesn't support case insensitive sorting/searching string operations.</span></span> <span data-ttu-id="03f3a-109">由于“C”区域设置用作部分 Linux 分发版中的默认区域设置，因此客户在这些操作系统上会遭遇此类不良行为。</span><span class="sxs-lookup"><span data-stu-id="03f3a-109">Because the "C" locale is used as a default locale in some of the Linux distros, customers experienced this undesired behavior on these operating systems.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="03f3a-110">引入的版本</span><span class="sxs-lookup"><span data-stu-id="03f3a-110">Version introduced</span></span>

<span data-ttu-id="03f3a-111">3.0</span><span class="sxs-lookup"><span data-stu-id="03f3a-111">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="03f3a-112">建议操作</span><span class="sxs-lookup"><span data-stu-id="03f3a-112">Recommended action</span></span>

<span data-ttu-id="03f3a-113">除了解此变更外，没有什么特别之处需要注意。</span><span class="sxs-lookup"><span data-stu-id="03f3a-113">Nothing specific more than the awareness of this change.</span></span> <span data-ttu-id="03f3a-114">此变更仅影响使用“C”本地映射的应用程序。</span><span class="sxs-lookup"><span data-stu-id="03f3a-114">This change affects only applications that use the "C" locale mapping.</span></span>

#### <a name="category"></a><span data-ttu-id="03f3a-115">类别</span><span class="sxs-lookup"><span data-stu-id="03f3a-115">Category</span></span>

<span data-ttu-id="03f3a-116">全球化</span><span class="sxs-lookup"><span data-stu-id="03f3a-116">Globalization</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="03f3a-117">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="03f3a-117">Affected APIs</span></span>

<span data-ttu-id="03f3a-118">所有排序规则和区域性 API 都会受到此变更的影响。</span><span class="sxs-lookup"><span data-stu-id="03f3a-118">All collation and culture APIs are affected by this change.</span></span>

<!--

#### Affected APIs

-->
