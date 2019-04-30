---
title: ICorProfilerInfo3::GetFunctionEnter3Info メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo3.GetFunctionEnter3Info Method
api_location:
- Mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo3::GetFunctionEnter3Info
helpviewer_keywords:
- GetFunctionEnter3Info method [.NET Framework profiling]
- ICorProfilerInfo3::GetFunctionEnter3Info method [.NET Framework profiling]
ms.assetid: 542c7c65-dd56-4651-b76f-5db2465e4a15
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8df3700c6002e7a181d4882c4afd8542c6b6c93a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62049532"
---
# <a name="icorprofilerinfo3getfunctionenter3info-method"></a>ICorProfilerInfo3::GetFunctionEnter3Info メソッド
によってプロファイラーに報告される関数のスタック フレームおよび引数情報を提供、 [FunctionEnter3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md)関数。 このメソッドは、`FunctionEnter3WithInfo` コールバック中にのみ呼び出すことができます。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT GetFunctionEnter3Info(  
            [in]  FunctionID functionId,   
            [in]  COR_PRF_ELT_INFO eltInfo,  
            [out] COR_PRF_FRAME_INFO *pFrameInfo,  
            [in, out] ULONG *pcbArgumentInfo,  
            [out, size_is(*pcbArgumentInfo)]  
                  COR_PRF_FUNCTION_ARGUMENT_INFO *pArgumentInfo);  
```  
  
## <a name="parameters"></a>パラメーター  
 `functionId`  
 [in] 入力される関数の `FunctionID`。  
  
 `eltInfo`  
 [in] 特定のスタック フレームに関する情報を表す不透明ハンドル。 プロファイラーを提供する必要があります、同じ`eltInfo`によって指定されたもの、 [FunctionEnter3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md)関数。  
  
 `pFrameInfo`  
 [out] 特定のスタック フレームに関するジェネリック情報を表す不透明ハンドル。 このハンドルは、プロファイラーが `FunctionEnter3WithInfo` メソッドを呼び出した `GetFunctionEnter3Info` コールバック内でのみ有効です。  
  
 `pcbArgumentInfo`  
 [入力、出力]合計サイズ (バイト単位) へのポインターの[COR_PRF_FUNCTION_ARGUMENT_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-function-argument-info-structure.md)構造 (、追加[COR_PRF_FUNCTION_ARGUMENT_RANGE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-function-argument-range-structure.md) によって示される引数範囲内の構造体`pArgumentInfo`). 指定されたサイズの大きさが十分でない場合、ERROR_INSUFFICIENT_BUFFER が戻り、必要なサイズが `pcbArgumentInfo` に格納されます。 `GetFunctionEnter3Info` を呼び出して `*pcbArgumentInfo` の必要な値を取得するには、`*pcbArgumentInfo` を 0 に、`pArgumentInfo` を NULL にそれぞれ設定します。  
  
 `pArgumentInfo`  
 [out]ポインターを[COR_PRF_FUNCTION_ARGUMENT_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-function-argument-info-structure.md)左から右の順序でのメモリ内の関数の引数の場所を記述する構造体。  
  
## <a name="remarks"></a>Remarks  
 プロファイラーは、調べている関数の `COR_PRF_FUNCTION_ARGUMENT_INFO` 構造体に十分な領域を割り当て、`pcbArgumentInfo` パラメーターでサイズを示す必要があります。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorProf.idl、CorProf.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [FunctionEnter3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md)
- [FunctionLeave3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md)
- [FunctionTailcall3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md)
- [ICorProfilerInfo3 インターフェイス](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)
- [プロファイリングのインターフェイス](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [プロファイル](../../../../docs/framework/unmanaged-api/profiling/index.md)
