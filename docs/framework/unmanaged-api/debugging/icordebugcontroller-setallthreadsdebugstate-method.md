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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9348652129a3357784654006dc16d822298f28f8
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/10/2019
ms.locfileid: "67749963"
---
# <a name="icordebugcontrollersetallthreadsdebugstate-method"></a>ICorDebugController::SetAllThreadsDebugState メソッド
プロセス内のすべてのマネージ スレッドのデバッグ状態を設定します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT SetAllThreadsDebugState (  
    [in] CorDebugThreadState  state,  
    [in] ICorDebugThread      *pExceptThisThread  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `state`  
 [in]デバッグのスレッドの状態を指定する"CorDebugThreadState"列挙型の値。  
  
 `pExceptThisThread`  
 [in]デバッグの状態設定から除外するスレッドを表す"ICorDebugThread"オブジェクトへのポインター。 この値が null の場合は、反映されないスレッドはありません。  
  
## <a name="remarks"></a>Remarks  
 `SetAllThreadsDebugState`メソッドを使用して表示されていないスレッドに影響する可能性[EnumerateThreads メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-enumeratethreads-method.md)、そのスレッドで中断された、`SetAllThreadsDebugState`メソッドを再開する必要があります、`SetAllThreadsDebugState`メソッド。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:** [システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目
