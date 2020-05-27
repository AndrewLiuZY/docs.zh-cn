---
title: IMetaDataDispenserEx::FindAssemblyModule 方法
ms.date: 03/30/2017
api_name:
- IMetaDataDispenserEx.FindAssemblyModule
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataDispenserEx::FindAssemblyModule
helpviewer_keywords:
- FindAssemblyModule method [.NET Framework metadata]
- IMetaDataDispenserEx::FindAssemblyModule method [.NET Framework metadata]
ms.assetid: d1fb65e1-7e19-4513-85b1-44f87c294d3e
topic_type:
- apiref
ms.openlocfilehash: 64f1e2a8f05616c7ca84bc130428629b1176e985
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/27/2020
ms.locfileid: "84006176"
---
# <a name="imetadatadispenserexfindassemblymodule-method"></a><span data-ttu-id="83296-102">IMetaDataDispenserEx::FindAssemblyModule 方法</span><span class="sxs-lookup"><span data-stu-id="83296-102">IMetaDataDispenserEx::FindAssemblyModule Method</span></span>
<span data-ttu-id="83296-103">未实现此方法。</span><span class="sxs-lookup"><span data-stu-id="83296-103">This method is not implemented.</span></span> <span data-ttu-id="83296-104">如果调用，它将返回 E_NOTIMPL。</span><span class="sxs-lookup"><span data-stu-id="83296-104">If called, it returns E_NOTIMPL.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="83296-105">语法</span><span class="sxs-lookup"><span data-stu-id="83296-105">Syntax</span></span>  
  
```cpp  
HRESULT FindAssemblyModule(  
    [in]  LPCWSTR  szAppBase,  
    [in]  LPCWSTR  szPrivateBin,  
    [in]  LPCWSTR  szGlobalBin,  
    [in]  LPCWSTR  szAssemblyName,  
    [in]  LPCWSTR  szModuleName,  
    [out] LPCWSTR  szName,  
    [in]  ULONG    cchName,  
    [out] ULONG    *pcName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="83296-106">参数</span><span class="sxs-lookup"><span data-stu-id="83296-106">Parameters</span></span>  
 `szAppBase`  
 <span data-ttu-id="83296-107">中不使用。</span><span class="sxs-lookup"><span data-stu-id="83296-107">[in] Not used.</span></span>  
  
 `szPrivateBin`  
 <span data-ttu-id="83296-108">中不使用。</span><span class="sxs-lookup"><span data-stu-id="83296-108">[in] Not used.</span></span>  
  
 `szGlobalBin`  
 <span data-ttu-id="83296-109">中不使用。</span><span class="sxs-lookup"><span data-stu-id="83296-109">[in] Not used.</span></span>  
  
 `szAssemblyName`  
 <span data-ttu-id="83296-110">中模块的名称。</span><span class="sxs-lookup"><span data-stu-id="83296-110">[in] The name of the module.</span></span>  
  
 `szModuleName`  
 <span data-ttu-id="83296-111">中要查找的程序集。</span><span class="sxs-lookup"><span data-stu-id="83296-111">[in] The assembly to be found.</span></span>  
  
 `szName`  
 <span data-ttu-id="83296-112">弄程序集的简单名称。</span><span class="sxs-lookup"><span data-stu-id="83296-112">[out] The simple name of the assembly.</span></span>  
  
 `cchName`  
 <span data-ttu-id="83296-113">中的大小（以字节为单位） `szName` 。</span><span class="sxs-lookup"><span data-stu-id="83296-113">[in] The size, in bytes, of `szName`.</span></span>  
  
 `pcName`  
 <span data-ttu-id="83296-114">弄中实际返回的字符数 `szName` 。</span><span class="sxs-lookup"><span data-stu-id="83296-114">[out] The number of characters actually returned in `szName`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="83296-115">要求</span><span class="sxs-lookup"><span data-stu-id="83296-115">Requirements</span></span>  
 <span data-ttu-id="83296-116">**平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="83296-116">**Platform:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="83296-117">**标头：** Cor</span><span class="sxs-lookup"><span data-stu-id="83296-117">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="83296-118">**库：** 用作 Mscoree.dll 中的资源</span><span class="sxs-lookup"><span data-stu-id="83296-118">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="83296-119">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="83296-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="83296-120">另请参阅</span><span class="sxs-lookup"><span data-stu-id="83296-120">See also</span></span>

- [<span data-ttu-id="83296-121">IMetaDataDispenserEx 接口</span><span class="sxs-lookup"><span data-stu-id="83296-121">IMetaDataDispenserEx Interface</span></span>](imetadatadispenserex-interface.md)
- [<span data-ttu-id="83296-122">IMetaDataDispenser 接口</span><span class="sxs-lookup"><span data-stu-id="83296-122">IMetaDataDispenser Interface</span></span>](imetadatadispenser-interface.md)
