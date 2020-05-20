---
title: GetRequestedRuntimeVersionForCLSID 函数
ms.date: 03/30/2017
api_name:
- GetRequestedRuntimeVersionForCLSID
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- GetRequestedRuntimeVersionForCLSID
helpviewer_keywords:
- GetRequestedRuntimeVersionForCLSID function [.NET Framework hosting]
ms.assetid: 5bb12f9a-0612-434b-b4ed-2db636a20bec
topic_type:
- apiref
ms.openlocfilehash: 899d6e74902e47f1f41b849bd5c25048baa175f7
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/19/2020
ms.locfileid: "83617134"
---
# <a name="getrequestedruntimeversionforclsid-function"></a><span data-ttu-id="4867c-102">GetRequestedRuntimeVersionForCLSID 函数</span><span class="sxs-lookup"><span data-stu-id="4867c-102">GetRequestedRuntimeVersionForCLSID Function</span></span>
<span data-ttu-id="4867c-103">获取具有指定的类的相应公共语言运行时（CLR）版本信息 `CLSID` 。</span><span class="sxs-lookup"><span data-stu-id="4867c-103">Gets the appropriate common language runtime (CLR) version information for the class with the specified `CLSID`.</span></span>  
  
 <span data-ttu-id="4867c-104">此函数已在 .NET Framework 4 中弃用。</span><span class="sxs-lookup"><span data-stu-id="4867c-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4867c-105">语法</span><span class="sxs-lookup"><span data-stu-id="4867c-105">Syntax</span></span>  
  
```cpp  
HRESULT GetRequestedRuntimeVersionForCLSID (  
    [in]  REFCLSID   rclsid,
    [out]  LPWSTR     pVersion,
    [in]  DWORD      cchBuffer,
    [out] DWORD*     dwLength,
    [in]  CLSID_RESOLUTION_FLAGS dwResolutionFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4867c-106">参数</span><span class="sxs-lookup"><span data-stu-id="4867c-106">Parameters</span></span>  
 `rclsid`  
 <span data-ttu-id="4867c-107">中 `CLSID`组件的。</span><span class="sxs-lookup"><span data-stu-id="4867c-107">[in]  The `CLSID` of the component.</span></span>  
  
 `pVersion`  
 <span data-ttu-id="4867c-108">弄 一个缓冲区，其中包含成功完成后的版本号字符串。</span><span class="sxs-lookup"><span data-stu-id="4867c-108">[out]  A buffer that contains the version number string upon successful completion.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="4867c-109">中 缓冲区的大小（宽字符） `pVersion` 。</span><span class="sxs-lookup"><span data-stu-id="4867c-109">[in]  The size, in wide characters, of the `pVersion` buffer.</span></span>  
  
 `dwLength`  
 <span data-ttu-id="4867c-110">弄返回的缓冲区的长度（以字节为单位）。</span><span class="sxs-lookup"><span data-stu-id="4867c-110">[out] The length, in bytes, of the returned buffer.</span></span>  
  
 `dwResolutionFlags`  
 <span data-ttu-id="4867c-111">中 CLSID_RESOLUTION_FLAGS 值之一。</span><span class="sxs-lookup"><span data-stu-id="4867c-111">[in]  One of the CLSID_RESOLUTION_FLAGS values.</span></span> <span data-ttu-id="4867c-112">支持以下值：</span><span class="sxs-lookup"><span data-stu-id="4867c-112">The following values are supported:</span></span>  
  
- <span data-ttu-id="4867c-113">CLSID_RESOLUTION_DEFAULT：（0x0）指定应使用默认的互操作行为。</span><span class="sxs-lookup"><span data-stu-id="4867c-113">CLSID_RESOLUTION_DEFAULT: (0x0) Specifies that default interop behavior should be used.</span></span>  
  
- <span data-ttu-id="4867c-114">CLSID_RESOLUTION_REGISTERED：（0x1）指定应搜索注册表并应用填充程序策略。</span><span class="sxs-lookup"><span data-stu-id="4867c-114">CLSID_RESOLUTION_REGISTERED: (0x1) Specifies that the registry should be searched and shim policy should be applied.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4867c-115">返回值</span><span class="sxs-lookup"><span data-stu-id="4867c-115">Return Value</span></span>  
  
|<span data-ttu-id="4867c-116">HRESULT</span><span class="sxs-lookup"><span data-stu-id="4867c-116">HRESULT</span></span>|<span data-ttu-id="4867c-117">说明</span><span class="sxs-lookup"><span data-stu-id="4867c-117">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="4867c-118">S_OK</span><span class="sxs-lookup"><span data-stu-id="4867c-118">S_OK</span></span>|<span data-ttu-id="4867c-119">函数已成功返回。</span><span class="sxs-lookup"><span data-stu-id="4867c-119">The function returned successfully.</span></span>|  
|<span data-ttu-id="4867c-120">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="4867c-120">E_INVALIDARG</span></span>|<span data-ttu-id="4867c-121">其中一个参数的类型或格式无效。</span><span class="sxs-lookup"><span data-stu-id="4867c-121">One of the parameters has an invalid type or format.</span></span>|  
|<span data-ttu-id="4867c-122">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="4867c-122">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="4867c-123">`pVersion`缓冲区不够大，无法容纳整个版本字符串。</span><span class="sxs-lookup"><span data-stu-id="4867c-123">The `pVersion` buffer is not large enough to hold the entire version string.</span></span>|  
|<span data-ttu-id="4867c-124">REGDB_E_CLASSNOTREG</span><span class="sxs-lookup"><span data-stu-id="4867c-124">REGDB_E_CLASSNOTREG</span></span>|<span data-ttu-id="4867c-125">没有用指定的注册的类 `CLSID` 。</span><span class="sxs-lookup"><span data-stu-id="4867c-125">There is no class registered with the specified `CLSID`.</span></span>|  
|<span data-ttu-id="4867c-126">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="4867c-126">E_POINTER</span></span>|<span data-ttu-id="4867c-127">`dwLength`为 null，或 `cchBuffer` 足以容纳版本字符串，但 `pVersion` 为 null。</span><span class="sxs-lookup"><span data-stu-id="4867c-127">`dwLength` is null, or `cchBuffer` is large enough to hold the version string, but `pVersion` is null.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="4867c-128">要求</span><span class="sxs-lookup"><span data-stu-id="4867c-128">Requirements</span></span>  
 <span data-ttu-id="4867c-129">**平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="4867c-129">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4867c-130">**标头：** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="4867c-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="4867c-131">**.NET Framework 版本：**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4867c-131">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4867c-132">另请参阅</span><span class="sxs-lookup"><span data-stu-id="4867c-132">See also</span></span>

- [<span data-ttu-id="4867c-133">弃用的 CLR 承载函数</span><span class="sxs-lookup"><span data-stu-id="4867c-133">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
