---
title: IHostSecurityManager インターフェイス
ms.date: 03/30/2017
api_name:
- IHostSecurityManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSecurityManager
helpviewer_keywords:
- IHostSecurityManager interface [.NET Framework hosting]
ms.assetid: c3be2cbd-2d93-438b-9888-9a0251b63c03
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f45379fe8640ef7e7b3917bac8d10ca956d75ffb
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59223759"
---
# <a name="ihostsecuritymanager-interface"></a>IHostSecurityManager インターフェイス
アクセスと、現在実行中のスレッドのセキュリティ コンテキストに対する制御を許可するメソッドを提供します。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[GetSecurityContext メソッド](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-getsecuritycontext-method.md)|要求された取得[IHostSecurityContext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md)ホストから。|  
|[ImpersonateLoggedOnUser メソッド](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-impersonateloggedonuser-method.md)|要求の現在のユーザー id の資格情報を使用してコードを実行します。|  
|[OpenThreadToken メソッド](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-openthreadtoken-method.md)|現在のスレッドに関連付けられた随意アクセス トークンを開きます。|  
|[RevertToSelf メソッド](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-reverttoself-method.md)|現在のユーザー id の権限の借用を終了し、元のスレッド トークンを返します。|  
|[SetSecurityContext メソッド](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-setsecuritycontext-method.md)|現在実行中のスレッドのセキュリティ コンテキストを設定します。|  
|[SetThreadToken メソッド](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-setthreadtoken-method.md)|現在実行中のスレッドのハンドルを設定します。|  
  
## <a name="remarks"></a>Remarks  
 ホストは、共通言語ランタイム (CLR) とユーザー コードの両方で、スレッド トークンへのすべてのコード アクセスを制御できます。 その完全なセキュリティを確保できますも非同期操作または制限付きのコード アクセス権を持つコード ポイントの間で渡されるコンテキスト情報。 `IHostSecurityContext` CLR に非透過的であるこのセキュリティ コンテキスト情報をカプセル化します。  
  
 CLR では、マネージ スレッドのコンテキストを内部的に処理します。 プロセス固有のクエリを実行`IHostSecurityManager`次の状況で。  
  
-   ファイナライザー スレッド、ファイナライザーの実行中です。  
  
-   実行中にクラスとモジュールのコンス トラクター。  
  
-   呼び出しで、ワーカー スレッドで非同期の時点で、 [ihostthreadpoolmanager::queueuserworkitem](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-queueuserworkitem-method.md)メソッド。  
  
-   I/O 完了ポートの使用中です。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** MSCorEE.h  
  
 **ライブラリ:** MSCorEE.dll でリソースとして含まれます  
  
 **.NET Framework のバージョン: ** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [IHostSecurityContext インターフェイス](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md)
- [ホスト インターフェイス](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
