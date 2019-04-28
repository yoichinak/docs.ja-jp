---
title: <add> の <baseAddressPrefixFilter>
ms.date: 03/30/2017
ms.assetid: b226bede-8459-4de9-b2ac-3d39604ce2bc
ms.openlocfilehash: a58a29e44fff3d653d04da271e3b240f2969611f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61673751"
---
# <a name="add-of-baseaddressprefixfilter"></a>\<add> of \<baseAddressPrefixFilter>
パススルー フィルター、IIS で Windows Communication Foundation (WCF) アプリケーションをホストする場合は、適切なインターネット インフォメーション サービス (IIS) バインドを選択するメカニズムを提供するを指定する構成要素を表します。  
  
 \<system.ServiceModel >  
\<serviceHostingEnvironment >  
\<baseAddressPrefixFilters>  
\<add>  
  
## <a name="syntax"></a>構文  
  
```xml  
<serviceHostingEnvironment>
  <baseAddressPrefixFilters>
    <add prefix="String" />
  </baseAddressPrefixFilters>
</serviceHostingEnvironment>
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|prefix|ベース アドレスの一部の一致に使用される URI。|  
  
### <a name="child-elements"></a>子要素  
 なし。  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<baseAddressPrefixFilters>](../../../../../docs/framework/configure-apps/file-schema/wcf/baseaddressprefixfilters.md)|パススルー フィルター、IIS で Windows Communication Foundation (WCF) アプリケーションをホストする場合は、適切な IIS バインドを選択するためのメカニズムを提供するを指定する構成要素のコレクション。|  
  
## <a name="remarks"></a>Remarks  
 プレフィックス フィルターは、サービスによって使用される URI を、共有ホスティング プロバイダーが指定できるようにする手段を提供します。 これにより、共有ホストは、同じサイト上の同じスキームに対して、別々のベース アドレスを使用して複数のアプリケーションをホストできるようになります。  
  
 IIS Web サイトは、仮想ディレクトリを含む仮想アプリケーションのコンテナーです。 サイト内のアプリケーションに、1 つ以上の IIS バインディングからアクセスできます。 IIS バインディングは、バインディング プロトコルとバインディング情報という 2 つの情報を提供します。 バインディング プロトコル (HTTP など) は通信を行うスキームを定義し、バインディング情報 (IP アドレス、ポート、ホスト ヘッダーなど) にはサイトにアクセスするために使用するデータが含まれます。  
  
 IIS では、サイトごとに複数の IIS バインディングを指定できるので、各スキームに複数のベース アドレスが定義されることがあります。 サイトでホストされている WCF サービスにスキームごとに 1 つだけのベース アドレスにバインドが使用できるため、ホステッド サービスの必要なベース アドレスを選択、プレフィックス フィルター機能を使用することができます。 IIS によって指定される受信ベース アドレスは、オプションのプレフィックス リスト フィルターに基づいてフィルター処理されます。  
  
 たとえば、サイトに次のベース アドレスが含まれているとします。  
  
```  
http://testl.fabrikam.com/Service.svc  
http://test2.fabrikam.com/Service.svc  
```  
  
 次の構成ファイルを使用して、appdomain レベルでプレフィックス フィルターを指定できます。  
  
```xml  
<system.serviceModel>
  <serviceHostingEnvironment>
    <baseAddressPrefixFilters>
      <add prefix="net.tcp://test1.fabrikam.com:8000" />
      <add prefix="http://test2.fabrikam.com:9000" />
    </baseAddressPrefixFilters>
  </serviceHostingEnvironment>
</system.serviceModel>
```  
  
 この例では、`net.tcp://test1.fabrikam.com:8000` と `http://test2.fabrikam.com:9000` はそれぞれのスキームにおいて、そのまま渡すことができる唯一のベース アドレスです。  
  
 既定では、プレフィックスを指定しない場合、すべてのアドレスが渡されます。 プレフィックスだけを指定すると、そのスキームに一致するベース アドレスを渡すことができます。  
  
> [!NOTE]
>  フィルターでワイルドカードはサポートされません。 また、IIS が提供する baseAddresses には、`baseAddressPrefixFilters` リストに存在しない他のスキームにバインドされたアドレスが指定される場合があります。 これらのアドレスはフィルターで除外されません。  
  
## <a name="see-also"></a>関連項目

- <xref:System.ServiceModel.Configuration.BaseAddressPrefixFilterElement>
- <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>
- <xref:System.ServiceModel.ServiceHostingEnvironment>
- [ホスティング](../../../../../docs/framework/wcf/feature-details/hosting.md)
