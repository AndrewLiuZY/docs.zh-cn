---
title: IAppDomainSetup 接口
ms.date: 03/30/2017
api_name:
- IAppDomainSetup
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IAppDomainSetup
helpviewer_keywords:
- IAppDomainSetup interface [.NET Framework hosting]
ms.assetid: 1844da85-c031-40bf-bea4-1a3d12a36c8c
topic_type:
- apiref
ms.openlocfilehash: 1726f8929404e0dde979972d7830a6951dd71891
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/19/2020
ms.locfileid: "83617056"
---
# <a name="iappdomainsetup-interface"></a><span data-ttu-id="6fa5d-102">IAppDomainSetup 接口</span><span class="sxs-lookup"><span data-stu-id="6fa5d-102">IAppDomainSetup Interface</span></span>
<span data-ttu-id="6fa5d-103">提供属性，这些属性使宿主可以 <xref:System.AppDomain?displayProperty=nameWithType> 在调用[ICorRuntimeHost：： CreateDomainEx](icorruntimehost-createdomainex-method.md)方法创建类型之前配置该类型。</span><span class="sxs-lookup"><span data-stu-id="6fa5d-103">Provides properties that allow the host to configure an <xref:System.AppDomain?displayProperty=nameWithType> type before calling the [ICorRuntimeHost::CreateDomainEx](icorruntimehost-createdomainex-method.md) method to create it.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="6fa5d-104">属性</span><span class="sxs-lookup"><span data-stu-id="6fa5d-104">Properties</span></span>  
  
