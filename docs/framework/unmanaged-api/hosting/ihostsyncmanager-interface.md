---
title: IHostSyncManager インターフェイス
ms.date: 03/30/2017
api_name:
- IHostSyncManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSyncManager
helpviewer_keywords:
- IHostSyncManager interface [.NET Framework hosting]
ms.assetid: 2e081a37-6a28-4c93-b7ab-1c96a464637c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 200da8b87b52a29c2b075d1e06929031d3f588b7
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59174227"
---
# <a name="ihostsyncmanager-interface"></a>IHostSyncManager インターフェイス
共通言語ランタイム (CLR) に同期の Win32 関数を使用する代わりに、ホストを呼び出すことによって同期プリミティブを作成できるようにするメソッドを提供します。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[CreateAutoEvent メソッド](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createautoevent-method.md)|自動リセット イベント オブジェクトを作成します。|  
|[CreateCrst メソッド](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createcrst-method.md)|同期のためのクリティカル セクション オブジェクトを作成します。|  
|[CreateCrstWithSpinCount メソッド](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createcrstwithspincount-method.md)|同期のためのスピン カウントとクリティカル セクション オブジェクトを作成します。|  
|[CreateManualEvent メソッド](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createmanualevent-method.md)|手動リセット イベント オブジェクトを作成します。|  
|[CreateMonitorEvent メソッド](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createmonitorevent-method.md)|監視対象の自動リセット イベント オブジェクトを作成します。|  
|[CreateRWLockReaderEvent メソッド](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createrwlockreaderevent-method.md)|リーダー ロックの実装のための手動リセット イベント オブジェクトを作成します。|  
|[CreateRWLockWriterEvent メソッド](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createrwlockwriterevent-method.md)|ライター ロックの実装の自動リセット イベント オブジェクトを作成します。|  
|[CreateSemaphore メソッド](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createsemaphore-method.md)|作成、 [IHostSemaphore](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md)待機イベントのセマフォとして使用する clr オブジェクト。|  
|[SetCLRSyncManager メソッド](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-setclrsyncmanager-method.md)|セット、 [ICLRSyncManager](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)インスタンスに現在関連付ける`IHostSyncManager`インスタンス。|  
  
## <a name="remarks"></a>Remarks  
 CLR のホストの実装を検出する`IHostSyncManager`呼び出すことによって、 [ihostcontrol::gethostmanager](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-gethostmanager-method.md)メソッドを`IID`IID_IHostSyncManager の。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** MSCorEE.h  
  
 **ライブラリ:** MSCorEE.dll でリソースとして含まれます  
  
 **.NET Framework のバージョン: ** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICLRSyncManager インターフェイス](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [ホスト インターフェイス](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
