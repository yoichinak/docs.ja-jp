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
ms.openlocfilehash: 1a5a259e6604d906e55166b3fcb770bc37d346c5
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/23/2019
ms.locfileid: "74444736"
---
# <a name="icorprofilerinfo9getiltonativemapping3-method"></a>ICorProfilerInfo9::GetILToNativeMapping3 Method

Given the native code start address, returns the native to IL mapping information for this jitted version of the code.

## <a name="syntax"></a>構文

```cpp
HRESULT GetILToNativeMapping3( [in]  UINT_PTR pNativeCodeStartAddress,
                               [in]  ULONG32 cMap,
                               [out] ULONG32 *pcMap,
                               [out] COR_DEBUG_IL_TO_NATIVE_MAP map[]);
```

#### <a name="parameters"></a>パラメーター

`pNativeCodeStartAddress` \
[in] A pointer to the start of a native function.

`cMap` \
[in] `map` 配列の最大サイズ。

`pcMap` \
[out] The total number of available COR_DEBUG_IL_TO_NATIVE_MAP structures.

`map` \
[out] An array of [COR_DEBUG_IL_TO_NATIVE_MAP](../debugging/cor-debug-il-to-native-map-structure.md) structures, each of which specifies the offsets. `GetILToNativeMapping3` メソッドから制御が戻ると、`COR_DEBUG_IL_TO_NATIVE_MAP` 構造体の一部または全部が `map` に格納されます。

## <a name="remarks"></a>Remarks

When tiered compilation is enabled, a method may have more than one native code body. [ICorProfilerInfo9::GetNativeCodeStartAddresses](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo9-getnativecodestartaddresses-method.md) will return the start addresses for all of the native code bodies.

## <a name="requirements"></a>［要件］

**Platforms:** See [.NET Core supported operating systems](../../../core/install/dependencies.md?tabs=netcore30&pivots=os-windows).

**ヘッダー** : CorProf.idl、CorProf.h

**ライブラリ:** CorGuids.lib

**.NET Framework のバージョン:** [!INCLUDE[net_core_22](../../../../includes/net-core-22-md.md)]

## <a name="see-also"></a>関連項目

- [ICorProfilerInfo9 Interface](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo9-interface.md)
