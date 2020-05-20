---
ms.openlocfilehash: fc315faef750d93d914104dd568078aa3fc430d4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/15/2020
ms.locfileid: "72887732"
---
### <a name="rsacngverifyhash-now-returns-false-for-any-verification-failure"></a>RSACng.VerifyHash 现在为任意验证失败返回 False

|   |   |
|---|---|
|详细信息|自 .NET Framework 4.6.2 起，如果签名本身格式不正确，则此方法返回 False  。 现在为任意验证失败返回 false。在 .NET Framework 4.6 和 4.6.1 中，如果签名格式错误，则此方法引发 <xref:System.Security.Cryptography.CryptographicException?displayProperty=name>。|
|建议|如果验证失败且此方法返回 False，应改为执行依赖处理 <xref:System.Security.Cryptography.CryptographicException?displayProperty=name> 而实现执行的任意代码。|
|范围|次要|
|Version|4.6.2|
|类型|运行时|
|受影响的 API|<ul><li><xref:System.Security.Cryptography.RSACng.VerifyHash(System.Byte[],System.Byte[],System.Security.Cryptography.HashAlgorithmName,System.Security.Cryptography.RSASignaturePadding)?displayProperty=nameWithType></li></ul>|
