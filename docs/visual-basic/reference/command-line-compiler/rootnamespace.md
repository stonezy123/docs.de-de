---
title: -rootnamespace
ms.date: 03/13/2018
f1_keywords:
- /rootnamespace
- rootnamespace
helpviewer_keywords:
- /rootnamespace compiler option [Visual Basic]
- -rootnamespace compiler option [Visual Basic]
- rootnamespace compiler option [Visual Basic]
ms.assetid: e9245edf-6bef-420d-a7c7-324117752783
ms.openlocfilehash: d9388ace03f654458eb955e989673b7441e72f23
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/23/2020
ms.locfileid: "91085138"
---
# <a name="-rootnamespace"></a>-rootnamespace

Gibt einen Namespace für alle Typdeklarationen an.  
  
## <a name="syntax"></a>Syntax  
  
```console  
-rootnamespace:namespace  
```  
  
## <a name="arguments"></a>Argumente  
  
|Begriff|Definition|  
|---|---|  
|`namespace`|Der Name des Namespace, in dem alle Typdeklarationen für das aktuelle Projekt eingeschlossen werden sollen|  
  
## <a name="remarks"></a>Hinweise  

 Wenn Sie die ausführbare Visual Studio-Datei (Devenv.exe) verwenden, um ein Projekt zu kompilieren, das in der integrierten Entwicklungsumgebung in Visual Studio erstellt wurde, verwenden Sie `-rootnamespace`, um den Wert der <xref:VSLangProj80.VBProjectProperties3.RootNamespace%2A>-Eigenschaft anzugeben. Weitere Informationen finden Sie unter [Devenv-Befehlszeilenparameter](/visualstudio/ide/reference/devenv-command-line-switches).  
  
 Verwenden Sie den MSIL-Disassembler der Common Language Runtime (`Ildasm.exe`), um die Namespacenamen in Ihrer Ausgabedatei anzuzeigen.  
  
|So legen Sie -rootnamespace in der integrierten Visual Studio-Entwicklungsumgebung fest|  
|---|  
|1.  Ein Projekt auswählen in **Projektmappen-Explorer**. Klicken Sie im Menü **Projekt** auf **Eigenschaften**. <br />2.  Klicken Sie auf die Registerkarte **Anwendung** .<br />3.  Ändern Sie den Wert im Feld **Stammnamespace** entsprechend.|  
  
## <a name="example"></a>Beispiel  

 Der folgende Code kompiliert `In.vb` und schließt alle Typdeklarationen im Namespace `mynamespace` ein.  
  
```console
vbc -rootnamespace:mynamespace in.vb  
```  
  
## <a name="see-also"></a>Siehe auch

- [Visual Basic-Befehlszeilencompiler](index.md)
- [Ildasm.exe (IL-Disassembler)](../../../framework/tools/ildasm-exe-il-disassembler.md)
- [Beispiele für Kompilierungsbefehlszeilen](sample-compilation-command-lines.md)
