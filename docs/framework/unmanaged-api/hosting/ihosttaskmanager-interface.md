---
title: IHostTaskManager インターフェイス
ms.date: 03/30/2017
api_name:
- IHostTaskManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager
helpviewer_keywords:
- IHostTaskManager interface [.NET Framework hosting]
ms.assetid: 4a0b05b9-3ef1-4607-b7c8-bd4dd43647a0
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: da30e75bf4a58e66bb0dd8210368b162cf14c3f7
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59091266"
---
# <a name="ihosttaskmanager-interface"></a>IHostTaskManager インターフェイス
共通言語ランタイム (CLR) 標準のオペレーティング システムのスレッドやファイバーの関数を使用する代わりに、ホストでタスクを処理できるようにするメソッドを提供します。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[BeginDelayAbort メソッド](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-begindelayabort-method.md)|マネージ コードのホストが、現在のタスクを中止しない期間を入力することを通知します。|  
|[BeginThreadAffinity メソッド](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-beginthreadaffinity-method.md)|マネージ コードのホストが、現在のタスクを別のオペレーティング システム スレッドに移動できない期間を入力することを通知します。|  
|[CallNeedsHostHook メソッド](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-callneedshosthook-method.md)|共通言語ランタイムがアンマネージ関数に指定された呼び出しをインラインにできるかどうかを指定するホストを有効にします。|  
|[CreateTask メソッド](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-createtask-method.md)|ホストが新しいタスクを作成することを要求します。|  
|[EndDelayAbort メソッド](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-enddelayabort-method.md)|マネージ コードのホストが終了する期間を現在のタスクを中止する必要がない、事前に呼び出した通知`BeginDelayAbort`します。|  
|[EndThreadAffinity メソッド](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-endthreadaffinity-method.md)|マネージ コードのホストが終了する、現在のタスクを別のオペレーティング システム スレッドに移動できない期間以前の呼び出しに通知`BeginThreadAffinity`します。|  
|[EnterRuntime メソッド](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-enterruntime-method.md)|ホストに、非管理対象のメソッドの呼び出しなど、プラットフォーム呼び出しメソッドを返すこと実行制御、CLR に通知します。|  
|[GetCurrentTask メソッド](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-getcurrenttask-method.md)|この呼び出しが行われた元のオペレーティング システム スレッドで現在実行しているタスクには、インターフェイス ポインターを取得します。|  
|[GetStackGuarantee メソッド](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-getstackguarantee-method.md)|プロセスの終了前に、スタック操作の完了後に、使用することが保証されるスタック領域の量を取得します。|  
|[LeaveRuntime メソッド](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-leaveruntime-method.md)|アンマネージ関数を呼び出すにマネージ コードをホストに通知します。|  
|[ReverseEnterRuntime メソッド](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseenterruntime-method.md)|アンマネージ コードから共通言語ランタイム (CLR) に呼び出しがされているホストに通知します。|  
|[ReverseLeaveRuntime メソッド](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseleaveruntime-method.md)|コントロールが、CLR のままであり、さらに、マネージ コードから呼び出されたアンマネージ関数を入力することをホストに通知します。|  
|[SetCLRTaskManager メソッド](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-setclrtaskmanager-method.md)|により、ホストへのインターフェイス ポインターで、 [ICLRTaskManager](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md) CLR で実装されているインスタンス。|  
|[SetLocale メソッド](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-setlocale-method.md)|CLR の現在のタスクのロケールが変更されたことをホストに通知します。|  
|[SetStackGuarantee メソッド](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-setstackguarantee-method.md)|内部使用専用に予約されています。|  
|[SetUILocale メソッド](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-setuilocale-method.md)|現在のタスクのユーザー インターフェイスのロケールが変更されたことをホストに通知します。|  
|[Sleep メソッド](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-sleep-method.md)|現在のタスクがスリープ状態になることをホストに通知します。|  
|[SwitchToTask メソッド](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-switchtotask-method.md)|現在のタスクを切り離すことをホストに通知します。|  
  
## <a name="remarks"></a>Remarks  
 `IHostTaskManager` 作成および管理タスク、CLR は、マネージとアンマネージ コードは、逆から制御が転送するときにアクションを実行して、特定のアクションを指定するためのフックを提供するホストことができ、コードが実行時に実行できません。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** MSCorEE.h  
  
 **ライブラリ:** MSCorEE.dll でリソースとして含まれます  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICLRTask インターフェイス](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [ICLRTaskManager インターフェイス](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [IHostTask インターフェイス](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [ホスト インターフェイス](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
