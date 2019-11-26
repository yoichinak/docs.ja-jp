---
title: ICorProfilerInfo4 インターフェイス
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo4
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo4
helpviewer_keywords:
- ICorProfilerInfo4 interface [.NET Framework profiling]
ms.assetid: 80a5308e-c22f-4201-ba89-31cc8562515b
topic_type:
- apiref
ms.openlocfilehash: cbd7c0d8fff55766a98e727ce22c77dd5214611b
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448008"
---
# <a name="icorprofilerinfo4-interface"></a>ICorProfilerInfo4 インターフェイス
Provides methods that code profilers use to communicate with the common language runtime (CLR) to control event monitoring and request information. である必要があります。 The `ICorProfilerInfo4` interface is an extension of the other `ICorProfilerInfo` interfaces. It provides new methods to support just-in-time (JIT) recompilation, added in the .NET Framework 4.5.  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[EnumJITedFunctions2 メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-enumjitedfunctions2-method.md)|Returns an enumerator for all functions that were previously JIT-compiled and JIT-recompiled.|  
|[EnumThreads メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-enumthreads-method.md)|Gets an enumerator that provides methods to sequentially iterate through the collection of all managed threads in the profiled process.|  
|[GetCodeInfo3 メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getcodeinfo3-method.md)|指定した関数の JIT 再コンパイル バージョンに関連付けられているネイティブ コードの範囲を取得します。|  
|[GetFunctionFromIP2 メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getfunctionfromip2-method.md)|Maps a managed code instruction pointer to the JIT-recompiled version of a specified function.|  
|[GetILToNativeMapping2 メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getiltonativemapping2-method.md)|Gets a map from Microsoft intermediate language (MSIL) offsets to native offsets for the code contained in the JIT-recompiled version of the specified function .|  
|[GetObjectSize2 メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getobjectsize2-method.md)|Returns the size of a specified object.|  
|[GetReJITIDs メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getrejitids-method.md)|Returns an array of IDs that identify all JIT-recompiled versions of the specified function that are still allocated.|  
|[InitializeCurrentThread メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-initializecurrentthread-method.md)|Initializes the current thread in advance of subsequent profiler API calls on the same thread, so that deadlock can be avoided.|  
|[RequestReJIT メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-requestrejit-method.md)|指定された関数のすべてのインスタンスの JIT 再コンパイルを要求します。|  
|[RequestRevert メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-requestrevert-method.md)|指定された関数のすべてのインスタンスを元のバージョンに戻します。|  
  
## <a name="remarks"></a>Remarks  
 CLR は、`ICorProfilerInfo4` インターフェイスのメソッドを、フリー スレッド モデルを使用して実装します。 各メソッドが、成功または失敗を示す HRESULT を返します。 返される可能性があるリターン コードの一覧については、CorError.h ファイルを参照してください。  
  
## <a name="requirements"></a>［要件］  
 **:** 「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー** : CorProf.idl、CorProf.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [プロファイリングのインターフェイス](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [ICorProfilerInfo インターフェイス](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
