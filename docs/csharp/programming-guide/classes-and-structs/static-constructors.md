---
title: Statische Konstruktoren – C#-Programmierhandbuch
description: Ein statischer Konstruktor in C# initialisiert statische Daten oder führt eine Aktion aus, die nur einmal ausgeführt wird, bevor die erste Instanz erstellt oder auf statische Member verwiesen wird.
ms.date: 07/20/2015
helpviewer_keywords:
- static constructors [C#]
- constructors [C#], static
ms.assetid: 151ec95e-3c4d-4ed7-885d-95b7a3be2e7d
ms.openlocfilehash: 07b3e54c9ffeb1abacaf5ddd04d2058697e653e4
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/24/2020
ms.locfileid: "91203968"
---
# <a name="static-constructors-c-programming-guide"></a><span data-ttu-id="5bbd1-103">Statische Konstruktoren (C#-Programmierhandbuch)</span><span class="sxs-lookup"><span data-stu-id="5bbd1-103">Static Constructors (C# Programming Guide)</span></span>

<span data-ttu-id="5bbd1-104">Ein statischer Konstruktor wird verwendet, um [static](../../language-reference/keywords/static.md)-Daten zu initialisieren oder um eine bestimmte Aktion auszuführen, die nur einmal ausgeführt werden muss.</span><span class="sxs-lookup"><span data-stu-id="5bbd1-104">A static constructor is used to initialize any [static](../../language-reference/keywords/static.md) data, or to perform a particular action that needs to be performed once only.</span></span> <span data-ttu-id="5bbd1-105">Er wird automatisch aufgerufen, bevor die erste Instanz erstellt oder auf irgendwelche statischen Member verwiesen wird.</span><span class="sxs-lookup"><span data-stu-id="5bbd1-105">It is called automatically before the first instance is created or any static members are referenced.</span></span>  
  
 [!code-csharp[csProgGuideObjects#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#14)]  

## <a name="remarks"></a><span data-ttu-id="5bbd1-106">Hinweise</span><span class="sxs-lookup"><span data-stu-id="5bbd1-106">Remarks</span></span>

<span data-ttu-id="5bbd1-107">Statische Konstruktoren verfügen über folgende Eigenschaften:</span><span class="sxs-lookup"><span data-stu-id="5bbd1-107">Static constructors have the following properties:</span></span>  
  
- <span data-ttu-id="5bbd1-108">Ein statischer Konstruktor kann nicht über Zugriffsmodifizierer oder Parameter verfügen.</span><span class="sxs-lookup"><span data-stu-id="5bbd1-108">A static constructor does not take access modifiers or have parameters.</span></span>  

- <span data-ttu-id="5bbd1-109">Eine Klasse oder Struktur kann nur einen statischen Konstruktor besitzen.</span><span class="sxs-lookup"><span data-stu-id="5bbd1-109">A class or struct can only have one static constructor.</span></span>

- <span data-ttu-id="5bbd1-110">Statische Konstruktoren können nicht vererbt oder überladen werden.</span><span class="sxs-lookup"><span data-stu-id="5bbd1-110">Static constructors cannot be inherited or overloaded.</span></span>

- <span data-ttu-id="5bbd1-111">Ein statischer Konstruktor kann nicht direkt aufgerufen werden und ist nur für den Aufruf durch die Common Language Runtime (CLR) gedacht.</span><span class="sxs-lookup"><span data-stu-id="5bbd1-111">A static constructor cannot be called directly and is only meant to be called by the common language runtime (CLR).</span></span> <span data-ttu-id="5bbd1-112">Er wird automatisch aufgerufen.</span><span class="sxs-lookup"><span data-stu-id="5bbd1-112">It is invoked automatically.</span></span>

- <span data-ttu-id="5bbd1-113">Der Benutzer hat keine Kontrolle, wenn der statische Konstruktor im Programm ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="5bbd1-113">The user has no control on when the static constructor is executed in the program.</span></span>
  
- <span data-ttu-id="5bbd1-114">Ein statischer Konstruktor wird automatisch zum Initialisieren von [class](../../language-reference/keywords/class.md) aufgerufen, bevor die erste Instanz erzeugt wird oder auf irgendwelche statischen Member verwiesen wird.</span><span class="sxs-lookup"><span data-stu-id="5bbd1-114">A static constructor is called automatically to initialize the [class](../../language-reference/keywords/class.md) before the first instance is created or any static members are referenced.</span></span> <span data-ttu-id="5bbd1-115">Ein statischer Konstruktor wird vor einem Instanzkonstruktor ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="5bbd1-115">A static constructor will run before an instance constructor.</span></span> <span data-ttu-id="5bbd1-116">Der statische Konstruktor eines Typs wird aufgerufen, wenn eine statische Methode, die einem Ereignis oder Delegaten zugewiesen ist, aufgerufen wird. Dies erfolgt nicht während der Zuweisung.</span><span class="sxs-lookup"><span data-stu-id="5bbd1-116">A type's static constructor is called when a static method assigned to an event or a delegate is invoked and not when it is assigned.</span></span> <span data-ttu-id="5bbd1-117">Wenn Variableninitialisierer für statische Felder in der Klasse des statischen Konstruktors vorhanden sind, werden sie direkt vor Ausführung des statischen Konstruktors in der Textreihenfolge ausgeführt, in der sie in der Klassendeklaration vorhanden sind.</span><span class="sxs-lookup"><span data-stu-id="5bbd1-117">If static field variable initializers are present in the class of the static constructor, they will be executed in the textual order in which they appear in the class declaration immediately prior to the execution of the static constructor.</span></span>

- <span data-ttu-id="5bbd1-118">Wenn Sie keinen statischen Konstruktor zum Initialisieren von statischen Feldern angeben, werden alle statischen Felder mit ihrem Standardwert initialisiert, wie unter [Standardwerte für C#-Typen](../../language-reference/builtin-types/default-values.md) aufgeführt.</span><span class="sxs-lookup"><span data-stu-id="5bbd1-118">If you don't provide a static constructor to initialize static fields, all static fields are initialized to their default value as listed in [Default values of C# types](../../language-reference/builtin-types/default-values.md).</span></span>
  
- <span data-ttu-id="5bbd1-119">Wenn ein statischer Konstruktor eine Ausnahme auslöst, wird die Laufzeit ihn kein zweites Mal aufrufen, und der Typ bleibt für die Lebensdauer der Anwendungsdomäne, in der das Programm ausgeführt wird, nicht initialisiert.</span><span class="sxs-lookup"><span data-stu-id="5bbd1-119">If a static constructor throws an exception, the runtime will not invoke it a second time, and the type will remain uninitialized for the lifetime of the application domain in which your program is running.</span></span> <span data-ttu-id="5bbd1-120">Eine <xref:System.TypeInitializationException>-Ausnahme wird in aller Regel ausgelöst, wenn ein statischer Konstruktor keinen Typ instanziieren kann oder wenn in einem statischen Konstruktor ein Ausnahmefehler auftritt.</span><span class="sxs-lookup"><span data-stu-id="5bbd1-120">Most commonly, a <xref:System.TypeInitializationException> exception is thrown when a static constructor is unable to instantiate a type or for an unhandled exception occurring within a static constructor.</span></span> <span data-ttu-id="5bbd1-121">Bei impliziten statischen Konstruktoren, die im Quellcode nicht explizit definiert sind, ist zur Problembehandlung möglicherweise eine Prüfung des IL-Codes (Intermediate Language, Zwischensprache) erforderlich.</span><span class="sxs-lookup"><span data-stu-id="5bbd1-121">For implicit static constructors that are not explicitly defined in source code, troubleshooting may require inspection of the intermediate language (IL) code.</span></span>

- <span data-ttu-id="5bbd1-122">Die Existenz eines statischen Konstruktors verhindert die Hinzufügung des <xref:System.Reflection.TypeAttributes.BeforeFieldInit>-Typattributs.</span><span class="sxs-lookup"><span data-stu-id="5bbd1-122">The presence of a static constructor prevents the addition of the <xref:System.Reflection.TypeAttributes.BeforeFieldInit> type attribute.</span></span> <span data-ttu-id="5bbd1-123">Dadurch wird die Laufzeitoptimierung eingeschränkt.</span><span class="sxs-lookup"><span data-stu-id="5bbd1-123">This limits runtime optimization.</span></span>

- <span data-ttu-id="5bbd1-124">Ein als `static readonly` deklariertes Feld darf nur als Teil der Deklaration oder in einem statischen Konstruktor zugewiesen werden.</span><span class="sxs-lookup"><span data-stu-id="5bbd1-124">A field declared as `static readonly` may only be assigned as part of its declaration or in a static constructor.</span></span> <span data-ttu-id="5bbd1-125">Wenn ein expliziter statischer Konstruktor nicht erforderlich ist, initialisieren Sie statische Felder in der Deklaration anstatt über einen statischen Konstruktor, um die Laufzeitoptimierung zu verbessern.</span><span class="sxs-lookup"><span data-stu-id="5bbd1-125">When an explicit static constructor is not required, initialize static fields at declaration, rather than through a static constructor for better runtime optimization.</span></span>

> [!Note]
> <span data-ttu-id="5bbd1-126">Auch wenn auf einen expliziten statischen Konstruktor nicht direkt zugegriffen werden kann, sollte seine Existenz dennoch dokumentiert werden, um bei der Fehlerbehebung von Initialisierungsausnahmen zu helfen.</span><span class="sxs-lookup"><span data-stu-id="5bbd1-126">Though not directly accessible, the presence of an explicit static constructor should be documented to assist with troubleshooting initialization exceptions.</span></span>

### <a name="usage"></a><span data-ttu-id="5bbd1-127">Verwendung</span><span class="sxs-lookup"><span data-stu-id="5bbd1-127">Usage</span></span>

- <span data-ttu-id="5bbd1-128">Eine typische Verwendung statischer Konstruktoren besteht darin, wenn die Klasse eine Protokolldatei verwendet und der Konstruktor verwendet wird, um Einträge in dieser Datei zu schreiben.</span><span class="sxs-lookup"><span data-stu-id="5bbd1-128">A typical use of static constructors is when the class is using a log file and the constructor is used to write entries to this file.</span></span>  
- <span data-ttu-id="5bbd1-129">Statische Konstruktoren sind auch beim Erstellen von Wrapperklassen für nicht verwalteten Code nützlich, wenn der Konstruktor die `LoadLibrary`-Methode aufrufen kann.</span><span class="sxs-lookup"><span data-stu-id="5bbd1-129">Static constructors are also useful when creating wrapper classes for unmanaged code, when the constructor can call the `LoadLibrary` method.</span></span>  

- <span data-ttu-id="5bbd1-130">Statische Konstruktoren sind auch eine praktische Möglichkeit, Laufzeitüberprüfungen des Typparameters über Einschränkungen (Typparametereinschränkungen) zu erzwingen, der zur Kompilierzeit nicht überprüft werden kann.</span><span class="sxs-lookup"><span data-stu-id="5bbd1-130">Static constructors are also a convenient place to enforce run-time checks on the type parameter that cannot be checked at compile time via constraints (Type parameter constraints).</span></span>

## <a name="example"></a><span data-ttu-id="5bbd1-131">Beispiel</span><span class="sxs-lookup"><span data-stu-id="5bbd1-131">Example</span></span>

 <span data-ttu-id="5bbd1-132">In diesem Beispiel verfügt die Klasse `Bus` über einen statischen Konstruktor.</span><span class="sxs-lookup"><span data-stu-id="5bbd1-132">In this example, class `Bus` has a static constructor.</span></span> <span data-ttu-id="5bbd1-133">Wenn die erste Instanz von `Bus` erstellt wird (`bus1`), wird der statische Konstruktor zur Initialisierung der Klasse aufgerufen.</span><span class="sxs-lookup"><span data-stu-id="5bbd1-133">When the first instance of `Bus` is created (`bus1`), the static constructor is invoked to initialize the class.</span></span> <span data-ttu-id="5bbd1-134">Die Beispielausgabe überprüft, ob der statische Konstruktor nur einmal ausgeführt wird, obwohl zwei Instanzen von `Bus` erstellt werden, und dass er vor dem Ausführen des Instanzkonstruktors ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="5bbd1-134">The sample output verifies that the static constructor runs only one time, even though two instances of `Bus` are created, and that it runs before the instance constructor runs.</span></span>  
  
 [!code-csharp[csProgGuideObjects#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#15)]

## <a name="c-language-specification"></a><span data-ttu-id="5bbd1-135">C#-Sprachspezifikation</span><span class="sxs-lookup"><span data-stu-id="5bbd1-135">C# language specification</span></span>

<span data-ttu-id="5bbd1-136">Weitere Informationen finden Sie im Abschnitt [Statische Konstruktoren](~/_csharplang/spec/classes.md#static-constructors) der [C#-Sprachspezifikation](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="5bbd1-136">For more information, see the [Static constructors](~/_csharplang/spec/classes.md#static-constructors) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="5bbd1-137">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="5bbd1-137">See also</span></span>

- [<span data-ttu-id="5bbd1-138">C#-Programmierhandbuch</span><span class="sxs-lookup"><span data-stu-id="5bbd1-138">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="5bbd1-139">Klassen und Strukturen</span><span class="sxs-lookup"><span data-stu-id="5bbd1-139">Classes and Structs</span></span>](./index.md)
- [<span data-ttu-id="5bbd1-140">Konstruktoren</span><span class="sxs-lookup"><span data-stu-id="5bbd1-140">Constructors</span></span>](./constructors.md)
- [<span data-ttu-id="5bbd1-141">Statische Klassen und statische Klassenmember</span><span class="sxs-lookup"><span data-stu-id="5bbd1-141">Static Classes and Static Class Members</span></span>](./static-classes-and-static-class-members.md)
- [<span data-ttu-id="5bbd1-142">Finalizer</span><span class="sxs-lookup"><span data-stu-id="5bbd1-142">Finalizers</span></span>](./destructors.md)
- [<span data-ttu-id="5bbd1-143">Entwurfsrichtlinien für Konstruktoren</span><span class="sxs-lookup"><span data-stu-id="5bbd1-143">Constructor Design Guidelines</span></span>](../../../standard/design-guidelines/constructor.md#type-constructor-guidelines)
- [<span data-ttu-id="5bbd1-144">Sicherheitswarnung – CA2121: Statische Konstruktoren sollten privat sein.</span><span class="sxs-lookup"><span data-stu-id="5bbd1-144">Security Warning - CA2121: Static constructors should be private</span></span>](/visualstudio/code-quality/ca2121-static-constructors-should-be-private)
