---
title: ICorProfilerInfo8 インターフェイス
ms.date: 08/06/2019
author: davmason
ms.author: davmason
ms.openlocfilehash: 2baa33a7a3527392d8095b5d0ec7ad6af8a71a8e
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70928934"
---
# <a name="icorprofilerinfo8-interface"></a>ICorProfilerInfo8 インターフェイス

動的メソッドに関する情報を照会するメソッドを提供する[ICorProfilerInfo7](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-interface.md)のサブクラス。

## <a name="methods"></a>メソッド  

| メソッド|説明|  
| ------------|-----------------|  
|[IsFunctionDynamic メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo8-isfunctiondynamic-method.md)| 関数にメタデータが関連付けられていないかどうかを判断します。|
|[GetFunctionFromIP3 メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo8-getfunctionfromip3-method.md)| マネージコード命令ポインターを FunctionID にマップします。 このメソッドは、動的メソッドと非動的メソッドの両方に対して機能します。 |
|[GetDynamicFunctionInfo メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo8-getdynamicfunctioninfo-method.md)| 動的メソッドに関する情報を取得します。 |

## <a name="requirements"></a>必要条件  
**・** [システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
**ヘッダー:** Corprof.idl、Corprof.idl  
**.NET Framework のバージョン:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  

## <a name="see-also"></a>関連項目

- [プロファイリングのインターフェイス](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
