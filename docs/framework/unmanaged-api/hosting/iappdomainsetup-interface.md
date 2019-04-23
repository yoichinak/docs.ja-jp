---
title: IAppDomainSetup インターフェイス
ms.date: 03/30/2017
api_name:
- IAppDomainSetup
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IAppDomainSetup
helpviewer_keywords:
- IAppDomainSetup interface [.NET Framework hosting]
ms.assetid: 1844da85-c031-40bf-bea4-1a3d12a36c8c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bbde873481aea9de94862117a99079301965f33c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59220072"
---
# <a name="iappdomainsetup-interface"></a>IAppDomainSetup インターフェイス
プロパティを構成するホストを提供します、<xref:System.AppDomain?displayProperty=nameWithType>型を呼び出す前に、 [icorruntimehost::createdomainex](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomainex-method.md)メソッドを作成します。  
  
## <a name="properties"></a>プロパティ  
  
|プロパティ|説明|  
|--------------|-----------------|  
|<xref:System.AppDomainSetup.ApplicationBase%2A>|取得またはアプリケーションを含むディレクトリの名前を設定します。|  
|<xref:System.AppDomainSetup.ApplicationName%2A>|アプリケーションの名前を取得または設定します。|  
|<xref:System.AppDomainSetup.CachePath%2A>|取得または設定領域の名前特定アプリケーションにファイルがシャドウ コピーされた場所。|  
|<xref:System.AppDomainSetup.ConfigurationFile%2A>|取得またはアプリケーションの構成ファイルの名前を設定します。|  
|<xref:System.AppDomainSetup.DynamicBase%2A>|取得または動的に生成されたファイルを格納し、アクセスする場所のディレクトリの名前を設定します。|  
|<xref:System.AppDomainSetup.LicenseFile%2A>|取得またはこのドメインに関連付けられているライセンス ファイルへのパスを設定します。|  
|<xref:System.AppDomainSetup.PrivateBinPath%2A>|取得または設定組み合わせたディレクトリの一覧、<xref:System.AppDomainSetup.ApplicationBase%2A>プライベート アセンブリをプローブするディレクトリ。|  
|<xref:System.AppDomainSetup.PrivateBinPathProbe%2A>|追加または除外する文字列値の設定を取得または<xref:System.AppDomainSetup.ApplicationBase%2A>アプリケーションの検索パスから。|  
|<xref:System.AppDomainSetup.ShadowCopyDirectories%2A>|取得またはアセンブリ シャドウ コピーにはが含まれているディレクトリの名前を設定します。|  
|<xref:System.AppDomainSetup.ShadowCopyFiles%2A>|取得または設定をオンまたはオフ シャドウ コピーになっているかどうかを示す文字列。 有効な値は"true"または"false です"。|  
  
## <a name="remarks"></a>Remarks  
 `IAppDomainSetup`インターフェイスに対応するマネージ<xref:System.IAppDomainSetup>が、インターフェイス、<xref:System.AppDomainSetup>実装を入力します。 参照してください<xref:System.IAppDomainSetup?displayProperty=nameWithType>そのプロパティの詳細についてはします。  
  
 `IAppDomainSetup` 追加できるアセンブリのバインド情報を表す、<xref:System.AppDomain>インスタンスを作成する前にします。 たとえば、ホストを設定できます、<xref:System.AppDomainSetup.ApplicationBase%2A>マネージ アセンブリのプロパティを共通言語ランタイム (CLR) をプローブするルート ディレクトリを作成します。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** MSCorEE.h  
  
 **ライブラリ:** MSCorEE.dll でリソースとして含まれます  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- <xref:System.AppDomain>
- <xref:System.AppDomainSetup>
- <xref:System.IAppDomainSetup>
- [ホスト インターフェイス](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
