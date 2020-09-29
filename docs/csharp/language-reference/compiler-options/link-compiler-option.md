---
description: -link (C#-Compileroptionen)
title: -link (C#-Compileroptionen)
ms.date: 07/20/2015
helpviewer_keywords:
- /l compiler option [C#]
- /link compiler option [C#]
- -l compiler option [C#]
- EmbedInteropTypes
- l compiler option [C#]
- embed interop types [COM Interop]
- -link compiler option [C#]
- link compiler option [C#]
ms.assetid: 00da70c6-9ea1-43c2-86f2-aa7f26c03475
ms.openlocfilehash: f6e654f4a24829de579ac94ef75b1c645fcb1685
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/24/2020
ms.locfileid: "91165831"
---
# <a name="-link-c-compiler-options"></a>-link (C#-Compileroptionen)

Bewirkt, dass der Compiler dem Projekt, das Sie aktuell kompilieren, COM-Typinformationen in den angegebenen Assemblys bereitstellt.

## <a name="syntax"></a>Syntax

```console
-link:fileList
// -or-
-l:fileList
```

## <a name="arguments"></a>Argumente

 `fileList`  
 Erforderlich. Durch Trennzeichen getrennte Liste von Assemblydateinamen. Wenn der Dateiname ein Leerzeichen enthält, müssen Sie den Namen in Anführungszeichen einschließen.

## <a name="remarks"></a>Hinweise

 Die Option `-link` ermöglicht es Ihnen, eine Anwendung mit eingebetteten Typinformationen bereitzustellen. Die Anwendung kann dann Typen in einer Runtime-Assembly verwenden, die die eingebetteten Typinformationen implementieren, ohne dass ein Verweis auf die Runtime-Assembly erforderlich ist. Wenn verschiedene Versionen der Runtime-Assembly veröffentlicht werden, kann die Anwendung, die die eingebetteten Typinformationen enthält, mit den verschiedenen Versionen arbeiten, ohne neu kompiliert werden zu müssen. Ein Beispiel finden Sie unter [Exemplarische Vorgehensweise: Einbetten von Typen aus verwalteten Assemblys](../../../standard/assembly/embed-types-visual-studio.md).

 Die Option `-link` ist besonders nützlich, wenn Sie COM-Interop verwenden. Sie können COM-Typen einbetten, sodass für Ihre Anwendung keine primäre Interopassembly (PIA) auf dem Zielcomputer mehr erforderlich ist. Die Option `-link` weist den Compiler an, die COM-Typinformationen aus der Interopassembly, auf die verwiesen wird, in den resultierenden kompilierten Code einzubetten. Der COM-Typ wird durch den CLSID (GUID)-Wert identifiziert. Dadurch kann Ihre Anwendung auf einem Zielcomputer ausgeführt werden, auf dem die gleichen COM-Typen mit den gleichen CLSID-Werten installiert sind. Anwendungen, die Microsoft Office automatisieren, sind ein gutes Beispiel. Da Anwendungen wie Office in der Regel den gleichen CLSID-Wert in den verschiedenen Versionen behalten, kann die Anwendung die COM-Typen, auf die verwiesen wird, verwenden, wenn .NET Framework 4 oder höher auf dem Zielcomputer installiert ist und die Anwendung Methoden, Eigenschaften oder Ereignisse verwendet, die in den COM-Typen, auf die verwiesen wird, enthalten sind.

 Die Option `-link` bettet nur Schnittstellen, Strukturen und Delegaten ein. Das Einbetten von COM-Klassen wird nicht unterstützt.

> [!NOTE]
> Wenn Sie eine Instanz eines eingebetteten COM-Typs in Ihrem Code erstellen, müssen Sie die Instanz mithilfe der entsprechenden Schnittstelle erstellen. Der Versuch, eine Instanz eines eingebetteten COM-Typs mit der Co-Klasse zu erstellen, verursacht einen Fehler.

 Fügen Sie zum Festlegen der Option `-link` in Visual Studio einen Assemblyverweis hinzu, und legen Sie die `Embed Interop Types`-Eigenschaft auf **TRUE** fest. Der Standardwert der `Embed Interop Types`-Eigenschaft ist **false**.

 Wenn Sie eine Verknüpfung mit einer COM-Assembly (Assembly A) erstellen, die selbst auf eine andere COM-Assembly (Assembly B) verweist, müssen Sie auch eine Verknüpfung mit Assembly B erstellen, wenn eine der folgenden Aussagen zutrifft:

- Ein Typ von Assembly A erbt von einem Typ oder implementiert eine Schnittstelle aus Assembly B.

- Es wird ein Feld, eine Eigenschaft, ein Ereignis oder eine Methode aufgerufen, das/die über einen Rückgabetyp oder Parametertyp von Assembly B verfügt.

 Wie die Compileroption [-reference](./reference-compiler-option.md) verwendet auch die Compileroption `-link` die Antwortdatei „Csc.rsp“, die auf häufig verwendete .NET-Assemblys verweist. Verwenden Sie die Compileroption [-noconfig](./noconfig-compiler-option.md), wenn Sie nicht möchten, dass der Compiler die Datei „Csc.rsp“ verwendet.

 Die Kurzform von `-link` ist `-l`.

## <a name="generics-and-embedded-types"></a>Generics und eingebettete Typen

 In den folgenden Abschnitten werden die Einschränkungen bei der Verwendung von generischen Typen in Anwendungen, die Interop-Typen einbetten, beschrieben.

### <a name="generic-interfaces"></a>Generische Schnittstellen

 Generische Schnittstellen, die von einer Interopassembly eingebettet werden, können nicht verwendet werden. Dies wird im folgenden Beispiel gezeigt.

 [!code-csharp[VbLinkCompilerCS#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/vblinkcompilercs/cs/program.cs#1)]

### <a name="types-that-have-generic-parameters"></a>Typen, die generische Parameter aufweisen

 Typen, die über einen generischen Parameter verfügen, dessen Typ aus einer Interop-Assembly eingebettet wird, können nicht verwendet werden, wenn dieser Typ aus einer externen Assembly stammt. Diese Einschränkung gilt nicht für Schnittstellen. Nehmen Sie z.B. die <xref:Microsoft.Office.Interop.Excel.Range> Schnittstellen, die in der <xref:Microsoft.Office.Interop.Excel>-Assembly definiert wird. Wenn eine Bibliothek Interop-Typen aus der <xref:Microsoft.Office.Interop.Excel>-Assembly einbettet und eine Methode verfügbar macht, die einen generischen Typ zurückgibt, der einen Parameter mit dem Typ <xref:Microsoft.Office.Interop.Excel.Range>-Schnittstelle hat, muss diese Methode eine generische Schnittstelle zurückgeben, wie im folgenden Codebeispiel gezeigt.

[!code-csharp[VbLinkCompilerCS#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/vblinkcompilercs/cs/utility.cs)]

 Im folgenden Beispiel kann der Clientcode die Methode aufrufen, die die generische Schnittstelle <xref:System.Collections.IList> ohne Fehler zurückgibt.

 [!code-csharp[VbLinkCompilerCS#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/vblinkcompilercs/cs/program.cs#5)]

## <a name="example"></a>Beispiel

 Der folgende Code kompiliert die Quelldatei `OfficeApp.cs` und Verweisassemblys aus `COMData1.dll` und `COMData2.dll`, um `OfficeApp.exe` zu produzieren.

```csharp
csc -link:COMData1.dll,COMData2.dll -out:OfficeApp.exe OfficeApp.cs
```

## <a name="see-also"></a>Weitere Informationen

- [C#-Compileroptionen](./index.md)
- [Exemplarische Vorgehensweise: Einbetten von Typen aus verwalteten Assemblys in Visual Studio](../../../standard/assembly/embed-types-visual-studio.md)
- [-reference (C#-Compileroptionen)](./reference-compiler-option.md)
- [-noconfig (C#-Compileroptionen)](./noconfig-compiler-option.md)
- [Erstellen über die Befehlszeile mit csc.exe](./command-line-building-with-csc-exe.md)
- [Überblick über die Interoperabilität](../../programming-guide/interop/interoperability-overview.md)
