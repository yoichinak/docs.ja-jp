---
title: ICorProfilerCallback::ThreadAssignedToOSThread メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ThreadAssignedToOSThread
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ThreadAssignedToOSThread
helpviewer_keywords:
- ThreadAssignedToOSThread method [.NET Framework profiling]
- ICorProfilerCallback::ThreadAssignedToOSThread method [.NET Framework profiling]
ms.assetid: f9671e5a-7b14-4f5b-8404-58136422c8b2
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0e955d2fdca67448897ed49b3200542075b4d534
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2019
ms.locfileid: "57466779"
---
# <a name="icorprofilercallbackthreadassignedtoosthread-method"></a>ICorProfilerCallback::ThreadAssignedToOSThread メソッド
特定のオペレーティング システム スレッドを使用して、マネージ スレッドが実装されることをプロファイラーに通知します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT ThreadAssignedToOSThread(  
    [in] ThreadID managedThreadId,  
    [in] DWORD    osThreadId);  
```  
  
## <a name="parameters"></a>パラメーター  
 `managedThreadId`  
 [in]マネージ スレッドの識別子。  
  
 `osThreadId`  
 [in]オペレーティング システム スレッドの識別子。  
  
## <a name="remarks"></a>Remarks  
 `ThreadAssignedToOSThread`コールバックが存在できるように、プロファイラーはマネージ スレッドをオペレーティング システムのスレッドのファイバー間での正確なマッピングを維持することができます。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorProf.idl、CorProf.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目
- [ICorProfilerCallback インターフェイス](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
