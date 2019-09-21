---
title: ICorProfilerInfo10 インターフェイス
ms.date: 08/06/2019
author: davmason
ms.author: davmason
ms.openlocfilehash: 06cce79fbb2b2eb143e77e3c6fda194e47d4f4f3
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70928800"
---
# <a name="icorprofilerinfo10-interface"></a>ICorProfilerInfo10 インターフェイス

関数 IL の変更、ランタイムからの情報のクエリ、およびランタイムの中断と再開を行うメソッドを提供する[ICorProfilerInfo9](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo9-interface.md)のサブクラス。

## <a name="methods"></a>メソッド  

| メソッド|説明|  
| ------------|-----------------|  
|[EnumerateObjectReferences メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo10-enumerateobjectreferences-method.md)|ObjectID、callback、および clientData を指定すると、各オブジェクト参照 (存在する場合) が列挙されます。 |
|[IsFrozenObject メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo10-isfrozenobject-method.md)|ObjectID が指定された場合、オブジェクトが読み取り専用セグメント内にあるかどうかを判断します。 |
|[GetLOHObjectSizeThreshold メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo10-getlohobjectsizethreshold-method.md)|構成された LOH しきい値の値を取得します。 |
|[RequestReJITWithInliners メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo10-requestrejitwithinliners-method.md)| 要求されたメソッドのほか、要求されたメソッドの inliners を再適用します。  |
|[SuspendRuntime メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo10-suspendruntime-method.md)| GC を実行せずにランタイムを中断します。 |
|[ResumeRuntime メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo10-resumeruntime-method.md)| GC を実行せずにランタイムを再開します。 |

## <a name="requirements"></a>必要条件  
**・** 「 [.Net Core でサポートされるオペレーティングシステム](../../../core/windows-prerequisites.md#net-core-supported-operating-systems)」を参照してください。  
**ヘッダー:** Corprof.idl、Corprof.idl  
**.Net のバージョン:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)] 

## <a name="see-also"></a>関連項目

- [プロファイリングのインターフェイス](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
