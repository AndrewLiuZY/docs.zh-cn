---
title: 如何：对区域使用命中测试
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hit tests [Windows Forms], using regions
- regions [Windows Forms], hit testing
ms.assetid: 3a4c07cb-a40a-4d14-ad35-008f531910a8
ms.openlocfilehash: 136f15f1364fb2aed791b4a61d0f11411b055967
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "61778867"
---
# <a name="how-to-use-hit-testing-with-a-region"></a>如何：对区域使用命中测试
命中测试的目的是确定光标是否位于给定的对象，例如图标或按钮。  
  
## <a name="example"></a>示例  
 下面的示例通过两个矩形区域的并集创建 plus 形区域。 假设变量`point`保存最新的单击的位置。 代码检查是否`point`plus 形区域中。 如果点在区域 （命中），该区域是使用不透明红色画笔填充。 否则，该区域是用半透明的红色画笔填充。  
  
 [!code-csharp[System.Drawing.MiscLegacyTopics#31](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.MiscLegacyTopics#31](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#31)]  
  
## <a name="compiling-the-code"></a>编译代码  
 前面的示例专用于 Windows 窗体，并且它需要<xref:System.Windows.Forms.PaintEventArgs> `e`，这是一个参数的<xref:System.Windows.Forms.PaintEventHandler>。  
  
## <a name="see-also"></a>请参阅

- <xref:System.Drawing.Region>
- [GDI+ 中的区域](regions-in-gdi.md)
- [如何：对区域使用剪辑](how-to-use-clipping-with-a-region.md)
