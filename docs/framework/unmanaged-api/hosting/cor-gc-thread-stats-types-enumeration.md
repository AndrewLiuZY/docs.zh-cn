---
title: COR_GC_THREAD_STATS_TYPES 枚举
ms.date: 03/30/2017
api_name:
- COR_GC_THREAD_STATS_TYPES
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- COR_GC_THREAD_STATS_TYPES
helpviewer_keywords:
- COR_GC_THREAD_STATS_TYPES enumeration [.NET Framework hosting]
ms.assetid: aa227704-0ab1-4b08-aee2-1f439762162e
topic_type:
- apiref
ms.openlocfilehash: 2206499cad9be2a29f485ee66d468accbe00b5f5
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616665"
---
# <a name="cor_gc_thread_stats_types-enumeration"></a><span data-ttu-id="ae38e-102">COR_GC_THREAD_STATS_TYPES 枚举</span><span class="sxs-lookup"><span data-stu-id="ae38e-102">COR_GC_THREAD_STATS_TYPES Enumeration</span></span>
<span data-ttu-id="ae38e-103">指示线程的垃圾回收统计信息。</span><span class="sxs-lookup"><span data-stu-id="ae38e-103">Indicates the garbage collection statistics for a thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ae38e-104">语法</span><span class="sxs-lookup"><span data-stu-id="ae38e-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    COR_GC_THREAD_HAS_PROMOTED_BYTES  = 0x00000001  
} COR_GC_THREAD_STATS_TYPES;  
```  
  
## <a name="members"></a><span data-ttu-id="ae38e-105">成员</span><span class="sxs-lookup"><span data-stu-id="ae38e-105">Members</span></span>  
  
|<span data-ttu-id="ae38e-106">成员</span><span class="sxs-lookup"><span data-stu-id="ae38e-106">Member</span></span>|<span data-ttu-id="ae38e-107">描述</span><span class="sxs-lookup"><span data-stu-id="ae38e-107">Description</span></span>|  
|------------|-----------------|  
|`COR_GC_THREAD_HAS_PROMOTED_BYTES`|<span data-ttu-id="ae38e-108">线程具有在最近的垃圾回收中升级的字节数。</span><span class="sxs-lookup"><span data-stu-id="ae38e-108">The thread has bytes that were promoted in the most recent garbage collection.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ae38e-109">要求</span><span class="sxs-lookup"><span data-stu-id="ae38e-109">Requirements</span></span>  
 <span data-ttu-id="ae38e-110">**平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ae38e-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ae38e-111">**标头：** GCHost，GCHost</span><span class="sxs-lookup"><span data-stu-id="ae38e-111">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="ae38e-112">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ae38e-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ae38e-113">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ae38e-113">See also</span></span>

- [<span data-ttu-id="ae38e-114">承载枚举</span><span class="sxs-lookup"><span data-stu-id="ae38e-114">Hosting Enumerations</span></span>](hosting-enumerations.md)
