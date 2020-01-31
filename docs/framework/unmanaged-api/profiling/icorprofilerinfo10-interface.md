---
title: ICorProfilerInfo10 インターフェイス
ms.date: 08/06/2019
author: davmason
ms.author: davmason
ms.openlocfilehash: e90a1ffbc037636e4296bbd4f4c3c5082885e9f3
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/29/2020
ms.locfileid: "76863245"
---
# <a name="icorprofilerinfo10-interface"></a>ICorProfilerInfo10 インターフェイス

関数 IL の変更、ランタイムからの情報のクエリ、およびランタイムの中断と再開を行うメソッドを提供する[ICorProfilerInfo9](icorprofilerinfo9-interface.md)のサブクラス。

## <a name="methods"></a>メソッド  

| メソッド|説明|  
| ------------|-----------------|  
|[EnumerateObjectReferences メソッド](icorprofilerinfo10-enumerateobjectreferences-method.md)|ObjectID、callback、および clientData を指定すると、各オブジェクト参照 (存在する場合) が列挙されます。 |
|[IsFrozenObject メソッド](icorprofilerinfo10-isfrozenobject-method.md)|ObjectID が指定された場合、オブジェクトが読み取り専用セグメント内にあるかどうかを判断します。 |
|[GetLOHObjectSizeThreshold メソッド](icorprofilerinfo10-getlohobjectsizethreshold-method.md)|構成された LOH しきい値の値を取得します。 |
|[RequestReJITWithInliners メソッド](icorprofilerinfo10-requestrejitwithinliners-method.md)| 要求されたメソッドのほか、要求されたメソッドの inliners を再適用します。  |
|[SuspendRuntime メソッド](icorprofilerinfo10-suspendruntime-method.md)| GC を実行せずにランタイムを中断します。 |
|[ResumeRuntime メソッド](icorprofilerinfo10-resumeruntime-method.md)| GC を実行せずにランタイムを再開します。 |

## <a name="requirements"></a>要件  
**プラットフォーム:** 「 [.Net Core でサポートされるオペレーティングシステム](../../../core/install/dependencies.md?tabs=netcore30&pivots=os-windows)」を参照してください。  
**ヘッダー** : CorProf.idl、CorProf.h  
**.Net のバージョン:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)] 

## <a name="see-also"></a>関連項目

- [プロファイリングのインターフェイス](profiling-interfaces.md)
