---
title: IHostThreadPoolManager インターフェイス
ms.date: 03/30/2017
api_name:
- IHostThreadPoolManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostThreadPoolManager
helpviewer_keywords:
- IHostThreadPoolManager interface [.NET Framework hosting]
ms.assetid: c3a2cd90-7c4e-4374-bb87-b41befb8344f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2e7976740a79efda8e5ab569f2efb55444012c5d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59220371"
---
# <a name="ihostthreadpoolmanager-interface"></a>IHostThreadPoolManager インターフェイス
共通言語ランタイム (CLR) スレッド プールを構成し、スレッド プールに作業項目をキューに登録を有効にする方法を提供します。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[GetAvailableThreads メソッド](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-getavailablethreads-method.md)|作業項目を現在処理していないスレッド プールのスレッドの数を取得します。|  
|[GetMaxThreads メソッド](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-getmaxthreads-method.md)|スレッド プールに同時にホストで管理されるスレッドの最大数を取得します。|  
|[GetMinThreads メソッド](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-getminthreads-method.md)|要求に応じるためには、ホストで管理されるアイドル状態のスレッドの最小数を取得します。|  
|[QueueUserWorkItem メソッド](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-queueuserworkitem-method.md)|キューに入れ、実行するための関数および関数によって使用されるデータを格納しているオブジェクトを提供します。|  
|[SetMaxThreads メソッド](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-setmaxthreads-method.md)|ホストは、スレッド プールで保持できるスレッドの最大数を設定します。|  
|[SetMinThreads メソッド](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-setminthreads-method.md)|要求に応じるため、ホストを管理する必要があるアイドル状態のスレッドの最小数を設定します。|  
  
## <a name="remarks"></a>Remarks  
 ホストがへの呼び出しで指定された値を使用して、スレッド プールを構成する必要はありません、`SetMaxThreads`と`SetMinThreads`メソッド。 この場合、ホストは、これらのメソッドから HRESULT 値 E_NOTIMPL を返す必要があります。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** MSCorEE.h  
  
 **ライブラリ:** MSCorEE.dll でリソースとして含まれます  
  
 **.NET Framework のバージョン: ** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- <xref:System.Threading>
- <xref:System.Threading.ThreadPool>
- [ホスト インターフェイス](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
