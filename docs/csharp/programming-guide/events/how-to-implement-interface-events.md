---
title: 'Vorgehensweise: Implementieren von Schnittstellenereignissen (C#-Programmierleitfaden)'
description: Erfahren Sie, wie Sie Schnittstellenereignisse in einer Klasse implementieren. Hier finden Sie Codebeispiele und zusätzliche verfügbare Ressourcen.
ms.date: 07/20/2015
helpviewer_keywords:
- interfaces [C#], event implementation in classes
- events [C#], in interfaces
ms.assetid: 63527447-9535-4880-8e95-35e2075827df
ms.openlocfilehash: 153a2efa254bf2f2c81cec4b28a53207cdc4efe5
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/24/2020
ms.locfileid: "91167547"
---
# <a name="how-to-implement-interface-events-c-programming-guide"></a>Vorgehensweise: Implementieren von Schnittstellenereignissen (C#-Programmierleitfaden)

Eine [Schnittstelle](../../language-reference/keywords/interface.md) kann ein [Ereignis](../../language-reference/keywords/event.md) deklarieren. Das folgende Beispiel zeigt, wie Schnittstellenereignisse in einer Klasse implementiert werden. Die Regeln sind mit den Regeln zum Implementieren von Schnittstellenmethoden oder -eigenschaften weitestgehend identisch.  
  
## <a name="to-implement-interface-events-in-a-class"></a>So implementieren Sie Schnittstellenereignisse in einer Klasse  
  
Deklarieren Sie das Ereignis in der Klasse, und rufen Sie es dann an den entsprechenden Stellen auf.  
  
```csharp
namespace ImplementInterfaceEvents  
{  
    public interface IDrawingObject  
    {  
        event EventHandler ShapeChanged;  
    }  
    public class MyEventArgs : EventArgs
    {  
        // class members  
    }  
    public class Shape : IDrawingObject  
    {  
        public event EventHandler ShapeChanged;  
        void ChangeShape()  
        {  
            // Do something here before the event…  

            OnShapeChanged(new MyEventArgs(/*arguments*/));  

            // or do something here after the event.
        }  
        protected virtual void OnShapeChanged(MyEventArgs e)  
        {  
            ShapeChanged?.Invoke(this, e);  
        }  
    }  

}  
```  
  
## <a name="example"></a>Beispiel  

Das folgende Beispiel zeigt die ungewöhnlichere Vorgehensweise, wenn die Klasse von zwei oder mehr Schnittstellen erbt und jede Schnittstelle über ein Ereignis mit dem gleichen Namen verfügt. In dieser Situation müssen Sie eine explizite Schnittstellenimplementierung für mindestens eines der Ereignisse bereitstellen. Wenn Sie eine explizite Schnittstellenimplementierung für ein Ereignis schreiben, müssen Sie auch den `add`-Ereignisaccessor und den `remove`-Ereignisaccessor schreiben. Normalerweise werden diese vom Compiler bereitgestellt, was in diesem Fall jedoch nicht möglich ist.  
  
Durch das Bereitstellen Ihrer eigenen Accessoren können Sie festlegen, ob die beiden Ereignisse durch das gleiche Ereignis oder durch verschiedene Ereignisse in der Klasse dargestellt werden sollen. Wenn z. B. die Ereignisse gemäß den Schnittstellenspezifikationen zu unterschiedlichen Zeiten ausgelöst werden sollen, können Sie jedes Ereignis einer separaten Implementierung in der Klasse zuordnen. Im folgenden Beispiel bestimmen Abonnenten, welches `OnDraw`-Ereignis sie erhalten, indem sie den Formverweis entweder in eine `IShape` oder ein `IDrawingObject` umwandeln.  
  
 [!code-csharp[csProgGuideEvents#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEvents/CS/Events.cs#10)]
  
## <a name="see-also"></a>Weitere Informationen

- [C#-Programmierhandbuch](../index.md)
- [Ereignisse](./index.md)
- [Delegaten](../delegates/index.md)
- [Explizite Schnittstellenimplementierung](../interfaces/explicit-interface-implementation.md)
- [Auslösen von Basisklassenereignissen in abgeleiteten Klassen](./how-to-raise-base-class-events-in-derived-classes.md)
