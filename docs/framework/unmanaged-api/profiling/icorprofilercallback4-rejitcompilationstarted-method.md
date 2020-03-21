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
ms.openlocfilehash: be257930ca0fad658afa75d6efa4573d4f888a2b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177088"
---
# <a name="icorprofilercallback4rejitcompilationstarted-method"></a>ICorProfilerCallback4::ReJITCompilationStarted メソッド
ジャスト イン タイム (JIT) コンパイラが関数の再コンパイルを開始したことをプロファイラーに通知します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT ReJITCompilationStarted(
    [in] FunctionID functionId,  
    [in] ReJITID    rejitId,  
    [in] BOOL       fIsSafeToBlock);  
```  
  
## <a name="parameters"></a>パラメーター  
 `functionId`  
 [in]JIT コンパイラが再コンパイルを開始した関数の ID。  
  
 `rejitId`  
 [in]関数の新しいバージョンの再コンパイル ID。  
  
 `fIsSafeToBlock`  
 [in]`true`をクリックすると、呼び出し元のスレッドがこのコールバックから返されるのをランタイムが待機する可能性があることを示します。`false`ブロックがランタイムの操作に影響しないことを示します。 値を指定`true`すると、ランタイムに影響はありませんが、プロファイル結果に影響を与える可能性があります。  
  
## <a name="remarks"></a>解説  
 ランタイムがクラス コンストラクターを処理する方法により`ReJITCompilationStarted`、各関数に対して複数のペアと[ReJITCompilationFinished](icorprofilercallback4-rejitcompilationfinished-method.md)メソッド呼び出しを受け取ることも可能です。 たとえば、ランタイムはメソッド A の再コンパイルを開始しますが、クラス B のクラス コンストラクターを実行する必要があります。 したがって、ランタイムはクラス B のコンストラクターを再コンパイルして実行します。 コンストラクターの実行中にメソッド A が呼び出され、メソッド A が再コンパイルされます。 このシナリオでは、メソッド A の最初の再コンパイルが停止します。 ただし、メソッド A の再コンパイルは、両方とも JIT 再コンパイル イベントと共に報告されます。  
  
 2 つのスレッドが同時にコールバックを行っている場合、プロファイラーは JIT 再コンパイル コールバックのシーケンスをサポートする必要があります。 たとえば、スレッド A`ReJITCompilationStarted`が呼び出し、ただし、スレッド A[が ReJITCompilationFinished を](icorprofilercallback4-rejitcompilationfinished-method.md)呼び出す前に、スレッド B は、スレッド A`ReJITCompilationStarted`のコールバックから関数 ID を使用して[ICorProfilerCallback::ExceptionSearchFunctionEnter を](icorprofilercallback-exceptionsearchfunctionenter-method.md)呼び出します。[ReJITCompilationFinished](icorprofilercallback4-rejitcompilationfinished-method.md)の呼び出しがプロファイラーによって受信されていないため、関数 ID がまだ有効でないように見える場合があります。 ただし、この場合、関数 ID は有効です。  
  
## <a name="requirements"></a>必要条件  
 **:**「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー** : CorProf.idl、CorProf.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICorProfilerCallback インターフェイス](icorprofilercallback-interface.md)
- [ICorProfilerCallback4 インターフェイス](icorprofilercallback4-interface.md)
- [JITCompilationFinished メソッド](icorprofilercallback-jitcompilationfinished-method.md)
- [ReJITCompilationFinished メソッド](icorprofilercallback4-rejitcompilationfinished-method.md)
