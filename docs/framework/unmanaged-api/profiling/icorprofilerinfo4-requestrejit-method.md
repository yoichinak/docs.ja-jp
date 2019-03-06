---
title: ICorProfilerInfo4::RequestReJIT メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo4.RequestReJIT
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo4::RequestReJIT
helpviewer_keywords:
- RequestReJIT method, ICorProfilerInfo4 interface [.NET Framework profiling]
- ICorProfilerInfo4::RequestReJIT method [.NET Framework profiling]
ms.assetid: 781ed736-f30c-4816-920e-3552e36542c6
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 20312b80a4882acdaf53d9bcbf95ae2babe0fdca
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2019
ms.locfileid: "57476721"
---
# <a name="icorprofilerinfo4requestrejit-method"></a>ICorProfilerInfo4::RequestReJIT メソッド
指定された関数のすべてのインスタンスの JIT 再コンパイルを要求します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT RequestReJIT (  
   [in] ULONG    cFunctions,  
   [in, size_is(cFunctions)]  ModuleID    moduleIds[],  
   [in, size_is(cFunctions)]  mdMethodDef methodIds[]);  
```  
  
## <a name="parameters"></a>パラメーター  
 `cFunctions`  
 [in] 再コンパイルする関数の数。  
  
 `moduleIds`  
 [in] 再コンパイルする関数を識別する (`module`、`methodDef`) ペアの `moduleId` の部分を指定します。  
  
 `methodIds`  
 [in] 再コンパイルする関数を識別する (`module`、`methodDef`) ペアの `methodId` の部分を指定します。  
  
## <a name="return-value"></a>戻り値  
 このメソッドは、次の特定の HRESULT と、メソッドの失敗を示す HRESULT エラーも返します。  
  
|HRESULT|説明|  
|-------------|-----------------|  
|S_OK|すべてのメソッドを JIT 再コンパイル対象としてマークする操作が試行されました。 プロファイラーを実装する必要があります、 [icorprofilercallback 4::rejiterror](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejiterror-method.md)メソッドの JIT 再コンパイルが正常にマークされているかのメソッド。|  
|CORPROF_E_CALLBACK4_REQUIRED|プロファイラーを実装する必要があります、 [ICorProfilerCallback4](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md)この呼び出しをサポートするためのインターフェイス。|  
|CORPROF_E_REJIT_NOT_ENABLED|JIT 再コンパイルが有効になっていませんでした。 使用して初期化中に JIT 再コンパイルを有効にする必要があります、 [icorprofilerinfo::seteventmask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md)を設定するメソッド、`COR_PRF_ENABLE_REJIT`フラグ。|  
|E_INVALIDARG|`cFunctions` が 0 であるか、`moduleIds` または `methodIds` が `NULL` です。|  
|||  
|E_OUTOFMEMORY|メモリが不足しているために、CLR は要求を完了できませんでした。|  
  
## <a name="remarks"></a>Remarks  
 指定された一連の関数をこのラインタイムで再コンパイルするため、`RequestReJIT` を呼び出します。 コード プロファイラーを使用できますし、 [ICorProfilerFunctionControl](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-interface.md)関数が再コンパイルされるときに生成されるコードを調整するインターフェイス。 これは、今後の関数呼び出しにのみ影響し、現在実行中の関数には影響しません。 指定されている関数のいずれかが以前に JIT 再コンパイルされている場合、再コンパイルを要求する操作は、関数を元に戻して再コンパイルする操作と同等です。 可逆性を維持するため、JIT コンパイラは関数の元のバージョンのコンパイル時に、インライン処理の決定のために呼び出し先の元のバージョンだけを考慮します。 JIT コンパイラは関数の再コンパイル時に、インライン処理のためにその呼び出し先の現行バージョン (再コンパイル バージョンまたは元のバージョン) を考慮します。  
  
 プロファイラーは一般に、プロファイラーが 1 つ以上のメソッドをインストルメント化することを求めるユーザー入力に対応して `RequestReJIT` を呼び出します。 `RequestReJIT` は一般に、一部の処理を実行するためにランタイムを一時停止します。また、ガベージ コレクションをトリガーする可能性があります。 このためプロファイラーは、現在プロファイラー コールバックを実行している CLR 作成スレッドではなく、以前に作成したスレッドから `RequestReJIT` を呼び出す必要があります。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorProf.idl、CorProf.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>関連項目
- [ICorProfilerInfo4 インターフェイス](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)
- [プロファイリングのインターフェイス](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [プロファイル](../../../../docs/framework/unmanaged-api/profiling/index.md)
