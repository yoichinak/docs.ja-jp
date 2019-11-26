---
title: ICorProfilerInfo10::GetLOHObjectSizeThreshold
ms.date: 08/06/2019
dev_langs:
- cpp
api_name:
- ICorProfilerInfo10.GetLOHObjectSizeThreshold
api_location:
- mscorwks.dll
api_type:
- COM
author: davmason
ms.author: davmason
ms.openlocfilehash: 7a38ee4ae74ca5b96dd082e752fc733eb85fca3f
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/23/2019
ms.locfileid: "74427027"
---
# <a name="icorprofilerinfo10getlohobjectsizethreshold-method"></a>ICorProfilerInfo10::GetLOHObjectSizeThreshold Method

Gets the value of the configured large object heap (LOH) threshold.

## <a name="syntax"></a>構文

```cpp
HRESULT GetLOHObjectSizeThreshold( [out] DWORD *pThreshold );
```

#### <a name="parameters"></a>パラメーター

`pThreshold` \
[out] The large object heap threshold in bytes.

## <a name="remarks"></a>Remarks

Objects larger than the large object heap threshold will be allocated on the large object heap. Starting with .NET Core 3.0 the large object heap threshold is configurable, `pThreshold` will contain the active large object heap threshold size in bytes.

## <a name="requirements"></a>［要件］

**Platforms:** See [.NET Core supported operating systems](../../../core/install/dependencies.md?tabs=netcore30&pivots=os-windows).

**ヘッダー** : CorProf.idl、CorProf.h

**ライブラリ:** CorGuids.lib

**.NET Versions:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]

## <a name="see-also"></a>関連項目

- [ICorProfilerInfo10 Interface](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo10-interface.md)
