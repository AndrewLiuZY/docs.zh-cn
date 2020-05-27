---
title: IGCHost2 接口
ms.date: 03/30/2017
api_name:
- IGCHost2
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IGCHost2
helpviewer_keywords:
- IGCHost2 interface [.NET Framework hosting]
ms.assetid: e5323fa4-18ac-424d-859d-a65a550d08d9
topic_type:
- apiref
ms.openlocfilehash: 976673a0caab4e041cc80e5536544c195fcf692a
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/22/2020
ms.locfileid: "83805183"
---
# <a name="igchost2-interface"></a><span data-ttu-id="0e3a5-102">IGCHost2 接口</span><span class="sxs-lookup"><span data-stu-id="0e3a5-102">IGCHost2 Interface</span></span>
<span data-ttu-id="0e3a5-103">提供一些方法，用于获取有关垃圾回收系统的信息并控制垃圾回收的某些方面。</span><span class="sxs-lookup"><span data-stu-id="0e3a5-103">Provides methods for obtaining information about the garbage collection system and for controlling some aspects of garbage collection.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0e3a5-104">对于新开发，建议改为使用[ICLRGCManager2](iclrgcmanager2-interface.md)接口。</span><span class="sxs-lookup"><span data-stu-id="0e3a5-104">For new development, we recommend that you use the [ICLRGCManager2](iclrgcmanager2-interface.md) interface instead.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="0e3a5-105">方法</span><span class="sxs-lookup"><span data-stu-id="0e3a5-105">Methods</span></span>  
  
|<span data-ttu-id="0e3a5-106">方法</span><span class="sxs-lookup"><span data-stu-id="0e3a5-106">Method</span></span>|<span data-ttu-id="0e3a5-107">说明</span><span class="sxs-lookup"><span data-stu-id="0e3a5-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="0e3a5-108">SetGCStartupLimitsEx 方法</span><span class="sxs-lookup"><span data-stu-id="0e3a5-108">SetGCStartupLimitsEx Method</span></span>](igchost2-setgcstartuplimitsex-method.md)|<span data-ttu-id="0e3a5-109">设置第0代的段大小和最大大小。</span><span class="sxs-lookup"><span data-stu-id="0e3a5-109">Sets the segment size and the maximum size for generation 0.</span></span> <span data-ttu-id="0e3a5-110">启用0代和大于的段大小 `DWORD` 。</span><span class="sxs-lookup"><span data-stu-id="0e3a5-110">Enables generation 0 and segment sizes larger than `DWORD`.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="0e3a5-111">要求</span><span class="sxs-lookup"><span data-stu-id="0e3a5-111">Requirements</span></span>  
 <span data-ttu-id="0e3a5-112">**平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="0e3a5-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0e3a5-113">**标头：** GCHost，GCHost</span><span class="sxs-lookup"><span data-stu-id="0e3a5-113">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="0e3a5-114">**库：** 作为资源包括在 Mscoree.dll 中</span><span class="sxs-lookup"><span data-stu-id="0e3a5-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0e3a5-115">**.NET Framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0e3a5-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0e3a5-116">另请参阅</span><span class="sxs-lookup"><span data-stu-id="0e3a5-116">See also</span></span>

- [<span data-ttu-id="0e3a5-117">承载接口</span><span class="sxs-lookup"><span data-stu-id="0e3a5-117">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="0e3a5-118">CLR 承载接口</span><span class="sxs-lookup"><span data-stu-id="0e3a5-118">CLR Hosting Interfaces</span></span>](clr-hosting-interfaces.md)
- [<span data-ttu-id="0e3a5-119">CorRuntimeHost 组件类</span><span class="sxs-lookup"><span data-stu-id="0e3a5-119">CorRuntimeHost Coclass</span></span>](corruntimehost-coclass.md)
