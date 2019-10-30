---
title: ICorDebugController::HasQueuedCallbacks メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugController.HasQueuedCallbacks
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugController::HasQueuedCallbacks
helpviewer_keywords:
- HasQueuedCallbacks method [.NET Framework debugging]
- ICorDebugController::HasQueuedCallbacks method [.NET Framework debugging]
ms.assetid: 0d6a1cd9-370b-4462-adbf-e3980e897ea7
topic_type:
- apiref
ms.openlocfilehash: 51ee8b3631bffe9fd7fef4351e0aa67d1cbbe2c9
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/30/2019
ms.locfileid: "73125399"
---
# <a name="icordebugcontrollerhasqueuedcallbacks-method"></a>ICorDebugController::HasQueuedCallbacks メソッド
マネージコールバックが、指定されたスレッドに対して現在キューに登録されているかどうかを示す値を取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT HasQueuedCallbacks (  
    [in] ICorDebugThread *pThread,  
    [out] BOOL           *pbQueued  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `pThread`  
 からスレッドを表す "ツールスレッド" オブジェクトへのポインター。  
  
 `pbQueued`  
 入出力マネージコールバックが、指定されたスレッドに対して現在キューに格納されている場合に `true` される値へのポインター。それ以外の場合は、`false`ます。  
  
 `pThread` パラメーターに null が指定されている場合、現在マネージコールバックが任意のスレッドに対してキューに置かれている場合、`HasQueuedCallbacks` は `true` を返します。  
  
## <a name="remarks"></a>Remarks  
 コールバックは[、次の](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md)ように表示されるたびに1つずつディスパッチされます。 デバッガーでは、同時に発生する複数のデバッグイベントを報告する場合に、このフラグをチェックできます。  
  
 デバッグイベントがキューに登録されている場合は、既に発生しているため、デバッガーはキュー全体をドレインして、デバッグ対象の状態を確認する必要があります。 (`ICorDebugController::Continue` を呼び出してキューをドレインします)。たとえば、キューにスレッド*x*の2つのデバッグイベントが含まれており、デバッガーが最初のデバッグイベントの後にスレッド*x*を中断し、`ICorDebugController::Continue`を呼び出すと、スレッド*x*の2番目のデバッグイベントがディスパッチされますが、スレッドが中断されました。  
  
## <a name="requirements"></a>［要件］  
 **:** 「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目
