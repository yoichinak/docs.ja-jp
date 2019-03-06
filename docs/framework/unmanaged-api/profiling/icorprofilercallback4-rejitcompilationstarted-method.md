---
title: ICorProfilerCallback4::ReJITCompilationStarted メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback4.ReJITCompilationStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback4::ReJITCompilationStarted
helpviewer_keywords:
- ReJITCompilationStarted method, ICorProfilerCallback4 interface [.NET Framework profiling]
- ICorProfilerCallback4::ReJITCompilationStarted method [.NET Framework profiling]
ms.assetid: 512fdd00-262a-4456-a075-365ef4133c4d
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 83caaa04481b4ed92407294584512b38553710b4
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2019
ms.locfileid: "57501488"
---
# <a name="icorprofilercallback4rejitcompilationstarted-method"></a>ICorProfilerCallback4::ReJITCompilationStarted メソッド
関数を再コンパイル、ジャストイン タイム (JIT) コンパイラが開始されたことをプロファイラーに通知します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT ReJITCompilationStarted(   
    [in] FunctionID functionId,  
    [in] ReJITID    rejitId,  
    [in] BOOL       fIsSafeToBlock);  
```  
  
## <a name="parameters"></a>パラメーター  
 `functionId`  
 [in]再コンパイル、JIT コンパイラが開始した関数の ID。  
  
 `rejitId`  
 [in]関数の新しいバージョンの再コンパイルの ID。  
  
 `fIsSafeToBlock`  
 [in]`true`をブロックしていることにより、ランタイムでこのコールバックから返される呼び出し元のスレッドを待機するかを示す`false`をブロックしてに影響しないこと、実行時の操作を示します。 値`true`ランタイムは害を及ぼしませんが、プロファイリングの結果に影響を与えることができます。  
  
## <a name="remarks"></a>Remarks  
 1 つ以上のペアを受信することは`ReJITCompilationStarted`と[ReJITCompilationFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejitcompilationfinished-method.md)メソッド呼び出しの各関数の方法により、ランタイム ハンドル クラスのコンス トラクター。 たとえば、メソッドを再コンパイルする、ランタイムが開始されますが、クラス B のクラス コンス トラクターを実行する必要があります。 そのため、ランタイムは B クラスのコンス トラクターを再コンパイルし、それを実行します。 コンス トラクターが実行されている、A で、メソッド、もう一度再コンパイルすると、メソッドの呼び出しになります。 このシナリオでは、メソッド A の最初の再コンパイルが停止します。 ただし、両方は、メソッドの JIT 再コンパイル イベントで報告されるが再コンパイルを試行します。  
  
 プロファイラーは、場合、2 つのスレッドではコールバックを行う同時に JIT 再コンパイルのコールバックのシーケンスをサポートする必要があります。 たとえば、スレッド A が呼び出す`ReJITCompilationStarted`ただし、スレッド A 呼び出しの前に[ReJITCompilationFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejitcompilationfinished-method.md)、スレッド B 呼び出し[icorprofilercallback::exceptionsearchfunctionenter](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfunctionenter-method.md)関数の id。`ReJITCompilationStarted`スレッド A のコールバック関数の ID がまだされないこと有効が表示されるためへの呼び出し[ReJITCompilationFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejitcompilationfinished-method.md)プロファイラーがまだ受信したされません。 ただし、この場合、関数の ID は有効です。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorProf.idl、CorProf.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>関連項目
- [ICorProfilerCallback インターフェイス](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [ICorProfilerCallback4 インターフェイス](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md)
- [JITCompilationFinished メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationfinished-method.md)
- [ReJITCompilationFinished メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejitcompilationfinished-method.md)
