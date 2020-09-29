---
description: '@ (C#-Compileroptionen)'
title: '@ (C#-Compileroptionen)'
ms.date: 07/20/2015
f1_keywords:
- '@'
helpviewer_keywords:
- response files, specifying for compilation [C#]
- '@ compiler option'
ms.assetid: dda4fa9f-a02c-400f-8b6a-d58834e13d7f
ms.openlocfilehash: 8f7e222e194fc4ba96159ecd792765f64b4d1c57
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/24/2020
ms.locfileid: "91193751"
---
# <a name="-c-compiler-options"></a>@ (C#-Compileroptionen)

Mit der @-Option können Sie eine Datei angeben, die Compileroptionen und zu kompilierende Quellcodedateien enthält.  
  
## <a name="syntax"></a>Syntax  
  
```console  
@response_file  
```  
  
## <a name="arguments"></a>Argumente  

 `response_file`  
 Eine Datei, die Compileroptionen oder zu kompilierende Quellcodedateien auflistet.  
  
## <a name="remarks"></a>Bemerkungen  

 Die Compileroptionen und Quellcodedateien werden vom Compiler so verarbeitet, als ob sie in der Befehlszeile angegeben wären.  
  
 Wenn Sie mehr als eine Antwortdatei in einer Kompilierung angeben möchten, geben Sie mehrere Antwortdateioptionen an. Beispiel:  
  
```console  
@file1.rsp @file2.rsp  
```  
  
 In einer Antwortdatei können mehrere Compileroptionen und Quellcodedateien in einer Zeile angezeigt werden. Eine einzelne Compileroption muss in einer Zeile angegeben werden (und darf nicht mehrere Zeilen umfassen). Antwortdateien können Kommentare aufweisen, die mit einem #-Symbol beginnen.  
  
 Die Angabe von Compileroptionen innerhalb einer Antwortdatei entspricht dem Ausgeben von Befehlen in der Befehlszeile. Weitere Informationen finden Sie unter [Erstellen von der Befehlszeile aus](./how-to-set-environment-variables-for-the-visual-studio-command-line.md).  
  
 Der Compiler verarbeitet die Befehlsoptionen in der Reihenfolge, in der sie auftreten. Daher können Befehlszeilenargumente zuvor aufgeführte Optionen in Antwortdateien überschreiben. Im Gegensatz dazu überschreiben Optionen in einer Antwortdatei zuvor in der Befehlszeile oder in anderen Antwortdateien aufgeführte Optionen.  
  
 C# stellt die Datei „csc.rsp“ bereit, die sich im selben Verzeichnis wie die Datei „csc.exe“ befindet. Weitere Informationen zu „csc.rsp“ finden Sie unter [-noconfig](./noconfig-compiler-option.md).  
  
 Diese Compileroption kann weder in der Visual Studio-Entwicklungsumgebung festgelegt werden, noch kann sie programmgesteuert geändert werden.  
  
## <a name="example"></a>Beispiel  

 Nachfolgend sind einige Zeilen aus einer Beispielantwortdatei aufgeführt:  
  
```console  
# build the first output file  
-target:exe -out:MyExe.exe source1.cs source2.cs  
```  
  
## <a name="see-also"></a>Weitere Informationen

- [C#-Compileroptionen](./index.md)
