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
ms.openlocfilehash: dfce86e95ba41a65e72524546072244a47f8360c
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/23/2019
ms.locfileid: "74442930"
---
# <a name="icorprofilerinfo4getiltonativemapping2-method"></a>ICorProfilerInfo4::GetILToNativeMapping2 メソッド
Microsoft Intermediate Language (MSIL) オフセットから、指定した関数の JIT 再コンパイル バージョンに含まれるコードのネイティブ オフセットへのマップを取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
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
 [in] JIT 再コンパイルされた関数のID。 The identity must be zero in the .NET Framework 4.5.  
  
 `cMap`  
 [in] `map` 配列の最大サイズ。  
  
 `pcMap`  
 [out] The total number of available COR_DEBUG_IL_TO_NATIVE_MAP structures.  
  
 `map`  
 [out] `COR_DEBUG_IL_TO_NATIVE_MAP` 構造体の配列。各構造体はオフセットを指定します。 `GetILToNativeMapping2` メソッドから制御が戻ると、`COR_DEBUG_IL_TO_NATIVE_MAP` 構造体の一部または全部が `map` に格納されます。  
  
## <a name="remarks"></a>Remarks  
 `GetILToNativeMapping2` is similar to the [ICorProfilerInfo::GetILToNativeMapping](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getiltonativemapping-method.md) method, except that it will allow the profiler to specify the ID of the recompiled function in future releases.  
  
> [!NOTE]
> The [ICorProfilerFunctionControl::SetILInstrumentedCodeMap](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-setilinstrumentedcodemap-method.md) method is not implemented in the .NET Framework 4.5, so functions that have been JIT-recompiled cannot have an IL-to-native mapping that differs from the originally compiled function. As such, `GetILToNativeMapping2` cannot be called with a nonzero JIT-recompiled ID in the .NET Framework 4.5.  
  
 `GetILToNativeMapping2` メソッドは、`COR_DEBUG_IL_TO_NATIVE_MAP` 構造体の配列を返します。 To convey that certain ranges of native instructions correspond to special regions of code (for example, the prolog), an entry in the array can have its `ilOffset` field set to a value of the [CorDebugIlToNativeMappingTypes](../../../../docs/framework/unmanaged-api/debugging/cordebugiltonativemappingtypes-enumeration.md) enumeration.  
  
 `GetILToNativeMapping2` から制御が戻ったら、`map` バッファーのサイズが十分で、すべての `COR_DEBUG_IL_TO_NATIVE_MAP` 構造体を格納できたかどうかを確認する必要があります。 これを行うには、`cMap` の値を `pcMap` パラメーターの値と比較します。 `pcMap` 値 に `COR_DEBUG_IL_TO_NATIVE_MAP` 構造体のサイズを乗算した結果が `cMap` より大きい場合は、`map` バッファーの割り当てを増やし、`cMap` を新しい大きいサイズに更新した後、`GetILToNativeMapping2` を再度呼び出します。  
  
 別の方法として、最初に `GetILToNativeMapping2` を長さゼロの `map` バッファーで呼び出して、適切なバッファーのサイズを取得します。 その後、バッファーのサイズを `pcMap` で返された値に設定し、`GetILToNativeMapping2` を再度呼び出します。  
  
## <a name="requirements"></a>［要件］  
 **:** 「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー** : CorProf.idl、CorProf.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [GetILToNativeMapping メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getiltonativemapping-method.md)
- [ICorProfilerInfo4 インターフェイス](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)
- [プロファイリングのインターフェイス](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [プロファイル](../../../../docs/framework/unmanaged-api/profiling/index.md)
