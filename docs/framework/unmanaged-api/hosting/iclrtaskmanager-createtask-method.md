---
title: ICLRTaskManager::CreateTask メソッド
ms.date: 03/30/2017
api_name:
- ICLRTaskManager.CreateTask
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTaskManager::CreateTask
helpviewer_keywords:
- ICLRTaskManager::CreateTask method [.NET Framework hosting]
- CreateTask method, ICLRTaskManager interface [.NET Framework hosting]
ms.assetid: eea570d9-2e53-4320-9ea0-eb777bf9dcf3
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8833daa9cd385a1a76c5b706f15a76bb15139b84
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61763439"
---
# <a name="iclrtaskmanagercreatetask-method"></a>ICLRTaskManager::CreateTask メソッド
共通言語ランタイム (CLR) が新しいタスクを作成することを明示的に要求します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT CreateTask (  
    [out] ICLRTask **pTask  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `pTask`  
 [out]新しく作成されたのアドレスへのポインター [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)、または null の場合は、タスクを作成できませんでした。  
  
## <a name="return-value"></a>戻り値  
  
|HRESULT|説明|  
|-------------|-----------------|  
|S_OK|メソッドが正常に返されます。|  
|HOST_E_CLRNOTAVAILABLE|プロセスに CLR が読み込まれていないか、CLR は状態をマネージ コードを実行または呼び出しを正常に処理ができません。|  
|HOST_E_TIMEOUT|呼び出しがタイムアウトになりました。|  
|HOST_E_NOT_OWNER|呼び出し元がロックを所有していません。|  
|HOST_E_ABANDONED|イベントがキャンセルされましたブロックされたスレッドまたはファイバーが待機しています。|  
|E_FAIL|不明な致命的なエラーが発生しました。 メソッドには、E_FAIL が返される、ときに、CLR は、プロセス内で使用可能ではなくなりました。 メソッドをホストする後続の呼び出しには、HOST_E_CLRNOTAVAILABLE が返されます。|  
|E_OUTOFMEMORY|メモリが不足していますが、要求されたリソースを割り当てることができます。|  
  
## <a name="remarks"></a>Remarks  
 ユーザー コードで型を使用してスレッドを作成するときに、CLR が初期化時に自動的に新しいタスクを作成、<xref:System.Threading>名前空間には、スレッド プールのサイズを増加する場合またはします。 また、アンマネージ コードがマネージ関数の呼び出しを行うときにも、タスクを作成します。  
  
 `CreateTask` により、CLR が新しいタスクを作成することが明示的に要求をホストできます。 たとえば、ホストは、このメソッドを呼び出してデータ構造を呼び出すことができます。  
  
> [!IMPORTANT]
>  新しいタスクが中断状態に返され、ホストを明示的に呼び出すまで、中断されたまま[ihosttask::start](../../../../docs/framework/unmanaged-api/hosting/ihosttask-start-method.md)します。  
  
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
