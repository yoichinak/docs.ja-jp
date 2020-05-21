---
title: ICLRTaskManager インターフェイス
ms.date: 03/30/2017
api_name:
- ICLRTaskManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTaskManager
helpviewer_keywords:
- ICLRTaskManager interface [.NET Framework hosting]
ms.assetid: 2bd55e0c-001b-41fd-b29d-f01670fe8216
topic_type:
- apiref
ms.openlocfilehash: 9e26071181e8e0712c753fa03d5e16eb85e5ee68
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762835"
---
# <a name="iclrtaskmanager-interface"></a>ICLRTaskManager インターフェイス
ホストが、共通言語ランタイム (CLR) が新しいタスクを作成し、現在実行中のタスクを取得し、タスクの地理的言語とカルチャを設定することを明示的に要求するメソッドを提供します。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[CreateTask メソッド](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-createtask-method.md)|CLR が新しい[ICLRTask](iclrtask-interface.md)インスタンスを作成することを明示的に要求します。|  
|[GetCurrentTask メソッド](iclrtaskmanager-getcurrenttask-method.md)|`ICLRTask`現在実行中のタスクを表すインスタンスを取得します。|  
|[GetCurrentTaskType メソッド](iclrtaskmanager-getcurrenttasktype-method.md)|現在実行中のタスクの種類を取得します。|  
|[SetLocale メソッド](iclrtaskmanager-setlocale-method.md)|現在実行中のタスクのロケール識別子がホストによって変更されたことを CLR に通知します。|  
|[SetUILocale メソッド](iclrtaskmanager-setuilocale-method.md)|現在実行中のタスクのユーザーインターフェイスのロケール識別子がホストによって変更されたことを、共通言語ランタイムに通知します。|  
  
## <a name="remarks"></a>解説  
 ホスト環境で実行されている各タスクは、ホスト側 ( [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)のインスタンス) と CLR 側 ( [ICLRTask](iclrtask-interface.md)のインスタンス) の両方で表現されます。 ホストまたは CLR がタスクの作成を開始することはできますが、ホストと CLR の間でタスクに関して正常に通信できるように、ホスト側表現を対応する CLR 側表現に関連付ける必要があります。 マネージコードをオペレーティングシステムのスレッドで実行するには、2つのオブジェクトを作成してインスタンス化する必要があります。  
  
## <a name="requirements"></a>要件  
 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** Mscoree.dll  
  
 **ライブラリ:** Mscoree.dll にリソースとして含まれています  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICLRTask インターフェイス](iclrtask-interface.md)
- [IHostTask インターフェイス](ihosttask-interface.md)
- [IHostTaskManager インターフェイス](ihosttaskmanager-interface.md)
- [ホスト インターフェイス](hosting-interfaces.md)
