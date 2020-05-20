---
title: ISymUnmanagedWriter::SetScopeRange 方法
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.SetScopeRange
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::SetScopeRange
helpviewer_keywords:
- SetScopeRange method [.NET Framework debugging]
- ISymUnmanagedWriter::SetScopeRange method [.NET Framework debugging]
ms.assetid: d4d98676-444b-46ca-bfe6-0d827385cd22
topic_type:
- apiref
ms.openlocfilehash: b57bb549278f62cdce6ed5deaaa62f154ec919b5
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/19/2020
ms.locfileid: "83609360"
---
# <a name="isymunmanagedwritersetscoperange-method"></a><span data-ttu-id="82804-102">ISymUnmanagedWriter::SetScopeRange 方法</span><span class="sxs-lookup"><span data-stu-id="82804-102">ISymUnmanagedWriter::SetScopeRange Method</span></span>
<span data-ttu-id="82804-103">定义指定词法范围的偏移量范围。</span><span class="sxs-lookup"><span data-stu-id="82804-103">Defines the offset range for the specified lexical scope.</span></span> <span data-ttu-id="82804-104">范围将成为新的当前范围，并推送到作用域的堆栈上。</span><span class="sxs-lookup"><span data-stu-id="82804-104">The scope becomes the new current scope and is pushed onto a stack of scopes.</span></span> <span data-ttu-id="82804-105">范围必须构成层次结构。</span><span class="sxs-lookup"><span data-stu-id="82804-105">Scopes must form a hierarchy.</span></span> <span data-ttu-id="82804-106">同级不允许重叠。</span><span class="sxs-lookup"><span data-stu-id="82804-106">Siblings are not allowed to overlap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="82804-107">语法</span><span class="sxs-lookup"><span data-stu-id="82804-107">Syntax</span></span>  
  
```cpp  
HRESULT OpenScope(  
    [in] ULONG32  scopeID,  
    [in] ULONG32  startOffset,  
    [in] ULONG32  endOffset);  
```  
  
## <a name="parameters"></a><span data-ttu-id="82804-108">参数</span><span class="sxs-lookup"><span data-stu-id="82804-108">Parameters</span></span>  
 `scopeId`  
 <span data-ttu-id="82804-109">中作用域的作用域标识符。</span><span class="sxs-lookup"><span data-stu-id="82804-109">[in] The scope identifier for the scope.</span></span>  
  
 `startOffset`  
 <span data-ttu-id="82804-110">中词法范围中从该方法的开头开始的第一个指令的偏移量（以字节为单位）。</span><span class="sxs-lookup"><span data-stu-id="82804-110">[in] The offset, in bytes, of the first instruction in the lexical scope from the beginning of the method.</span></span>  
  
 `endOffset`  
 <span data-ttu-id="82804-111">中词法范围中从该方法的开头开始的最后一个指令的偏移量（以字节为单位）。</span><span class="sxs-lookup"><span data-stu-id="82804-111">[in] The offset, in bytes, of the last instruction in the lexical scope from the beginning of the method.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="82804-112">返回值</span><span class="sxs-lookup"><span data-stu-id="82804-112">Return Value</span></span>  
 <span data-ttu-id="82804-113">如果该方法成功，则 S_OK;否则，E_FAIL 或其他一些错误代码。</span><span class="sxs-lookup"><span data-stu-id="82804-113">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="82804-114">备注</span><span class="sxs-lookup"><span data-stu-id="82804-114">Remarks</span></span>  
 <span data-ttu-id="82804-115">[ISymUnmanagedWriter：： OpenScope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openscope-method.md)返回一个不透明的范围标识符，该标识符可与一起用于 `ISymUnmanagedWriter::SetScopeRange` 定义范围的起始和结束偏移量。</span><span class="sxs-lookup"><span data-stu-id="82804-115">[ISymUnmanagedWriter::OpenScope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openscope-method.md) returns an opaque scope identifier that can be used with `ISymUnmanagedWriter::SetScopeRange` to define a scope's starting and ending offset at a later time.</span></span> <span data-ttu-id="82804-116">在这种情况下，将忽略传递到 `ISymUnmanagedWriter::OpenScope` 和[ISymUnmanagedWriter：： CloseScope](isymunmanagedwriter-closescope-method.md)的偏移量。</span><span class="sxs-lookup"><span data-stu-id="82804-116">In this case, the offsets passed to `ISymUnmanagedWriter::OpenScope` and [ISymUnmanagedWriter::CloseScope](isymunmanagedwriter-closescope-method.md) are ignored.</span></span> <span data-ttu-id="82804-117">范围标识符只在当前方法中有效。</span><span class="sxs-lookup"><span data-stu-id="82804-117">Scope identifiers are only valid in the current method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="82804-118">要求</span><span class="sxs-lookup"><span data-stu-id="82804-118">Requirements</span></span>  
 <span data-ttu-id="82804-119">**标头：** CorSym，CorSym</span><span class="sxs-lookup"><span data-stu-id="82804-119">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="82804-120">另请参阅</span><span class="sxs-lookup"><span data-stu-id="82804-120">See also</span></span>

- [<span data-ttu-id="82804-121">ISymUnmanagedWriter 接口</span><span class="sxs-lookup"><span data-stu-id="82804-121">ISymUnmanagedWriter Interface</span></span>](isymunmanagedwriter-interface.md)
