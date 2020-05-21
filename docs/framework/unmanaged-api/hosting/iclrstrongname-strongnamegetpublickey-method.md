---
title: ICLRStrongName::StrongNameGetPublicKey 方法
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameGetPublicKey
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameGetPublicKey
helpviewer_keywords:
- StrongNameGetPublicKey method, ICLRStrongName interface [.NET Framework hosting]
- ICLRStrongName::StrongNameGetPublicKey method [.NET Framework hosting]
ms.assetid: a31dcaa9-a404-4c1d-8cc7-081827c52935
topic_type:
- apiref
ms.openlocfilehash: 5a20bde64830617090c92afe5fae3a603cf9103b
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/21/2020
ms.locfileid: "83763120"
---
# <a name="iclrstrongnamestrongnamegetpublickey-method"></a><span data-ttu-id="98ed6-102">ICLRStrongName::StrongNameGetPublicKey 方法</span><span class="sxs-lookup"><span data-stu-id="98ed6-102">ICLRStrongName::StrongNameGetPublicKey Method</span></span>
<span data-ttu-id="98ed6-103">获取公钥/私钥对中的公钥。</span><span class="sxs-lookup"><span data-stu-id="98ed6-103">Gets the public key from a public/private key pair.</span></span> <span data-ttu-id="98ed6-104">密钥对可以作为加密服务提供程序（CSP）中的密钥容器名称提供，也可以作为字节的原始集合提供。</span><span class="sxs-lookup"><span data-stu-id="98ed6-104">The key pair can be supplied either as a key container name within a cryptographic service provider (CSP) or as a raw collection of bytes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="98ed6-105">语法</span><span class="sxs-lookup"><span data-stu-id="98ed6-105">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameGetPublicKey (
    [in]  LPCWSTR   szKeyContainer,  
    [in]  BYTE      *pbKeyBlob,  
    [in]  ULONG     cbKeyBlob,  
    [out] BYTE      **ppbPublicKeyBlob,  
    [out] ULONG     *pcbPublicKeyBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="98ed6-106">参数</span><span class="sxs-lookup"><span data-stu-id="98ed6-106">Parameters</span></span>  
 `szKeyContainer`  
 <span data-ttu-id="98ed6-107">中包含公钥/私钥对的密钥容器的名称。</span><span class="sxs-lookup"><span data-stu-id="98ed6-107">[in] The name of the key container that contains the public/private key pair.</span></span> <span data-ttu-id="98ed6-108">如果 `pbKeyBlob` 为 null，则 `szKeyContainer` 必须在 CSP 内指定有效容器。</span><span class="sxs-lookup"><span data-stu-id="98ed6-108">If `pbKeyBlob` is null, `szKeyContainer` must specify a valid container within the CSP.</span></span> <span data-ttu-id="98ed6-109">在这种情况下， [ICLRStrongName：： StrongNameGetPublicKey](iclrstrongname-strongnamegetpublickey-method.md)方法将从存储在容器中的密钥对中提取公钥。</span><span class="sxs-lookup"><span data-stu-id="98ed6-109">In this case, the [ICLRStrongName::StrongNameGetPublicKey](iclrstrongname-strongnamegetpublickey-method.md) method extracts the public key from the key pair stored in the container.</span></span>  
  
 <span data-ttu-id="98ed6-110">如果不为 `pbKeyBlob` null，则假定密钥对包含在关键的二进制大型对象（BLOB）中。</span><span class="sxs-lookup"><span data-stu-id="98ed6-110">If `pbKeyBlob` is not null, the key pair is assumed to be contained in the key binary large object (BLOB).</span></span>  
  
 <span data-ttu-id="98ed6-111">密钥必须是1024位 Rivest-Rivest-shamir-adleman-Rivest-shamir-adleman （RSA）签名密钥。</span><span class="sxs-lookup"><span data-stu-id="98ed6-111">The keys must be 1024-bit Rivest-Shamir-Adleman (RSA) signing keys.</span></span> <span data-ttu-id="98ed6-112">此时不支持其他类型的密钥。</span><span class="sxs-lookup"><span data-stu-id="98ed6-112">No other types of keys are supported at this time.</span></span>  
  
 `pbKeyBlob`  
 <span data-ttu-id="98ed6-113">中指向公钥/私钥对的指针。</span><span class="sxs-lookup"><span data-stu-id="98ed6-113">[in] A pointer to the public/private key pair.</span></span> <span data-ttu-id="98ed6-114">此对采用 Win32 函数创建的格式 `CryptExportKey` 。</span><span class="sxs-lookup"><span data-stu-id="98ed6-114">This pair is in the format created by the Win32 `CryptExportKey` function.</span></span> <span data-ttu-id="98ed6-115">如果 `pbKeyBlob` 为 null，则假定指定的密钥容器 `szKeyContainer` 包含密钥对。</span><span class="sxs-lookup"><span data-stu-id="98ed6-115">If `pbKeyBlob` is null, the key container specified by `szKeyContainer` is assumed to contain the key pair.</span></span>  
  
 `cbKeyBlob`  
 <span data-ttu-id="98ed6-116">中的大小（以字节为单位） `pbKeyBlob` 。</span><span class="sxs-lookup"><span data-stu-id="98ed6-116">[in] The size, in bytes, of `pbKeyBlob`.</span></span>  
  
 `ppbPublicKeyBlob`  
 <span data-ttu-id="98ed6-117">弄返回的公钥 BLOB。</span><span class="sxs-lookup"><span data-stu-id="98ed6-117">[out] The returned public key BLOB.</span></span> <span data-ttu-id="98ed6-118">`ppbPublicKeyBlob`参数由公共语言运行时分配并返回给调用方。</span><span class="sxs-lookup"><span data-stu-id="98ed6-118">The `ppbPublicKeyBlob` parameter is allocated by the common language runtime and returned to the caller.</span></span> <span data-ttu-id="98ed6-119">调用方必须使用[ICLRStrongName：： StrongNameFreeBuffer](iclrstrongname-strongnamefreebuffer-method.md)方法释放内存。</span><span class="sxs-lookup"><span data-stu-id="98ed6-119">The caller must free the memory by using the [ICLRStrongName::StrongNameFreeBuffer](iclrstrongname-strongnamefreebuffer-method.md) method.</span></span>  
  
 `pcbPublicKeyBlob`  
 <span data-ttu-id="98ed6-120">弄返回的公钥 BLOB 的大小。</span><span class="sxs-lookup"><span data-stu-id="98ed6-120">[out] The size of the returned public key BLOB.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="98ed6-121">返回值</span><span class="sxs-lookup"><span data-stu-id="98ed6-121">Return Value</span></span>  
 <span data-ttu-id="98ed6-122">`S_OK`如果该方法已成功完成，则为;否则，表示失败的 HRESULT 值（请参阅列表的[常见 HRESULT 值](/windows/win32/seccrypto/common-hresult-values)）。</span><span class="sxs-lookup"><span data-stu-id="98ed6-122">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="98ed6-123">注解</span><span class="sxs-lookup"><span data-stu-id="98ed6-123">Remarks</span></span>  
 <span data-ttu-id="98ed6-124">公钥包含在[PublicKeyBlob](../strong-naming/publickeyblob-structure.md)结构中。</span><span class="sxs-lookup"><span data-stu-id="98ed6-124">The public key is contained in a [PublicKeyBlob](../strong-naming/publickeyblob-structure.md) structure.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="98ed6-125">要求</span><span class="sxs-lookup"><span data-stu-id="98ed6-125">Requirements</span></span>  
 <span data-ttu-id="98ed6-126">**平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="98ed6-126">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="98ed6-127">**标头：** MetaHost</span><span class="sxs-lookup"><span data-stu-id="98ed6-127">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="98ed6-128">**库：** 作为资源包括在 Mscoree.dll 中</span><span class="sxs-lookup"><span data-stu-id="98ed6-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="98ed6-129">**.NET Framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="98ed6-129">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="98ed6-130">另请参阅</span><span class="sxs-lookup"><span data-stu-id="98ed6-130">See also</span></span>

- [<span data-ttu-id="98ed6-131">StrongNameTokenFromPublicKey 方法</span><span class="sxs-lookup"><span data-stu-id="98ed6-131">StrongNameTokenFromPublicKey Method</span></span>](iclrstrongname-strongnametokenfrompublickey-method.md)
- [<span data-ttu-id="98ed6-132">PublicKeyBlob 结构</span><span class="sxs-lookup"><span data-stu-id="98ed6-132">PublicKeyBlob Structure</span></span>](../strong-naming/publickeyblob-structure.md)
- [<span data-ttu-id="98ed6-133">ICLRStrongName 接口</span><span class="sxs-lookup"><span data-stu-id="98ed6-133">ICLRStrongName Interface</span></span>](iclrstrongname-interface.md)
