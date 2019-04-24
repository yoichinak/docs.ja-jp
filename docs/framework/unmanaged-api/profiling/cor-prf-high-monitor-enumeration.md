---
title: COR_PRF_HIGH_MONITOR 列挙型
ms.date: 04/10/2018
ms.assetid: 3ba543d8-15e5-4322-b6e7-1ebfc92ed7dd
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 572fcee528098a4f2929e07dfae63efc56e93dfd
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59081646"
---
# <a name="corprfhighmonitor-enumeration"></a>COR_PRF_HIGH_MONITOR 列挙型
[.NET Framework 4.5.2 以降のバージョンでのみでサポート]  
  
 :Seteventmask2 フラグを提供、 [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md)列挙型を指定できる、プロファイラー、 [icorprofilerinfo 5::seteventmask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md)メソッドが読み込まれます。  
  
## <a name="syntax"></a>構文  
  
```  
typedef enum {  
    COR_PRF_HIGH_MONITOR_NONE                     = 0x00000000,  
    COR_PRF_HIGH_ADD_ASSEMBLY_REFERENCES          = 0x00000001,  
    COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED        = 0x00000002,     
    COR_PRF_HIGH_MONITOR_DYNAMIC_FUNCTION_UNLOADS = 0x00000004,    
    COR_PRF_HIGH_REQUIRE_PROFILE_IMAGE            = 0,  
    COR_PRF_HIGH_ALLOWABLE_AFTER_ATTACH           = COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED | 
                                                    COR_PRF_HIGH_MONITOR_DYNAMIC_FUNCTION_UNLOADS,  
    COR_PRF_HIGH_MONITOR_IMMUTABLE                = 0  
} COR_PRF_HIGH_MONITOR;  
```  
  
## <a name="members"></a>メンバー  
  
|メンバー|説明|  
|------------|-----------------|  
|`COR_PRF_HIGH_MONITOR_NONE`|フラグが設定されていません。|  
|`COR_PRF_HIGH_ADD_ASSEMBLY_REFERENCES`|コントロール、 [icorprofilercallback 6::getassemblyreference](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md) CLR アセンブリ参照クロージャのウォーク中にアセンブリ参照を追加するためのコールバック。|  
|`COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED`|コントロール、 [ICorProfilerCallback7::ModuleInMemorySymbolsUpdated](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback7-moduleinmemorysymbolsupdated-method.md)メモリ内のモジュールに関連付けられているシンボルのストリームを更新するためのコールバック。|  
|`COR_PRF_HIGH_MONITOR_DYNAMIC_FUNCTION_UNLOADS`|コントロール、 [ICorProfilerCallback9::DynamicMethodUnloaded](icorprofilercallback9-dynamicmethodunloaded-method.md)動的メソッドのガベージがされた時点を示すためのコールバックが収集され、アンロードします。 <br/> [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]|   
|`COR_PRF_HIGH_REQUIRE_PROFILE_IMAGE`|プロファイルが強化されたイメージを必要とするすべての `COR_PRF_HIGH_MONITOR` フラグを表しています。 対応する、`COR_PRF_REQUIRE_PROFILE_IMAGE`フラグ、 [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md)列挙体。|  
|`COR_PRF_HIGH_ALLOWABLE_AFTER_ATTACH`|プロファイラーが実行中のアプリケーションに割り当てられた後に設定することが可能な、`COR_PRF_HIGH_MONITOR` のすべてのフラグを表します。|  
|`COR_PRF_HIGH_MONITOR_IMMUTABLE`|初期化中にのみ設定可能な、`COR_PRF_HIGH_MONITOR` のすべてのフラグを表します。 他の場所でこれらのフラグを変更しようとすると、エラーを表す `HRESULT` 値が生じます。|  
  
## <a name="remarks"></a>Remarks  
 `COR_PRF_HIGH_MONITOR`でフラグを使用して、`pdwEventsHigh`のパラメーター、 [icorprofilerinfo 5::geteventmask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-geteventmask2-method.md)と[icorprofilerinfo 5::seteventmask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md)メソッド。  
  
以降では、[!INCLUDE[net_v461](../../../../includes/net-v461-md.md)]の値、`COR_PRF_HIGH_ALLOWABLE_AFTER_ATTACH`を 0 から変更`COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED`(0x00000002)。 以降、.NET Framework 4.7.2 では、その値がから変更された`COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED`に`COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED | COR_PRF_HIGH_MONITOR_DYNAMIC_FUNCTION_UNLOADS`します。   

`COR_PRF_HIGH_MONITOR_IMMUTABLE` 初期化中にのみ設定可能なすべてのフラグを表すビットマスクを指定するためのものです。 結果、失敗した、他の場所でこれらのフラグのいずれかを変更しようとしています。`HRESULT`します。

## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorProf.idl、CorProf.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [列挙型のプロファイリング](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
- [COR_PRF_MONITOR 列挙型](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md)
- [ICorProfilerInfo5 インターフェイス](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-interface.md)
