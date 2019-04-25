---
title: ICorProfilerCallback8::DynamicMethodJITCompilationStarted メソッド
ms.date: 04/10/2018
api_name:
- ICorProfilerCallback8.DynamicMethodJITCompilationStarted
api_location:
- mscorwks.dll
- corprof.idl
api_type:
- COM
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c4b8bffeb71497a7dd8e2ed25b833f9216d8017e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59142247"
---
# <a name="icorprofilercallback8dynamicmethodjitcompilationstarted-method"></a>ICorProfilerCallback8::DynamicMethodJITCompilationStarted メソッド
[.NET Framework 4.7 以降のバージョンでサポートされます]  
  
動的メソッドの JIT コンパイルが開始されるたびに、プロファイラーに通知します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT DynamicMethodJITCompilationStarted(  
     [in]  FunctionID  functionId,   
     [in]  BOOL        fIsSafeToBlock,   
     [in]  LPCBYTE     pILHeader,   
     [in]  LONG        cbILHeader   
);  
```  
  
## <a name="parameters"></a>パラメーター  
[入力] `functionId`  
どの JIT コンパイルが開始されてメモリ内の関数の識別子です。   

[in] `fIsSafeToBlock`   
`true` ブロックしていることにより、ランタイムでこのコールバックから返される呼び出し元のスレッドを待機するかを示す`false`をブロックしてに影響しないこと、実行時の操作を示します。  

[in] `pILHeader`    
メソッドの IL のヘッダーの最初のバイトへのポインター。   

[in] `cbILHeader`    
IL ヘッダーのバイト数。 

## <a name="remarks"></a>Remarks  

動的メソッドが JIT コンパイルされるたびに、このコールバックがトリガーされます。 これには、さまざまな IL スタブと LCG メソッドが含まれます。 その目的はプロファイラー ライターをユーザーにコンパイルされたメソッドを識別するために十分な情報を提供します。

> [!NOTE]
> `functionId` 値は、動的メソッドのメタデータがないため、メタデータ トークンを解決するのには使用できません。

`pILHeader`ポインターは、コールバック中にのみ有効です。

## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorProf.idl、CorProf.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  
  
## <a name="see-also"></a>関連項目

- [DynamicMethodJITCompilationFinished メソッド](icorprofilercallback8-dynamicmethodjitcompilationfinished-method.md)
- [ICorProfilerCallback8 インターフェイス](icorprofilercallback8-interface.md)
