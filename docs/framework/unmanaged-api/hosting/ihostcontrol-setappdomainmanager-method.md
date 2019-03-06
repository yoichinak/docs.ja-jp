---
title: IHostControl::SetAppDomainManager メソッド
ms.date: 03/30/2017
api_name:
- IHostControl.SetAppDomainManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostControl::SetAppDomainManager
helpviewer_keywords:
- IHostControl::SetAppDomainManager method [.NET Framework hosting]
- SetAppDomainManager method [.NET Framework hosting]
ms.assetid: 6562bbe7-0d67-4c50-a958-3a18cf680375
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 83461f89be9a16305da2732536dcc6847b45027d
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2019
ms.locfileid: "57482562"
---
# <a name="ihostcontrolsetappdomainmanager-method"></a>IHostControl::SetAppDomainManager メソッド
アプリケーション ドメインが作成されたことをホストに通知します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT SetAppDomainManager (  
    [in] DWORD     dwAppDomainID,  
    [in] IUnknown* pUnkAppDomainManager  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `dwAppDomainID`  
 [in]選択した数値識別子<xref:System.AppDomain>します。  
  
 `pUnkAppDomainManager`  
 [in]ポインター、<xref:System.AppDomainManager>としてホストを実装するオブジェクト`IUnknown`します。  
  
## <a name="return-value"></a>戻り値  
  
|HRESULT|説明|  
|-------------|-----------------|  
|S_OK|`SetAppDomainManager` 正常に返されます。|  
|HOST_E_CLRNOTAVAILABLE|共通言語ランタイム (CLR) は、プロセスに読み込まれていないか、CLR は状態をマネージ コードを実行または呼び出しを正常に処理ができません。|  
|HOST_E_TIMEOUT|呼び出しがタイムアウトになりました。|  
|HOST_E_NOT_OWNER|呼び出し元がロックを所有していません。|  
|HOST_E_ABANDONED|イベントがキャンセルされましたブロックされたスレッドまたはファイバーが待機しています。|  
|E_FAIL|不明な致命的なエラーが発生しました。 メソッドには、E_FAIL が返される、ときに、CLR は、プロセス内で使用可能ではなくなりました。 メソッドをホストする後続の呼び出しには、HOST_E_CLRNOTAVAILABLE が返されます。|  
  
## <a name="remarks"></a>Remarks  
 <xref:System.AppDomainManager>により、ホストにマネージ コードをブートス トラップを作成およびそれぞれの設定を制御するメカニズムで<xref:System.AppDomain>します。 <xref:System.AppDomainManager>それぞれに読み込まれる<xref:System.AppDomain>ときを<xref:System.AppDomain>が作成されます。 選択した場合、CLR をホストに通知の値を設定して、アプリケーション ドメインが作成されたこと、`pUnkAppDomainManager`パラメーター。  
  
 実装で、`SetAppDomainManager`メソッド、ホスト設定できますアセンブリの名前と種類のアプリケーション ドメイン マネージャー。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** MSCorEE.h  
  
 **ライブラリ:** MSCorEE.dll でリソースとして含まれます  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目
- <xref:System.AppDomain>
- <xref:System.AppDomainManager>
- [IHostControl インターフェイス](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)
