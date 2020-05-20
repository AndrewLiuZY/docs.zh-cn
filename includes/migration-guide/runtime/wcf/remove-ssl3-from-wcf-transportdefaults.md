---
ms.openlocfilehash: d75eff2d2a43ab4488577014ec43a9826b2b2924
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/15/2020
ms.locfileid: "68237846"
---
### <a name="remove-ssl3-from-the-wcf-transportdefaults"></a><span data-ttu-id="1c15c-101">从 WCF TransportDefaults 删除 Ssl3</span><span class="sxs-lookup"><span data-stu-id="1c15c-101">Remove Ssl3 from the WCF TransportDefaults</span></span>

|   |   |
|---|---|
|<span data-ttu-id="1c15c-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="1c15c-102">Details</span></span>|<span data-ttu-id="1c15c-103">结合使用 NetTcp 与传输安全性和凭据类型证书时，SSL 3 协议不再是用于协商安全连接的默认协议。</span><span class="sxs-lookup"><span data-stu-id="1c15c-103">When using NetTcp with transport security and a credential type of certificate, the SSL 3 protocol is no longer a default protocol used for negotiating a secure connection.</span></span> <span data-ttu-id="1c15c-104">在大多数情况下，应该不会对现有应用程序造成任何影响，因为 TLS 1.0 始终包含在 NetTcp 协议列表中。</span><span class="sxs-lookup"><span data-stu-id="1c15c-104">In most cases there should be no impact to existing apps as TLS 1.0 has always been included in the protocol list for NetTcp.</span></span> <span data-ttu-id="1c15c-105">所有现有客户端应该至少能够使用 TLS 1.0 来协商连接。</span><span class="sxs-lookup"><span data-stu-id="1c15c-105">All existing clients should be able to negotiate a connection using at least TLS1.0.</span></span>|
|<span data-ttu-id="1c15c-106">建议</span><span class="sxs-lookup"><span data-stu-id="1c15c-106">Suggestion</span></span>|<span data-ttu-id="1c15c-107">如果 Ssl3 必需，则使用以下配置机制之一将 Ssl3 添加到协商协议的列表。</span><span class="sxs-lookup"><span data-stu-id="1c15c-107">If Ssl3 is required, use one of the following configuration mechanisms to add Ssl3 to the list of negotiated protocols.</span></span><ul><li><xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement.SslProtocols></li><li><xref:System.ServiceModel.TcpTransportSecurity.SslProtocols></li><li>[<](~/docs/framework/configure-apps/file-schema/wcf/transport-of-nettcpbinding.md)</li><li><span data-ttu-id="1c15c-108">[&lt;customBinding&gt; 的 &lt;sslStreamSecurity&gt; 部分]~/docs/framework/configure-apps/file-schema/wcf/sslstreamsecurity.md)</span><span class="sxs-lookup"><span data-stu-id="1c15c-108">[&lt;sslStreamSecurity&gt; section of &lt;customBinding&gt;]~/docs/framework/configure-apps/file-schema/wcf/sslstreamsecurity.md)</span></span></li></ul>|
|<span data-ttu-id="1c15c-109">范围</span><span class="sxs-lookup"><span data-stu-id="1c15c-109">Scope</span></span>|<span data-ttu-id="1c15c-110">边缘</span><span class="sxs-lookup"><span data-stu-id="1c15c-110">Edge</span></span>|
|<span data-ttu-id="1c15c-111">Version</span><span class="sxs-lookup"><span data-stu-id="1c15c-111">Version</span></span>|<span data-ttu-id="1c15c-112">4.6.2</span><span class="sxs-lookup"><span data-stu-id="1c15c-112">4.6.2</span></span>|
|<span data-ttu-id="1c15c-113">类型</span><span class="sxs-lookup"><span data-stu-id="1c15c-113">Type</span></span>|<span data-ttu-id="1c15c-114">运行时</span><span class="sxs-lookup"><span data-stu-id="1c15c-114">Runtime</span></span>|
|<span data-ttu-id="1c15c-115">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="1c15c-115">Affected APIs</span></span>|<ul><li><xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement.SslProtocols?displayProperty=nameWithType></li><li><xref:System.ServiceModel.TcpTransportSecurity.SslProtocols?displayProperty=nameWithType></li></ul>|
