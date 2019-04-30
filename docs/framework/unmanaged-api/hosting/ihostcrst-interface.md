---
title: IHostCrst インターフェイス
ms.date: 03/30/2017
api_name:
- IHostCrst
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostCrst
helpviewer_keywords:
- IHostCrst interface [.NET Framework hosting]
ms.assetid: ac298ebd-0815-47e4-a823-30b31baab903
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 939f100e8ee386642a29c33827a8339caf0467b9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61967831"
---
# <a name="ihostcrst-interface"></a>IHostCrst インターフェイス
ホストのスレッドのクリティカル セクションの表現として機能します。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[Enter メソッド](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-enter-method.md)|クリティカル セクションに入ります。|  
|[Leave メソッド](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-leave-method.md)|クリティカル セクションを残します。|  
|[SetSpinCount メソッド](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-setspincount-method.md)|クリティカル セクションのスピン カウントを設定します。|  
|[TryEnter メソッド](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-tryenter-method.md)|クリティカル セクション、およびレポートの成功または失敗をすぐに入力しようとします。|  
  
## <a name="remarks"></a>Remarks  
 `IHostCrst` などの Win32 関数を使用するのではなく、共通言語ランタイム (CLR) のクリティカル セクションでは、ホストの表現と直接通信するためには、`EnterCriticalSection`または`LeaveCriticalSection`します。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** MSCorEE.h  
  
 **ライブラリ:** MSCorEE.dll でリソースとして含まれます  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICLRSyncManager インターフェイス](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [IHostSyncManager インターフェイス](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
- [ホスト インターフェイス](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
