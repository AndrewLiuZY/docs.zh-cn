---
title: IHostIoCompletionManager::SetMaxThreads 方法
ms.date: 03/30/2017
api_name:
- IHostIoCompletionManager.SetMaxThreads
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostIoCompletionManager::SetMaxThreads
helpviewer_keywords:
- IHostIoCompletionManager::SetMaxThreads method [.NET Framework hosting]
- SetMaxThreads method, IHostIoCompletionManager interface [.NET Framework hosting]
ms.assetid: ebad4f40-d9f1-4dc6-9b27-a89c9eb3926f
topic_type:
- apiref
ms.openlocfilehash: 55727903a7f3c798e7472de6de5249de98af7ae7
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/22/2020
ms.locfileid: "83804676"
---
# <a name="ihostiocompletionmanagersetmaxthreads-method"></a><span data-ttu-id="0faa7-102">IHostIoCompletionManager::SetMaxThreads 方法</span><span class="sxs-lookup"><span data-stu-id="0faa7-102">IHostIoCompletionManager::SetMaxThreads Method</span></span>
<span data-ttu-id="0faa7-103">设置主机 allots i/o 请求的最大线程数。</span><span class="sxs-lookup"><span data-stu-id="0faa7-103">Sets the maximum number of threads that the host allots to service I/O requests.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0faa7-104">语法</span><span class="sxs-lookup"><span data-stu-id="0faa7-104">Syntax</span></span>  
  
```cpp  
HRESULT SetMaxThreads (  
    [in] DWORD dwMaxIoCompletionThreads  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0faa7-105">参数</span><span class="sxs-lookup"><span data-stu-id="0faa7-105">Parameters</span></span>  
 `dwMaxIoCompletionThreads`  
 <span data-ttu-id="0faa7-106">中为 i/o 请求分配的最大线程数。</span><span class="sxs-lookup"><span data-stu-id="0faa7-106">[in] The maximum number of threads to allot for I/O requests.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0faa7-107">返回值</span><span class="sxs-lookup"><span data-stu-id="0faa7-107">Return Value</span></span>  
  
|<span data-ttu-id="0faa7-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="0faa7-108">HRESULT</span></span>|<span data-ttu-id="0faa7-109">说明</span><span class="sxs-lookup"><span data-stu-id="0faa7-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="0faa7-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="0faa7-110">S_OK</span></span>|<span data-ttu-id="0faa7-111">`SetMaxThreads`已成功返回。</span><span class="sxs-lookup"><span data-stu-id="0faa7-111">`SetMaxThreads` returned successfully.</span></span>|  
|<span data-ttu-id="0faa7-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="0faa7-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="0faa7-113">公共语言运行时（CLR）未加载到进程中，或 CLR 处于无法运行托管代码或成功处理调用的状态。</span><span class="sxs-lookup"><span data-stu-id="0faa7-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="0faa7-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="0faa7-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="0faa7-115">调用超时。</span><span class="sxs-lookup"><span data-stu-id="0faa7-115">The call timed out.</span></span>|  
|<span data-ttu-id="0faa7-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="0faa7-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="0faa7-117">调用方不拥有该锁。</span><span class="sxs-lookup"><span data-stu-id="0faa7-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="0faa7-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="0faa7-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="0faa7-119">已阻止的线程或纤程正在等待某个事件时，该事件被取消。</span><span class="sxs-lookup"><span data-stu-id="0faa7-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="0faa7-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="0faa7-120">E_FAIL</span></span>|<span data-ttu-id="0faa7-121">发生未知的灾难性故障。</span><span class="sxs-lookup"><span data-stu-id="0faa7-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="0faa7-122">当方法返回 E_FAIL 时，CLR 在该进程内将不再可用。</span><span class="sxs-lookup"><span data-stu-id="0faa7-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="0faa7-123">对宿主方法的后续调用会返回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="0faa7-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="0faa7-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="0faa7-124">E_NOTIMPL</span></span>|<span data-ttu-id="0faa7-125">宿主不提供的实现 `SetMaxThreads` 。</span><span class="sxs-lookup"><span data-stu-id="0faa7-125">The host does not provide an implementation of `SetMaxThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0faa7-126">备注</span><span class="sxs-lookup"><span data-stu-id="0faa7-126">Remarks</span></span>  
 <span data-ttu-id="0faa7-127">`SetMaxThreads`向 CLR 提供一个机会，用于设置对 i/o 端口上的服务请求可用的最大线程数。</span><span class="sxs-lookup"><span data-stu-id="0faa7-127">`SetMaxThreads` provides the CLR with an opportunity to set the maximum number of threads that are available to service requests on I/O ports.</span></span> <span data-ttu-id="0faa7-128">出于实现、性能或可伸缩性等原因，主机可能需要独占控制线程池的大小。</span><span class="sxs-lookup"><span data-stu-id="0faa7-128">A host might need exclusive control over the size of the thread pool, for reasons such as implementation, performance, or scalability.</span></span> <span data-ttu-id="0faa7-129">出于此原因，主机不需要实现 `SetMaxThreads` 。</span><span class="sxs-lookup"><span data-stu-id="0faa7-129">For this reason, the host is not required to implement `SetMaxThreads`.</span></span> <span data-ttu-id="0faa7-130">在这种情况下，主机应从此方法返回 E_NOTIMPL。</span><span class="sxs-lookup"><span data-stu-id="0faa7-130">In this case, a host should return E_NOTIMPL from this method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0faa7-131">要求</span><span class="sxs-lookup"><span data-stu-id="0faa7-131">Requirements</span></span>  
 <span data-ttu-id="0faa7-132">**平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="0faa7-132">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0faa7-133">**标头：** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="0faa7-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="0faa7-134">**库：** 作为资源包括在 Mscoree.dll 中</span><span class="sxs-lookup"><span data-stu-id="0faa7-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0faa7-135">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0faa7-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0faa7-136">另请参阅</span><span class="sxs-lookup"><span data-stu-id="0faa7-136">See also</span></span>

- [<span data-ttu-id="0faa7-137">ICLRIoCompletionManager 接口</span><span class="sxs-lookup"><span data-stu-id="0faa7-137">ICLRIoCompletionManager Interface</span></span>](iclriocompletionmanager-interface.md)
- [<span data-ttu-id="0faa7-138">IHostIoCompletionManager 接口</span><span class="sxs-lookup"><span data-stu-id="0faa7-138">IHostIoCompletionManager Interface</span></span>](ihostiocompletionmanager-interface.md)
