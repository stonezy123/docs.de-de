---
title: -define
ms.date: 03/10/2018
helpviewer_keywords:
- -d compiler option [Visual Basic]
- /d compiler option [Visual Basic]
- -define compiler option [Visual Basic]
- d compiler option [Visual Basic]
- /define compiler option [Visual Basic]
- define compiler option [Visual Basic]
ms.assetid: f735c57d-1cf9-4f2f-a26f-0de630fd4077
ms.openlocfilehash: cb56e727479fd249cb0d7e5e7c3c50d5b68b3a72
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/23/2020
ms.locfileid: "91072014"
---
# <a name="-define-visual-basic"></a>-define (Visual Basic)

Definiert Konstanten für die bedingte Kompilierung.  
  
## <a name="syntax"></a>Syntax  
  
```console  
-define:["]symbol[=value][,symbol[=value]]["]  
```

oder

```console  
-d:["]symbol[=value][,symbol[=value]]["]  
```  
  
## <a name="arguments"></a>Argumente  
  
|Begriff|Definition|  
|---|---|  
|`symbol`|Erforderlich. Das zu definierende Symbol.|  
|`value`|Dies ist optional. Der Wert, der `symbol` zugewiesen werden soll. Wenn `value` eine Zeichenfolge ist, muss sie von einer Kombination aus umgekehrtem Schrägstrich/Anführungszeichen (\\") statt Anführungszeichen umgeben sein. Wurde kein Wert festgelegt, dann wird er als True angenommen.|  
  
## <a name="remarks"></a>Hinweise  

 Die Option `-define` hat einen ähnlichen Effekt wie das Verwenden einer `#Const`-Präprozessoranweisung in der Quelldatei, außer dass mit `-define` definierte Konstanten öffentlich sind und für alle Dateien im Projekt gelten.  
  
 Sie können Symbole, die mit dieser Option erstellt wurden, mit der `#If`...`Then`...`#Else`-Anweisung verwenden, um Quelldateien bedingt zu kompilieren.  
  
 `-d` ist die Kurzform von `-define`.  
  
 Sie können mehrere Symbole mit `-define` definieren, wenn Sie kommagetrennte Symboldefinitionen verwenden.  
  
|So legen Sie -define in der integrierten Visual Studio-Entwicklungsumgebung fest|  
|---|  
|1.  Ein Projekt auswählen in **Projektmappen-Explorer**. Klicken Sie im Menü **Projekt** auf **Eigenschaften**. <br />2.  Klicken Sie auf die Registerkarte **Kompilieren**.<br />3.  Klicken Sie auf **Erweitert**.<br />4.  Ändern Sie den Wert im Feld **Benutzerdefinierte Konstanten**.|  
  
## <a name="example"></a>Beispiel  

 Der folgende Code definiert zwei konditionelle Compilerkonstanten und verwendet sie anschließend.  
  
 [!code-vb[VbVbalrCompiler#45](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/Class1.vb#45)]  
  
## <a name="see-also"></a>Siehe auch

- [Visual Basic-Befehlszeilencompiler](index.md)
- [#If...Then...#Else-Anweisungen](../../language-reference/directives/if-then-else-directives.md)
- [#Const-Anweisung](../../language-reference/directives/const-directive.md)
- [Beispiele für Kompilierungsbefehlszeilen](sample-compilation-command-lines.md)
