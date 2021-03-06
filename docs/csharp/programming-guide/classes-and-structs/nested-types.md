---
title: Geschachtelte Typen – C#-Programmierhandbuch
description: Ein innerhalb einer Klasse, Struktur oder Schnittstelle definierter Typ wird in C# als geschachtelter Typ bezeichnet.
ms.date: 02/08/2020
helpviewer_keywords:
- nested types [C#]
ms.assetid: f2e1b315-e3d1-48ce-977f-7bae0960ba99
ms.openlocfilehash: 9e1c6c1e8b22b5447d43915ab02984aa13146301
ms.sourcegitcommit: 3d84eac0818099c9949035feb96bbe0346358504
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/21/2020
ms.locfileid: "86864942"
---
# <a name="nested-types-c-programming-guide"></a>Geschachtelte Typen (C#-Programmierhandbuch)

Ein innerhalb einer [Klasse](../../language-reference/keywords/class.md), [Struktur](../../language-reference/builtin-types/struct.md) oder [Schnittstelle](../../language-reference/keywords/interface.md) definierter Typ wird als geschachtelter Typ bezeichnet. Beispiel:

[!code-csharp[DeclareNestedClass](~/samples/snippets/csharp/objectoriented/nestedtypes.cs#DeclareNestedClass)]

Unabhängig davon, ob es sich beim äußeren Typ um eine Klasse, Schnittstelle oder Struktur handelt, sind geschachtelte Typen standardmäßig [privat](../../language-reference/keywords/private.md), d. h. sie sind nur über den enthaltenden Typ zugänglich. Im vorherigen Beispiel konnten externe Typen nicht auf die `Nested`-Klasse zugreifen.

Sie können auch einen [Zugriffsmodifizierer](../../language-reference/keywords/access-modifiers.md) angeben, um den Zugriff auf einen geschachtelten Typ wie folgt zu definieren:

- Geschachtelte Typen von **class** können [public](../../language-reference/keywords/public.md), [protected](../../language-reference/keywords/protected.md), [internal](../../language-reference/keywords/internal.md), [protected internal](../../language-reference/keywords/protected-internal.md), [private](../../language-reference/keywords/private.md) oder [private protected](../../language-reference/keywords/private-protected.md) sein.

   Durch das Definieren einer geschachtelten `protected`-, `protected internal`- oder `private protected`-Klasse innerhalb einer [versiegelten Klasse](../../language-reference/keywords/sealed.md) wird jedoch die Compilerwarnung [CS0628](../../misc/cs0628.md), „Neuer geschützter Member in versiegelter Klasse deklariert“, generiert.
  
- Geschachtelte Typen einer **Struktur** können öffentlich ([public](../../language-reference/keywords/public.md)), intern ([internal](../../language-reference/keywords/internal.md)) oder privat ([private](../../language-reference/keywords/private.md)) sein.

Im folgenden Beispiel wird die `Nested`-Klasse öffentlich gemacht:

[!code-csharp[PublicNestedClass](~/samples/snippets/csharp/objectoriented/nestedtypes.cs#PublicNestedClass)]

Der geschachtelte oder innere Typ kann auf den enthaltenden oder äußeren Typ zugreifen. Um auf den enthaltenden Typ zuzugreifen, übergeben Sie ihn als Argument dem Konstruktor des geschachtelten Typs. Zum Beispiel:

[!code-csharp[DeclareNestedInstance](~/samples/snippets/csharp/objectoriented/nestedtypes.cs#DeclareNestedInstance)]

Ein geschachtelter Typ hat Zugriff auf alle Member, die für ihren äußeren (enthaltenden) Typ zugreifbar sind. Er kann auf die Member des äußeren (enthaltenden) Typs zugreifen, die "private" oder "protected" sind, ebenso auf alle geerbten Member, die "private" oder "protected" sind.

In der vorherigen Deklaration ist `Nested` der vollständige Name der Klasse `Container.Nested`. Mit diesem Namen wird wie folgt eine neue Instanz der geschachtelten Klasse erstellt:

[!code-csharp[UseNestedInstance](~/samples/snippets/csharp/objectoriented/nestedtypes.cs#UseNestedInstance)]

## <a name="see-also"></a>Siehe auch

- [C#-Programmierhandbuch](../index.md)
- [Klassen und Strukturen](./index.md)
- [Zugriffsmodifizierer](./access-modifiers.md)
- [Konstruktoren](./constructors.md)
