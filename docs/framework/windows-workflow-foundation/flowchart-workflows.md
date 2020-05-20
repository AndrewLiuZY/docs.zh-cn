---
title: 流程图工作流
description: 本文介绍流程图活动，该活动通常用于实现 Workflow Foundation 中的非顺序工作流。
ms.date: 03/30/2017
ms.assetid: b0a3475c-d22f-49eb-8912-973c960aebf5
ms.openlocfilehash: ce0661653a1d50b3f7264246b810faabbd12bf5f
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/15/2020
ms.locfileid: "83419910"
---
# <a name="flowchart-workflows"></a><span data-ttu-id="51b49-103">流程图工作流</span><span class="sxs-lookup"><span data-stu-id="51b49-103">Flowchart Workflows</span></span>

<span data-ttu-id="51b49-104">流程图是用于设计程序的已知范例。</span><span class="sxs-lookup"><span data-stu-id="51b49-104">A flowchart is a well-known paradigm for designing programs.</span></span> <span data-ttu-id="51b49-105">Flowchart 活动通常用于实现非顺序工作流，但如果未使用 `FlowDecision` 节点，则也可以用于顺序工作流。</span><span class="sxs-lookup"><span data-stu-id="51b49-105">The Flowchart activity is typically used to implement non-sequential workflows, but can be used for sequential workflows if no `FlowDecision` nodes are used.</span></span>

## <a name="flowchart-workflow-structure"></a><span data-ttu-id="51b49-106">流程图工作流结构</span><span class="sxs-lookup"><span data-stu-id="51b49-106">Flowchart workflow structure</span></span>

 <span data-ttu-id="51b49-107">Flowchart 活动是一种活动，该活动包含要执行的活动集合。</span><span class="sxs-lookup"><span data-stu-id="51b49-107">A Flowchart activity is an activity that contains a collection of activities to be executed.</span></span>  <span data-ttu-id="51b49-108">流程图还包含流控制元素，如 <xref:System.Activities.Statements.FlowDecision> 和 <xref:System.Activities.Statements.FlowSwitch%601>，这些元素基于变量的值指示所包含活动之间的执行。</span><span class="sxs-lookup"><span data-stu-id="51b49-108">Flowcharts also contain flow control elements such as <xref:System.Activities.Statements.FlowDecision> and <xref:System.Activities.Statements.FlowSwitch%601> that direct execution between contained activities based on the values of variables.</span></span>

## <a name="types-of-flow-nodes"></a><span data-ttu-id="51b49-109">流节点类型</span><span class="sxs-lookup"><span data-stu-id="51b49-109">Types of flow nodes</span></span>

 <span data-ttu-id="51b49-110">根据执行元素时所需的流控制类型，使用不同的元素类型。</span><span class="sxs-lookup"><span data-stu-id="51b49-110">Different types of elements are used depending on the type of flow control required when the element executes.</span></span> <span data-ttu-id="51b49-111">流程图元素的类型包括：</span><span class="sxs-lookup"><span data-stu-id="51b49-111">Types of flowchart elements include:</span></span>

- <span data-ttu-id="51b49-112">`FlowStep` - 在流程图中建立一个执行步骤的模型。</span><span class="sxs-lookup"><span data-stu-id="51b49-112">`FlowStep` - Models one step of execution in the flowchart.</span></span>

- <span data-ttu-id="51b49-113">`FlowDecision` - 基于布尔条件建立执行分支，类似于 <xref:System.Activities.Statements.If>。</span><span class="sxs-lookup"><span data-stu-id="51b49-113">`FlowDecision` - Branches execution based on a Boolean condition, similar to <xref:System.Activities.Statements.If>.</span></span>

- <span data-ttu-id="51b49-114">`FlowSwitch` – 基于独占 Switch 建立执行分支，类似于 <xref:System.Activities.Statements.Switch%601>。</span><span class="sxs-lookup"><span data-stu-id="51b49-114">`FlowSwitch` – Branches execution based on an exclusive switch, similar to <xref:System.Activities.Statements.Switch%601>.</span></span>

