---
title: IHostSecurityManager::OpenThreadToken メソッド
ms.date: 03/30/2017
api_name:
- IHostSecurityManager.OpenThreadToken
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSecurityManager::OpenThreadToken
helpviewer_keywords:
- IHostSecurityManager::OpenThreadToken method [.NET Framework hosting]
- OpenThreadToken method [.NET Framework hosting]
ms.assetid: d5999052-8bf0-4a9e-8621-da6284406b18
topic_type:
- apiref
ms.openlocfilehash: 11d042ea9eecc8d428761da6eaa15f7c2907ebd8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176267"
---
# <a name="ihostsecuritymanageropenthreadtoken-method"></a>IHostSecurityManager::OpenThreadToken メソッド
現在実行中のスレッドに関連付けられている任意のアクセス トークンを開きます。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT OpenThreadToken (  
    [in]  DWORD    dwDesiredAccess,
    [in]  BOOL     bOpenAsSelf,
    [out] HANDLE   *phThreadToken  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `dwDesiredAccess`  
 [in]スレッド トークンへのアクセスの要求された種類を指定するアクセス値のマスク。 これらの値は Win32`OpenThreadToken`関数で定義されます。 要求されたアクセスの種類は、トークンの随意アクセス制御リスト (DACL) に対して調整され、許可または拒否するアクセスの種類を決定します。  
  
 `bOpenAsSelf`  
 [in]`true`呼び出し元スレッドのプロセスのセキュリティ コンテキストを使用してアクセス チェックを行うことを指定します。`false`呼び出し元スレッド自体のセキュリティ コンテキストを使用してアクセス チェックを実行するように指定します。 スレッドがクライアントを偽装している場合、セキュリティ コンテキストはクライアント プロセスのコンテキストにすることができます。  
  
 `phThreadToken`  
 [アウト]新しく開いたアクセス トークンへのポインター。  
  
## <a name="return-value"></a>戻り値  
  
|HRESULT|説明|  
|-------------|-----------------|  
|S_OK|`OpenThreadToken`正常に返されました。|  
|HOST_E_CLRNOTAVAILABLE|共通言語ランタイム (CLR) がプロセスに読み込まれていないか、CLR がマネージ コードを実行できない状態または呼び出しを正常に処理できない状態にあります。|  
|HOST_E_TIMEOUT|通話がタイムアウトしました。|  
|HOST_E_NOT_OWNER|呼び出し元がロックを所有していません。|  
|HOST_E_ABANDONED|ブロックされたスレッドまたはファイバが待機しているときにイベントがキャンセルされました。|  
|E_FAIL|不明な致命的なエラーが発生しました。 メソッドがE_FAILを返すと、CLR はプロセス内で使用できなくなります。 ホスト メソッドへの後続の呼び出しは、HOST_E_CLRNOTAVAILABLEを返します。|  
  
## <a name="remarks"></a>解説  
 `IHostSecurityManager::OpenThreadToken`Win32 関数では、呼び出し元が任意のスレッドにハンドルを渡し、呼び出し元スレッドに関連付けられたトークンのみを`IHostSecurityManager::OpenThreadToken`開くことを許可する点を除いて、同じ名前の対応する Win32 関数と同様に動作します。  
  
 型`HANDLE`は COM に準拠していない、つまり、そのサイズはオペレーティング システムに固有であり、カスタム マーシャリングが必要です。 したがって、このトークンは、プロセス内で、CLR とホストの間でのみ使用されます。  
  
## <a name="requirements"></a>必要条件  
 **:**「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** msCorEE.h  
  
 **ライブラリ:** MSCorEE.dll にリソースとして含まれる  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [IHostSecurityContext インターフェイス](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md)
- [IHostSecurityManager インターフェイス](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-interface.md)
