---
title: 文档审批过程
description: 此示例演示文档审批过程中的许多 Windows Workflow Foundation 和 Windows Communication Foundation 功能。
ms.date: 03/30/2017
ms.assetid: 9b240937-76a7-45cd-8823-7f82c34d03bd
ms.openlocfilehash: 18b4f978e9234daf22395f0d2f6f0889d0edf966
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/15/2020
ms.locfileid: "83421405"
---
# <a name="document-approval-process"></a><span data-ttu-id="586fe-103">文档审批过程</span><span class="sxs-lookup"><span data-stu-id="586fe-103">Document Approval Process</span></span>

<span data-ttu-id="586fe-104">此示例演示如何将多个 Windows Workflow Foundation （WF）和 Windows Communication Foundation （WCF）功能一起使用。</span><span class="sxs-lookup"><span data-stu-id="586fe-104">This sample demonstrates the use of many Windows Workflow Foundation (WF) and Windows Communication Foundation (WCF) features together.</span></span> <span data-ttu-id="586fe-105">这些功能一起使用实现一个文档审批过程方案。</span><span class="sxs-lookup"><span data-stu-id="586fe-105">Together they implement a document approval process scenario.</span></span> <span data-ttu-id="586fe-106">客户端应用程序既可提交等待审批的文档，也可批准文档。</span><span class="sxs-lookup"><span data-stu-id="586fe-106">A client application can submit documents for approval and approve documents.</span></span> <span data-ttu-id="586fe-107">有一个审批管理器应用程序，可用于促进客户端之间的通信和强制执行审批过程的规则。</span><span class="sxs-lookup"><span data-stu-id="586fe-107">An approval manager application exists to facilitate communications between clients and to enforce the rules of the approval process.</span></span> <span data-ttu-id="586fe-108">审批过程是一个可执行多种类型的审批的工作流。</span><span class="sxs-lookup"><span data-stu-id="586fe-108">The approval process is a workflow that can execute several types of approval.</span></span> <span data-ttu-id="586fe-109">存在多个活动来获取个人审批过程、团体审批过程（一定百分比的审批者）和复合审批过程（由团体审批和个人审批按顺序组成）。</span><span class="sxs-lookup"><span data-stu-id="586fe-109">Activities exist to get a single approval, a quorum approval (a percentage of set of approvers), and a complex approval process that consists of a quorum and single approval in a sequence.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="586fe-110">您的计算机上可能已安装这些示例。</span><span class="sxs-lookup"><span data-stu-id="586fe-110">The samples may already be installed on your machine.</span></span> <span data-ttu-id="586fe-111">在继续操作之前，请先检查以下（默认）目录：</span><span class="sxs-lookup"><span data-stu-id="586fe-111">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="586fe-112">如果此目录不存在，请参阅[.NET Framework 4 的 Windows Communication Foundation （wcf）和 Windows Workflow Foundation （WF）示例](https://www.microsoft.com/download/details.aspx?id=21459)以下载所有 WINDOWS COMMUNICATION FOUNDATION （wcf）和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 示例。</span><span class="sxs-lookup"><span data-stu-id="586fe-112">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="586fe-113">此示例位于以下目录：</span><span class="sxs-lookup"><span data-stu-id="586fe-113">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Application\DocumentApprovalProcess`

## <a name="sample-details"></a><span data-ttu-id="586fe-114">示例详细信息</span><span class="sxs-lookup"><span data-stu-id="586fe-114">Sample Details</span></span>

<span data-ttu-id="586fe-115">下图演示了文档审批过程工作流：</span><span class="sxs-lookup"><span data-stu-id="586fe-115">The following graphic demonstrates the document approval process workflow:</span></span>

![文档审批进程工作流](./media/document-approval-process/document-approval-process.jpg)

<span data-ttu-id="586fe-117">从客户端的角度来看，审批过程的工作方式如下：</span><span class="sxs-lookup"><span data-stu-id="586fe-117">From the client's perspective, the approval process functions as follows:</span></span>

1. <span data-ttu-id="586fe-118">客户端申请成为审批过程系统中的用户。</span><span class="sxs-lookup"><span data-stu-id="586fe-118">A client subscribes to be a user in the approval process system.</span></span>

2. <span data-ttu-id="586fe-119">WCF 客户端发送到由审批管理器应用程序承载的 WCF 服务。</span><span class="sxs-lookup"><span data-stu-id="586fe-119">A WCF client sends to a WCF service hosted by the approval manager application.</span></span>

3. <span data-ttu-id="586fe-120">将唯一的用户 ID 返回到客户端。</span><span class="sxs-lookup"><span data-stu-id="586fe-120">A unique user ID is returned to the client.</span></span> <span data-ttu-id="586fe-121">此时，客户端可参与审批过程。</span><span class="sxs-lookup"><span data-stu-id="586fe-121">The client can now participate in approval processes.</span></span>

4. <span data-ttu-id="586fe-122">客户端在加入后可发送文档以通过个人审批过程、团体审批过程或复合审批过程进行审批。</span><span class="sxs-lookup"><span data-stu-id="586fe-122">Once joined, a client can send a document for approval using single, quorum or complex approval processes.</span></span>

5. <span data-ttu-id="586fe-123">单击客户端界面中的按钮，在客户端工作流服务主机中启动工作流实例。</span><span class="sxs-lookup"><span data-stu-id="586fe-123">A button in the client’s interface is clicked, starting a workflow instance in a client Workflow Service Host.</span></span>

6. <span data-ttu-id="586fe-124">工作流将审批请求发送到审批管理器应用程序。</span><span class="sxs-lookup"><span data-stu-id="586fe-124">The workflow sends an approval request to the approval manager application.</span></span>

7. <span data-ttu-id="586fe-125">工作流管理器启动其自身的工作流以表示审批过程。</span><span class="sxs-lookup"><span data-stu-id="586fe-125">The workflow manager starts a workflow on its own side to represent an approval process.</span></span>

8. <span data-ttu-id="586fe-126">一旦执行管理器审批工作流，就会将结果发送回客户端。</span><span class="sxs-lookup"><span data-stu-id="586fe-126">Once the manager approval workflow executes, the results are sent back to the client.</span></span>

9. <span data-ttu-id="586fe-127">客户端显示结果。</span><span class="sxs-lookup"><span data-stu-id="586fe-127">The client displays the results.</span></span>

10. <span data-ttu-id="586fe-128">客户端可以随时接收审批请求并对其做出响应。</span><span class="sxs-lookup"><span data-stu-id="586fe-128">A client may receive an approval request and respond to the request at any point in time.</span></span>

11. <span data-ttu-id="586fe-129">在客户端上承载的 WCF 服务可以接收来自审批管理器应用程序的审批请求。</span><span class="sxs-lookup"><span data-stu-id="586fe-129">A WCF service hosted on the client can receive an approval request from the approval manager application.</span></span>

12. <span data-ttu-id="586fe-130">客户端上将呈现文档信息以供审阅。</span><span class="sxs-lookup"><span data-stu-id="586fe-130">The document information is presented on the client for review.</span></span>

13. <span data-ttu-id="586fe-131">用户可以批准或拒绝文档。</span><span class="sxs-lookup"><span data-stu-id="586fe-131">The user can approve or reject the document.</span></span>

14. <span data-ttu-id="586fe-132">WCF 客户端用于将审批响应发送回审批管理器应用程序。</span><span class="sxs-lookup"><span data-stu-id="586fe-132">A WCF client is used to send an approval response back to the approval manager application.</span></span>

<span data-ttu-id="586fe-133">从审批管理器应用程序的角度来看，审批过程的工作方式如下：</span><span class="sxs-lookup"><span data-stu-id="586fe-133">From the approval manager application’s point of view, the approval process functions as follows:</span></span>

1. <span data-ttu-id="586fe-134">客户端请求加入审批过程系统。</span><span class="sxs-lookup"><span data-stu-id="586fe-134">A client requests to participate to the approval process system.</span></span>

2. <span data-ttu-id="586fe-135">审批管理器上的 WCF 服务接收属于审批流程系统的请求。</span><span class="sxs-lookup"><span data-stu-id="586fe-135">A WCF service on the approval manager receives a request to be part of the approval process system.</span></span>

3. <span data-ttu-id="586fe-136">为客户端生成唯一的 ID。</span><span class="sxs-lookup"><span data-stu-id="586fe-136">A unique ID is generated for the client.</span></span> <span data-ttu-id="586fe-137">将用户信息存储在数据库中。</span><span class="sxs-lookup"><span data-stu-id="586fe-137">The user information is stored in a database.</span></span>

4. <span data-ttu-id="586fe-138">将唯一的 ID 发送回用户。</span><span class="sxs-lookup"><span data-stu-id="586fe-138">The unique ID is sent back to the user.</span></span>

5. <span data-ttu-id="586fe-139">接收审批请求。</span><span class="sxs-lookup"><span data-stu-id="586fe-139">An approval request is receive.</span></span> <span data-ttu-id="586fe-140">审批管理器执行审批过程。</span><span class="sxs-lookup"><span data-stu-id="586fe-140">The approval manager executes an approval process.</span></span>

6. <span data-ttu-id="586fe-141">审批管理器接收审批请求，启动新的工作流。</span><span class="sxs-lookup"><span data-stu-id="586fe-141">An approval request is received by the approval manager, starting a new workflow.</span></span>

7. <span data-ttu-id="586fe-142">根据请求的类型（个人、团体或复合）来执行不同的活动。</span><span class="sxs-lookup"><span data-stu-id="586fe-142">Depending on the type of request (simple, quorum, or complex) a different activity is executed.</span></span>

8. <span data-ttu-id="586fe-143">发送和接收相关的活动，这些活动用于向客户端发送供审阅的审批请求和从客户端接收响应。</span><span class="sxs-lookup"><span data-stu-id="586fe-143">Send and Receive activities with correlation are used to send the approval request to the client for review and receive the response.</span></span>

9. <span data-ttu-id="586fe-144">将审批过程工作流的结果发送到客户端。</span><span class="sxs-lookup"><span data-stu-id="586fe-144">The result of the approval process workflow is sent to the client.</span></span>

## <a name="using-the-sample"></a><span data-ttu-id="586fe-145">使用示例</span><span class="sxs-lookup"><span data-stu-id="586fe-145">Using the Sample</span></span>

##### <a name="to-set-up-the-database"></a><span data-ttu-id="586fe-146">安装数据库</span><span class="sxs-lookup"><span data-stu-id="586fe-146">To set up the database</span></span>

1. <span data-ttu-id="586fe-147">从使用管理员特权打开的 Visual Studio 2010 命令提示符下，导航到此 DocumentApprovalProcess 文件夹并运行 Setup .cmd。</span><span class="sxs-lookup"><span data-stu-id="586fe-147">From a Visual Studio 2010 command prompt opened with Administrator privileges, navigate to this DocumentApprovalProcess folder and run Setup.cmd.</span></span>

##### <a name="to-set-up-the-application"></a><span data-ttu-id="586fe-148">设置应用程序</span><span class="sxs-lookup"><span data-stu-id="586fe-148">To set up the application</span></span>

1. <span data-ttu-id="586fe-149">使用 Visual Studio 2010 打开 DocumentApprovalProcess 解决方案文件。</span><span class="sxs-lookup"><span data-stu-id="586fe-149">Using Visual Studio 2010, open the DocumentApprovalProcess.sln solution file.</span></span>

2. <span data-ttu-id="586fe-150">要生成解决方案，按 Ctrl+Shift+B。</span><span class="sxs-lookup"><span data-stu-id="586fe-150">To build the solution, press CTRL+SHIFT+B.</span></span>

3. <span data-ttu-id="586fe-151">若要运行解决方案，请在**解决方案资源管理器**中右键单击 "ApprovalManager" 项目，然后单击右键菜单中的 "**调试**" -> "**启动**新实例"，以启动审批管理器应用程序。</span><span class="sxs-lookup"><span data-stu-id="586fe-151">To run the solution, launch the Approval Manager Application by right-clicking the ApprovalManager project in the **Solution Explorer** and clicking **Debug**->**Start** new instance from the right-click menu.</span></span>

    <span data-ttu-id="586fe-152">等待管理器的输出指示已做好准备工作。</span><span class="sxs-lookup"><span data-stu-id="586fe-152">Wait for the manager’s output to let you know that it is ready.</span></span>

##### <a name="to-run-the-single-approval-scenario"></a><span data-ttu-id="586fe-153">运行个人审批方案</span><span class="sxs-lookup"><span data-stu-id="586fe-153">To run the single approval scenario</span></span>

1. <span data-ttu-id="586fe-154">使用管理员权限打开命令提示符。</span><span class="sxs-lookup"><span data-stu-id="586fe-154">Open a command prompt with administrator permission.</span></span>

2. <span data-ttu-id="586fe-155">导航到包含解决方案的目录。</span><span class="sxs-lookup"><span data-stu-id="586fe-155">Navigate to the directory that contains the solution.</span></span>

3. <span data-ttu-id="586fe-156">导航到 ApprovalClient\Bin\Debug 文件夹并执行两个 ApprovalClient.exe 实例。</span><span class="sxs-lookup"><span data-stu-id="586fe-156">Navigate to the ApprovalClient\Bin\Debug folder and execute two instances of ApprovalClient.exe.</span></span>

4. <span data-ttu-id="586fe-157">单击 "**发现**"，等待 "**订阅**" 按钮启用。</span><span class="sxs-lookup"><span data-stu-id="586fe-157">Click **discover**, wait until the **subscribe** button is enabled.</span></span>

5. <span data-ttu-id="586fe-158">键入任何用户名并单击 "**订阅**"。</span><span class="sxs-lookup"><span data-stu-id="586fe-158">Type any user name and click **subscribe**.</span></span> <span data-ttu-id="586fe-159">对于一个客户端，使用 `UserType1` 和其他类型 `UserType2`。</span><span class="sxs-lookup"><span data-stu-id="586fe-159">For one client, use `UserType1` and the other type `UserType2`.</span></span>

6. <span data-ttu-id="586fe-160">在 `UserType1` 客户端中，从下拉菜单中选择个人审批类型，然后键入文档名称和内容。</span><span class="sxs-lookup"><span data-stu-id="586fe-160">In the `UserType1` client, select the single approval type from the drop down menu and type a document name and content.</span></span> <span data-ttu-id="586fe-161">单击 "**请求批准**"。</span><span class="sxs-lookup"><span data-stu-id="586fe-161">Click **Request Approval**.</span></span>

7. <span data-ttu-id="586fe-162">在 `UserType2` 客户端中，将显示等待审批的文档。</span><span class="sxs-lookup"><span data-stu-id="586fe-162">In the `UserType2` client, a document awaiting approval appears.</span></span> <span data-ttu-id="586fe-163">选择它，然后按 "**批准**" 或 "**拒绝**"。</span><span class="sxs-lookup"><span data-stu-id="586fe-163">Select it and press **approve** or **reject**.</span></span> <span data-ttu-id="586fe-164">结果将显示在 `UserType1` 客户端中。</span><span class="sxs-lookup"><span data-stu-id="586fe-164">The results should show in the `UserType1` client.</span></span>

##### <a name="to-run-the-quorum-approval-scenario"></a><span data-ttu-id="586fe-165">运行团体审批方案</span><span class="sxs-lookup"><span data-stu-id="586fe-165">To run the quorum approval scenario</span></span>

1. <span data-ttu-id="586fe-166">使用管理员权限打开命令提示符。</span><span class="sxs-lookup"><span data-stu-id="586fe-166">Open a command prompt with administrator permission.</span></span>

2. <span data-ttu-id="586fe-167">导航到包含解决方案的目录。</span><span class="sxs-lookup"><span data-stu-id="586fe-167">Navigate to the directory that contains the solution.</span></span>

3. <span data-ttu-id="586fe-168">导航到 ApprovalClient\Bin\Debug 文件夹并执行三个 ApprovalClient.exe 实例。</span><span class="sxs-lookup"><span data-stu-id="586fe-168">Navigate to the ApprovalClient\Bin\Debug folder and execute three instances of ApprovalClient.exe.</span></span>

4. <span data-ttu-id="586fe-169">单击 "**发现**"，等待 "**订阅**" 按钮启用。</span><span class="sxs-lookup"><span data-stu-id="586fe-169">Click **discover**, wait until the **subscribe** button is enabled.</span></span>

5. <span data-ttu-id="586fe-170">键入任何用户名并单击 "**订阅**"。</span><span class="sxs-lookup"><span data-stu-id="586fe-170">Type any user name and click **subscribe**.</span></span> <span data-ttu-id="586fe-171">对于一个客户端，使用 `UserType1` 和其他两个类型 `UserType2`。</span><span class="sxs-lookup"><span data-stu-id="586fe-171">For one client use `UserType1` and the other two type `UserType2`.</span></span>

6. <span data-ttu-id="586fe-172">在 `UserType1` 客户端中，从下拉菜单中选择团体审批类型，然后键入文档名称和内容。</span><span class="sxs-lookup"><span data-stu-id="586fe-172">In the `UserType1` client, select the quorum approval type from the drop down menu and type a document name and content.</span></span> <span data-ttu-id="586fe-173">单击 "**请求批准**"。</span><span class="sxs-lookup"><span data-stu-id="586fe-173">Click **Request Approval**.</span></span> <span data-ttu-id="586fe-174">这将请求两个 `UserType2` 客户端批准或拒绝该文档。</span><span class="sxs-lookup"><span data-stu-id="586fe-174">This requests that the two `UserType2` clients approve or reject the document.</span></span> <span data-ttu-id="586fe-175">虽然两个 `UserType2` 客户端都必须做出响应，但只需一个客户端批准文档即可使文档获得审批。</span><span class="sxs-lookup"><span data-stu-id="586fe-175">While both `UserType2` clients must respond, only one client must approve the document for it to be approved.</span></span>

7. <span data-ttu-id="586fe-176">在 `UserType2` 客户端中，将显示等待审批的文档。</span><span class="sxs-lookup"><span data-stu-id="586fe-176">In the `UserType2` clients, a document awaiting approval appears.</span></span> <span data-ttu-id="586fe-177">选择它，然后按 "**批准**" 或 "**拒绝**"。</span><span class="sxs-lookup"><span data-stu-id="586fe-177">Select it and press **approve** or **reject**.</span></span> <span data-ttu-id="586fe-178">结果将显示在 `UserType1` 客户端中。</span><span class="sxs-lookup"><span data-stu-id="586fe-178">The results should show in the `UserType1` client.</span></span>

##### <a name="to-run-the-complex-approval-scenario"></a><span data-ttu-id="586fe-179">运行复合审批方案</span><span class="sxs-lookup"><span data-stu-id="586fe-179">To run the complex approval scenario</span></span>

1. <span data-ttu-id="586fe-180">使用管理员权限打开命令提示符。</span><span class="sxs-lookup"><span data-stu-id="586fe-180">Open a command prompt with administrator permission.</span></span>

2. <span data-ttu-id="586fe-181">导航到包含解决方案的目录。</span><span class="sxs-lookup"><span data-stu-id="586fe-181">Navigate to the directory that contains the solution.</span></span>

3. <span data-ttu-id="586fe-182">导航到 ApprovalClient\Bin\Debug 文件夹并执行四个 ApprovalClient.exe 实例。</span><span class="sxs-lookup"><span data-stu-id="586fe-182">Navigate to the ApprovalClient\Bin\Debug folder and execute four instances of ApprovalClient.exe.</span></span>

4. <span data-ttu-id="586fe-183">单击 "**发现**"，等待 "**订阅**" 按钮启用。</span><span class="sxs-lookup"><span data-stu-id="586fe-183">Click **discover**, wait until the **subscribe** button is enabled.</span></span>

5. <span data-ttu-id="586fe-184">键入任何用户名并单击 "**订阅**"。</span><span class="sxs-lookup"><span data-stu-id="586fe-184">Type any user name and click **subscribe**.</span></span> <span data-ttu-id="586fe-185">为第一个客户端使用 `UserType1`，为第二个客户端使用 `UserType2`，为最后一个客户端使用 `UserType3`。</span><span class="sxs-lookup"><span data-stu-id="586fe-185">For one client use `UserType1`, in two uses type `UserType2`, and in the last use `UserType3`.</span></span>

6. <span data-ttu-id="586fe-186">在 `UserType1` 客户端中，从下拉菜单中选择个人审批类型，然后键入文档名称和内容。</span><span class="sxs-lookup"><span data-stu-id="586fe-186">In the `UserType1` client, select the single approval type from the drop down menu and type a document name and content.</span></span> <span data-ttu-id="586fe-187">单击 "**请求批准**"。</span><span class="sxs-lookup"><span data-stu-id="586fe-187">Click **Request Approval**.</span></span>

7. <span data-ttu-id="586fe-188">在 `UserType2` 客户端中，将显示等待审批的文档。</span><span class="sxs-lookup"><span data-stu-id="586fe-188">In the `UserType2` clients, a document awaiting approval appears.</span></span> <span data-ttu-id="586fe-189">选择它并按 "**批准**"，文档将传递给 `UserType3` 客户端。</span><span class="sxs-lookup"><span data-stu-id="586fe-189">Select it and press **approve**, the document is passed to the `UserType3` client.</span></span>

    <span data-ttu-id="586fe-190">如果第一个 `UserType2` 团体批准该文档，则该文档将传递到 `UserType3` 客户端。</span><span class="sxs-lookup"><span data-stu-id="586fe-190">If the document is approved by the first `UserType2` quorum, the document is passed to the `UserType3` client.</span></span>

8. <span data-ttu-id="586fe-191">批准或拒绝来自 `UserType3` 客户端的文档。</span><span class="sxs-lookup"><span data-stu-id="586fe-191">Approve or reject the document from the `UserType3` client.</span></span> <span data-ttu-id="586fe-192">结果将显示在 `UserType1` 客户端中。</span><span class="sxs-lookup"><span data-stu-id="586fe-192">The results should show in the `UserType1` client.</span></span>

##### <a name="to-clean-up"></a><span data-ttu-id="586fe-193">清理</span><span class="sxs-lookup"><span data-stu-id="586fe-193">To clean up</span></span>

1. <span data-ttu-id="586fe-194">在 Visual Studio 2010 命令提示符下，导航到 DocumentApprovalProcess 文件夹并运行 "清理"。</span><span class="sxs-lookup"><span data-stu-id="586fe-194">From a Visual Studio 2010 command prompt, navigate to the DocumentApprovalProcess folder and run Cleanup.cmd.</span></span>
