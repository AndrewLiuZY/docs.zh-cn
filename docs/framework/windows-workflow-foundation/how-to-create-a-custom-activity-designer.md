---
title: 如何：创建自定义活动设计器
description: 本文介绍如何创建一个工作流基础自定义活动设计器，该设计器具有放置区，可在其中放置任意活动。
ms.date: 03/30/2017
ms.assetid: 2f3aade6-facc-44ef-9657-a407ef8b9b31
ms.openlocfilehash: 015efd1e482e2b531d28b9caec411c76116c9653
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/15/2020
ms.locfileid: "83419780"
---
# <a name="how-to-create-a-custom-activity-designer"></a><span data-ttu-id="3212c-103">如何：创建自定义活动设计器</span><span class="sxs-lookup"><span data-stu-id="3212c-103">How to: Create a Custom Activity Designer</span></span>

<span data-ttu-id="3212c-104">通常实现自定义活动设计器，以便其相关活动可与其他活动（这些活动的设计器可与它们一起放置到设计图面上）组合在一起。</span><span class="sxs-lookup"><span data-stu-id="3212c-104">Custom activity designers are typically implemented so that their associated activities are composable with other activities whose designers can be dropped on to the design surface with them.</span></span> <span data-ttu-id="3212c-105">此功能要求自定义活动设计器提供一个可放置任意活动的 "放置区"，以及用于管理设计图面上生成的元素集合的方法。</span><span class="sxs-lookup"><span data-stu-id="3212c-105">This functionality requires that a custom activity designer provide a "drop zone" where an arbitrary activity can be placed and also the means to manage the resulting collection of elements on the design surface.</span></span> <span data-ttu-id="3212c-106">本主题介绍如何创建一个包含上述放置区的自定义活动设计器，以及如何创建一个可提供管理设计器元素集合所需的编辑功能的自定义活动设计器。</span><span class="sxs-lookup"><span data-stu-id="3212c-106">This topic describes how to create a custom activity designer that contains such a drop zone and how to create a custom activity designer that provides that editing functionality needed to manage the collection of designer elements.</span></span>

<span data-ttu-id="3212c-107">自定义活动设计器通常继承自 <xref:System.Activities.Presentation.ActivityDesigner>，后者是任何无特定设计器的活动的默认基活动设计器类型。</span><span class="sxs-lookup"><span data-stu-id="3212c-107">Custom activity designers typically inherit from <xref:System.Activities.Presentation.ActivityDesigner> which is the default base activity designer type for any activities without a specific designer.</span></span> <span data-ttu-id="3212c-108">此类型提供与属性网格交互以及配置管理颜色和图标等基本方面的设计时体验。</span><span class="sxs-lookup"><span data-stu-id="3212c-108">This type provides the design-time experience of interacting with the property grid and configuring basic aspects such as managing colors and icons.</span></span>

<span data-ttu-id="3212c-109"><xref:System.Activities.Presentation.ActivityDesigner> 采用两个帮助器控件，即 <xref:System.Activities.Presentation.WorkflowItemPresenter> 和 <xref:System.Activities.Presentation.WorkflowItemsPresenter>，以便更易于开发自定义活动设计器。</span><span class="sxs-lookup"><span data-stu-id="3212c-109"><xref:System.Activities.Presentation.ActivityDesigner> uses two helper controls, <xref:System.Activities.Presentation.WorkflowItemPresenter> and <xref:System.Activities.Presentation.WorkflowItemsPresenter> to make it easier to develop custom activity designers.</span></span> <span data-ttu-id="3212c-110">这两个控件处理常用功能，例如，拖放子元素，删除、选择和添加这些子元素。</span><span class="sxs-lookup"><span data-stu-id="3212c-110">They handle common functionality like dragging and dropping of child elements, deletion, selection, and addition of those child elements.</span></span> <span data-ttu-id="3212c-111"><xref:System.Activities.Presentation.WorkflowItemPresenter>允许内部的单个子 UI 元素（提供 "放置区域"），而 <xref:System.Activities.Presentation.WorkflowItemsPresenter> 可以提供支持多个 UI 元素，包括排序、移动、删除和添加子元素等附加功能。</span><span class="sxs-lookup"><span data-stu-id="3212c-111">The <xref:System.Activities.Presentation.WorkflowItemPresenter> allows a single child UI element inside, providing the "drop zone", it while the <xref:System.Activities.Presentation.WorkflowItemsPresenter> can provide support multiple UI elements, including additional functionality like the ordering, moving, deleting, and adding of child elements.</span></span>

