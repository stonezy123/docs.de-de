---
ms.openlocfilehash: de35df21d1887bc95a3106edba312c53daad8b68
ms.sourcegitcommit: 4d45bda8cd9558ea8af4be591e3d5a29360c1ece
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2020
ms.locfileid: "91654736"
---
### <a name="netcoreapp3_1-preprocessor-symbol-is-not-defined-when-targeting-net-5"></a>Das NETCOREAPP3_1-Präprozessorsymbol ist nicht definiert, wenn .NET 5 als Zielversion verwendet wird

In .NET 5.0 RC2 und höher definieren Projekte keine Präprozessorsymbole mehr für frühere Versionen, sondern nur für die Zielversion. Dieses Verhalten entspricht dem von .NET Core 1.0 bis .NET Core 3.1.

#### <a name="version-introduced"></a>Eingeführt in Version

5.0 RC2

#### <a name="change-description"></a>Änderungsbeschreibung

In .NET 5.0 Preview 7 bis .NET 5.0 RC1 definieren Projekte für `net5.0` die Präprozessorsymbole `NETCOREAPP3_1` und `NET5_0`. Durch diesen Behavior Change sind [Symbole für die bedingte Kompilierung ab .NET 5.0 kumulativ](https://github.com/dotnet/designs/blob/main/accepted/2020/net5/net5.md#preprocessor-symbols).

Ab .NET 5.0 RC2 definieren Projekte nur Symbole für die Zielframeworkmoniker, nicht jedoch für frühere Versionen.

#### <a name="reason-for-change"></a>Grund für die Änderung

Die Änderung aus Preview 7 wurde aufgrund von Kundenfeedback zurückgenommen. Kunden waren überrascht und verwirrt, dass sie Symbole für frühere Versionen definieren mussten, und einige hielten dies für einen Fehler im C#-Compiler.

#### <a name="recommended-action"></a>Empfohlene Maßnahme

Stellen Sie sicher, dass Ihre `#if`-Logik nicht von einer vorhandenen `NETCOREAPP3_1`-Definition ausgeht, wenn das Projekt auf `net5.0` oder höher ausgerichtet ist. Es sollte stattdessen davon ausgegangen werden, dass `NETCOREAPP3_1` nur definiert ist, wenn das Projekt explizit auf `netcoreapp3.1` ausgerichtet ist.

Wenn Ihr Projekt beispielsweise .NET Core 2.1 und .NET Core 3.1 als Zielversionen verwendet und Sie APIs aufrufen, die in .NET Core 3.1 eingeführt wurden, sollte Ihre `#if`-Logik folgendermaßen aussehen:

```csharp
#if NETCOREAPP2_1 || NETCOREAPP3_0
    // Fallback behavior for old versions.
#elif NETCOREAPP
    // Behavior for .NET Core 3.1 and later.
#endif
```

#### <a name="category"></a>Kategorie

MSBuild

#### <a name="affected-apis"></a>Betroffene APIs

Nicht zutreffend

<!--

#### Affected APIs

Not detectable via API analysis.

-->
