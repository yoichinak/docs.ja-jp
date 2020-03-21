---
title: メソッドを開始 :Dしました。
ms.date: 04/10/2018
api_name:
- ICorProfilerCallback8.DynamicMethodJITCompilationStarted
api_location:
- mscorwks.dll
- corprof.idl
api_type:
- COM
ms.openlocfilehash: e8b1a243b691d8d5eb364fd16821fd9156505c60
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177047"
---
# <a name="icorprofilercallback8dynamicmethodjitcompilationstarted-method"></a>メソッドを開始 :Dしました。
[.NET Framework 4.7 以降のバージョンでサポートされています]  
  
動的メソッドの JIT コンパイルが開始されるたびにプロファイラーに通知します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT DynamicMethodJITCompilationStarted(  
     [in]  FunctionID  functionId,
     [in]  BOOL        fIsSafeToBlock,
     [in]  LPCBYTE     pILHeader,
     [in]  LONG        cbILHeader
);  
```  
  
## <a name="parameters"></a>パラメーター  
[入力] `functionId`  
JIT コンパイルを開始するインメモリ関数の識別子。

[in]`fIsSafeToBlock`をクリックすると、呼び出し元のスレッドがこのコールバックから返されるのをランタイムが待機する可能性があることを示
`true`します。`false`ブロックがランタイムの操作に影響しないことを示します。  

[in]`pILHeader`メソッドの IL ヘッダーの最初のバイトへのポインター。

[in]`cbILHeader` IL ヘッダーのバイト数。

## <a name="remarks"></a>解説  

このコールバックは、動的メソッドが JIT コンパイルされたときにトリガーされます。 これには、さまざまな IL スタブと LCG メソッドが含まれます。 その目的は、プロファイラーの作成者に、コンパイルされたメソッドを識別するための十分な情報をユーザーに提供することです。

> [!NOTE]
> `functionId`動的メソッドにはメタデータがないため、値をメタデータ トークンに解決するために使用することはできません。

ポインター`pILHeader`はコールバック中にのみ有効です。

## <a name="requirements"></a>必要条件  
 **:**「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー** : CorProf.idl、CorProf.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  
  
## <a name="see-also"></a>関連項目

- [DynamicMethodJITCompilationFinished メソッド](icorprofilercallback8-dynamicmethodjitcompilationfinished-method.md)
- [ICorProfilerCallback8 インターフェイス](icorprofilercallback8-interface.md)
