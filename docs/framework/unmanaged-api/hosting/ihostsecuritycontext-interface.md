---
title: IHostSecurityContext インターフェイス
ms.date: 03/30/2017
api_name:
- IHostSecurityContext
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSecurityContext
helpviewer_keywords:
- IHostSecurityContext interface [.NET Framework hosting]
ms.assetid: 88e2eac0-8ccb-404f-abbc-287d55159842
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9d71b7e1265110a70329377ce8ab7430e1943c49
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61984296"
---
# <a name="ihostsecuritycontext-interface"></a>IHostSecurityContext インターフェイス
により、共通言語ランタイム (CLR) にホストによって実装されるセキュリティ コンテキスト情報を保持します。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[Capture メソッド](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-capture-method.md)|複製を取得、`IHostSecurityContext`への呼び出しから返されるインスタンス[ihostsecuritymanager::getsecuritycontext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-getsecuritycontext-method.md)します。|  
  
## <a name="remarks"></a>Remarks  
 ホストは、CLR とユーザーの両方のコードでスレッド トークンへのすべてのコード アクセスを制御できます。 その完全なセキュリティを確保できますも非同期操作または制限付きのコード アクセス権を持つコード ポイントの間で渡されるコンテキスト情報。 `IHostSecurityContext` このは、ランタイムに対して非透過的セキュリティ コンテキスト情報をカプセル化します。 ランタイムを使用してこの情報をキャプチャする`Capture`、し、スレッド プールのワーカーの項目のディスパッチ、ファイナライザーの実行、およびモジュールとクラスのコンス トラクターの間で移動します。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** MSCorEE.h  
  
 **ライブラリ:** MSCorEE.dll でリソースとして含まれます  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICLRHostProtectionManager インターフェイス](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-interface.md)
- [IHostSecurityManager インターフェイス](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-interface.md)
- [ホスト インターフェイス](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