<span data-ttu-id="3212c-112">在实现自定义活动设计器的过程中，需要突出显示的情景的其他关键部分考虑到，使用 WPF 数据绑定将视觉对象编辑绑定到在设计器中编辑的内容的内存中存储的实例。</span><span class="sxs-lookup"><span data-stu-id="3212c-112">The other key part of the story that needs highlighting in the implementation of a custom activity designer concerns the way in which the visual edits are bound using WPF data binding to the instance stored in memory of what we are editing in the designer.</span></span> <span data-ttu-id="3212c-113">这是通过模型项树实现的，它还负责启用更改通知和跟踪事件（例如状态的更改）。</span><span class="sxs-lookup"><span data-stu-id="3212c-113">This is accomplished by the Model Item tree, which is also responsible for enabling change notification and the tracking of events like changes in states.</span></span>

<span data-ttu-id="3212c-114">本主题概述了两个过程。</span><span class="sxs-lookup"><span data-stu-id="3212c-114">This topic outlines two procedures.</span></span>

1. <span data-ttu-id="3212c-115">第一个过程介绍如何使用 <xref:System.Activities.Presentation.WorkflowItemPresenter> 创建一个自定义活动设计器，用于提供接收其他活动的放置区。</span><span class="sxs-lookup"><span data-stu-id="3212c-115">The first procedure describes how to create a custom activity designer with a <xref:System.Activities.Presentation.WorkflowItemPresenter> that provides the drop zone that receives other activities.</span></span> <span data-ttu-id="3212c-116">此过程基于[自定义复合设计器—工作流项呈现器](./samples/custom-composite-designers-workflow-item-presenter.md)示例。</span><span class="sxs-lookup"><span data-stu-id="3212c-116">This procedure is based on the [Custom Composite Designers - Workflow Item Presenter](./samples/custom-composite-designers-workflow-item-presenter.md) sample.</span></span>

2. <span data-ttu-id="3212c-117">第二个过程介绍如何使用 <xref:System.Activities.Presentation.WorkflowItemsPresenter> 创建一个自定义活动设计器，用于提供编辑包含的元素的集合所需的功能。</span><span class="sxs-lookup"><span data-stu-id="3212c-117">The second procedure describes how to create a custom activity designer with a <xref:System.Activities.Presentation.WorkflowItemsPresenter> that provides the functionality needed to edit of a collection of contained elements.</span></span> <span data-ttu-id="3212c-118">此过程基于[自定义复合设计器—工作流项演示者](./samples/custom-composite-designers-workflow-items-presenter.md)示例。</span><span class="sxs-lookup"><span data-stu-id="3212c-118">This procedure is based on the [Custom Composite Designers - Workflow Items Presenter](./samples/custom-composite-designers-workflow-items-presenter.md) sample.</span></span>

## <a name="to-create-a-custom-activity-designer-with-a-drop-zone-using-workflowitempresenter"></a><span data-ttu-id="3212c-119">使用 WorkflowItemPresenter 创建带有放置区的自定义活动设计器</span><span class="sxs-lookup"><span data-stu-id="3212c-119">To create a custom activity designer with a drop zone using WorkflowItemPresenter</span></span>

1. <span data-ttu-id="3212c-120">启动 Visual Studio 2010。</span><span class="sxs-lookup"><span data-stu-id="3212c-120">Start Visual Studio 2010.</span></span>

2. <span data-ttu-id="3212c-121">在 "**文件**" 菜单上，指向 "**新建**"，然后选择 "**项目 ...**"。</span><span class="sxs-lookup"><span data-stu-id="3212c-121">On the **File** menu, point to **New**, and then select **Project…**.</span></span>

     <span data-ttu-id="3212c-122">**“新建项目”** 对话框随即打开。</span><span class="sxs-lookup"><span data-stu-id="3212c-122">The **New Project** dialog box opens.</span></span>

