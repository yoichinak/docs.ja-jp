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
ms.openlocfilehash: a89ea76d78431ae8833602588379d5150e473710
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69938306"
---
# <a name="iclrtaskmanagercreatetask-method"></a>ICLRTaskManager::CreateTask メソッド
共通言語ランタイム (CLR) によって新しいタスクが作成されることを明示的に要求します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT CreateTask (  
    [out] ICLRTask **pTask  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `pTask`  
 入出力新しく作成された[ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)のアドレスへのポインター、またはタスクを作成できなかった場合は null。  
  
## <a name="return-value"></a>戻り値  
  
|HRESULT|説明|  
|-------------|-----------------|  
|S_OK|メソッドが正常に返されました。|  
|HOST_E_CLRNOTAVAILABLE|CLR がプロセスに読み込まれていないか、CLR がマネージドコードを実行できない状態であるか、または呼び出しが正常に処理されていません。|  
|HOST_E_TIMEOUT|呼び出しがタイムアウトしました。|  
|HOST_E_NOT_OWNER|呼び出し元がロックを所有していません。|  
|HOST_E_ABANDONED|ブロックされたスレッドまたはファイバーが待機しているときに、イベントが取り消されました。|  
|E_FAIL|原因不明の致命的なエラーが発生しました。 メソッドから E_FAIL が返された場合、そのプロセス内で CLR は使用できなくなります。 後続のホストメソッドの呼び出しでは、HOST_E_CLRNOTAVAILABLE が返されます。|  
|E_OUTOFMEMORY|要求されたリソースを割り当てるのに十分なメモリがありません。|  
  
## <a name="remarks"></a>Remarks  
 CLR は、初期化時、ユーザーコードが<xref:System.Threading>名前空間の型を使用してスレッドを作成するとき、またはスレッドプールのサイズが増加したときに、新しいタスクを自動的に作成します。 また、アンマネージコードがマネージ関数を呼び出す場合にも、タスクが作成されます。  
  
 `CreateTask`CLR によって新しいタスクが作成されることをホストが明示的に要求できるようにします。 たとえば、ホストはこのメソッドを呼び出して、データ構造を事前に初期化できます。  
  
> [!IMPORTANT]
> 新しいタスクは中断状態で返され、ホストが明示的に[IHostTask:: Start](../../../../docs/framework/unmanaged-api/hosting/ihosttask-start-method.md)を呼び出すまで中断されたままになります。  
  
## <a name="requirements"></a>必要条件  
 **・**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** Mscoree.dll  
  
 **ライブラリ**Mscoree.dll にリソースとして含まれています  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICLRTask インターフェイス](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [ICLRTaskManager インターフェイス](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [IHostTask インターフェイス](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [IHostTaskManager インターフェイス](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
