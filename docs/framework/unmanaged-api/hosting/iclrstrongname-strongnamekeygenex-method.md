---
title: ICLRStrongName::StrongNameKeyGenEx 方法
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameKeyGenEx
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameKeyGenEx
helpviewer_keywords:
- ICLRStrongName::StrongNameKeyGenEx method [.NET Framework hosting]
- StrongNameKeyGenEx method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: 1f8b59d0-5b72-45b8-ab74-c2b43ffc806e
topic_type:
- apiref
ms.openlocfilehash: fb18b7b5ac73a1f270af6fae95a23e04b17ca5f1
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/21/2020
ms.locfileid: "83763067"
---
# <a name="iclrstrongnamestrongnamekeygenex-method"></a><span data-ttu-id="d052d-102">ICLRStrongName::StrongNameKeyGenEx 方法</span><span class="sxs-lookup"><span data-stu-id="d052d-102">ICLRStrongName::StrongNameKeyGenEx Method</span></span>
<span data-ttu-id="d052d-103">使用指定的密钥大小生成新的公钥/私钥对，以便使用强名称。</span><span class="sxs-lookup"><span data-stu-id="d052d-103">Generates a new public/private key pair with the specified key size, for strong name use.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d052d-104">语法</span><span class="sxs-lookup"><span data-stu-id="d052d-104">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameKeyGenEx (  
    [in]  LPCWSTR   wszKeyContainer,  
    [in]  DWORD     dwFlags,  
    [in]  DWORD     dwKeySize,  
    [out] BYTE      **ppbKeyBlob,  
    [out] ULONG     *pcbKeyBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d052d-105">参数</span><span class="sxs-lookup"><span data-stu-id="d052d-105">Parameters</span></span>  
 `wszKeyContainer`  
 <span data-ttu-id="d052d-106">中请求的密钥容器名称。</span><span class="sxs-lookup"><span data-stu-id="d052d-106">[in] The requested key container name.</span></span> <span data-ttu-id="d052d-107">`wszKeyContainer`必须为非空字符串，或者为 null 以生成临时名称。</span><span class="sxs-lookup"><span data-stu-id="d052d-107">`wszKeyContainer` must either be a non-empty string or null to generate a temporary name.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="d052d-108">中一个值，该值指定是否保留注册的密钥。</span><span class="sxs-lookup"><span data-stu-id="d052d-108">[in] A value that specifies whether to leave the key registered.</span></span> <span data-ttu-id="d052d-109">支持以下值：</span><span class="sxs-lookup"><span data-stu-id="d052d-109">The following values are supported:</span></span>  
  
- <span data-ttu-id="d052d-110">0x00000000-在 `wszKeyContainer` 为 null 时用于生成临时密钥容器名称。</span><span class="sxs-lookup"><span data-stu-id="d052d-110">0x00000000 - Used when `wszKeyContainer` is null to generate a temporary key container name.</span></span>  
  
- <span data-ttu-id="d052d-111">0x00000001 （ `SN_LEAVE_KEY` ）-指定密钥应为 "已注册"。</span><span class="sxs-lookup"><span data-stu-id="d052d-111">0x00000001 (`SN_LEAVE_KEY`) - Specifies that the key should be left registered.</span></span>  
  
 `dwKeySize`  
 <span data-ttu-id="d052d-112">中请求的密钥大小，以位为单位。</span><span class="sxs-lookup"><span data-stu-id="d052d-112">[in] The requested size of the key, in bits.</span></span>  
  
 `ppbKeyBlob`  
 <span data-ttu-id="d052d-113">弄返回的公钥/私钥对。</span><span class="sxs-lookup"><span data-stu-id="d052d-113">[out] The returned public/private key pair.</span></span>  
  
 `pcbKeyBlob`  
 <span data-ttu-id="d052d-114">弄的大小（以字节为单位） `ppbKeyBlob` 。</span><span class="sxs-lookup"><span data-stu-id="d052d-114">[out] The size, in bytes, of `ppbKeyBlob`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d052d-115">返回值</span><span class="sxs-lookup"><span data-stu-id="d052d-115">Return Value</span></span>  
 <span data-ttu-id="d052d-116">`S_OK`如果该方法已成功完成，则为;否则，表示失败的 HRESULT 值（请参阅列表的[常见 HRESULT 值](/windows/win32/seccrypto/common-hresult-values)）。</span><span class="sxs-lookup"><span data-stu-id="d052d-116">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d052d-117">注解</span><span class="sxs-lookup"><span data-stu-id="d052d-117">Remarks</span></span>  
 <span data-ttu-id="d052d-118">.NET Framework 版本1.0 和1.1 需要 `dwKeySize` 1024 位才能使用强名称对程序集进行签名; 版本2.0 增加了对2048位密钥的支持。</span><span class="sxs-lookup"><span data-stu-id="d052d-118">The .NET Framework versions 1.0 and 1.1 require a `dwKeySize` of 1024 bits to sign an assembly with a strong name; version 2.0 adds supports for 2048-bit keys.</span></span>  
  
 <span data-ttu-id="d052d-119">检索到密钥后，应调用[ICLRStrongName：： StrongNameFreeBuffer](iclrstrongname-strongnamefreebuffer-method.md)方法来释放已分配的内存。</span><span class="sxs-lookup"><span data-stu-id="d052d-119">After the key is retrieved, you should call the [ICLRStrongName::StrongNameFreeBuffer](iclrstrongname-strongnamefreebuffer-method.md) method to release the allocated memory.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d052d-120">要求</span><span class="sxs-lookup"><span data-stu-id="d052d-120">Requirements</span></span>  
 <span data-ttu-id="d052d-121">**平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d052d-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d052d-122">**标头：** MetaHost</span><span class="sxs-lookup"><span data-stu-id="d052d-122">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="d052d-123">**库：** 作为资源包括在 Mscoree.dll 中</span><span class="sxs-lookup"><span data-stu-id="d052d-123">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d052d-124">**.NET Framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d052d-124">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d052d-125">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d052d-125">See also</span></span>

- [<span data-ttu-id="d052d-126">StrongNameKeyGen 方法</span><span class="sxs-lookup"><span data-stu-id="d052d-126">StrongNameKeyGen Method</span></span>](iclrstrongname-strongnamekeygen-method.md)
- [<span data-ttu-id="d052d-127">ICLRStrongName 接口</span><span class="sxs-lookup"><span data-stu-id="d052d-127">ICLRStrongName Interface</span></span>](iclrstrongname-interface.md)
