---
title: ICorProfilerCallback4::ReJITError メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback4.ReJITError
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback4::ReJITError
helpviewer_keywords:
- ReJITError method, ICorProfilerCallback4 interface [.NET Framework profiling]
- ICorProfilerCallback4::ReJITError method [.NET Framework profiling]
ms.assetid: d7888aa9-dfaa-420f-9f99-e06ab35ca482
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 66f152279a21f28b54acebbf0be7c65bb73efa70
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59150593"
---
# <a name="icorprofilercallback4rejiterror-method"></a>ICorProfilerCallback4::ReJITError メソッド
ジャストイン タイム (JIT) コンパイラに再コンパイル プロセスでエラーが発生したことをプロファイラーに通知します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT ReJITError(  
    [in] ModuleID    moduleId,  
    [in] mdMethodDef methodId,  
    [in] FunctionID  functionId,  
    [in] HRESULT     hrStatus);  
```  
  
## <a name="parameters"></a>パラメーター  
 `moduleID`  
 [in]`ModuleID`再コンパイルが失敗した試行が行われる。  
  
 `methodId`  
 [in]`MethodDef`の再コンパイルが失敗した試行が行われたメソッド。  
  
 `functionId`  
 [in]再コンパイルされたまたはマークの再コンパイルされている関数のインスタンス。 この値は、 `NULL` (たとえば、プロファイラーには、再コンパイルするメソッドを無効なメタデータ トークンが指定された) 場合、インスタンス化ごとにではなく、メソッドごとに障害が発生したかどうか。  
  
 `hrStatus`  
 [in]エラーの性質を示す HRESULT。 値の一覧については、状態 HRESULT」を参照してください。  
  
## <a name="return-value"></a>戻り値  
 このコールバックからの戻り値は無視されます。  
  
## <a name="status-hresults"></a>状態 HRESULT  
  
|状態配列 HRESULT|説明|  
|--------------------------|-----------------|  
|E_INVALIDARG|`moduleID`または`methodDef`トークンが`NULL`します。|  
|CORPROF_E_DATAINCOMPLETE|モジュールが完全に読み込まれていないか、またはアンロード中です。|  
|CORPROF_E_MODULE_IS_DYNAMIC|指定したモジュールを動的に生成されました (たとえば、 `Reflection.Emit`) はこのメソッドによってサポートされていませんので。|  
|CORPROF_E_FUNCTION_IS_COLLECTIBLE|メソッドは、収集可能なアセンブリにインスタンス化であるため再コンパイルすることができません。 型に注意してくださいと非リフレクション コンテキストで定義されている関数 (たとえば、 `List<MyCollectibleStruct>`) 収集可能なアセンブリにインスタンス化することができます。|  
|E_OUTOFMEMORY|CLR は JIT 再コンパイルの指定したメソッドをマークしているときにメモリ不足になりました。|  
|その他|オペレーティング システムは、CLR 制御範囲外のエラーを返しました。 たとえば、メモリのページのアクセスの保護を変更するシステム コールに失敗した場合、オペレーティング システム エラーが表示されます。|  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorProf.idl、CorProf.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICorProfilerCallback インターフェイス](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [ICorProfilerCallback4 インターフェイス](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md)
