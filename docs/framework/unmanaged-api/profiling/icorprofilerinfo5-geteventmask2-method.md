---
title: ICorProfilerInfo5::GetEventMask2 メソッド
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICorProfilerInfo5.GetEventMask2
api_location:
- mscorwks.dll
api_type:
- COM
ms.assetid: f854b68f-009c-4ffb-89cd-ca874d1c0fb7
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f8ebddf9a16b2eddbbc58342f68b517064e8d794
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62041043"
---
# <a name="icorprofilerinfo5geteventmask2-method"></a>ICorProfilerInfo5::GetEventMask2 メソッド
[.NET Framework 4.5.2 以降のバージョンでのみでサポート]  
  
 現在のイベント カテゴリを取得します。プロファイラーは、これに関する通知を共通言語ランタイム (CLR) から受け取ります。  によって提供されない機能を提供しますが、 [icorprofilerinfo::geteventmask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-geteventmask-method.md)メソッド。  
  
## <a name="syntax"></a>構文  
  
```cpp
HRESULT GetEventMask2(  
        [out] DWORD* pdwEventsLow,  
        [out] DWORD* pdwEventsHigh  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `pdwEventsLow`  
 [out] イベントのカテゴリを指定する 4 バイト値へのポインター。 各ビットは、異なる性能、動作、またはイベントの型を制御します。 ビットが記載されて、 [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md)列挙体。  
  
 `pdwEventsHigh`  
 [out] イベントのカテゴリを指定する 4 バイト値へのポインター。  各ビットは、異なる性能、動作、またはイベントの型を制御します。 ビットが記載されて、 [COR_PRF_HIGH_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-high-monitor-enumeration.md)列挙体。  
  
## <a name="remarks"></a>Remarks  
 `GetEventMask2` メソッドは、プロファイラーがサブスクライブしたコールバックを判断するのに使用します。 論理 OR を実行する、通常、`pdwEventsLow`と`pdwEventsHigh`値と新しいビットを設定し、呼び出すたい、 [SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md)メソッド。  
  
 このメソッドは、推奨される代替、 [GetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-geteventmask-method.md)メソッド。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorProf.idl、CorProf.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICorProfilerInfo5 インターフェイス](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-interface.md)
- [SetEventMask2 メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md)
