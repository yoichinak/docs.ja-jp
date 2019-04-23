---
title: ICorDebugUnmanagedCallback::DebugEvent メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugUnmanagedCallback.DebugEvent
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugUnmanagedCallback::DebugEvent
helpviewer_keywords:
- DebugEvent method [.NET Framework debugging]
- ICorDebugUnmanagedCallback::DebugEvent method [.NET Framework debugging]
ms.assetid: be9cab04-65ec-44d5-a39a-f90709fdd043
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6ec45004f5dd87983187690a0a4feefb35b05e85
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59183613"
---
# <a name="icordebugunmanagedcallbackdebugevent-method"></a>ICorDebugUnmanagedCallback::DebugEvent メソッド
ネイティブ イベントが発生したことをデバッガーに通知します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT DebugEvent (  
    [in] LPDEBUG_EVENT  pDebugEvent,  
    [in] BOOL           fOutOfBand  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `pDebugEvent`  
 [in]ネイティブ イベントへのポインター。  
  
 `fOutOfBand`  
 [in]`true`デバッガー呼び出されるまで、非管理対象のイベントの発生後に管理対象プロセスの状態との対話が不可能な場合、 [icordebugcontroller::continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md)、それ以外の`false`します。  
  
## <a name="remarks"></a>Remarks  
 デバッグ中のスレッドが Win32 スレッドの場合は、デバッグのインターフェイス、Win32 のメンバーを使用しないでください。 呼び出すことができます`ICorDebugController::Continue`Win32 スレッドでのみ、および過去の帯域外のイベントを続行するときのみです。  
  
 `DebugEvent`コールバックがコールバックの標準の規則に従っていません。 呼び出すと`DebugEvent`、生のプロセスになる、OS デバッグは停止状態です。 プロセスは同期されません。 同期完了の状態をそれ以外の入れ子になっている可能性がマネージ コードに関する情報の要求を満たすために必要な場合に自動的に入力`DebugEvent`コールバック。  
  
 呼び出す[icordebugprocess::clearcurrentexception](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-clearcurrentexception-method.md)プロセスを続行する前に、例外イベントを無視するプロセス。 このメソッドを呼び出すと、続行要求で、DBG_EXCEPTION_NOT_HANDLED ではなく DBG_CONTINUE を送信し、帯域外のブレークポイントとシングル ステップの例外を自動的にクリアします。 帯域外のイベントは、未処理の帯域内イベントが既に存在する場合、デバッグ中のアプリケーションが停止している場合でも、いつでも取得できます。  
  
 .NET framework version 2.0 では、デバッガーを過去の帯域外のブレークポイント イベント続行すぐにする必要があります。 デバッガーを使用する必要があります、 [icordebugprocess 2::setunmanagedbreakpoint](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-setunmanagedbreakpoint-method.md)と[icordebugprocess 2::clearunmanagedbreakpoint](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-clearunmanagedbreakpoint-method.md)メソッドを追加し、ブレークポイントを削除します。 これらのメソッドは、帯域外のブレークポイントを自動的にスキップされます。 したがって、ディスパッチの帯域外のだけのブレークポイントは Win32 への呼び出しなど、命令ストリーム内に既にある生のブレークポイントをする必要があります`DebugBreak`関数。 使用しないで`ICorDebugProcess::ClearCurrentException`、 [icordebugprocess::getthreadcontext](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-getthreadcontext-method.md)、 [icordebugprocess::setthreadcontext](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-setthreadcontext-method.md)、または他のメンバー、[デバッグ API](../../../../docs/framework/unmanaged-api/debugging/index.md)します。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICorDebugUnmanagedCallback インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebugunmanagedcallback-interface.md)
