---
title: ICorProfilerCallback::COMClassicVTableDestroyed メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.COMClassicVTableDestroyed
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::COMClassicVTableDestroyed
helpviewer_keywords:
- ICorProfilerCallback::COMClassicVTableDestroyed method [.NET Framework profiling]
- COMClassicVTableDestroyed method [.NET Framework profiling]
ms.assetid: 29da20ca-bf39-4356-8099-d9c3ac3423a9
topic_type:
- apiref
ms.openlocfilehash: 0b0683d43778c4733b476e9feef459207b9d1ee6
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/23/2019
ms.locfileid: "74445032"
---
# <a name="icorprofilercallbackcomclassicvtabledestroyed-method"></a>ICorProfilerCallback::COMClassicVTableDestroyed メソッド
Notifies the profiler that a COM interop vtable is being destroyed.  
  
> [!NOTE]
> This callback is likely never to occur, because the destruction of vtables occurs very close to shutdown.  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT COMClassicVTableDestroyed(  
    [in] ClassID wrappedClassId,  
    [in] REFGUID implementedIID,  
    [in] void    *pVTable);  
```  
  
## <a name="parameters"></a>パラメーター  
 `wrappedClassId`  
 [in] The ID of the class for which this vtable was created.  
  
 `implementedIID`  
 [in] The ID of the interface implemented by the class. This value may be NULL if the interface is internal only.  
  
 `pVTable`  
 [in] A pointer to the start of the vtable.  
  
## <a name="remarks"></a>Remarks  
 The profiler should not block in its implementation of this method because the stack may not be in a state that allows garbage collection, and therefore preemptive garbage collection cannot be enabled. If the profiler blocks here and garbage collection is attempted, the runtime will block until this callback returns.  
  
 The profiler's implementation of this method should not call into managed code or in any way cause a managed-memory allocation.  
  
## <a name="requirements"></a>［要件］  
 **:** 「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー** : CorProf.idl、CorProf.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICorProfilerCallback インターフェイス](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [COMClassicVTableCreated メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-comclassicvtablecreated-method.md)
