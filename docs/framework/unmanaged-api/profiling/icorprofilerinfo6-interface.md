---
title: ICorProfilerInfo6 インターフェイス
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo6
api_location:
- mscorwks.dll
api_type:
- COM
ms.assetid: 6f2bb148-1e2b-4e45-a5a5-0ceddc40064b
ms.openlocfilehash: b1d31012662964132f8b65f030a062ae39ded56e
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/30/2019
ms.locfileid: "73130363"
---
# <a name="icorprofilerinfo6-interface"></a>ICorProfilerInfo6 インターフェイス
[.NET Framework 4.6 以降のバージョンでサポートされています]  
  
 特定の NGen モジュールで定義され、特定のメソッドにインラインで定義されているすべてのメソッドの列挙子を提供する[ICorProfilerInfo5](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-interface.md)のサブクラス。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[ICorProfilerInfo6::EnumNgenModuleMethodsInliningThisMethod メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo6-enumngenmodulemethodsinliningthismethod-method.md)|特定の NGen モジュールに属し、特定のメソッドの本体にインライン化されているすべてのメソッドの列挙子を返します。|  
  
## <a name="requirements"></a>［要件］  
 **:** 「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー** : CorProf.idl、CorProf.h  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [プロファイリングのインターフェイス](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
