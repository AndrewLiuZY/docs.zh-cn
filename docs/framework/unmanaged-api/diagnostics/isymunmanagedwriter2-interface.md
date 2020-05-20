---
title: ISymUnmanagedWriter2 接口
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter2
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter2
helpviewer_keywords:
- ISymUnmanagedWriter2 interface [.NET Framework debugging]
ms.assetid: 8e78faa4-cf43-44fb-a91d-94d6df692a25
topic_type:
- apiref
ms.openlocfilehash: 1fe6055d930c6d30e947d6bc774d0520a9e175ae
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/19/2020
ms.locfileid: "83614677"
---
# <a name="isymunmanagedwriter2-interface"></a><span data-ttu-id="3753f-102">ISymUnmanagedWriter2 接口</span><span class="sxs-lookup"><span data-stu-id="3753f-102">ISymUnmanagedWriter2 Interface</span></span>
<span data-ttu-id="3753f-103">表示符号编写器，并提供定义文档、序列点、词法范围和变量的方法。</span><span class="sxs-lookup"><span data-stu-id="3753f-103">Represents a symbol writer, and provides methods to define documents, sequence points, lexical scopes, and variables.</span></span> <span data-ttu-id="3753f-104">此接口扩展[ISymUnmanagedWriter](isymunmanagedwriter-interface.md)接口。</span><span class="sxs-lookup"><span data-stu-id="3753f-104">This interface extends the [ISymUnmanagedWriter](isymunmanagedwriter-interface.md) interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="3753f-105">方法</span><span class="sxs-lookup"><span data-stu-id="3753f-105">Methods</span></span>  
  
|<span data-ttu-id="3753f-106">方法</span><span class="sxs-lookup"><span data-stu-id="3753f-106">Method</span></span>|<span data-ttu-id="3753f-107">说明</span><span class="sxs-lookup"><span data-stu-id="3753f-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="3753f-108">DefineConstant2 方法</span><span class="sxs-lookup"><span data-stu-id="3753f-108">DefineConstant2 Method</span></span>](isymunmanagedwriter2-defineconstant2-method.md)|<span data-ttu-id="3753f-109">定义常数值的名称。</span><span class="sxs-lookup"><span data-stu-id="3753f-109">Defines a name for a constant value.</span></span>|  
|[<span data-ttu-id="3753f-110">DefineGlobalVariable2 方法</span><span class="sxs-lookup"><span data-stu-id="3753f-110">DefineGlobalVariable2 Method</span></span>](isymunmanagedwriter2-defineglobalvariable2-method.md)|<span data-ttu-id="3753f-111">定义单个全局变量。</span><span class="sxs-lookup"><span data-stu-id="3753f-111">Defines a single global variable.</span></span>|  
|[<span data-ttu-id="3753f-112">DefineLocalVariable2 方法</span><span class="sxs-lookup"><span data-stu-id="3753f-112">DefineLocalVariable2 Method</span></span>](isymunmanagedwriter2-definelocalvariable2-method.md)|<span data-ttu-id="3753f-113">在当前词法范围内定义单个变量。</span><span class="sxs-lookup"><span data-stu-id="3753f-113">Defines a single variable in the current lexical scope.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="3753f-114">要求</span><span class="sxs-lookup"><span data-stu-id="3753f-114">Requirements</span></span>  
 <span data-ttu-id="3753f-115">**标头：** CorSym，CorSym</span><span class="sxs-lookup"><span data-stu-id="3753f-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3753f-116">另请参阅</span><span class="sxs-lookup"><span data-stu-id="3753f-116">See also</span></span>

- [<span data-ttu-id="3753f-117">诊断符号存储区接口</span><span class="sxs-lookup"><span data-stu-id="3753f-117">Diagnostics Symbol Store Interfaces</span></span>](diagnostics-symbol-store-interfaces.md)
- [<span data-ttu-id="3753f-118">ISymUnmanagedWriter 接口</span><span class="sxs-lookup"><span data-stu-id="3753f-118">ISymUnmanagedWriter Interface</span></span>](isymunmanagedwriter-interface.md)
- [<span data-ttu-id="3753f-119">ISymUnmanagedWriter3 接口</span><span class="sxs-lookup"><span data-stu-id="3753f-119">ISymUnmanagedWriter3 Interface</span></span>](isymunmanagedwriter3-interface.md)
