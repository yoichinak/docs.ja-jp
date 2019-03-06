---
title: ICorDebugController::Continue メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugController.Continue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugController::Continue
helpviewer_keywords:
- Continue method [.NET Framework debugging]
- ICorDebugController::Continue method [.NET Framework debugging]
ms.assetid: 8684cd06-ad3e-48ef-832e-15320e1f43a2
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4f448a0383d3ad121cbddb59e13acef46a336261
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2019
ms.locfileid: "57485734"
---
# <a name="icordebugcontrollercontinue-method"></a>ICorDebugController::Continue メソッド
呼び出しの後にマネージ スレッドの実行を再開[Stop メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-stop-method.md)します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT Continue (  
    [in] BOOL fIsOutOfBand  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `fIsOutOfBand`  
 [in]設定`true`帯域外のイベントを引き続き使用する場合がそれに設定`false`します。  
  
## <a name="remarks"></a>Remarks  
 `Continue` 呼び出しの後に、プロセスを続行、`ICorDebugController::Stop`メソッド。  
  
 混合モードのデバッグを行うときに呼び出さない`Continue`帯域外のイベントから続行する場合を除き、Win32 のイベントがスレッドします。  
  
 *帯域内イベント*マネージ イベントまたはデバッガーがプロセスの状態の管理との対話をサポートする通常の非管理対象イベントのいずれかです。 この場合、デバッガーを受け取る、 [icordebugunmanagedcallback::debugevent](../../../../docs/framework/unmanaged-api/debugging/icordebugunmanagedcallback-debugevent-method.md)のコールバックをその`fOutOfBand`パラメーターに設定`false`します。  
  
 *帯域外のイベント*はプロセスの状態の管理との対話にできなくなること、イベントのため、プロセスの停止中に非管理対象のイベントです。 この場合、デバッガーを受け取る、`ICorDebugUnmanagedCallback::DebugEvent`のコールバックをその`fOutOfBand`パラメーターに設定`true`します。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