3. <span data-ttu-id="3212c-123">在 "**已安装的模板**" 窗格中，从首选语言类别中选择 " **Windows** "。</span><span class="sxs-lookup"><span data-stu-id="3212c-123">In the **Installed Templates** pane, select **Windows** from your preferred language category.</span></span>

4. <span data-ttu-id="3212c-124">在 "**模板**" 窗格中，选择 " **WPF 应用程序**"。</span><span class="sxs-lookup"><span data-stu-id="3212c-124">In the **Templates** pane, select **WPF Application**.</span></span>

5. <span data-ttu-id="3212c-125">在 "**名称**" 框中，输入 `UsingWorkflowItemPresenter` 。</span><span class="sxs-lookup"><span data-stu-id="3212c-125">In the **Name** box, enter `UsingWorkflowItemPresenter`.</span></span>

6. <span data-ttu-id="3212c-126">在 "**位置**" 框中，输入要保存项目的目录，或者单击 "**浏览**" 导航到该目录。</span><span class="sxs-lookup"><span data-stu-id="3212c-126">In the **Location** box, enter the directory in which you want to save your project, or click **Browse** to navigate to it.</span></span>

7. <span data-ttu-id="3212c-127">在 "**解决方案**" 框中，接受默认值。</span><span class="sxs-lookup"><span data-stu-id="3212c-127">In the **Solution** box, accept the default value.</span></span>

8. <span data-ttu-id="3212c-128">单击“确定” 。</span><span class="sxs-lookup"><span data-stu-id="3212c-128">Click **OK**.</span></span>

9. <span data-ttu-id="3212c-129">右键单击**解决方案资源管理器**中*的右击 mainwindows.xaml*文件，在 " **Microsoft Visual Studio** " 对话框中选择 "**删除**并确认 **" 确定 "** 。</span><span class="sxs-lookup"><span data-stu-id="3212c-129">Right-click the *MainWindows.xaml* file in the **Solution Explorer**, select **Delete** and confirm **OK** in the **Microsoft Visual Studio** dialog box.</span></span>

10. <span data-ttu-id="3212c-130">在**解决方案资源管理器**中右键单击 "右击 usingworkflowitempresenter" 项目，依次选择 "**添加**"、"**新建项 ...** "</span><span class="sxs-lookup"><span data-stu-id="3212c-130">Right-click the UsingWorkflowItemPresenter project in **Solution Explorer**, select **Add**, then **New Item…**</span></span> <span data-ttu-id="3212c-131">若要打开 "**添加新项**" 对话框，请从左侧的 "**已安装的模板**" 部分中选择 " **WPF** " 类别。</span><span class="sxs-lookup"><span data-stu-id="3212c-131">to bring up the **Add New Item** dialog and select the **WPF** category from the **Installed Templates** section on the left.</span></span>

11. <span data-ttu-id="3212c-132">选择 "**窗口（WPF）** " 模板，将其命名为 `RehostingWFDesigner` ，然后单击 "**添加**"。</span><span class="sxs-lookup"><span data-stu-id="3212c-132">Select the  **Window (WPF)** template, name it `RehostingWFDesigner`, and click **Add**.</span></span>

