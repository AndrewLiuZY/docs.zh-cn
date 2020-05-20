---
title: 抽象类、密封类和类成员 - C# 编程指南
ms.date: 07/20/2015
helpviewer_keywords:
- abstract classes [C#]
- sealed classes [C#]
- C# language, abstract classes
- C# language, sealed
ms.assetid: 99aa52f7-b435-43f9-936e-2470af734c4e
ms.openlocfilehash: 07738031f1dec05424f7c3756f49a8f1f9a2c44b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/14/2020
ms.locfileid: "75714997"
---
# <a name="abstract-and-sealed-classes-and-class-members-c-programming-guide"></a><span data-ttu-id="7d7b0-102">抽象类、密封类及类成员（C# 编程指南）</span><span class="sxs-lookup"><span data-stu-id="7d7b0-102">Abstract and Sealed Classes and Class Members (C# Programming Guide)</span></span>
<span data-ttu-id="7d7b0-103">使用 [abstract](../../language-reference/keywords/abstract.md) 关键字可以创建不完整且必须在派生类中实现的类和 [class](../../language-reference/keywords/class.md) 成员。</span><span class="sxs-lookup"><span data-stu-id="7d7b0-103">The [abstract](../../language-reference/keywords/abstract.md) keyword enables you to create classes and [class](../../language-reference/keywords/class.md) members that are incomplete and must be implemented in a derived class.</span></span>  
  
 <span data-ttu-id="7d7b0-104">使用 [sealed](../../language-reference/keywords/sealed.md) 关键字可以防止继承以前标记为 [virtual](../../language-reference/keywords/virtual.md) 的类或某些类成员。</span><span class="sxs-lookup"><span data-stu-id="7d7b0-104">The [sealed](../../language-reference/keywords/sealed.md) keyword enables you to prevent the inheritance of a class or certain class members that were previously marked [virtual](../../language-reference/keywords/virtual.md).</span></span>  
  
## <a name="abstract-classes-and-class-members"></a><span data-ttu-id="7d7b0-105">抽象类和类成员</span><span class="sxs-lookup"><span data-stu-id="7d7b0-105">Abstract Classes and Class Members</span></span>  
 <span data-ttu-id="7d7b0-106">通过在类定义前面放置关键字 `abstract`，可以将类声明为抽象类。</span><span class="sxs-lookup"><span data-stu-id="7d7b0-106">Classes can be declared as abstract by putting the keyword `abstract` before the class definition.</span></span> <span data-ttu-id="7d7b0-107">例如:</span><span class="sxs-lookup"><span data-stu-id="7d7b0-107">For example:</span></span>  
  
 [!code-csharp[csProgGuideInheritance#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#13)]  
  
 <span data-ttu-id="7d7b0-108">抽象类不能实例化。</span><span class="sxs-lookup"><span data-stu-id="7d7b0-108">An abstract class cannot be instantiated.</span></span> <span data-ttu-id="7d7b0-109">抽象类的用途是提供一个可供多个派生类共享的通用基类定义。</span><span class="sxs-lookup"><span data-stu-id="7d7b0-109">The purpose of an abstract class is to provide a common definition of a base class that multiple derived classes can share.</span></span> <span data-ttu-id="7d7b0-110">例如，类库可以定义一个抽象类，将其用作多个类库函数的参数，并要求使用该库的程序员通过创建派生类来提供自己的类实现。</span><span class="sxs-lookup"><span data-stu-id="7d7b0-110">For example, a class library may define an abstract class that is used as a parameter to many of its functions, and require programmers using that library to provide their own implementation of the class by creating a derived class.</span></span>  
  
 <span data-ttu-id="7d7b0-111">抽象类也可以定义抽象方法。</span><span class="sxs-lookup"><span data-stu-id="7d7b0-111">Abstract classes may also define abstract methods.</span></span> <span data-ttu-id="7d7b0-112">方法是将关键字 `abstract` 添加到方法的返回类型的前面。</span><span class="sxs-lookup"><span data-stu-id="7d7b0-112">This is accomplished by adding the keyword `abstract` before the return type of the method.</span></span> <span data-ttu-id="7d7b0-113">例如:</span><span class="sxs-lookup"><span data-stu-id="7d7b0-113">For example:</span></span>  
  
 [!code-csharp[csProgGuideInheritance#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#14)]  
  
 <span data-ttu-id="7d7b0-114">抽象方法没有实现，所以方法定义后面是分号，而不是常规的方法块。</span><span class="sxs-lookup"><span data-stu-id="7d7b0-114">Abstract methods have no implementation, so the method definition is followed by a semicolon instead of a normal method block.</span></span> <span data-ttu-id="7d7b0-115">抽象类的派生类必须实现所有抽象方法。</span><span class="sxs-lookup"><span data-stu-id="7d7b0-115">Derived classes of the abstract class must implement all abstract methods.</span></span> <span data-ttu-id="7d7b0-116">当抽象类从基类继承虚方法时，抽象类可以使用抽象方法重写该虚方法。</span><span class="sxs-lookup"><span data-stu-id="7d7b0-116">When an abstract class inherits a virtual method from a base class, the abstract class can override the virtual method with an abstract method.</span></span> <span data-ttu-id="7d7b0-117">例如:</span><span class="sxs-lookup"><span data-stu-id="7d7b0-117">For example:</span></span>  
  
 [!code-csharp[csProgGuideInheritance#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#15)]  
  
 <span data-ttu-id="7d7b0-118">如果将 `virtual` 方法声明为 `abstract`，则该方法对于从抽象类继承的所有类而言仍然是虚方法。</span><span class="sxs-lookup"><span data-stu-id="7d7b0-118">If a `virtual` method is declared `abstract`, it is still virtual to any class inheriting from the abstract class.</span></span> <span data-ttu-id="7d7b0-119">继承抽象方法的类无法访问方法的原始实现，因此在上一示例中，类 F 上的 `DoWork` 无法调用类 D 上的 `DoWork`。通过这种方式，抽象类可强制派生类向虚拟方法提供新的方法实现。</span><span class="sxs-lookup"><span data-stu-id="7d7b0-119">A class inheriting an abstract method cannot access the original implementation of the method—in the previous example, `DoWork` on class F cannot call `DoWork` on class D. In this way, an abstract class can force derived classes to provide new method implementations for virtual methods.</span></span>  
  
## <a name="sealed-classes-and-class-members"></a><span data-ttu-id="7d7b0-120">密封类和类成员</span><span class="sxs-lookup"><span data-stu-id="7d7b0-120">Sealed Classes and Class Members</span></span>  
 <span data-ttu-id="7d7b0-121">通过在类定义前面放置关键字 `sealed`，可以将类声明为[密封类](../../language-reference/keywords/sealed.md)。</span><span class="sxs-lookup"><span data-stu-id="7d7b0-121">Classes can be declared as [sealed](../../language-reference/keywords/sealed.md) by putting the keyword `sealed` before the class definition.</span></span> <span data-ttu-id="7d7b0-122">例如:</span><span class="sxs-lookup"><span data-stu-id="7d7b0-122">For example:</span></span>  
  
 [!code-csharp[csProgGuideInheritance#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#16)]  
  
 <span data-ttu-id="7d7b0-123">密封类不能用作基类。</span><span class="sxs-lookup"><span data-stu-id="7d7b0-123">A sealed class cannot be used as a base class.</span></span> <span data-ttu-id="7d7b0-124">因此，它也不能是抽象类。</span><span class="sxs-lookup"><span data-stu-id="7d7b0-124">For this reason, it cannot also be an abstract class.</span></span> <span data-ttu-id="7d7b0-125">密封类禁止派生。</span><span class="sxs-lookup"><span data-stu-id="7d7b0-125">Sealed classes prevent derivation.</span></span> <span data-ttu-id="7d7b0-126">由于密封类从不用作基类，所以有些运行时优化可以略微提高密封类成员的调用速度。</span><span class="sxs-lookup"><span data-stu-id="7d7b0-126">Because they can never be used as a base class, some run-time optimizations can make calling sealed class members slightly faster.</span></span>  
  
 <span data-ttu-id="7d7b0-127">在对基类的虚成员进行重写的派生类上，方法、索引器、属性或事件可以将该成员声明为密封成员。</span><span class="sxs-lookup"><span data-stu-id="7d7b0-127">A method, indexer, property, or event, on a derived class that is overriding a virtual member of the base class can declare that member as sealed.</span></span> <span data-ttu-id="7d7b0-128">在用于以后的派生类时，这将取消成员的虚效果。</span><span class="sxs-lookup"><span data-stu-id="7d7b0-128">This negates the virtual aspect of the member for any further derived class.</span></span> <span data-ttu-id="7d7b0-129">方法是在类成员声明中将 `sealed` 关键字置于 [override](../../language-reference/keywords/override.md) 关键字前面。</span><span class="sxs-lookup"><span data-stu-id="7d7b0-129">This is accomplished by putting the `sealed` keyword before the [override](../../language-reference/keywords/override.md) keyword in the class member declaration.</span></span> <span data-ttu-id="7d7b0-130">例如:</span><span class="sxs-lookup"><span data-stu-id="7d7b0-130">For example:</span></span>  
  
 [!code-csharp[csProgGuideInheritance#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#17)]  
  
## <a name="see-also"></a><span data-ttu-id="7d7b0-131">另请参阅</span><span class="sxs-lookup"><span data-stu-id="7d7b0-131">See also</span></span>

- [<span data-ttu-id="7d7b0-132">C# 编程指南</span><span class="sxs-lookup"><span data-stu-id="7d7b0-132">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="7d7b0-133">类和结构</span><span class="sxs-lookup"><span data-stu-id="7d7b0-133">Classes and Structs</span></span>](./index.md)
- [<span data-ttu-id="7d7b0-134">继承</span><span class="sxs-lookup"><span data-stu-id="7d7b0-134">Inheritance</span></span>](./inheritance.md)
- [<span data-ttu-id="7d7b0-135">方法</span><span class="sxs-lookup"><span data-stu-id="7d7b0-135">Methods</span></span>](./methods.md)
- [<span data-ttu-id="7d7b0-136">字段</span><span class="sxs-lookup"><span data-stu-id="7d7b0-136">Fields</span></span>](./fields.md)
- [<span data-ttu-id="7d7b0-137">如何定义抽象属性</span><span class="sxs-lookup"><span data-stu-id="7d7b0-137">How to define abstract properties</span></span>](./how-to-define-abstract-properties.md)
