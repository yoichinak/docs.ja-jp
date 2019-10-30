---
title: ICorDebugManagedCallback2::MDANotification メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback2.MDANotification
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback2::MDANotification
helpviewer_keywords:
- MDANotification method [.NET Framework debugging]
- ICorDebugManagedCallback2::MDANotification method [.NET Framework debugging]
ms.assetid: 93f79627-bd31-4f4f-b95d-46a032a52fe4
topic_type:
- apiref
ms.openlocfilehash: ab3819d5c33f090fda1ca9c3dccb5d08ab8f84cc
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131460"
---
# <a name="icordebugmanagedcallback2mdanotification-method"></a>ICorDebugManagedCallback2::MDANotification メソッド
コード実行で、デバッグ中のアプリケーションでマネージデバッグアシスタント (MDA) が検出されたことを通知します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT MDANotification(  
    [in] ICorDebugController  *pController,  
    [in] ICorDebugThread      *pThread,  
    [in] ICorDebugMDA         *pMDA  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `pController`  
 からMDA が発生したプロセスまたはアプリケーションドメインを公開する、表示コントローラーインターフェイスへのポインター。  
  
 デバッガーでは、コントローラーがプロセスとアプリケーションドメインのどちらであるかについては想定しませんが、常にインターフェイスを照会して決定を行うことができます。  
  
 `pThread`  
 からデバッグイベントが発生したマネージスレッドを公開する、コードスレッドインターフェイスへのポインター。  
  
 アンマネージスレッドで MDA が発生した場合、`pThread` の値は null になります。  
  
 MDA オブジェクト自体からオペレーティングシステム (OS) のスレッド ID を取得する必要があります。  
  
 `pMDA`  
 からMDA 情報を公開[する、ツールのインターフェイスへ](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md)のポインター。  
  
## <a name="remarks"></a>Remarks  
 MDA は、ヒューリスティック警告であり、[例外を明示的に呼び出す必要](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md)はありません。ただし、デバッグ中のアプリケーションの実行を再開する場合を除き、明示的なデバッガーアクションは必要ありません。  
  
 共通言語ランタイム (CLR) は、どの Mda が発生したか、また任意の時点でどのデータが特定の MDA に存在するかを判断できます。 したがって、デバッガーでは、特定の MDA パターンを必要とする機能を構築しないでください。  
  
 Mda は、MDA が検出された直後にキューに入れられ、発生する可能性があります。 これは、mda が発生したときに MDA を起動するのではなく、MDA を起動するためのセーフポイントに到達するまで、ランタイムが待機する必要がある場合に発生する可能性があります。 また、ランタイムは、キューに置かれたコールバックの1つのセット ("attach" イベント操作に似ています) で多数の Mda を起動することもあります。  
  
 デバッガーは、`MDANotification` コールバックから戻った直後に `ICorDebugMDA` インスタンスへの参照を解放し、CLR が MDA によって消費されるメモリを再利用できるようにする必要があります。 多くの Mda が起動している場合、インスタンスを解放するとパフォーマンスが向上する可能性があります。  
  
## <a name="requirements"></a>［要件］  
 **:** 「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [マネージド デバッグ アシスタントによるエラーの診断](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [ICorDebugManagedCallback2 インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)
- [ICorDebugManagedCallback インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
