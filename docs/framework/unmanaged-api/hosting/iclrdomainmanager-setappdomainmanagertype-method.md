---
title: ICLRDomainManager::SetAppDomainManagerType メソッド
ms.date: 03/30/2017
api_name:
- ICLRDomainManager.SetAppDomainManagerType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRDomainManager::SetAppDomainManagerType
helpviewer_keywords:
- SetAppDomainManagerType method, ICLRDomainManager interface [.NET Framework hosting]
- ICLRDomainManager::SetAppDomainManagerType method [.NET Framework hosting]
ms.assetid: ee91abb0-cb74-41dd-927b-e117fb8ffdf4
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6cfef7d929d40996716a02a4db51630827011a68
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61984777"
---
# <a name="iclrdomainmanagersetappdomainmanagertype-method"></a>ICLRDomainManager::SetAppDomainManagerType メソッド
派生した、型を指定します、<xref:System.AppDomainManager?displayProperty=nameWithType>の既定のアプリケーション ドメインを初期化するために使用されるアプリケーション ドメイン マネージャーのクラス。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT SetAppDomainManagerType(  
    [in] LPCWSTR wszAppDomainManagerAssembly,  
    [in] LPCWSTR wszAppDomainManagerType,  
    [in] EInitializeNewDomainFlags dwInitializeDomainFlags  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `wszAppDomainManagerAssembly`  
 [in]アプリケーション ドメイン マネージャーの種類; を含むアセンブリの表示名例えば："AdMgrExample、バージョン 1.0.0.0、Culture = neutral, PublicKeyToken = = 6856bccf150f00b3"。  
  
 `wszAppDomainManagerType`  
 [in]名前空間を含む、アプリケーション ドメイン マネージャーの型名。  
  
 `dwInitializeDomainFlags`  
 [in]組み合わせた[EInitializeNewDomainFlags](../../../../docs/framework/unmanaged-api/hosting/einitializenewdomainflags-enumeration.md)アプリケーション ドメイン マネージャーに関する情報を提供する列挙値。  
  
## <a name="return-value"></a>戻り値  
 このメソッドは、次の特定の HRESULT と、メソッドの失敗を示す HRESULT エラーも返します。  
  
|HRESULT|説明|  
|-------------|-----------------|  
|S_OK|メソッドは正常に完了しました。|  
|HOST_E_CLRNOTAVAILABLE|共通言語ランタイム (CLR) は、プロセスに読み込まれていないか、CLR は状態をマネージ コードを実行または呼び出しを正常に処理ができません。|  
  
## <a name="remarks"></a>Remarks  
 現時点では、のみ定義されている値の`dwInitializeDomainFlags`は`eInitializeNewDomainFlags_NoSecurityChanges`、共通言語ランタイム (CLR) を指示すると、アプリケーション ドメイン マネージャーが実行中のセキュリティ設定を変更しないこと、<xref:System.AppDomainManager.InitializeNewDomain%2A?displayProperty=nameWithType>メソッド。 これにより、条件付きのアセンブリの読み込みを最適化するために CLR <xref:System.Security.AllowPartiallyTrustedCallersAttribute> (APTCA) 属性。 これは、結果、この一連のアセンブリの推移閉包が大きい場合に、起動時間が大幅に向上。  
  
> [!IMPORTANT]
>  ホストが指定されている場合`eInitializeNewDomainFlags_NoSecurityChanges`のアプリケーション ドメイン マネージャーに、<xref:System.InvalidOperationException>が、アプリケーション ドメインのセキュリティを変更する試行が行われた場合にスローされます。  
  
 呼び出す、 [iclrcontrol::setappdomainmanagertype](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-setappdomainmanagertype-method.md)メソッドを呼び出すことは`ICLRDomainManager::SetAppDomainManagerType`で`eInitializeNewDomainFlags_None`します。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** MetaHost.h  
  
 **ライブラリ:** MSCorEE.dll でリソースとして含まれます  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ホスティング](../../../../docs/framework/unmanaged-api/hosting/index.md)
- [ICLRDomainManager インターフェイス](../../../../docs/framework/unmanaged-api/hosting/iclrdomainmanager-interface.md)
- [EInitializeNewDomainFlags 列挙型](../../../../docs/framework/unmanaged-api/hosting/einitializenewdomainflags-enumeration.md)
