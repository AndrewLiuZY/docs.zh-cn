---
title: _CorValidateImage 函数
ms.date: 03/30/2017
api_name:
- _CorValidateImage
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- _CorValidateImage
helpviewer_keywords:
- _CorValidateImage function [.NET Framework hosting]
ms.assetid: 0117e080-05f9-4772-885d-e1847230947c
topic_type:
- apiref
ms.openlocfilehash: 8841fab0517353849ef99594bcbd03dda772c766
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616497"
---
# <a name="_corvalidateimage-function"></a><span data-ttu-id="339c5-102">_CorValidateImage 函数</span><span class="sxs-lookup"><span data-stu-id="339c5-102">_CorValidateImage Function</span></span>
<span data-ttu-id="339c5-103">验证托管模块映像，并在加载后通知操作系统加载程序。</span><span class="sxs-lookup"><span data-stu-id="339c5-103">Validates managed module images, and notifies the operating system loader after they have been loaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="339c5-104">语法</span><span class="sxs-lookup"><span data-stu-id="339c5-104">Syntax</span></span>  
  
```cpp  
STDAPI _CorValidateImage (
   [in] PVOID* ImageBase,  
   [in] LPCWSTR FileName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="339c5-105">参数</span><span class="sxs-lookup"><span data-stu-id="339c5-105">Parameters</span></span>  
 `ImageBase`  
 <span data-ttu-id="339c5-106">中一个指针，指向要作为托管代码验证的图像的起始位置。</span><span class="sxs-lookup"><span data-stu-id="339c5-106">[in] A pointer to the starting location of the image to validate as managed code.</span></span> <span data-ttu-id="339c5-107">必须已将该映像加载到内存中。</span><span class="sxs-lookup"><span data-stu-id="339c5-107">The image must already be loaded into memory.</span></span>  
  
 `FileName`  
 <span data-ttu-id="339c5-108">中图像的文件名。</span><span class="sxs-lookup"><span data-stu-id="339c5-108">[in] The file name of the image.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="339c5-109">返回值</span><span class="sxs-lookup"><span data-stu-id="339c5-109">Return Value</span></span>  
 <span data-ttu-id="339c5-110">此函数返回标准值 `E_INVALIDARG` 、、 `E_OUTOFMEMORY` `E_UNEXPECTED` 和，以及 `E_FAIL` 以下值。</span><span class="sxs-lookup"><span data-stu-id="339c5-110">This function returns the standard values `E_INVALIDARG`, `E_OUTOFMEMORY`, `E_UNEXPECTED`, and `E_FAIL`, as well as the following values.</span></span>  
  
|<span data-ttu-id="339c5-111">返回值</span><span class="sxs-lookup"><span data-stu-id="339c5-111">Return value</span></span>|<span data-ttu-id="339c5-112">说明</span><span class="sxs-lookup"><span data-stu-id="339c5-112">Description</span></span>|  
|------------------|-----------------|  
|`STATUS_INVALID_IMAGE_FORMAT`|<span data-ttu-id="339c5-113">图像无效。</span><span class="sxs-lookup"><span data-stu-id="339c5-113">The image is invalid.</span></span> <span data-ttu-id="339c5-114">此值具有 HRESULT 0xC000007BL。</span><span class="sxs-lookup"><span data-stu-id="339c5-114">This value has the HRESULT 0xC000007BL.</span></span>|  
|`STATUS_SUCCESS`|<span data-ttu-id="339c5-115">图像有效。</span><span class="sxs-lookup"><span data-stu-id="339c5-115">The image is valid.</span></span> <span data-ttu-id="339c5-116">此值具有 HRESULT 0x00000000L。</span><span class="sxs-lookup"><span data-stu-id="339c5-116">This value has the HRESULT 0x00000000L.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="339c5-117">备注</span><span class="sxs-lookup"><span data-stu-id="339c5-117">Remarks</span></span>  
 <span data-ttu-id="339c5-118">在 Windows XP 和更高版本中，操作系统加载程序通过检查通用对象文件格式（COFF）标头中的 COM 描述符目录位检查托管模块。</span><span class="sxs-lookup"><span data-stu-id="339c5-118">In Windows XP and later versions, the operating system loader checks for managed modules by examining the COM Descriptor Directory bit in the common object file format (COFF) header.</span></span> <span data-ttu-id="339c5-119">设置位表示托管模块。</span><span class="sxs-lookup"><span data-stu-id="339c5-119">A set bit indicates a managed module.</span></span> <span data-ttu-id="339c5-120">如果加载程序检测到托管模块，它将加载 Mscoree.dll 并调用 `_CorValidateImage` ，这会执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="339c5-120">If the loader detects a managed module, it loads MsCorEE.dll and calls `_CorValidateImage`, which performs the following actions:</span></span>  
  
- <span data-ttu-id="339c5-121">确认映像是有效的托管模块。</span><span class="sxs-lookup"><span data-stu-id="339c5-121">Confirms that the image is a valid managed module.</span></span>  
  
- <span data-ttu-id="339c5-122">将映像中的入口点更改为公共语言运行时（CLR）中的入口点。</span><span class="sxs-lookup"><span data-stu-id="339c5-122">Changes the entry point in the image to an entry point in the common language runtime (CLR).</span></span>  
  
- <span data-ttu-id="339c5-123">对于64位版本的 Windows，通过将其从 PE32 转换为 PE32 + 格式修改内存中的映像。</span><span class="sxs-lookup"><span data-stu-id="339c5-123">For 64-bit versions of Windows, modifies the image that is in memory by transforming it from PE32 to PE32+ format.</span></span>  
  
- <span data-ttu-id="339c5-124">加载托管模块映像时返回到加载程序。</span><span class="sxs-lookup"><span data-stu-id="339c5-124">Returns to the loader when the managed module images are loaded.</span></span>  
  
 <span data-ttu-id="339c5-125">对于可执行映像，操作系统加载器会调用[_CorExeMain](../../../../docs/framework/unmanaged-api/hosting/corexemain-function.md)函数，而不考虑可执行文件中指定的入口点。</span><span class="sxs-lookup"><span data-stu-id="339c5-125">For executable images, the operating system loader then calls the [_CorExeMain](../../../../docs/framework/unmanaged-api/hosting/corexemain-function.md) function, regardless of the entry point specified in the executable.</span></span> <span data-ttu-id="339c5-126">对于 DLL 程序集映像，加载程序将调用[_CorDllMain](cordllmain-function.md)函数。</span><span class="sxs-lookup"><span data-stu-id="339c5-126">For DLL assembly images, the loader calls the [_CorDllMain](cordllmain-function.md) function.</span></span>  
  
 <span data-ttu-id="339c5-127">`_CorExeMain`或 `_CorDllMain` 执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="339c5-127">`_CorExeMain` or `_CorDllMain` performs the following actions:</span></span>  
  
- <span data-ttu-id="339c5-128">初始化 CLR。</span><span class="sxs-lookup"><span data-stu-id="339c5-128">Initializes the CLR.</span></span>  
  
- <span data-ttu-id="339c5-129">定位程序集的 CLR 头中的托管入口点。</span><span class="sxs-lookup"><span data-stu-id="339c5-129">Locates the managed entry point from the assembly's CLR header.</span></span>  
  
- <span data-ttu-id="339c5-130">开始执行。</span><span class="sxs-lookup"><span data-stu-id="339c5-130">Begins execution.</span></span>  
  
 <span data-ttu-id="339c5-131">卸载托管模块映像时，加载程序将调用[_CorImageUnloading](corimageunloading-function.md)函数。</span><span class="sxs-lookup"><span data-stu-id="339c5-131">The loader calls the [_CorImageUnloading](corimageunloading-function.md) function when managed module images are unloaded.</span></span> <span data-ttu-id="339c5-132">但是，此函数不执行任何操作;它仅返回。</span><span class="sxs-lookup"><span data-stu-id="339c5-132">However, this function does not perform any action; it just returns.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="339c5-133">要求</span><span class="sxs-lookup"><span data-stu-id="339c5-133">Requirements</span></span>  
 <span data-ttu-id="339c5-134">**平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="339c5-134">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="339c5-135">**标头：** Cor</span><span class="sxs-lookup"><span data-stu-id="339c5-135">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="339c5-136">**库：** 作为资源包括在 Mscoree.dll 中</span><span class="sxs-lookup"><span data-stu-id="339c5-136">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="339c5-137">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="339c5-137">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="339c5-138">另请参阅</span><span class="sxs-lookup"><span data-stu-id="339c5-138">See also</span></span>

- [<span data-ttu-id="339c5-139">元数据全局静态函数</span><span class="sxs-lookup"><span data-stu-id="339c5-139">Metadata Global Static Functions</span></span>](../metadata/metadata-global-static-functions.md)
