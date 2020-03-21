---
title: COR_PRF_HIGH_MONITOR 列挙型
ms.date: 04/10/2018
ms.assetid: 3ba543d8-15e5-4322-b6e7-1ebfc92ed7dd
ms.openlocfilehash: 5c6e34746368a7658c43fe0e2472000c29292569
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175214"
---
# <a name="cor_prf_high_monitor-enumeration"></a>COR_PRF_HIGH_MONITOR 列挙型

[.NET Framework 4.5.2 以降のバージョンでのみでサポート]  
  
プロファイラーが読み込み中に[ICorProfilerInfo5::SetEventMask2](icorprofilerinfo5-seteventmask2-method.md)メソッドに指定できる[COR_PRF_MONITOR](cor-prf-monitor-enumeration.md)列挙で見つかったものに加えて、フラグを提供します。  
  
## <a name="syntax"></a>構文  
  
```cpp
typedef enum {  
    COR_PRF_HIGH_MONITOR_NONE                     = 0x00000000,  
    COR_PRF_HIGH_ADD_ASSEMBLY_REFERENCES          = 0x00000001,  
    COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED        = 0x00000002,
    COR_PRF_HIGH_MONITOR_DYNAMIC_FUNCTION_UNLOADS = 0x00000004,
    COR_PRF_HIGH_DISABLE_TIERED_COMPILATION       = 0x00000008,
    COR_PRF_HIGH_BASIC_GC                         = 0x00000010,
    COR_PRF_HIGH_MONITOR_GC_MOVED_OBJECTS         = 0x00000020,
    COR_PRF_HIGH_MONITOR_LARGEOBJECT_ALLOCATED    = 0x00000040,
    COR_PRF_HIGH_REQUIRE_PROFILE_IMAGE            = 0,  
    COR_PRF_HIGH_ALLOWABLE_AFTER_ATTACH           = COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED |
                                                    COR_PRF_HIGH_MONITOR_DYNAMIC_FUNCTION_UNLOADS |
                                                    COR_PRF_HIGH_BASIC_GC |
                                                    COR_PRF_HIGH_MONITOR_GC_MOVED_OBJECTS |
                                                    COR_PRF_HIGH_MONITOR_LARGEOBJECT_ALLOCATED,  
    COR_PRF_HIGH_MONITOR_IMMUTABLE                = COR_PRF_HIGH_DISABLE_TIERED_COMPILATION  
} COR_PRF_HIGH_MONITOR;  
```  
  
## <a name="members"></a>メンバー  
  
|メンバー|説明|  
|------------|-----------------|  
|`COR_PRF_HIGH_MONITOR_NONE`|フラグが設定されていません。|  
|`COR_PRF_HIGH_ADD_ASSEMBLY_REFERENCES`|CLR アセンブリ参照クロージャウォーク中にアセンブリ参照を追加するための[ICorProfilerCallback6::GetAssemblyReference](icorprofilercallback6-getassemblyreferences-method.md)コールバックを制御します。|  
|`COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED`|メモリ内[モジュール](icorprofilercallback7-moduleinmemorysymbolsupdated-method.md)に関連付けられたシンボル ストリームの更新のコールバックを制御します。|  
|`COR_PRF_HIGH_MONITOR_DYNAMIC_FUNCTION_UNLOADS`|動的メソッドがガベージ コレクションおよびアンロードされたタイミングを示す[ICorProfilerCallback9::DynamicMethodUnloaded](icorprofilercallback9-dynamicmethodunloaded-method.md)コールバックを制御します。 <br/> [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]|
|`COR_PRF_HIGH_DISABLE_TIERED_COMPILATION`|.NET Core 3.0 以降のバージョンのみ: プロファイラーの[階層化コンパイル](../../../core/whats-new/dotnet-core-3-0.md)を無効にします。|
|`COR_PRF_HIGH_BASIC_GC`|.NET Core 3.0 以降のバージョンのみ: と比較して軽量[`COR_PRF_MONITOR_GC`](cor-prf-monitor-enumeration.md)の GC プロファイリング オプションを提供します。 コールバックのみを制御[GarbageCollectionStarted](icorprofilercallback2-garbagecollectionstarted-method.md)します。 [GarbageCollectionFinished](icorprofilercallback2-garbagecollectionfinished-method.md) [GetGenerationBounds](icorprofilerinfo2-getgenerationbounds-method.md) フラグと`COR_PRF_MONITOR_GC`は異`COR_PRF_HIGH_BASIC_GC`なり、同時実行ガベージ コレクションは無効にしません。|
|`COR_PRF_HIGH_MONITOR_GC_MOVED_OBJECTS`|.NET Core 3.0 以降のバージョンのみ: GC を最適化するためだけに[、移動参照](icorprofilercallback-movedreferences-method.md)と[移動参照 2](icorprofilercallback4-movedreferences2-method.md)コールバックを有効にします。|
|`COR_PRF_HIGH_MONITOR_LARGEOBJECT_ALLOCATED`|.NET Core 3.0 以降のバージョンのみ[`COR_PRF_MONITOR_OBJECT_ALLOCATED`](cor-prf-monitor-enumeration.md): に類似していますが、ラージ オブジェクト ヒープ (LOH) のオブジェクト割り当てについてのみ情報を提供します。|
|`COR_PRF_HIGH_REQUIRE_PROFILE_IMAGE`|プロファイルが強化されたイメージを必要とするすべての `COR_PRF_HIGH_MONITOR` フラグを表しています。 これは[、COR_PRF_MONITOR](cor-prf-monitor-enumeration.md)列挙体`COR_PRF_REQUIRE_PROFILE_IMAGE`のフラグに対応します。|  
|`COR_PRF_HIGH_ALLOWABLE_AFTER_ATTACH`|プロファイラーが実行中のアプリケーションに割り当てられた後に設定することが可能な、`COR_PRF_HIGH_MONITOR` のすべてのフラグを表します。|  
|`COR_PRF_HIGH_MONITOR_IMMUTABLE`|初期化中にのみ設定可能な、`COR_PRF_HIGH_MONITOR` のすべてのフラグを表します。 他の場所でこれらのフラグを変更しようとすると、エラーを表す `HRESULT` 値が生じます。|  
  
## <a name="remarks"></a>解説

フラグ`COR_PRF_HIGH_MONITOR`は、`pdwEventsHigh`[メソッド](icorprofilerinfo5-geteventmask2-method.md)のパラメーターで使用されます。 [ICorProfilerInfo5::SetEventMask2](icorprofilerinfo5-seteventmask2-method.md)  
  
NET Framework 4.6.1 以降、0 から`COR_PRF_HIGH_ALLOWABLE_AFTER_ATTACH`(0x0000002) に`COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED`変更された値。 NET Framework 4.7.2 以降の値は、`COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED``COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED | COR_PRF_HIGH_MONITOR_DYNAMIC_FUNCTION_UNLOADS`から に変更されました。

`COR_PRF_HIGH_MONITOR_IMMUTABLE`は初期化中にしか設定できないすべてのフラグを表すビットマスクを意図しています。 これらのフラグを他の場所で変更しようとすると、失敗します`HRESULT`。

## <a name="requirements"></a>必要条件

**:**「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。  
  
**ヘッダー** : CorProf.idl、CorProf.h  
  
**ライブラリ:** CorGuids.lib  
  
**.NET Framework のバージョン:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [列挙体のプロファイリング](profiling-enumerations.md)
- [COR_PRF_MONITOR 列挙型](cor-prf-monitor-enumeration.md)
- [ICorProfilerInfo5 インターフェイス](icorprofilerinfo5-interface.md)
