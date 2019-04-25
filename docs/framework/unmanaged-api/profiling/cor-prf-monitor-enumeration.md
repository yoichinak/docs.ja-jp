---
title: COR_PRF_MONITOR 列挙型
ms.date: 03/30/2017
api_name:
- COR_PRF_MONITOR
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_MONITOR
helpviewer_keywords:
- COR_PRF_MONITOR enumeration [.NET Framework profiling]
ms.assetid: 9294d702-b4e5-441c-a930-e63d27b86bfd
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: dbb39eb768069a737f3f89c771bf02fd6bc0c3b4
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59102402"
---
# <a name="corprfmonitor-enumeration"></a>COR_PRF_MONITOR 列挙型
プロファイラーがサブスクライブしようとする動作、機能、またはイベントの指定で使用する値を含めます。  
  
## <a name="syntax"></a>構文  
  
```  
typedef enum {  
    COR_PRF_MONITOR_NONE                = 0x00000000,  
    COR_PRF_MONITOR_FUNCTION_UNLOADS    = 0x00000001,  
    COR_PRF_MONITOR_CLASS_LOADS         = 0x00000002,  
    COR_PRF_MONITOR_MODULE_LOADS        = 0x00000004,  
    COR_PRF_MONITOR_ASSEMBLY_LOADS      = 0x00000008,  
    COR_PRF_MONITOR_APPDOMAIN_LOADS     = 0x00000010,  
    COR_PRF_MONITOR_JIT_COMPILATION     = 0x00000020,  
    COR_PRF_MONITOR_EXCEPTIONS          = 0x00000040,  
    COR_PRF_MONITOR_GC                  = 0x00000080,  
    COR_PRF_MONITOR_OBJECT_ALLOCATED    = 0x00000100,  
    COR_PRF_MONITOR_THREADS             = 0x00000200,  
    COR_PRF_MONITOR_REMOTING            = 0x00000400,  
    COR_PRF_MONITOR_CODE_TRANSITIONS    = 0x00000800,  
    COR_PRF_MONITOR_ENTERLEAVE          = 0x00001000,  
    COR_PRF_MONITOR_CCW                 = 0x00002000,  
    COR_PRF_MONITOR_REMOTING_COOKIE     = 0x00004000 |   
                                          COR_PRF_MONITOR_REMOTING,  
    COR_PRF_MONITOR_REMOTING_ASYNC      = 0x00008000 |   
                                          COR_PRF_MONITOR_REMOTING,  
    COR_PRF_MONITOR_SUSPENDS            = 0x00010000,  
    COR_PRF_MONITOR_CACHE_SEARCHES      = 0x00020000,  
    COR_PRF_ENABLE_REJIT                = 0x00040000,  
    COR_PRF_ENABLE_INPROC_DEBUGGING     = 0x00080000,  
    COR_PRF_ENABLE_JIT_MAPS             = 0x00100000,  
    COR_PRF_DISABLE_INLINING            = 0x00200000,  
    COR_PRF_DISABLE_OPTIMIZATIONS       = 0x00400000,  
    COR_PRF_ENABLE_OBJECT_ALLOCATED     = 0x00800000,  
    COR_PRF_MONITOR_CLR_EXCEPTIONS      = 0x01000000,  
    COR_PRF_MONITOR_ALL                 = 0x0107FFFF,  
    COR_PRF_ENABLE_FUNCTION_ARGS        = 0X02000000,  
    COR_PRF_ENABLE_FUNCTION_RETVAL      = 0X04000000,  
    COR_PRF_ENABLE_FRAME_INFO           = 0X08000000,  
    COR_PRF_ENABLE_STACK_SNAPSHOT       = 0X10000000,  
    COR_PRF_USE_PROFILE_IMAGES          = 0x20000000,  
    COR_PRF_DISABLE_TRANSPARENCY_CHECKS_UNDER_FULL_TRUST  
                                        = 0x40000000,  
    COR_PRF_DISABLE_ALL_NGEN_IMAGES     = 0x80000000,  
    COR_PRF_ALL                         = 0x8FFFFFFF,  
    COR_PRF_REQUIRE_PROFILE_IMAGE       = COR_PRF_USE_PROFILE_IMAGES |   
                                          COR_PRF_MONITOR_CODE_TRANSITIONS |   
                                          COR_PRF_MONITOR_ENTERLEAVE,  
    COR_PRF_ALLOWABLE_AFTER_ATTACH      = COR_PRF_MONITOR_THREADS |  
                                          COR_PRF_MONITOR_MODULE_LOADS |  
                                          COR_PRF_MONITOR_ASSEMBLY_LOADS |  
                                          COR_PRF_MONITOR_APPDOMAIN_LOADS |  
                                          COR_PRF_ENABLE_STACK_SNAPSHOT |  
                                          COR_PRF_MONITOR_GC |  
                                          COR_PRF_MONITOR_SUSPENDS |  
                                          COR_PRF_MONITOR_CLASS_LOADS |  
                                          COR_PRF_MONITOR_JIT_COMPILATION,  
    COR_PRF_MONITOR_IMMUTABLE           = COR_PRF_MONITOR_CODE_TRANSITIONS |  
                                          COR_PRF_MONITOR_REMOTING |  
                                          COR_PRF_MONITOR_REMOTING_COOKIE |  
                                          COR_PRF_MONITOR_REMOTING_ASYNC |  
                                          COR_PRF_ENABLE_REJIT |  
                                          COR_PRF_ENABLE_INPROC_DEBUGGING |  
                                          COR_PRF_ENABLE_JIT_MAPS |  
                                          COR_PRF_DISABLE_OPTIMIZATIONS |  
                                          COR_PRF_DISABLE_INLINING |  
                                          COR_PRF_ENABLE_OBJECT_ALLOCATED |  
                                          COR_PRF_ENABLE_FUNCTION_ARGS |  
                                          COR_PRF_ENABLE_FUNCTION_RETVAL |  
                                          COR_PRF_ENABLE_FRAME_INFO |  
                                          COR_PRF_USE_PROFILE_IMAGES |  
                     COR_PRF_DISABLE_TRANSPARENCY_CHECKS_UNDER_FULL_TRUST |  
                                          COR_PRF_DISABLE_ALL_NGEN_IMAGES  
} COR_PRF_MONITOR;  
```  
  
