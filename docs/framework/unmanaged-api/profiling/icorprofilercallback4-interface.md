---
title: ICorProfilerCallback4 インターフェイス
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback4
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback4
helpviewer_keywords:
- ICorProfilerCallback4 interface [.NET Framework profiling]
ms.assetid: 665f3cfc-cd6f-4880-906c-ea65ad384783
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3eb1f46900199db65be5d14c56bfc0b6f55bf269
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59205135"
---
# <a name="icorprofilercallback4-interface"></a>ICorProfilerCallback4 インターフェイス
共通言語ランタイム (CLR) がプロファイラーに情報を通信に使用するコールバック メソッドを提供します。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[GetReJITParameters メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-getrejitparameters-method.md)|新しい再コンパイルされたメソッド本体の代替コード生成フラグを設定するコード プロファイラーを使用できます。|  
|[MovedReferences2 メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-movedreferences2-method.md)|圧縮ガベージ コレクション ヒープ内のオブジェクトの新しいレイアウトを報告します。|  
|[ReJITCompilationFinished メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejitcompilationfinished-method.md)|ジャストイン タイム (JIT) コンパイラが関数の再コンパイルを完了したことをプロファイラーに通知します。|  
|[ReJITCompilationStarted メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejitcompilationstarted-method.md)|関数を再コンパイル、ジャストイン タイム (JIT) コンパイラが開始されたことをプロファイラーに通知します。|  
|[ReJITError メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejiterror-method.md)|再コンパイル要求の処理中に発生したエラーを報告します。|  
|[SurvivingReferences2 メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-survivingreferences2-method.md)|非圧縮ガベージ コレクションを実行した後の、ヒープ内のオブジェクトのレイアウトを報告します。|  
  
## <a name="remarks"></a>Remarks  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorProf.idl、CorProf.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICorProfilerCallback2 インターフェイス](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)
- [プロファイリングのインターフェイス](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [ICorProfilerInfo インターフェイス](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
