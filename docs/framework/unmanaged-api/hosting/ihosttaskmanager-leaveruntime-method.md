---
title: IHostTaskManager::LeaveRuntime メソッド
ms.date: 03/30/2017
api_name:
- IHostTaskManager.LeaveRuntime
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::LeaveRuntime
helpviewer_keywords:
- IHostTaskManager::LeaveRuntime method [.NET Framework hosting]
- LeaveRuntime method [.NET Framework hosting]
ms.assetid: 43689cc4-e48e-46e5-a22d-bafd768b8759
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2059657a6f4543ee29d795ecae7b93b72876fdf4
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2019
ms.locfileid: "57474632"
---
# <a name="ihosttaskmanagerleaveruntime-method"></a>IHostTaskManager::LeaveRuntime メソッド
現在実行中のタスクが共通言語ランタイム (CLR) のままにし、アンマネージ コードを入力することをホストに通知します。  
  
> [!IMPORTANT]
>  対応する呼び出し[ihosttaskmanager::enterruntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-enterruntime-method.md)現在実行中のタスクがマネージ コードを再入力するホストに通知します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT LeaveRuntime (  
    [in] SIZE_T target  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `target`  
 [in]呼び出されるアンマネージ関数のマップされたポータブル実行可能ファイル内のアドレス。  
  
## <a name="return-value"></a>戻り値  
  
|HRESULT|説明|  
|-------------|-----------------|  
|S_OK|`LeaveRuntime` 正常に返されます。|  
|HOST_E_CLRNOTAVAILABLE|プロセスに CLR が読み込まれていないか、CLR は状態をマネージ コードを実行または呼び出しを正常に処理ができません。|  
|HOST_E_TIMEOUT|呼び出しがタイムアウトになりました。|  
|HOST_E_NOT_OWNER|呼び出し元がロックを所有していません。|  
|HOST_E_ABANDONED|イベントがキャンセルされましたブロックされたスレッドまたはファイバーが待機しています。|  
|E_FAIL|不明な致命的なエラーが発生しました。 メソッドには、E_FAIL が返される、ときに、CLR は、プロセス内で使用可能ではなくなりました。 メソッドをホストする後続の呼び出しには、HOST_E_CLRNOTAVAILABLE が返されます。|  
|E_OUTOFMEMORY|十分なメモリが要求された割り当てを完了します。|  
  
## <a name="remarks"></a>Remarks  
 アンマネージ コードとの間の呼び出しシーケンスを入れ子にすることができます。 たとえば、以下の一覧は、仮定の状況を記述しますへの呼び出しのシーケンス`LeaveRuntime`、 [ihosttaskmanager::reverseenterruntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseenterruntime-method.md)、 [ihosttaskmanager::reverseleaveruntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseleaveruntime-method.md)。、および`IHostTaskManager::EnterRuntime`入れ子になったレイヤーを識別するためにホストできるようにします。  
  
|アクション|対応するメソッドの呼び出し|  
|------------|-------------------------------|  
|マネージ Visual Basic 実行可能なプラットフォームを使用して C# で記述されたアンマネージ関数を呼び出します。|`IHostTaskManager::LeaveRuntime`|  
|アンマネージ C 関数で記述されたマネージ DLL のメソッドを呼び出すC#します。|`IHostTaskManager::ReverseEnterRuntime`|  
|マネージC#関数が C で記述された別のアンマネージ関数を呼び出し、呼び出しもプラットフォームを使用します。|`IHostTaskManager::LeaveRuntime`|  
|2 番目のアンマネージ関数が実行を返す、C#関数。|`IHostTaskManager::EnterRuntime`|  
|C#関数は、最初にアンマネージ関数に実行を戻します。|`IHostTaskManager::ReverseLeaveRuntime`|  
|最初のアンマネージ関数では、Visual Basic プログラムを実行を返します。|`IHostTaskManager::EnterRuntime`|  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** MSCorEE.h  
  
 **ライブラリ:** MSCorEE.dll でリソースとして含まれます  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目
- [ICLRTask インターフェイス](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [ICLRTaskManager インターフェイス](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [IHostTask インターフェイス](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [IHostTaskManager インターフェイス](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
