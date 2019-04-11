---
title: ICorDebugController インターフェイス
ms.date: 03/30/2017
api_name:
- ICorDebugController
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugController
helpviewer_keywords:
- ICorDebugController interface [.NET Framework debugging]
ms.assetid: dbb1c4dc-269a-459b-ab1d-6c70788782ce
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7628aa0ad10398f92d475c4c776810e13fac22b7
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59107550"
---
# <a name="icordebugcontroller-interface"></a>ICorDebugController インターフェイス

コードの実行コンテキストを制御できる <xref:System.Diagnostics.Process> または <xref:System.AppDomain> のスコープを表します。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|`ICorDebugController::CanCommitChanges`|このメソッドは、互換性のために残されています。|  
|`ICorDebugController::CommitChanges`|このメソッドは、互換性のために残されています。|  
|[Continue メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md)|呼び出しの後にマネージ スレッドの実行を再開[icordebugcontroller::stop](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-stop-method.md)します。|  
|[Detach メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-detach-method.md)|プロセスまたはアプリケーション ドメインからデバッガーをデタッチします。|  
|[EnumerateThreads メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-enumeratethreads-method.md)|プロセスのアクティブなマネージ スレッドの列挙子を取得します。|  
|[HasQueuedCallbacks メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-hasqueuedcallbacks-method.md)|任意のマネージ コールバックが、指定されたスレッドの現在キューに登録するかどうかを示す値を取得します。|  
|[IsRunning メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-isrunning-method.md)|プロセスのスレッドが自由に実行して現在かどうかを示す値を取得します。|  
|[SetAllThreadsDebugState メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-setallthreadsdebugstate-method.md)|プロセス内のすべてのマネージ スレッドのデバッグ状態を設定します。|  
|[Stop メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-stop-method.md)|プロセスでマネージ コードを実行しているすべてのスレッドを協調停止を実行します。|  
|[Terminate メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-terminate-method.md)|指定した終了コードを使用して、プロセスを終了します。|  
  
## <a name="remarks"></a>Remarks  
 場合`ICorDebugController`はプロセスを制御するには、スコープには、プロセスのすべてのスレッドが含まれます。 場合`ICorDebugController`がアプリケーション ドメインを制御するには、スコープにはその特定のアプリケーション ドメインのスレッドのみが含まれます。  
  
> [!NOTE]
>  このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン: ** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [デバッグのインターフェイス](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
