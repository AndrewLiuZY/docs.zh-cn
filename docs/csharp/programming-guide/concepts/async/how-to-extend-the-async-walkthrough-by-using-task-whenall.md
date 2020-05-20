---
title: 如何使用 Task.WhenAll 扩展异步演练 (C#)
ms.date: 07/20/2015
ms.assetid: f6927ef2-dc6c-43f8-bc82-bbeac42de423
ms.openlocfilehash: afd7dda4e876b7faa54ae4a8e62d640d2b9aaf07
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/14/2020
ms.locfileid: "73970024"
---
# <a name="how-to-extend-the-async-walkthrough-by-using-taskwhenall-c"></a><span data-ttu-id="af12a-102">如何使用 Task.WhenAll 扩展异步演练 (C#)</span><span class="sxs-lookup"><span data-stu-id="af12a-102">How to extend the async walkthrough by using Task.WhenAll (C#)</span></span>

<span data-ttu-id="af12a-103">可以使用 <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> 方法来改进[演练：使用 Async 和 Await 访问 Web (C#)](./walkthrough-accessing-the-web-by-using-async-and-await.md) 中的异步解决方案性能。</span><span class="sxs-lookup"><span data-stu-id="af12a-103">You can improve the performance of the async solution in [Walkthrough: Accessing the Web by Using async and await (C#)](./walkthrough-accessing-the-web-by-using-async-and-await.md) by using the <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="af12a-104">此方法以异步方式等待多个异步操作（它们表示为任务的集合）。</span><span class="sxs-lookup"><span data-stu-id="af12a-104">This method asynchronously awaits multiple asynchronous operations, which are represented as a collection of tasks.</span></span>

<span data-ttu-id="af12a-105">你可能已在演练中注意到网站以不同速率进行下载。</span><span class="sxs-lookup"><span data-stu-id="af12a-105">You might have noticed in the walkthrough that the websites download at different rates.</span></span> <span data-ttu-id="af12a-106">有时一个网站非常慢，这会延迟所有其余下载。</span><span class="sxs-lookup"><span data-stu-id="af12a-106">Sometimes one of the websites is very slow, which delays all the remaining downloads.</span></span> <span data-ttu-id="af12a-107">运行在演练中生成的异步解决方案时，如果不想等待，则可以方便地结束程序，但更好的选项是同时启动所有下载，并让较快的下载继续进行而不等待延迟的下载。</span><span class="sxs-lookup"><span data-stu-id="af12a-107">When you run the asynchronous solutions that you build in the walkthrough, you can end the program easily if you don't want to wait, but a better option would be to start all the downloads at the same time and let faster downloads continue without waiting for the one that’s delayed.</span></span>

<span data-ttu-id="af12a-108">可将 `Task.WhenAll` 方法应用于任务的集合。</span><span class="sxs-lookup"><span data-stu-id="af12a-108">You apply the `Task.WhenAll` method to a collection of tasks.</span></span> <span data-ttu-id="af12a-109">`WhenAll` 的应用程序返回单个任务，直到集合中的每个任务都已完成之后，该任务才会完成。</span><span class="sxs-lookup"><span data-stu-id="af12a-109">The application of `WhenAll` returns a single task that isn’t complete until every task in the collection is completed.</span></span> <span data-ttu-id="af12a-110">任务会表现为并行运行，但不会创建其他线程。</span><span class="sxs-lookup"><span data-stu-id="af12a-110">The tasks appear to run in parallel, but no additional threads are created.</span></span> <span data-ttu-id="af12a-111">任务可以按任何顺序完成。</span><span class="sxs-lookup"><span data-stu-id="af12a-111">The tasks can complete in any order.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="af12a-112">下面的过程介绍[演练：使用 Async 和 Await 访问 Web (C#)](./walkthrough-accessing-the-web-by-using-async-and-await.md) 中开发的异步应用程序的扩展。</span><span class="sxs-lookup"><span data-stu-id="af12a-112">The following procedures describe extensions to the async applications that are developed in [Walkthrough: Accessing the Web by Using async and await (C#)](./walkthrough-accessing-the-web-by-using-async-and-await.md).</span></span> <span data-ttu-id="af12a-113">可以通过完成演练或从[开发人员代码示例](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f)下载代码来开发应用程序。</span><span class="sxs-lookup"><span data-stu-id="af12a-113">You can develop the applications by either completing the walkthrough or downloading the code from [Developer Code Samples](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f).</span></span>
>
> <span data-ttu-id="af12a-114">若要运行示例，必须在计算机上安装 Visual Studio 2012 或更高版本。</span><span class="sxs-lookup"><span data-stu-id="af12a-114">To run the example, you must have Visual Studio 2012 or later installed on your computer.</span></span>

### <a name="to-add-taskwhenall-to-your-geturlcontentsasync-solution"></a><span data-ttu-id="af12a-115">向你的 GetURLContentsAsync 解决方案中添加 Task.WhenAll</span><span class="sxs-lookup"><span data-stu-id="af12a-115">To add Task.WhenAll to your GetURLContentsAsync solution</span></span>

1. <span data-ttu-id="af12a-116">向[演练：使用 Async 和 Await 访问 Web (C#)](./walkthrough-accessing-the-web-by-using-async-and-await.md) 中开发的第一个应用程序添加 `ProcessURLAsync` 方法。</span><span class="sxs-lookup"><span data-stu-id="af12a-116">Add the `ProcessURLAsync` method to the first application that's developed in [Walkthrough: Accessing the Web by Using async and await (C#)](./walkthrough-accessing-the-web-by-using-async-and-await.md).</span></span>

    - <span data-ttu-id="af12a-117">如果是从[开发人员代码示例](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f)下载的代码，请打开 AsyncWalkthrough 项目，然后向 MainWindow.xaml.cs 文件添加 `ProcessURLAsync`。</span><span class="sxs-lookup"><span data-stu-id="af12a-117">If you downloaded the code from  [Developer Code Samples](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f), open the AsyncWalkthrough project, and then add `ProcessURLAsync` to the MainWindow.xaml.cs file.</span></span>

    - <span data-ttu-id="af12a-118">如果是通过完成演练开发的代码，请向包含 `GetURLContentsAsync` 方法的应用程序添加 `ProcessURLAsync`。</span><span class="sxs-lookup"><span data-stu-id="af12a-118">If you developed the code by completing the walkthrough, add `ProcessURLAsync` to the application that includes the `GetURLContentsAsync` method.</span></span> <span data-ttu-id="af12a-119">此应用程序的 MainWindow.xaml.cs 文件是“完成演练中的代码示例”部分中的第一个示例。</span><span class="sxs-lookup"><span data-stu-id="af12a-119">The MainWindow.xaml.cs file for this application is the first example in the "Complete Code Examples from the Walkthrough" section.</span></span>

    <span data-ttu-id="af12a-120">`ProcessURLAsync` 方法整合了原始演练的 `SumPageSizesAsync` 中的 `foreach` 循环体中的操作。</span><span class="sxs-lookup"><span data-stu-id="af12a-120">The `ProcessURLAsync` method consolidates the actions in the body of the `foreach` loop in `SumPageSizesAsync` in the original walkthrough.</span></span> <span data-ttu-id="af12a-121">该方法以异步方式将指定网站的内容作为字节数组进行下载，然后显示并返回字节数组的长度。</span><span class="sxs-lookup"><span data-stu-id="af12a-121">The method asynchronously downloads the contents of a specified website as a byte array, and then displays and returns the length of the byte array.</span></span>

    ```csharp
    private async Task<int> ProcessURLAsync(string url)
    {
        var byteArray = await GetURLContentsAsync(url);
        DisplayResults(url, byteArray);
        return byteArray.Length;
    }
    ```

2. <span data-ttu-id="af12a-122">注释禁止或删除 `SumPageSizesAsync` 中的 `foreach` 循环，如以下代码所示。</span><span class="sxs-lookup"><span data-stu-id="af12a-122">Comment out or delete the `foreach` loop in `SumPageSizesAsync`, as the following code shows.</span></span>

    ```csharp
    //var total = 0;
    //foreach (var url in urlList)
    //{
    //    byte[] urlContents = await GetURLContentsAsync(url);

    //    // The previous line abbreviates the following two assignment statements.
    //    // GetURLContentsAsync returns a Task<T>. At completion, the task
    //    // produces a byte array.
    //    //Task<byte[]> getContentsTask = GetURLContentsAsync(url);
    //    //byte[] urlContents = await getContentsTask;

    //    DisplayResults(url, urlContents);

    //    // Update the total.
    //    total += urlContents.Length;
    //}
    ```

3. <span data-ttu-id="af12a-123">创建任务集合。</span><span class="sxs-lookup"><span data-stu-id="af12a-123">Create a collection of tasks.</span></span> <span data-ttu-id="af12a-124">以下代码定义一个[查询](../linq/index.md)，由 <xref:System.Linq.Enumerable.ToArray%2A> 方法执行该查询时，它会创建下载每个网站内容的任务集合。</span><span class="sxs-lookup"><span data-stu-id="af12a-124">The following code defines a [query](../linq/index.md) that, when executed by the <xref:System.Linq.Enumerable.ToArray%2A> method, creates a collection of tasks that download the contents of each website.</span></span> <span data-ttu-id="af12a-125">计算该查询时，会启动任务。</span><span class="sxs-lookup"><span data-stu-id="af12a-125">The tasks are started when the query is evaluated.</span></span>

    <span data-ttu-id="af12a-126">在 `urlList` 的声明后，将以下代码添加到方法 `SumPageSizesAsync` 中。</span><span class="sxs-lookup"><span data-stu-id="af12a-126">Add the following code to method `SumPageSizesAsync` after the declaration of `urlList`.</span></span>

    ```csharp
    // Create a query.
    IEnumerable<Task<int>> downloadTasksQuery =
        from url in urlList select ProcessURLAsync(url);

    // Use ToArray to execute the query and start the download tasks.
    Task<int>[] downloadTasks = downloadTasksQuery.ToArray();
    ```

4. <span data-ttu-id="af12a-127">将 `Task.WhenAll` 应用于任务集合 `downloadTasks`。</span><span class="sxs-lookup"><span data-stu-id="af12a-127">Apply `Task.WhenAll` to the collection of tasks, `downloadTasks`.</span></span> <span data-ttu-id="af12a-128">`Task.WhenAll` 返回单个任务，它在任务集合中的所有任务都已完成时完成。</span><span class="sxs-lookup"><span data-stu-id="af12a-128">`Task.WhenAll` returns a single task that finishes when all the tasks in the collection of tasks have completed.</span></span>

    <span data-ttu-id="af12a-129">在以下示例中，`await` 表达式等待 `WhenAll` 返回的单个任务完成。</span><span class="sxs-lookup"><span data-stu-id="af12a-129">In the following example, the `await` expression awaits the completion of the single task that `WhenAll` returns.</span></span> <span data-ttu-id="af12a-130">该表达式的计算结果为整数数组，其中每个整数都是一个下载的网站的长度。</span><span class="sxs-lookup"><span data-stu-id="af12a-130">The expression evaluates to an array of integers, where each integer is the length of a downloaded website.</span></span> <span data-ttu-id="af12a-131">就在上一步添加的代码后，将以下代码添加到 `SumPageSizesAsync` 中。</span><span class="sxs-lookup"><span data-stu-id="af12a-131">Add the following code to `SumPageSizesAsync`, just after the code that you added in the previous step.</span></span>

    ```csharp
    // Await the completion of all the running tasks.
    int[] lengths = await Task.WhenAll(downloadTasks);

    //// The previous line is equivalent to the following two statements.
    //Task<int[]> whenAllTask = Task.WhenAll(downloadTasks);
    //int[] lengths = await whenAllTask;
    ```

5. <span data-ttu-id="af12a-132">最后，使用 <xref:System.Linq.Enumerable.Sum%2A> 方法计算所有网站的长度总和。</span><span class="sxs-lookup"><span data-stu-id="af12a-132">Finally, use the <xref:System.Linq.Enumerable.Sum%2A> method to calculate the sum of the lengths of all the websites.</span></span> <span data-ttu-id="af12a-133">将以下行添加到 `SumPageSizesAsync` 中。</span><span class="sxs-lookup"><span data-stu-id="af12a-133">Add the following line to `SumPageSizesAsync`.</span></span>

    ```csharp
    int total = lengths.Sum();
    ```

### <a name="to-add-taskwhenall-to-the-httpclientgetbytearrayasync-solution"></a><span data-ttu-id="af12a-134">向 HttpClient.GetByteArrayAsync 解决方案中添加 Task.WhenAll</span><span class="sxs-lookup"><span data-stu-id="af12a-134">To add Task.WhenAll to the HttpClient.GetByteArrayAsync solution</span></span>

1. <span data-ttu-id="af12a-135">向[演练：使用 Async 和 Await 访问 Web (C#)](./walkthrough-accessing-the-web-by-using-async-and-await.md) 中开发的第二个应用程序添加以下版本的 `ProcessURLAsync`。</span><span class="sxs-lookup"><span data-stu-id="af12a-135">Add the following version of `ProcessURLAsync` to the second application that's developed in [Walkthrough: Accessing the Web by Using async and await (C#)](./walkthrough-accessing-the-web-by-using-async-and-await.md).</span></span>

    - <span data-ttu-id="af12a-136">如果是从[开发人员代码示例](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f)下载的代码，请打开 AsyncWalkthrough_HttpClient 项目，然后向 MainWindow.xaml.cs 文件添加 `ProcessURLAsync`。</span><span class="sxs-lookup"><span data-stu-id="af12a-136">If you downloaded the code from [Developer Code Samples](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f), open the AsyncWalkthrough_HttpClient project, and then add `ProcessURLAsync` to the MainWindow.xaml.cs file.</span></span>

    - <span data-ttu-id="af12a-137">如果是通过完成演练开发的代码，请向使用 `HttpClient.GetByteArrayAsync` 方法的应用程序添加 `ProcessURLAsync`。</span><span class="sxs-lookup"><span data-stu-id="af12a-137">If you developed the code by completing the walkthrough, add `ProcessURLAsync` to the application that uses the `HttpClient.GetByteArrayAsync` method.</span></span> <span data-ttu-id="af12a-138">此应用程序的 MainWindow.xaml.cs 文件是“完成演练中的代码示例”部分中的第二个示例。</span><span class="sxs-lookup"><span data-stu-id="af12a-138">The MainWindow.xaml.cs file for this application is the second example in the "Complete Code Examples from the Walkthrough" section.</span></span>

    <span data-ttu-id="af12a-139">`ProcessURLAsync` 方法整合了原始演练的 `SumPageSizesAsync` 中的 `foreach` 循环体中的操作。</span><span class="sxs-lookup"><span data-stu-id="af12a-139">The `ProcessURLAsync` method consolidates the actions in the body of the `foreach` loop in `SumPageSizesAsync` in the original walkthrough.</span></span> <span data-ttu-id="af12a-140">该方法以异步方式将指定网站的内容作为字节数组进行下载，然后显示并返回字节数组的长度。</span><span class="sxs-lookup"><span data-stu-id="af12a-140">The method asynchronously downloads the contents of a specified website as a byte array, and then displays and returns the length of the byte array.</span></span>

    <span data-ttu-id="af12a-141">与上面过程中的 `ProcessURLAsync` 方法的唯一区别是使用 <xref:System.Net.Http.HttpClient> 实例 `client`。</span><span class="sxs-lookup"><span data-stu-id="af12a-141">The only difference from the `ProcessURLAsync` method in the previous procedure is the use of the <xref:System.Net.Http.HttpClient> instance, `client`.</span></span>

    ```csharp
    async Task<int> ProcessURLAsync(string url, HttpClient client)
    {
        byte[] byteArray = await client.GetByteArrayAsync(url);
        DisplayResults(url, byteArray);
        return byteArray.Length;
    }
    ```

2. <span data-ttu-id="af12a-142">注释禁止或删除 `SumPageSizesAsync` 中的 `For Each` 或 `foreach` 循环，如以下代码所示。</span><span class="sxs-lookup"><span data-stu-id="af12a-142">Comment out or delete the `For Each` or `foreach` loop in `SumPageSizesAsync`, as the following code shows.</span></span>

    ```csharp
    //var total = 0;
    //foreach (var url in urlList)
    //{
    //    // GetByteArrayAsync returns a Task<T>. At completion, the task
    //    // produces a byte array.
    //    byte[] urlContent = await client.GetByteArrayAsync(url);

    //    // The previous line abbreviates the following two assignment
    //    // statements.
    //    Task<byte[]> getContentTask = client.GetByteArrayAsync(url);
    //    byte[] urlContent = await getContentTask;

    //    DisplayResults(url, urlContent);

    //    // Update the total.
    //    total += urlContent.Length;
    //}
    ```

3. <span data-ttu-id="af12a-143">定义一个[查询](../linq/index.md)，由 <xref:System.Linq.Enumerable.ToArray%2A> 方法执行该查询时，它会创建下载每个网站内容的任务集合。</span><span class="sxs-lookup"><span data-stu-id="af12a-143">Define a [query](../linq/index.md) that, when executed by the <xref:System.Linq.Enumerable.ToArray%2A> method, creates a collection of tasks that download the contents of each website.</span></span> <span data-ttu-id="af12a-144">计算该查询时，会启动任务。</span><span class="sxs-lookup"><span data-stu-id="af12a-144">The tasks are started when the query is evaluated.</span></span>

    <span data-ttu-id="af12a-145">在 `client` 和 `urlList` 的声明后，将以下代码添加到方法 `SumPageSizesAsync` 中。</span><span class="sxs-lookup"><span data-stu-id="af12a-145">Add the following code to method `SumPageSizesAsync` after the declaration of `client` and `urlList`.</span></span>

    ```csharp
    // Create a query.
    IEnumerable<Task<int>> downloadTasksQuery =
        from url in urlList select ProcessURLAsync(url, client);

    // Use ToArray to execute the query and start the download tasks.
    Task<int>[] downloadTasks = downloadTasksQuery.ToArray();
    ```

4. <span data-ttu-id="af12a-146">接下来，将 `Task.WhenAll` 应用于任务集合 `downloadTasks`。</span><span class="sxs-lookup"><span data-stu-id="af12a-146">Next, apply `Task.WhenAll` to the collection of tasks, `downloadTasks`.</span></span> <span data-ttu-id="af12a-147">`Task.WhenAll` 返回单个任务，它在任务集合中的所有任务都已完成时完成。</span><span class="sxs-lookup"><span data-stu-id="af12a-147">`Task.WhenAll` returns a single task that finishes when all the tasks in the collection of tasks have completed.</span></span>

    <span data-ttu-id="af12a-148">在以下示例中，`await` 表达式等待 `WhenAll` 返回的单个任务完成。</span><span class="sxs-lookup"><span data-stu-id="af12a-148">In the following example, the `await` expression awaits the completion of the single task that `WhenAll` returns.</span></span> <span data-ttu-id="af12a-149">完成后，`await` 表达式的计算结果为整数数组，其中每个整数都是一个下载的网站的长度。</span><span class="sxs-lookup"><span data-stu-id="af12a-149">When complete, the `await` expression evaluates to an array of integers, where each integer is the length of a downloaded website.</span></span> <span data-ttu-id="af12a-150">就在上一步添加的代码后，将以下代码添加到 `SumPageSizesAsync` 中。</span><span class="sxs-lookup"><span data-stu-id="af12a-150">Add the following code to `SumPageSizesAsync`, just after the code that you added in the previous step.</span></span>

    ```csharp
    // Await the completion of all the running tasks.
    int[] lengths = await Task.WhenAll(downloadTasks);

    //// The previous line is equivalent to the following two statements.
    //Task<int[]> whenAllTask = Task.WhenAll(downloadTasks);
    //int[] lengths = await whenAllTask;
    ```

5. <span data-ttu-id="af12a-151">最后，使用 <xref:System.Linq.Enumerable.Sum%2A> 方法获取所有网站的长度总和。</span><span class="sxs-lookup"><span data-stu-id="af12a-151">Finally, use the <xref:System.Linq.Enumerable.Sum%2A> method to get the sum of the lengths of all the websites.</span></span> <span data-ttu-id="af12a-152">将以下行添加到 `SumPageSizesAsync` 中。</span><span class="sxs-lookup"><span data-stu-id="af12a-152">Add the following line to `SumPageSizesAsync`.</span></span>

    ```csharp
    int total = lengths.Sum();
    ```

### <a name="to-test-the-taskwhenall-solutions"></a><span data-ttu-id="af12a-153">测试 Task.WhenAll 解决方案</span><span class="sxs-lookup"><span data-stu-id="af12a-153">To test the Task.WhenAll solutions</span></span>

- <span data-ttu-id="af12a-154">对于任一解决方案，按 F5 键以运行程序，然后选择“启动”  按钮。</span><span class="sxs-lookup"><span data-stu-id="af12a-154">For either solution, choose the F5 key to run the program, and then choose the **Start** button.</span></span> <span data-ttu-id="af12a-155">输出应类似于[演练：使用 Async 和 Await 访问 Web (C#)](./walkthrough-accessing-the-web-by-using-async-and-await.md) 中的异步解决方案的输出。</span><span class="sxs-lookup"><span data-stu-id="af12a-155">The output should resemble the output from the async solutions in [Walkthrough: Accessing the Web by Using async and await (C#)](./walkthrough-accessing-the-web-by-using-async-and-await.md).</span></span> <span data-ttu-id="af12a-156">但请注意，网站每次会以不同顺序出现。</span><span class="sxs-lookup"><span data-stu-id="af12a-156">However, notice that the websites appear in a different order each time.</span></span>

## <a name="example"></a><span data-ttu-id="af12a-157">示例</span><span class="sxs-lookup"><span data-stu-id="af12a-157">Example</span></span>

<span data-ttu-id="af12a-158">以下代码演示使用 `GetURLContentsAsync` 方法从 Web 下载内容的项目的扩展。</span><span class="sxs-lookup"><span data-stu-id="af12a-158">The following code shows the extensions to the project that uses the `GetURLContentsAsync` method to download content from the web.</span></span>

```csharp
// Add the following using directives, and add a reference for System.Net.Http.
using System.Net.Http;
using System.IO;
using System.Net;

namespace AsyncExampleWPF_WhenAll
{
    public partial class MainWindow : Window
    {
        public MainWindow()
        {
            InitializeComponent();
        }

        private async void startButton_Click(object sender, RoutedEventArgs e)
        {
            resultsTextBox.Clear();

            // Two-step async call.
            Task sumTask = SumPageSizesAsync();
            await sumTask;

            // One-step async call.
            //await SumPageSizesAsync();

            resultsTextBox.Text += "\r\nControl returned to startButton_Click.\r\n";
        }

        private async Task SumPageSizesAsync()
        {
            // Make a list of web addresses.
            List<string> urlList = SetUpURLList();

            // Create a query.
            IEnumerable<Task<int>> downloadTasksQuery =
                from url in urlList select ProcessURLAsync(url);

            // Use ToArray to execute the query and start the download tasks.
            Task<int>[] downloadTasks = downloadTasksQuery.ToArray();

            // You can do other work here before awaiting.

            // Await the completion of all the running tasks.
            int[] lengths = await Task.WhenAll(downloadTasks);

            //// The previous line is equivalent to the following two statements.
            //Task<int[]> whenAllTask = Task.WhenAll(downloadTasks);
            //int[] lengths = await whenAllTask;

            int total = lengths.Sum();

            //var total = 0;
            //foreach (var url in urlList)
            //{
            //    byte[] urlContents = await GetURLContentsAsync(url);

            //    // The previous line abbreviates the following two assignment statements.
            //    // GetURLContentsAsync returns a Task<T>. At completion, the task
            //    // produces a byte array.
            //    //Task<byte[]> getContentsTask = GetURLContentsAsync(url);
            //    //byte[] urlContents = await getContentsTask;

            //    DisplayResults(url, urlContents);

            //    // Update the total.
            //    total += urlContents.Length;
            //}

            // Display the total count for all of the websites.
            resultsTextBox.Text +=
                $"\r\n\r\nTotal bytes returned:  {total}\r\n";
        }

        private List<string> SetUpURLList()
        {
            List<string> urls = new List<string>
            {
                "https://msdn.microsoft.com",
                "https://msdn.microsoft.com/library/windows/apps/br211380.aspx",
                "https://msdn.microsoft.com/library/hh290136.aspx",
                "https://msdn.microsoft.com/library/ee256749.aspx",
                "https://msdn.microsoft.com/library/hh290138.aspx",
                "https://msdn.microsoft.com/library/hh290140.aspx",
                "https://msdn.microsoft.com/library/dd470362.aspx",
                "https://msdn.microsoft.com/library/aa578028.aspx",
                "https://msdn.microsoft.com/library/ms404677.aspx",
                "https://msdn.microsoft.com/library/ff730837.aspx"
            };
            return urls;
        }

        // The actions from the foreach loop are moved to this async method.
        private async Task<int> ProcessURLAsync(string url)
        {
            var byteArray = await GetURLContentsAsync(url);
            DisplayResults(url, byteArray);
            return byteArray.Length;
        }

        private async Task<byte[]> GetURLContentsAsync(string url)
        {
            // The downloaded resource ends up in the variable named content.
            var content = new MemoryStream();

            // Initialize an HttpWebRequest for the current URL.
            var webReq = (HttpWebRequest)WebRequest.Create(url);

            // Send the request to the Internet resource and wait for
            // the response.
            using (WebResponse response = await webReq.GetResponseAsync())
            {
                // Get the data stream that is associated with the specified url.
                using (Stream responseStream = response.GetResponseStream())
                {
                    await responseStream.CopyToAsync(content);
                }
            }

            // Return the result as a byte array.
            return content.ToArray();

        }

        private void DisplayResults(string url, byte[] content)
        {
            // Display the length of each website. The string format
            // is designed to be used with a monospaced font, such as
            // Lucida Console or Global Monospace.
            var bytes = content.Length;
            // Strip off the "https://".
            var displayURL = url.Replace("https://", "");
            resultsTextBox.Text += $"\n{displayURL,-58} {bytes,8}";
        }
    }
}
```

## <a name="example"></a><span data-ttu-id="af12a-159">示例</span><span class="sxs-lookup"><span data-stu-id="af12a-159">Example</span></span>

<span data-ttu-id="af12a-160">以下代码演示使用 `HttpClient.GetByteArrayAsync` 方法从 Web 下载内容的项目的扩展。</span><span class="sxs-lookup"><span data-stu-id="af12a-160">The following code shows the extensions to the project that uses method `HttpClient.GetByteArrayAsync` to download content from the web.</span></span>

```csharp
// Add the following using directives, and add a reference for System.Net.Http.
using System.Net.Http;
using System.IO;
using System.Net;

namespace AsyncExampleWPF_HttpClient_WhenAll
{
    public partial class MainWindow : Window
    {
        public MainWindow()
        {
            InitializeComponent();
        }

        private async void startButton_Click(object sender, RoutedEventArgs e)
        {
            resultsTextBox.Clear();

            // One-step async call.
            await SumPageSizesAsync();

            // Two-step async call.
            //Task sumTask = SumPageSizesAsync();
            //await sumTask;

            resultsTextBox.Text += "\r\nControl returned to startButton_Click.\r\n";
        }

        private async Task SumPageSizesAsync()
        {
            // Make a list of web addresses.
            List<string> urlList = SetUpURLList();

            // Declare an HttpClient object and increase the buffer size. The
            // default buffer size is 65,536.
            HttpClient client = new HttpClient() { MaxResponseContentBufferSize = 1000000 };

            // Create a query.
            IEnumerable<Task<int>> downloadTasksQuery =
                from url in urlList select ProcessURLAsync(url, client);

            // Use ToArray to execute the query and start the download tasks.
            Task<int>[] downloadTasks = downloadTasksQuery.ToArray();

            // You can do other work here before awaiting.

            // Await the completion of all the running tasks.
            int[] lengths = await Task.WhenAll(downloadTasks);

            //// The previous line is equivalent to the following two statements.
            //Task<int[]> whenAllTask = Task.WhenAll(downloadTasks);
            //int[] lengths = await whenAllTask;

            int total = lengths.Sum();

            //var total = 0;
            //foreach (var url in urlList)
            //{
            //    // GetByteArrayAsync returns a Task<T>. At completion, the task
            //    // produces a byte array.
            //    byte[] urlContent = await client.GetByteArrayAsync(url);

            //    // The previous line abbreviates the following two assignment
            //    // statements.
            //    Task<byte[]> getContentTask = client.GetByteArrayAsync(url);
            //    byte[] urlContent = await getContentTask;

            //    DisplayResults(url, urlContent);

            //    // Update the total.
            //    total += urlContent.Length;
            //}

            // Display the total count for all of the web addresses.
            resultsTextBox.Text +=
                $"\r\n\r\nTotal bytes returned:  {total}\r\n";
        }

        private List<string> SetUpURLList()
        {
            List<string> urls = new List<string>
            {
                "https://msdn.microsoft.com",
                "https://msdn.microsoft.com/library/hh290136.aspx",
                "https://msdn.microsoft.com/library/ee256749.aspx",
                "https://msdn.microsoft.com/library/hh290138.aspx",
                "https://msdn.microsoft.com/library/hh290140.aspx",
                "https://msdn.microsoft.com/library/dd470362.aspx",
                "https://msdn.microsoft.com/library/aa578028.aspx",
                "https://msdn.microsoft.com/library/ms404677.aspx",
                "https://msdn.microsoft.com/library/ff730837.aspx"
            };
            return urls;
        }

        // The actions from the foreach loop are moved to this async method.
        async Task<int> ProcessURLAsync(string url, HttpClient client)
        {
            byte[] byteArray = await client.GetByteArrayAsync(url);
            DisplayResults(url, byteArray);
            return byteArray.Length;
        }

        private void DisplayResults(string url, byte[] content)
        {
            // Display the length of each web site. The string format
            // is designed to be used with a monospaced font, such as
            // Lucida Console or Global Monospace.
            var bytes = content.Length;
            // Strip off the "https://".
            var displayURL = url.Replace("https://", "");
            resultsTextBox.Text += $"\n{displayURL,-58} {bytes,8}";
        }
    }
}
```

## <a name="see-also"></a><span data-ttu-id="af12a-161">另请参阅</span><span class="sxs-lookup"><span data-stu-id="af12a-161">See also</span></span>

- <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>
- [<span data-ttu-id="af12a-162">演练：使用 Async 和 Await 访问 Web (C#)</span><span class="sxs-lookup"><span data-stu-id="af12a-162">Walkthrough: Accessing the Web by Using async and await (C#)</span></span>](./walkthrough-accessing-the-web-by-using-async-and-await.md)
