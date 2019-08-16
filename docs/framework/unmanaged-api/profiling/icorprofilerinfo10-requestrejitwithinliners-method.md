---
title: ICorProfilerInfo10::RequestReJITWithInliners
ms.date: 08/06/2019
dev_langs:
- cpp
api_name:
- ICorProfilerInfo10.RequestReJITWithInliners
api_location:
- mscorwks.dll
api_type:
- COM
author: davmason
ms.author: davmason
ms.openlocfilehash: 79a1c80f1c7582bd0751c43dea1d35a4d4d1c661
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/13/2019
ms.locfileid: "68973982"
---
# <a name="icorprofilerinfo10requestrejitwithinliners-method"></a>ICorProfilerInfo10:: RequestReJITWithInliners メソッド
  
要求されたメソッドのほか、要求されたメソッドの inliners を再適用します。   
  
## <a name="syntax"></a>構文  
  
```cpp
HRESULT RequestReJITWithInliners( [in]                       DWORD       dwRejitFlags,
                                  [in]                       ULONG       cFunctions,
                                  [in, size_is(cFunctions)]  ModuleID    moduleIds[],
                                  [in, size_is(cFunctions)]  mdMethodDef methodIds[]);
```  
  
#### <a name="parameters"></a>パラメーター  
 
 `dwRejitFlags` \
 から[COR_PRF_REJIT_FLAGS](../../../../docs/framework/unmanaged-api/profiling/cor-prf-rejit-flags-enumeration.md)のビットマスク。
 
 `cFunctions`  
 [in] 再コンパイルする関数の数。  
  
 `moduleIds`  
 [in] 再コンパイルする関数を識別する (`module`、`methodDef`) ペアの `moduleId` の部分を指定します。  
  
 `methodIds`  
 [in] 再コンパイルする関数を識別する (`module`、`methodDef`) ペアの `methodId` の部分を指定します。  

## <a name="remarks"></a>Remarks  
  [RequestReJIT](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-requestrejit-method.md)では、インラインメソッドの追跡は行われません。 プロファイラーは、インライン化されたメソッドのすべてのインスタンス`RequestReJIT`が ReJITted であることを確認するために、インライン展開をブロックするか、インライン展開を追跡し、すべての inliners に対してを呼び出す必要がありました これにより、再インライン化を監視するためのプロファイラーが存在しないため、ReJIT on attach に問題が生じます。 このメソッドを呼び出すことにより、inliners の完全なセットも ReJITted になることを保証できます。  

## <a name="requirements"></a>必要条件  
 **・** 「 [.Net Core でサポートされるオペレーティングシステム](../../../core/windows-prerequisites.md#net-core-supported-operating-systems)」を参照してください。  
  
 **ヘッダー:** Corprof.idl、Corprof.idl  
  
 **ライブラリ**CorGuids .lib  
  
 **.Net のバージョン:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]
  
## <a name="see-also"></a>関連項目
- [ICorProfilerInfo10 インターフェイス](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo10-interface.md)

