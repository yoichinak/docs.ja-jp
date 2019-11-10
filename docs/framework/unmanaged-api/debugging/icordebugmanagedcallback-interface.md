---
title: ICorDebugManagedCallback インターフェイス
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback
helpviewer_keywords:
- ICorDebugManagedCallback interface [.NET Framework debugging]
ms.assetid: b47f1d61-c7dc-4196-b926-0b08c94f7041
topic_type:
- apiref
ms.openlocfilehash: 96dedcd27e87c5afc504e7840100eb121410675e
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/30/2019
ms.locfileid: "73130754"
---
# <a name="icordebugmanagedcallback-interface"></a>ICorDebugManagedCallback インターフェイス
デバッガーのコールバックを処理するメソッドを提供します。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[Break メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-break-method.md)|コードストリーム内の <xref:System.Reflection.Emit.OpCodes.Break> 命令が実行されたときに、デバッガーに通知します。|  
|[Breakpoint メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-breakpoint-method.md)|ブレークポイントが検出されたときにデバッガーに通知します。|  
|[BreakpointSetError メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-breakpointseterror-method.md)|関数が just-in-time (JIT) コンパイルされる前に設定されたブレークポイントを共通言語ランタイム (CLR) が正しくバインドできなかったことをデバッガーに通知します。|  
|[ControlCTrap メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-controlctrap-method.md)|デバッグ中のプロセスで CTRL + C がトラップされることをデバッガーに通知します。|  
|[CreateAppDomain メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createappdomain-method.md)|アプリケーションドメインが作成されたことをデバッガーに通知します。|  
|[CreateProcess メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createprocess-method.md)|プロセスが初めてアタッチまたは開始されたときにデバッガーに通知します。|  
|[CreateThread メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createthread-method.md)|スレッドがマネージコードの実行を開始したことをデバッガーに通知します。|  
|[DebuggerError メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-debuggererror-method.md)|CLR からのイベントを処理しようとしたときにエラーが発生したことをデバッガーに通知します。|  
|[EditAndContinueRemap メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-editandcontinueremap-method.md)|非推奨。 リマップイベントが IDE に送信されたことをデバッガーに通知します。|  
|[EvalComplete メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-evalcomplete-method.md)|評価が完了したことをデバッガーに通知します。|  
|[EvalException メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-evalexception-method.md)|ハンドルされない例外で評価が終了したことをデバッガーに通知します。|  
|[Exception メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exception-method.md)|マネージコードから例外がスローされたことをデバッガーに通知します。|  
|[ExitAppDomain メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitappdomain-method.md)|アプリケーションドメインが終了したことをデバッガーに通知します。|  
|[ExitProcess メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitprocess-method.md)|プロセスが終了したことをデバッガーに通知します。|  
|[ExitThread メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitthread-method.md)|マネージコードを実行していたスレッドが終了したことをデバッガーに通知します。|  
|[LoadAssembly メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadassembly-method.md)|CLR アセンブリが正常に読み込まれたことをデバッガーに通知します。|  
|[LoadClass メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md)|クラスが読み込まれたことをデバッガーに通知します。|  
|[LoadModule メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadmodule-method.md)|CLR モジュールが正常に読み込まれたことをデバッガーに通知します。|  
|[LogMessage メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-logmessage-method.md)|CLR マネージスレッドが、イベントを記録するために <xref:System.Diagnostics.EventLog> クラスのメソッドを呼び出したことをデバッガーに通知します。|  
|[LogSwitch メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-logswitch-method.md)|CLR マネージスレッドが、デバッグ/トレーススイッチを作成、変更、または削除するために <xref:System.Diagnostics.Switch> クラスのメソッドを呼び出したことをデバッガーに通知します。|  
|[NameChange メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-namechange-method.md)|アプリケーションドメインまたはスレッドの名前が変更されたことをデバッガーに通知します。|  
|[StepComplete メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-stepcomplete-method.md)|ステップが完了したことをデバッガーに通知します。|  
|[UnloadAssembly メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-unloadassembly-method.md)|CLR アセンブリがアンロードされたことをデバッガーに通知します。|  
|[UnloadClass メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-unloadclass-method.md)|クラスがアンロードされていることをデバッガーに通知します。|  
|[UnloadModule メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-unloadmodule-method.md)|CLR モジュール (DLL) がアンロードされたことをデバッガーに通知します。|  
|[UpdateModuleSymbols メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-updatemodulesymbols-method.md)|CLR モジュールのシンボルが変更されたことをデバッガーに通知します。|  
  
## <a name="remarks"></a>Remarks  
 すべてのコールバックがシリアル化され、同じスレッドで呼び出され、プロセスと同期された状態で呼び出されます。  
  
 各コールバックの実装では、実行を再開するために、「いいね! [:: Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) 」を呼び出します。 コールバックが戻る前に `ICorDebugController::Continue` が呼び出されなかった場合、プロセスは停止したままになり、`ICorDebugController::Continue` が呼び出されるまで、これ以上イベントコールバックは実行されません。  
  
 デバッガーが .NET Framework バージョン2.0 のアプリケーションをデバッグしている場合は、 [ICorDebugManagedCallback2](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)を実装する必要があります。 `ICorDebugManagedCallback` または `ICorDebugManagedCallback2` のインスタンスは、 [ICorDebug:: SetManagedHandler](../../../../docs/framework/unmanaged-api/debugging/icordebug-setmanagedhandler-method.md)にコールバックオブジェクトとして渡されます。  
  
> [!NOTE]
> このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。  
  
## <a name="requirements"></a>［要件］  
 **:** 「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICorDebug インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
- [ICorDebugManagedCallback2 インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)
- [デバッグ インターフェイス](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
