---
title: 上下文关键字 - C# 参考
ms.date: 03/07/2017
helpviewer_keywords:
- contextual keywords [C#]
ms.assetid: 7c76bc29-a754-4389-b0ab-f6b441018298
ms.openlocfilehash: 1de8fbccfa9485a546689233ea8a601a8bd697a5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/14/2020
ms.locfileid: "75713647"
---
# <a name="contextual-keywords-c-reference"></a><span data-ttu-id="98111-102">上下文关键字（C# 参考）</span><span class="sxs-lookup"><span data-stu-id="98111-102">Contextual Keywords (C# Reference)</span></span>

<span data-ttu-id="98111-103">上下文关键字用于在代码中提供特定含义，但不是 C# 中的保留字。</span><span class="sxs-lookup"><span data-stu-id="98111-103">A contextual keyword is used to provide a specific meaning in the code, but it is not a reserved word in C#.</span></span> <span data-ttu-id="98111-104">本部分介绍下面这些上下文关键字：</span><span class="sxs-lookup"><span data-stu-id="98111-104">The following contextual keywords are introduced in this section:</span></span>  
  
|<span data-ttu-id="98111-105">关键字</span><span class="sxs-lookup"><span data-stu-id="98111-105">Keyword</span></span>|<span data-ttu-id="98111-106">说明</span><span class="sxs-lookup"><span data-stu-id="98111-106">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="98111-107">add</span><span class="sxs-lookup"><span data-stu-id="98111-107">add</span></span>](./add.md)|<span data-ttu-id="98111-108">定义一个自定义事件访问器，客户端代码订阅事件时会调用该访问器。</span><span class="sxs-lookup"><span data-stu-id="98111-108">Defines a custom event accessor that is invoked when client code subscribes to the event.</span></span>|  
|[<span data-ttu-id="98111-109">async</span><span class="sxs-lookup"><span data-stu-id="98111-109">async</span></span>](./async.md)|<span data-ttu-id="98111-110">指示修改后的方法、lambda 表达式或匿名方法是异步的。</span><span class="sxs-lookup"><span data-stu-id="98111-110">Indicates that the modified method, lambda expression, or anonymous method is asynchronous.</span></span>|  
|[<span data-ttu-id="98111-111">await</span><span class="sxs-lookup"><span data-stu-id="98111-111">await</span></span>](../operators/await.md)|<span data-ttu-id="98111-112">挂起异步方法，直到等待的任务完成。</span><span class="sxs-lookup"><span data-stu-id="98111-112">Suspends an async method until an awaited task is completed.</span></span>|  
|[<span data-ttu-id="98111-113">dynamic</span><span class="sxs-lookup"><span data-stu-id="98111-113">dynamic</span></span>](../builtin-types/reference-types.md)|<span data-ttu-id="98111-114">定义一个引用类型，实现发生绕过编译时类型检查的操作。</span><span class="sxs-lookup"><span data-stu-id="98111-114">Defines a reference type that enables operations in which it occurs to bypass compile-time type checking.</span></span>|  
|[<span data-ttu-id="98111-115">get</span><span class="sxs-lookup"><span data-stu-id="98111-115">get</span></span>](./get.md)|<span data-ttu-id="98111-116">为属性或索引器定义访问器方法。</span><span class="sxs-lookup"><span data-stu-id="98111-116">Defines an accessor method for a property or an indexer.</span></span>|  
|[<span data-ttu-id="98111-117">global</span><span class="sxs-lookup"><span data-stu-id="98111-117">global</span></span>](../operators/namespace-alias-qualifier.md)|<span data-ttu-id="98111-118">未以其他方式命名的全局命名空间的别名。</span><span class="sxs-lookup"><span data-stu-id="98111-118">Alias of the global namespace, which is otherwise unnamed.</span></span>|  
|[<span data-ttu-id="98111-119">partial</span><span class="sxs-lookup"><span data-stu-id="98111-119">partial</span></span>](./partial-type.md)|<span data-ttu-id="98111-120">在整个同一编译单元内定义分部类、结构和接口。</span><span class="sxs-lookup"><span data-stu-id="98111-120">Defines partial classes, structs, and interfaces throughout the same compilation unit.</span></span>|  
|[<span data-ttu-id="98111-121">remove</span><span class="sxs-lookup"><span data-stu-id="98111-121">remove</span></span>](./remove.md)|<span data-ttu-id="98111-122">定义一个自定义事件访问器，客户端代码取消订阅事件时会调用该访问器。</span><span class="sxs-lookup"><span data-stu-id="98111-122">Defines a custom event accessor that is invoked when client code unsubscribes from the event.</span></span>|  
|[<span data-ttu-id="98111-123">set</span><span class="sxs-lookup"><span data-stu-id="98111-123">set</span></span>](./set.md)|<span data-ttu-id="98111-124">为属性或索引器定义访问器方法。</span><span class="sxs-lookup"><span data-stu-id="98111-124">Defines an accessor method for a property or an indexer.</span></span>|  
|[<span data-ttu-id="98111-125">value</span><span class="sxs-lookup"><span data-stu-id="98111-125">value</span></span>](./value.md)|<span data-ttu-id="98111-126">用于设置访问器和添加或删除事件处理程序。</span><span class="sxs-lookup"><span data-stu-id="98111-126">Used to set accessors and to add or remove event handlers.</span></span>|  
|[<span data-ttu-id="98111-127">var</span><span class="sxs-lookup"><span data-stu-id="98111-127">var</span></span>](./var.md)|<span data-ttu-id="98111-128">使编译器能够确定在方法作用域中声明的变量类型。</span><span class="sxs-lookup"><span data-stu-id="98111-128">Enables the type of a variable declared at method scope to be determined by the compiler.</span></span>|  
|[<span data-ttu-id="98111-129">when</span><span class="sxs-lookup"><span data-stu-id="98111-129">when</span></span>](when.md)|<span data-ttu-id="98111-130">指定 `catch` 块的筛选条件或 `switch` 语句的 `case` 标签。</span><span class="sxs-lookup"><span data-stu-id="98111-130">Specifies a filter condition for a `catch` block or the `case` label of a `switch` statement.</span></span>|
|[<span data-ttu-id="98111-131">where</span><span class="sxs-lookup"><span data-stu-id="98111-131">where</span></span>](./where-generic-type-constraint.md)|<span data-ttu-id="98111-132">将约束添加到泛型声明。</span><span class="sxs-lookup"><span data-stu-id="98111-132">Adds constraints to a generic declaration.</span></span> <span data-ttu-id="98111-133">（另请参阅 [where](./where-clause.md)）。</span><span class="sxs-lookup"><span data-stu-id="98111-133">(See also [where](./where-clause.md)).</span></span>|  
|[<span data-ttu-id="98111-134">yield</span><span class="sxs-lookup"><span data-stu-id="98111-134">yield</span></span>](./yield.md)|<span data-ttu-id="98111-135">在迭代器块中使用，用于向枚举数对象返回值或用于表示迭代结束。</span><span class="sxs-lookup"><span data-stu-id="98111-135">Used in an iterator block to return a value to the enumerator object or to signal the end of iteration.</span></span>|  
  
 <span data-ttu-id="98111-136">C# 3.0 中引入的所有查询关键字也都是上下文相关的。</span><span class="sxs-lookup"><span data-stu-id="98111-136">All query keywords introduced in C# 3.0 are also contextual.</span></span> <span data-ttu-id="98111-137">有关详细信息，请参阅[查询关键字 (LINQ)](./query-keywords.md)。</span><span class="sxs-lookup"><span data-stu-id="98111-137">For more information, see [Query Keywords (LINQ)](./query-keywords.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="98111-138">另请参阅</span><span class="sxs-lookup"><span data-stu-id="98111-138">See also</span></span>

- [<span data-ttu-id="98111-139">C# 参考</span><span class="sxs-lookup"><span data-stu-id="98111-139">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="98111-140">C# 编程指南</span><span class="sxs-lookup"><span data-stu-id="98111-140">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="98111-141">C# 关键字</span><span class="sxs-lookup"><span data-stu-id="98111-141">C# Keywords</span></span>](./index.md)
