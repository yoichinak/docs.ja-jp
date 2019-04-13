---
title: ICorProfilerCallback3::ProfilerAttachComplete メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback3.ProfilerAttachComplete Method
api_location:
- Mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback3::ProfilerAttachComplete
helpviewer_keywords:
- ProfilerAttachComplete method [.NET Framework profiling]
- ICorProfilerCallback3::ProfilerAttachComplete method [.NET Framework profiling]
ms.assetid: 257d6076-06e0-4d93-bb33-651fbb2b92d7
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6bd3326aa5807bd7f2dd882991d211cbbf873067
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59150411"
---
# <a name="icorprofilercallback3profilerattachcomplete-method"></a>ICorProfilerCallback3::ProfilerAttachComplete メソッド
共通言語ランタイム (CLR)、プロファイラーが呼び出すことができますようになりましたことを示すためにメソッドを呼び出して、 [icorprofilerinfo 3::enumjitedfunctions](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-enumjitedfunctions-method.md)と[icorprofilerinfo 3::enummodules](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-enummodules-method.md)キャッチアップ メソッド。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT ProfilerAttachComplete ();  
```  
  
## <a name="remarks"></a>Remarks  
 `ProfilerAttachComplete`コールバックが後に発行された、 [icorprofilercallback 3::initializeforattach](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback3-initializeforattach-method.md)メソッドが呼び出されます。 これは、次のことを示します。  
  
-   `InitializeForAttach` でプロファイラーによって要求されたコールバックがアクティブ化されました。  
  
-   プロファイラーは、通知されないことを心配せずに、関連付けられた ID でキャッチアップを実行できます。  
  
 CLR はこのコールバックからの戻り値を無視します。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorProf.idl、CorProf.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン: ** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICorProfilerCallback インターフェイス](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [ICorProfilerInfo3 インターフェイス](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)
- [プロファイリングのインターフェイス](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [プロファイル](../../../../docs/framework/unmanaged-api/profiling/index.md)
