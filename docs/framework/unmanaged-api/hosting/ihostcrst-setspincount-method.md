---
title: IHostCrst::SetSpinCount メソッド
ms.date: 03/30/2017
api_name:
- IHostCrst.SetSpinCount
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostCrst::SetSpinCount
helpviewer_keywords:
- IHostCrst::SetSpinCount method [.NET Framework hosting]
- SetSpinCount method [.NET Framework hosting]
ms.assetid: 863fc8ce-9b8a-477e-8dd8-75c8544bb43a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3ca17a6814b56c0fe781cfb28a35a576f02f1943
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61967675"
---
# <a name="ihostcrstsetspincount-method"></a>IHostCrst::SetSpinCount メソッド
現在のスピン カウントを設定[IHostCrst](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md)インスタンス。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT SetSpinCount (  
    [in] DWORD dwSpinCount  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `dwSpinCount`  
 [in]現在の新しいスピン カウント`IHostCrst`インスタンス。  
  
## <a name="return-value"></a>戻り値  
  
|HRESULT|説明|  
|-------------|-----------------|  
|S_OK|`SetSpinCount` 正常に返されます。|  
|HOST_E_CLRNOTAVAILABLE|共通言語ランタイム (CLR) は、プロセスに読み込まれていないか、CLR は状態をマネージ コードを実行または呼び出しを正常に処理ができません。|  
|HOST_E_TIMEOUT|呼び出しがタイムアウトになりました。|  
|HOST_E_NOT_OWNER|呼び出し元がロックを所有していません。|  
|HOST_E_ABANDONED|イベントがキャンセルされましたブロックされたスレッドまたはファイバーが待機しています。|  
|E_FAIL|不明な致命的なエラーが発生しました。 メソッドには、E_FAIL が返される、ときに、CLR は、プロセス内で使用可能ではなくなりました。 メソッドをホストする後続の呼び出しには、HOST_E_CLRNOTAVAILABLE が返されます。|  
  
## <a name="remarks"></a>Remarks  
 マルチプロセッサ システムでは、現在、クリティカル セクションを表す場合`IHostCrst`インスタンスが利用できない、呼び出し元のスレッドをスピン`dwSpinCount`回呼び出す前に[ihostsemaphore::wait](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-wait-method.md)関連付けられているセマフォで重要なセクションです。 クリティカル セクションは、スピン操作中に無料になると、呼び出し元のスレッドは待機操作を回避できます。  
  
 使用状況`dwSpinCount`、Win32 では、同じ名前のパラメーターの使用量と同じ`InitializeCriticalSectionAndSpinCount`関数。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** MSCorEE.h  
  
 **ライブラリ:** MSCorEE.dll でリソースとして含まれます  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICLRSyncManager インターフェイス](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [IHostCrst インターフェイス](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md)
- [IHostSyncManager インターフェイス](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
