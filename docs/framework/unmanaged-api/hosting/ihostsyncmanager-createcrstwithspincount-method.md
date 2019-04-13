---
title: IHostSyncManager::CreateCrstWithSpinCount メソッド
ms.date: 03/30/2017
api_name:
- IHostSyncManager.CreateCrstWithSpinCount
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSyncManager::CreateCrstWithSpinCount
helpviewer_keywords:
- CreateCrstWithSpinCount method [.NET Framework hosting]
- IHostSyncManager::CreateCrstWithSpinCount method [.NET Framework hosting]
ms.assetid: 7280fa8c-3639-4abf-91cb-bc343da742d1
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1a288edc89029804de277484741c1895af7859b1
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59081529"
---
# <a name="ihostsyncmanagercreatecrstwithspincount-method"></a>IHostSyncManager::CreateCrstWithSpinCount メソッド
同期のためのスピン カウントとクリティカル セクション オブジェクトを作成します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT CreateCrstWithSpinCount (  
    [in]  DWORD dwSpinCount,  
    [out] IHostCrst** ppCrst  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `dwSpinCount`  
 [in]クリティカル セクション オブジェクトのスピン カウントを指定します。  
  
 `ppCrst`  
 [out]アドレスへのポインター、 [IHostCrst](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md)インスタンス、または、クリティカル セクションを作成できなかった場合は null です。  
  
## <a name="return-value"></a>戻り値  
  
|HRESULT|説明|  
|-------------|-----------------|  
|S_OK|`CreateCrstWithSpinCount` 正常に返されます。|  
|HOST_E_CLRNOTAVAILABLE|共通言語ランタイム (CLR) は、プロセスに読み込まれていないか、CLR は状態をマネージ コードを実行または呼び出しを正常に処理ができません。|  
|HOST_E_TIMEOUT|呼び出しがタイムアウトになりました。|  
|HOST_E_NOT_OWNER|呼び出し元がロックを所有していません。|  
|HOST_E_ABANDONED|イベントがキャンセルされましたブロックされたスレッドまたはファイバーが待機しています。|  
|E_FAIL|不明な致命的なエラーが発生しました。 メソッドには、E_FAIL が返される、ときに、CLR は、プロセス内で使用可能ではなくなりました。 メソッドをホストする後続の呼び出しには、HOST_E_CLRNOTAVAILABLE が返されます。|  
|E_OUTOFMEMORY|メモリ不足は、要求のクリティカル セクションを作成できませんでした。|  
  
## <a name="remarks"></a>Remarks  
 スピン カウントは、マルチプロセッサ システムでのみ使用されます。 スピン カウントには、呼び出し元のスレッドが利用不可のクリティカル セクションに関連付けられているセマフォの待機操作を実行する前に回転する必要があります回数を指定します。 クリティカル セクションは、スピン操作中に無料になると、呼び出し元のスレッドは待機操作を回避できます。 `CreateCrstWithSpinCount` Win32 をミラー化`InitializeCriticalSectionAndSpinCount`関数。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** MSCorEE.h  
  
 **ライブラリ:** MSCorEE.dll でリソースとして含まれます  
  
 **.NET Framework のバージョン: ** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICLRSyncManager インターフェイス](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [IHostSemaphore インターフェイス](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md)
- [IHostSyncManager インターフェイス](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
