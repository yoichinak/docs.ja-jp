---
title: ICorDebugProcess インターフェイス
ms.date: 03/30/2017
api_name:
- ICorDebugProcess
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess
helpviewer_keywords:
- ICorDebugProcess interface [.NET Framework debugging]
ms.assetid: be86f4b5-418a-4c5c-a67c-97148c65ed8c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7dc732a8e3419a7ca42f5180d1bd32128ec33417
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/28/2019
ms.locfileid: "56967517"
---
# <a name="icordebugprocess-interface"></a>ICorDebugProcess インターフェイス
マネージド コードを実行しているプロセスを表します。 このインターフェイスは、ICorDebugController のサブクラスです。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[ClearCurrentException メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-clearcurrentexception-method.md)|特定のスレッドで現在管理されていない例外をクリアします。|  
|[EnableLogMessages メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-enablelogmessages-method.md)|有効にし、デバッガーへのログ メッセージの送信を無効にします。|  
|[EnumerateAppDomains メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-enumerateappdomains-method.md)|すべてのプロセスのアプリケーション ドメインを列挙します。|  
|[EnumerateObjects メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-enumerateobjects-method.md)|実装されていません。|  
|[GetHandle メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-gethandle-method.md)|プロセスを識別するハンドルを取得します。|  
|[GetHelperThreadID メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-gethelperthreadid-method.md)|デバッガーの内部ヘルパーのスレッドのオペレーティング システム (OS) のスレッド ID を取得します。|  
|[GetID メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-getid-method.md)|プロセスのオペレーティング システム (OS) の ID を取得します。|  
|[GetObject メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-getobject-method.md)|実装されていません。|  
|[GetThread メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-getthread-method.md)|取得しますが、指定された OS スレッドをある ICorDebugThread インスタンスの id。|  
|[GetThreadContext メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-getthreadcontext-method.md)|特定のスレッドのコンテキストを取得します。|  
|[IsOSSuspended メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-isossuspended-method.md)|デバッガーがプロセスを停止したため、スレッドが中断されたかどうかを判断します。|  
|[IsTransitionStub メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-istransitionstub-method.md)|マネージ コードへの遷移を発生させるスタブ内にアドレスがあるかどうかを判断します。|  
|[ModifyLogSwitch メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-modifylogswitch-method.md)|指定したログ スイッチの重大度レベルを設定します。|  
|[ReadMemory メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-readmemory-method.md)|プロセスからメモリを読み取ります。|  
|[SetThreadContext メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-setthreadcontext-method.md)|特定のスレッドのコンテキストを設定します。|  
|[ThreadForFiberCookie メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-threadforfibercookie-method.md)|非推奨。|  
|[WriteMemory メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-writememory-method.md)|プロセスのメモリの領域にデータを書き込みます。|  
  
## <a name="remarks"></a>Remarks  
  
> [!NOTE]
>  このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目
- [ICorDebug インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
- [デバッグ インターフェイス](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
