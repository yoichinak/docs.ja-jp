---
title: ICorDebugController::SetAllThreadsDebugState メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugController.SetAllThreadsDebugState
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugController::SetAllThreadsDebugState
helpviewer_keywords:
- SetAllThreadsDebugState method [.NET Framework debugging]
- ICorDebugController::SetAllThreadsDebugState method [.NET Framework debugging]
ms.assetid: bdda4bd7-4743-4d58-a22b-8067e967db95
topic_type:
- apiref
ms.openlocfilehash: 1190f83e2671216cf1627eeb710ba576e4b2ec93
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/30/2019
ms.locfileid: "73125355"
---
# <a name="icordebugcontrollersetallthreadsdebugstate-method"></a>ICorDebugController::SetAllThreadsDebugState メソッド
プロセス内のすべてのマネージスレッドのデバッグ状態を設定します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT SetAllThreadsDebugState (  
    [in] CorDebugThreadState  state,  
    [in] ICorDebugThread      *pExceptThisThread  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `state`  
 からデバッグ用のスレッドの状態を指定する "CorDebugThreadState" 列挙の値。  
  
 `pExceptThisThread`  
 からデバッグ状態設定から除外されるスレッドを表す "のスレッド" オブジェクトへのポインター。 この値が null の場合、スレッドは除外されません。  
  
## <a name="remarks"></a>Remarks  
 `SetAllThreadsDebugState` メソッドは、 [EnumerateThreads メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-enumeratethreads-method.md)によって表示されないスレッドに影響を与える可能性があります。そのため、`SetAllThreadsDebugState` メソッドで中断されたスレッドは、`SetAllThreadsDebugState` メソッドを使用して再開する必要があります。  
  
## <a name="requirements"></a>［要件］  
 **:** 「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目
