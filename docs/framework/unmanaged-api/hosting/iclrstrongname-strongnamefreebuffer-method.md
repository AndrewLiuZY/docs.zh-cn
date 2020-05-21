---
title: ICLRStrongName::StrongNameFreeBuffer 方法
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameFreeBuffer
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameFreeBuffer
helpviewer_keywords:
- StrongNameFreeBuffer method, ICLRStrongName interface [.NET Framework hosting]
- ICLRStrongName::StrongNameFreeBuffer method [.NET Framework hosting]
ms.assetid: 6148c508-bd1d-4a37-85c3-06ecb09cc857
topic_type:
- apiref
ms.openlocfilehash: bd5275f4ef8bfecdcfcfa48afe59f3bea579bd30
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762031"
---
# <a name="iclrstrongnamestrongnamefreebuffer-method"></a><span data-ttu-id="19ee2-102">ICLRStrongName::StrongNameFreeBuffer 方法</span><span class="sxs-lookup"><span data-stu-id="19ee2-102">ICLRStrongName::StrongNameFreeBuffer Method</span></span>
<span data-ttu-id="19ee2-103">释放先前调用强名称方法（如[ICLRStrongName：： StrongNameGetPublicKey](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetpublickey-method.md)、 [ICLRStrongName：： StrongNameTokenFromPublicKey](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfrompublickey-method.md)或[ICLRStrongName：： StrongNameSignatureGeneration](iclrstrongname-strongnamesignaturegeneration-method.md)）时分配的内存。</span><span class="sxs-lookup"><span data-stu-id="19ee2-103">Frees memory that was allocated with a previous call to a strong name method such as [ICLRStrongName::StrongNameGetPublicKey](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetpublickey-method.md), [ICLRStrongName::StrongNameTokenFromPublicKey](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfrompublickey-method.md), or [ICLRStrongName::StrongNameSignatureGeneration](iclrstrongname-strongnamesignaturegeneration-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="19ee2-104">语法</span><span class="sxs-lookup"><span data-stu-id="19ee2-104">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameFreeBuffer (
   [in] BYTE   *pbMemory  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="19ee2-105">参数</span><span class="sxs-lookup"><span data-stu-id="19ee2-105">Parameters</span></span>  
 `pbMemory`  
 <span data-ttu-id="19ee2-106">中指向要释放的内存的指针。</span><span class="sxs-lookup"><span data-stu-id="19ee2-106">[in] A pointer to the memory to free.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="19ee2-107">返回值</span><span class="sxs-lookup"><span data-stu-id="19ee2-107">Return Value</span></span>  
 <span data-ttu-id="19ee2-108">`S_OK`如果该方法已成功完成，则为;否则，表示失败的 HRESULT 值（请参阅列表的[常见 HRESULT 值](/windows/win32/seccrypto/common-hresult-values)）。</span><span class="sxs-lookup"><span data-stu-id="19ee2-108">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="19ee2-109">要求</span><span class="sxs-lookup"><span data-stu-id="19ee2-109">Requirements</span></span>  
 <span data-ttu-id="19ee2-110">**平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="19ee2-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="19ee2-111">**标头：** MetaHost</span><span class="sxs-lookup"><span data-stu-id="19ee2-111">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="19ee2-112">**库：** 作为资源包括在 Mscoree.dll 中</span><span class="sxs-lookup"><span data-stu-id="19ee2-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="19ee2-113">**.NET Framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="19ee2-113">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="19ee2-114">另请参阅</span><span class="sxs-lookup"><span data-stu-id="19ee2-114">See also</span></span>

- [<span data-ttu-id="19ee2-115">ICLRStrongName 接口</span><span class="sxs-lookup"><span data-stu-id="19ee2-115">ICLRStrongName Interface</span></span>](iclrstrongname-interface.md)
