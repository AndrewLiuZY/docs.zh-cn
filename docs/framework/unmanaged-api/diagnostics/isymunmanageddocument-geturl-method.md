---
title: ISymUnmanagedDocument::GetURL 方法
ms.date: 03/30/2017
api_name:
- ISymUnmanagedDocument.GetURL
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedDocument::GetURL
helpviewer_keywords:
- GetURL method [.NET Framework debugging]
- ISymUnmanagedDocument::GetURL method [.NET Framework debugging]
ms.assetid: 60600178-c2b5-4cab-b3a5-f0f61acebaf1
topic_type:
- apiref
ms.openlocfilehash: 3685707f1983ffec413e9cea2df5034ac53f643a
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615587"
---
# <a name="isymunmanageddocumentgeturl-method"></a><span data-ttu-id="eb1e3-102">ISymUnmanagedDocument::GetURL 方法</span><span class="sxs-lookup"><span data-stu-id="eb1e3-102">ISymUnmanagedDocument::GetURL Method</span></span>
<span data-ttu-id="eb1e3-103">返回此文档的统一资源定位器（URL）。</span><span class="sxs-lookup"><span data-stu-id="eb1e3-103">Returns the uniform resource locator (URL) for this document.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eb1e3-104">语法</span><span class="sxs-lookup"><span data-stu-id="eb1e3-104">Syntax</span></span>  
  
```cpp  
HRESULT GetURL(  
    [in]  ULONG32  cchUrl,  
    [out] ULONG32  *pcchUrl,  
    [out, size_is(cchUrl), length_is(*pcchUrl)] WCHAR szUrl[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="eb1e3-105">参数</span><span class="sxs-lookup"><span data-stu-id="eb1e3-105">Parameters</span></span>  
 `cchUrl`  
 <span data-ttu-id="eb1e3-106">中缓冲区的大小（以字符为字符） `szURL` 。</span><span class="sxs-lookup"><span data-stu-id="eb1e3-106">[in] The size, in characters, of the `szURL` buffer.</span></span>  
  
 `pcchUrl`  
 <span data-ttu-id="eb1e3-107">弄指向一个变量的指针，该变量接收 URL 的大小，包括 null 终止。</span><span class="sxs-lookup"><span data-stu-id="eb1e3-107">[out] A pointer to a variable that receives the size of the URL, including the null termination.</span></span>  
  
 `szUrl`  
 <span data-ttu-id="eb1e3-108">弄包含 URL 的缓冲区。</span><span class="sxs-lookup"><span data-stu-id="eb1e3-108">[out] The buffer containing the URL.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="eb1e3-109">返回值</span><span class="sxs-lookup"><span data-stu-id="eb1e3-109">Return Value</span></span>  
 <span data-ttu-id="eb1e3-110">如果该方法成功，则 S_OK;否则为错误代码。</span><span class="sxs-lookup"><span data-stu-id="eb1e3-110">S_OK if the method succeeds; otherwise, an error code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eb1e3-111">另请参阅</span><span class="sxs-lookup"><span data-stu-id="eb1e3-111">See also</span></span>

- [<span data-ttu-id="eb1e3-112">ISymUnmanagedDocument 接口</span><span class="sxs-lookup"><span data-stu-id="eb1e3-112">ISymUnmanagedDocument Interface</span></span>](isymunmanageddocument-interface.md)
