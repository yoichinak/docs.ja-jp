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
ms.openlocfilehash: d6b6575cf04635b40b504b11bc415f61f05b4205
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/13/2019
ms.locfileid: "68974022"
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

