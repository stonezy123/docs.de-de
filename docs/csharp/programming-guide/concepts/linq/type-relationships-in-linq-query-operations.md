---
title: Typbeziehungen in LINQ-Abfragevorgängen (C#)
description: Erfahren Sie, welche Variablentypen in einer LINQ-Abfrage miteinander in Zusammenhang stehen. LINQ-Abfragevorgänge sind in der Datenquelle, in der Abfrage und in der Ausführung stark typisiert.
ms.date: 07/20/2015
helpviewer_keywords:
- inferring type information [LINQ in C#]
- data sources [LINQ in C#], type relationships
- queries [LINQ in C#], type relationships
- relationships [LINQ in C#]
- type relationships [LINQ in C#]
- variable relationships [LINQ in C#]
- type information inferred [LINQ in C#]
- data transformations [LINQ in C#]
- LINQ [C#], type relationships
ms.assetid: 99118938-d47c-4d7e-bb22-2657a9f95268
ms.openlocfilehash: 78cdb550e59bc82386d34f0e2bf6b1cae11d72de
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/24/2020
ms.locfileid: "91203981"
---
# <a name="type-relationships-in-linq-query-operations-c"></a><span data-ttu-id="406f3-104">Typbeziehungen in LINQ-Abfragevorgängen (C#)</span><span class="sxs-lookup"><span data-stu-id="406f3-104">Type Relationships in LINQ Query Operations (C#)</span></span>

<span data-ttu-id="406f3-105">Um Abfragen effektiv erstellen zu können, ist es wichtig, dass Sie verstehen, wie die Variablentypen in einer vollständigen Abfrageoperation miteinander zusammenhängen.</span><span class="sxs-lookup"><span data-stu-id="406f3-105">To write queries effectively, you should understand how types of the variables in a complete query operation all relate to each other.</span></span> <span data-ttu-id="406f3-106">Wenn Sie diese Beziehungen verstehen, können Sie die LINQ-Beispiele und die Codebeispiele in der Dokumentation besser nachvollziehen.</span><span class="sxs-lookup"><span data-stu-id="406f3-106">If you understand these relationships you will more easily comprehend the LINQ samples and code examples in the documentation.</span></span> <span data-ttu-id="406f3-107">Weiterhin können Sie dann besser verstehen, was im Hintergrund abläuft, wenn Variablen implizit mithilfe von `var` typisiert werden.</span><span class="sxs-lookup"><span data-stu-id="406f3-107">Furthermore, you will understand what occurs behind the scenes when variables are implicitly typed by using `var`.</span></span>  
  
 <span data-ttu-id="406f3-108">LINQ-Abfrageoperationen sind in der Datenquelle, in der Abfrage selbst und in der Abfrageausführung stark typisiert.</span><span class="sxs-lookup"><span data-stu-id="406f3-108">LINQ query operations are strongly typed in the data source, in the query itself, and in the query execution.</span></span> <span data-ttu-id="406f3-109">Die Variablentypen in der Abfrage müssen mit den Elementtypen in der Datenquelle und mit dem Typ der Iterationsvariablen in der `foreach`-Anweisung kompatibel sein.</span><span class="sxs-lookup"><span data-stu-id="406f3-109">The type of the variables in the query must be compatible with the type of the elements in the data source and with the type of the iteration variable in the `foreach` statement.</span></span> <span data-ttu-id="406f3-110">Diese starke Typisierung stellt sicher, dass Typfehler zur Kompilierzeit abgefangen werden, sodass sie korrigiert werden können, bevor die Benutzer sie ausführen.</span><span class="sxs-lookup"><span data-stu-id="406f3-110">This strong typing guarantees that type errors are caught at compile time when they can be corrected before users encounter them.</span></span>  
  
 <span data-ttu-id="406f3-111">Um diese Typbeziehungen zu veranschaulichen, wird in den meisten folgenden Beispielen explizite Typisierung für alle Variablen angewendet.</span><span class="sxs-lookup"><span data-stu-id="406f3-111">In order to demonstrate these type relationships, most of the examples that follow use explicit typing for all variables.</span></span> <span data-ttu-id="406f3-112">Im letzten Beispiel wird gezeigt, wie diese Prinzipien auch dann gelten, wenn Sie die implizite Typisierung mithilfe von [var](../../../language-reference/keywords/var.md) verwenden.</span><span class="sxs-lookup"><span data-stu-id="406f3-112">The last example shows how the same principles apply even when you use implicit typing by using [var](../../../language-reference/keywords/var.md).</span></span>  
  
## <a name="queries-that-do-not-transform-the-source-data"></a><span data-ttu-id="406f3-113">Abfragen, bei denen die Quelldaten nicht transformiert werden</span><span class="sxs-lookup"><span data-stu-id="406f3-113">Queries that do not Transform the Source Data</span></span>  

 <span data-ttu-id="406f3-114">Die folgende Abbildung zeigt eine LINQ to Objects-Abfrageoperation für Objekte, die keine Transformationen der Daten ausführt.</span><span class="sxs-lookup"><span data-stu-id="406f3-114">The following illustration shows a LINQ to Objects query operation that performs no transformations on the data.</span></span> <span data-ttu-id="406f3-115">Die Quelle enthält eine Sequenz von Zeichenfolgen, und die Abfrageausgabe ist ebenfalls eine Sequenz von Zeichenfolgen.</span><span class="sxs-lookup"><span data-stu-id="406f3-115">The source contains a sequence of strings and the query output is also a sequence of strings.</span></span>  
  
 ![Diagramm, dass die Beziehung von Datentypen in einer LINQ-Abfrage zeigt.](./media/type-relationships-in-linq-query-operations/linq-query-data-type-relation.png)  
  
1. <span data-ttu-id="406f3-117">Das Typargument der Datenquelle bestimmt den Typ der Bereichsvariablen.</span><span class="sxs-lookup"><span data-stu-id="406f3-117">The type argument of the data source determines the type of the range variable.</span></span>  
  
2. <span data-ttu-id="406f3-118">Der Typ des Objekts, das ausgewählt ist, bestimmt den Typ der Abfragevariablen.</span><span class="sxs-lookup"><span data-stu-id="406f3-118">The type of the object that is selected determines the type of the query variable.</span></span> <span data-ttu-id="406f3-119">In diesem Beispiel ist `name` eine Zeichenfolge.</span><span class="sxs-lookup"><span data-stu-id="406f3-119">Here `name` is a string.</span></span> <span data-ttu-id="406f3-120">Daher ist die Abfragevariable ein `IEnumerable<string>`.</span><span class="sxs-lookup"><span data-stu-id="406f3-120">Therefore, the query variable is an `IEnumerable<string>`.</span></span>  
  
3. <span data-ttu-id="406f3-121">Die Abfragevariable durchläuft in der `foreach`-Anweisung verschiedene Iterationen.</span><span class="sxs-lookup"><span data-stu-id="406f3-121">The query variable is iterated over in the `foreach` statement.</span></span> <span data-ttu-id="406f3-122">Da die Abfragevariable eine Sequenz von Zeichenfolgen ist, ist die Iterationsvariable ebenfalls eine Zeichenfolge.</span><span class="sxs-lookup"><span data-stu-id="406f3-122">Because the query variable is a sequence of strings, the iteration variable is also a string.</span></span>  
  
## <a name="queries-that-transform-the-source-data"></a><span data-ttu-id="406f3-123">Abfragen, bei denen die Quelldaten transformiert werden</span><span class="sxs-lookup"><span data-stu-id="406f3-123">Queries that Transform the Source Data</span></span>  

 <span data-ttu-id="406f3-124">Die folgende Abbildung zeigt eine [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)]-Abfrageoperation, die eine einfache Datentransformation ausführt.</span><span class="sxs-lookup"><span data-stu-id="406f3-124">The following illustration shows a [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] query operation that performs a simple transformation on the data.</span></span> <span data-ttu-id="406f3-125">Die Abfrage verwendet eine Sequenz von `Customer`-Objekten als Eingabe und wählt nur die `Name`-Eigenschaft im Ergebnis aus.</span><span class="sxs-lookup"><span data-stu-id="406f3-125">The query takes a sequence of `Customer` objects as input, and selects only the `Name` property in the result.</span></span> <span data-ttu-id="406f3-126">Da `Name` eine Zeichenfolge ist, erzeugt die Abfrage eine Sequenz von Zeichenfolgen als Ausgabe.</span><span class="sxs-lookup"><span data-stu-id="406f3-126">Because `Name` is a string, the query produces a sequence of strings as output.</span></span>  
  
 ![Diagramm, das eine Abfrage zeigt, die den Datentyp transformiert.](./media/type-relationships-in-linq-query-operations/linq-query-transform-data-type.png)  
  
1. <span data-ttu-id="406f3-128">Das Typargument der Datenquelle bestimmt den Typ der Bereichsvariablen.</span><span class="sxs-lookup"><span data-stu-id="406f3-128">The type argument of the data source determines the type of the range variable.</span></span>  
  
2. <span data-ttu-id="406f3-129">Die `select`-Anweisung gibt die `Name`-Eigenschaft statt des vollständigen `Customer`-Objekts zurück.</span><span class="sxs-lookup"><span data-stu-id="406f3-129">The `select` statement returns the `Name` property instead of the complete `Customer` object.</span></span> <span data-ttu-id="406f3-130">Da `Name` eine Zeichenfolge ist, lautet das Typargument von `custNameQuery` nicht `Customer`, sondern `string`.</span><span class="sxs-lookup"><span data-stu-id="406f3-130">Because `Name` is a string, the type argument of `custNameQuery` is `string`, not `Customer`.</span></span>  
  
3. <span data-ttu-id="406f3-131">Da `custNameQuery` eine Sequenz von Zeichenfolgen ist, muss die Iterationsvariable der `foreach`-Schleife auch ein `string` sein.</span><span class="sxs-lookup"><span data-stu-id="406f3-131">Because `custNameQuery` is a sequence of strings, the `foreach` loop's iteration variable must also be a `string`.</span></span>  
  
 <span data-ttu-id="406f3-132">Die folgende Abbildung zeigt eine etwas komplexere Transformation.</span><span class="sxs-lookup"><span data-stu-id="406f3-132">The following illustration shows a slightly more complex transformation.</span></span> <span data-ttu-id="406f3-133">Die `select`-Anweisung gibt einen anonymen Typ zurück, der nur zwei Member des ursprünglichen `Customer`-Objekts erfasst.</span><span class="sxs-lookup"><span data-stu-id="406f3-133">The `select` statement returns an anonymous type that captures just two members of the original `Customer` object.</span></span>  
  
 ![Diagramm, das eine komplexere Abfrage zeigt, die den Datentyp transformiert.](./media/type-relationships-in-linq-query-operations/linq-complex-query-transform-data-type.png)  
  
1. <span data-ttu-id="406f3-135">Das Typargument der Datenquelle ist immer der Typ der Bereichsvariablen in der Abfrage.</span><span class="sxs-lookup"><span data-stu-id="406f3-135">The type argument of the data source is always the type of the range variable in the query.</span></span>  
  
2. <span data-ttu-id="406f3-136">Da die `select`-Anweisung einen anonymen Typ erzeugt, muss die Abfragevariable mithilfe von `var` implizit typisiert werden.</span><span class="sxs-lookup"><span data-stu-id="406f3-136">Because the `select` statement produces an anonymous type, the query variable must be implicitly typed by using `var`.</span></span>  
  
3. <span data-ttu-id="406f3-137">Da der Typ der Abfragevariablen implizit ist, muss die Iterationsvariable in der `foreach`-Schleife auch implizit sein.</span><span class="sxs-lookup"><span data-stu-id="406f3-137">Because the type of the query variable is implicit, the iteration variable in the `foreach` loop must also be implicit.</span></span>  
  
## <a name="letting-the-compiler-infer-type-information"></a><span data-ttu-id="406f3-138">Ableiten von Typinformationen durch den Compiler</span><span class="sxs-lookup"><span data-stu-id="406f3-138">Letting the compiler infer type information</span></span>  

 <span data-ttu-id="406f3-139">Auch wenn Sie die Typbeziehungen einer Abfrageoperation grundsätzlich verstehen sollten, haben Sie die Option, den Compiler alle Arbeitsschritte ausführen zu lassen.</span><span class="sxs-lookup"><span data-stu-id="406f3-139">Although you should understand the type relationships in a query operation, you have the option to let the compiler do all the work for you.</span></span> <span data-ttu-id="406f3-140">Das [var](../../../language-reference/keywords/var.md)-Schlüsselwort kann in einer Abfrageoperation für jede lokale Variable verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="406f3-140">The keyword [var](../../../language-reference/keywords/var.md) can be used for any local variable in a query operation.</span></span> <span data-ttu-id="406f3-141">Die folgende Abbildung ähnelt Beispiel Nummer 2, das zuvor erläutert wurde.</span><span class="sxs-lookup"><span data-stu-id="406f3-141">The following illustration is similar to example number 2 that was discussed earlier.</span></span> <span data-ttu-id="406f3-142">Allerdings stellt der Compiler den starken Typ für jede Variable in der Abfrageoperation bereit.</span><span class="sxs-lookup"><span data-stu-id="406f3-142">However, the compiler supplies the strong type for each variable in the query operation.</span></span>  
  
 ![Diagramm, das den Typenfluss mit implizierter Typisierung zeigt.](./media/type-relationships-in-linq-query-operations/linq-type-flow-implicit-typing.png)  
  
 <span data-ttu-id="406f3-144">Weitere Informationen zu `var` finden Sie unter [Implizit typisierte lokale Variablen](../../classes-and-structs/implicitly-typed-local-variables.md).</span><span class="sxs-lookup"><span data-stu-id="406f3-144">For more information about `var`, see [Implicitly Typed Local Variables](../../classes-and-structs/implicitly-typed-local-variables.md).</span></span>  
