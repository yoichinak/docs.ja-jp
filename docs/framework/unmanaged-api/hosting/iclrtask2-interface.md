---
title: ICLRTask2 インターフェイス
ms.date: 03/30/2017
api_name:
- ICLRTask2
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTask2
helpviewer_keywords:
- ICLRTask2 interface [.NET Framework hosting]
ms.assetid: b5a22ebc-0582-49de-91f9-97a3d9789290
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 518248651de6d8afdf25692c5f48da52b11eb0f7
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59172472"
---
# <a name="iclrtask2-interface"></a>ICLRTask2 インターフェイス
すべての機能を提供、 [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)インターフェイスは、さらに、現在のスレッドが遅延するスレッドの中止できるようにするメソッドを提供します。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[BeginPreventAsyncAbort メソッド](../../../../docs/framework/unmanaged-api/hosting/iclrtask2-beginpreventasyncabort-method.md)|新しいスレッドの遅延は、現在のスレッドで要求を中止します。|  
|[EndPreventAsyncAbort メソッド](../../../../docs/framework/unmanaged-api/hosting/iclrtask2-endpreventasyncabort-method.md)|保留中のスレッドで発生するスレッドの中止要求を現在のスレッドの中止または新規作成できます。|  
  
## <a name="remarks"></a>Remarks  
 `ICLRTask2`インターフェイスの継承、`ICLRTask`インターフェイスし、ホストが失敗する必要がありますしないコードの領域を保護するために、スレッドの中止を遅延できるようにするメソッドを追加します。 呼び出す`BeginPreventAsyncAbort`、現在のスレッドと呼び出し元のスレッド中止を遅延カウンターをインクリメント`EndPreventAsyncAbort`デクリメントこと。 呼び出す`BeginPreventAsyncAbort`と`EndPreventAsyncAbort`入れ子にすることができます。 カウンターが 0 より大きい場合に限り、現在のスレッドのスレッドの中止が遅延します。  
  
 場合呼び出し`BeginPreventAsyncAbort`と`EndPreventAsyncAbort`が対になっていない、することは、現在のスレッドにスレッドの中止を配信できない状態に到達します。  
  
 遅延自体を中止するスレッドを有効になりません。  
  
 この機能によって公開される機能は、仮想マシン (VM) で内部的に使用されます。 これらのメソッドの誤用によっては、VM の未定義の動作があります。 たとえば、呼び出し`EndPreventAsyncAbort`最初に呼び出さず`BeginPreventAsyncAbort`VM がインクリメントしていたときに、カウンターを 0 に設定でした。 同様に、内部カウンターは、オーバーフローはチェックされません。 ホストと VM の両方でインクリメントされますので、その整数の制限を超えている場合、結果として得られる動作は指定されていません。  
  
 継承されたメンバーに関する情報の`ICLRTask`このインターフェイスの他の使用の詳細についてを参照してください。 および、 [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)インターフェイス。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** MSCorEE.h  
  
 **ライブラリ:** MSCorEE.dll でリソースとして含まれます  
  
 **.NET Framework のバージョン: ** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICLRTask インターフェイス](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [ICLRTaskManager インターフェイス](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [IHostTask インターフェイス](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [IHostTaskManager インターフェイス](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
- [ホスト インターフェイス](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
