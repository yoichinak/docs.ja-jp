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
ms.openlocfilehash: c03be2405e1ab0287a2921b6e2e293862c67a193
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137373"
---
# <a name="icordebugmanagedcallbackdebuggererror-method"></a>ICorDebugManagedCallback::DebuggerError メソッド
共通言語ランタイム (CLR) からのイベントを処理しようとしたときに、エラーが発生したことをデバッガーに通知します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT DebuggerError (  
    [in] ICorDebugProcess *pProcess,  
    [in] HRESULT           errorHR,  
    [in] DWORD             errorCode  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `pProcess`  
 からイベントが発生したプロセスを表す "いいプロセス" オブジェクトへのポインター。  
  
 `errorHR`  
 からイベントハンドラーから返された HRESULT 値。  
  
 `errorCode`  
 からCLR エラーを示す整数です。  
  
## <a name="remarks"></a>Remarks  
 プロセスは、エラーの性質によっては、パススルーモードに配置される場合があります。  
  
 `DebugError` のコールバックは、エラーのためにデバッグサービスが無効になっていることを示します。そのため、デバッガーは、ユーザーがエラーメッセージを使用できるようにする必要があります。 [GetID:](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-getid-method.md) : ICorDebug は安全に呼び出すことができますが、他のすべてのメソッド ( [:: Terminate](../../../../docs/framework/unmanaged-api/debugging/icordebug-terminate-method.md)を含む) は呼び出さないでください。 デバッガーでは、プロセスを終了するためにオペレーティングシステムの機能を使用する必要があります。  
  
## <a name="requirements"></a>［要件］  
 **:** 「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICorDebugManagedCallback インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
