---
description: '#endif – C#-Referenz'
title: '#endif – C#-Referenz'
ms.date: 07/20/2015
f1_keywords:
- '#endif'
helpviewer_keywords:
- '#endif directive [C#]'
ms.assetid: 6a5fca55-5aee-441f-86f6-1c99fbe9ec05
ms.openlocfilehash: 0ccc00ceab2aa67c77140e3ef09907ba260d7e9b
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/24/2020
ms.locfileid: "91168633"
---
# <a name="endif-c-reference"></a>#endif (C#-Referenz)

`#endif` gibt das Ende einer bedingten Anweisung an, die mit der [#if](./preprocessor-if.md)-Anweisung angefangen hat. Beispiel:  
  
```csharp
#define DEBUG  
// ...  
#if DEBUG  
    Console.WriteLine("Debug version");  
#endif  
```  
  
## <a name="remarks"></a>Bemerkungen  

 Eine bedingte Anweisung, die mit einer `#if`-Anweisung beginnt, muss explizit mit einer `#endif`-Anweisung beendet werden. Unter [#if](./preprocessor-if.md) finden Sie ein Beispiel zur Verwendung von `#endif`.  
  
## <a name="see-also"></a>Siehe auch

- [C#-Referenz](../index.md)
- [C#-Programmierhandbuch](../../programming-guide/index.md)
- [C#-Präprozessoranweisungen](./index.md)
