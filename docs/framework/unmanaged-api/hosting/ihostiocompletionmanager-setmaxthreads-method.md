---
title: IHostIoCompletionManager::SetMaxThreads メソッド
ms.date: 03/30/2017
api_name:
- IHostIoCompletionManager.SetMaxThreads
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostIoCompletionManager::SetMaxThreads
helpviewer_keywords:
- IHostIoCompletionManager::SetMaxThreads method [.NET Framework hosting]
- SetMaxThreads method, IHostIoCompletionManager interface [.NET Framework hosting]
ms.assetid: ebad4f40-d9f1-4dc6-9b27-a89c9eb3926f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d867dcfc91a2da256e6857f1594701ab7d58c0b3
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2019
ms.locfileid: "57468651"
---
# <a name="ihostiocompletionmanagersetmaxthreads-method"></a>IHostIoCompletionManager::SetMaxThreads メソッド
I/O 要求を処理するため、ホストに割り当てるスレッドの最大数を設定します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT SetMaxThreads (  
    [in] DWORD dwMaxIoCompletionThreads  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `dwMaxIoCompletionThreads`  
 [in]I/O 要求に割り当てるスレッドの最大数。  
  
## <a name="return-value"></a>戻り値  
  
|HRESULT|説明|  
|-------------|-----------------|  
|S_OK|`SetMaxThreads` 正常に返されます。|  
|HOST_E_CLRNOTAVAILABLE|共通言語ランタイム (CLR) は、プロセスに読み込まれていないか、CLR は状態をマネージ コードを実行または呼び出しを正常に処理ができません。|  
|HOST_E_TIMEOUT|呼び出しがタイムアウトになりました。|  
|HOST_E_NOT_OWNER|呼び出し元がロックを所有していません。|  
|HOST_E_ABANDONED|イベントがキャンセルされましたブロックされたスレッドまたはファイバーが待機しています。|  
|E_FAIL|不明な致命的なエラーが発生しました。 メソッドには、E_FAIL が返される、ときに、CLR は、プロセス内で使用可能ではなくなりました。 メソッドをホストする後続の呼び出しには、HOST_E_CLRNOTAVAILABLE が返されます。|  
|E_NOTIMPL|ホストがの実装を提供しない`SetMaxThreads`します。|  
  
## <a name="remarks"></a>Remarks  
 `SetMaxThreads` CLR は、I/O ポート上でサービス要求に使用できるスレッドの最大数を設定する機会を提供します。 ホストの実装、パフォーマンス、スケーラビリティなどの理由から、スレッド プールのサイズを排他的に制御を必要があります。 このため、ホストする必要はありません実装`SetMaxThreads`します。 この場合、ホストは、このメソッドから E_NOTIMPL を返す必要があります。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** MSCorEE.h  
  
 **ライブラリ:** MSCorEE.dll でリソースとして含まれます  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目
- [ICLRIoCompletionManager インターフェイス](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)
- [IHostIoCompletionManager インターフェイス](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)
