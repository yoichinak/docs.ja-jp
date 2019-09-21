---
title: ICorDebugManagedCallback2 インターフェイス
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback2
helpviewer_keywords:
- ICorDebugManagedCallback2 interface [.NET Framework debugging]
ms.assetid: cf7b7cfa-1c4b-4d8c-be70-4f9ed15a788b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ca33436d98edf5844a5ca27c9ac89648f10ec0c5
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69909984"
---
# <a name="icordebugmanagedcallback2-interface"></a>ICorDebugManagedCallback2 インターフェイス
デバッガーの例外処理およびマネージド デバッグ アシスタント (MDA: Managed Debugging Assistants) をサポートするメソッドを提供します。 `ICorDebugManagedCallback2`は[、のように、の](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)論理上の拡張機能です。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[ChangeConnection メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-changeconnection-method.md)|指定した接続に関連付けられたタスクのセットが変更されたことをデバッガーに通知します。|  
|[CreateConnection メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-createconnection-method.md)|新しい接続が作成されたことをデバッガーに通知します。|  
|[DestroyConnection メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-destroyconnection-method.md)|指定された接続が終了したことをデバッガーに通知します。|  
|[Exception メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-exception-method.md)|例外ハンドラーの検索が開始されたことをデバッガーに通知します。|  
|[ExceptionUnwind メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-exceptionunwind-method.md)|例外アンワインド処理中の状態通知を提供します。|  
|[FunctionRemapComplete メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-functionremapcomplete-method.md)|コードの実行が編集された関数の新しいバージョンに切り替わったことをデバッガーに通知します。|  
|[FunctionRemapOpportunity メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-functionremapopportunity-method.md)|コードの実行が、編集された関数の古いバージョンのシーケンスポイントに達したことをデバッガーに通知します。|  
|[MDANotification メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-mdanotification-method.md)|コード実行でマネージデバッグアシスタント (MDA) メッセージが検出されたことを通知します。|  
  
## <a name="remarks"></a>Remarks  
 インターフェイス`ICorDebugManagedCallback2`は、 `ICorDebugManagedCallback`インターフェイスを拡張して、.NET Framework バージョン2.0 で導入された新しいデバッグイベントを処理します。  
  
 デバッガーが .NET Framework 2.0 `ICorDebugManagedCallback2`アプリケーションをデバッグしている場合は、を実装する必要があります。 または`ICorDebugManagedCallback` `ICorDebugManagedCallback2`のインスタンスは、コールバックオブジェクトとして[ICorDebug:: setmanagedhandler](../../../../docs/framework/unmanaged-api/debugging/icordebug-setmanagedhandler-method.md)に渡されます。  
  
> [!NOTE]
> このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。  
  
## <a name="requirements"></a>必要条件  
 **・**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorDebug .idl、CorDebug. h  
  
 **ライブラリ**CorGuids .lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [マネージド デバッグ アシスタントによるエラーの診断](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [デバッグ インターフェイス](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [ICorDebugManagedCallback インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
