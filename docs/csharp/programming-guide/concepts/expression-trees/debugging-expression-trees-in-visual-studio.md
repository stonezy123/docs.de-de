---
title: Debuggen von Ausdrucksbäumen in Visual Studio (C#)
description: Hier erhalten Sie Informationen zur DebugView-Eigenschaft in Visual Studio. Sie erfahren, wie Sie diese Eigenschaft verwenden, um die Struktur und den Inhalt einer Ausdrucksbaumstruktur zu analysieren.
ms.date: 07/20/2015
ms.assetid: 1369fa25-0fbd-4b92-98d0-8df79c49c27a
ms.openlocfilehash: 5dcf56f96ecdbfdc3f4cb171fdb30b96456b59c9
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/24/2020
ms.locfileid: "91154131"
---
# <a name="debugging-expression-trees-in-visual-studio-c"></a><span data-ttu-id="3ff13-104">Debuggen von Ausdrucksbäumen in Visual Studio (C#)</span><span class="sxs-lookup"><span data-stu-id="3ff13-104">Debugging Expression Trees in Visual Studio (C#)</span></span>

<span data-ttu-id="3ff13-105">Sie können die Struktur und den Inhalt von Ausdrucksbaumstrukturen beim Debuggen Ihrer Anwendung analysieren.</span><span class="sxs-lookup"><span data-stu-id="3ff13-105">You can analyze the structure and content of expression trees when you debug your applications.</span></span> <span data-ttu-id="3ff13-106">Um eine Übersicht über die Ausdrucksbaumstruktur zu erhalten, können Sie die `DebugView`-Eigenschaft verwenden, die Ausdrucksbaumstrukturen mit einer [speziellen Syntax](debugview-syntax.md) darstellt.</span><span class="sxs-lookup"><span data-stu-id="3ff13-106">To get a quick overview of the expression tree structure, you can use the `DebugView` property, which represents expression trees [using a special syntax](debugview-syntax.md).</span></span> <span data-ttu-id="3ff13-107">(Beachten Sie, dass `DebugView` nur im Debugmodus verfügbar ist.)</span><span class="sxs-lookup"><span data-stu-id="3ff13-107">(Note that `DebugView` is available only in debug mode.)</span></span>  

![Screenshot der DebugView einer Ausdrucksbaumstruktur im VS-Debugger.](media/debugging-expression-trees-in-visual-studio/debugview-expression-tree.png)

<span data-ttu-id="3ff13-109">Da `DebugView` eine Zeichenfolge ist, können Sie die [integrierte Text-Schnellansicht](/visualstudio/debugger/view-strings-visualizer#open-a-string-visualizer) verwenden, um eine Ansicht mit mehreren Zeilen zu erhalten. Wählen Sie hierzu über das Lupensymbol neben `DebugView` die Option **Text-Schnellansicht**.</span><span class="sxs-lookup"><span data-stu-id="3ff13-109">Since `DebugView` is a string, you can use the [built-in Text Visualizer](/visualstudio/debugger/view-strings-visualizer#open-a-string-visualizer) to view it across multiple lines, by selecting **Text Visualizer** from the magnifying glass icon next to the `DebugView` label.</span></span>

 ![Screenshot der Text-Schnellansicht für Ergebnisse von DebugView.](media/debugging-expression-trees-in-visual-studio/string-visualizer-debugview.png)

<span data-ttu-id="3ff13-111">Alternativ dazu können Sie eine [benutzerdefinierte Schnellansicht](/visualstudio/debugger/create-custom-visualizers-of-data) für Ausdrucksbaumstrukturen installieren und verwenden, wie z.B.:</span><span class="sxs-lookup"><span data-stu-id="3ff13-111">Alternatively, you can install and use [a custom visualizer](/visualstudio/debugger/create-custom-visualizers-of-data) for expression trees, such as:</span></span>

- <span data-ttu-id="3ff13-112">Mit [lesbaren Ausdrücken](https://github.com/agileobjects/ReadableExpressions) ([MIT-Lizenz](https://github.com/agileobjects/ReadableExpressions/blob/master/LICENSE.md), die über den [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=vs-publisher-1232914.ReadableExpressionsVisualizers) verfügbar ist) wird die Ausdrucksbaumstruktur als C#-Code, der ein Design zugewiesen werden kann, und mit verschiedenen Renderingoptionen gerendert:</span><span class="sxs-lookup"><span data-stu-id="3ff13-112">[Readable Expressions](https://github.com/agileobjects/ReadableExpressions) ([MIT license](https://github.com/agileobjects/ReadableExpressions/blob/master/LICENSE.md), available at the [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=vs-publisher-1232914.ReadableExpressionsVisualizers)), renders the expression tree as themeable C# code, with various rendering options:</span></span>

  ![Screenshot der Schnellansicht für lesbare Ausdrücke.](media/debugging-expression-trees-in-visual-studio/readable-expressions-visualizer.png)

- <span data-ttu-id="3ff13-114">Bei der [Schnellansicht für lesbare Ausdrücke](https://github.com/zspitz/ExpressionTreeVisualizer/blob/master/README.md) ([MIT-Lizenz](https://github.com/zspitz/ExpressionTreeVisualizer/blob/master/LICENSE)) wird eine Strukturansicht der Ausdrucksbaumstruktur und der zugehörigen einzelnen Knoten bereitgestellt:</span><span class="sxs-lookup"><span data-stu-id="3ff13-114">[Expression Tree Visualizer](https://github.com/zspitz/ExpressionTreeVisualizer/blob/master/README.md) ([MIT license](https://github.com/zspitz/ExpressionTreeVisualizer/blob/master/LICENSE)) provides a tree view of the expression tree and its individual nodes:</span></span>

  ![Screenshot der Schnellansicht der Ausdrucksbaumstruktur.](media/debugging-expression-trees-in-visual-studio/expression-tree-visualizer.png)

### <a name="to-open-a-visualizer-for-an-expression-tree"></a><span data-ttu-id="3ff13-116">So öffnen Sie eine Schnellansicht für eine Ausdrucksbaumstruktur</span><span class="sxs-lookup"><span data-stu-id="3ff13-116">To open a visualizer for an expression tree</span></span>  
  
1. <span data-ttu-id="3ff13-117">Klicken Sie auf das Lupensymbol, das in **DataTips** neben einer Ausdrucksbaumstruktur, in einem **Überwachungsfenster**, einem **Auto**- oder einem **Lokalfenster** angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="3ff13-117">Click the magnifying glass icon that appears next to the expression tree in **DataTips**, a **Watch** window, the **Autos** window, or the **Locals** window.</span></span>  

    <span data-ttu-id="3ff13-118">Eine Liste mit den verfügbaren Schnellansichten wird angezeigt:</span><span class="sxs-lookup"><span data-stu-id="3ff13-118">A list of available visualizers is displayed.:</span></span>

    ![Screenshot, der das Öffnen von Schnellansichten aus Visual Studio zeigt.](media/debugging-expression-trees-in-visual-studio/expression-tree-visualizers.png)

2. <span data-ttu-id="3ff13-120">Klicken Sie auf die gewünschte Schnellansicht.</span><span class="sxs-lookup"><span data-stu-id="3ff13-120">Click the visualizer you want to use.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3ff13-121">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="3ff13-121">See also</span></span>

- [<span data-ttu-id="3ff13-122">Ausdrucksbaumstrukturen (C#)</span><span class="sxs-lookup"><span data-stu-id="3ff13-122">Expression Trees (C#)</span></span>](./index.md)
- [<span data-ttu-id="3ff13-123">Debuggen in Visual Studio</span><span class="sxs-lookup"><span data-stu-id="3ff13-123">Debugging in Visual Studio</span></span>](/visualstudio/debugger/debugger-feature-tour)
- [<span data-ttu-id="3ff13-124">Erstellen benutzerdefinierter Schnellansichten</span><span class="sxs-lookup"><span data-stu-id="3ff13-124">Create Custom Visualizers</span></span>](/visualstudio/debugger/create-custom-visualizers-of-data)
- [<span data-ttu-id="3ff13-125">`DebugView`-Syntax</span><span class="sxs-lookup"><span data-stu-id="3ff13-125">`DebugView` syntax</span></span>](debugview-syntax.md)
