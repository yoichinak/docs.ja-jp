---
title: ICLRSyncManager インターフェイス
ms.date: 03/30/2017
api_name:
- ICLRSyncManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRSyncManager
helpviewer_keywords:
- ICLRSyncManager interface [.NET Framework hosting]
ms.assetid: a49f9d80-1c76-4ddd-8c49-34f913a5c596
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d3e4affa363083ce55ac3764c26412a0d60ba3f6
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59203094"
---
# <a name="iclrsyncmanager-interface"></a>ICLRSyncManager インターフェイス
要求されたタスクに関する情報を取得し、その同期実装でデッドロックを検出するためにホストできるようにするメソッドを定義します。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[CreateRWLockOwnerIterator メソッド](iclrsyncmanager-createrwlockowneriterator-method.md)|共通言語ランタイム (CLR) を使用して、リーダー/ライター ロックで待機しているタスクのセットを決定するホストの反復子を作成するように要求します。|  
|[DeleteRWLockOwnerIterator メソッド](iclrsyncmanager-deleterwlockowneriterator-method.md)|要求に CLR への呼び出しによって作成された反復子の破棄`CreateRWLockOwnerIterator`します。|  
|[GetMonitorOwner メソッド](iclrsyncmanager-getmonitorowner-method.md)|指定したモニターを所有するタスクを取得します。|  
|[GetRWLockOwnerNext メソッド](iclrsyncmanager-getrwlockownernext-method.md)|現在のリーダー/ライター ロックを待機している次のタスクを取得します。|  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** MSCorEE.h  
  
 **ライブラリ:** MSCorEE.dll でリソースとして含まれます  
  
 **.NET Framework のバージョン: ** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- <xref:System.Threading.Thread>
- [IHostSyncManager インターフェイス](ihostsyncmanager-interface.md)
- [マネージド スレッドとアンマネージド スレッド](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/5s8ee185(v=vs.100))
- [ホスト インターフェイス](hosting-interfaces.md)