<span data-ttu-id="51b49-115">每个链接都具有一个 `Action` 属性，该属性定义可用于执行子活动的 <xref:System.Activities.ActivityAction>，并且每个链接还具有一个或多个 `Next` 属性，这些属性定义当前元素完成执行后要执行的元素。</span><span class="sxs-lookup"><span data-stu-id="51b49-115">Each link has an `Action` property that defines a <xref:System.Activities.ActivityAction> that can be used to execute child activities, and one or more `Next` properties that define which element or elements to execute when the current element finishes execution.</span></span>

### <a name="creating-a-basic-activity-sequence-with-a-flowstep-node"></a><span data-ttu-id="51b49-116">使用 FlowStep 节点创建基本活动序列</span><span class="sxs-lookup"><span data-stu-id="51b49-116">Creating a basic activity sequence with a FlowStep node</span></span>

<span data-ttu-id="51b49-117">若要建立一个基本的顺序模型，在该模型中依次执行两个活动，请使用 `FlowStep` 元素。</span><span class="sxs-lookup"><span data-stu-id="51b49-117">To model a basic sequence in which two activities execute in turn, the `FlowStep` element is used.</span></span> <span data-ttu-id="51b49-118">在下面的示例中，使用了两个 `FlowStep` 元素按顺序执行两个活动。</span><span class="sxs-lookup"><span data-stu-id="51b49-118">In the following example, two `FlowStep` elements are used to execute two activities in sequence.</span></span>

```xml
<Flowchart>
  <FlowStep>
    <Assign DisplayName="Get Name">
      <Assign.To>
        <OutArgument x:TypeArguments="x:String">[result]</OutArgument>
      </Assign.To>
      <Assign.Value>
        <InArgument x:TypeArguments="x:String">["User"]</InArgument>
      </Assign.Value>
    </Assign>
    <FlowStep.Next>
      <FlowStep>
        <WriteLine Text="Hello, " & [result]/>
      </FlowStep>
    </FlowStep.Next>
  </FlowStep>
</Flowchart>
```

### <a name="creating-a-conditional-flowchart-with-a-flowdecision-node"></a><span data-ttu-id="51b49-119">使用 FlowDecision 节点创建条件流程图</span><span class="sxs-lookup"><span data-stu-id="51b49-119">Creating a conditional flowchart with a FlowDecision node</span></span>

