---
title: 表达式 - C# 编程指南
ms.date: 05/11/2017
helpviewer_keywords:
- expressions [C#]
- C# language, expressions
ms.assetid: c7d8feb0-0e58-4f94-8bf6-4d070550a832
ms.openlocfilehash: 4bbee8f15c2591e8b172df9a6759449d48697804
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/14/2020
ms.locfileid: "75699088"
---
# <a name="expressions-c-programming-guide"></a><span data-ttu-id="42af8-102">表达式（C# 编程指南）</span><span class="sxs-lookup"><span data-stu-id="42af8-102">Expressions (C# Programming Guide)</span></span>

<span data-ttu-id="42af8-103">表达式是由一个或多个操作数以及零个或多个[运算符](../../language-reference/operators/index.md)组成的序列，其计算结果为一个值、对象、方法或命名空间。</span><span class="sxs-lookup"><span data-stu-id="42af8-103">An *expression* is a sequence of one or more operands and zero or more [operators](../../language-reference/operators/index.md) that can be evaluated to a single value, object, method, or namespace.</span></span> <span data-ttu-id="42af8-104">表达式可以包含文本值、方法调用、运算符及其操作数，或简单名称  。</span><span class="sxs-lookup"><span data-stu-id="42af8-104">Expressions can consist of a literal value, a method invocation, an operator and its operands, or a *simple name*.</span></span> <span data-ttu-id="42af8-105">简单名称可以是变量名、类型成员名、方法参数名、命名空间名或类型名。</span><span class="sxs-lookup"><span data-stu-id="42af8-105">Simple names can be the name of a variable, type member, method parameter, namespace or type.</span></span>  
  
 <span data-ttu-id="42af8-106">表达式可以使用运算符（运算符又可使用其他表达式作为参数）或方法调用（方法调用的参数又可以是其他方法调用），因此表达式可以非常简单，也可以极其复杂。</span><span class="sxs-lookup"><span data-stu-id="42af8-106">Expressions can use operators that in turn use other expressions as parameters, or method calls whose parameters are in turn other method calls, so expressions can range from simple to very complex.</span></span> <span data-ttu-id="42af8-107">下面是表达式的两个示例：</span><span class="sxs-lookup"><span data-stu-id="42af8-107">Following are two examples of expressions:</span></span>  
  
```csharp  
((x < 10) && ( x > 5)) || ((x > 20) && (x < 25));

System.Convert.ToInt32("35");  
```  
  
## <a name="expression-values"></a><span data-ttu-id="42af8-108">表达式值</span><span class="sxs-lookup"><span data-stu-id="42af8-108">Expression values</span></span>

 <span data-ttu-id="42af8-109">在大部分使用表达式的上下文中（例如在语句或方法参数中），表达式的计算结果应为某个值。</span><span class="sxs-lookup"><span data-stu-id="42af8-109">In most of the contexts in which expressions are used, for example in statements or method parameters, the expression is expected to evaluate to some value.</span></span> <span data-ttu-id="42af8-110">如果 x 和 y 是整数，表达式 `x + y` 的计算结果为一个数值。</span><span class="sxs-lookup"><span data-stu-id="42af8-110">If x and y are integers, the expression `x + y` evaluates to a numeric value.</span></span> <span data-ttu-id="42af8-111">表达式 `new MyClass()` 的计算结果为对 `MyClass` 类的新实例的引用。</span><span class="sxs-lookup"><span data-stu-id="42af8-111">The expression `new MyClass()` evaluates to a reference to a new instance of a `MyClass` class.</span></span> <span data-ttu-id="42af8-112">表达式 `myClass.ToString()` 的计算结果为一个字符串，因为字符串是该方法的返回类型。</span><span class="sxs-lookup"><span data-stu-id="42af8-112">The expression `myClass.ToString()` evaluates to a string because that is the return type of the method.</span></span> <span data-ttu-id="42af8-113">然而，虽然命名空间名称归类为表达式，但它的计算结果不是一个值，因此绝不会作为任何表达式的最终结果。</span><span class="sxs-lookup"><span data-stu-id="42af8-113">However, although a namespace name is classified as an expression, it does not evaluate to a value and therefore can never be the final result of any expression.</span></span> <span data-ttu-id="42af8-114">命名空间名称不得传递给方法参数，不能用在新表达式中，也不能赋给变量。</span><span class="sxs-lookup"><span data-stu-id="42af8-114">You cannot pass a namespace name to a method parameter, or use it in a new expression, or assign it to a variable.</span></span> <span data-ttu-id="42af8-115">命名空间名称只能用作较大表达式的子表达式。</span><span class="sxs-lookup"><span data-stu-id="42af8-115">You can only use it as a sub-expression in a larger expression.</span></span> <span data-ttu-id="42af8-116">同样如此的还有类型（与 <xref:System.Type?displayProperty=nameWithType> 对象不同）、方法组名称（与特定方法不同）以及事件 [add](../../language-reference/keywords/add.md) 和 [remove](../../language-reference/keywords/remove.md) 访问器。</span><span class="sxs-lookup"><span data-stu-id="42af8-116">The same is true for types (as distinct from <xref:System.Type?displayProperty=nameWithType> objects), method group names (as distinct from specific methods), and event [add](../../language-reference/keywords/add.md) and [remove](../../language-reference/keywords/remove.md) accessors.</span></span>  
  
 <span data-ttu-id="42af8-117">每个值都有关联的类型。</span><span class="sxs-lookup"><span data-stu-id="42af8-117">Every value has an associated type.</span></span> <span data-ttu-id="42af8-118">例如，如果 x 和 y 都是 `int` 类型的变量，则表达式 `x + y` 的值也属于 `int` 类型。</span><span class="sxs-lookup"><span data-stu-id="42af8-118">For example, if x and y are both variables of type `int`, the value of the expression `x + y` is also typed as `int`.</span></span> <span data-ttu-id="42af8-119">如果将该值赋给不同类型的变量，或者如果 x 和 y 是不同的类型，则应用类型转换规则。</span><span class="sxs-lookup"><span data-stu-id="42af8-119">If the value is assigned to a variable of a different type, or if x and y are different types, the rules of type conversion are applied.</span></span> <span data-ttu-id="42af8-120">若要详细了解如何进行这种转换，请参阅[强制转换和类型转换](../types/casting-and-type-conversions.md)。</span><span class="sxs-lookup"><span data-stu-id="42af8-120">For more information about how such conversions work, see [Casting and Type Conversions](../types/casting-and-type-conversions.md).</span></span>  
  
## <a name="overflows"></a><span data-ttu-id="42af8-121">溢出</span><span class="sxs-lookup"><span data-stu-id="42af8-121">Overflows</span></span>

 <span data-ttu-id="42af8-122">如果值大于值类型的最大值，数值表达式可能导致溢出。</span><span class="sxs-lookup"><span data-stu-id="42af8-122">Numeric expressions may cause overflows if the value is larger than the maximum value of the value's type.</span></span> <span data-ttu-id="42af8-123">有关详细信息，请参阅[内置数值转换](../../language-reference/builtin-types/numeric-conversions.md)一文的 [Checked 和 Unchecked](../../language-reference/keywords/checked-and-unchecked.md) 和[显式数值转换](../../language-reference/builtin-types/numeric-conversions.md#explicit-numeric-conversions)部分。</span><span class="sxs-lookup"><span data-stu-id="42af8-123">For more information, see [Checked and Unchecked](../../language-reference/keywords/checked-and-unchecked.md) and the [Explicit numeric conversions](../../language-reference/builtin-types/numeric-conversions.md#explicit-numeric-conversions) section of the [Built-in numeric conversions](../../language-reference/builtin-types/numeric-conversions.md) article.</span></span>
  
## <a name="operator-precedence-and-associativity"></a><span data-ttu-id="42af8-124">运算符优先级和关联性</span><span class="sxs-lookup"><span data-stu-id="42af8-124">Operator precedence and associativity</span></span>

 <span data-ttu-id="42af8-125">计算表达式的方式取决于关联性和运算符优先级规则。</span><span class="sxs-lookup"><span data-stu-id="42af8-125">The manner in which an expression is evaluated is governed by the rules of associativity and operator precedence.</span></span> <span data-ttu-id="42af8-126">有关详细信息，请参阅[运算符](../../language-reference/operators/index.md)。</span><span class="sxs-lookup"><span data-stu-id="42af8-126">For more information, see [Operators](../../language-reference/operators/index.md).</span></span>  
  
 <span data-ttu-id="42af8-127">除赋值表达式和方法调用表达式之外，大部分表达式都必须嵌在语句中。</span><span class="sxs-lookup"><span data-stu-id="42af8-127">Most expressions, except assignment expressions and method invocation expressions, must be embedded in a statement.</span></span> <span data-ttu-id="42af8-128">有关详细信息，请参阅[语句](./statements.md)。</span><span class="sxs-lookup"><span data-stu-id="42af8-128">For more information, see [Statements](./statements.md).</span></span>  
  
## <a name="literals-and-simple-names"></a><span data-ttu-id="42af8-129">文本和简单名称</span><span class="sxs-lookup"><span data-stu-id="42af8-129">Literals and simple names</span></span>

 <span data-ttu-id="42af8-130">最简单的两种表达式类型是文本和简单名称。</span><span class="sxs-lookup"><span data-stu-id="42af8-130">The two simplest types of expressions are literals and simple names.</span></span> <span data-ttu-id="42af8-131">文本是没有名称的常数值。</span><span class="sxs-lookup"><span data-stu-id="42af8-131">A literal is a constant value that has no name.</span></span> <span data-ttu-id="42af8-132">例如，在以下代码示例中，`5` 和 `"Hello World"` 都是文本值：</span><span class="sxs-lookup"><span data-stu-id="42af8-132">For example, in the following code example, both `5` and `"Hello World"` are literal values:</span></span>  
  
 [!code-csharp[csProgGuideStatements#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStatements/CS/Statements.cs#2)]  
  
 <span data-ttu-id="42af8-133">有关文本的详细信息，请参阅[类型](/dotnet/csharp/language-reference/keywords)。</span><span class="sxs-lookup"><span data-stu-id="42af8-133">For more information on literals, see [Types](/dotnet/csharp/language-reference/keywords).</span></span>  
  
 <span data-ttu-id="42af8-134">在前面的示例中，`i` 和 `s` 都是用于标识局部变量的简单名称。</span><span class="sxs-lookup"><span data-stu-id="42af8-134">In the preceding example, both `i` and `s` are simple names that identify local variables.</span></span> <span data-ttu-id="42af8-135">在表达式中使用这些变量时，变量名称计算为当前在该变量的内存位置所存储的值。</span><span class="sxs-lookup"><span data-stu-id="42af8-135">When those variables are used in an expression, the variable name evaluates to the value that is currently stored in the variable's location in memory.</span></span> <span data-ttu-id="42af8-136">下面的示例对此进行了演示：</span><span class="sxs-lookup"><span data-stu-id="42af8-136">This is shown in the following example:</span></span>  
  
 [!code-csharp[csProgGuideStatements#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStatements/CS/Statements.cs#3)]

## <a name="invocation-expressions"></a><span data-ttu-id="42af8-137">调用表达式</span><span class="sxs-lookup"><span data-stu-id="42af8-137">Invocation expressions</span></span>

 <span data-ttu-id="42af8-138">在下面的代码示例中，对 `DoWork` 的调用是一个调用表达式。</span><span class="sxs-lookup"><span data-stu-id="42af8-138">In the following code example, the call to `DoWork` is an invocation expression.</span></span>  
  
```csharp
DoWork();  
```  
  
 <span data-ttu-id="42af8-139">方法调用需要方法的名称（如之前的示例中那样作为名称，或作为其他表达式的结果），后跟括号和任意方法参数。</span><span class="sxs-lookup"><span data-stu-id="42af8-139">A method invocation requires the name of the method, either as a name as in the previous example, or as the result of another expression, followed by parenthesis and any method parameters.</span></span> <span data-ttu-id="42af8-140">有关详细信息，请参阅[方法](../classes-and-structs/methods.md)。</span><span class="sxs-lookup"><span data-stu-id="42af8-140">For more information, see [Methods](../classes-and-structs/methods.md).</span></span> <span data-ttu-id="42af8-141">委托调用使用委托的名称和括号内的方法参数。</span><span class="sxs-lookup"><span data-stu-id="42af8-141">A delegate invocation uses the name of a delegate and method parameters in parenthesis.</span></span> <span data-ttu-id="42af8-142">有关详细信息，请参阅[委托](../delegates/index.md)。</span><span class="sxs-lookup"><span data-stu-id="42af8-142">For more information, see [Delegates](../delegates/index.md).</span></span> <span data-ttu-id="42af8-143">如果方法返回值，则方法调用和委托调用的计算结果为该方法的返回值。</span><span class="sxs-lookup"><span data-stu-id="42af8-143">Method invocations and delegate invocations evaluate to the return value of the method, if the method returns a value.</span></span> <span data-ttu-id="42af8-144">返回 void 的方法不能替代表达式中的值。</span><span class="sxs-lookup"><span data-stu-id="42af8-144">Methods that return void cannot be used in place of a value in an expression.</span></span>  

## <a name="query-expressions"></a><span data-ttu-id="42af8-145">查询表达式</span><span class="sxs-lookup"><span data-stu-id="42af8-145">Query expressions</span></span>

 <span data-ttu-id="42af8-146">针对常规表达式的规则同样适用于查询表达式。</span><span class="sxs-lookup"><span data-stu-id="42af8-146">The same rules for expressions in general apply to query expressions.</span></span> <span data-ttu-id="42af8-147">有关详细信息，请参阅 [LINQ](../../linq/index.md)。</span><span class="sxs-lookup"><span data-stu-id="42af8-147">For more information, see [LINQ](../../linq/index.md).</span></span>  
  
## <a name="lambda-expressions"></a><span data-ttu-id="42af8-148">Lambda 表达式</span><span class="sxs-lookup"><span data-stu-id="42af8-148">Lambda expressions</span></span>

 <span data-ttu-id="42af8-149">Lambda 表达式表示没有名称但可以具有输入参数和多个语句的“内联方法”。</span><span class="sxs-lookup"><span data-stu-id="42af8-149">Lambda expressions represent "inline methods" that have no name but can have input parameters and multiple statements.</span></span> <span data-ttu-id="42af8-150">它们在 LINQ 中广泛用于向方法传递参数。</span><span class="sxs-lookup"><span data-stu-id="42af8-150">They are used extensively in LINQ to pass arguments to methods.</span></span> <span data-ttu-id="42af8-151">Lambda 表达式会编译为委托或表达式树，具体取决于使用它们的上下文。</span><span class="sxs-lookup"><span data-stu-id="42af8-151">Lambda expressions are compiled to either delegates or expression trees depending on the context in which they are used.</span></span> <span data-ttu-id="42af8-152">有关详细信息，请参阅 [Lambda 表达式](lambda-expressions.md)。</span><span class="sxs-lookup"><span data-stu-id="42af8-152">For more information, see [Lambda Expressions](lambda-expressions.md).</span></span>  
  
## <a name="expression-trees"></a><span data-ttu-id="42af8-153">表达式树</span><span class="sxs-lookup"><span data-stu-id="42af8-153">Expression trees</span></span>

<span data-ttu-id="42af8-154">使用表达式树可将表达式表示为数据结构。</span><span class="sxs-lookup"><span data-stu-id="42af8-154">Expression trees enable expressions to be represented as data structures.</span></span> <span data-ttu-id="42af8-155">表达式树由 LINQ 提供程序广泛使用，用来将查询表达式转换为在其他某些上下文（如 SQL 数据库）中有意义的代码。</span><span class="sxs-lookup"><span data-stu-id="42af8-155">They are used extensively by LINQ providers to translate query expressions into code that is meaningful in some other context, such as a SQL database.</span></span> <span data-ttu-id="42af8-156">有关详细信息，请参阅[表达式树 (C#)](../concepts/expression-trees/index.md)。</span><span class="sxs-lookup"><span data-stu-id="42af8-156">For more information, see [Expression Trees (C#)](../concepts/expression-trees/index.md).</span></span>
  
## <a name="expression-body-definitions"></a><span data-ttu-id="42af8-157">表达式主体定义</span><span class="sxs-lookup"><span data-stu-id="42af8-157">Expression body definitions</span></span>

<span data-ttu-id="42af8-158">C# 支持“Expression-Bodied 成员”  ，这允许为方法、构造函数、终结器、属性和索引器提供简洁的表达式主体定义。</span><span class="sxs-lookup"><span data-stu-id="42af8-158">C# supports *expression-bodied members*, which allow you to supply a concise expression body definition for methods, constructors, finalizers, properties, and indexers.</span></span> <span data-ttu-id="42af8-159">有关详细信息，请参阅 “[Expression-bodied 成员](expression-bodied-members.md)”。</span><span class="sxs-lookup"><span data-stu-id="42af8-159">For more information, see [Expression-bodied members](expression-bodied-members.md).</span></span>

## <a name="remarks"></a><span data-ttu-id="42af8-160">备注</span><span class="sxs-lookup"><span data-stu-id="42af8-160">Remarks</span></span>

 <span data-ttu-id="42af8-161">只要从表达式中识别到变量、对象属性或对象索引器访问，该项的值都会用作表达式的值。</span><span class="sxs-lookup"><span data-stu-id="42af8-161">Whenever a variable, object property, or object indexer access is identified from an expression, the value of that item is used as the value of the expression.</span></span> <span data-ttu-id="42af8-162">只要表达式的最终计算结果是所需的类型，表达式就可以置于 C# 中任何需要值或对象的位置。</span><span class="sxs-lookup"><span data-stu-id="42af8-162">An expression can be placed anywhere in C# where a value or object is required, as long as the expression ultimately evaluates to the required type.</span></span>  

## <a name="c-language-specification"></a><span data-ttu-id="42af8-163">C# 语言规范</span><span class="sxs-lookup"><span data-stu-id="42af8-163">C# language specification</span></span>

<span data-ttu-id="42af8-164">有关详细信息，请参阅 [C# 语言规范](~/_csharplang/spec/introduction.md)中的[表达式](~/_csharplang/spec/expressions.md)部分。</span><span class="sxs-lookup"><span data-stu-id="42af8-164">For more information, see the [Expressions](~/_csharplang/spec/expressions.md) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="42af8-165">请参阅</span><span class="sxs-lookup"><span data-stu-id="42af8-165">See also</span></span>

- [<span data-ttu-id="42af8-166">C# 编程指南</span><span class="sxs-lookup"><span data-stu-id="42af8-166">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="42af8-167">运算符</span><span class="sxs-lookup"><span data-stu-id="42af8-167">Operators</span></span>](../../language-reference/operators/index.md)
- [<span data-ttu-id="42af8-168">方法</span><span class="sxs-lookup"><span data-stu-id="42af8-168">Methods</span></span>](../classes-and-structs/methods.md)
- [<span data-ttu-id="42af8-169">委托</span><span class="sxs-lookup"><span data-stu-id="42af8-169">Delegates</span></span>](../delegates/index.md)
- [<span data-ttu-id="42af8-170">类型</span><span class="sxs-lookup"><span data-stu-id="42af8-170">Types</span></span>](../types/index.md)
- [<span data-ttu-id="42af8-171">LINQ</span><span class="sxs-lookup"><span data-stu-id="42af8-171">LINQ</span></span>](../../linq/index.md)
