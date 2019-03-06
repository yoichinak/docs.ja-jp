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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b107ceec5c9e88117e8ec1f6f94d60debfdf7201
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2019
ms.locfileid: "57500058"
---
# <a name="icordebugcontrollerhasqueuedcallbacks-method"></a>ICorDebugController::HasQueuedCallbacks メソッド
任意のマネージ コールバックが、指定されたスレッドの現在キューに登録するかどうかを示す値を取得します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT HasQueuedCallbacks (  
    [in] ICorDebugThread *pThread,  
    [out] BOOL           *pbQueued  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `pThread`  
 [in]スレッドを表す"ICorDebugThread"オブジェクトへのポインター。  
  
 `pbQueued`  
 [out]ある値へのポインター`true`任意のマネージ コールバックがいると、それ以外の指定したスレッドのキューに置かれた場合は`false`します。  
  
 Null が指定されている場合、`pThread`パラメーター、`HasQueuedCallbacks`戻ります`true`マネージ コールバックのいずれかのスレッド キューに存在している場合。  
  
## <a name="remarks"></a>Remarks  
 コールバックにディスパッチされる 1 つずつ、毎回なります[icordebugcontroller::continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md)が呼び出されます。 デバッガーは、同時に発生する複数のデバッグ イベントを報告する必要がある場合、このフラグを確認できます。  
  
 デバッグ イベントがキューに置かれたときに、既に発生した、ため、デバッガーがデバッグ対象の状態を必ずキュー全体をドレインする必要があります。 (呼び出し`ICorDebugController::Continue`キューをドレインするまでにします)。たとえば、キューには、スレッドで 2 つのデバッグ イベントが含まれている場合*X*、し、デバッガー スレッドを中断します*X*デバッグの最初のイベントと、呼び出しの後に`ICorDebugController::Continue`、2 つ目のデバッグ イベントをスレッド*X*スレッドが中断されたがディスパッチされます。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

