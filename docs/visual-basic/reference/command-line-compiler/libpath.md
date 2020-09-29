---
title: -libpath
ms.date: 03/10/2018
helpviewer_keywords:
- libpath compiler option [Visual Basic]
- /libpath compiler option [Visual Basic]
- -libpath compiler option [Visual Basic]
ms.assetid: 5f1c26c9-3455-4e89-bdf3-b12d6c2e655b
ms.openlocfilehash: a91bd74d0be4f1cb223091ee2527f9567b4ca5db
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/23/2020
ms.locfileid: "91058468"
---
# <a name="-libpath"></a>-libpath

Gibt den Speicherort der Verweisassemblys an.  
  
## <a name="syntax"></a>Syntax  
  
```console  
-libpath:dirList  
```  
  
## <a name="arguments"></a>Argumente  
  
|Begriff|Definition|  
|---|---|  
|`dirList`|Erforderlich. Eine durch Semikolons getrennte Liste von Verzeichnissen, in denen der Compiler suchen kann, wenn die Assembly, auf die verwiesen wird, im aktuellen Arbeitsverzeichnis (das Verzeichnis, in dem Sie den Compiler aufrufen) oder im CLR-Systemverzeichnis (Common Language Runtime) nicht gefunden werden kann. Wenn der Verzeichnisname ein Leerzeichen enthält, müssen Sie den Name in Anführungszeichen (" ") einschließen.|  
  
## <a name="remarks"></a>Hinweise  

 Die `-libpath`-Option gibt den Speicherort der Assemblys an, auf die durch die [-reference](reference.md)-Option verwiesen wird.  
  
 Der Compiler sucht in folgender Reihenfolge nach Assemblyverweisen, die nicht voll qualifiziert sind:  
  
1. Aktuelles Arbeitsverzeichnis Dies ist das Arbeitsverzeichnis, aus dem der Compiler abgerufen wird.  
  
2. Das Verzeichnis des CLR-Systems (Common Language Runtime)  
  
3. Von `-libpath` angegebene Verzeichnisse.  
  
4. Von den LIB-Umgebungsvariablen angegebene Verzeichnisse  
  
 Die `-libpath`-Option ist additiv. Wenn sie mehr als einmal angegeben wird, wird sie an jeden vorherigen Wert angehängt.  
  
 Verwenden Sie `-reference`, um einen Assemblyverweis anzugeben.  
  
|So legen Sie -libpath in der integrierten Visual Studio-Entwicklungsumgebung fest|  
|---|  
|1.  Ein Projekt auswählen in **Projektmappen-Explorer**. Klicken Sie im Menü **Projekt** auf **Eigenschaften**. <br />2.  Klicken Sie auf die Registerkarte **Verweise**.<br />3.  Klicken Sie auf die Schaltfläche **Verweispfade…** .<br />4.  Geben Sie im Dialogfeld **Verweispfade** den Verzeichnisname im Feld **Ordner:** ein.<br />5.  Klicken Sie auf **Ordner hinzufügen**.|  
  
## <a name="example"></a>Beispiel  

 Der folgende Code kompiliert `T2.vb`, um eine EXE-Datei zu erstellen. Der Compiler sucht im Arbeitsverzeichnis, im Stammverzeichnis des Laufwerks C: und im Verzeichnis „Neue Verzeichnisse“ des Laufwerks C: nach Assemblyverweisen.  
  
```console  
vbc -libpath:c:\;"c:\New Assemblies" -reference:t2.dll t2.vb  
```  
  
## <a name="see-also"></a>Siehe auch

- [Assemblys in .NET](../../../standard/assembly/index.md)
- [Visual Basic-Befehlszeilencompiler](index.md)
- [Beispiele für Kompilierungsbefehlszeilen](sample-compilation-command-lines.md)
