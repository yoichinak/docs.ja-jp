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
ms.openlocfilehash: d4d498c1d75625b2abc37dc1f4c88d73b58ec675
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790028"
---
# <a name="icorprofilerinfo10getlohobjectsizethreshold-method"></a>ICorProfilerInfo10:: GetLOHObjectSizeThreshold メソッド

構成されたラージオブジェクトヒープ (LOH) のしきい値の値を取得します。

## <a name="syntax"></a>構文

```cpp
HRESULT GetLOHObjectSizeThreshold( [out] DWORD *pThreshold );
```

## <a name="parameters"></a>パラメーター

- `pThreshold`

  \[out] 大きなオブジェクトヒープのしきい値 (バイト単位)。

## <a name="remarks"></a>コメント

大きなオブジェクトヒープのしきい値より大きいオブジェクトは、大きなオブジェクトヒープに割り当てられます。 .NET Core 3.0 以降では、大きなオブジェクトヒープのしきい値は構成可能で、`pThreshold` にはアクティブな大きなオブジェクトヒープのしきい値サイズ (バイト単位) が含まれます。

## <a name="requirements"></a>要件

**プラットフォーム:** 「 [.Net Core でサポートされるオペレーティングシステム](../../../core/install/dependencies.md?tabs=netcore30&pivots=os-windows)」を参照してください。

**ヘッダー** : CorProf.idl、CorProf.h

**ライブラリ:** CorGuids.lib

**.Net のバージョン:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]

## <a name="see-also"></a>関連項目

- [ICorProfilerInfo10 インターフェイス](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo10-interface.md)
