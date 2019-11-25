---
title: COR_PRF_SUSPEND_REASON 列挙型
ms.date: 03/30/2017
api_name:
- COR_PRF_SUSPEND_REASON
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_SUSPEND_REASON
helpviewer_keywords:
- COR_PRF_SUSPEND_REASON enumeration [.NET Framework profiling]
ms.assetid: 75594833-bed3-47b2-a426-b75c5fe6fbcf
topic_type:
- apiref
ms.openlocfilehash: d2d9ca77e764fe439753f1174a42af5ef80faa59
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/23/2019
ms.locfileid: "74447708"
---
# <a name="cor_prf_suspend_reason-enumeration"></a>COR_PRF_SUSPEND_REASON 列挙型
Indicates the reason that the runtime is suspended.  
  
## <a name="syntax"></a>構文  
  
```cpp  
typedef enum {  
    COR_PRF_SUSPEND_OTHER                   = 0x00,  
    COR_PRF_SUSPEND_FOR_GC                  = 0x01,  
    COR_PRF_SUSPEND_FOR_APPDOMAIN_SHUTDOWN  = 0x02,  
    COR_PRF_SUSPEND_FOR_CODE_PITCHING       = 0x03,  
    COR_PRF_SUSPEND_FOR_SHUTDOWN            = 0x04,  
    COR_PRF_SUSPEND_FOR_INPROC_DEBUGGER     = 0x06,  
    COR_PRF_SUSPEND_FOR_GC_PREP             = 0x07,    COR_PRF_SUSPEND_FOR_REJIT               = 8  
} COR_PRF_SUSPEND_REASON;  
```  
  
## <a name="members"></a>メンバー  
  
|メンバー|説明|  
|------------|-----------------|  
|`COR_PRF_FIELD_SUSPEND_OTHER`|The runtime is suspended for an unspecified reason.|  
|`COR_PRF_FIELD_SUSPEND_FOR_GC`|The runtime is suspended to service a garbage collection request.<br /><br /> The garbage collection-related callbacks occur between the [ICorProfilerCallback::RuntimeSuspendFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendfinished-method.md) and [ICorProfilerCallback::RuntimeResumeStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimeresumestarted-method.md) callbacks.|  
|`COR_PRF_FIELD_SUSPEND_FOR_APPDOMAIN_SHUTDOWN`|The runtime is suspended so that an `AppDomain` can be shut down.<br /><br /> While the runtime is suspended, the runtime will determine which threads are in the `AppDomain` that is being shut down and set them to abort when they resume. There are no `AppDomain`-specific callbacks during this suspension.|  
|`COR_PRF_FIELD_SUSPEND_FOR_CODE_PITCHING`|The runtime is suspended so that code pitching can occur.<br /><br /> Code pitching ensues only when the just-in-time (JIT) compiler is active with code pitching enabled. Code pitching callbacks occur between the `ICorProfilerCallback::RuntimeSuspendFinished` and `ICorProfilerCallback::RuntimeResumeStarted` callbacks. **Note:**  The CLR JIT does not pitch functions in the .NET Framework version 2.0, so this value is not used in 2.0.|  
|`COR_PRF_FIELD_SUSPEND_FOR_SHUTDOWN`|The runtime is suspended so that it can shut down. It must suspend all threads to complete the operation.|  
|`COR_PRF_FIELD_SUSPEND_FOR_INPROC_DEBUGGER`|The runtime is suspended for in-process debugging.|  
|`COR_PRF_FIELD_SUSPEND_FOR_GC_PREP`|The runtime is suspended to prepare for a garbage collection.|  
|`COR_PRF_SUSPEND_FOR_REJIT`|The runtime is suspended for JIT recompilation.|  
  
## <a name="remarks"></a>Remarks  
 All runtime threads that are in unmanaged code are permitted to continue running until they try to re-enter the runtime, at which point they will also be suspended until the runtime resumes. This also applies to new threads that enter the runtime. All threads within the runtime are either suspended immediately if they are in interruptible code, or asked to suspend when they do reach interruptible code.  
  
## <a name="requirements"></a>［要件］  
 **:** 「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー** : CorProf.idl、CorProf.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [列挙型のプロファイリング](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
