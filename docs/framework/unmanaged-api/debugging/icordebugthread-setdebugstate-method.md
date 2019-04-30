---
title: ICorDebugThread::SetDebugState メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugThread.SetDebugState
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread::SetDebugState
helpviewer_keywords:
- ICorDebugThread::SetDebugState method [.NET Framework debugging]
- SetDebugState method [.NET Framework debugging]
ms.assetid: 6382bdf6-d488-4952-b653-cb09b6e1c6c2
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d29f5cefd22592fa8949ff5361109c09c0972b24
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61987143"
---
# <a name="icordebugthreadsetdebugstate-method"></a>ICorDebugThread::SetDebugState メソッド
この ICorDebugThread のデバッグ状態を記述するフラグを設定します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT SetDebugState (  
    [in] CorDebugThreadState state  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `state`  
 [in]このスレッドのデバッグ状態を指定する CorDebugThreadState 列挙値のビットごとの組み合わせ。  
  
## <a name="remarks"></a>Remarks  
 `SetDebugState` スレッドの現在のデバッグ状態を設定します。 (「現在のデバッグ状態」状態を表しますデバッグ プロセスに続く、実際の現状ではない場合。)通常この値は、THREAD_RUNNING です。 デバッガーのみ、スレッドのデバッグ状態に影響を与えることができます。 デバッグ状態は最終間で継続されるため、複数経由で THREAD_SUSPENDed 継続スレッドを保持する場合は、一度の設定し、その後、それについて心配する必要ありません。 スレッドの中断とプロセスを再開する可能性があります、デッドロックは通常はほとんどありません。 スレッドおよびプロセスの組み込みの品質は、この設計では、します。 デバッガーは、非同期的に中断し、デッドロックを中断するスレッドを再開できます。 スレッドのユーザーの状態には、USER_UNSAFE_POINT が含まれている場合、スレッドがガベージ コレクション (GC) をブロックします。 つまり、中断されたスレッドがする可能性が高いデッドロックが発生します。 これはデバッグ イベントが既にキューに登録には影響可能性があります。 したがって、デバッガーが全体のイベント キューをドレインする必要があります (呼び出して[icordebugcontroller::hasqueuedcallbacks](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-hasqueuedcallbacks-method.md)) を中断またはスレッドを再開する前にします。 それ以外の場合は既に中断されていると確信するスレッドでイベントを取得、可能性があります。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
