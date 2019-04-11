---
title: ICLRTask インターフェイス
ms.date: 03/30/2017
api_name:
- ICLRTask
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTask
helpviewer_keywords:
- ICLRTask interface [.NET Framework hosting]
ms.assetid: b3a44df3-578a-4451-b55e-70c8e7695f5e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1baeac5db41aa64380d694ebab5419229d8adb4c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59088208"
---
# <a name="iclrtask-interface"></a>ICLRTask インターフェイス
ホストまたは関連するタスクについて、CLR に通知を提供する共通言語ランタイム (CLR) の要求を行うことができるようにするメソッドを提供します。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[Abort メソッド](../../../../docs/framework/unmanaged-api/hosting/iclrtask-abort-method.md)|CLR がタスクを中止する要求を現在`ICLRTask`インスタンスが表す。|  
|[ExitTask メソッド](../../../../docs/framework/unmanaged-api/hosting/iclrtask-exittask-method.md)|現在のタスクが関連付けられている CLR に通知`ICLRTask`インスタンスが終了し、タスクを正常にシャット ダウンしようとしています。|  
|[GetMemStats メソッド](../../../../docs/framework/unmanaged-api/hosting/iclrtask-getmemstats-method.md)|現在によって表されるタスクによってメモリ リソースの使用に関する統計情報を取得します。`ICLRTask`インスタンス。|  
|[LocksHeld メソッド](../../../../docs/framework/unmanaged-api/hosting/iclrtask-locksheld-method.md)|タスクで現在保持されているロックの数を取得します。|  
|[NeedsPriorityScheduling メソッド](../../../../docs/framework/unmanaged-api/hosting/iclrtask-needspriorityscheduling-method.md)|ホストが現在によって表されるタスクをスケジュールする優先度の高いを割り当てる必要があるかどうかを示す値を取得します`ICLRTask`インスタンス。|  
|[Reset メソッド](../../../../docs/framework/unmanaged-api/hosting/iclrtask-reset-method.md)|ホストは、タスクを完了し、により、現在の再利用する CLR を CLR に通知`ICLRTask`を別のタスクを表すインスタンス。|  
|[RudeAbort メソッド](../../../../docs/framework/unmanaged-api/hosting/iclrtask-rudeabort-method.md)|Clr は、現在によって表されるタスクを中止する`ICLRTask`インスタンスをすぐに、ファイナライザーが実行されることを保証なし。|  
|[SetTaskIdentifier メソッド](../../../../docs/framework/unmanaged-api/hosting/iclrtask-settaskidentifier-method.md)|現在のタスクの一意の識別子を設定`ICLRTask`デバッグで使用するためのインスタンス。|  
|[SwitchIn メソッド](../../../../docs/framework/unmanaged-api/hosting/iclrtask-switchin-method.md)|現在のタスクが表す CLR に通知`ICLRTask`インスタンスが操作可能な状態です。|  
|[SwitchOut メソッド](../../../../docs/framework/unmanaged-api/hosting/iclrtask-switchout-method.md)|現在のタスクが表す CLR に通知`ICLRTask`インスタンスは操作可能な状態ではありません。|  
|[YieldTask メソッド](../../../../docs/framework/unmanaged-api/hosting/iclrtask-yieldtask-method.md)|その他のタスクで使用できる CLR 作成のプロセッサ時間を要求します。 CLR には、タスクが処理時間を得ることのできる状態になる保証はありません。|  
  
## <a name="remarks"></a>Remarks  
 `ICLRTask` Clr タスクの表現です。 コードの実行中にいつでも実行中または実行を待機して、タスクを記述できます。 ホストの呼び出し、`ICLRTask::SwitchIn`メソッドが CLR に通知するタスクを現在`ICLRTask`インスタンスを表しますが、可能な状態で。 呼び出しの後に`ICLRTask::SwitchIn`、ホストは、ランタイムへの呼び出しで指定したとおり、スレッド アフィニティが必要な場合を除く、任意のオペレーティング システム スレッドでタスクをスケジュールすることができます、 [ihosttaskmanager::beginthreadaffinity](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-beginthreadaffinity-method.md)と[Ihosttaskmanager::endthreadaffinity](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-endthreadaffinity-method.md)メソッド。 しばらくしてから、スレッドからタスクを削除し、実行されていない状態で配置するオペレーティング システムがあります。 たとえば、タスクの同期プリミティブでブロックまたは I/O 操作が完了するまで待機するたびに、これが発生可能性があります。 ホスト呼び出し[SwitchOut](../../../../docs/framework/unmanaged-api/hosting/iclrtask-switchout-method.md)タスクが現在によって表される CLR に通知する`ICLRTask`インスタンスは操作可能な状態ではありません。  
  
 タスクは、通常、コードの実行の最後に終了します。 ホストを呼び出して、その時点で`ICLRTask::ExitTask`、関連付けられているを破棄する`ICLRTask`します。 ただし、タスクもとして再利用できるへの呼び出しを使用して`ICLRTask::Reset`、これにより、`ICLRTask`もう一度使用するインスタンス。 このアプローチには、繰り返し作成して、インスタンスの破棄のオーバーヘッドができないようにします。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** MSCorEE.h  
  
 **ライブラリ:** MSCorEE.dll でリソースとして含まれます  
  
 **.NET Framework のバージョン: ** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICLRTaskManager インターフェイス](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [IHostTask インターフェイス](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [IHostTaskManager インターフェイス](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
- [ホスト インターフェイス](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [ICLRTask2 インターフェイス](../../../../docs/framework/unmanaged-api/hosting/iclrtask2-interface.md)
