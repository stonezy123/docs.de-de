---
description: -bugreport (C#-Compileroptionen)
title: -bugreport (C#-Compileroptionen)
ms.date: 07/20/2015
f1_keywords:
- /bugreport
helpviewer_keywords:
- /bugreport compiler option [C#]
- -bugreport compiler option [C#]
- bugreport compiler option [C#]
ms.assetid: f39665e3-4f6f-4357-88a2-3274c7bec0c1
ms.openlocfilehash: 2afab44eec0c7bcc9809b458be0348093cb6dd07
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/24/2020
ms.locfileid: "91196818"
---
# <a name="-bugreport-c-compiler-options"></a>-bugreport (C#-Compileroptionen)

Gibt an, dass Debuginformationen zum Zweck einer späteren Analyse in eine Datei eingefügt werden sollen.  
  
## <a name="syntax"></a>Syntax  
  
```console  
-bugreport:file  
```  
  
## <a name="arguments"></a>Argumente  

 `file`  
 Der Name der Datei, die den Problembericht enthalten soll.  
  
## <a name="remarks"></a>Bemerkungen  

 Die Option **-bugreport** gibt an, dass die folgende Informationen in `file` eingefügt werden soll:  
  
- Eine Kopie aller Quellcodedateien in der Kompilierung.  
  
- Eine Liste der bei der Kompilierung verwendeten Compileroptionen.  
  
- Versionsinformationen über den Compiler, die Laufzeit und das Betriebssystem.  
  
- Assemblys und Module, auf die verwiesen wird und die als Hexadezimalzahlen gespeichert sind, außer im Lieferumfang von .NET Framework und dem SDK enthaltene Assemblys.  
  
- Compilerausgabe, falls vorhanden.  
  
- Eine Beschreibung des Problems. Sie werden aufgefordert, diese Beschreibung einzugeben.  
  
- Eine Beschreibung Ihres Vorschlags zur Beseitigung des Problems. Sie werden aufgefordert, diese Beschreibung einzugeben.  
  
 Wenn diese Option mit **-errorreport:prompt** oder **-errorreport:send** verwendet wird, werden die Informationen in der Datei an die Microsoft Corporation gesendet.  
  
 Da von allen Quellcodedateien Kopien in `file` gespeichert werden, empfiehlt es sich, den vermuteten Codefehler im kürzestmöglichen Programm zu reproduzieren.  
  
 Diese Compileroption steht in Visual Studio nicht zur Verfügung und kann auch nicht programmgesteuert angepasst werden.  
  
 Beachten Sie, dass im Inhalt der generierten Datei Quellcode offen gelegt wird, was zu einer unbeabsichtigten Veröffentlichung von Informationen führen konnte.  
  
## <a name="see-also"></a>Weitere Informationen

- [C#-Compileroptionen](./index.md)
- [-errorreport (C#-Compileroptionen)](./errorreport-compiler-option.md)
- [Verwalten von Projekt- und Projektmappeneigenschaften](/visualstudio/ide/managing-project-and-solution-properties)
