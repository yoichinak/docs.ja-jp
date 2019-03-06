---
title: ICorProfilerCallback::JITCachedFunctionSearchFinished メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.JITCachedFunctionSearchFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::JITCachedFunctionSearchFinished
helpviewer_keywords:
- JITCachedFunctionSearchFinished method [.NET Framework profiling]
- ICorProfilerCallback::JITCachedFunctionSearchFinished method [.NET Framework profiling]
ms.assetid: 3c325c82-cddd-4b00-b3da-e450c36abf62
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 49f47b23cba64b16b5d9322e82695623f0a5ca03
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2019
ms.locfileid: "57494494"
---
# <a name="icorprofilercallbackjitcachedfunctionsearchfinished-method"></a>ICorProfilerCallback::JITCachedFunctionSearchFinished メソッド
ネイティブ イメージ ジェネレーター (NGen.exe) を使用して以前にコンパイルされた関数の検索が完了したことをプロファイラーに通知します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT JITCachedFunctionSearchFinished(  
    [in] FunctionID        functionId,  
    [in] COR_PRF_JIT_CACHE result);  
```  
  
## <a name="parameters"></a>パラメーター  
 `functionId`  
 [in]検索の実行対象の関数の ID。  
  
 `result`  
 [in]値、 [COR_PRF_JIT_CACHE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-jit-cache-enumeration.md)検索の結果を示す列挙体。  
  
## <a name="remarks"></a>Remarks  
 .NET Framework version 2.0 で、 [icorprofilercallback::jitcachedfunctionsearchstarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcachedfunctionsearchstarted-method.md)と`JITCachedFunctionSearchFinished`正規の NGen イメージのすべての関数のコールバックは行われません。 プロファイラー用に最適化された NGen イメージだけでは、イメージのすべての関数のコールバックが生成されます。 ただし、追加のオーバーヘッドが原因で、プロファイラー NGen イメージのプロファイラーを最適化する必要があります要求した場合、関数のコンパイル済みの just-in-time (JIT) を強制的にこれらのコールバックを使用する場合にのみにします。 それ以外の場合、プロファイラーは、関数の情報を収集するため、遅延の戦略を使用してください。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorProf.idl、CorProf.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目
- [ICorProfilerCallback インターフェイス](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