12. <span data-ttu-id="3212c-133">打开*rehostingwfdesigner.xaml*文件并将以下代码粘贴到其中以定义应用程序的 UI：</span><span class="sxs-lookup"><span data-stu-id="3212c-133">Open the *RehostingWFDesigner.xaml* file and paste the following code into it to define the UI for the application:</span></span>

    ```xaml
    <Window x:Class=" UsingWorkflowItemPresenter.RehostingWFDesigner"
            xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
            xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
            xmlns:sapt="clr-namespace:System.Activities.Presentation.Toolbox;assembly=System.Activities.Presentation"
            xmlns:sys="clr-namespace:System;assembly=mscorlib"
            Title="Window1" Height="600" Width="900">
        <Window.Resources>
            <sys:String x:Key="AssemblyName">System.Activities, Version=4.0.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35</sys:String>
        </Window.Resources>
        <Grid>
            <Grid.ColumnDefinitions>
                <ColumnDefinition Width="2*"/>
                <ColumnDefinition Width="7*"/>
                <ColumnDefinition Width="3*"/>
            </Grid.ColumnDefinitions>
            <Border Grid.Column="0">
                <sapt:ToolboxControl Name="Toolbox">
                    <sapt:ToolboxCategory CategoryName="Basic">
                        <sapt:ToolboxItemWrapper AssemblyName="{StaticResource AssemblyName}" >
                            <sapt:ToolboxItemWrapper.ToolName>
                                System.Activities.Statements.Sequence
                            </sapt:ToolboxItemWrapper.ToolName>
                           </sapt:ToolboxItemWrapper>
                        <sapt:ToolboxItemWrapper  AssemblyName="{StaticResource AssemblyName}">
                            <sapt:ToolboxItemWrapper.ToolName>
                                System.Activities.Statements.WriteLine
                            </sapt:ToolboxItemWrapper.ToolName>

                        </sapt:ToolboxItemWrapper>
                        <sapt:ToolboxItemWrapper  AssemblyName="{StaticResource AssemblyName}">
                            <sapt:ToolboxItemWrapper.ToolName>
                                System.Activities.Statements.If
                            </sapt:ToolboxItemWrapper.ToolName>

                        </sapt:ToolboxItemWrapper>
                        <sapt:ToolboxItemWrapper  AssemblyName="{StaticResource AssemblyName}">
                            <sapt:ToolboxItemWrapper.ToolName>
                                System.Activities.Statements.While
                            </sapt:ToolboxItemWrapper.ToolName>

                        </sapt:ToolboxItemWrapper>
                    </sapt:ToolboxCategory>
                </sapt:ToolboxControl>
            </Border>
            <Border Grid.Column="1" Name="DesignerBorder"/>
            <Border Grid.Column="2" Name="PropertyBorder"/>
        </Grid>
    </Window>
    ```

13. <span data-ttu-id="3212c-134">若要将活动设计器与活动类型相关联，您必须向元数据存储注册活动设计器。</span><span class="sxs-lookup"><span data-stu-id="3212c-134">To associate an activity designer with an activity type, you must register that activity designer with the metadata store.</span></span> <span data-ttu-id="3212c-135">为此，请将 `RegisterMetadata` 方法添加到 `RehostingWFDesigner` 类中。</span><span class="sxs-lookup"><span data-stu-id="3212c-135">To do this, add the `RegisterMetadata` method to the `RehostingWFDesigner` class.</span></span> <span data-ttu-id="3212c-136">在 `RegisterMetadata` 方法的范围内，创建一个 <xref:System.Activities.Presentation.Metadata.AttributeTableBuilder> 对象，并调用 <xref:System.Activities.Presentation.Metadata.AttributeTableBuilder.AddCustomAttributes%2A> 方法以向其添加特性。</span><span class="sxs-lookup"><span data-stu-id="3212c-136">Within the scope of the  `RegisterMetadata` method, create an <xref:System.Activities.Presentation.Metadata.AttributeTableBuilder> object and call the <xref:System.Activities.Presentation.Metadata.AttributeTableBuilder.AddCustomAttributes%2A> method to add the attributes to it.</span></span> <span data-ttu-id="3212c-137">调用 <xref:System.Activities.Presentation.Metadata.MetadataStore.AddAttributeTable%2A> 方法以向元数据存储添加 <xref:System.Activities.Presentation.Metadata.AttributeTable>。</span><span class="sxs-lookup"><span data-stu-id="3212c-137">Call the <xref:System.Activities.Presentation.Metadata.MetadataStore.AddAttributeTable%2A> method to add the <xref:System.Activities.Presentation.Metadata.AttributeTable> to the metadata store.</span></span> <span data-ttu-id="3212c-138">下面的代码包含设计器的重新承载逻辑。</span><span class="sxs-lookup"><span data-stu-id="3212c-138">The following code contains the rehosting logic for the designer.</span></span> <span data-ttu-id="3212c-139">它注册元数据，将 `SimpleNativeActivity` 放入工具箱中，并创建工作流。</span><span class="sxs-lookup"><span data-stu-id="3212c-139">It registers the metadata, puts the `SimpleNativeActivity` into the toolbox, and creates the workflow.</span></span> <span data-ttu-id="3212c-140">将此代码放入*RehostingWFDesigner.xaml.cs*文件。</span><span class="sxs-lookup"><span data-stu-id="3212c-140">Put this code into the *RehostingWFDesigner.xaml.cs* file.</span></span>

    ```csharp
    using System;
    using System.Activities.Core.Presentation;
    using System.Activities.Presentation;
    using System.Activities.Presentation.Metadata;
    using System.Activities.Presentation.Toolbox;
    using System.Activities.Statements;
    using System.ComponentModel;
    using System.Windows;

    namespace UsingWorkflowItemPresenter
    {
        // Interaction logic for RehostingWFDesigner.xaml
        public partial class RehostingWFDesigner
        {
            public RehostingWFDesigner()
            {
                InitializeComponent();
            }

            protected override void OnInitialized(EventArgs e)
            {
                base.OnInitialized(e);
                // Register metadata.
                (new DesignerMetadata()).Register();
                RegisterCustomMetadata();
                // Add custom activity to toolbox.
                Toolbox.Categories.Add(new ToolboxCategory("Custom activities"));
                Toolbox.Categories[1].Add(new ToolboxItemWrapper(typeof(SimpleNativeActivity)));

                // Create the workflow designer.
                var wd = new WorkflowDesigner();
                wd.Load(new Sequence());
                DesignerBorder.Child = wd.View;
                PropertyBorder.Child = wd.PropertyInspectorView;

            }

            void RegisterCustomMetadata()
            {
                var builder = new AttributeTableBuilder();
                builder.AddCustomAttributes(typeof(SimpleNativeActivity), new DesignerAttribute(typeof(SimpleNativeDesigner)));
                MetadataStore.AddAttributeTable(builder.CreateTable());
            }
        }
    }
    ```

