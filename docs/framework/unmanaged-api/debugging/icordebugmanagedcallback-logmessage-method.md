---
title: ICorDebugManagedCallback::LogMessage メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.LogMessage
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::LogMessage
helpviewer_keywords:
- ICorDebugManagedCallback::LogMessage method [.NET Framework debugging]
- LogMessage method [.NET Framework debugging]
ms.assetid: d218554a-bf42-4d88-833d-ede30de67a53
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cf83124af5ced7bb6458564430ceb319ce7d680a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61995177"
---
# <a name="icordebugmanagedcallbacklogmessage-method"></a>ICorDebugManagedCallback::LogMessage メソッド
共通言語ランタイム (CLR) によって管理されるスレッドがメソッドを呼び出すことをデバッガーに通知、<xref:System.Diagnostics.EventLog>クラスをイベント ログに記録します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT LogMessage (  
    [in] ICorDebugAppDomain  *pAppDomain,  
    [in] ICorDebugThread     *pThread,  
    [in] LONG                 lLevel,  
    [in] WCHAR               *pLogSwitchName,  
    [in] WCHAR               *pMessage  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `pAppDomain`  
 [in]イベントを記録したマネージ スレッドを格納しているアプリケーション ドメインを表す ICorDebugAppDomain オブジェクトへのポインター。  
  
 `pThread`  
 [in]マネージ スレッドを表す ICorDebugThread オブジェクトへのポインター。  
  
 `lLevel`  
 [in]値、 [LoggingLevelEnum](../../../../docs/framework/unmanaged-api/debugging/logginglevelenum-enumeration.md)イベント ログに書き込まれた内容を示すメッセージの重大度レベルを示す列挙体。  
  
 `pLogSwitchName`  
 [in]トレース スイッチの名前へのポインター。  
  
 `pMessage`  
 [in]イベント ログに書き込まれたメッセージへのポインター。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICorDebugManagedCallback インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
