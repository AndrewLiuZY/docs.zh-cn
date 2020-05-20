---
title: FExecuteInAppDomainCallback 函数指针
ms.date: 03/30/2017
api_name:
- FExecuteInAppDomainCallback
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- FExecuteInAppDomainCallback
helpviewer_keywords:
- FExecuteInAppDomainCallback function pointer [.NET Framework hosting]
ms.assetid: 2709f18f-3eee-497f-bc33-3ab7a485599b
topic_type:
- apiref
ms.openlocfilehash: 6fd7a19d9fc77b43bbceb1b5e5399a455429e700
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616146"
---
# <a name="fexecuteinappdomaincallback-function-pointer"></a><span data-ttu-id="523f3-102">FExecuteInAppDomainCallback 函数指针</span><span class="sxs-lookup"><span data-stu-id="523f3-102">FExecuteInAppDomainCallback Function Pointer</span></span>
<span data-ttu-id="523f3-103">指向由公共语言运行时（CLR）调用以执行托管代码的函数。</span><span class="sxs-lookup"><span data-stu-id="523f3-103">Points to a function that is called by the common language runtime (CLR) to execute managed code.</span></span>  
  
 <span data-ttu-id="523f3-104">此函数指针在 .NET Framework 4 中已弃用。</span><span class="sxs-lookup"><span data-stu-id="523f3-104">This function pointer has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="523f3-105">语法</span><span class="sxs-lookup"><span data-stu-id="523f3-105">Syntax</span></span>  
  
```cpp  
typedef HRESULT (__stdcall *FExecuteInAppDomainCallback) (  
    [in] void  *cookie  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="523f3-106">参数</span><span class="sxs-lookup"><span data-stu-id="523f3-106">Parameters</span></span>  
 `cookie`  
 <span data-ttu-id="523f3-107">中指向包含要执行的托管代码的不透明调用方分配的内存的指针。</span><span class="sxs-lookup"><span data-stu-id="523f3-107">[in] A pointer to opaque caller-allocated memory that contains the managed code to be executed.</span></span>  
  
 <span data-ttu-id="523f3-108">此内存的分配和生存期由调用方（即 CLR）控制。</span><span class="sxs-lookup"><span data-stu-id="523f3-108">The allocation and lifetime of this memory are controlled by the caller (that is, the CLR).</span></span> <span data-ttu-id="523f3-109">这不是 CLR 托管堆内存。</span><span class="sxs-lookup"><span data-stu-id="523f3-109">This is not CLR managed-heap memory.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="523f3-110">要求</span><span class="sxs-lookup"><span data-stu-id="523f3-110">Requirements</span></span>  
 <span data-ttu-id="523f3-111">**平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="523f3-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="523f3-112">**标头：** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="523f3-112">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="523f3-113">**库：** Mscorwks.dll</span><span class="sxs-lookup"><span data-stu-id="523f3-113">**Library:** MSCorWks.dll</span></span>  
  
 <span data-ttu-id="523f3-114">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="523f3-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="523f3-115">另请参阅</span><span class="sxs-lookup"><span data-stu-id="523f3-115">See also</span></span>

- [<span data-ttu-id="523f3-116">弃用的 CLR 承载函数</span><span class="sxs-lookup"><span data-stu-id="523f3-116">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
