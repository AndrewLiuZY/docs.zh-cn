---
title: 如何：显示可用的串行端口
ms.date: 07/20/2015
helpviewer_keywords:
- serial ports, availability
- My.Computer.Ports.SerialPortNames property
- My.Computer.Ports object
- ports, serial port availability
ms.assetid: eaf2ee5a-8103-4e10-a205-ed1d4db120ba
ms.openlocfilehash: c7e5f797c1d098a3b2d01745b949ed50375ea7e8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/15/2020
ms.locfileid: "74345577"
---
# <a name="how-to-show-available-serial-ports-in-visual-basic"></a><span data-ttu-id="89ebf-102">如何：在 Visual Basic 中显示可用的串行端口</span><span class="sxs-lookup"><span data-stu-id="89ebf-102">How to: Show Available Serial Ports in Visual Basic</span></span>

<span data-ttu-id="89ebf-103">本主题介绍在 Visual Basic 中如何使用 `My.Computer.Ports` 显示计算机的可用串行端口。</span><span class="sxs-lookup"><span data-stu-id="89ebf-103">This topic describes how to use `My.Computer.Ports` to show the available serial ports of the computer in Visual Basic.</span></span>  
  
 <span data-ttu-id="89ebf-104">若要使用户可以选择要使用的端口，请将串行端口的名称置于 <xref:System.Windows.Forms.ListBox> 控件中。</span><span class="sxs-lookup"><span data-stu-id="89ebf-104">To allow a user to select which port to use, the names of the serial ports are placed in a <xref:System.Windows.Forms.ListBox> control.</span></span>  
  
