---
title: ISymUnmanagedWriter::DefineSequencePoints 方法
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.DefineSequencePoints
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::DefineSequencePoints
helpviewer_keywords:
- DefineSequencePoints method [.NET Framework debugging]
- ISymUnmanagedWriter::DefineSequencePoints method [.NET Framework debugging]
ms.assetid: 64202baf-be6b-40ba-8162-8cc6c0c9b8e1
topic_type:
- apiref
ms.openlocfilehash: 8889c412f414f38d1d18d33ec297e82fd052280d
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/19/2020
ms.locfileid: "83614794"
---
# <a name="isymunmanagedwriterdefinesequencepoints-method"></a>ISymUnmanagedWriter::DefineSequencePoints 方法
在当前方法内定义一组序列点。 每个起始行和起始列定义方法中语句的开头。 每个结束行和结束列定义方法中语句的末尾。 应按偏移量的递增顺序对数组进行排序。 始终从方法的开头开始度量偏移量（以字节为单位）。  
  
## <a name="syntax"></a>语法  
  
```cpp  
HRESULT DefineSequencePoints(  
    [in] ISymUnmanagedDocumentWriter*  document,  
    [in] ULONG32 spCount,  
    [in, size_is(spCount)] ULONG32     offsets[],  
    [in, size_is(spCount)] ULONG32     lines[],  
    [in, size_is(spCount)] ULONG32     columns[],  
    [in, size_is(spCount)] ULONG32     endLines[],  
    [in, size_is(spCount)] ULONG32     endColumns[]);  
```  
  
## <a name="parameters"></a>参数  
 `document`  
 中正在为其定义序列点的文档对象。  
  
 `spCount`  
 中， `ULONG32` 指示、、、 `offsets` `lines` `columns` `endLines` 和 `endColumns` 缓冲区的大小。  
  
 `offsets`  
 中从方法的开头测量的序列点的偏移量。  
  
 `lines`  
 中序列点的起始行号。  
  
 `columns`  
 中序列点的起始列号。  
  
 `endLines`  
 中序列点的结束行号。 该参数为可选参数。  
  
 `endColumns`  
 中序列点的结束列号。 该参数为可选参数。  
  
## <a name="return-value"></a>返回值  
 如果该方法成功，则 S_OK;否则，E_FAIL 或其他一些错误代码。  
  
## <a name="requirements"></a>要求  
 **标头：** CorSym，CorSym  
  
## <a name="see-also"></a>另请参阅

- [ISymUnmanagedWriter 接口](isymunmanagedwriter-interface.md)
