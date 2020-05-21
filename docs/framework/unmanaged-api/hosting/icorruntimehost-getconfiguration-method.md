---
title: ICorRuntimeHost::GetConfiguration 方法
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost.GetConfiguration
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::GetConfiguration
helpviewer_keywords:
- ICorRuntimeHost::GetConfiguration method [.NET Framework hosting]
- GetConfiguration method [.NET Framework hosting]
ms.assetid: c431617a-b055-44a0-8730-48b7a86d9610
topic_type:
- apiref
ms.openlocfilehash: 88abdbc62c8b27f48c5629afb99ab6e30ee67e00
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762261"
---
# <a name="icorruntimehostgetconfiguration-method"></a><span data-ttu-id="49e05-102">ICorRuntimeHost::GetConfiguration 方法</span><span class="sxs-lookup"><span data-stu-id="49e05-102">ICorRuntimeHost::GetConfiguration Method</span></span>
<span data-ttu-id="49e05-103">获取一个对象，该对象允许宿主指定公共语言运行时（CLR）的回调配置。</span><span class="sxs-lookup"><span data-stu-id="49e05-103">Gets an object that allows the host to specify the callback configuration of the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="49e05-104">语法</span><span class="sxs-lookup"><span data-stu-id="49e05-104">Syntax</span></span>  
  
```cpp  
HRESULT GetConfiguration(  
    [out] ICorConfiguration** pConfiguration  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="49e05-105">参数</span><span class="sxs-lookup"><span data-stu-id="49e05-105">Parameters</span></span>  
 `pConfiguration`  
 <span data-ttu-id="49e05-106">弄指向可用于配置 CLR 的[ICorConfiguration](icorconfiguration-interface.md)对象地址的指针。</span><span class="sxs-lookup"><span data-stu-id="49e05-106">[out] A pointer to the address of an [ICorConfiguration](icorconfiguration-interface.md) object that can be used to configure the CLR.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="49e05-107">注解</span><span class="sxs-lookup"><span data-stu-id="49e05-107">Remarks</span></span>  
 <span data-ttu-id="49e05-108">必须在初始化之前配置 CLR;否则，该 `GetConfiguration` 方法将返回一个 HRESULT，指示错误。</span><span class="sxs-lookup"><span data-stu-id="49e05-108">The CLR must be configured prior to its initialization; otherwise, the `GetConfiguration` method returns an HRESULT indicating an error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="49e05-109">要求</span><span class="sxs-lookup"><span data-stu-id="49e05-109">Requirements</span></span>  
 <span data-ttu-id="49e05-110">**平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="49e05-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="49e05-111">**标头：** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="49e05-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="49e05-112">**库：** 作为资源包括在 Mscoree.dll 中</span><span class="sxs-lookup"><span data-stu-id="49e05-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="49e05-113">**.NET Framework 版本：** 1.0、1。1</span><span class="sxs-lookup"><span data-stu-id="49e05-113">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="49e05-114">另请参阅</span><span class="sxs-lookup"><span data-stu-id="49e05-114">See also</span></span>

- [<span data-ttu-id="49e05-115">ICorRuntimeHost 接口</span><span class="sxs-lookup"><span data-stu-id="49e05-115">ICorRuntimeHost Interface</span></span>](icorruntimehost-interface.md)