<span data-ttu-id="51b49-120">若要在流程图工作流中建立条件流节点的模型（即，创建一个充当传统流程图的决策符号的链接），请使用 <xref:System.Activities.Statements.FlowDecision> 节点。</span><span class="sxs-lookup"><span data-stu-id="51b49-120">To model a conditional flow node in a flowchart workflow (that is, to create a link that functions as a traditional flowchart's decision symbol), a <xref:System.Activities.Statements.FlowDecision> node is used.</span></span> <span data-ttu-id="51b49-121">该节点的 <xref:System.Activities.Statements.FlowDecision.Condition%2A> 属性设置为定义条件的表达式，并且 <xref:System.Activities.Statements.FlowDecision.True%2A> 和 <xref:System.Activities.Statements.FlowDecision.False%2A> 属性设置为表达式计算结果为 <xref:System.Activities.Statements.FlowNode> 或 `true` 时要执行的 `false` 实例。</span><span class="sxs-lookup"><span data-stu-id="51b49-121">The <xref:System.Activities.Statements.FlowDecision.Condition%2A> property of the node is set to an expression that defines the condition, and the <xref:System.Activities.Statements.FlowDecision.True%2A> and <xref:System.Activities.Statements.FlowDecision.False%2A> properties are set to <xref:System.Activities.Statements.FlowNode> instances to be executed if the expression evaluates to `true` or `false`.</span></span> <span data-ttu-id="51b49-122">下面的示例演示如何定义使用 <xref:System.Activities.Statements.FlowDecision> 节点的工作流。</span><span class="sxs-lookup"><span data-stu-id="51b49-122">The following example shows how to define a workflow that uses a <xref:System.Activities.Statements.FlowDecision> node.</span></span>

```xml
<Flowchart>
  <FlowStep>
    <Read Result="[s]"/>
    <FlowStep.Next>
      <FlowDecision>
        <IsEmpty Input="[s]" />
        <FlowDecision.True>
          <FlowStep>
            <Write Text="Empty"/>
          </FlowStep>
        </FlowDecision.True>
        <FlowDecision.False>
          <FlowStep>
            <Write Text="Non-Empty"/>
          </FlowStep>
        </FlowDecision.False>
      </FlowDecision>
    </FlowStep.Next>
  </FlowStep>
</Flowchart>
```

### <a name="creating-an-exclusive-switch-with-a-flowswitch-node"></a><span data-ttu-id="51b49-123">使用 FlowSwitch 节点创建独占开关</span><span class="sxs-lookup"><span data-stu-id="51b49-123">Creating an exclusive switch with a FlowSwitch node</span></span>

<span data-ttu-id="51b49-124">若要建立某个流程图的模型，在该流程图中基于匹配的值选择了一个独占路径，请使用 <xref:System.Activities.Statements.FlowSwitch%601> 节点。</span><span class="sxs-lookup"><span data-stu-id="51b49-124">To model a flowchart in which one exclusive path is selected based on a matching value, the <xref:System.Activities.Statements.FlowSwitch%601> node is used.</span></span> <span data-ttu-id="51b49-125"><xref:System.Activities.Statements.FlowSwitch%601.Expression%2A> 属性设置为 <xref:System.Activities.Activity%601>，其中类型参数 <xref:System.Object> 定义匹配选择的值。</span><span class="sxs-lookup"><span data-stu-id="51b49-125">The <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A> property is set to a <xref:System.Activities.Activity%601> with a type parameter of <xref:System.Object> that defines the value to match choices against.</span></span> <span data-ttu-id="51b49-126"><xref:System.Activities.Statements.FlowSwitch%601.Cases%2A> 属性定义要匹配条件表达式的键和 <xref:System.Activities.Statements.FlowNode> 对象的字典，以及一组 <xref:System.Activities.Statements.FlowNode> 对象，这些对象定义在给定情况与条件表达式匹配时的执行流方式。</span><span class="sxs-lookup"><span data-stu-id="51b49-126">The <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A> property defines a dictionary of keys and <xref:System.Activities.Statements.FlowNode> objects to match against the conditional expression, and a set of <xref:System.Activities.Statements.FlowNode> objects that define how execution should flow if the given case matches the conditional expression.</span></span> <span data-ttu-id="51b49-127"><xref:System.Activities.Statements.FlowSwitch%601> 还定义一个 <xref:System.Activities.Statements.FlowSwitch%601.Default%2A> 属性，该属性定义没有情况与条件表达式匹配时的执行流方式。</span><span class="sxs-lookup"><span data-stu-id="51b49-127">The <xref:System.Activities.Statements.FlowSwitch%601> also defines a <xref:System.Activities.Statements.FlowSwitch%601.Default%2A> property that defines how execution should flow if no cases match the condition expression.</span></span> <span data-ttu-id="51b49-128">下面的示例演示如何定义使用 <xref:System.Activities.Statements.FlowSwitch%601> 元素的工作流。</span><span class="sxs-lookup"><span data-stu-id="51b49-128">The following example demonstrates how to define a workflow that uses a <xref:System.Activities.Statements.FlowSwitch%601> element.</span></span>

```xml
<Flowchart>
  <FlowSwitch>
    <FlowStep x:Key="Red">
      <WriteRed/>
    </FlowStep>
    <FlowStep x:Key="Blue">
      <WriteBlue/>
    </FlowStep>
    <FlowStep x:Key="Green">
      <WriteGreen/>
    </FlowStep>
  </FlowSwitch>
</Flowchart>
```
