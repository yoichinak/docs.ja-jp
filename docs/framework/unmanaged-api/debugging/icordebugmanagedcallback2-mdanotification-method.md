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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4011932af6f4b058906c19566e4c1abe96b409db
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/10/2019
ms.locfileid: "67762088"
---
# <a name="icordebugmanagedcallback2mdanotification-method"></a>ICorDebugManagedCallback2::MDANotification メソッド
コードが実行されるには、デバッグ中のアプリケーションでマネージ デバッグ アシスタント (MDA) が発生した通知を提供します。  
  
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
 [in]プロセスを公開する ICorDebugController インターフェイスまたは MDA が発生したアプリケーション ドメインへのポインター。  
  
 デバッガーは、コント ローラーは、プロセスまたはアプリケーション ドメインでは、かどうかについてどのような想定をしないでを決定するインターフェイスを常に照会できることですが。  
  
 `pThread`  
 [in]デバッグ イベントが発生したマネージ スレッドを公開する ICorDebugThread インターフェイスへのポインター。  
  
 MDA は、アンマネージで発生した場合のスレッドの値`pThread`は null になります。  
  
 MDA オブジェクト自体からは、オペレーティング システム (OS) のスレッド ID を取得する必要があります。  
  
 `pMDA`  
 [in]ポインター、 [ICorDebugMDA](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md) MDA 情報を公開するインターフェイス。  
  
## <a name="remarks"></a>Remarks  
 MDA はヒューリスティック警告であり、呼び出し元を除く任意の明示的なデバッガー操作が必要としない[icordebugcontroller::continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md)がデバッグされているアプリケーションの実行を再開します。  
  
 Mda が起動され、特定の MDA 任意の時点でのデータは、共通言語ランタイム (CLR) を確認できます。 そのため、デバッガーは特定の MDA パターンを必要とするすべての機能をビルドする必要があります。  
  
 Mda は、キューに MDA が発生した直後後に発生した可能性があります。 これは、ランタイムがそれを見つけたときに MDA を発生させるのではなく、MDA を発生させるためのセーフ ポイントに到達するまで待機する必要がある場合に発生する可能性があります。 また、ランタイムは、Mda のキューに置かれたコールバック (「添付」イベントの操作に似ています) の 1 組の数で発生する可能性があります。  
  
 デバッガーへの参照を解放する必要があります、`ICorDebugMDA`インスタンスから取得した直後に、`MDANotification`コールバック、MDA によって消費されるメモリのリサイクル、CLR を許可します。 インスタンスを解放すると、多数の Mda が発生している場合にパフォーマンスが向上する可能性があります。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:** [システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [マネージド デバッグ アシスタントによるエラーの診断](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [ICorDebugManagedCallback2 インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)
- [ICorDebugManagedCallback インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