14. <span data-ttu-id="3212c-141">在解决方案资源管理器中右键单击 "引用" 目录，然后选择 "**添加引用 ...** "</span><span class="sxs-lookup"><span data-stu-id="3212c-141">Right-click the References directory in Solution Explorer and select **Add Reference …**</span></span> <span data-ttu-id="3212c-142">显示 "**添加引用**" 对话框。</span><span class="sxs-lookup"><span data-stu-id="3212c-142">to bring up the **Add Reference** dialog.</span></span>

15. <span data-ttu-id="3212c-143">单击 " **.net** " 选项卡，找到名为 " **system.web**" 的程序集，选择它并单击 **"确定"**。</span><span class="sxs-lookup"><span data-stu-id="3212c-143">Click the **.NET** tab, locate the assembly named **System.Activities.Core.Presentation**, select it and click **OK**.</span></span>

16. <span data-ttu-id="3212c-144">使用相同的过程，添加对下列程序集的引用：</span><span class="sxs-lookup"><span data-stu-id="3212c-144">Using the same procedure, add references to the following assemblies:</span></span>

    1. <span data-ttu-id="3212c-145">System.Data.DataSetExtensions.dll</span><span class="sxs-lookup"><span data-stu-id="3212c-145">System.Data.DataSetExtensions.dll</span></span>

    2. <span data-ttu-id="3212c-146">System.Activities.Presentation.dll</span><span class="sxs-lookup"><span data-stu-id="3212c-146">System.Activities.Presentation.dll</span></span>

    3. <span data-ttu-id="3212c-147">System.ServiceModel.Activities.dll</span><span class="sxs-lookup"><span data-stu-id="3212c-147">System.ServiceModel.Activities.dll</span></span>

17. <span data-ttu-id="3212c-148">打开*app.xaml*文件，将 system.windows.application.startupuri 的值更改为 "rehostingwfdesigner.xaml"。</span><span class="sxs-lookup"><span data-stu-id="3212c-148">Open the *App.xaml* file and change the value of the StartUpUri to "RehostingWFDesigner.xaml".</span></span>

18. <span data-ttu-id="3212c-149">在**解决方案资源管理器**中右键单击 "右击 usingworkflowitempresenter" 项目，依次选择 "**添加**"、"**新建项 ...** "</span><span class="sxs-lookup"><span data-stu-id="3212c-149">Right-click the UsingWorkflowItemPresenter project in **Solution Explorer**, select **Add**, then **New Item…**</span></span> <span data-ttu-id="3212c-150">若要打开 "**添加新项**" 对话框，请选择**左侧的**"**已安装的模板**" 部分。</span><span class="sxs-lookup"><span data-stu-id="3212c-150">to bring up the **Add New Item** dialog and select the **Workflow** category form the **Installed Templates** section on the left.</span></span>

