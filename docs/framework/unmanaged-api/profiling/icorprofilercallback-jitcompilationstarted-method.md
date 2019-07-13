---
title: ICorProfilerCallback::JITCompilationStarted メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.JITCompilationStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::JITCompilationStarted
helpviewer_keywords:
- JITCompilationStarted method [.NET Framework profiling]
- ICorProfilerCallback::JITCompilationStarted method [.NET Framework profiling]
ms.assetid: 31782b36-d311-4518-8f45-25f65385af5b
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a5ba90ce4523fcc55fca3f84a78fa4cfeb6a93f0
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/10/2019
ms.locfileid: "67782825"
---
# <a name="icorprofilercallbackjitcompilationstarted-method"></a>ICorProfilerCallback::JITCompilationStarted メソッド
ジャストイン タイム (JIT) コンパイラが関数のコンパイルを開始されたことをプロファイラーに通知します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT JITCompilationStarted(  
    [in] FunctionID functionId,  
    [in] BOOL       fIsSafeToBlock);  
```  
  
## <a name="parameters"></a>パラメーター  
 `functionId`  
 [in]コンパイルの開始を関数の ID。  
  
 `fIsSafeToBlock`  
 [in]プロファイラーをブロックしているかどうかを示す値は、ランタイムの操作に影響されます。 値が`true`ブロックにより、ランタイムでこのコールバックから返される呼び出し元のスレッドを待機する場合は、それ以外の場合、`false`します。  
  
 値が`true`ランタイムは害を及ぼしません、プロファイリングの結果の傾斜を実行できます。  
  
## <a name="remarks"></a>Remarks  
 1 つ以上のペアを受信することは`JITCompilationStarted`と[icorprofilercallback::jitcompilationfinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationfinished-method.md)ランタイムを呼び出して、各関数の方法により、ハンドル クラスのコンス トラクター。 たとえば、ランタイムの JIT コンパイル メソッド A、開始しますが、クラス B のクラス コンス トラクターを実行する必要があります。 ランタイムの JIT コンパイルではそのため、クラス B のコンス トラクターが実行されるとします。 コンス トラクターが実行されている、メソッド、メソッドを再度 JIT コンパイルに A、A への呼び出しになります。 このシナリオでは、メソッド A の最初の JIT コンパイルが停止します。 ただし、JIT コンパイル メソッド A に両方の試行は、JIT コンパイル イベントで報告されます。 プロファイラーを呼び出すことによってメソッド A 用の Microsoft intermediate language (MSIL) コードを置き換える場合は、 [icorprofilerinfo::setilfunctionbody](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilfunctionbody-method.md)メソッドでは、両方を行う必要があります`JITCompilationStarted`イベントが同じ MSIL ブロックの使用可能性がありますします。  
  
 プロファイラーは、場合、2 つのスレッドではコールバックを行う同時に JIT コールバックのシーケンスをサポートする必要があります。 たとえば、スレッド A が呼び出す`JITCompilationStarted`します。 ただし、スレッド A 呼び出しの前に`JITCompilationFinished`、スレッド B 呼び出し[icorprofilercallback::exceptionsearchfunctionenter](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfunctionenter-method.md)スレッド A にから関数の ID を持つ`JITCompilationStarted`コールバック。 関数の ID がまだされないこと有効が表示されるためへの呼び出し`JITCompilationFinished`プロファイラーがまだ受信したされません。 ただし、このような場合は、関数の ID は有効です。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:** [システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorProf.idl、CorProf.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICorProfilerCallback インターフェイス](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [JITCompilationFinished メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationfinished-method.md)
