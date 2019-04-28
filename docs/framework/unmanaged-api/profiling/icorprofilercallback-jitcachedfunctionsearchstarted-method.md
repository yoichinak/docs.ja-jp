---
title: ICorProfilerCallback::JITCachedFunctionSearchStarted メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.JITCachedFunctionSearchStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::JITCachedFunctionSearchStarted
helpviewer_keywords:
- JITCachedFunctionSearchStarted method [.NET Framework profiling]
- ICorProfilerCallback::JITCachedFunctionSearchStarted method [.NET Framework profiling]
ms.assetid: 5cba642c-0d80-48ee-889d-198c5044d821
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3550f4da497574ea5076766ad201e9431af52e4c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61598034"
---
# <a name="icorprofilercallbackjitcachedfunctionsearchstarted-method"></a>ICorProfilerCallback::JITCachedFunctionSearchStarted メソッド
ネイティブ イメージ ジェネレーター (NGen.exe) を使用して以前にコンパイルされた関数の検索が開始されたことをプロファイラーに通知します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT JITCachedFunctionSearchStarted(  
    [in]  FunctionID functionId,  
    [out] BOOL *pbUseCachedFunction);  
```  
  
## <a name="parameters"></a>パラメーター  
 `functionId`  
 [in]検索が実行されている関数の ID。  
  
 `pbUseCachedFunction`  
 [out]`true`場合 (該当する場合)、実行エンジンはキャッシュされたバージョンの関数を使用する必要があります。 そうしないと`false`します。 値が場合`false`、実行エンジンは JIT コンパイル、JIT コンパイルではないバージョンを使用する代わりに関数。  
  
## <a name="remarks"></a>Remarks  
 .NET Framework version 2.0 で、`JITCachedFunctionSearchStarted`と[icorprofilercallback::jitcachedfunctionsearchfinished メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcachedfunctionsearchfinished-method.md)正規の NGen イメージのすべての関数のコールバックは行われません。 プロファイル用に最適化された NGen イメージだけでは、イメージのすべての関数のコールバックが生成されます。 ただし、追加のオーバーヘッドが原因で、プロファイラー NGen イメージのプロファイラーを最適化する必要があります要求した場合、関数のコンパイル済みの just-in-time (JIT) を強制的にこれらのコールバックを使用する場合にのみにします。 それ以外の場合、プロファイラーは、関数の情報を収集するため、遅延の戦略を使用してください。  
  
 プロファイラーは、プロファイリング対象のアプリケーションの複数のスレッドが、同じメソッドを同時に呼び出す場合をサポートする必要があります。 たとえば、スレッド A が呼び出す`JITCachedFunctionSearchStarted`し応答する状態を設定して、プロファイラー *pbUseCachedFunction*に JIT コンパイルを強制する場合は FALSE。 スレッド A はその呼び出し[icorprofilercallback::jitcompilationstarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationstarted-method.md)と[icorprofilercallback::jitcompilationfinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationfinished-method.md)します。  
  
 スレッド B の呼び出しのようになりました`JITCachedFunctionSearchStarted`同じ関数。 プロファイラーがスレッド B が、プロファイラーがスレッドの呼び出し前に、コールバックを送信するために、2 番目のコールバックを受け取る場合でも、プロファイラーが、関数の JIT コンパイルする意向を説明すると、`JITCachedFunctionSearchStarted`します。 これで、スレッドは呼び出しを行う順序は、スレッドをスケジュールする方法に依存します。  
  
 によって参照される値を設定する必要があります、プロファイラーは、重複するコールバックを受信すると`pbUseCachedFunction`重複するすべてのコールバックの同じ値にします。 つまり、`JITCachedFunctionSearchStarted`同じで複数回呼び出された`functionId`値、プロファイラー対応する必要が同じたび。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorProf.idl、CorProf.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICorProfilerCallback インターフェイス](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
