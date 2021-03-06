---
title: ICorDebugProcess2-Schnittstelle
ms.date: 03/30/2017
api_name:
- ICorDebugProcess2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess2
helpviewer_keywords:
- ICorDebugProcess2 interface [.NET Framework debugging]
ms.assetid: 73332138-5fea-441f-b893-61af87d45a42
topic_type:
- apiref
ms.openlocfilehash: 1a57b7ceb6da961fba1f0d6e8e0ba1aa88ca0541
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213490"
---
# <a name="icordebugprocess2-interface"></a>ICorDebugProcess2-Schnittstelle
Eine logische Erweiterung der ICorDebugProcess-Schnittstelle, die einen Prozess darstellt, der verwalteten Code ausführt.  
  
## <a name="methods"></a>Methoden  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[ClearUnmanagedBreakpoint-Methode](icordebugprocess2-clearunmanagedbreakpoint-method.md)|Entfernt einen Haltepunkt am angegebenen Offset, der durch einen früheren-Aufrufsatz festgelegt wurde `ICorDebugProcess2::SetUnmanagedBreakpoint` .|  
|[GetDesiredNGENCompilerFlags-Methode](icordebugprocess2-getdesiredngencompilerflags-method.md)|Ruft die Flags ab, die für die Common Language Runtime (CLR) festgelegt werden müssen, um das Bild in den Prozess zu laden, auf den von verwiesen wird `ICorDebugProcess2` .|  
|[GetReferenceValueFromGCHandle-Methode](icordebugprocess2-getreferencevaluefromgchandle-method.md)|Ruft einen Verweis Zeiger auf das angegebene verwaltete Objekt ab, das über ein Garbage Collection Handle verfügt.|  
|[GetThreadForTaskID-Methode](icordebugprocess2-getthreadfortaskid-method.md)|Ruft den Thread ab, in dem die Aufgabe mit dem angegebenen Bezeichner ausgeführt wird.|  
|[GetVersion-Methode](icordebugprocess2-getversion-method.md)|Ruft die Version der CLR ab, auf der der Prozess ausgeführt wird, der debuggt wird.|  
|[SetDesiredNGENCompilerFlags-Methode](icordebugprocess2-setdesiredngencompilerflags-method.md)|Legt die Flags fest, die für den Just-in-time (JIT)-Compiler erforderlich sind, um ein Bild in den Prozess zu laden, der gedebuggt wird.|  
|[SetUnmanagedBreakpoint-Methode](icordebugprocess2-setunmanagedbreakpoint-method.md)|Legt einen nicht verwalteten Haltepunkt am angegebenen systemeigenen Abbild Offset fest.|  
  
## <a name="remarks"></a>Hinweise  
  
> [!NOTE]
> Diese Schnittstelle kann weder computerübergreifend noch prozessübergreifend remote aufgerufen werden.  
  
## <a name="requirements"></a>Requirements (Anforderungen)  
 **Plattformen:** Informationen finden Sie unter [Systemanforderungen](../../get-started/system-requirements.md).  
  
 **Header:** CorDebug.idl, CorDebug.h  
  
 **Bibliothek:** CorGuids.lib  
  
 **.NET Framework Versionen:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Siehe auch

- [Debugschnittstellen](debugging-interfaces.md)
