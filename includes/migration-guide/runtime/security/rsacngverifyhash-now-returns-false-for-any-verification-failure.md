---
ms.openlocfilehash: fc315faef750d93d914104dd568078aa3fc430d4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/15/2020
ms.locfileid: "72887732"
---
### <a name="rsacngverifyhash-now-returns-false-for-any-verification-failure"></a><span data-ttu-id="9a252-101">RSACng.VerifyHash 现在为任意验证失败返回 False</span><span class="sxs-lookup"><span data-stu-id="9a252-101">RSACng.VerifyHash now returns False for any verification failure</span></span>

|   |   |
|---|---|
|<span data-ttu-id="9a252-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="9a252-102">Details</span></span>|<span data-ttu-id="9a252-103">自 .NET Framework 4.6.2 起，如果签名本身格式不正确，则此方法返回 False  。</span><span class="sxs-lookup"><span data-stu-id="9a252-103">Starting with the .NET Framework 4.6.2, this method returns **False** if the signature itself is badly formatted.</span></span> <span data-ttu-id="9a252-104">现在为任意验证失败返回 false。在 .NET Framework 4.6 和 4.6.1 中，如果签名格式错误，则此方法引发 <xref:System.Security.Cryptography.CryptographicException?displayProperty=name>。</span><span class="sxs-lookup"><span data-stu-id="9a252-104">It now returns false for any verification failure.In the .NET Framework 4.6 and 4.6.1, the method throws a <xref:System.Security.Cryptography.CryptographicException?displayProperty=name> if the signature itself is badly formatted.</span></span>|
|<span data-ttu-id="9a252-105">建议</span><span class="sxs-lookup"><span data-stu-id="9a252-105">Suggestion</span></span>|<span data-ttu-id="9a252-106">如果验证失败且此方法返回 False，应改为执行依赖处理 <xref:System.Security.Cryptography.CryptographicException?displayProperty=name> 而实现执行的任意代码。</span><span class="sxs-lookup"><span data-stu-id="9a252-106">Any code whose execution depends on handling the <xref:System.Security.Cryptography.CryptographicException?displayProperty=name> should instead execute if validation fails and the method returns **False**.</span></span>|
|<span data-ttu-id="9a252-107">范围</span><span class="sxs-lookup"><span data-stu-id="9a252-107">Scope</span></span>|<span data-ttu-id="9a252-108">次要</span><span class="sxs-lookup"><span data-stu-id="9a252-108">Minor</span></span>|
|<span data-ttu-id="9a252-109">Version</span><span class="sxs-lookup"><span data-stu-id="9a252-109">Version</span></span>|<span data-ttu-id="9a252-110">4.6.2</span><span class="sxs-lookup"><span data-stu-id="9a252-110">4.6.2</span></span>|
|<span data-ttu-id="9a252-111">类型</span><span class="sxs-lookup"><span data-stu-id="9a252-111">Type</span></span>|<span data-ttu-id="9a252-112">运行时</span><span class="sxs-lookup"><span data-stu-id="9a252-112">Runtime</span></span>|
|<span data-ttu-id="9a252-113">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="9a252-113">Affected APIs</span></span>|<ul><li><xref:System.Security.Cryptography.RSACng.VerifyHash(System.Byte[],System.Byte[],System.Security.Cryptography.HashAlgorithmName,System.Security.Cryptography.RSASignaturePadding)?displayProperty=nameWithType></li></ul>|
