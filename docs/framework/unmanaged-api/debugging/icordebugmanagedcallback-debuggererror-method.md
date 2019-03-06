---
title: ICorDebugManagedCallback::DebuggerError メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.DebuggerError
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::DebuggerError
helpviewer_keywords:
- DebuggerError method [.NET Framework debugging]
- ICorDebugManagedCallback::DebuggerError method [.NET Framework debugging]
ms.assetid: 9e983d11-eaf3-4741-b936-29ec456384a3
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 25af2c8fa3e3d49b3c2832a69f14b2691585d775
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2019
ms.locfileid: "57489849"
---
# <a name="icordebugmanagedcallbackdebuggererror-method"></a>ICorDebugManagedCallback::DebuggerError メソッド
共通言語ランタイム (CLR) からのイベントの処理を試行中にエラーが発生したことをデバッガーに通知します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT DebuggerError (  
    [in] ICorDebugProcess *pProcess,  
    [in] HRESULT           errorHR,  
    [in] DWORD             errorCode  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `pProcess`  
 [in]イベントが発生したプロセスを表す"ICorDebugProcess"オブジェクトへのポインター。  
  
 `errorHR`  
 [in]イベント ハンドラーから返された HRESULT 値。  
  
 `errorCode`  
 [in]CLR エラーを示す整数。  
  
## <a name="remarks"></a>Remarks  
 プロセスは、パススルー モードでは、エラーの性質によってに配置することがあります。  
  
 `DebugError`コールバックでは、デバッグ サービスが無効である、エラーのため、デバッガーは、エラー メッセージを使用できるように、ユーザーを示します。 [Icordebugprocess::getid](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-getid-method.md)など、他のすべてのメソッド呼び出しになれる[icordebug::terminate](../../../../docs/framework/unmanaged-api/debugging/icordebug-terminate-method.md)、呼び出すことはできません。 デバッガーは、プロセスを終了するためにオペレーティング システムの機能を使用します。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目
- [ICorDebugManagedCallback インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
