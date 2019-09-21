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
ms.openlocfilehash: 38938de335e5f0d7cb8051554c400f16df012362
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69965357"
---
# <a name="iclrruntimehostexecuteapplication-method"></a>ICLRRuntimeHost::ExecuteApplication メソッド
新しいドメインでアクティブ化するアプリケーションを指定するために、マニフェストベースの ClickOnce 配置シナリオで使用されます。 これらのシナリオの詳細については、「 [ClickOnce のセキュリティと配置](/visualstudio/deployment/clickonce-security-and-deployment)」を参照してください。  
  
## <a name="syntax"></a>構文  
  
```cpp  
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
 からに<xref:System.ApplicationIdentity>定義されているアプリケーションの完全名。  
  
 `dwManifestPaths`  
 から`ppwzManifestPaths`配列に格納されている文字列の数。  
  
 `ppwzManifestPaths`  
 [in] オプション。 アプリケーションのマニフェストパスを格納する文字列配列。  
  
 `dwActivationData`  
 から`ppwzActivationData`配列に格納されている文字列の数。  
  
 `ppwzActivationData`  
 [in] オプション。 Web に配置されたアプリケーションの URL のクエリ文字列部分など、アプリケーションのアクティベーションデータを格納する文字列配列。  
  
 `pReturnValue`  
 入出力アプリケーションのエントリポイントから返される値。  
  
## <a name="return-value"></a>戻り値  
  
|HRESULT|説明|  
|-------------|-----------------|  
|S_OK|`ExecuteApplication`正常に返されました。|  
|HOST_E_CLRNOTAVAILABLE|共通言語ランタイム (CLR) がプロセスに読み込まれていないか、CLR がマネージコードを実行できない状態であるか、または呼び出しが正常に処理されていません。|  
|HOST_E_TIMEOUT|呼び出しがタイムアウトしました。|  
|HOST_E_NOT_OWNER|呼び出し元がロックを所有していません。|  
|HOST_E_ABANDONED|ブロックされたスレッドまたはファイバーが待機しているときに、イベントが取り消されました。|  
|E_FAIL|原因不明の致命的なエラーが発生しました。 メソッドから E_FAIL が返された場合、そのプロセス内で CLR は使用できなくなります。 後続のホストメソッドの呼び出しでは、HOST_E_CLRNOTAVAILABLE が返されます。|  
  
## <a name="remarks"></a>Remarks  
 `ExecuteApplication`は、新しく作成されたアプリケーションドメインで ClickOnce アプリケーションをアクティブ化するために使用されます。  
  
 `pReturnValue`出力パラメーターは、アプリケーションによって返される値に設定されます。 に`pReturnValue`null 値を指定した場合、 `ExecuteApplication`は失敗しませんが、値を返しません。  
  
> [!IMPORTANT]
> `ExecuteApplication`メソッドを呼び出してからマニフェストベースのアプリケーションをアクティブ化する前に、 [Start メソッド](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md)メソッドを呼び出さないでください。 メソッドが最初`ExecuteApplication`に呼び出された場合、メソッドの呼び出しは失敗します。 `Start`  
  
## <a name="requirements"></a>必要条件  
 **・** [システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** Mscoree.dll  
  
 **ライブラリ**Mscoree.dll にリソースとして含まれています  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- <xref:System.ActivationContext>
- <xref:System.AppDomainManager>
- <xref:System.ApplicationIdentity>
- [ICLRRuntimeHost インターフェイス](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)
- [SetAppDomainManager メソッド](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-setappdomainmanager-method.md)
- [チュートリアル: デザイナーを使用し、ClickOnce 配置 API で必要に応じてアセンブリをダウンロードする](/visualstudio/deployment/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api-using-the-designer)
