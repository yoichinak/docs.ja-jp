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
ms.openlocfilehash: 9b142f1a05036eddf44c69d8b7da95091dc8f445
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69963087"
---
# <a name="iclrdomainmanagersetappdomainmanagertype-method"></a>ICLRDomainManager::SetAppDomainManagerType メソッド
既定のアプリケーションドメインを初期化する<xref:System.AppDomainManager?displayProperty=nameWithType>ために使用されるアプリケーションドメインマネージャーのクラスから派生した型を指定します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT SetAppDomainManagerType(  
    [in] LPCWSTR wszAppDomainManagerAssembly,  
    [in] LPCWSTR wszAppDomainManagerType,  
    [in] EInitializeNewDomainFlags dwInitializeDomainFlags  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `wszAppDomainManagerAssembly`  
 からアプリケーションドメインマネージャーの種類を含むアセンブリの表示名です。例えば："このような場合、バージョン = 1.0.0.0, Culture = ニュートラル, PublicKeyToken = 6856bccf150f00b3" のようになります。  
  
 `wszAppDomainManagerType`  
 から名前空間を含む、アプリケーションドメインマネージャーの型名。  
  
 `dwInitializeDomainFlags`  
 からアプリケーションドメインマネージャーに関する情報を提供する[EInitializeNewDomainFlags](../../../../docs/framework/unmanaged-api/hosting/einitializenewdomainflags-enumeration.md)列挙値の組み合わせ。  
  
## <a name="return-value"></a>戻り値  
 このメソッドは、次の特定の HRESULT と、メソッドの失敗を示す HRESULT エラーも返します。  
  
|HRESULT|説明|  
|-------------|-----------------|  
|S_OK|メソッドは正常に完了しました。|  
|HOST_E_CLRNOTAVAILABLE|共通言語ランタイム (CLR) がプロセスに読み込まれていないか、CLR がマネージコードを実行できない状態であるか、または呼び出しが正常に処理されていません。|  
  
## <a name="remarks"></a>Remarks  
 現時点では、に対し`dwInitializeDomainFlags`て定義されている値はのみです`eInitializeNewDomainFlags_NoSecurityChanges`。これは、アプリケーションドメインマネージャーが<xref:System.AppDomainManager.InitializeNewDomain%2A?displayProperty=nameWithType>メソッドの実行中にセキュリティ設定を変更しないことを共通言語ランタイム (CLR) に通知します。 これにより、CLR は条件付き<xref:System.Security.AllowPartiallyTrustedCallersAttribute> (APTCA) 属性を持つアセンブリの読み込みを最適化できます。 これにより、このアセンブリセットの推移的なクロージャが大きい場合に、起動時間が大幅に向上する可能性があります。  
  
> [!IMPORTANT]
> ホストがアプリケーションドメイン`eInitializeNewDomainFlags_NoSecurityChanges`マネージャーに対してを指定し<xref:System.InvalidOperationException>た場合、アプリケーションドメインのセキュリティを変更しようとすると、がスローされます。  
  
 [ICLRControl:: SetAppDomainManagerType](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-setappdomainmanagertype-method.md)メソッドを呼び出すことは、 `ICLRDomainManager::SetAppDomainManagerType`を`eInitializeNewDomainFlags_None`使用してを呼び出すことと同じです。  
  
## <a name="requirements"></a>必要条件  
 **・** [システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** メタホスト .h  
  
 **ライブラリ**Mscoree.dll にリソースとして含まれています  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ホスティング](../../../../docs/framework/unmanaged-api/hosting/index.md)
- [ICLRDomainManager インターフェイス](../../../../docs/framework/unmanaged-api/hosting/iclrdomainmanager-interface.md)
- [EInitializeNewDomainFlags 列挙型](../../../../docs/framework/unmanaged-api/hosting/einitializenewdomainflags-enumeration.md)
