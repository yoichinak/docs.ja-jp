---
title: IHostTaskManager::CreateTask メソッド
ms.date: 03/30/2017
api_name:
- IHostTaskManager.CreateTask
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::CreateTask
helpviewer_keywords:
- CreateTask method, IHostTaskManager interface [.NET Framework hosting]
- IHostTaskManager::CreateTask method [.NET Framework hosting]
ms.assetid: a6f8ad36-61e1-42b0-9db2-add575646d18
topic_type:
- apiref
ms.openlocfilehash: fef2f56fd000a8610a40661a30aa306ae5a7884e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177997"
---
# <a name="ihosttaskmanagercreatetask-method"></a>IHostTaskManager::CreateTask メソッド
ホストに新しいタスクの作成を要求します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT CreateTask (  
    [in]  DWORD stacksize,
    [in]  LPTHREAD_START_ROUTINE pStartAddress,  
    [in]  PVOID pParameter,  
    [out] IHostTask **ppTask  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `stacksize`  
 [in]要求されたスタックの要求されたサイズ (バイト単位) またはデフォルト サイズの 0 (ゼロ)。  
  
 `pStartAddress`  
 [in]タスクが実行する関数へのポインター。  
  
 `pParameter`  
 [in]関数に渡されるユーザー データへのポインター。  
  
 `ppTask`  
 [アウト]ホストによって作成された[IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)インスタンスのアドレスへのポインター。 タスクは[、IHostTask::Start](../../../../docs/framework/unmanaged-api/hosting/ihosttask-start-method.md)の呼び出しによって明示的に開始されるまで中断状態のままになります。  
  
## <a name="return-value"></a>戻り値  
  
|HRESULT|説明|  
|-------------|-----------------|  
|S_OK|`CreateTask`正常に返されました。|  
|HOST_E_CLRNOTAVAILABLE|共通言語ランタイム (CLR) がプロセスに読み込まれていないか、CLR がマネージ コードを実行できない状態または呼び出しを正常に処理できない状態にあります。|  
|HOST_E_TIMEOUT|通話がタイムアウトしました。|  
|HOST_E_NOT_OWNER|呼び出し元がロックを所有していません。|  
|HOST_E_ABANDONED|ブロックされたスレッドまたはファイバが待機しているときにイベントがキャンセルされました。|  
|E_FAIL|不明な致命的なエラーが発生しました。 メソッドがE_FAILを返すと、CLR はプロセス内で使用できなくなります。 ホスト メソッドへの後続の呼び出しは、HOST_E_CLRNOTAVAILABLEを返します。|  
|E_OUTOFMEMORY|メモリ不足で、要求されたタスクを作成できませんでした。|  
  
## <a name="remarks"></a>解説  
 ホストが新`CreateTask`しいタスクを作成することを要求する CLR 呼び出し。 ホストは、インスタンスへのインターフェイス ポインター`IHostTask`を返します。 返されたタスクは、 への呼び出しによって明示的に開始されるまで`IHostTask::Start`中断されたままにする必要があります。  
  
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
