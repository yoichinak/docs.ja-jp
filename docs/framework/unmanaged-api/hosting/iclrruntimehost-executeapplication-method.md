---
title: ICLRRuntimeHost::ExecuteApplication メソッド
ms.date: 03/30/2017
api_name:
- ICLRRuntimeHost.ExecuteApplication
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeHost::ExecuteApplication
helpviewer_keywords:
- ICLRRuntimeHost::ExecuteApplication method [.NET Framework hosting]
- ExecuteApplication method [.NET Framework hosting]
ms.assetid: 5f28cc4e-7176-4e00-aa1f-58ae6ee52fe4
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3c2a56d153fcd7238f58c9650b8db08b3f39edaa
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2019
ms.locfileid: "57496275"
---
# <a name="iclrruntimehostexecuteapplication-method"></a>ICLRRuntimeHost::ExecuteApplication メソッド
マニフェスト ベースの ClickOnce 配置のシナリオで使用すると、新しいドメインでアクティブ化するアプリケーションを指定します。 これらのシナリオの詳細については、次を参照してください。 [ClickOnce Security and Deployment](/visualstudio/deployment/clickonce-security-and-deployment)します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT ExecuteApplication(  
    [in] LPCWSTR   pwzAppFullName,  
    [in] DWORD     dwManifestPaths,  
    [in] LPCWSTR   *ppwzManifestPaths,  
    [in] DWORD     dwActivationData,  
    [in] LPCWSTR   *ppwzActivationData,  
    [out] int      *pReturnValue  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `pwzAppFullName`  
 [in]に対して定義されている、アプリケーションの完全名<xref:System.ApplicationIdentity>します。  
  
 `dwManifestPaths`  
 [in]含まれる文字列の数、`ppwzManifestPaths`配列。  
  
 `ppwzManifestPaths`  
 [in] オプション。 アプリケーションのマニフェストのパスを含む文字列配列。  
  
 `dwActivationData`  
 [in]含まれる文字列の数、`ppwzActivationData`配列。  
  
 `ppwzActivationData`  
 [in] オプション。 Web 経由でデプロイされたアプリケーションの URL のクエリ文字列部分などのアプリケーションのアクティベーション データを含む文字列配列。  
  
 `pReturnValue`  
 [out]アプリケーションのエントリ ポイントから返される値。  
  
## <a name="return-value"></a>戻り値  
  
|HRESULT|説明|  
|-------------|-----------------|  
|S_OK|`ExecuteApplication` 正常に返されます。|  
|HOST_E_CLRNOTAVAILABLE|共通言語ランタイム (CLR) は、プロセスに読み込まれていないか、CLR は状態をマネージ コードを実行または呼び出しを正常に処理ができません。|  
|HOST_E_TIMEOUT|呼び出しがタイムアウトになりました。|  
|HOST_E_NOT_OWNER|呼び出し元がロックを所有していません。|  
|HOST_E_ABANDONED|イベントがキャンセルされましたブロックされたスレッドまたはファイバーが待機しています。|  
|E_FAIL|不明な致命的なエラーが発生しました。 メソッドから E_FAIL が返された場合、CLR は、プロセス内で使用可能ではなくなりました。 メソッドをホストする後続の呼び出しには、HOST_E_CLRNOTAVAILABLE が返されます。|  
  
## <a name="remarks"></a>Remarks  
 `ExecuteApplication` 新しく作成されたアプリケーション ドメインで ClickOnce アプリケーションをアクティブ化に使用されます。  
  
 `pReturnValue`出力パラメーターが、アプリケーションによって返される値に設定します。 場合は null の値を指定する場合`pReturnValue`、`ExecuteApplication`失敗しませんが、値を返さない。  
  
> [!IMPORTANT]
>  呼び出すのではない、 [Start メソッド](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md)メソッドを呼び出す前に、`ExecuteApplication`マニフェスト ベースのアプリケーションをアクティブ化するメソッド。 場合、`Start`メソッドが最初に、呼び出された、`ExecuteApplication`メソッドの呼び出しが失敗します。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** MSCorEE.h  
  
 **ライブラリ:** MSCorEE.dll でリソースとして含まれます  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目
- <xref:System.ActivationContext>
- <xref:System.AppDomainManager>
- <xref:System.ApplicationIdentity>
- [ICLRRuntimeHost インターフェイス](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)
- [SetAppDomainManager メソッド](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-setappdomainmanager-method.md)
- [チュートリアル: デザイナーを使用し、ClickOnce 配置 API で必要に応じてアセンブリをダウンロードする](/visualstudio/deployment/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api-using-the-designer)