19. <span data-ttu-id="3212c-151">选择 "**活动设计器**" 模板，将其命名为 `SimpleNativeDesigner` ，然后单击 "**添加**"。</span><span class="sxs-lookup"><span data-stu-id="3212c-151">Select the **Activity Designer** template, name it `SimpleNativeDesigner`, and click **Add**.</span></span>

20. <span data-ttu-id="3212c-152">打开*SimpleNativeDesigner*文件并将以下代码粘贴到其中。</span><span class="sxs-lookup"><span data-stu-id="3212c-152">Open the *SimpleNativeDesigner.xaml* file and paste the following code into it.</span></span> <span data-ttu-id="3212c-153">请注意，此代码使用 <xref:System.Activities.Presentation.ActivityDesigner> 作为根元素，并演示如何使用绑定将 <xref:System.Activities.Presentation.WorkflowItemPresenter> 集成到设计器中，以便可以在复合活动设计器中显示子类型。</span><span class="sxs-lookup"><span data-stu-id="3212c-153">Note this code uses <xref:System.Activities.Presentation.ActivityDesigner> as your root element and shows how binding is used to integrate <xref:System.Activities.Presentation.WorkflowItemPresenter> into your designer so a child type can be displayed in your composite activity designer.</span></span>

    > [!NOTE]
    > <span data-ttu-id="3212c-154"><xref:System.Activities.Presentation.ActivityDesigner> 的架构只允许向自定义活动设计器定义中添加一个子元素；不过，这个元素可以是 `StackPanel`、`Grid` 或某些其他复合 UI 元素。</span><span class="sxs-lookup"><span data-stu-id="3212c-154">The schema for <xref:System.Activities.Presentation.ActivityDesigner> allows the addition of only one child element to your custom activity designer definition; however, this element could be a `StackPanel`, `Grid`, or some other composite UI element.</span></span>

    ```xaml
    <sap:ActivityDesigner x:Class=" UsingWorkflowItemPresenter.SimpleNativeDesigner"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        xmlns:sap="clr-namespace:System.Activities.Presentation;assembly=System.Activities.Presentation"
        xmlns:sapv="clr-namespace:System.Activities.Presentation.View;assembly=System.Activities.Presentation">
        <sap:ActivityDesigner.Resources>
            <DataTemplate x:Key="Collapsed">
                <StackPanel>
                    <TextBlock>This is the collapsed view</TextBlock>
                </StackPanel>
            </DataTemplate>
            <DataTemplate x:Key="Expanded">
                <StackPanel>
                    <TextBlock>Custom Text</TextBlock>
                    <sap:WorkflowItemPresenter Item="{Binding Path=ModelItem.Body, Mode=TwoWay}"
                                            HintText="Please drop an activity here" />
                </StackPanel>
            </DataTemplate>
            <Style x:Key="ExpandOrCollapsedStyle" TargetType="{x:Type ContentPresenter}">
                <Setter Property="ContentTemplate" Value="{DynamicResource Collapsed}"/>
                <Style.Triggers>
                    <DataTrigger Binding="{Binding Path=ShowExpanded}" Value="true">
                        <Setter Property="ContentTemplate" Value="{DynamicResource Expanded}"/>
                    </DataTrigger>
                </Style.Triggers>
            </Style>
        </sap:ActivityDesigner.Resources>
        <Grid>
            <ContentPresenter Style="{DynamicResource ExpandOrCollapsedStyle}" Content="{Binding}" />
        </Grid>
    </sap:ActivityDesigner>
    ```

21. <span data-ttu-id="3212c-155">在**解决方案资源管理器**中右键单击 "右击 usingworkflowitempresenter" 项目，依次选择 "**添加**"、"**新建项 ...** "</span><span class="sxs-lookup"><span data-stu-id="3212c-155">Right-click the UsingWorkflowItemPresenter project in **Solution Explorer**, select **Add**, then **New Item…**</span></span> <span data-ttu-id="3212c-156">若要打开 "**添加新项**" 对话框，请选择**左侧的**"**已安装的模板**" 部分。</span><span class="sxs-lookup"><span data-stu-id="3212c-156">to bring up the **Add New Item** dialog and select the **Workflow** category form the **Installed Templates** section on the left.</span></span>

