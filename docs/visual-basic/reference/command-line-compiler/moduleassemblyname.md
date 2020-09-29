---
title: -moduleassemblyname
ms.date: 03/13/2018
helpviewer_keywords:
- moduleassemblyname compiler option [Visual Basic]
- /moduleassemblyname compiler option [Visual Basic]
- -moduleassemblyname compiler option [Visual Basic]
ms.assetid: 013a57b6-f425-4dd3-b333-512d72c42f55
ms.openlocfilehash: 9fb9287f9472d4b33eff4cb601aff5eed370b2c0
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/23/2020
ms.locfileid: "91065566"
---
# <a name="-moduleassemblyname"></a>-moduleassemblyname

Gibt den Namen der Assembly an, zu der dieses Modul gehört.  
  
## <a name="syntax"></a>Syntax  
  
```console  
-moduleassemblyname:assembly_name  
```  
  
## <a name="arguments"></a>Argumente  
  
|Begriff|Definition|  
|---|---|  
|`assembly_name`|Der Name der Assembly, zu der dieses Modul gehört|  
  
## <a name="remarks"></a>Hinweise  

 Der Compiler verarbeitet die `-moduleassemblyname`-Option nur, wenn die `-target:module`-Option angegeben wurde. Dies führt dazu, dass der Compiler ein Modul erstellt. Das vom Compiler erstellte Modul ist nur für die mit der `-moduleassemblyname`-Option angegebene Assembly gültig. Wenn Sie das Modul in eine andere Assembly verschieben, treten Laufzeitfehler auf.  
  
 Die `-moduleassemblyname`-Option ist nur erforderlich, wenn Folgendes gilt:  
  
- Ein Datentyp im Modul benötigt Zugriff auf einen `Friend`-Typ in einer Referenzassembly.  
  
- Die Referenzassembly hat der Assembly, in die das Modul integriert wird, Friend-Assembly-Zugriff erteilt.  
  
 Weitere Informationen zur Erstellung eines Moduls finden Sie unter [-target (Visual Basic)](target.md). Weitere Informationen zu Friend-Assemblys finden Sie unter [Friend-Assemblys](../../../standard/assembly/friend.md).  
  
> [!NOTE]
> Die Option `-moduleassemblyname` steht nicht in der Visual Studio-Entwicklungsumgebung zur Verfügung. Sie ist nur verfügbar, wenn Sie über eine Eingabeaufforderung kompilieren.  
  
## <a name="see-also"></a>Siehe auch

- [How to: Erstellen einer Mehrfachdateiassembly](../../../framework/app-domains/build-multifile-assembly.md)
- [Visual Basic-Befehlszeilencompiler](index.md)
- [-target (Visual Basic)](target.md)
- [-main](main.md)
- [-reference (Visual Basic)](reference.md)
- [-addmodule](addmodule.md)
- [Assemblys in .NET](../../../standard/assembly/index.md)
- [Beispiele für Kompilierungsbefehlszeilen](sample-compilation-command-lines.md)
- [Friend-Assemblys](../../../standard/assembly/friend.md)
