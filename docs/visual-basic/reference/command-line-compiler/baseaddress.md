---
title: -baseaddress
ms.date: 08/09/2018
f1_keywords:
- /baseaddress
- baseaddress
helpviewer_keywords:
- -baseaddress compiler option [Visual Basic]
- /baseaddress compiler option [Visual Basic]
- baseaddress compiler option [Visual Basic]
ms.assetid: c982bcf2-46e5-47a2-bc8f-a5cc32b7dc47
ms.openlocfilehash: c794d1fc1c9d20e22ffa747e3175c846341ad8ad
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/23/2020
ms.locfileid: "91097760"
---
# <a name="-baseaddress"></a>-baseaddress

Gibt beim Erstellen einer DLL-Datei eine Standardbasisadresse an  
  
## <a name="syntax"></a>Syntax  
  
```console  
-baseaddress:address  
```  
  
## <a name="arguments"></a>Argumente  
  
|Begriff|Definition|  
|---|---|  
|`address`|Erforderlich. Die Basisadresse für die DLL. Diese Adresse muss als Hexadezimalzahl angegeben werden.|  
  
## <a name="remarks"></a>Hinweise  

 Die Standardbasisadresse für eine DLL-Datei wird durch das .NET Framework festgelegt.  
  
 Denken Sie daran, dass das niederwertige Wort in dieser Adresse gerundet wird. Wenn Sie zum Beispiel 0x11110001 angeben, wird dieser Wert auf 0x11110000 gerundet.  
  
 Verwenden Sie die `–R`-Option des Strong Name-Tool (Sn.exe), um den Signaturvorgang für die DLL-Datei abzuschließen.  
  
 Diese Option wird ignoriert, wenn das Ziel keine DLL-Datei ist.  
  
|So legen Sie -baseaddress in der Visual Studio-IDE fest|  
|---|  
|1.  Ein Projekt auswählen in **Projektmappen-Explorer**. Klicken Sie im Menü **Projekt** auf **Eigenschaften**. <br />2.  Klicken Sie auf die Registerkarte **Kompilieren**.<br />3.  Klicken Sie auf **Erweitert**.<br />4.  Ändern Sie den Wert im Feld **DLL-Basisadresse:** . **Hinweis**:      Das Feld **DLL-Basisadresse:** ist schreibgeschützt, wenn das Ziel keine DLL-Datei ist.|  
  
## <a name="see-also"></a>Siehe auch

- [Visual Basic-Befehlszeilencompiler](index.md)
- [-target (Visual Basic)](target.md)
- [Beispiele für Kompilierungsbefehlszeilen](sample-compilation-command-lines.md)
- [Sn.exe (Strong Name-Tool)](../../../framework/tools/sn-exe-strong-name-tool.md))
