---
title: IXCLRDataProcess：： GetAppDomainByUniqueId 方法
ms.date: 01/16/2019
api.name:
- IXCLRDataProcess::GetAppDomainByUniqueId Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataProcess::GetAppDomainByUniqueId Method
helpviewer.keywords:
- IXCLRDataProcess::GetAppDomainByUniqueId Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: bb02ffed09cbcc31e653bfd3165050c247908c5d
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/15/2020
ms.locfileid: "83420774"
---
# <a name="ixclrdataprocessgetappdomainbyuniqueid-method"></a><span data-ttu-id="8860d-102">IXCLRDataProcess：： GetAppDomainByUniqueId 方法</span><span class="sxs-lookup"><span data-stu-id="8860d-102">IXCLRDataProcess::GetAppDomainByUniqueId Method</span></span>

<span data-ttu-id="8860d-103">`AppDomain`基于其唯一标识符，在进程中获取。</span><span class="sxs-lookup"><span data-stu-id="8860d-103">Gets an `AppDomain` in a process based on its unique identifier.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="8860d-104">语法</span><span class="sxs-lookup"><span data-stu-id="8860d-104">Syntax</span></span>

```cpp
HRESULT GetAppDomainByUniqueID(
    [in] ULONG64               id,
    [out] IXCLRDataAppDomain **appDomain
);
```

## <a name="parameters"></a><span data-ttu-id="8860d-105">参数</span><span class="sxs-lookup"><span data-stu-id="8860d-105">Parameters</span></span>

`id`\
<span data-ttu-id="8860d-106">中AppDomain 的唯一标识符</span><span class="sxs-lookup"><span data-stu-id="8860d-106">[in] The unique identifier of the AppDomain</span></span>

`appDomain`\
<span data-ttu-id="8860d-107">弄AppDomain</span><span class="sxs-lookup"><span data-stu-id="8860d-107">[out] The AppDomain</span></span>

## <a name="remarks"></a><span data-ttu-id="8860d-108">备注</span><span class="sxs-lookup"><span data-stu-id="8860d-108">Remarks</span></span>

<span data-ttu-id="8860d-109">提供的方法是接口的一部分 `IXCLRDataProcess` ，并且对应于虚拟方法表的第20个槽。</span><span class="sxs-lookup"><span data-stu-id="8860d-109">The provided method is part of the `IXCLRDataProcess` interface and corresponds to the 20th slot of the virtual method table.</span></span> <span data-ttu-id="8860d-110">`IXCLRDataAppDomain*`返回的用于与其他 api 交互。</span><span class="sxs-lookup"><span data-stu-id="8860d-110">The `IXCLRDataAppDomain*` returned is used for interaction with other APIs.</span></span>

## <a name="requirements"></a><span data-ttu-id="8860d-111">要求</span><span class="sxs-lookup"><span data-stu-id="8860d-111">Requirements</span></span>

<span data-ttu-id="8860d-112">**平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="8860d-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>
<span data-ttu-id="8860d-113">**标头：** 无**库：** 无 **.NET Framework 版本：**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="8860d-113">**Header:** None **Library:** None **.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="8860d-114">另请参阅</span><span class="sxs-lookup"><span data-stu-id="8860d-114">See also</span></span>

- [<span data-ttu-id="8860d-115">调试</span><span class="sxs-lookup"><span data-stu-id="8860d-115">Debugging</span></span>](index.md)
- [<span data-ttu-id="8860d-116">IXCLRDataProcess 接口</span><span class="sxs-lookup"><span data-stu-id="8860d-116">IXCLRDataProcess Interface</span></span>](ixclrdataprocess-interface.md)
