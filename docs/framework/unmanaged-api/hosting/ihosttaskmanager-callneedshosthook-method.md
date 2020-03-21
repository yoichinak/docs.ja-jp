---
title: IHostTaskManager::CallNeedsHostHook メソッド
ms.date: 03/30/2017
api_name:
- IHostTaskManager.CallNeedsHostHook
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::CallNeedsHostHook
helpviewer_keywords:
- CallNeedsHostHook method [.NET Framework hosting]
- IHostTaskManager::CallNeedsHostHook method [.NET Framework hosting]
ms.assetid: b60f1f59-9825-4b57-961f-d2979518e6a7
topic_type:
- apiref
ms.openlocfilehash: 8b8b8521a09fa54a105e8263a471ab0467fb6ccc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176293"
---
# <a name="ihosttaskmanagercallneedshosthook-method"></a>IHostTaskManager::CallNeedsHostHook メソッド
ホストが、指定されたアンマネージ関数の呼び出しをインライン処理できるかどうかを指定できます。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT CallNeedsHostHook (  
    [in]  SIZE_T target,
    [out] BOOL   *pbCallNeedsHostHook  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `target`  
 [in]呼び出されるアンマネージ関数の、マップされたポータブル実行可能 (PE) ファイル内のアドレス。  
  
 `pbCallNeedsHostHook`  
 [アウト]ホストが呼び出しをフックする必要があるかどうかを示すブール値へのポインター。  
  
## <a name="return-value"></a>戻り値  
  
|HRESULT|説明|  
|-------------|-----------------|  
|S_OK|`CallNeedsHostHook`正常に返されました。|  
|HOST_E_CLRNOTAVAILABLE|CLR がプロセスに読み込まれていないか、CLR がマネージ コードを実行できない状態または呼び出しを正常に処理できない状態にあります。|  
|HOST_E_TIMEOUT|通話がタイムアウトしました。|  
|HOST_E_NOT_OWNER|呼び出し元がロックを所有していません。|  
|HOST_E_ABANDONED|ブロックされたスレッドまたはファイバが待機しているときにイベントがキャンセルされました。|  
|E_FAIL|不明な致命的な障害が発生しました。 メソッドがE_FAILを返すと、CLR はプロセス内で使用できなくなります。 ホスト メソッドへの後続の呼び出しは、HOST_E_CLRNOTAVAILABLEを返します。|  
  
## <a name="remarks"></a>解説  
 コードの実行を最適化するために、CLR はコンパイル中に各プラットフォーム呼び出しの分析を実行し、呼び出しをインライン展開できるかどうかを判断します。 `CallNeedsHostHook`を使用すると、ホストはアンマネージ関数の呼び出しをフックするように要求することによって、その決定をオーバーライドできます。 ホストがフックを必要とする場合、ランタイムは呼び出しをインライン行いません。  
  
 ホストは通常、浮動小数点の状態を調整する必要があるフックを必要とするか、または呼び出しがランタイムのメモリ要求またはロックを追跡できない状態に入っているという通知を受け取ったときに必要になります。 ホストが呼び出しをフックする必要がある場合、ランタイムは[、EnterRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-enterruntime-method.md) [、LeaveRuntime、](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-leaveruntime-method.md)[リバースエンターランタイム](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseenterruntime-method.md)、および[リバースリーブランタイム](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseleaveruntime-method.md)の呼び出しを使用して、マネージ コードとの間の遷移のホストに通知します。  
  
## <a name="requirements"></a>必要条件  
 **:**「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** msCorEE.h  
  
 **ライブラリ:** MSCorEE.dll にリソースとして含まれる  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICLRTask インターフェイス](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [ICLRTaskManager インターフェイス](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [IHostTask インターフェイス](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [IHostTaskManager インターフェイス](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