## <a name="members"></a>メンバー  
 次のセクションでは一覧`COR_PRF_MONITOR`カテゴリ別の列挙型メンバー。 カテゴリは次のとおりです。  
  
-   [フラグが設定されていません](#None)  
  
-   [コールバック フラグ](#Callback)  
  
-   [機能の有効化フラグ](#Feature)  
  
-   [構成フラグ](#Config)  
  
-   [複合フラグ](#Composite)  
  
<a name="None"></a>   
### <a name="no-flags-set"></a>フラグが設定されていません  
  
|メンバー|説明|  
|------------|-----------------|  
|`COR_PRF_MONITOR_NONE`|フラグが設定されていません。|  
  
<a name="Callback"></a>   
### <a name="callback-flags"></a>コールバック フラグ  
  
|メンバー|説明|  
|------------|-----------------|  
|`COR_PRF_MONITOR_ALL`|すべてのコールバック イベントを有効にします。|  
|`COR_PRF_MONITOR_APPDOMAIN_LOADS`|コントロール、`AppDomainCreation*`と`AppDomainShutdown*`コールバックで、 [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)インターフェイス。|  
|`COR_PRF_MONITOR_ASSEMBLY_LOADS`|コントロール、`AssemblyLoad*`と`AssemblyUnload*`コールバックで、 [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)インターフェイス。|  
|`COR_PRF_MONITOR_CACHE_SEARCHES`|コントロール、`JITCachedFunctionSearch*`コールバックで、 [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)インターフェイス。<br /><br /> このフラグの動作は、.NET Framework バージョン 2.0 で変更されています。|  
|`COR_PRF_MONITOR_CCW`|コントロール、`COMClassicVTable*`コールバックで、 [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)インターフェイス。|  
|`COR_PRF_MONITOR_CLASS_LOADS`|コントロール、`ClassLoad*`と`ClassUnload*`コールバックで、 [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)インターフェイス。|  
|`COR_PRF_MONITOR_CLR_EXCEPTIONS`|コントロール、`ExceptionCLRCatcher*`コールバックで、 [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)インターフェイス。|  
|`COR_PRF_MONITOR_CODE_TRANSITIONS`|コントロール、 [UnmanagedToManagedTransition](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-unmanagedtomanagedtransition-method.md)と[ManagedToUnmanagedTransition](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-managedtounmanagedtransition-method.md)コールバックで、 [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)インターフェイス|  
|`COR_PRF_MONITOR_ENTERLEAVE`|コントロール、 `FunctionEnter*`、 `FunctionLeave*`、および`FunctionTailCall*`[プロファイリング グローバル静的関数](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)します。|  
|`COR_PRF_MONITOR_EXCEPTIONS`|コントロール、 [ExceptionThrown](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionthrown-method.md)コールバックと`ExceptionSearch*`、 `ExceptionOSHandler*`、 `ExceptionUnwind*`、および`ExceptionCatcher*`コールバックで、 [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)インターフェイス。|  
|`COR_PRF_MONITOR_FUNCTION_UNLOADS`|コントロール、 [FunctionUnloadStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-functionunloadstarted-method.md)コールバックで、 [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)インターフェイス。|  
|`COR_PRF_MONITOR_GC`|コントロール、 [GarbageCollectionStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionstarted-method.md)、 [GarbageCollectionFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md)、 [MovedReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-movedreferences-method.md)、 [MovedReferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-movedreferences2-method.md)、 [SurvivingReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-survivingreferences-method.md)、 [SurvivingReferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-survivingreferences2-method.md)、 [ObjectReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectreferences-method.md)、 [ObjectsAllocatedByClass](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectsallocatedbyclass-method.md)、 [RootReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-rootreferences-method.md)、 [RootReferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-rootreferences2-method.md)、 [HandleCreated](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-handlecreated-method.md)、 [HandleDestroyed](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-handledestroyed-method.md)、および[FinalizeableObjectQueued](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-finalizeableobjectqueued-method.md)コールバックで、`ICorProfilerCallback*`インターフェイス。|  
|`COR_PRF_MONITOR_JIT_COMPILATION`|コントロール、 `JITCompilation*`、 [JITFunctionPitched](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitfunctionpitched-method.md)、および[JITInlining](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitinlining-method.md)コールバックで、 [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)インターフェイス。|  
|`COR_PRF_MONITOR_MODULE_LOADS`|コントロール、 `ModuleLoad*`、 `ModuleUnload*`、および[ModuleAttachedToAssembly](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleattachedtoassembly-method.md)コールバックで、 [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)インターフェイス。|  
|`COR_PRF_MONITOR_OBJECT_ALLOCATED`|コントロール、 [ObjectAllocated](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectallocated-method.md)コールバックで、 [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)インターフェイス。|  
|`COR_PRF_MONITOR_REMOTING`|コントロール、`Remoting*`コールバックで、 [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)インターフェイス。|  
|`COR_PRF_MONITOR_REMOTING_ASYNC`|`Remoting*` コールバックが非同期イベントを監視するかどうかを制御します。|  
|`COR_PRF_MONITOR_REMOTING_COOKIE`|クッキーが `Remoting*` コールバックに渡されるかどうかを制御します。|  
|`COR_PRF_MONITOR_SUSPENDS`|コントロール、 `RuntimeSuspend*`、 `RuntimeResume*`、 [RuntimeThreadSuspended](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimethreadsuspended-method.md)、および[RuntimeThreadResumed](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimethreadresumed-method.md)コールバックで、 [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)インターフェイス。|  
|`COR_PRF_MONITOR_THREADS`|コントロール、 [ThreadCreated](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-threadcreated-method.md)、 [ThreadDestroyed](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-threaddestroyed-method.md)、 [ThreadAssignedToOSThread](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-threadassignedtoosthread-method.md)、および[ThreadNameChanged](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-threadnamechanged-method.md)コールバックで、[ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)と[ICorProfilerCallback2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)インターフェイス。|  
  
<a name="Feature"></a>   
### <a name="feature-enabling-flags"></a>機能の有効化フラグ  
  
|メンバー|説明|  
|------------|-----------------|  
|`COR_PRF_ENABLE_FRAME_INFO`|正確な取得できるように`ClassID`ジェネリック関数を呼び出して、 [GetFunctionInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctioninfo2-method.md)メソッドを`COR_PRF_FRAME_INFO`によって返される値、 [FunctionEnter2](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md)コールバック。|  
|`COR_PRF_ENABLE_FUNCTION_ARGS`|により引数のトレースを使用して、 [FunctionEnter2](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md)コールバックまたは[FunctionEnter3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md)コールバックと[GetFunctionEnter3Info](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctionenter3info-method.md)メソッド。|  
|`COR_PRF_ENABLE_FUNCTION_RETVAL`|戻り値を使用してトレースを有効、 [FunctionLeave2](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md)コールバックまたは[FunctionLeave3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md)コールバックと[GetFunctionLeave3Info](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctionleave3info-method.md)メソッド。|  
|`COR_PRF_ENABLE_INPROC_DEBUGGING`|非推奨。<br /><br /> プロセス中のデバッグはサポートされていません。 このフラグは無効です。|  
|`COR_PRF_ENABLE_JIT_MAPS`|非推奨。<br /><br /> により、プロファイラーを使用して IL からネイティブへのマップを取得する[GetILToNativeMapping](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getiltonativemapping-method.md)します。 .NET Framework 2.0 以降、ランタイムは常に IL-to-native マップを追跡するため、このフラグは常に設定されていると見なされます。|  
|`COR_PRF_ENABLE_OBJECT_ALLOCATED`|プロファイラーがオブジェクトの割り当て通知を必要とする可能性があることをランタイムに通知します。 このフラグは、初期化中に設定する必要があります。 これにより、プロファイラーを使用して、その後、`COR_PRF_MONITOR_OBJECT_ALLOCATED`フラグを受け取る[ObjectAllocated](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectallocated-method.md)コールバック。|  
|`COR_PRF_ENABLE_REJIT`|呼び出しを有効に、 [RequestReJIT](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-requestrejit-method.md)と[RequestRevert](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-requestrevert-method.md)メソッド。 プロファイラーは起動時にこのフラグを設定する必要があります。  プロファイラーがこのフラグを設定する場合は、`COR_PRF_DISABLE_ALL_NGEN_IMAGES` も指定する必要があります。|  
|`COR_PRF_ENABLE_STACK_SNAPSHOT`|呼び出しを有効に、 [DoStackSnapshot](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md)メソッド。|  
  
<a name="Config"></a>   
### <a name="configuration-flags"></a>構成フラグ  
  
|メンバー|説明|  
|------------|-----------------|  
|`COR_PRF_DISABLE_ALL_NGEN_IMAGES`|(プロファイラーが拡張したイメージも含めて) すべてのネイティブ イメージがロードされないようにします。  このフラグと `COR_PRF_USE_PROFILE_IMAGES` フラグが両方指定されている場合は、`COR_PRF_DISABLE_ALL_NGEN_IMAGES` が使用されます。|  
|`COR_PRF_DISABLE_INLINING`|すべてのインライン展開を無効にします。|  
|`COR_PRF_DISABLE_OPTIMIZATIONS`|すべてのコードの最適化を無効にします。|  
|`COR_PRF_DISABLE_TRANSPARENCY_CHECKS_UNDER_FULL_TRUST`|セキュリティの透過性チェックを無効にします。このチェックは通常 just-in-time (JIT) コンパイル中に行われ、完全に信頼されているアセンブリではクラスのロード中に行われます。 これにより、いくつかのインストルメンテーションの実行が容易になります。|  
|`COR_PRF_USE_PROFILE_IMAGES`|ネイティブ イメージを検索して、プロファイラーが拡張したイメージを見つけます。 特定のアセンブリでプロファイラーが拡張したイメージが見つからなかった場合、共通言語ランタイムはそのアセンブリの JIT に戻ります。 このフラグと `COR_PRF_DISABLE_ALL_NGEN_IMAGES` フラグが両方指定されている場合は、`COR_PRF_DISABLE_ALL_NGEN_IMAGES` が使用されます。|  
  
<a name="Composite"></a>   
### <a name="composite-flags"></a>複合フラグ  
  
|メンバー|説明|  
|------------|-----------------|  
|`COR_PRF_ALL`|`COR_PRF_MONITOR` のすべてのフラグ値を表します。|  
|`COR_PRF_ALLOWABLE_AFTER_ATTACH`|プロファイラーが実行中のアプリケーションに割り当てられた後に設定することが可能な、`COR_PRF_MONITOR` のすべてのフラグを表します。 構文セクションは、このビットマスク内に存在する個々のフラグを示します。|  
|`COR_PRF_MONITOR_ALL`|すべてのコールバック イベントを有効にします。|  
|`COR_PRF_MONITOR_IMMUTABLE`|初期化中にのみ設定可能な、`COR_PRF_MONITOR` のすべてのフラグを表します。 初期化の後にこれらのいずれかのフラグを変更しようとすると、処理が失敗したことを示す `HRESULT` 値が返されます。|  
|`COR_PRF_REQUIRE_PROFILE_IMAGE`|プロファイルが強化されたイメージを必要とするすべての `COR_PRF_MONITOR` フラグを表しています。|  
  
## <a name="remarks"></a>Remarks  
 A`COR_PRF_MONITOR`で値が使用される、 [icorprofilerinfo::geteventmask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-geteventmask-method.md)と[icorprofilerinfo::seteventmask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md)イベント通知を発行する共通言語ランタイムを定義する方法プロファイラー。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorProf.idl、CorProf.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [列挙型のプロファイリング](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
- [GetEventMask メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-geteventmask-method.md)
- [SetEventMask メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md)
