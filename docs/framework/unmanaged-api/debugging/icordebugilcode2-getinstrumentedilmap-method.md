---
title: ICorDebugILCode2::GetInstrumentedILMap メソッド
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICorDebugILCode2.GetInstrumentedILMap
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 7a4e3085-8f95-40ef-a4be-7d6146f47ce2
topic_type:
- apiref
ms.openlocfilehash: 7dede4e5af702f1b86b430450db4a669c326c062
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131075"
---
# <a name="icordebugilcode2getinstrumentedilmap-method"></a>ICorDebugILCode2::GetInstrumentedILMap メソッド
[.NET Framework 4.5.2 以降のバージョンでのみでサポート]  
  
 このインスタンスについて、プロファイラー インストルメント中間言語 (IL: intermediate language) オフセットから、元のメソッドの IL オフセットまでのマップを返します。  
  
## <a name="syntax"></a>構文  
  
```cpp
HRESULT GetInstrumentedILMap(  
   [in] ULONG32 cMap,  
   [out] ULONG32 *pcMap,  
   [out, size_is(cMap), length_is(*pcMap)] COR_IL_MAP map[]  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 cMap  
 [入力] `map` 配列の記憶容量。 詳細については、次の「解説」を参照してください。  
  
 pcMap  
 入出力マップ配列に書き込まれた COR_IL_MAP 値の数。  
  
 map  
 入出力プロファイラーによってインストルメント化された IL から元のメソッドの IL へのマッピングに関する情報を提供する COR_IL_MAP 値の配列。  
  
## <a name="remarks"></a>Remarks  
 プロファイラーが[ICorProfilerInfo:: SetILInstrumentedCodeMap](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilinstrumentedcodemap-method.md)メソッドを呼び出すことによってマッピングを設定した場合、デバッガーはこのメソッドを呼び出してマッピングを取得し、スタックトレースと変数の IL オフセットを計算するときにマッピングを内部的に使用することができます。期間.  
  
 `cMap` が0で `pcMap` が**null**以外の場合、`pcMap` は使用可能な COR_IL_MAP 値の数に設定されます。 `cMap` が 0 以外の場合は、`map` アレイの記憶容量を表します。 メソッドが返された場合、`map` には最大 `cMap` の項目が含まれ、`pcMap` は `map` 配列に実際に書き込まれた COR_IL_MAP 値の数に設定されます。  
  
 IL がインストルメント化されていない、またはプロファイラーによってマッピングが指定されなかった場合、このメソッドは `S_OK` を返し、`pcMap` を 0 に設定します。  
  
## <a name="requirements"></a>［要件］  
 **:** 「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICorProfilerInfo:: SetILInstrumentedCodeMap](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilinstrumentedcodemap-method.md)
- [ICorDebugILCode2 インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode2-interface.md)
- [デバッグ インターフェイス](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
