---
title: ICLRTask2::EndPreventAsyncAbort メソッド
ms.date: 03/30/2017
api_name:
- ICLRTask2.EndPreventAsyncAbort
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTask2::EndPreventAsyncAbort
helpviewer_keywords:
- EndPreventAsyncAbort method [.NET Framework hosting]
- ICLRTask2::EndPreventAsyncAbort method [.NET Framework hosting]
ms.assetid: d8013659-e3df-44b3-814f-a6b534ce62f8
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 60997717baf70e10366e7f0ba6a06daa1f35f8cd
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59121668"
---
# <a name="iclrtask2endpreventasyncabort-method"></a>ICLRTask2::EndPreventAsyncAbort メソッド
保留中のスレッドで発生するスレッドの中止要求を現在のスレッドの中止または新規作成できます。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT EndPreventAsyncAbort();  
```  
  
## <a name="return-value"></a>戻り値  
 このメソッドは、次の特定の HRESULT と、メソッドの失敗を示す HRESULT エラーも返します。  
  
|HRESULT|説明|  
|-------------|-----------------|  
|S_OK|メソッドは正常に完了しました。|  
|HOST_E_INVALIDOPERATION|メソッドは、現在のスレッドではないスレッドで呼び出されました。|  
  
## <a name="remarks"></a>Remarks  
 現在のスレッドのいずれかでこのメソッドをデクリメント遅延スレッド中止のカウンターを呼び出しています。  
  
 呼び出す[iclrtask 2::beginpreventasyncabort](../../../../docs/framework/unmanaged-api/hosting/iclrtask2-beginpreventasyncabort-method.md)と`EndPreventAsyncAbort`入れ子にすることができます。 カウンターが 0 より大きい場合に限り、現在のスレッドのスレッドの中止が遅延します。  
  
 この機能によって公開される機能は、仮想マシン (VM) で内部的に使用されます。 これらのメソッドの誤用によっては、VM の未定義の動作があります。 たとえば、呼び出し`EndPreventAsyncAbort`最初に呼び出さず`BeginPreventAsyncAbort`VM がインクリメントしていたときに、カウンターを 0 に設定でした。 同様に、内部カウンターは、オーバーフローはチェックされません。 ホストと VM の両方でインクリメントされますので、その整数の制限を超えている場合、結果として得られる動作は指定されていません。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** MSCorEE.h  
  
 **ライブラリ:** MSCorEE.dll でリソースとして含まれます  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [BeginPreventAsyncAbort メソッド](../../../../docs/framework/unmanaged-api/hosting/iclrtask2-beginpreventasyncabort-method.md)
- [ICLRTask2 インターフェイス](../../../../docs/framework/unmanaged-api/hosting/iclrtask2-interface.md)
- [ICLRTaskManager インターフェイス](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [IHostTask インターフェイス](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [IHostTaskManager インターフェイス](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
- [ホスト インターフェイス](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
