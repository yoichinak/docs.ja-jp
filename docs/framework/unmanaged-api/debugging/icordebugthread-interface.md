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
ms.openlocfilehash: 1517d686c50923f5599e33436e0ad6126e8be140
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69923143"
---
# <a name="icordebugthread-interface"></a>ICorDebugThread インターフェイス
プロセス内のスレッドを表します。 `ICorDebugThread` インスタンスの有効期間は、それが表しているスレッドの有効期間と同じです。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[ClearCurrentException メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-clearcurrentexception-method.md)|このメソッドは実装されていません。 使用しないでください。|  
|[CreateEval メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-createeval-method.md)|この`ICorDebugThread`を操作する、のオブジェクトを作成します。|  
|[CreateStepper メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-createstepper-method.md)|この`ICorDebugThread`のアクティブなフレームをステップ実行できるようにする ICorDebugStepper オブジェクトを作成します。|  
|[EnumerateChains メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-enumeratechains-method.md)|この`ICorDebugThread`内のすべてのスタックチェーンを格納している ICorDebugChainEnum 列挙子へのインターフェイスポインターを取得します。|  
|[GetActiveChain メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getactivechain-method.md)|この`ICorDebugThread`のアクティブなツールチェーンへのインターフェイスポインターを取得します。|  
|[GetActiveFrame メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getactiveframe-method.md)|この`ICorDebugThread`上のアクティブなテキストフレームへのインターフェイスポインターを取得します。|  
|[GetAppDomain メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getappdomain-method.md)|この`ICorDebugThread`が現在実行されているアプリケーションドメインへのインターフェイスポインターを取得します。|  
|[GetCurrentException メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getcurrentexception-method.md)|現在マネージコードによってスローされている例外を表す、ICorDebugValue オブジェクトへのインターフェイスポインターを取得します。|  
|[GetDebugState メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getdebugstate-method.md)|この`ICorDebugThread`の現在のデバッグ状態を示す CorDebugThreadState 値を取得します。|  
|[GetHandle メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-gethandle-method.md)|この`ICorDebugThread`のアクティブな部分の現在のハンドルを取得します。|  
|[GetID メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getid-method.md)|この`ICorDebugThread`のアクティブな部分の現在のオペレーティングシステム識別子を取得します。|  
|[GetObject メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getobject-method.md)|共通言語ランタイム (CLR) スレッドへのインターフェイスポインターを取得します。|  
|[GetProcess メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getprocess-method.md)|この`ICorDebugThread`がパートを形成するプロセスへのインターフェイスポインターを取得します。|  
|[GetRegisterSet メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getregisterset-method.md)|この`ICorDebugThread`に関連付けられているレジスタセットへのインターフェイスポインターを取得します。|  
|[GetUserState メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getuserstate-method.md)|この`ICorDebugThread`の現在の状態を示す cordebuguserstate 値のビットごとの組み合わせを取得します。|  
|[SetDebugState メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-setdebugstate-method.md)|`CorDebugThreadState` この`ICorDebugThread`のデバッグ状態を記述する値のビットごとの組み合わせを設定します。|  
  
## <a name="remarks"></a>Remarks  
  
> [!NOTE]
> このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。  
  
## <a name="requirements"></a>必要条件  
 **・** [システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorDebug .idl、CorDebug. h  
  
 **ライブラリ**CorGuids .lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [デバッグ インターフェイス](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
