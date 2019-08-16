---
title: ICorProfilerInfo10::IsFrozenObject
ms.date: 08/06/2019
dev_langs:
- cpp
api_name:
- ICorProfilerInfo10.IsFrozenObject
api_location:
- mscorwks.dll
api_type:
- COM
author: davmason
ms.author: davmason
ms.openlocfilehash: 05f25d8fb61a16f41a82a987529017db6a687740
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/13/2019
ms.locfileid: "68973992"
---
# <a name="icorprofilerinfo10isfrozenobject-method"></a>ICorProfilerInfo10:: IsFrozenObject メソッド
  
 ObjectID が指定された場合、オブジェクトが読み取り専用セグメント内にあるかどうかを判断します。   
  
## <a name="syntax"></a>構文  
  
```cpp
HRESULT IsFrozenObject( [in]  ObjectID objectId,
                        [out] BOOL *pbFrozen);
```  
  
#### <a name="parameters"></a>パラメーター  
 
 `objectId` \
 から調べるオブジェクト。

 `pbFrozen` \
 入出力オブジェクトが読み取り専用セグメント内にあるかどうかを示すです。`BOOL`

## <a name="requirements"></a>必要条件  
 **・** 「 [.Net Core でサポートされるオペレーティングシステム](../../../core/windows-prerequisites.md#net-core-supported-operating-systems)」を参照してください。  
  
 **ヘッダー:** Corprof.idl、Corprof.idl  
  
 **ライブラリ**CorGuids .lib  
  
 **.Net のバージョン:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)] 
  
## <a name="see-also"></a>関連項目
- [ICorProfilerInfo10 インターフェイス](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo10-interface.md)

