---
title: ICorProfilerCallback::ObjectReferences メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ObjectReferences
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ObjectReferences
helpviewer_keywords:
- ObjectReferences method [.NET Framework profiling]
- ICorProfilerCallback::ObjectReferences method [.NET Framework profiling]
ms.assetid: dd5e9b64-b4a3-4ba6-9be6-ddb540f4ffcf
topic_type:
- apiref
ms.openlocfilehash: 4f8cfd912a3d6f66f5f2586a8942c7ce9bd52a63
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/23/2019
ms.locfileid: "74445891"
---
# <a name="icorprofilercallbackobjectreferences-method"></a>ICorProfilerCallback::ObjectReferences メソッド
Notifies the profiler about objects in memory that are being referenced by the specified object.  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT ObjectReferences(  
    [in]  ObjectID objectId,  
    [in]  ClassID  classId,  
    [in]  ULONG    cObjectRefs,  
    [in, size_is(cObjectRefs)] ObjectID objectRefIds[] );  
```  
  
## <a name="parameters"></a>パラメーター  
 `objectId`  
 [in] The ID of the object that is referencing objects.  
  
 `classId`  
 [in] The ID of the class that the specified object is an instance of.  
  
 `cObjectRefs`  
 [in] The number of objects referenced by the specified object (that is, the number of elements in the `objectRefIds` array).  
  
 `objectRefIds`  
 [in] An array of IDs of objects that are being referenced by `objectId`.  
  
## <a name="remarks"></a>Remarks  
 The `ObjectReferences` method is called for each object remaining in the heap after a garbage collection has completed. If the profiler returns an error from this callback, the profiling services will discontinue invoking this callback until the next garbage collection.  
  
 The `ObjectReferences` callback can be used in conjunction with the [ICorProfilerCallback::RootReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-rootreferences-method.md) callback to create a complete object reference graph for the runtime. The common language runtime (CLR) ensures that each object reference is reported only once by the `ObjectReferences` method.  
  
 The object IDs returned by `ObjectReferences` are not valid during the callback itself, because the garbage collection might be in the middle of moving objects. Therefore, profilers must not attempt to inspect objects during an `ObjectReferences` call. When [ICorProfilerCallback2::GarbageCollectionFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md) is called, the garbage collection is complete and inspection can be safely done.  
  
 A null `ClassId` indicates that `objectId` has a type that is unloading.  
  
## <a name="requirements"></a>［要件］  
 **:** 「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー** : CorProf.idl、CorProf.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICorProfilerCallback インターフェイス](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
