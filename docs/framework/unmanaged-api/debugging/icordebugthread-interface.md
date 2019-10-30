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
ms.openlocfilehash: c7333f4210d0a2ec4ff71a0fac0ea00068fecc57
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133498"
---
# <a name="icordebugthread-interface"></a>ICorDebugThread インターフェイス
プロセス内のスレッドを表します。 `ICorDebugThread` インスタンスの有効期間は、それが表しているスレッドの有効期間と同じです。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[ClearCurrentException メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-clearcurrentexception-method.md)|このメソッドは実装されていません。 使用しないでください。|  
|[CreateEval メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-createeval-method.md)|この `ICorDebugThread`を操作する、のオブジェクトを作成します。|  
|[CreateStepper メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-createstepper-method.md)|この `ICorDebugThread`内のアクティブなフレームをステップ実行できるようにする、ICorDebugStepper オブジェクトを作成します。|  
|[EnumerateChains メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-enumeratechains-method.md)|この `ICorDebugThread`内のすべてのスタックチェーンを格納している ICorDebugChainEnum 列挙子へのインターフェイスポインターを取得します。|  
|[GetActiveChain メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getactivechain-method.md)|この `ICorDebugThread`上のアクティブなについてのオブジェクトチェーンへのインターフェイスポインターを取得します。|  
|[GetActiveFrame メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getactiveframe-method.md)|この `ICorDebugThread`のアクティブなテキストフレームへのインターフェイスポインターを取得します。|  
|[GetAppDomain メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getappdomain-method.md)|この `ICorDebugThread` が現在実行されているアプリケーションドメインへのインターフェイスポインターを取得します。|  
|[GetCurrentException メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getcurrentexception-method.md)|現在マネージコードによってスローされている例外を表す、ICorDebugValue オブジェクトへのインターフェイスポインターを取得します。|  
|[GetDebugState メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getdebugstate-method.md)|この `ICorDebugThread`の現在のデバッグ状態を示す CorDebugThreadState 値を取得します。|  
|[GetHandle メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-gethandle-method.md)|この `ICorDebugThread`のアクティブな部分の現在のハンドルを取得します。|  
|[GetID メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getid-method.md)|この `ICorDebugThread`のアクティブな部分の現在のオペレーティングシステム識別子を取得します。|  
|[GetObject メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getobject-method.md)|共通言語ランタイム (CLR) スレッドへのインターフェイスポインターを取得します。|  
|[GetProcess メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getprocess-method.md)|この `ICorDebugThread` がパートを形成するプロセスへのインターフェイスポインターを取得します。|  
|[GetRegisterSet メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getregisterset-method.md)|この `ICorDebugThread`に関連付けられているレジスタセットへのインターフェイスポインターを取得します。|  
|[GetUserState メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getuserstate-method.md)|この `ICorDebugThread`の現在の状態を示す CorDebugUserState 値のビットごとの組み合わせを取得します。|  
|[SetDebugState メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-setdebugstate-method.md)|この `ICorDebugThread`のデバッグ状態を記述する `CorDebugThreadState` 値のビットごとの組み合わせを設定します。|  
  
## <a name="remarks"></a>Remarks  
  
> [!NOTE]
> このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。  
  
## <a name="requirements"></a>［要件］  
 **:** 「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [デバッグ インターフェイス](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
