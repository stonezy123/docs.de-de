---
title: IValidator::Validate-Methode
ms.date: 03/30/2017
api_name:
- IValidator.Validate
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- Validate
helpviewer_keywords:
- IValidator::Validate method [.NET Framework hosting]
- Validate method, IValidator interface [.NET Framework hosting]
ms.assetid: 7d68666a-fb73-4455-bebd-908d49a16abc
topic_type:
- apiref
ms.openlocfilehash: 688abd210cca193bf03c40f000b74ecb66eb8ede
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008546"
---
# <a name="ivalidatorvalidate-method"></a>IValidator::Validate-Methode
Überprüft die angegebene PE-Datei (portable ausführbare Datei) oder die MSIL-Datei (Microsoft Intermediate Language).  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT Validate (  
    [in] IVEHandler            *veh,  
    [in] IUnknown              *pAppDomain,  
    [in] unsigned long          ulFlags,  
    [in] unsigned long          ulMaxError,  
    [in] unsigned long          token,  
    [in] LPWSTR                 fileName,  
    [in, size_is(ulSize)] BYTE *pe,  
    [in] unsigned long          ulSize  
);  
```  
  
## <a name="parameters"></a>Parameter  
 `veh`  
 in Ein Zeiger auf eine- `IVEHandler` Instanz, die Validierungs Fehler behandelt.  
  
 `pAppDomain`  
 in Ein Zeiger auf die Anwendungsdomäne, in der die Datei geladen wird.  
  
 `ulFlags`  
 in Eine bitweise Kombination von [ValidatorFlags](validatorflags-enumeration.md) -Werten, die die auszuführenden Validierungen angeben.  
  
 `ulMaxError`  
 in Die maximal zulässige Anzahl von Fehlern, bevor die Überprüfung beendet wird.  
  
 `token`  
 [in] Wird nicht verwendet.  
  
 `fileName`  
 in Eine Zeichenfolge, die den Namen der zu validierenden Datei angibt.  
  
 `pe`  
 in Ein Zeiger auf den Speicherpuffer, in dem die Datei gespeichert ist.  
  
 `ulSize`  
 in Die Größe (in Bytes) der zu validierenden Datei.  
  
## <a name="requirements"></a>Requirements (Anforderungen)  
 **Plattformen:** Informationen finden Sie unter [Systemanforderungen](../../get-started/system-requirements.md).  
  
 **Header:** IValidator. idl, IValidator. h  
  
 **Bibliothek:** Als Ressource in Mscoree. dll enthalten  
  
 **.NET Framework Versionen:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
