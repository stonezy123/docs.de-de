---
title: Abstrakte und versiegelte Klassen und Klassenmember – C#-Programmierhandbuch
description: Das abstrakte Schlüsselwort in C# erstellt unvollständige Klassen und Klassenmember. Das versiegelte Schlüsselwort verhindert die Vererbung vorheriger virtueller Klassen oder Klassenmember.
ms.date: 07/20/2015
helpviewer_keywords:
- abstract classes [C#]
- sealed classes [C#]
- C# language, abstract classes
- C# language, sealed
ms.assetid: 99aa52f7-b435-43f9-936e-2470af734c4e
ms.openlocfilehash: ccbc6734d4e9bafe059dd45bfdf82af7c84438a2
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/24/2020
ms.locfileid: "91204033"
---
# <a name="abstract-and-sealed-classes-and-class-members-c-programming-guide"></a><span data-ttu-id="f21f3-104">Abstrakte und versiegelte Klassen und Klassenmember (C#-Programmierhandbuch)</span><span class="sxs-lookup"><span data-stu-id="f21f3-104">Abstract and Sealed Classes and Class Members (C# Programming Guide)</span></span>

<span data-ttu-id="f21f3-105">Das Schlüsselwort [abstract](../../language-reference/keywords/abstract.md) ermöglicht die Erstellung von Klassen und [Klassenmembern](../../language-reference/keywords/class.md), die unvollständig sind und in einer abgeleiteten Klasse implementiert werden müssen.</span><span class="sxs-lookup"><span data-stu-id="f21f3-105">The [abstract](../../language-reference/keywords/abstract.md) keyword enables you to create classes and [class](../../language-reference/keywords/class.md) members that are incomplete and must be implemented in a derived class.</span></span>  
  
 <span data-ttu-id="f21f3-106">Mit dem Schlüsselwort [sealed](../../language-reference/keywords/sealed.md) können Sie die Vererbung von Klassen oder bestimmten Klassenmembern unterbinden, die zuvor als [virtuell](../../language-reference/keywords/virtual.md) gekennzeichnet wurden.</span><span class="sxs-lookup"><span data-stu-id="f21f3-106">The [sealed](../../language-reference/keywords/sealed.md) keyword enables you to prevent the inheritance of a class or certain class members that were previously marked [virtual](../../language-reference/keywords/virtual.md).</span></span>  
  
## <a name="abstract-classes-and-class-members"></a><span data-ttu-id="f21f3-107">Abstrakte Klassen und Klassenmember</span><span class="sxs-lookup"><span data-stu-id="f21f3-107">Abstract Classes and Class Members</span></span>  

 <span data-ttu-id="f21f3-108">Klassen können durch Festlegen des Schlüsselworts `abstract` vor der Klassendefinition als abstrakt deklariert werden.</span><span class="sxs-lookup"><span data-stu-id="f21f3-108">Classes can be declared as abstract by putting the keyword `abstract` before the class definition.</span></span> <span data-ttu-id="f21f3-109">Zum Beispiel:</span><span class="sxs-lookup"><span data-stu-id="f21f3-109">For example:</span></span>  
  
 [!code-csharp[csProgGuideInheritance#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#13)]  
  
 <span data-ttu-id="f21f3-110">Eine abstrakte Klasse darf nicht instanziiert werden.</span><span class="sxs-lookup"><span data-stu-id="f21f3-110">An abstract class cannot be instantiated.</span></span> <span data-ttu-id="f21f3-111">Der Zweck einer abstrakten Klasse ist die Bereitstellung einer allgemeinen Definition einer Basisklasse, die für mehrere abgeleitete Klassen freigegeben ist.</span><span class="sxs-lookup"><span data-stu-id="f21f3-111">The purpose of an abstract class is to provide a common definition of a base class that multiple derived classes can share.</span></span> <span data-ttu-id="f21f3-112">Eine Klassenbibliothek kann beispielsweise eine abstrakte Klasse definieren, die als Parameter für ihre Funktionen verwendet wird. Programmierer, die diese Bibliothek verwenden, benötigen ihre eigene Implementierung der Klasse, die sie von ihr ableiten können.</span><span class="sxs-lookup"><span data-stu-id="f21f3-112">For example, a class library may define an abstract class that is used as a parameter to many of its functions, and require programmers using that library to provide their own implementation of the class by creating a derived class.</span></span>  
  
 <span data-ttu-id="f21f3-113">Abstrakte Klassen können auch abstrakte Methoden definieren.</span><span class="sxs-lookup"><span data-stu-id="f21f3-113">Abstract classes may also define abstract methods.</span></span> <span data-ttu-id="f21f3-114">Zu diesem Zweck wird das Schlüsselwort `abstract` vor dem Rückgabetyp der Methode einfügt.</span><span class="sxs-lookup"><span data-stu-id="f21f3-114">This is accomplished by adding the keyword `abstract` before the return type of the method.</span></span> <span data-ttu-id="f21f3-115">Zum Beispiel:</span><span class="sxs-lookup"><span data-stu-id="f21f3-115">For example:</span></span>  
  
 [!code-csharp[csProgGuideInheritance#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#14)]  
  
 <span data-ttu-id="f21f3-116">Abstrakte Methoden verfügen über keine Implementierung, deshalb folgt der Methodendefinition ein Semikolon statt eines normalen Methodenblocks.</span><span class="sxs-lookup"><span data-stu-id="f21f3-116">Abstract methods have no implementation, so the method definition is followed by a semicolon instead of a normal method block.</span></span> <span data-ttu-id="f21f3-117">Von der abstrakten Klasse abgeleitete Klassen müssen alle abstrakten Methoden implementieren.</span><span class="sxs-lookup"><span data-stu-id="f21f3-117">Derived classes of the abstract class must implement all abstract methods.</span></span> <span data-ttu-id="f21f3-118">Wenn eine abstrakte Klasse eine virtuelle Methode von einer Basisklasse erbt, kann sie die virtuelle Methode mit einer abstrakten Methode überschreiben.</span><span class="sxs-lookup"><span data-stu-id="f21f3-118">When an abstract class inherits a virtual method from a base class, the abstract class can override the virtual method with an abstract method.</span></span> <span data-ttu-id="f21f3-119">Zum Beispiel:</span><span class="sxs-lookup"><span data-stu-id="f21f3-119">For example:</span></span>  
  
 [!code-csharp[csProgGuideInheritance#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#15)]  
  
 <span data-ttu-id="f21f3-120">Wenn eine `virtual`-Methode als `abstract` deklariert ist, bleibt sie für alle Klassen virtuell, die von der abstrakten Klasse erben.</span><span class="sxs-lookup"><span data-stu-id="f21f3-120">If a `virtual` method is declared `abstract`, it is still virtual to any class inheriting from the abstract class.</span></span> <span data-ttu-id="f21f3-121">Eine Klasse, die eine abstrakte Methode erbt, kann nicht auf die ursprüngliche Implementierung der Methode zugreifen. Im vorherigen Beispiel konnte `DoWork` auf Klasse F `DoWork` auf Klasse D nicht aufrufen. So kann eine abstrakte Klasse abgeleitete Klassen dazu zwingen, neue Methodenimplementierungen für virtuelle Methoden bereitzustellen.</span><span class="sxs-lookup"><span data-stu-id="f21f3-121">A class inheriting an abstract method cannot access the original implementation of the method—in the previous example, `DoWork` on class F cannot call `DoWork` on class D. In this way, an abstract class can force derived classes to provide new method implementations for virtual methods.</span></span>  
  
## <a name="sealed-classes-and-class-members"></a><span data-ttu-id="f21f3-122">Versiegelte Klassen und Klassenmember</span><span class="sxs-lookup"><span data-stu-id="f21f3-122">Sealed Classes and Class Members</span></span>  

 <span data-ttu-id="f21f3-123">Klassen können durch Festlegen des Schlüsselworts `sealed` vor der Klassendefinition als [sealed](../../language-reference/keywords/sealed.md) deklariert werden.</span><span class="sxs-lookup"><span data-stu-id="f21f3-123">Classes can be declared as [sealed](../../language-reference/keywords/sealed.md) by putting the keyword `sealed` before the class definition.</span></span> <span data-ttu-id="f21f3-124">Zum Beispiel:</span><span class="sxs-lookup"><span data-stu-id="f21f3-124">For example:</span></span>  
  
 [!code-csharp[csProgGuideInheritance#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#16)]  
  
 <span data-ttu-id="f21f3-125">Eine versiegelte Klasse kann nicht als Basisklasse verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="f21f3-125">A sealed class cannot be used as a base class.</span></span> <span data-ttu-id="f21f3-126">Aus diesem Grund kann sie auch keine abstrakte Klasse sein.</span><span class="sxs-lookup"><span data-stu-id="f21f3-126">For this reason, it cannot also be an abstract class.</span></span> <span data-ttu-id="f21f3-127">Von versiegelten Klassen kann nicht abgeleitet werden.</span><span class="sxs-lookup"><span data-stu-id="f21f3-127">Sealed classes prevent derivation.</span></span> <span data-ttu-id="f21f3-128">Weil sie nicht als Basisklasse verwendet werden können, können Aufrufe an versiegelte Klassenmember durch Laufzeitoptimierungen etwas beschleunigt werden.</span><span class="sxs-lookup"><span data-stu-id="f21f3-128">Because they can never be used as a base class, some run-time optimizations can make calling sealed class members slightly faster.</span></span>  
  
 <span data-ttu-id="f21f3-129">Methoden, Indexer, Eigenschaften oder Ereignisse einer abgeleiteten Klasse, die einen virtuellen Member der Basisklasse überschreiben, können diesen Member als versiegelt deklarieren.</span><span class="sxs-lookup"><span data-stu-id="f21f3-129">A method, indexer, property, or event, on a derived class that is overriding a virtual member of the base class can declare that member as sealed.</span></span> <span data-ttu-id="f21f3-130">Damit wird der virtuelle Aspekt des Members für jede weitere abgeleitete Klasse aufgehoben.</span><span class="sxs-lookup"><span data-stu-id="f21f3-130">This negates the virtual aspect of the member for any further derived class.</span></span> <span data-ttu-id="f21f3-131">Dazu wird in die Klassenmemberdeklaration das Schlüsselwort `sealed` vor dem Schlüsselwort [override](../../language-reference/keywords/override.md) eingefügt.</span><span class="sxs-lookup"><span data-stu-id="f21f3-131">This is accomplished by putting the `sealed` keyword before the [override](../../language-reference/keywords/override.md) keyword in the class member declaration.</span></span> <span data-ttu-id="f21f3-132">Beispiel:</span><span class="sxs-lookup"><span data-stu-id="f21f3-132">For example:</span></span>  
  
 [!code-csharp[csProgGuideInheritance#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#17)]  
  
## <a name="see-also"></a><span data-ttu-id="f21f3-133">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="f21f3-133">See also</span></span>

- [<span data-ttu-id="f21f3-134">C#-Programmierhandbuch</span><span class="sxs-lookup"><span data-stu-id="f21f3-134">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="f21f3-135">Klassen und Strukturen</span><span class="sxs-lookup"><span data-stu-id="f21f3-135">Classes and Structs</span></span>](./index.md)
- [<span data-ttu-id="f21f3-136">Vererbung</span><span class="sxs-lookup"><span data-stu-id="f21f3-136">Inheritance</span></span>](./inheritance.md)
- [<span data-ttu-id="f21f3-137">Methoden</span><span class="sxs-lookup"><span data-stu-id="f21f3-137">Methods</span></span>](./methods.md)
- [<span data-ttu-id="f21f3-138">Felder</span><span class="sxs-lookup"><span data-stu-id="f21f3-138">Fields</span></span>](./fields.md)
- [<span data-ttu-id="f21f3-139">Definieren von abstrakten Eigenschaften</span><span class="sxs-lookup"><span data-stu-id="f21f3-139">How to define abstract properties</span></span>](./how-to-define-abstract-properties.md)