## <a name="example"></a><span data-ttu-id="89ebf-105">示例</span><span class="sxs-lookup"><span data-stu-id="89ebf-105">Example</span></span>  

 <span data-ttu-id="89ebf-106">此示例循环访问 `My.Computer.Ports.SerialPortNames` 属性返回的所有字符串。</span><span class="sxs-lookup"><span data-stu-id="89ebf-106">This example loops over all the strings that the `My.Computer.Ports.SerialPortNames` property returns.</span></span> <span data-ttu-id="89ebf-107">这些字符串是计算机上的可用串行端口的名称。</span><span class="sxs-lookup"><span data-stu-id="89ebf-107">These strings are the names of the available serial ports on the computer.</span></span>  
  
 <span data-ttu-id="89ebf-108">通常，用户从可用端口列表中选择应用程序应使用的串行端口。</span><span class="sxs-lookup"><span data-stu-id="89ebf-108">Typically, a user selects which serial port the application should use from the list of available ports.</span></span> <span data-ttu-id="89ebf-109">在此示例中，串行端口名称存储在 <xref:System.Windows.Forms.ListBox> 控件中。</span><span class="sxs-lookup"><span data-stu-id="89ebf-109">In this example, the serial port names are stored in a <xref:System.Windows.Forms.ListBox> control.</span></span> <span data-ttu-id="89ebf-110">有关详细信息，请参阅 [ListBox 控件](../../../../framework/winforms/controls/listbox-control-windows-forms.md)。</span><span class="sxs-lookup"><span data-stu-id="89ebf-110">For more information, see [ListBox Control](../../../../framework/winforms/controls/listbox-control-windows-forms.md).</span></span>  
  
 [!code-vb[VbVbalrMyComputer#45](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#45)]  
  
 <span data-ttu-id="89ebf-111">此代码示例也可作为 IntelliSense 代码片段。</span><span class="sxs-lookup"><span data-stu-id="89ebf-111">This code example is also available as an IntelliSense code snippet.</span></span> <span data-ttu-id="89ebf-112">它位于代码片段选取器的“连接和网络”中。 </span><span class="sxs-lookup"><span data-stu-id="89ebf-112">In the code snippet picker, it is located in **Connectivity and Networking**.</span></span> <span data-ttu-id="89ebf-113">有关详细信息，请参阅[代码片段](/visualstudio/ide/code-snippets)。</span><span class="sxs-lookup"><span data-stu-id="89ebf-113">For more information, see [Code Snippets](/visualstudio/ide/code-snippets).</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="89ebf-114">编译代码</span><span class="sxs-lookup"><span data-stu-id="89ebf-114">Compiling the Code</span></span>  

 <span data-ttu-id="89ebf-115">此示例需要：</span><span class="sxs-lookup"><span data-stu-id="89ebf-115">This example requires:</span></span>  
  
- <span data-ttu-id="89ebf-116">对 System.Windows.Forms.dll 的项目引用。</span><span class="sxs-lookup"><span data-stu-id="89ebf-116">A project reference to System.Windows.Forms.dll.</span></span>  
  
- <span data-ttu-id="89ebf-117">对 <xref:System.Windows.Forms> 命名空间成员的访问权限。</span><span class="sxs-lookup"><span data-stu-id="89ebf-117">Access to the members of the <xref:System.Windows.Forms> namespace.</span></span> <span data-ttu-id="89ebf-118">如果未在代码中完全限定成员名称，则添加 `Imports` 语句。</span><span class="sxs-lookup"><span data-stu-id="89ebf-118">Add an `Imports` statement if you are not fully qualifying member names in your code.</span></span> <span data-ttu-id="89ebf-119">有关详细信息，请参阅 [Imports 语句（.NET 命名空间和类型）](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)。</span><span class="sxs-lookup"><span data-stu-id="89ebf-119">For more information, see [Imports Statement (.NET Namespace and Type)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).</span></span>  
  
- <span data-ttu-id="89ebf-120">窗体具有名为 `ListBox1` 的 <xref:System.Windows.Forms.ListBox> 控件。</span><span class="sxs-lookup"><span data-stu-id="89ebf-120">That your form have a <xref:System.Windows.Forms.ListBox> control named `ListBox1`.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="89ebf-121">可靠编程</span><span class="sxs-lookup"><span data-stu-id="89ebf-121">Robust Programming</span></span>  

 <span data-ttu-id="89ebf-122">不必使用 <xref:System.Windows.Forms.ListBox> 控件显示可用串行端口名称。</span><span class="sxs-lookup"><span data-stu-id="89ebf-122">You do not have to use the <xref:System.Windows.Forms.ListBox> control to display the available serial port names.</span></span> <span data-ttu-id="89ebf-123">相反，可以使用 <xref:System.Windows.Forms.ComboBox> 或其他控件。</span><span class="sxs-lookup"><span data-stu-id="89ebf-123">Instead, you can use a <xref:System.Windows.Forms.ComboBox> or other control.</span></span> <span data-ttu-id="89ebf-124">如果应用程序不需要来自用户的响应，则可以使用 <xref:System.Windows.Forms.TextBox> 控件显示信息。</span><span class="sxs-lookup"><span data-stu-id="89ebf-124">If the application does not need a response from the user, you can use a <xref:System.Windows.Forms.TextBox> control to display the information.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="89ebf-125">在 Windows 98 上运行时，`My.Computer.Ports.SerialPortNames` 返回的端口名称可能不正确。</span><span class="sxs-lookup"><span data-stu-id="89ebf-125">The port names returned by `My.Computer.Ports.SerialPortNames` may be incorrect when run on Windows 98.</span></span> <span data-ttu-id="89ebf-126">若要防止应用程序错误，请在使用端口名称打开端口时使用异常处理（如 `Try...Catch...Finally` 语句或 `Using` 语句）。</span><span class="sxs-lookup"><span data-stu-id="89ebf-126">To prevent application errors, use exception handling, such as the `Try...Catch...Finally` statement or the `Using` statement, when using the port names to open ports.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="89ebf-127">另请参阅</span><span class="sxs-lookup"><span data-stu-id="89ebf-127">See also</span></span>

- <xref:Microsoft.VisualBasic.Devices.Ports>
- [<span data-ttu-id="89ebf-128">如何：使用连接到串行端口的调制解调器拨号</span><span class="sxs-lookup"><span data-stu-id="89ebf-128">How to: Dial Modems Attached to Serial Ports</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-dial-modems-attached-to-serial-ports.md)
- [<span data-ttu-id="89ebf-129">如何：将字符串发送到串行端口</span><span class="sxs-lookup"><span data-stu-id="89ebf-129">How to: Send Strings to Serial Ports</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-send-strings-to-serial-ports.md)
- [<span data-ttu-id="89ebf-130">如何：从串行端口接收字符串</span><span class="sxs-lookup"><span data-stu-id="89ebf-130">How to: Receive Strings From Serial Ports</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-receive-strings-from-serial-ports.md)
