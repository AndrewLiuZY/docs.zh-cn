---
title: CorLaunchApplication 函数
ms.date: 03/30/2017
api_name:
- CorLaunchApplication
api_location:
- mscoree.dll
- clr.dll
api_type:
- COM
f1_keywords:
- CorLaunchApplication
helpviewer_keywords:
- CorLaunchApplication function [.NET Framework hosting]
ms.assetid: 71f362a9-8fe2-47ce-9302-05a645cf3d7d
topic_type:
- apiref
ms.openlocfilehash: 031bfc3d7fcd9f1f04e616e460cb3201813eae55
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616549"
---
# <a name="corlaunchapplication-function"></a><span data-ttu-id="7a9ba-102">CorLaunchApplication 函数</span><span class="sxs-lookup"><span data-stu-id="7a9ba-102">CorLaunchApplication Function</span></span>
<span data-ttu-id="7a9ba-103">使用指定的清单和其他应用程序数据，在指定的网络路径下启动应用程序。</span><span class="sxs-lookup"><span data-stu-id="7a9ba-103">Starts the application at the specified network path, using the specified manifests and other application data.</span></span>  
  
 <span data-ttu-id="7a9ba-104">此函数已在 .NET Framework 4 中弃用。</span><span class="sxs-lookup"><span data-stu-id="7a9ba-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7a9ba-105">语法</span><span class="sxs-lookup"><span data-stu-id="7a9ba-105">Syntax</span></span>  
  
```cpp  
HRESULT CorLaunchApplication (  
    [in]  HOST_TYPE                dwClickOnceHost,  
    [in]  LPCWSTR                  pwzAppFullName,  
    [in]  DWORD                    dwManifestPaths,  
    [in]  LPCWSTR                 *ppwzManifestPaths,  
    [in]  DWORD                    dwActivationData,  
    [in]  LPCWSTR                 *ppwzActivationData,  
    [out] LPPROCESS_INFORMATION    lpProcessInformation  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7a9ba-106">参数</span><span class="sxs-lookup"><span data-stu-id="7a9ba-106">Parameters</span></span>  
 `dwClickOnceHost`  
 <span data-ttu-id="7a9ba-107">中一个[HOST_TYPE](host-type-enumeration.md)枚举的值，该值指定启动应用程序的主机的类型。</span><span class="sxs-lookup"><span data-stu-id="7a9ba-107">[in] A value of the [HOST_TYPE](host-type-enumeration.md) enumeration that specifies the type of host that is launching the application.</span></span>  
  
 `pwzAppFullName`  
 <span data-ttu-id="7a9ba-108">中正在启动的应用程序的完整名称。</span><span class="sxs-lookup"><span data-stu-id="7a9ba-108">[in] The full name of the application that is being launched.</span></span>  
  
 `dwManifestPaths`  
 <span data-ttu-id="7a9ba-109">中应用程序的清单路径数。</span><span class="sxs-lookup"><span data-stu-id="7a9ba-109">[in] The number of manifest paths for the application.</span></span>  
  
 `ppwzManifestPaths`  
 <span data-ttu-id="7a9ba-110">中一个字符串数组，其中每个字符串指定要启动的应用程序的清单的路径。</span><span class="sxs-lookup"><span data-stu-id="7a9ba-110">[in] An array of strings, each of which specifies a path to a manifest for the application that is being launched.</span></span>  
  
 `dwActivationData`  
 <span data-ttu-id="7a9ba-111">中正在启动的应用程序的激活数据项的数目。</span><span class="sxs-lookup"><span data-stu-id="7a9ba-111">[in] The number of activation data items for the application that is being launched.</span></span>  
  
 `ppwzActivationData`  
 <span data-ttu-id="7a9ba-112">中一个字符串数组，其中每个字符串都是要启动的应用程序的激活数据项。</span><span class="sxs-lookup"><span data-stu-id="7a9ba-112">[in] An array of strings, each of which is an activation data item for the application that is being launched.</span></span>  
  
 `lpProcessInformation`  
 <span data-ttu-id="7a9ba-113">弄一个指针，指向有关已加载应用程序的进程的信息。</span><span class="sxs-lookup"><span data-stu-id="7a9ba-113">[out] A pointer to information about the process in which the application has been loaded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7a9ba-114">要求</span><span class="sxs-lookup"><span data-stu-id="7a9ba-114">Requirements</span></span>  
 <span data-ttu-id="7a9ba-115">**平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="7a9ba-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7a9ba-116">**标头：** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="7a9ba-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="7a9ba-117">**库：** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="7a9ba-117">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7a9ba-118">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7a9ba-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7a9ba-119">另请参阅</span><span class="sxs-lookup"><span data-stu-id="7a9ba-119">See also</span></span>

- [<span data-ttu-id="7a9ba-120">弃用的 CLR 承载函数</span><span class="sxs-lookup"><span data-stu-id="7a9ba-120">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
