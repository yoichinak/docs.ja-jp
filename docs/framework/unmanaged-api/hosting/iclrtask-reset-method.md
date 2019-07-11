---
title: ICLRTask::Reset メソッド
ms.date: 03/30/2017
api_name:
- ICLRTask.Reset
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTask::Reset
helpviewer_keywords:
- ICLRTask::Reset method [.NET Framework hosting]
- Reset method, ICLRTask interface [.NET Framework hosting]
ms.assetid: 1bfb5d3a-0ffd-4bb4-9bf6-aec00cb675b7
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3039855a58e6db6a403ab33c226b4b8b390668f7
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/10/2019
ms.locfileid: "67758589"
---
# <a name="iclrtaskreset-method"></a>ICLRTask::Reset メソッド
ホストは、タスクを完了し、現在を再利用する CLR を有効に、共通言語ランタイム (CLR) を通知[ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)を別のタスクを表すインスタンス。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT Reset (  
    [in] BOOL fFull  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `fFull`  
 [in]`true`場合は、ランタイムは、現在に関連するセキュリティとロケール情報だけでなく、スレッド関連の静的な値をリセットする必要があります、`ICLRTask`インスタンス。 それ以外の場合、`false`します。  
  
 値が場合`true`、ランタイムを使用して格納されたデータをリセットする<xref:System.Threading.Thread.AllocateDataSlot%2A>または<xref:System.Threading.Thread.AllocateNamedDataSlot%2A>します。  
  
## <a name="return-value"></a>戻り値  
  
|HRESULT|説明|  
|-------------|-----------------|  
|S_OK|`Reset` 正常に返されます。|  
|HOST_E_CLRNOTAVAILABLE|プロセスに CLR が読み込まれていないか、CLR は状態をマネージ コードを実行または呼び出しの処理にことはできません。 正常に|  
|HOST_E_TIMEOUT|呼び出しがタイムアウトになりました。|  
|HOST_E_NOT_OWNER|呼び出し元がロックを所有していません。|  
|HOST_E_ABANDONED|イベントがキャンセルされましたブロックされたスレッドまたはファイバーが待機しています。|  
|E_FAIL|不明な致命的なエラーが発生しました。 メソッドには、E_FAIL が返される、ときに、CLR は、プロセス内で使用可能ではなくなりました。 メソッドをホストする後続の呼び出しには、HOST_E_CLRNOTAVAILABLE が返されます。|  
  
## <a name="remarks"></a>Remarks  
 以前に作成した、CLR をリサイクルできます`ICLRTask`インスタンスに新しいタスクが必要があるたびに、新しいインスタンスを繰り返し作成のオーバーヘッドを回避します。 ホストが呼び出すことによってこの機能を有効`ICLRTask::Reset`の代わりに[iclrtask::exittask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-exittask-method.md)タスクを完了したとき。 次の一覧は、通常のライフ サイクルをまとめたものです、`ICLRTask`インスタンス。  
  
1. 新しいランタイムを作成`ICLRTask`インスタンス。  
  
2. ランタイム呼び出し[ihosttaskmanager::getcurrenttask](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-getcurrenttask-method.md)ホストの現在のタスクへの参照を取得します。  
  
3. ランタイム呼び出し[ihosttask::setclrtask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-setclrtask-method.md)に新しいインスタンスを関連付けるホスト タスク。  
  
4. タスクを実行し、完了します。  
  
5. ホストが呼び出すことによって、タスクを破棄`ICLRTask::ExitTask`します。  
  
 `Reset` このシナリオは 2 つの方法を変更します。 5 は、ホストの呼び出し前の手順で`Reset`タスクをクリーンな状態にリセットしてを分離し、`ICLRTask`から関連付けられたインスタンス[IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)インスタンス。 ホストをキャッシュできますも、必要な場合は、`IHostTask`インスタンスを再利用します。 1 つ目の手順で、ランタイムは、リサイクル`ICLRTask`新しいインスタンスを作成する代わりにキャッシュからします。  
  
 このアプローチは、ホストにも再利用可能なワーカー タスクのプールがある場合に機能します。 ホストがのいずれかを破棄するときにその`IHostTask`インスタンス、破棄、対応する`ICLRTask`呼び出すことによって`ExitTask`。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:** [システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** MSCorEE.h  
  
 **ライブラリ:** MSCorEE.dll でリソースとして含まれます  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICLRTask インターフェイス](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [ICLRTaskManager インターフェイス](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [IHostTask インターフェイス](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [IHostTaskManager インターフェイス](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
