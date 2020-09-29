---
description: Modifizierer für out-Parameter – C#-Verweis
title: Modifizierer für out-Parameter – C#-Verweis
ms.date: 03/19/2020
helpviewer_keywords:
- parameters [C#], out
- out parameters [C#]
ms.openlocfilehash: 6addfa3a654c0bb4e10213a3fb4fc0368f2570b2
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/24/2020
ms.locfileid: "91200185"
---
# <a name="out-parameter-modifier-c-reference"></a><span data-ttu-id="8deec-103">Modifizierer für out-Parameter (C#-Verweis)</span><span class="sxs-lookup"><span data-stu-id="8deec-103">out parameter modifier (C# Reference)</span></span>

<span data-ttu-id="8deec-104">Das Schlüsselwort `out` bewirkt, dass Argumente per Verweis übergeben werden.</span><span class="sxs-lookup"><span data-stu-id="8deec-104">The `out` keyword causes arguments to be passed by reference.</span></span> <span data-ttu-id="8deec-105">Es stellt den formalen Parameter als Alias für das Argument dar, das eine Variable sein muss.</span><span class="sxs-lookup"><span data-stu-id="8deec-105">It makes the formal parameter an alias for the argument, which must be a variable.</span></span> <span data-ttu-id="8deec-106">Anders ausgedrückt, jede Operation mit dem Parameter wird mit dem Argument durchgeführt.</span><span class="sxs-lookup"><span data-stu-id="8deec-106">In other words, any operation on the parameter is made on the argument.</span></span> <span data-ttu-id="8deec-107">Dies entspricht dem Schlüsselwort [ref](ref.md), mit Ausnahme davon, dass bei `ref` die Variable initialisiert sein muss, bevor sie übergeben wird.</span><span class="sxs-lookup"><span data-stu-id="8deec-107">It is like the [ref](ref.md) keyword, except that `ref` requires that the variable be initialized before it is passed.</span></span> <span data-ttu-id="8deec-108">Es ähnelt auch dem Schlüsselwort [in](in-parameter-modifier.md). Allerdings lässt `in` nicht zu, dass die aufgerufene Methode den Argumentwert verändern kann.</span><span class="sxs-lookup"><span data-stu-id="8deec-108">It is also like the [in](in-parameter-modifier.md) keyword, except that `in` does not allow the called method to modify the argument value.</span></span> <span data-ttu-id="8deec-109">Um einen Parameter `out` zu verwenden, müssen sowohl die Methodendefinition als auch die aufrufende Methode das Schlüsselwort `out` explizit verwenden.</span><span class="sxs-lookup"><span data-stu-id="8deec-109">To use an `out` parameter, both the method definition and the calling method must explicitly use the `out` keyword.</span></span> <span data-ttu-id="8deec-110">Zum Beispiel:</span><span class="sxs-lookup"><span data-stu-id="8deec-110">For example:</span></span>  
  
[!code-csharp-interactive[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#1)]  

> [!NOTE]
> <span data-ttu-id="8deec-111">Das Schlüsselwort `out` kann auch mit einem generischen Typparameter verwendet werden, um anzugeben, dass der Typparameter kovariant ist.</span><span class="sxs-lookup"><span data-stu-id="8deec-111">The `out` keyword can also be used with a generic type parameter to specify that the type parameter is covariant.</span></span> <span data-ttu-id="8deec-112">Weitere Informationen zur Verwendung des Schlüsselworts `out` in diesem Kontext finden Sie unter [out (generischer Modifizierer)](out-generic-modifier.md).</span><span class="sxs-lookup"><span data-stu-id="8deec-112">For more information on the use of the `out` keyword in this context, see [out (Generic Modifier)](out-generic-modifier.md).</span></span>
  
<span data-ttu-id="8deec-113">Variablen, die als `out`-Argumente übergeben wurden, müssen nicht initialisiert werden, bevor sie in einen Methodenaufruf übergeben werden.</span><span class="sxs-lookup"><span data-stu-id="8deec-113">Variables passed as `out` arguments do not have to be initialized before being passed in a method call.</span></span> <span data-ttu-id="8deec-114">Die aufgerufene Methode ist jedoch erforderlich, um einen Wert zuzuweisen, bevor die Methode zurückgegeben wird.</span><span class="sxs-lookup"><span data-stu-id="8deec-114">However, the called method is required to assign a value before the method returns.</span></span>  
  
<span data-ttu-id="8deec-115">Die Schlüsselwörter `in`, `ref` und `out` werden nicht als Teil der Methodensignatur zum Zwecke der Überladungsauflösung betrachtet.</span><span class="sxs-lookup"><span data-stu-id="8deec-115">The `in`, `ref`, and `out` keywords are not considered part of the method signature for the purpose of overload resolution.</span></span> <span data-ttu-id="8deec-116">Aus diesem Grund können die Methoden nicht überladen werden, wenn der einzige Unterschied darin besteht, dass eine Methode ein `ref`- oder `in`-Argument übernimmt und die andere ein `out`-Argument.</span><span class="sxs-lookup"><span data-stu-id="8deec-116">Therefore, methods cannot be overloaded if the only difference is that one method takes a `ref` or `in` argument and the other takes an `out` argument.</span></span> <span data-ttu-id="8deec-117">Der folgende Code wird z. B. nicht kompiliert:</span><span class="sxs-lookup"><span data-stu-id="8deec-117">The following code, for example, will not compile:</span></span>  
  
```csharp
class CS0663_Example
{
    // Compiler error CS0663: "Cannot define overloaded
    // methods that differ only on ref and out".
    public void SampleMethod(out int i) { }
    public void SampleMethod(ref int i) { }
}
```
  
<span data-ttu-id="8deec-118">Überladen ist zwar legal, wenn jedoch eine Methode ein `ref`-, `in`- oder `out`-Argument übernimmt und die andere über keinen dieser Modifizierer verfügt, gilt Folgendes:</span><span class="sxs-lookup"><span data-stu-id="8deec-118">Overloading is legal, however, if one method takes a `ref`, `in`, or `out` argument and the other has none of those modifiers, like this:</span></span>  
  
[!code-csharp[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#2)]  

<span data-ttu-id="8deec-119">Der Compiler wählt die beste Überladung aus, indem er die Parametermodifizierer auf der Aufrufsite den im Methodenaufruf verwendeten Parametermodifizierern zuordnet.</span><span class="sxs-lookup"><span data-stu-id="8deec-119">The compiler chooses the best overload by matching the parameter modifiers at the call site to the parameter modifiers used in the method call.</span></span>

<span data-ttu-id="8deec-120">Eigenschaften sind keine Variablen und können daher nicht als `out`-Parameter übergeben werden.</span><span class="sxs-lookup"><span data-stu-id="8deec-120">Properties are not variables and therefore cannot be passed as `out` parameters.</span></span>
  
<span data-ttu-id="8deec-121">Sie können keines der Schlüsselwörter `in`, `ref` und `out` für die folgenden Methodentypen verwenden:</span><span class="sxs-lookup"><span data-stu-id="8deec-121">You can't use the `in`, `ref`, and `out` keywords for the following kinds of methods:</span></span>  
  
- <span data-ttu-id="8deec-122">Asynchrone Methoden, die Sie mit dem [async](./async.md)-Modifizierer definieren.</span><span class="sxs-lookup"><span data-stu-id="8deec-122">Async methods, which you define by using the [async](./async.md) modifier.</span></span>  
  
- <span data-ttu-id="8deec-123">Iterator-Methoden, die eine [yield return](./yield.md)- oder `yield break`-Anweisung enthalten.</span><span class="sxs-lookup"><span data-stu-id="8deec-123">Iterator methods, which include a [yield return](./yield.md) or `yield break` statement.</span></span>  

<span data-ttu-id="8deec-124">Für [Erweiterungsmethoden](../../programming-guide/classes-and-structs/extension-methods.md) gelten die folgenden Einschränkungen:</span><span class="sxs-lookup"><span data-stu-id="8deec-124">In addition, [extension methods](../../programming-guide/classes-and-structs/extension-methods.md) have the following restrictions:</span></span>

- <span data-ttu-id="8deec-125">Das `out`-Schlüsselwort kann nicht für das erste Argument einer Erweiterungsmethode verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="8deec-125">The `out` keyword cannot be used on the first argument of an extension method.</span></span>
- <span data-ttu-id="8deec-126">Das `ref`-Schlüsselwort kann nicht für das erste Argument einer Erweiterungsmethode verwendet werden, wenn es sich bei dem Argument nicht um eine Struktur handelt oder ein generischer Typ nicht auf eine Struktur beschränkt ist.</span><span class="sxs-lookup"><span data-stu-id="8deec-126">The `ref` keyword cannot be used on the first argument of an extension method when the argument is not a struct, or a generic type not constrained to be a struct.</span></span>
- <span data-ttu-id="8deec-127">Das `in`-Schlüsselwort kann nur verwendet werden, wenn das erste Argument eine Struktur ist.</span><span class="sxs-lookup"><span data-stu-id="8deec-127">The `in` keyword cannot be used unless the first argument is a struct.</span></span> <span data-ttu-id="8deec-128">Das `in`-Schlüsselwort kann nicht für einen generischen Typ verwendet werden – selbst bei einer Beschränkung auf eine Struktur.</span><span class="sxs-lookup"><span data-stu-id="8deec-128">The `in` keyword cannot be used on any generic type, even when constrained to be a struct.</span></span>

## <a name="declaring-out-parameters"></a><span data-ttu-id="8deec-129">Deklarieren eines `out`-Parameters</span><span class="sxs-lookup"><span data-stu-id="8deec-129">Declaring `out` parameters</span></span>

<span data-ttu-id="8deec-130">Das Deklarieren einer Methode mit `out`-Argumenten ist eine gängige Methode, um mehrere Werte zurückzugeben.</span><span class="sxs-lookup"><span data-stu-id="8deec-130">Declaring a method with `out` arguments is a classic workaround to return multiple values.</span></span> <span data-ttu-id="8deec-131">Ab C# 7.0 sollten Sie [Werttupel](../builtin-types/value-tuples.md) für ähnliche Szenarien berücksichtigen.</span><span class="sxs-lookup"><span data-stu-id="8deec-131">Beginning with C# 7.0, consider [value tuples](../builtin-types/value-tuples.md) for similar scenarios.</span></span> <span data-ttu-id="8deec-132">Im folgenden Beispiel wird `out` verwendet, um mit einem Methodenaufruf drei Variablen zurückzugeben.</span><span class="sxs-lookup"><span data-stu-id="8deec-132">The following example uses `out` to return three variables with a single method call.</span></span> <span data-ttu-id="8deec-133">Das dritte Argument ist NULL zugewiesen.</span><span class="sxs-lookup"><span data-stu-id="8deec-133">The third argument is assigned to null.</span></span> <span data-ttu-id="8deec-134">Dadurch können Methoden Werte optional zurückgeben.</span><span class="sxs-lookup"><span data-stu-id="8deec-134">This enables methods to return values optionally.</span></span>  
  
[!code-csharp-interactive[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#3)]  

## <a name="calling-a-method-with-an-out-argument"></a><span data-ttu-id="8deec-135">Aufrufen einer Methode mit einem `out`-Argument</span><span class="sxs-lookup"><span data-stu-id="8deec-135">Calling a method with an `out` argument</span></span>

<span data-ttu-id="8deec-136">In C# 6 und früheren Versionen müssen Sie eine Variable in einer separaten Anweisung deklarieren, bevor Sie es als ein `out`-Argument übergeben.</span><span class="sxs-lookup"><span data-stu-id="8deec-136">In C# 6 and earlier, you must declare a variable in a separate statement before you pass it as an `out` argument.</span></span> <span data-ttu-id="8deec-137">Das folgende Beispiel deklariert eine Variable namens `number`, bevor sie an die Methode [Int32.TryParse](xref:System.Int32.TryParse(System.String,System.Int32@)) übergeben wird, die versucht, eine Zeichenfolge in eine Zahl umzuwandeln.</span><span class="sxs-lookup"><span data-stu-id="8deec-137">The following example declares a variable named `number` before it is passed to the [Int32.TryParse](xref:System.Int32.TryParse(System.String,System.Int32@)) method, which attempts to convert a string to a number.</span></span>

[!code-csharp-interactive[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#4)]  

<span data-ttu-id="8deec-138">Ab C# 7.0 können Sie in der Argumentliste des Methodenaufrufs anstatt in einer separaten Variablendeklaration die `out`-Variable deklarieren.</span><span class="sxs-lookup"><span data-stu-id="8deec-138">Starting with C# 7.0, you can declare the `out` variable in the argument list of the method call, rather than in a separate variable declaration.</span></span> <span data-ttu-id="8deec-139">Dies erzeugt kompakteren, lesbaren Code und verhindert auch, dass Sie versehentlich der Variable vor dem Aufruf der Methode einen Wert zuweisen.</span><span class="sxs-lookup"><span data-stu-id="8deec-139">This produces more compact, readable code, and also prevents you from inadvertently assigning a value to the variable before the method call.</span></span> <span data-ttu-id="8deec-140">Das folgende Beispiel ähnelt dem vorherigen Beispiel, außer dass es die `number`-Variable im Aufruf der Methode [Int32.TryParse](xref:System.Int32.TryParse(System.String,System.Int32@))) definiert.</span><span class="sxs-lookup"><span data-stu-id="8deec-140">The following example is like the previous example, except that it defines the `number` variable in the call to the [Int32.TryParse](xref:System.Int32.TryParse(System.String,System.Int32@)) method.</span></span>

[!code-csharp-interactive[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#5)]  

<span data-ttu-id="8deec-141">Im vorherigen Beispiel ist die `number`-Variable stark als `int` typisiert.</span><span class="sxs-lookup"><span data-stu-id="8deec-141">In the previous example, the `number` variable is strongly typed as an `int`.</span></span> <span data-ttu-id="8deec-142">Sie können auch eine implizit typisierte lokale Variable deklarieren, wie es im folgenden Beispiel getan wird.</span><span class="sxs-lookup"><span data-stu-id="8deec-142">You can also declare an implicitly typed local variable, as the following example does.</span></span>

[!code-csharp-interactive[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#6)]  

## <a name="c-language-specification"></a><span data-ttu-id="8deec-143">C#-Programmiersprachenspezifikation</span><span class="sxs-lookup"><span data-stu-id="8deec-143">C# Language Specification</span></span>  

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="8deec-144">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="8deec-144">See also</span></span>

- [<span data-ttu-id="8deec-145">C#-Referenz</span><span class="sxs-lookup"><span data-stu-id="8deec-145">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="8deec-146">C#-Programmierhandbuch</span><span class="sxs-lookup"><span data-stu-id="8deec-146">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="8deec-147">C#-Schlüsselwörter</span><span class="sxs-lookup"><span data-stu-id="8deec-147">C# Keywords</span></span>](./index.md)
- [<span data-ttu-id="8deec-148">Methodenparameter</span><span class="sxs-lookup"><span data-stu-id="8deec-148">Method Parameters</span></span>](./method-parameters.md)
