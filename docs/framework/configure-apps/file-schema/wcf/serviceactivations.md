---
title: <serviceActivations>
ms.date: 03/30/2017
ms.assetid: 97e665b6-1c51-410b-928a-9bb42c954ddb
ms.openlocfilehash: 7506cce61966a4a4650ff591cd6106dfd4a33b67
ms.sourcegitcommit: 58fc0e6564a37fa1b9b1b140a637e864c4cf696e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/08/2019
ms.locfileid: "57680413"
---
# <a name="serviceactivations"></a>\<serviceActivations>

仮想サービス アクティベーション設定を定義する設定を追加することができます、Windows Communication Foundation (WCF) サービスの型にマップする構成要素。 これにより、.svc ファイルを使用せずに、WAS/IIS でホストされているサービスをアクティブ化できます。

\<system.ServiceModel>\
\<serviceHostingEnvironment>\
\<serviceActivations>

## <a name="syntax"></a>構文

```xml
<serviceHostingEnvironment>
  <serviceActivations>
    <add factory="String"
         service="String" />
  </serviceActivations>
</serviceHostingEnvironment>
```

## <a name="attributes-and-elements"></a>属性および要素

以降のセクションでは、属性、子要素、および親要素について説明します。

### <a name="attributes"></a>属性

なし。

### <a name="child-elements"></a>子要素

|要素|説明|
|-------------|-----------------|
|[\<add>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-serviceactivations.md)|サービス アプリケーションのアクティベーションを指定する構成要素を追加します。|

### <a name="parent-elements"></a>親要素

|要素|説明|
|-------------|-----------------|
|[\<serviceHostingEnvironment>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md)|環境をホストするサービスがインスタンス化する特定のトランスポートの型を定義します。|

## <a name="remarks"></a>Remarks

web.config ファイルでアクティベーション設定を構成する方法を次の例に示します。

```xml
<configuration>
  <system.serviceModel>
    <serviceHostingEnvironment>
      <serviceActivations>
        <add service="GreetingService" />
      </serviceActivations>
    </serviceHostingEnvironment>
  </system.serviceModel>
</configuration>
```

この構成を使用して、.svc ファイルを使用せずに、GreetingService をアクティブ化できます。

`<serviceHostingEnvironment>` はアプリケーション レベルの構成であることに注意してください。 構成を格納した `web.config` は、仮想アプリケーションのルートの下に配置する必要があります。 さらに、`serviceHostingEnvironment`は machineToApplication の継承可能なセクションです。 コンピューターのルートに単一のサービスを登録すると、アプリケーションの各サービスはこのサービスを継承します。

構成ベースのアクティベーションは、http および非 http プロトコル経由のアクティベーションをサポートします。 つまり、.svc、.xoml、.xamlx relativeAddress で拡張機能が必要です。 既知の buildProviders に対して独自の拡張子をマップできます。これにより、任意の拡張子を使用してサービスをアクティブ化できるようになります。 競合が発生した場合には、`<serviceActivations>` セクションにより、.svc の登録がオーバーライドされます。

## <a name="see-also"></a>関連項目

- <xref:System.ServiceModel.Configuration.ServiceActivationElementCollection>
- <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>
- <xref:System.ServiceModel.ServiceHostingEnvironment>
