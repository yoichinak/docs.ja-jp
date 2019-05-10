---
title: <serviceHostingEnvironment>
ms.date: 03/30/2017
ms.assetid: 4f8a7c4f-e735-4987-979a-b74fcdae2652
ms.openlocfilehash: 16dacee89576b4ede0f2f80255ba8a0dcbc8c0dc
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2019
ms.locfileid: "64610185"
---
# <a name="servicehostingenvironment"></a>\<serviceHostingEnvironment>
この要素は、環境をホストするサービスがインスタンス化する特定のトランスポートの型を定義します。 この要素が空の場合は、既定の型が使用されます。 この要素は、アプリケーション レベルまたはコンピューター レベルの構成ファイルでのみ使用できます。  
  
 \<system.ServiceModel >  
\<serviceHostingEnvironment >  
  
## <a name="syntax"></a>構文  
  
```xml  
<serviceHostingEnvironment aspNetCompatibilityEnabled="Boolean"
                           minFreeMemoryPercentageToActivateService="Integer"
                           multipleSiteBindingsEnabled="Boolean">
  <baseAddressPrefixFilters>
    <add prefix="string" />
  </baseAddressPrefixFilters>
  <serviceActivations>
    <add factory="String"
         service="String" />
  </serviceActivations>
  <transportConfigurationTypes>
    <add name="String"
         transportConfigurationType="String" />
  </transportConfigurationTypes>
</serviceHostingEnvironment>
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|aspNetCompatibilityEnabled|ASP.NET の互換モードが現在のアプリケーションに対して有効になっているかどうかを示すブール値。 既定値は `false` です。<br /><br /> この属性を設定すると`true`、Windows Communication Foundation (WCF) サービスへの要求を ASP.NET HTTP パイプラインを通過し、非 HTTP プロトコルを介した通信は禁止されています。 詳細については、次を参照してください。 [WCF サービスと ASP.NET](../../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md)します。|  
|minFreeMemoryPercentageToActivateService|WCF サービスをアクティブにする前に、システムに利用できるように、空きメモリの最小量を指定する整数。 **注意:** WCF サービスの web.config ファイルで部分信頼と共にこの属性を指定するが、<xref:System.Security.SecurityException>サービスを実行するとします。|  
|multipleSiteBindingsEnabled|1 つのサイトで複数の IIS バインディングが有効になっているかどうかを指定するブール値。<br /><br /> IIS は、仮想ディレクトリを含む仮想アプリケーションのコンテナーとしての Web サイトで構成されています。 サイト内のアプリケーションに、1 つ以上の IIS バインディングからアクセスできます。 IIS バインディングは、バインディング プロトコルとバインディング情報という 2 つの情報を提供します。 バインディング プロトコルは通信を行うスキームを定義するもので、バインディング情報はサイトにアクセスするために使用する情報です。 バインディング プロトコルの例には HTTP があり、一方、バインディング情報には IP アドレス、ポート、ホスト ヘッダーなどを含めることができます。<br /><br /> IIS ではサイトごとに複数の IIS バインディングを指定でき、これによりスキームごとに複数のベース アドレスをサポートできます。 ただし、サイトでホストされている Windows Communication Foundation (WCF) サービスは、スキームごとの 1 つのみの baseAddress へのバインドを許可します。<br /><br /> Windows Communication Foundation (WCF) サービスの 1 つのサイトの複数の IIS バインディングを有効にするのにはこの属性設定`true`します。 複数のサイト バインディングは HTTP プロトコルに対してのみサポートされています。 構成ファイル内のエンドポイントのアドレスには完全な URI を指定する必要があります。|  
  
### <a name="child-elements"></a>子要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<baseAddressPrefixFilters>](../../../../../docs/framework/configure-apps/file-schema/wcf/baseaddressprefixfilters.md)|サービス ホストによって使用されるベース アドレスのプレフィックス フィルターを指定する構成要素のコレクション。|  
|[\<serviceActivations>](../../../../../docs/framework/configure-apps/file-schema/wcf/serviceactivations.md)|アクティベーション設定を記述する構成セクション。|  
|[\<transportConfigurationTypes>](../../../../../docs/framework/configure-apps/file-schema/wcf/transportconfigurationtypes.md)|特定のトランスポートの型を識別する構成要素のコレクション。|  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|serviceModel|すべての Windows Communication Foundation (WCF) 構成要素のルート要素です。|  
  
## <a name="remarks"></a>Remarks  
 既定では、WCF サービスは、ホストされるアプリケーション ドメイン (AppDomain) で ASP.NET と並行で実行します。 WCF と ASP.NET が同じ AppDomain で共存できても、既定では WCF 要求は ASP.NET HTTP パイプラインでは処理されません。 結果として、ASP.NET アプリケーション プラットフォームのいくつかの要素は、WCF サービスでは使用できません。 これらの要素は次のとおりです。  
  
- ASP.NET ファイル/URL 承認  
  
- ASP.NET の偽装  
  
- クッキー ベースのセッションの状態  
  
- HttpContext.Current  
  
- カスタム HttpModule を経由するパイプライン拡張  
  
 WCF サービスが ASP.NET のコンテキストで機能し、HTTP 経由でのみ通信する必要がある場合は、WCF の ASP.NET 互換モードを使用できます。 このモードは、`aspNetCompatibilityEnabled` 属性がアプリケーション レベルで `true` に設定されている場合に有効です。 サービス実装では、<xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> クラスを使用して互換モードで実行できる機能を宣言する必要があります。 互換モードが有効な場合、  
  
- ASP.NET ファイル/URL 承認が、WCF 承認の前に強制的に実行されます。 承認決定は、要求のトランスポート レベルの ID に基づいています。 メッセージ レベルでの ID は、無視されます。  
  
- WCF サービス操作は、ASP.NET の偽装コンテキストで実行を開始します。 ASP.NET の偽装と WCF の偽装の両方が特定のサービスで有効な場合は、WCF の偽装コンテキストが適用されます。  
  
- HttpContext.Current を WCF サービス コードから使用できるため、サービスは非 HTTP エンドポイントを公開しません。  
  
- WCF 要求は、ASP.NET パイプラインによって処理されます。 受信要求を処理するように構成された HttpModules は、WCF 要求も処理できます。 これらには、ASP.NET プラットフォーム コンポーネント (<xref:System.Web.SessionState.SessionStateModule> など) とカスタム サードパーティ モジュールが含まれます。  
  
## <a name="example"></a>例  
 次のコード サンプルは、ASP 互換モードを有効にする方法を示します。  
  
## <a name="code"></a>コード  
  
```xml  
<serviceHostingEnvironment aspNetCompatibilityEnabled="true"/>
```  
  
## <a name="see-also"></a>関連項目

- <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>
- <xref:System.ServiceModel.ServiceHostingEnvironment>
- [ホスティング](../../../../../docs/framework/wcf/feature-details/hosting.md)
- [WCF サービスと ASP.NET](../../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md)