22. <span data-ttu-id="3212c-157">选择 "**代码" 活动**模板，将其命名为 `SimpleNativeActivity` ，然后单击 "**添加**"。</span><span class="sxs-lookup"><span data-stu-id="3212c-157">Select the  **Code Activity** template, name it `SimpleNativeActivity`, and click **Add**.</span></span>

23. <span data-ttu-id="3212c-158">通过在 `SimpleNativeActivity` *SimpleNativeActivity.cs*文件中输入以下代码来实现类：</span><span class="sxs-lookup"><span data-stu-id="3212c-158">Implement the `SimpleNativeActivity` class by entering the following code into the *SimpleNativeActivity.cs* file:</span></span>

    ```csharp
    using System.Activities;

    namespace UsingWorkflowItemPresenter
    {
        public sealed class SimpleNativeActivity : NativeActivity
        {
            // this property contains an activity that will be scheduled in the execute method
            // the WorkflowItemPresenter in the designer is bound to this to enable editing
            // of the value
            public Activity Body { get; set; }

            protected override void CacheMetadata(NativeActivityMetadata metadata)
            {
               metadata.AddChild(Body);
               base.CacheMetadata(metadata);

            }

            protected override void Execute(NativeActivityContext context)
            {
                context.ScheduleActivity(Body);
            }
        }
    }
    ```

24. <span data-ttu-id="3212c-159">从 "**生成**" 菜单中选择 "**生成解决方案**"。</span><span class="sxs-lookup"><span data-stu-id="3212c-159">Select **Build Solution** from the **Build** menu.</span></span>

25. <span data-ttu-id="3212c-160">从 "**调试**" 菜单中选择 "**启动（不调试**）" 以打开 "重新承载自定义设计" 窗口。</span><span class="sxs-lookup"><span data-stu-id="3212c-160">Select **Start Without Debugging** from the **Debug** menu to open the rehosted custom design window.</span></span>

### <a name="to-create-a-custom-activity-designer-using-workflowitemspresenter"></a><span data-ttu-id="3212c-161">使用 WorkflowItemsPresenter 创建自定义活动设计器</span><span class="sxs-lookup"><span data-stu-id="3212c-161">To create a custom activity designer using WorkflowItemsPresenter</span></span>

1. <span data-ttu-id="3212c-162">第二个自定义活动设计器的过程与第二个修改类似，第一种是对第二个应用程序进行命名 `UsingWorkflowItemsPresenter` 。</span><span class="sxs-lookup"><span data-stu-id="3212c-162">The procedure for the second custom activity designer is the parallels the first with a few modifications, the first of which is to name the second application `UsingWorkflowItemsPresenter`.</span></span> <span data-ttu-id="3212c-163">另外，此应用程序不会定义新的自定义活动。</span><span class="sxs-lookup"><span data-stu-id="3212c-163">Also this application does not define a new custom activity.</span></span>

