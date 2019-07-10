---
title: ICLRRuntimeHost::ExecuteInAppDomain メソッド
ms.date: 03/30/2017
api_name:
- ICLRRuntimeHost.ExecuteInAppDomain
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeHost::ExecuteInAppDomain
helpviewer_keywords:
- ICLRRuntimeHost::ExecuteInAppDomain method [.NET Framework hosting]
- ExecuteInAppDomain method [.NET Framework hosting]
ms.assetid: e2b0e2db-3fae-4b56-844e-d30a125a660c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 314ffb143e99f9490bcd4a6489f2afed314b7c2c
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/10/2019
ms.locfileid: "67768763"
---
# <a name="iclrruntimehostexecuteinappdomain-method"></a>ICLRRuntimeHost::ExecuteInAppDomain メソッド
指定します、<xref:System.AppDomain>指定したマネージ コードを実行します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT ExecuteInAppDomain(  
    [in] DWORD AppDomainId,   
    [in] FExecuteInDomainCallback pCallback,   
    [in] void* cookie  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `AppDomainId`  
 [in]数値 ID、<xref:System.AppDomain>指定されたメソッドを実行します。  
  
 `pCallback`  
 [in]指定した中で実行する関数へのポインター<xref:System.AppDomain>します。  
  
 `cookie`  
 [in]非透過の呼び出し元が割り当てたメモリへのポインター。 このパラメーターは、共通言語ランタイム (CLR) でドメインのコールバックに渡されます。 ランタイムで管理されたヒープ メモリではありません。このメモリの有効期間と割り当ては、呼び出し元によって制御されます。  
  
## <a name="return-value"></a>戻り値  
  
|HRESULT|説明|  
|-------------|-----------------|  
|S_OK|`ExecuteInAppDomain` 正常に返されます。|  
|HOST_E_CLRNOTAVAILABLE|プロセスに CLR が読み込まれていないか、CLR は状態をマネージ コードを実行または呼び出しを正常に処理ができません。|  
|HOST_E_TIMEOUT|呼び出しがタイムアウトになりました。|  
|HOST_E_NOT_OWNER|呼び出し元がロックを所有していません。|  
|HOST_E_ABANDONED|イベントがキャンセルされましたブロックされたスレッドまたはファイバーが待機しています。|  
|E_FAIL|不明な致命的なエラーが発生しました。 メソッドから E_FAIL が返された場合、CLR は、プロセス内で使用可能ではなくなりました。 メソッドをホストする後続の呼び出しには、HOST_E_CLRNOTAVAILABLE が返されます。|  
  
## <a name="remarks"></a>Remarks  
 `ExecuteInAppDomain` コントロールを練習をホストできるように管理 over<xref:System.AppDomain>で指定したマネージ メソッドを実行する必要があります。 値に対応するアプリケーション ドメインの識別子の値を取得することができます、<xref:System.AppDomain.Id%2A>プロパティを呼び出すことによって[GetCurrentAppDomainId メソッド](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-getcurrentappdomainid-method.md)します。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:** [システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** MSCorEE.h  
  
 **ライブラリ:** MSCorEE.dll でリソースとして含まれます  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICLRRuntimeHost インターフェイス](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)
