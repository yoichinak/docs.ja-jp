---
title: ICorProfilerInfo4::GetILToNativeMapping2 メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo4.GetILToNativeMapping2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo4::GetILToNativeMapping2
helpviewer_keywords:
- ICorProfilerInfo4::GetILToNativeMapping2 method [.NET Framework profiling]
- GetILToNativeMapping2 method, ICorProfilerInfo4 interface [.NET Framework profiling]
ms.assetid: 756c1c25-08a7-4060-9798-dbeaa2f3bee5
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f7124aadc9c848ee2656473b7e06c3bc9b7881a2
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2019
ms.locfileid: "57469334"
---
# <a name="icorprofilerinfo4getiltonativemapping2-method"></a>ICorProfilerInfo4::GetILToNativeMapping2 メソッド
Microsoft Intermediate Language (MSIL) オフセットから、指定した関数の JIT 再コンパイル バージョンに含まれるコードのネイティブ オフセットへのマップを取得します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT GetILToNativeMapping(  
    [in] FunctionID functionId,  
    [in] ReJITID reJitId,  
    [in] ULONG32 cMap,  
    [out] ULONG32 *pcMap,  
    [out, size_is(cMap), length_is(*pcMap)]  
        COR_DEBUG_IL_TO_NATIVE_MAP map[]);  
```  
  
## <a name="parameters"></a>パラメーター  
 `functionId`  
 [in] コードを含む関数の ID。  
  
 `pReJitId`  
 [in] JIT 再コンパイルされた関数のID。 
  [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)] ではこの ID はゼロでなければなりません。  
  
 `cMap`  
 [in] `map` 配列の最大サイズ。  
  
 `pcMap`  
 [out]使用可能な COR_DEBUG_IL_TO_NATIVE_MAP 構造体の合計数。  
  
 `map`  
 [out] `COR_DEBUG_IL_TO_NATIVE_MAP` 構造体の配列。各構造体はオフセットを指定します。 
  `GetILToNativeMapping2` メソッドから制御が戻ると、`COR_DEBUG_IL_TO_NATIVE_MAP` 構造体の一部または全部が `map` に格納されます。  
  
## <a name="remarks"></a>Remarks  
 `GetILToNativeMapping2` ような[icorprofilerinfo::getiltonativemapping](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getiltonativemapping-method.md)メソッド、プロファイラーが後で再コンパイルされた関数の ID を指定することができますが、解放します。  
  
> [!NOTE]
>  [Icorprofilerfunctioncontrol::setilinstrumentedcodemap](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-setilinstrumentedcodemap-method.md)でメソッドが実装されていません、 [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)]JIT 再コンパイルされている関数とは異なる IL からネイティブへのマッピングを含めることはできませんので、もともと関数をコンパイルします。 このため `GetILToNativeMapping2` は、[!INCLUDE[net_v45](../../../../includes/net-v45-md.md)] でゼロ以外の JIT 再コンパイル済み ID を使用して呼び出すことはできません。  
  
 
  `GetILToNativeMapping2` メソッドは、`COR_DEBUG_IL_TO_NATIVE_MAP` 構造体の配列を返します。 ネイティブ命令の特定の範囲がコード (たとえば、プロローグ) の特殊なリージョンに対応することを伝える、配列内のエントリを持つことができます、`ilOffset`フィールドの値に設定、 [CorDebugIlToNativeMappingTypes](../../../../docs/framework/unmanaged-api/debugging/cordebugiltonativemappingtypes-enumeration.md)列挙体です。  
  
 
  `GetILToNativeMapping2` から制御が戻ったら、`map` バッファーのサイズが十分で、すべての `COR_DEBUG_IL_TO_NATIVE_MAP` 構造体を格納できたかどうかを確認する必要があります。 これを行うには、`cMap` の値を `pcMap` パラメーターの値と比較します。 `pcMap` 値 に `COR_DEBUG_IL_TO_NATIVE_MAP` 構造体のサイズを乗算した結果が `cMap` より大きい場合は、`map` バッファーの割り当てを増やし、`cMap` を新しい大きいサイズに更新した後、`GetILToNativeMapping2` を再度呼び出します。  
  
 別の方法として、最初に `GetILToNativeMapping2` を長さゼロの `map` バッファーで呼び出して、適切なバッファーのサイズを取得します。 その後、バッファーのサイズを `pcMap` で返された値に設定し、`GetILToNativeMapping2` を再度呼び出します。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorProf.idl、CorProf.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>関連項目
- [GetILToNativeMapping メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getiltonativemapping-method.md)
- [ICorProfilerInfo4 インターフェイス](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)
- [プロファイリングのインターフェイス](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [プロファイル](../../../../docs/framework/unmanaged-api/profiling/index.md)