2. <span data-ttu-id="3212c-164">主要区别包含在*CustomParallelDesigner*和*RehostingWFDesigner.xaml.cs*文件中。</span><span class="sxs-lookup"><span data-stu-id="3212c-164">Key differences are contained in the *CustomParallelDesigner.xaml* and *RehostingWFDesigner.xaml.cs* files.</span></span> <span data-ttu-id="3212c-165">下面是*CustomParallelDesigner*文件中用于定义 UI 的代码：</span><span class="sxs-lookup"><span data-stu-id="3212c-165">Here is the code from the *CustomParallelDesigner.xaml* file that defines the UI:</span></span>

    ```xaml
    <sap:ActivityDesigner x:Class=" UsingWorkflowItemsPresenter.CustomParallelDesigner"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        xmlns:sap="clr-namespace:System.Activities.Presentation;assembly=System.Activities.Presentation"
        xmlns:sapv="clr-namespace:System.Activities.Presentation.View;assembly=System.Activities.Presentation">
        <sap:ActivityDesigner.Resources>
            <DataTemplate x:Key="Collapsed">
                <TextBlock>This is the Collapsed View</TextBlock>
            </DataTemplate>
            <DataTemplate x:Key="Expanded">
                <StackPanel>
                    <TextBlock HorizontalAlignment="Center">This is the</TextBlock>
                    <TextBlock HorizontalAlignment="Center">extended view</TextBlock>
                    <sap:WorkflowItemsPresenter HintText="Drop Activities Here"
                                        Items="{Binding Path=ModelItem.Branches}">
                        <sap:WorkflowItemsPresenter.SpacerTemplate>
                            <DataTemplate>
                                <Ellipse Width="10" Height="10" Fill="Black"/>
                            </DataTemplate>
                        </sap:WorkflowItemsPresenter.SpacerTemplate>
                        <sap:WorkflowItemsPresenter.ItemsPanel>
                            <ItemsPanelTemplate>
                                <StackPanel Orientation="Horizontal"/>
                            </ItemsPanelTemplate>
                        </sap:WorkflowItemsPresenter.ItemsPanel>
                    </sap:WorkflowItemsPresenter>
                </StackPanel>
            </DataTemplate>
            <Style x:Key="ExpandOrCollapsedStyle" TargetType="{x:Type ContentPresenter}">
                <Setter Property="ContentTemplate" Value="{DynamicResource Collapsed}"/>
                <Style.Triggers>
                    <DataTrigger Binding="{Binding Path=ShowExpanded}" Value="true">
                        <Setter Property="ContentTemplate" Value="{DynamicResource Expanded}"/>
                    </DataTrigger>
                </Style.Triggers>
            </Style>
        </sap:ActivityDesigner.Resources>
        <Grid>
            <ContentPresenter Style="{DynamicResource ExpandOrCollapsedStyle}" Content="{Binding}"/>
        </Grid>
    </sap:ActivityDesigner>
    ```

3. <span data-ttu-id="3212c-166">下面是*RehostingWFDesigner.xaml.cs*文件中的代码，提供重新承载逻辑：</span><span class="sxs-lookup"><span data-stu-id="3212c-166">Here is the code from the *RehostingWFDesigner.xaml.cs* file that provides the rehosting logic:</span></span>

    ```csharp
    using System;
    using System.Activities.Core.Presentation;
    using System.Activities.Presentation;
    using System.Activities.Presentation.Metadata;
    using System.Activities.Statements;
    using System.ComponentModel;
    using System.Windows;

    namespaceUsingWorkflowItemsPresenter
    {
        public partial class RehostingWfDesigner : Window
        {
            public RehostingWfDesigner()
            {
                InitializeComponent();
            }

            protected override void OnInitialized(EventArgs e)
            {
                base.OnInitialized(e);
                // Register metadata.
                (new DesignerMetadata()).Register();
                RegisterCustomMetadata();

                // Create the workflow designer.
                var wd = new WorkflowDesigner();
                wd.Load(new Sequence());
                DesignerBorder.Child = wd.View;
                PropertyBorder.Child = wd.PropertyInspectorView;

            }

            void RegisterCustomMetadata()
            {
                var builder = new AttributeTableBuilder();
                builder.AddCustomAttributes(typeof(Parallel), new DesignerAttribute(typeof(CustomParallelDesigner)));
                MetadataStore.AddAttributeTable(builder.CreateTable());
            }
        }
    }
    ```

## <a name="see-also"></a><span data-ttu-id="3212c-167">另请参阅</span><span class="sxs-lookup"><span data-stu-id="3212c-167">See also</span></span>

- <xref:System.Activities.Presentation.ActivityDesigner>
- <xref:System.Activities.Presentation.WorkflowItemPresenter>
- <xref:System.Activities.Presentation.WorkflowItemsPresenter>
- <xref:System.Activities.Presentation.WorkflowViewElement>
- <xref:System.Activities.Presentation.Model.ModelItem>
- [<span data-ttu-id="3212c-168">自定义工作流设计体验</span><span class="sxs-lookup"><span data-stu-id="3212c-168">Customizing the Workflow Design Experience</span></span>](customizing-the-workflow-design-experience.md)
