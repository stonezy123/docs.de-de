---
title: Varianz bei Delegaten (C#)
description: Hier erfahren Sie, wie Sie mit der Varianzunterstützung in .NET Methodensignaturen und Delegattypen in allen Delegaten vergleichen können.
ms.date: 07/20/2015
ms.assetid: 19de89d2-8224-4406-8964-2965b732b890
ms.openlocfilehash: 359f7051aa2eeb5d2dc9fef3d9ccb1e4aaebfb5c
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/24/2020
ms.locfileid: "91167742"
---
# <a name="variance-in-delegates-c"></a><span data-ttu-id="e6bea-103">Varianz bei Delegaten (C#)</span><span class="sxs-lookup"><span data-stu-id="e6bea-103">Variance in Delegates (C#)</span></span>

<span data-ttu-id="e6bea-104">Mit .NET Framework 3.5 wurde die Unterstützung von Varianz eingeführt, um Methodensignaturen und Delegattypen in allen Delegaten in C# vergleichen zu können.</span><span class="sxs-lookup"><span data-stu-id="e6bea-104">.NET Framework 3.5 introduced variance support for matching method signatures with delegate types in all delegates in C#.</span></span> <span data-ttu-id="e6bea-105">Das bedeutet, dass Sie Delegaten nicht nur Methoden mit übereinstimmenden Signaturen zuweisen können, sondern auch Methoden, die mehrere abgeleitete Typen zurückgeben (Kovarianz) oder die Parameter akzeptieren, die über weniger abgeleitete Typen verfügen, als durch den Delegattyp angegeben wurde (Kontravarianz).</span><span class="sxs-lookup"><span data-stu-id="e6bea-105">This means that you can assign to delegates not only methods that have matching signatures, but also methods that return more derived types (covariance) or that accept parameters that have less derived types (contravariance) than that specified by the delegate type.</span></span> <span data-ttu-id="e6bea-106">Dies umfasst generische und nicht generische Delegaten.</span><span class="sxs-lookup"><span data-stu-id="e6bea-106">This includes both generic and non-generic delegates.</span></span>  
  
 <span data-ttu-id="e6bea-107">Betrachten Sie beispielsweise folgenden Code, der zwei Klassen und zwei Delegaten aufweist: generisch und nicht generisch.</span><span class="sxs-lookup"><span data-stu-id="e6bea-107">For example, consider the following code, which has two classes and two delegates: generic and non-generic.</span></span>  
  
```csharp  
public class First { }  
public class Second : First { }  
public delegate First SampleDelegate(Second a);  
public delegate R SampleGenericDelegate<A, R>(A a);  
```  
  
 <span data-ttu-id="e6bea-108">Beim Erstellen von Delegaten vom Typ `SampleDelegate` oder `SampleGenericDelegate<A, R>` können Sie diesen Delegaten eine der folgenden Methoden zuweisen.</span><span class="sxs-lookup"><span data-stu-id="e6bea-108">When you create delegates of the `SampleDelegate` or `SampleGenericDelegate<A, R>` types, you can assign any one of the following methods to those delegates.</span></span>  
  
```csharp  
// Matching signature.  
public static First ASecondRFirst(Second second)  
{ return new First(); }  
  
// The return type is more derived.  
public static Second ASecondRSecond(Second second)  
{ return new Second(); }  
  
// The argument type is less derived.  
public static First AFirstRFirst(First first)  
{ return new First(); }  
  
// The return type is more derived
// and the argument type is less derived.  
public static Second AFirstRSecond(First first)  
{ return new Second(); }  
```  
  
 <span data-ttu-id="e6bea-109">Das folgende Codebeispiel veranschaulicht die implizite Konvertierung zwischen der Methodensignatur und dem Delegattyp.</span><span class="sxs-lookup"><span data-stu-id="e6bea-109">The following code example illustrates the implicit conversion between the method signature and the delegate type.</span></span>  
  
```csharp  
// Assigning a method with a matching signature
// to a non-generic delegate. No conversion is necessary.  
SampleDelegate dNonGeneric = ASecondRFirst;  
// Assigning a method with a more derived return type
// and less derived argument type to a non-generic delegate.  
// The implicit conversion is used.  
SampleDelegate dNonGenericConversion = AFirstRSecond;  
  
// Assigning a method with a matching signature to a generic delegate.  
// No conversion is necessary.  
SampleGenericDelegate<Second, First> dGeneric = ASecondRFirst;  
// Assigning a method with a more derived return type
// and less derived argument type to a generic delegate.  
// The implicit conversion is used.  
SampleGenericDelegate<Second, First> dGenericConversion = AFirstRSecond;  
```  
  
 <span data-ttu-id="e6bea-110">Weitere Beispiele finden Sie unter [Using Variance in Delegates (C#) (Verwenden von Varianz bei Delegaten (C#))](./using-variance-in-delegates.md) und [Using Variance for Func and Action Generic Delegates (C#) (Verwenden von Varianz für die generischen Delegaten Func und Action (C#))](./using-variance-for-func-and-action-generic-delegates.md).</span><span class="sxs-lookup"><span data-stu-id="e6bea-110">For more examples, see [Using Variance in Delegates (C#)](./using-variance-in-delegates.md) and [Using Variance for Func and Action Generic Delegates (C#)](./using-variance-for-func-and-action-generic-delegates.md).</span></span>  
  
## <a name="variance-in-generic-type-parameters"></a><span data-ttu-id="e6bea-111">Varianz in generischen Typparametern</span><span class="sxs-lookup"><span data-stu-id="e6bea-111">Variance in Generic Type Parameters</span></span>  

 <span data-ttu-id="e6bea-112">In .NET Framework 4 oder höher können Sie die implizierte Konvertierung zwischen Delegaten aktivieren. Das bedeutet, dass generische Delegaten, die über verschiedene von generischen Typparametern angegebene Typen verfügen, sich gegenseitig zugewiesen werden können, wenn die Typen voneinander geerbt werden. Dies ist für die Varianz erforderlich.</span><span class="sxs-lookup"><span data-stu-id="e6bea-112">In .NET Framework 4 or later you can enable implicit conversion between delegates, so that generic delegates that have different types specified by generic type parameters can be assigned to each other, if the types are inherited from each other as required by variance.</span></span>  
  
 <span data-ttu-id="e6bea-113">Sie müssen einen generischen Parameter in einem Delegaten mithilfe der Schlüsselwörter `in` oder `out` explizit als kovariant oder kontravariant deklarieren, um die implizite Konvertierung zu aktivieren.</span><span class="sxs-lookup"><span data-stu-id="e6bea-113">To enable implicit conversion, you must explicitly declare generic parameters in a delegate as covariant or contravariant by using the `in` or `out` keyword.</span></span>  
  
 <span data-ttu-id="e6bea-114">Im folgenden Codebeispiel wird veranschaulicht, wie Sie einen Delegaten erstellen können, der über einen kovarianten generischen Typparameter verfügt.</span><span class="sxs-lookup"><span data-stu-id="e6bea-114">The following code example shows how you can create a delegate that has a covariant generic type parameter.</span></span>  
  
```csharp  
// Type T is declared covariant by using the out keyword.  
public delegate T SampleGenericDelegate <out T>();  
  
public static void Test()  
{  
    SampleGenericDelegate <String> dString = () => " ";  
  
    // You can assign delegates to each other,  
    // because the type T is declared covariant.  
    SampleGenericDelegate <Object> dObject = dString;
}  
```  
  
 <span data-ttu-id="e6bea-115">Wenn Sie die Unterstützung von Varianz nur verwenden, um Methodensignaturen mit Delegaten zu vergleichen und nicht die Schlüsselwörter `in` und `out` verwenden, kann es möglicherweise passieren, dass Sie zwar Delegate mit identischen Lambdaausdrücken oder -Methoden instanziieren, aber keinen Delegaten einem anderen zuweisen können.</span><span class="sxs-lookup"><span data-stu-id="e6bea-115">If you use only variance support to match method signatures with delegate types and do not use the `in` and `out` keywords, you may find that sometimes you can instantiate delegates with identical lambda expressions or methods, but you cannot assign one delegate to another.</span></span>  
  
 <span data-ttu-id="e6bea-116">Im folgenden Codebeispiel kann `SampleGenericDelegate<String>` nicht expliziert in `SampleGenericDelegate<Object>` konvertiert werden, obwohl `String``Object` erbt.</span><span class="sxs-lookup"><span data-stu-id="e6bea-116">In the following code example, `SampleGenericDelegate<String>` cannot be explicitly converted to `SampleGenericDelegate<Object>`, although `String` inherits `Object`.</span></span> <span data-ttu-id="e6bea-117">Sie können dieses Problem beheben, indem Sie den generischen Parameter `T` mit dem Schlüsselwort `out` markieren.</span><span class="sxs-lookup"><span data-stu-id="e6bea-117">You can fix this problem by marking the generic parameter `T` with the `out` keyword.</span></span>  
  
```csharp  
public delegate T SampleGenericDelegate<T>();  
  
public static void Test()  
{  
    SampleGenericDelegate<String> dString = () => " ";  
  
    // You can assign the dObject delegate  
    // to the same lambda expression as dString delegate  
    // because of the variance support for
    // matching method signatures with delegate types.  
    SampleGenericDelegate<Object> dObject = () => " ";  
  
    // The following statement generates a compiler error  
    // because the generic type T is not marked as covariant.  
    // SampleGenericDelegate <Object> dObject = dString;  
  
}  
```  
  
### <a name="generic-delegates-that-have-variant-type-parameters-in-net"></a><span data-ttu-id="e6bea-118">Generische Delegaten mit varianten Typparametern in .NET</span><span class="sxs-lookup"><span data-stu-id="e6bea-118">Generic Delegates That Have Variant Type Parameters in .NET</span></span>

<span data-ttu-id="e6bea-119">Mit .NET Framework 4 wurde die Unterstützung von Varianz für generische Typparameter in verschiedenen vorhandenen generischen Delegaten eingeführt:</span><span class="sxs-lookup"><span data-stu-id="e6bea-119">.NET Framework 4 introduced variance support for generic type parameters in several existing generic delegates:</span></span>  
  
- <span data-ttu-id="e6bea-120">`Action`-Delegaten aus dem <xref:System>-Namespace, z.B. <xref:System.Action%601> und <xref:System.Action%602></span><span class="sxs-lookup"><span data-stu-id="e6bea-120">`Action` delegates from the <xref:System> namespace, for example, <xref:System.Action%601> and <xref:System.Action%602></span></span>  
  
- <span data-ttu-id="e6bea-121">`Func`-Delegaten aus dem <xref:System>-Namespace, z.B. <xref:System.Func%601> und <xref:System.Func%602></span><span class="sxs-lookup"><span data-stu-id="e6bea-121">`Func` delegates from the <xref:System> namespace, for example, <xref:System.Func%601> and <xref:System.Func%602></span></span>  
  
- <span data-ttu-id="e6bea-122">Der <xref:System.Predicate%601>-Delegat.</span><span class="sxs-lookup"><span data-stu-id="e6bea-122">The <xref:System.Predicate%601> delegate</span></span>  
  
- <span data-ttu-id="e6bea-123">Der <xref:System.Comparison%601>-Delegat.</span><span class="sxs-lookup"><span data-stu-id="e6bea-123">The <xref:System.Comparison%601> delegate</span></span>  
  
- <span data-ttu-id="e6bea-124">Der <xref:System.Converter%602>-Delegat.</span><span class="sxs-lookup"><span data-stu-id="e6bea-124">The <xref:System.Converter%602> delegate</span></span>  
  
 <span data-ttu-id="e6bea-125">Weitere Informationen und Beispiele finden Sie unter [Using Variance for Func and Action Generic Delegates (C#) (Verwenden von Varianz für die generischen Delegaten Func und Action (C#))](./using-variance-for-func-and-action-generic-delegates.md).</span><span class="sxs-lookup"><span data-stu-id="e6bea-125">For more information and examples, see [Using Variance for Func and Action Generic Delegates (C#)](./using-variance-for-func-and-action-generic-delegates.md).</span></span>  
  
### <a name="declaring-variant-type-parameters-in-generic-delegates"></a><span data-ttu-id="e6bea-126">Angeben varianter Typparameter in generischen Delegaten</span><span class="sxs-lookup"><span data-stu-id="e6bea-126">Declaring Variant Type Parameters in Generic Delegates</span></span>  

 <span data-ttu-id="e6bea-127">Wenn ein generischer Delegat über kovariante oder kontravariante generische Typparameter verfügt, kann er als *varianter generischer Delegat* bezeichnet werden.</span><span class="sxs-lookup"><span data-stu-id="e6bea-127">If a generic delegate has covariant or contravariant generic type parameters, it can be referred to as a *variant generic delegate*.</span></span>  
  
 <span data-ttu-id="e6bea-128">Sie können einen generischen Typparameter mithilfe des Schlüsselworts `out` in einem generischen Delegaten als kovariant deklarieren.</span><span class="sxs-lookup"><span data-stu-id="e6bea-128">You can declare a generic type parameter covariant in a generic delegate by using the `out` keyword.</span></span> <span data-ttu-id="e6bea-129">Der kovariante Typ kann nur als Typ von Methodenrückgaben und nicht von Methodenargumenten verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="e6bea-129">The covariant type can be used only as a method return type and not as a type of method arguments.</span></span> <span data-ttu-id="e6bea-130">Das folgende Codebeispiel zeigt, wie Sie einen kovarianten generischen Delegaten deklarieren.</span><span class="sxs-lookup"><span data-stu-id="e6bea-130">The following code example shows how to declare a covariant generic delegate.</span></span>  
  
```csharp  
public delegate R DCovariant<out R>();  
```  
  
 <span data-ttu-id="e6bea-131">Sie können einen generischen Typparameter mithilfe des Schlüsselworts `in` in einem generischen Delegaten als kontravariant deklarieren.</span><span class="sxs-lookup"><span data-stu-id="e6bea-131">You can declare a generic type parameter contravariant in a generic delegate by using the `in` keyword.</span></span> <span data-ttu-id="e6bea-132">Der kontravariante Typ kann nur als Typ von Methodenrückgaben und nicht von Methodenargumenten verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="e6bea-132">The contravariant type can be used only as a type of method arguments and not as a method return type.</span></span> <span data-ttu-id="e6bea-133">Das folgende Codebeispiel zeigt, wie Sie einen kontravarianten generischen Delegaten deklarieren.</span><span class="sxs-lookup"><span data-stu-id="e6bea-133">The following code example shows how to declare a contravariant generic delegate.</span></span>  
  
```csharp  
public delegate void DContravariant<in A>(A a);  
```  
  
> [!IMPORTANT]
> <span data-ttu-id="e6bea-134">Die Parameter `ref`, `in` und `out` in C# können nicht als variant markiert werden.</span><span class="sxs-lookup"><span data-stu-id="e6bea-134">`ref`, `in`, and `out` parameters in C# can't be marked as variant.</span></span>  
  
 <span data-ttu-id="e6bea-135">Es ist auch möglich, Varianz und Kovarianz im gleichen Delegaten, aber für verschiedene Typparameter, zu unterstützen.</span><span class="sxs-lookup"><span data-stu-id="e6bea-135">It is also possible to support both variance and covariance in the same delegate, but for different type parameters.</span></span> <span data-ttu-id="e6bea-136">Dies wird im folgenden Beispiel gezeigt.</span><span class="sxs-lookup"><span data-stu-id="e6bea-136">This is shown in the following example.</span></span>  
  
```csharp  
public delegate R DVariant<in A, out R>(A a);  
```  
  
### <a name="instantiating-and-invoking-variant-generic-delegates"></a><span data-ttu-id="e6bea-137">Instanziieren und Aufrufen von varianten generischen Delegaten</span><span class="sxs-lookup"><span data-stu-id="e6bea-137">Instantiating and Invoking Variant Generic Delegates</span></span>  

 <span data-ttu-id="e6bea-138">Sie können variante Delegaten genau wie invariante Delegaten instanziieren und aufrufen.</span><span class="sxs-lookup"><span data-stu-id="e6bea-138">You can instantiate and invoke variant delegates just as you instantiate and invoke invariant delegates.</span></span> <span data-ttu-id="e6bea-139">Im folgenden Beispiel wird der Delegat durch einen Lambdaausdruck instanziiert.</span><span class="sxs-lookup"><span data-stu-id="e6bea-139">In the following example, the delegate is instantiated by a lambda expression.</span></span>  
  
```csharp  
DVariant<String, String> dvariant = (String str) => str + " ";  
dvariant("test");  
```  
  
### <a name="combining-variant-generic-delegates"></a><span data-ttu-id="e6bea-140">Kombinieren von varianten generischen Delegaten</span><span class="sxs-lookup"><span data-stu-id="e6bea-140">Combining Variant Generic Delegates</span></span>  

<span data-ttu-id="e6bea-141">Kombinieren Sie keine varianten Delegaten.</span><span class="sxs-lookup"><span data-stu-id="e6bea-141">Don't combine variant delegates.</span></span> <span data-ttu-id="e6bea-142">Die Methode <xref:System.Delegate.Combine%2A> unterstützt keine Konvertierung von varianten Delegaten und erwartet, dass Delegaten vom exakt gleichen Typ sind.</span><span class="sxs-lookup"><span data-stu-id="e6bea-142">The <xref:System.Delegate.Combine%2A> method does not support variant delegate conversion and expects delegates to be of exactly the same type.</span></span> <span data-ttu-id="e6bea-143">Es kann zu einer Laufzeitausnahme führen, wenn Sie Delegaten entweder mit der Methode <xref:System.Delegate.Combine%2A> oder dem Operator `+` kombinieren, wie im folgenden Codebeispiel gezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="e6bea-143">This can lead to a run-time exception when you combine delegates either by using the <xref:System.Delegate.Combine%2A> method or by using the `+` operator, as shown in the following code example.</span></span>  
  
```csharp  
Action<object> actObj = x => Console.WriteLine("object: {0}", x);  
Action<string> actStr = x => Console.WriteLine("string: {0}", x);  
// All of the following statements throw exceptions at run time.  
// Action<string> actCombine = actStr + actObj;  
// actStr += actObj;  
// Delegate.Combine(actStr, actObj);  
```  
  
## <a name="variance-in-generic-type-parameters-for-value-and-reference-types"></a><span data-ttu-id="e6bea-144">Varianz in generischen Typparametern für Wert- und Referenztypen</span><span class="sxs-lookup"><span data-stu-id="e6bea-144">Variance in Generic Type Parameters for Value and Reference Types</span></span>  

 <span data-ttu-id="e6bea-145">Varianz für generische Typparameter wird nur für Referenztypen unterstützt.</span><span class="sxs-lookup"><span data-stu-id="e6bea-145">Variance for generic type parameters is supported for reference types only.</span></span> <span data-ttu-id="e6bea-146">`DVariant<int>` kann z.B. nicht implizit in `DVariant<Object>` oder `DVariant<long>` konvertiert werden, da es sich bei „Integer“ um einen Werttyp handelt.</span><span class="sxs-lookup"><span data-stu-id="e6bea-146">For example, `DVariant<int>` can't be implicitly converted to `DVariant<Object>` or `DVariant<long>`, because integer is a value type.</span></span>  
  
 <span data-ttu-id="e6bea-147">Das folgende Beispiel veranschaulicht, dass Varianz in generischen Typparametern für Werttypen nicht unterstützt wird.</span><span class="sxs-lookup"><span data-stu-id="e6bea-147">The following example demonstrates that variance in generic type parameters is not supported for value types.</span></span>  
  
```csharp  
// The type T is covariant.  
public delegate T DVariant<out T>();  
  
// The type T is invariant.  
public delegate T DInvariant<T>();  
  
public static void Test()  
{  
    int i = 0;  
    DInvariant<int> dInt = () => i;  
    DVariant<int> dVariantInt = () => i;  
  
    // All of the following statements generate a compiler error  
    // because type variance in generic parameters is not supported  
    // for value types, even if generic type parameters are declared variant.  
    // DInvariant<Object> dObject = dInt;  
    // DInvariant<long> dLong = dInt;  
    // DVariant<Object> dVariantObject = dVariantInt;  
    // DVariant<long> dVariantLong = dVariantInt;
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="e6bea-148">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="e6bea-148">See also</span></span>

- [<span data-ttu-id="e6bea-149">Generics</span><span class="sxs-lookup"><span data-stu-id="e6bea-149">Generics</span></span>](../../../../standard/generics/index.md)
- [<span data-ttu-id="e6bea-150">Verwenden von Varianz für die generischen Delegaten Func und Action (C#)</span><span class="sxs-lookup"><span data-stu-id="e6bea-150">Using Variance for Func and Action Generic Delegates (C#)</span></span>](./using-variance-for-func-and-action-generic-delegates.md)
- [<span data-ttu-id="e6bea-151">Kombinieren von Delegaten (Multicastdelegaten)</span><span class="sxs-lookup"><span data-stu-id="e6bea-151">How to combine delegates (Multicast Delegates)</span></span>](../../delegates/how-to-combine-delegates-multicast-delegates.md)
