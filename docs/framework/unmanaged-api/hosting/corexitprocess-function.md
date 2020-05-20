---
title: CorExitProcess 函数
ms.date: 03/30/2017
api_name:
- CorExitProcess
api_location:
- mscoree.dll
- clr.dll
- mscorwks.dll
- mscoreei.dll
- mscorsvr.dll
api_type:
- DLLExport
f1_keywords:
- CorExitProcess
helpviewer_keywords:
- CorExitProcess function [.NET Framework hosting]
ms.assetid: a5cab4c6-990e-47f3-8798-cf422b791015
topic_type:
- apiref
ms.openlocfilehash: a60805e1fd78cb14835957a7afc14fe279cb20fb
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616562"
---
# <a name="corexitprocess-function"></a><span data-ttu-id="bcf80-102">CorExitProcess 函数</span><span class="sxs-lookup"><span data-stu-id="bcf80-102">CorExitProcess Function</span></span>
<span data-ttu-id="bcf80-103">关闭当前的非托管进程。</span><span class="sxs-lookup"><span data-stu-id="bcf80-103">Shuts down the current unmanaged process.</span></span>  
  
 <span data-ttu-id="bcf80-104">此函数已在 .NET Framework 4 中弃用。</span><span class="sxs-lookup"><span data-stu-id="bcf80-104">This function has been deprecated in the .NET Framework 4.</span></span> <span data-ttu-id="bcf80-105">改为使用[ICLRMetaHost：： ExitProcess](iclrmetahost-exitprocess-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="bcf80-105">Use the [ICLRMetaHost::ExitProcess](iclrmetahost-exitprocess-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bcf80-106">语法</span><span class="sxs-lookup"><span data-stu-id="bcf80-106">Syntax</span></span>  
  
```cpp  
void STDMETHODCALLTYPE CorExitProcess (
  int  exitCode  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bcf80-107">参数</span><span class="sxs-lookup"><span data-stu-id="bcf80-107">Parameters</span></span>  
 `exitCode`  
 <span data-ttu-id="bcf80-108">一个整数，指定进程退出代码。</span><span class="sxs-lookup"><span data-stu-id="bcf80-108">An integer that specifies the process exit code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bcf80-109">备注</span><span class="sxs-lookup"><span data-stu-id="bcf80-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="bcf80-110">从 .NET Framework 4 开始， `CorExitProcess` 退出进程中的每个已启动的运行时，而不只是旧 api 所绑定到的运行时。</span><span class="sxs-lookup"><span data-stu-id="bcf80-110">Beginning with the .NET Framework 4, `CorExitProcess` exits every started runtime in the process, not just the runtime to which the legacy APIs have been bound.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bcf80-111">要求</span><span class="sxs-lookup"><span data-stu-id="bcf80-111">Requirements</span></span>  
 <span data-ttu-id="bcf80-112">**平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="bcf80-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bcf80-113">**标头：** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="bcf80-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="bcf80-114">**库：** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="bcf80-114">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="bcf80-115">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bcf80-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bcf80-116">另请参阅</span><span class="sxs-lookup"><span data-stu-id="bcf80-116">See also</span></span>

- [<span data-ttu-id="bcf80-117">弃用的 CLR 承载函数</span><span class="sxs-lookup"><span data-stu-id="bcf80-117">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
