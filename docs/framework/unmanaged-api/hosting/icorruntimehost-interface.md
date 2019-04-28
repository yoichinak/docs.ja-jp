---
title: ICorRuntimeHost インターフェイス
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost
helpviewer_keywords:
- ICorRuntimeHost interface [.NET Framework hosting]
ms.assetid: 4369533d-7834-4497-bc37-bfea0ad737b1
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ec893c898a6cd4abffd525056ed0d0169fcbb288
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61700729"
---
# <a name="icorruntimehost-interface"></a>ICorRuntimeHost インターフェイス
ホストが起動し、作成して既定のドメインにアクセスして、プロセスで実行されているすべてのドメインを列挙するために、アプリケーション ドメインを構成する共通言語ランタイム (CLR) を明示的に停止できるようにするメソッドを提供します。  
  
 .NET framework version 2.0 では、このインターフェイスはによって置き換え[ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)します。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[CloseEnum メソッド](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-closeenum-method.md)|ドメイン リストの先頭に戻るには、ドメインの列挙子をリセットします。|  
|[CreateDomain メソッド](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomain-method.md)|アプリケーション ドメインを作成します。 呼び出し元が型のインターフェイス ポインターを受け取る<xref:System._AppDomain>型のインスタンスに<xref:System.AppDomain?displayProperty=nameWithType>します。|  
|[CreateDomainEx メソッド](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomainex-method.md)|アプリケーション ドメインを作成します。 この方法により、呼び出し、返された追加の機能を構成する IAppDomainSetup インスタンス<xref:System._AppDomain>インスタンス。|  
|[CreateDomainSetup メソッド](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomainsetup-method.md)|型のインターフェイス ポインターを取得`IAppDomainSetup`を<xref:System.AppDomainSetup>インスタンス。 `IAppDomainSetup` 作成される前に、アプリケーション ドメインの側面を構成する方法を提供します。|  
|[CreateEvidence メソッド](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createevidence-method.md)|型のインターフェイス ポインターを取得<xref:System.Security.Principal.IIdentity>、ホストに渡すセキュリティ証拠を作成することができます[CreateDomain](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomain-method.md)または[CreateDomainEx](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomainex-method.md)します。|  
|[CreateLogicalThreadState メソッド](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createlogicalthreadstate-method.md)|使用しないでください。|  
|[CurrentDomain メソッド](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-currentdomain-method.md)|型のインターフェイス ポインターを取得<xref:System._AppDomain>を現在のスレッドで読み込まれているドメインを表します。|  
|[DeleteLogicalThreadState メソッド](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-deletelogicalthreadstate-method.md)|使用しないでください。|  
|[EnumDomains メソッド](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-enumdomains-method.md)|現在のプロセスで、ドメインの列挙子を取得します。|  
|[GetConfiguration メソッド](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-getconfiguration-method.md)|ホストは、CLR のコールバックの構成を指定できるようにするオブジェクトを取得します。|  
|[GetDefaultDomain メソッド](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-getdefaultdomain-method.md)|型のインターフェイス ポインターを取得<xref:System._AppDomain>現在のプロセスの既定のドメインを表します。|  
|[LocksHeldByLogicalThread メソッド](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-locksheldbylogicalthread-method.md)|使用しないでください。|  
|[MapFile メソッド](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-mapfile-method.md)|指定したファイルをメモリにマップします。 このメソッドは、互換性のために残されています。|  
|[NextDomain メソッド](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-nextdomain-method.md)|列挙体で、次のドメインへのインターフェイス ポインターを取得します。|  
|[Start メソッド](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-start-method.md)|CLR を開始します。|  
|[Stop メソッド](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-stop-method.md)|現在のプロセスの実行時にコードの実行を停止します。|  
|[SwitchInLogicalThreadState メソッド](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-switchinlogicalthreadstate-method.md)|使用しないでください。|  
|[SwitchOutLogicalThreadState メソッド](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-switchoutlogicalthreadstate-method.md)|使用しないでください。|  
|[UnloadDomain メソッド](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-unloaddomain-method.md)|現在のプロセスから指定したアプリケーション ドメインをアンロードします。|  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** MSCorEE.h  
  
 **ライブラリ:** MSCorEE.dll でリソースとして含まれます  
  
 **.NET framework のバージョン:** 1.0, 1.1  
  
## <a name="see-also"></a>関連項目

- <xref:System.AppDomain>
- [ホスティング](../../../../docs/framework/unmanaged-api/hosting/index.md)
- [ICLRRuntimeHost インターフェイス](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)
- [ランタイム ホスト](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/a51xd4ze(v=vs.100))
- [ホスト インターフェイス](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [CorRuntimeHost コクラス](../../../../docs/framework/unmanaged-api/hosting/corruntimehost-coclass.md)
