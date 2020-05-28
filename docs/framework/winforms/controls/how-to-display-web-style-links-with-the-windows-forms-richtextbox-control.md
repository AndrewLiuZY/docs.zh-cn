---
title: 用 RichTextBox 控件显示 Web 样式链接
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- text boxes [Windows Forms], displaying Web links
- examples [Windows Forms], text boxes
- RichTextBox control [Windows Forms], linking to Web pages
ms.assetid: 95089a37-a202-4f7a-94ee-6ee312908851
ms.openlocfilehash: 06ed304e566bb437a2353dd330d7de5328f2a729
ms.sourcegitcommit: ee5b798427f81237a3c23d1fd81fff7fdc21e8d3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/28/2020
ms.locfileid: "84144820"
---
# <a name="how-to-display-web-style-links-with-the-windows-forms-richtextbox-control"></a><span data-ttu-id="96483-102">如何：使用 Windows 窗体 RichTextBox 控件显示 Web 样式的链接</span><span class="sxs-lookup"><span data-stu-id="96483-102">How to: Display Web-Style Links with the Windows Forms RichTextBox Control</span></span>

<span data-ttu-id="96483-103">Windows 窗体 <xref:System.Windows.Forms.RichTextBox> 控件可将 Web 链接显示为彩色和带下划线。</span><span class="sxs-lookup"><span data-stu-id="96483-103">The Windows Forms <xref:System.Windows.Forms.RichTextBox> control can display Web links as colored and underlined.</span></span> <span data-ttu-id="96483-104">您可以编写代码，以在单击链接时打开显示链接文本中所指定网站的浏览器窗口。</span><span class="sxs-lookup"><span data-stu-id="96483-104">You can write code that opens a browser window showing the Web site specified in the link text when the link is clicked.</span></span>

### <a name="to-link-to-a-web-page-with-the-richtextbox-control"></a><span data-ttu-id="96483-105">使用 RichTextBox 控件链接到网页</span><span class="sxs-lookup"><span data-stu-id="96483-105">To link to a Web page with the RichTextBox control</span></span>

1. <span data-ttu-id="96483-106">将 <xref:System.Windows.Forms.RichTextBox.Text%2A> 属性设置为包含有效 URL 的字符串（例如 " https://www.microsoft.com/ "）。</span><span class="sxs-lookup"><span data-stu-id="96483-106">Set the <xref:System.Windows.Forms.RichTextBox.Text%2A> property to a string that includes a valid URL (for example, "https://www.microsoft.com/").</span></span>

2. <span data-ttu-id="96483-107">请确保将 <xref:System.Windows.Forms.RichTextBox.DetectUrls%2A> 属性设置为 `true` （默认值）。</span><span class="sxs-lookup"><span data-stu-id="96483-107">Make sure the <xref:System.Windows.Forms.RichTextBox.DetectUrls%2A> property is set to `true` (the default).</span></span>

3. <span data-ttu-id="96483-108">创建对象的新全局实例 <xref:System.Diagnostics.Process> 。</span><span class="sxs-lookup"><span data-stu-id="96483-108">Create a new global instance of the <xref:System.Diagnostics.Process> object.</span></span>

