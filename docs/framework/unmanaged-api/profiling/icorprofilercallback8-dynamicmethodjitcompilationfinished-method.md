---
title: ICorProfilerCallback8::DynamicMethodJITCompilationFinished メソッド
ms.date: 04/10/2018
api_name:
- ICorProfilerCallback8.DynamicMethodJITCompilationFinished
api_location:
- mscorwks.dll
- corprof.idl
api_type:
- COM
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ba9f9d4ee5f95def3dcd2d757517e225c826cb9e
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/10/2019
ms.locfileid: "67757993"
---
# <a name="icorprofilercallback8dynamicmethodjitcompilationfinished-method"></a>ICorProfilerCallback8::DynamicMethodJITCompilationFinished メソッド
[.NET Framework 4.7 以降のバージョンでサポートされます]  
  
動的メソッドの JIT コンパイルが完了したときに、プロファイラーに通知します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT DynamicMethodJITCompilationFinished(  
     [in]  FunctionID  functionId,   
     [in]  BOOL        hrStatus,   
     [in]  BOOL        fIsSafeToBlock   
);  
```  
  
## <a name="parameters"></a>パラメーター  
[入力] `functionId`  
どの JIT コンパイルが開始されてメモリ内の関数の識別子です。   

[in] `hrStatus`   
JIT コンパイルが成功したかどうかを示す値。

[in] `fIsSafeToBlock`   
`true` ブロックしていることにより、ランタイムでこのコールバックから返される呼び出し元のスレッドを待機するかを示す`false`をブロックしてに影響しないこと、実行時の操作を示します。  

## <a name="remarks"></a>Remarks  

動的メソッドの JIT コンパイルが完了するたびに、このコールバックがトリガーされます。 これには、さまざまな IL スタブと LCG メソッドが含まれます。 その目的はプロファイラー ライターをユーザーにコンパイルされたメソッドを識別するために十分な情報を提供します。

> [!NOTE]
> `functionId` 値は、動的メソッドのメタデータがないため、メタデータ トークンを解決するのには使用できません。

## <a name="requirements"></a>必要条件  
 **プラットフォーム:** [システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorProf.idl、CorProf.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  
  
## <a name="see-also"></a>関連項目

- [DynamicMethodJITCompilationStarted メソッド](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md)
- [ICorProfilerCallback8 インターフェイス](icorprofilercallback8-interface.md)
