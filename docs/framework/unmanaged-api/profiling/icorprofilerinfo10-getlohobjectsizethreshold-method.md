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
ms.openlocfilehash: 8c9a85e9f00027f597795eea55a9bbb0364790f8
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/21/2019
ms.locfileid: "69661237"
---
# <a name="icorprofilerinfo10getlohobjectsizethreshold-method"></a>ICorProfilerInfo10:: GetLOHObjectSizeThreshold メソッド

構成されたラージオブジェクトヒープ (LOH) のしきい値の値を取得します。

## <a name="syntax"></a>構文

```cpp
HRESULT GetLOHObjectSizeThreshold( [out] DWORD *pThreshold );
```

#### <a name="parameters"></a>パラメーター

`pThreshold` \
入出力ラージオブジェクトヒープのしきい値 (バイト単位)。

## <a name="remarks"></a>Remarks

大きなオブジェクトヒープのしきい値より大きいオブジェクトは、大きなオブジェクトヒープに割り当てられます。 .Net Core 3.0 以降では、大きなオブジェクトヒープのしきい値`pThreshold`は構成可能で、アクティブなラージオブジェクトヒープのしきい値のサイズはバイト単位で格納されます。

## <a name="requirements"></a>必要条件

**・** 「 [.Net Core でサポートされるオペレーティングシステム](../../../core/windows-prerequisites.md#net-core-supported-operating-systems)」を参照してください。

**ヘッダー:** Corprof.idl、Corprof.idl

**ライブラリ**CorGuids .lib

**.Net のバージョン:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]

## <a name="see-also"></a>関連項目

- [ICorProfilerInfo10 インターフェイス](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo10-interface.md)
