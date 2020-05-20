---
title: IXCLRDataMethodInstance 接口
ms.date: 02/01/2019
api.name:
- IXCLRDataMethodInstance Interface
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataMethodInstance Interface
helpviewer.keywords:
- IXCLRDataMethodInstance Interface [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 0b1c982b25af9edea76a038b4314b4bd608f07df
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/15/2020
ms.locfileid: "83420885"
---
# <a name="ixclrdatamethodinstance-interface"></a><span data-ttu-id="6077c-102">IXCLRDataMethodInstance 接口</span><span class="sxs-lookup"><span data-stu-id="6077c-102">IXCLRDataMethodInstance Interface</span></span>

<span data-ttu-id="6077c-103">提供用于查询有关方法实例的信息的方法。</span><span class="sxs-lookup"><span data-stu-id="6077c-103">Provides methods for querying information about a method instance.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="methods"></a><span data-ttu-id="6077c-104">方法</span><span class="sxs-lookup"><span data-stu-id="6077c-104">Methods</span></span>

| <span data-ttu-id="6077c-105">方法</span><span class="sxs-lookup"><span data-stu-id="6077c-105">Method</span></span>                                                                                                                  | <span data-ttu-id="6077c-106">说明</span><span class="sxs-lookup"><span data-stu-id="6077c-106">Description</span></span>                                 |
| ----------------------------------------------------------------------------------------------------------------------- | ------------------------------------------- |
| [<span data-ttu-id="6077c-107">GetILAddressMap</span><span class="sxs-lookup"><span data-stu-id="6077c-107">GetILAddressMap</span></span>](ixclrdatamethodinstance-getiladdressmap-method.md) | <span data-ttu-id="6077c-108">获取用于寻址映射信息的 IL。</span><span class="sxs-lookup"><span data-stu-id="6077c-108">Gets the IL to address mapping information.</span></span> |
| [<span data-ttu-id="6077c-109">GetRepresentativeEntryAddress</span><span class="sxs-lookup"><span data-stu-id="6077c-109">GetRepresentativeEntryAddress</span></span>](ixclrdatamethodinstance-getrepresentativeentryaddress-method.md) | <span data-ttu-id="6077c-110">获取方法的所有可能入口点的本机编译的最具代表性的入口点地址。</span><span class="sxs-lookup"><span data-stu-id="6077c-110">Gets the most representative entry point address for the native compilation of all the possible entry points for a method.</span></span> |

## <a name="remarks"></a><span data-ttu-id="6077c-111">备注</span><span class="sxs-lookup"><span data-stu-id="6077c-111">Remarks</span></span>

<span data-ttu-id="6077c-112">此接口在运行时中存在，不会通过任何标头或库文件公开。</span><span class="sxs-lookup"><span data-stu-id="6077c-112">This interface lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="6077c-113">但是，它是从使用 GUID 派生的 COM 接口， `IUnknown` `ECD73800-22CA-4b0d-AB55-E9BA7E6318A5` 该接口可通过常用的 COM 机制获得。</span><span class="sxs-lookup"><span data-stu-id="6077c-113">However, it's a COM interface that derives from `IUnknown` with GUID `ECD73800-22CA-4b0d-AB55-E9BA7E6318A5` that can be obtained through the usual COM mechanisms.</span></span>

## <a name="requirements"></a><span data-ttu-id="6077c-114">要求</span><span class="sxs-lookup"><span data-stu-id="6077c-114">Requirements</span></span>

<span data-ttu-id="6077c-115">**平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="6077c-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
<span data-ttu-id="6077c-116">**标头：** 内容</span><span class="sxs-lookup"><span data-stu-id="6077c-116">**Header:** None</span></span>  
<span data-ttu-id="6077c-117">**库：** 内容</span><span class="sxs-lookup"><span data-stu-id="6077c-117">**Library:** None</span></span>  
<span data-ttu-id="6077c-118">**.NET Framework 版本：**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="6077c-118">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="6077c-119">另请参阅</span><span class="sxs-lookup"><span data-stu-id="6077c-119">See also</span></span>

- [<span data-ttu-id="6077c-120">调试</span><span class="sxs-lookup"><span data-stu-id="6077c-120">Debugging</span></span>](index.md)
- [<span data-ttu-id="6077c-121">调试接口</span><span class="sxs-lookup"><span data-stu-id="6077c-121">Debugging Interfaces</span></span>](debugging-interfaces.md)
