---
title: ICorDebugThread インターフェイス
ms.date: 03/30/2017
api_name:
- ICorDebugThread
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread
helpviewer_keywords:
- ICorDebugThread interface [.NET Framework debugging]
ms.assetid: 3930fd9b-2bc3-4b72-80a0-b6eeb94d60c6
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9f2223230b18f175427bfbfeaa46bf1406d8c7e5
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/28/2019
ms.locfileid: "56976357"
---
# <a name="icordebugthread-interface"></a>ICorDebugThread インターフェイス
プロセス内のスレッドを表します。 
  `ICorDebugThread` インスタンスの有効期間は、それが表しているスレッドの有効期間と同じです。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[ClearCurrentException メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-clearcurrentexception-method.md)|このメソッドは実装されていません。 使用しないでください。|  
|[CreateEval メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-createeval-method.md)|これで動作する ICorDebugEval オブジェクトを作成`ICorDebugThread`です。|  
|[CreateStepper メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-createstepper-method.md)|これで、アクティブなフレームをステップ実行できるようにする ICorDebugStepper オブジェクトを作成します。`ICorDebugThread`します。|  
|[EnumerateChains メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-enumeratechains-method.md)|これですべてのスタック チェーンを含む ICorDebugChainEnum 列挙子へのインターフェイス ポインターを取得`ICorDebugThread`します。|  
|[GetActiveChain メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getactivechain-method.md)|これで active ICorDebugChain へのインターフェイス ポインターを取得`ICorDebugThread`します。|  
|[GetActiveFrame メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getactiveframe-method.md)|これで active ICorDebugFrame へのインターフェイス ポインターを取得`ICorDebugThread`します。|  
|[GetAppDomain メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getappdomain-method.md)|このアプリケーション ドメインへのインターフェイス ポインターを取得`ICorDebugThread`現在実行しています。|  
|[GetCurrentException メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getcurrentexception-method.md)|現在、マネージ コードによってスローされる例外を表す ICorDebugValue オブジェクトへのインターフェイス ポインターを取得します。|  
|[GetDebugState メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getdebugstate-method.md)|この現在のデバッグ状態を説明する CorDebugThreadState 値を取得`ICorDebugThread`します。|  
|[GetHandle メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-gethandle-method.md)|このアクティブな部分の現在のハンドルを取得`ICorDebugThread`します。|  
|[GetID メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getid-method.md)|このアクティブな部分の現在のオペレーティング システムの識別子を取得`ICorDebugThread`します。|  
|[GetObject メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getobject-method.md)|共通言語ランタイム (CLR) スレッドにインターフェイス ポインターを取得します。|  
|[GetProcess メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getprocess-method.md)|このプロセスにインターフェイス ポインターを取得`ICorDebugThread`一部を形成します。|  
|[GetRegisterSet メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getregisterset-method.md)|これに関連付けられている登録のセットにインターフェイス ポインターを取得`ICorDebugThread`します。|  
|[GetUserState メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getuserstate-method.md)|この現在の状態を記述する CorDebugUserState 値のビットごとの組み合わせを取得`ICorDebugThread`します。|  
|[SetDebugState メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-setdebugstate-method.md)|ビットごとの組み合わせを設定`CorDebugThreadState`このデバッグ状態を記述する値`ICorDebugThread`します。|  
  
## <a name="remarks"></a>Remarks  
  
> [!NOTE]
>  このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目
- [デバッグ インターフェイス](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
