---
title: INotifySink2::OnSyncCallOut 方法
ms.date: 03/30/2017
api_name:
- INotifySink2.OnSyncCallOut
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- INotifySink2::OnSyncCallOut
helpviewer_keywords:
- INotifySink2::OnSyncCallOut method [.NET Framework debugging]
- OnSyncCallOut method [.NET Framework debugging]
ms.assetid: 97f15656-8677-4079-8553-a1d8603355d6
topic_type:
- apiref
ms.openlocfilehash: ce0e192a9d7d5abf56a55f844cf886c386f1c563
ms.sourcegitcommit: 7b1497c1927cb449cefd313bc5126ae37df30746
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/16/2020
ms.locfileid: "83441989"
---
# <a name="inotifysink2onsynccallout-method"></a><span data-ttu-id="f91d7-102">INotifySink2::OnSyncCallOut 方法</span><span class="sxs-lookup"><span data-stu-id="f91d7-102">INotifySink2::OnSyncCallOut Method</span></span>
<span data-ttu-id="f91d7-103">在调用时调用。</span><span class="sxs-lookup"><span data-stu-id="f91d7-103">Gets invoked when a call is out.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f91d7-104">语法</span><span class="sxs-lookup"><span data-stu-id="f91d7-104">Syntax</span></span>  
  
```cpp  
HRESULT OnSyncCallOut  
(  
    [in]  CALL_ID  in_CallID,  
    [out, size_is(, *out_pBufferSize)] BYTE**  out_ppBuffer,  
    [out] DWORD*   out_pBufferSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f91d7-105">参数</span><span class="sxs-lookup"><span data-stu-id="f91d7-105">Parameters</span></span>  
 `in_CallID`  
 <span data-ttu-id="f91d7-106">中传出的调用的 ID。请参阅[CALL_ID 结构](call-id-structure.md)。</span><span class="sxs-lookup"><span data-stu-id="f91d7-106">[in] ID of the call that is out. See [CALL_ID Structure](call-id-structure.md).</span></span>  
  
 `out_ppBuffer`  
 <span data-ttu-id="f91d7-107">弄调用缓冲区。</span><span class="sxs-lookup"><span data-stu-id="f91d7-107">[out] Call buffer.</span></span>  
  
 `out_pBufferSize`  
 <span data-ttu-id="f91d7-108">弄调用缓冲区的大小（以字节为单位）。</span><span class="sxs-lookup"><span data-stu-id="f91d7-108">[out] Size of the call buffer, in bytes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f91d7-109">返回值</span><span class="sxs-lookup"><span data-stu-id="f91d7-109">Return Value</span></span>  
 <span data-ttu-id="f91d7-110">如果方法成功，则 S_OK。</span><span class="sxs-lookup"><span data-stu-id="f91d7-110">S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f91d7-111">要求</span><span class="sxs-lookup"><span data-stu-id="f91d7-111">Requirements</span></span>  
 <span data-ttu-id="f91d7-112">**标头：** ProtocolNotify2 .idl</span><span class="sxs-lookup"><span data-stu-id="f91d7-112">**Header:** ProtocolNotify2.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f91d7-113">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f91d7-113">See also</span></span>

- [<span data-ttu-id="f91d7-114">INotifySink2 接口</span><span class="sxs-lookup"><span data-stu-id="f91d7-114">INotifySink2 Interface</span></span>](inotifysink2-interface.md)
- [<span data-ttu-id="f91d7-115">INotifySource2 接口</span><span class="sxs-lookup"><span data-stu-id="f91d7-115">INotifySource2 Interface</span></span>](inotifysource2-interface.md)
- [<span data-ttu-id="f91d7-116">INotifyConnection2 接口</span><span class="sxs-lookup"><span data-stu-id="f91d7-116">INotifyConnection2 Interface</span></span>](inotifyconnection2-interface.md)
