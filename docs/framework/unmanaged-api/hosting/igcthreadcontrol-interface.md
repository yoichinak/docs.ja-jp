---
title: IGCThreadControl インターフェイス
ms.date: 03/30/2017
api_name:
- IGCThreadControl
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IGCThreadControl
helpviewer_keywords:
- IGCThreadControl interface [.NET Framework hosting]
ms.assetid: 3ff04d75-85ac-4df9-886d-dbaa037c0552
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5c00f401bedc1a2810c4e9b3046a45e53a79f1ea
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59134265"
---
# <a name="igcthreadcontrol-interface"></a>IGCThreadControl インターフェイス
それ以外の場合、ガベージ コレクションのブロックされるスレッドのスケジューリングに参加するためのメソッドを提供します。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[SuspensionEnding メソッド](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-suspensionending-method.md)|ランタイムがガベージ コレクションまたはその他の中断の後のスレッドを再開することをホストに通知します。|  
|[SuspensionStarting メソッド](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-suspensionstarting-method.md)|ランタイムがガベージ コレクションのスレッドの中断またはその他の中断を開始していることをホストに通知します。|  
|[ThreadIsBlockingForSuspension メソッド](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-threadisblockingforsuspension-method.md)|ガベージ コレクションまたはその他の中断のためにブロックする直前の呼び出しを行っているスレッドが、ホストに通知します。|  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** MSCorEE.h  
  
 **ライブラリ:** MSCorEE.dll でリソースとして含まれます  
  
 **.NET Framework のバージョン: ** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ホスト インターフェイス](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
