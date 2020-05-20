---
title: ISymUnmanagedWriter::SetSymAttribute 方法
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.SetSymAttribute
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::SetSymAttribute
helpviewer_keywords:
- SetSymAttribute method [.NET Framework debugging]
- ISymUnmanagedWriter::SetSymAttribute method [.NET Framework debugging]
ms.assetid: 64d9b80e-b883-4539-89c7-03573185a1eb
topic_type:
- apiref
ms.openlocfilehash: 39b0c065a324f2b3939467901739f995bc9abbad
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/19/2020
ms.locfileid: "83614755"
---
# <a name="isymunmanagedwritersetsymattribute-method"></a><span data-ttu-id="28624-102">ISymUnmanagedWriter::SetSymAttribute 方法</span><span class="sxs-lookup"><span data-stu-id="28624-102">ISymUnmanagedWriter::SetSymAttribute Method</span></span>
<span data-ttu-id="28624-103">基于名称定义自定义属性。</span><span class="sxs-lookup"><span data-stu-id="28624-103">Defines a custom attribute based upon its name.</span></span> <span data-ttu-id="28624-104">这些特性保存在符号存储区中，与元数据自定义特性不同。</span><span class="sxs-lookup"><span data-stu-id="28624-104">These attributes are held in the symbol store, unlike metadata custom attributes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="28624-105">语法</span><span class="sxs-lookup"><span data-stu-id="28624-105">Syntax</span></span>  
  
```cpp  
HRESULT SetSymAttribute(  
    [in] mdToken parent,  
    [in] const WCHAR *name,  
    [in] ULONG32 cData,  
    [in, size_is(cData)] unsigned char data[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="28624-106">参数</span><span class="sxs-lookup"><span data-stu-id="28624-106">Parameters</span></span>  
 `parent`  
 <span data-ttu-id="28624-107">中正在为其定义特性的元数据标记。</span><span class="sxs-lookup"><span data-stu-id="28624-107">[in] The metadata token for which the attribute is being defined.</span></span>  
  
 `name`  
 <span data-ttu-id="28624-108">中指向 `WCHAR` 包含特性名称的的指针。</span><span class="sxs-lookup"><span data-stu-id="28624-108">[in] A pointer to a `WCHAR` that contains the attribute name.</span></span>  
  
 `cData`  
 <span data-ttu-id="28624-109">中`ULONG32`指示数组大小的 `data` 。</span><span class="sxs-lookup"><span data-stu-id="28624-109">[in] A `ULONG32` that indicates the size of the `data` array.</span></span>  
  
 `data`  
 <span data-ttu-id="28624-110">中特性值。</span><span class="sxs-lookup"><span data-stu-id="28624-110">[in] The attribute value.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="28624-111">返回值</span><span class="sxs-lookup"><span data-stu-id="28624-111">Return Value</span></span>  
 <span data-ttu-id="28624-112">如果该方法成功，则 S_OK;否则，E_FAIL 或其他一些错误代码。</span><span class="sxs-lookup"><span data-stu-id="28624-112">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="28624-113">要求</span><span class="sxs-lookup"><span data-stu-id="28624-113">Requirements</span></span>  
 <span data-ttu-id="28624-114">**标头：** CorSym，CorSym</span><span class="sxs-lookup"><span data-stu-id="28624-114">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="28624-115">另请参阅</span><span class="sxs-lookup"><span data-stu-id="28624-115">See also</span></span>

- [<span data-ttu-id="28624-116">ISymUnmanagedWriter 接口</span><span class="sxs-lookup"><span data-stu-id="28624-116">ISymUnmanagedWriter Interface</span></span>](isymunmanagedwriter-interface.md)
