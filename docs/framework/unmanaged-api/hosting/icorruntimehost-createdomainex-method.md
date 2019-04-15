---
title: ICorRuntimeHost::CreateDomainEx メソッド
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost.CreateDomainEx
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::CreateDomainEx
helpviewer_keywords:
- ICorRuntimeHost::CreateDomainEx method [.NET Framework hosting]
- CreateDomainEx method [.NET Framework hosting]
ms.assetid: 1bdde382-f8ba-4cc8-94b2-d1ac919c585e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7a538f14e7dbf24a94343f364201e968bffa757f
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59158926"
---
# <a name="icorruntimehostcreatedomainex-method"></a>ICorRuntimeHost::CreateDomainEx メソッド
アプリケーション ドメインを作成します。 呼び出し元が型のインターフェイス ポインターを受け取る<xref:System._AppDomain>、型のインスタンスに<xref:System.AppDomain?displayProperty=nameWithType>します。 この方法により、呼び出し、返された追加の機能を構成する IAppDomainSetup インスタンス<xref:System._AppDomain>インスタンス。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT CreateDomainEx (  
    [in] LPCWSTR     pwzFriendlyName,  
    [in] IUnknown*   pSetup,  
    [in] IUnknown*   pIdentityArray,  
    [out] IUnknown** pAppDomain  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `pwzFriendlyName`  
 [in]ドメインにわかりやすい名前を指定するために使用する省略可能なパラメーター。 この表示名は、ドメインを識別するためにデバッガーなどのユーザー インターフェイスで表示できます。  
  
 `pSetup`  
 [in]型の省略可能なインターフェイス ポインターを`IAppDomainSetup`への呼び出しで取得した、 [icorruntimehost::createdomainsetup](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomainsetup-method.md)メソッド。  
  
 `pIdentityArray`  
 [in]ポインターの省略可能な配列`IIdentity`権限セットを確立するためにセキュリティ ポリシーを通じて割り当てられる証拠を表すインスタンス。 `IIdentity`オブジェクトを取得するには呼び出すことによって、 [CreateEvidence](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createevidence-method.md)メソッド。  
  
 `pAppDomain`  
 [out]型のインターフェイス ポインターを<xref:System._AppDomain>のインスタンスに<xref:System.AppDomain?displayProperty=nameWithType>さらに、ドメインを制御できます。  
  
## <a name="return-value"></a>戻り値  
  
|HRESULT|説明|  
|-------------|-----------------|  
|S_OK|操作が正常に完了しました。|  
|S_FALSE|操作を完了できませんでした。|  
|E_FAIL|未知の致命的なエラーが発生しました。 場合は、メソッドは、E_FAIL を返します、共通言語ランタイム (CLR) はプロセスで使用可能ではなくなりました。 Api をホストする後続の呼び出しには、HOST_E_CLRNOTAVAILABLE が返されます。|  
|HOST_E_CLRNOTAVAILABLE|プロセスに CLR が読み込まれていないか、CLR は状態をマネージ コードを実行または呼び出しを正常に処理ができません。|  
  
## <a name="remarks"></a>Remarks  
 `CreateDomainEx` 機能を拡張[CreateDomain](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomain-method.md)を渡す呼び出し元を許可することで、`IAppDomainSetup`アプリケーション ドメインを構成するためのプロパティの値を持つインスタンス。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** MSCorEE.h  
  
 **ライブラリ:** MSCorEE.dll でリソースとして含まれます  
  
 **.NET framework のバージョン:** 1.0, 1.1  
  
## <a name="see-also"></a>関連項目

- <xref:System._AppDomain>
- <xref:System.AppDomain>
- <xref:System.IAppDomainSetup?displayProperty=nameWithType>
- [CreateDomain メソッド](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomain-method.md)
- [ICorRuntimeHost インターフェイス](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
