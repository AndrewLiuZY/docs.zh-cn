---
title: ICLRTaskManager 接口
ms.date: 03/30/2017
api_name:
- ICLRTaskManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTaskManager
helpviewer_keywords:
- ICLRTaskManager interface [.NET Framework hosting]
ms.assetid: 2bd55e0c-001b-41fd-b29d-f01670fe8216
topic_type:
- apiref
ms.openlocfilehash: 9e26071181e8e0712c753fa03d5e16eb85e5ee68
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762820"
---
# <a name="iclrtaskmanager-interface"></a><span data-ttu-id="a391c-102">ICLRTaskManager 接口</span><span class="sxs-lookup"><span data-stu-id="a391c-102">ICLRTaskManager Interface</span></span>
<span data-ttu-id="a391c-103">提供允许主机显式请求公共语言运行时（CLR）创建新任务、获取当前正在执行的任务以及设置任务的地理语言和区域性的方法。</span><span class="sxs-lookup"><span data-stu-id="a391c-103">Provides methods that allow the host to request explicitly that the common language runtime (CLR) create a new task, get the currently executing task, and set the geographic language and culture for the task.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a391c-104">方法</span><span class="sxs-lookup"><span data-stu-id="a391c-104">Methods</span></span>  
  
|<span data-ttu-id="a391c-105">方法</span><span class="sxs-lookup"><span data-stu-id="a391c-105">Method</span></span>|<span data-ttu-id="a391c-106">说明</span><span class="sxs-lookup"><span data-stu-id="a391c-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="a391c-107">CreateTask 方法</span><span class="sxs-lookup"><span data-stu-id="a391c-107">CreateTask Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-createtask-method.md)|<span data-ttu-id="a391c-108">显式请求 CLR 创建新的[ICLRTask](iclrtask-interface.md)实例。</span><span class="sxs-lookup"><span data-stu-id="a391c-108">Requests explicitly that the CLR create a new [ICLRTask](iclrtask-interface.md) instance.</span></span>|  
|[<span data-ttu-id="a391c-109">GetCurrentTask 方法</span><span class="sxs-lookup"><span data-stu-id="a391c-109">GetCurrentTask Method</span></span>](iclrtaskmanager-getcurrenttask-method.md)|<span data-ttu-id="a391c-110">获取 `ICLRTask` 表示当前正在执行的任务的实例。</span><span class="sxs-lookup"><span data-stu-id="a391c-110">Gets the `ICLRTask` instance that represents the task that is currently executing.</span></span>|  
|[<span data-ttu-id="a391c-111">GetCurrentTaskType 方法</span><span class="sxs-lookup"><span data-stu-id="a391c-111">GetCurrentTaskType Method</span></span>](iclrtaskmanager-getcurrenttasktype-method.md)|<span data-ttu-id="a391c-112">获取当前正在执行的任务的类型。</span><span class="sxs-lookup"><span data-stu-id="a391c-112">Gets the type of the task that is currently executing.</span></span>|  
|[<span data-ttu-id="a391c-113">SetLocale 方法</span><span class="sxs-lookup"><span data-stu-id="a391c-113">SetLocale Method</span></span>](iclrtaskmanager-setlocale-method.md)|<span data-ttu-id="a391c-114">通知 CLR 宿主已经修改了当前正在执行的任务的区域设置标识符。</span><span class="sxs-lookup"><span data-stu-id="a391c-114">Notifies the CLR that the host has modified the locale identifier on the currently executing task.</span></span>|  
|[<span data-ttu-id="a391c-115">SetUILocale 方法</span><span class="sxs-lookup"><span data-stu-id="a391c-115">SetUILocale Method</span></span>](iclrtaskmanager-setuilocale-method.md)|<span data-ttu-id="a391c-116">通知公共语言运行时宿主已经修改了当前正在执行的任务的用户界面区域设置标识符。</span><span class="sxs-lookup"><span data-stu-id="a391c-116">Notifies the common language runtime that the host has modified the user interface locale identifier on the currently executing task.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a391c-117">注解</span><span class="sxs-lookup"><span data-stu-id="a391c-117">Remarks</span></span>  
 <span data-ttu-id="a391c-118">宿主环境中运行的每个任务在主机端（ [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)的实例）和 CLR 端（ [ICLRTask](iclrtask-interface.md)的一个实例）上都具有表示形式。</span><span class="sxs-lookup"><span data-stu-id="a391c-118">Each task that is running in a hosted environment has representations both on the host side (an instance of [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)) and on the CLR side (an instance of [ICLRTask](iclrtask-interface.md)).</span></span> <span data-ttu-id="a391c-119">宿主或 CLR 可以启动任务创建，但宿主端表示形式必须与相应的 CLR 端表示形式相关联，以确保主机与 CLR 之间的有关任务的通信成功。</span><span class="sxs-lookup"><span data-stu-id="a391c-119">Either the host or the CLR can initiate the creation of a task, but the host-side representation must be associated with a corresponding CLR-side representation to ensure successful communication between the host and the CLR regarding the task.</span></span> <span data-ttu-id="a391c-120">必须先创建并实例化两个对象，然后托管代码才能在操作系统线程上执行。</span><span class="sxs-lookup"><span data-stu-id="a391c-120">The two objects must be created and instantiated before managed code can execute on an operating system thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a391c-121">要求</span><span class="sxs-lookup"><span data-stu-id="a391c-121">Requirements</span></span>  
 <span data-ttu-id="a391c-122">**平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a391c-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a391c-123">**标头：** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="a391c-123">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a391c-124">**库：** 作为资源包括在 Mscoree.dll 中</span><span class="sxs-lookup"><span data-stu-id="a391c-124">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a391c-125">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a391c-125">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a391c-126">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a391c-126">See also</span></span>

- [<span data-ttu-id="a391c-127">ICLRTask 接口</span><span class="sxs-lookup"><span data-stu-id="a391c-127">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="a391c-128">IHostTask 接口</span><span class="sxs-lookup"><span data-stu-id="a391c-128">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="a391c-129">IHostTaskManager 接口</span><span class="sxs-lookup"><span data-stu-id="a391c-129">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
- [<span data-ttu-id="a391c-130">承载接口</span><span class="sxs-lookup"><span data-stu-id="a391c-130">Hosting Interfaces</span></span>](hosting-interfaces.md)