|<span data-ttu-id="6fa5d-105">properties</span><span class="sxs-lookup"><span data-stu-id="6fa5d-105">Property</span></span>|<span data-ttu-id="6fa5d-106">说明</span><span class="sxs-lookup"><span data-stu-id="6fa5d-106">Description</span></span>|  
|--------------|-----------------|  
|<xref:System.AppDomainSetup.ApplicationBase%2A>|<span data-ttu-id="6fa5d-107">获取或设置包含该应用程序的目录的名称。</span><span class="sxs-lookup"><span data-stu-id="6fa5d-107">Gets or sets the name of the directory that contains the application.</span></span>|  
|<xref:System.AppDomainSetup.ApplicationName%2A>|<span data-ttu-id="6fa5d-108">获取或设置应用程序的名称。</span><span class="sxs-lookup"><span data-stu-id="6fa5d-108">Gets or sets the name of the application.</span></span>|  
|<xref:System.AppDomainSetup.CachePath%2A>|<span data-ttu-id="6fa5d-109">获取或设置特定于应用程序的区域的名称，在该区域中对文件进行卷影复制。</span><span class="sxs-lookup"><span data-stu-id="6fa5d-109">Gets or sets the name of an area specific to the application where files are shadow-copied.</span></span>|  
|<xref:System.AppDomainSetup.ConfigurationFile%2A>|<span data-ttu-id="6fa5d-110">获取或设置应用程序的配置文件的名称。</span><span class="sxs-lookup"><span data-stu-id="6fa5d-110">Gets or sets the name of the configuration file for an application.</span></span>|  
|<xref:System.AppDomainSetup.DynamicBase%2A>|<span data-ttu-id="6fa5d-111">获取或设置用于存储和访问动态生成的文件的目录的名称。</span><span class="sxs-lookup"><span data-stu-id="6fa5d-111">Gets or sets the name of the directory where dynamically generated files are stored and accessed.</span></span>|  
|<xref:System.AppDomainSetup.LicenseFile%2A>|<span data-ttu-id="6fa5d-112">获取或设置与此域关联的许可证文件的路径。</span><span class="sxs-lookup"><span data-stu-id="6fa5d-112">Gets or sets the path to the license file that is associated with this domain.</span></span>|  
|<xref:System.AppDomainSetup.PrivateBinPath%2A>|<span data-ttu-id="6fa5d-113">获取或设置与 <xref:System.AppDomainSetup.ApplicationBase%2A> 要探测专用程序集的目录结合在一起的目录列表。</span><span class="sxs-lookup"><span data-stu-id="6fa5d-113">Gets or sets the list of directories combined with the <xref:System.AppDomainSetup.ApplicationBase%2A> directory to probe for private assemblies.</span></span>|  
|<xref:System.AppDomainSetup.PrivateBinPathProbe%2A>|<span data-ttu-id="6fa5d-114">获取或设置一个字符串值，该值包含或排除 <xref:System.AppDomainSetup.ApplicationBase%2A> 应用程序的搜索路径。</span><span class="sxs-lookup"><span data-stu-id="6fa5d-114">Gets or sets a string value that includes or excludes <xref:System.AppDomainSetup.ApplicationBase%2A> from the search path for the application.</span></span>|  
|<xref:System.AppDomainSetup.ShadowCopyDirectories%2A>|<span data-ttu-id="6fa5d-115">获取或设置目录的名称，这些目录包含要进行卷影复制的程序集。</span><span class="sxs-lookup"><span data-stu-id="6fa5d-115">Gets or sets the names of the directories that contain assemblies to be shadow-copied.</span></span>|  
|<xref:System.AppDomainSetup.ShadowCopyFiles%2A>|<span data-ttu-id="6fa5d-116">获取或设置一个字符串，该字符串指示阴影复制是打开还是关闭。</span><span class="sxs-lookup"><span data-stu-id="6fa5d-116">Gets or sets a string that indicates whether shadow-copying is turned on or off.</span></span> <span data-ttu-id="6fa5d-117">有效值为 "true" 或 "false"。</span><span class="sxs-lookup"><span data-stu-id="6fa5d-117">Valid values are "true" or "false".</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6fa5d-118">备注</span><span class="sxs-lookup"><span data-stu-id="6fa5d-118">Remarks</span></span>  
 <span data-ttu-id="6fa5d-119">`IAppDomainSetup`接口对应于 <xref:System.IAppDomainSetup> 类型实现的托管接口 <xref:System.AppDomainSetup> 。</span><span class="sxs-lookup"><span data-stu-id="6fa5d-119">The `IAppDomainSetup` interface corresponds to the managed <xref:System.IAppDomainSetup> interface, which the <xref:System.AppDomainSetup> type implements.</span></span> <span data-ttu-id="6fa5d-120"><xref:System.IAppDomainSetup?displayProperty=nameWithType>有关其属性的详细说明，请参阅。</span><span class="sxs-lookup"><span data-stu-id="6fa5d-120">See <xref:System.IAppDomainSetup?displayProperty=nameWithType> for detailed descriptions of its properties.</span></span>  
  
 <span data-ttu-id="6fa5d-121">`IAppDomainSetup`表示可以在创建之前添加到实例的程序集绑定信息 <xref:System.AppDomain> 。</span><span class="sxs-lookup"><span data-stu-id="6fa5d-121">`IAppDomainSetup` represents assembly binding information that can be added to an <xref:System.AppDomain> instance before its creation.</span></span> <span data-ttu-id="6fa5d-122">例如，主机可以设置 <xref:System.AppDomainSetup.ApplicationBase%2A> 属性来建立根目录，公共语言运行时（CLR）会探测托管程序集。</span><span class="sxs-lookup"><span data-stu-id="6fa5d-122">For example, a host can set the <xref:System.AppDomainSetup.ApplicationBase%2A> property to establish a root directory, which the common language runtime (CLR) probes for managed assemblies.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6fa5d-123">要求</span><span class="sxs-lookup"><span data-stu-id="6fa5d-123">Requirements</span></span>  
 <span data-ttu-id="6fa5d-124">**平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="6fa5d-124">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6fa5d-125">**标头：** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="6fa5d-125">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="6fa5d-126">**库：** 作为资源包括在 Mscoree.dll 中</span><span class="sxs-lookup"><span data-stu-id="6fa5d-126">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6fa5d-127">**.NET Framework 版本：**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6fa5d-127">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6fa5d-128">另请参阅</span><span class="sxs-lookup"><span data-stu-id="6fa5d-128">See also</span></span>

- <xref:System.AppDomain>
- <xref:System.AppDomainSetup>
- <xref:System.IAppDomainSetup>
- [<span data-ttu-id="6fa5d-129">承载接口</span><span class="sxs-lookup"><span data-stu-id="6fa5d-129">Hosting Interfaces</span></span>](hosting-interfaces.md)
