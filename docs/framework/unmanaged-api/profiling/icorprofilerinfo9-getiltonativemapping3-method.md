---
title: ICorProfilerInfo9::GetILToNativeMapping3
ms.date: 08/06/2019
dev_langs:
- cpp
api_name:
- ICorProfilerInfo9.GetILToNativeMapping3
api_location:
- mscorwks.dll
api_type:
- COM
author: davmason
ms.author: davmason
ms.openlocfilehash: 46ceef43806fda9956797935c5eeec61f865dc6e
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/13/2019
ms.locfileid: "68973792"
---
# <a name="icorprofilerinfo9getiltonativemapping3-method"></a>ICorProfilerInfo9:: GetILToNativeMapping3 メソッド
  
 ネイティブコードの開始アドレスが指定されている場合、この just-in-time バージョンのコードのネイティブから IL へのマッピング情報を返します。   
  
## <a name="syntax"></a>構文  
  
```cpp
HRESULT GetILToNativeMapping3( [in]  UINT_PTR pNativeCodeStartAddress,
                               [in]  ULONG32 cMap,
                               [out] ULONG32 *pcMap,
                               [out] COR_DEBUG_IL_TO_NATIVE_MAP map[]);
```  
  
#### <a name="parameters"></a>パラメーター  
 `pNativeCodeStartAddress` \
 からネイティブ関数の先頭へのポインター。

 `cMap` \
 [in] `map` 配列の最大サイズ。 

 `pcMap` \
 入出力使用できる COR_DEBUG_IL_TO_NATIVE_MAP 構造体の合計数。

 `map` \
 入出力[COR_DEBUG_IL_TO_NATIVE_MAP](../debugging/cor-debug-il-to-native-map-structure.md)構造体の配列。それぞれがオフセットを指定します。 `GetILToNativeMapping3` メソッドから制御が戻ると、`COR_DEBUG_IL_TO_NATIVE_MAP` 構造体の一部または全部が `map` に格納されます。

## <a name="remarks"></a>Remarks  
 階層化コンパイルが有効になっている場合、メソッドは複数のネイティブコード本体を持つことができます。 [ICorProfilerInfo9:: GetNativeCodeStartAddresses](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo9-getnativecodestartaddresses-method.md)は、すべてのネイティブコード本体の開始アドレスを返します。

## <a name="requirements"></a>必要条件  
 **・** 「 [.Net Core でサポートされるオペレーティングシステム](../../../core/windows-prerequisites.md#net-core-supported-operating-systems)」を参照してください。  
  
 **ヘッダー:** Corprof.idl、Corprof.idl  
  
 **ライブラリ**CorGuids .lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_core_22](../../../../includes/net-core-22-md.md)] 
  
## <a name="see-also"></a>関連項目
- [ICorProfilerInfo9 インターフェイス](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo9-interface.md)