4. <span data-ttu-id="96483-109">为 <xref:System.Windows.Forms.RichTextBox.LinkClicked> 发送浏览器所需文本的事件编写事件处理程序。</span><span class="sxs-lookup"><span data-stu-id="96483-109">Write an event handler for the <xref:System.Windows.Forms.RichTextBox.LinkClicked> event that sends the browser the desired text.</span></span>

    <span data-ttu-id="96483-110">在下面的示例中， <xref:System.Windows.Forms.RichTextBox.LinkClicked> 事件会将 Internet Explorer 的一个实例打开到在控件的属性中指定的 URL <xref:System.Windows.Forms.RichTextBox.Text%2A> <xref:System.Windows.Forms.RichTextBox> 。</span><span class="sxs-lookup"><span data-stu-id="96483-110">In the example below, the <xref:System.Windows.Forms.RichTextBox.LinkClicked> event opens an instance of Internet Explorer to the URL specified in the <xref:System.Windows.Forms.RichTextBox.Text%2A> property of the <xref:System.Windows.Forms.RichTextBox> control.</span></span> <span data-ttu-id="96483-111">此示例假设窗体具有一个 <xref:System.Windows.Forms.RichTextBox> 控件。</span><span class="sxs-lookup"><span data-stu-id="96483-111">This example assumes a form with a <xref:System.Windows.Forms.RichTextBox> control.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="96483-112">在调用 <xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType> 方法 <xref:System.Security.SecurityException> 时，如果在部分信任上下文中运行代码，则会遇到异常，因为权限不足。</span><span class="sxs-lookup"><span data-stu-id="96483-112">In calling the <xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType> method, you will encounter a <xref:System.Security.SecurityException> exception if you are running the code in a partial-trust context because of insufficient privileges.</span></span> <span data-ttu-id="96483-113">有关详细信息，请参阅 [Code Access Security Basics](../../misc/code-access-security-basics.md)。</span><span class="sxs-lookup"><span data-stu-id="96483-113">For more information, see [Code Access Security Basics](../../misc/code-access-security-basics.md).</span></span>

    ```vb
    Public p As New System.Diagnostics.Process
    Private Sub RichTextBox1_LinkClicked _
       (ByVal sender As Object, ByVal e As _
       System.Windows.Forms.LinkClickedEventArgs) _
       Handles RichTextBox1.LinkClicked
          ' Call Process.Start method to open a browser
          ' with link text as URL.
          p = System.Diagnostics.Process.Start("IExplore.exe", e.LinkText)
    End Sub
    ```

    ```csharp
    public System.Diagnostics.Process p = new System.Diagnostics.Process();

    private void richTextBox1_LinkClicked(object sender,
    System.Windows.Forms.LinkClickedEventArgs e)
    {
       // Call Process.Start method to open a browser
       // with link text as URL.
       p = System.Diagnostics.Process.Start("IExplore.exe", e.LinkText);
    }
    ```

    ```cpp
    public:
       System::Diagnostics::Process ^ p;

    private:
       void richTextBox1_LinkClicked(System::Object ^  sender,
          System::Windows::Forms::LinkClickedEventArgs ^  e)
       {
          // Call Process.Start method to open a browser
          // with link text as URL.
          p = System::Diagnostics::Process::Start("IExplore.exe",
             e->LinkText);
       }
    ```

    <span data-ttu-id="96483-114">（Visual C++）若要执行此操作 `p` ，必须在窗体的构造函数中包括以下语句，以便进行初始化：</span><span class="sxs-lookup"><span data-stu-id="96483-114">(Visual C++) You must initialize process `p`, which you can do by including the following statement in the constructor of your form:</span></span>

    ```cpp
    p = gcnew System::Diagnostics::Process();
    ```

    <span data-ttu-id="96483-115">（Visual c #、Visual C++）将以下代码放在窗体的构造函数中以注册事件处理程序。</span><span class="sxs-lookup"><span data-stu-id="96483-115">(Visual C#, Visual C++) Place the following code in the form's constructor to register the event handler.</span></span>

    ```csharp
    this.richTextBox1.LinkClicked += new
       System.Windows.Forms.LinkClickedEventHandler
       (this.richTextBox1_LinkClicked);
    ```

    ```cpp
    this->richTextBox1->LinkClicked += gcnew
       System::Windows::Forms::LinkClickedEventHandler
       (this, &Form1::richTextBox1_LinkClicked);
    ```

    <span data-ttu-id="96483-116">完成操作后，立即停止创建的过程非常重要。</span><span class="sxs-lookup"><span data-stu-id="96483-116">It is important to immediately stop the process you have created once you have finished working with it.</span></span> <span data-ttu-id="96483-117">参考以上所示的代码，停止此过程的代码可能如下所示：</span><span class="sxs-lookup"><span data-stu-id="96483-117">Referring to the code presented above, your code to stop the process might look like this:</span></span>

    ```vb
    Public Sub StopWebProcess()
       p.Kill()
    End Sub
    ```

    ```csharp
    public void StopWebProcess()
    {
       p.Kill();
    }
    ```

    ```cpp
    public: void StopWebProcess()
    {
       p->Kill();
    }
    ```

## <a name="see-also"></a><span data-ttu-id="96483-118">另请参阅</span><span class="sxs-lookup"><span data-stu-id="96483-118">See also</span></span>

- <xref:System.Windows.Forms.RichTextBox.DetectUrls%2A>
- <xref:System.Windows.Forms.RichTextBox.LinkClicked>
- <xref:System.Windows.Forms.RichTextBox>
- [<span data-ttu-id="96483-119">RichTextBox 控件</span><span class="sxs-lookup"><span data-stu-id="96483-119">RichTextBox Control</span></span>](richtextbox-control-windows-forms.md)
- [<span data-ttu-id="96483-120">在 Windows 窗体上使用的控件</span><span class="sxs-lookup"><span data-stu-id="96483-120">Controls to Use on Windows Forms</span></span>](controls-to-use-on-windows-forms.md)
