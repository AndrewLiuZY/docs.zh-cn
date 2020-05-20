---
title: ISymUnmanagedSymbolSearchInfo::GetHRESULT 方法
ms.date: 03/30/2017
api_name:
- ISymUnmanagedSymbolSearchInfo.GetHRESULT
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedSymbolSearchInfo::GetHRESULT
helpviewer_keywords:
- ISymUnmanagedSymbolSearchInfo::GetHRESULT method [.NET Framework debugging]
- GetHRESULT method [.NET Framework debugging]
ms.assetid: 6999dc3d-65d7-4bf6-bb0a-6efc0fc72588
topic_type:
- apiref
ms.openlocfilehash: 9dcd8282adf200932e86c950bee0b073780ce02d
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615301"
---
# <a name="isymunmanagedsymbolsearchinfogethresult-method"></a><span data-ttu-id="2caa0-102">ISymUnmanagedSymbolSearchInfo::GetHRESULT 方法</span><span class="sxs-lookup"><span data-stu-id="2caa0-102">ISymUnmanagedSymbolSearchInfo::GetHRESULT Method</span></span>
<span data-ttu-id="2caa0-103">获取 HRESULT。</span><span class="sxs-lookup"><span data-stu-id="2caa0-103">Gets the HRESULT.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2caa0-104">语法</span><span class="sxs-lookup"><span data-stu-id="2caa0-104">Syntax</span></span>  
  
```cpp  
HRESULT GetHRESULT(  
    [out] HRESULT *phr);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2caa0-105">参数</span><span class="sxs-lookup"><span data-stu-id="2caa0-105">Parameters</span></span>  
 `phr`  
 <span data-ttu-id="2caa0-106">弄指向 HRESULT 的指针。</span><span class="sxs-lookup"><span data-stu-id="2caa0-106">[out] A pointer to the HRESULT.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2caa0-107">返回值</span><span class="sxs-lookup"><span data-stu-id="2caa0-107">Return Value</span></span>  
 <span data-ttu-id="2caa0-108">如果该方法成功，则 S_OK;否则，E_FAIL 或其他一些错误代码。</span><span class="sxs-lookup"><span data-stu-id="2caa0-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2caa0-109">要求</span><span class="sxs-lookup"><span data-stu-id="2caa0-109">Requirements</span></span>  
 <span data-ttu-id="2caa0-110">**标头：** CorSym，CorSym</span><span class="sxs-lookup"><span data-stu-id="2caa0-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2caa0-111">另请参阅</span><span class="sxs-lookup"><span data-stu-id="2caa0-111">See also</span></span>

- [<span data-ttu-id="2caa0-112">ISymUnmanagedSymbolSearchInfo 接口</span><span class="sxs-lookup"><span data-stu-id="2caa0-112">ISymUnmanagedSymbolSearchInfo Interface</span></span>](isymunmanagedsymbolsearchinfo-interface.md)
