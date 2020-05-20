---
title: 创建 Internet 请求
ms.date: 03/30/2017
helpviewer_keywords:
- WebRequest class, sending and receiving data
- Networking
- HttpWebResponse class, sending and receiving data
- requesting data from Internet, creating requests
- Network Resources
- Internet, requesting data
- data requests, creating requests
ms.assetid: faab683e-3f1e-4eee-b5e9-59f7245033d5
ms.openlocfilehash: 80e3a6bd199691df9391e88d5a64fab5df2a08a1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/15/2020
ms.locfileid: "71048623"
---
# <a name="creating-internet-requests"></a><span data-ttu-id="f6c6e-102">创建 Internet 请求</span><span class="sxs-lookup"><span data-stu-id="f6c6e-102">Creating Internet Requests</span></span>
<span data-ttu-id="f6c6e-103">应用程序通过 <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> 方法创建 <xref:System.Net.WebRequest> 实例。</span><span class="sxs-lookup"><span data-stu-id="f6c6e-103">Applications create <xref:System.Net.WebRequest> instances through the <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="f6c6e-104">这是一种基于传递给它的 URI 方案创建从 WebRequest 派生的类的静态方法  。</span><span class="sxs-lookup"><span data-stu-id="f6c6e-104">This is a static method that creates a class derived from **WebRequest** based on the URI scheme passed to it.</span></span>  
  
## <a name="web-file-and-ftp-requests"></a><span data-ttu-id="f6c6e-105">Web、文件和 FTP 请求</span><span class="sxs-lookup"><span data-stu-id="f6c6e-105">Web, File and FTP Requests</span></span>  
 <span data-ttu-id="f6c6e-106">.NET Framework 提供从 WebRequest 派生的 <xref:System.Net.HttpWebRequest> 类，用以处理 HTTP 和 HTTPS 请求  。</span><span class="sxs-lookup"><span data-stu-id="f6c6e-106">The .NET Framework provides the <xref:System.Net.HttpWebRequest> class, which is derived from **WebRequest**, to handle HTTP and HTTPS requests.</span></span> <span data-ttu-id="f6c6e-107">在大多数情况下，WebRequest 类提供提出请求所需的所有属性；但是，如有必要，将 WebRequest.Create 方法创建的 WebRequest 对象转换为 HttpWebRequest 类型，即可访问该请求特定于 HTTP 的属性     。</span><span class="sxs-lookup"><span data-stu-id="f6c6e-107">In most cases, the **WebRequest** class provides all the properties you need to make a request; however, if necessary, you can cast **WebRequest** objects created by the **WebRequest.Create** method to the **HttpWebRequest** type to access the HTTP-specific properties of the request.</span></span> <span data-ttu-id="f6c6e-108">同样，HttpWebResponse 对象可处理来自 HTTP 和 HTTPS 请求的响应  。</span><span class="sxs-lookup"><span data-stu-id="f6c6e-108">Similarly, the **HttpWebResponse** object handles the responses from HTTP and HTTPS requests.</span></span> <span data-ttu-id="f6c6e-109">要访问 HttpWebResponse 对象特定于 HTTP 的属性，需将 WebResponse 对象转换为 HttpWebResponse 类型    。</span><span class="sxs-lookup"><span data-stu-id="f6c6e-109">To access the HTTP-specific properties of the **HttpWebResponse** object, you need to cast **WebResponse** objects to the **HttpWebResponse** type.</span></span>  
  
 <span data-ttu-id="f6c6e-110">.NET Framework 还提供 <xref:System.Net.FileWebRequest> 和 <xref:System.Net.FileWebResponse> 类来处理使用“file:”URI 方案的资源请求。</span><span class="sxs-lookup"><span data-stu-id="f6c6e-110">The .NET Framework also provides the <xref:System.Net.FileWebRequest> and <xref:System.Net.FileWebResponse> classes to handle requests for resources that use the "file:" URI scheme.</span></span> <span data-ttu-id="f6c6e-111">同样，提供的 <xref:System.Net.FtpWebRequest> 和 <xref:System.Net.FtpWebResponse> 类可处理使用“ftp:”方案的资源请求。</span><span class="sxs-lookup"><span data-stu-id="f6c6e-111">Likewise, the <xref:System.Net.FtpWebRequest> and <xref:System.Net.FtpWebResponse> classes are provided to handle requests for resources that use the "ftp:" scheme.</span></span> <span data-ttu-id="f6c6e-112">如果请求的是使用上述任一方案的资源，则可使用 WebRequest.Create 方法获取用于发出请求的对象  。</span><span class="sxs-lookup"><span data-stu-id="f6c6e-112">If your request is for a resource that uses any of these schemes, you can use the **WebRequest.Create** method to obtain an object with which to make your request.</span></span>  
  
 <span data-ttu-id="f6c6e-113">要处理使用其他应用程序级协议的请求，需实现从 WebRequest 和 WebResponse 派生的协议特定的类   。</span><span class="sxs-lookup"><span data-stu-id="f6c6e-113">To handle requests that use other application-level protocols, you need to implement protocol-specific classes derived from **WebRequest** and **WebResponse**.</span></span> <span data-ttu-id="f6c6e-114">有关详细信息，请参阅[对可插入协议进行编程](programming-pluggable-protocols.md)。</span><span class="sxs-lookup"><span data-stu-id="f6c6e-114">For more information, see [Programming Pluggable Protocols](programming-pluggable-protocols.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f6c6e-115">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f6c6e-115">See also</span></span>

- [<span data-ttu-id="f6c6e-116">如何：使用 WebRequest 类请求数据</span><span class="sxs-lookup"><span data-stu-id="f6c6e-116">How to: Request Data Using the WebRequest Class</span></span>](how-to-request-data-using-the-webrequest-class.md)
- [<span data-ttu-id="f6c6e-117">请求数据</span><span class="sxs-lookup"><span data-stu-id="f6c6e-117">Requesting Data</span></span>](requesting-data.md)
