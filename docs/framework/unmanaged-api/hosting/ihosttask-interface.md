---
title: IHostTask インターフェイス
ms.date: 03/30/2017
api_name:
- IHostTask
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTask
helpviewer_keywords:
- IHostTask interface [.NET Framework hosting]
ms.assetid: a71dbbd5-64b8-47eb-9f03-8e8c85fbe2bc
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cb15da31d91565d49df83099045f742866eebcaa
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61992837"
---
# <a name="ihosttask-interface"></a>IHostTask インターフェイス
共通言語ランタイム (CLR) にタスクを管理するホストと通信できるようにするメソッドを提供します。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[Alert メソッド](../../../../docs/framework/unmanaged-api/hosting/ihosttask-alert-method.md)|要求のホストが現在によって表されるタスクを wake`IHostTask`のインスタンスのため、タスクが中止されることができます。|  
|[GetPriority メソッド](../../../../docs/framework/unmanaged-api/hosting/ihosttask-getpriority-method.md)|現在のタスクのスレッド優先度レベルを取得`IHostTask`インスタンス。|  
|[Join メソッド](../../../../docs/framework/unmanaged-api/hosting/ihosttask-join-method.md)|現在によって表されるタスクまで呼び出し元のタスクをブロック`IHostTask`インスタンスが完了すると、指定した時間間隔が経過すると、または[ihosttask::alert](../../../../docs/framework/unmanaged-api/hosting/ihosttask-alert-method.md)が呼び出されます。|  
|[SetCLRTask メソッド](../../../../docs/framework/unmanaged-api/hosting/ihosttask-setclrtask-method.md)|関連付けます、 [ICLRTask インターフェイス](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)を現在`IHostTask`インスタンス。|  
|[SetPriority メソッド](../../../../docs/framework/unmanaged-api/hosting/ihosttask-setpriority-method.md)|現在によって表されるタスクのスレッドの優先順位を変更するホストの要求レベル`IHostTask`インスタンス。|  
|[Start メソッド](../../../../docs/framework/unmanaged-api/hosting/ihosttask-start-method.md)|ホストが現在によって表されるタスクを移動要求`IHostTask`インスタンス、中断状態からコードを実行できる、ライブ状態にします。|  
  
## <a name="remarks"></a>Remarks  
 CLR によって定義されたメソッドを呼び出し、`IHostTask`タスクを開始するにはそのスレッドの優先度をレベルの設定。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** MSCorEE.h  
  
 **ライブラリ:** MSCorEE.dll でリソースとして含まれます  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICLRTask インターフェイス](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [ICLRTaskManager インターフェイス](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [IHostTaskManager インターフェイス](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
- [ホスト インターフェイス](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
