---
title: <add> の <serviceActivations>
ms.date: 03/30/2017
ms.assetid: e5b01fc8-ee84-48b7-95fd-95ab54fa871f
ms.openlocfilehash: 929773fcb6b6a3ee5c75aa970147277d9dbe7b45
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69920024"
---
# <a name="add-of-serviceactivations"></a>\<serviceactivations の\<アクティブ化の追加 >

Windows Communication Foundation (WCF) サービスの種類にマップする仮想サービスのアクティブ化の設定を定義できるようにする構成要素。 これにより、.svc ファイルを使用せずに、WAS/IIS でホストされているサービスをアクティブ化できます。

\<system.ServiceModel>\
\<serviceHostingEnvironment >

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

|属性|説明|
|---------------|-----------------|
|factory|サービス アクティベーション要素を生成するファクトリの CLR 型名を指定する文字列。|
|サービス|サービスを実装する ServiceType (完全修飾 Typename または省略形の Typename (App_Code フォルダーに配置されている場合))。|
|relativeAddress|現在の IIS アプリケーション内の相対アドレス (たとえば "Service.svc")。 WCF 4.0 ではこの相対アドレスが 1 個の既知のファイル拡張子 (.svc、.xamlx など) を含む必要があります。relativeUrl 用の物理ファイルは必要ありません。|

### <a name="child-elements"></a>子要素

なし。

### <a name="parent-elements"></a>親要素

|要素|説明|
|-------------|-----------------|
|[\<serviceHostingEnvironment >](servicehostingenvironment.md)|アクティベーション設定を記述する構成セクション。|

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

`<serviceHostingEnvironment>` はアプリケーション レベルの構成であることに注意してください。 構成を格納した `web.config` は、仮想アプリケーションのルートの下に配置する必要があります。 また、 `serviceHostingEnvironment`は machineToApplication 継承可能なセクションです。 コンピューターのルートに単一のサービスを登録すると、アプリケーションの各サービスはこのサービスを継承します。

構成ベースのアクティベーションは、http および非 http プロトコル経由のアクティベーションをサポートします。 RelativeAddress の拡張機能、つまり .svc、xoml、または .xamlx が必要です。 既知の buildProviders に対して独自の拡張子をマップできます。これにより、任意の拡張子を使用してサービスをアクティブ化できるようになります。 競合が発生した場合には、`<serviceActivations>` セクションにより、.svc の登録がオーバーライドされます。

## <a name="see-also"></a>関連項目

- <xref:System.ServiceModel.Configuration.ServiceActivationElement>
- <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>
- <xref:System.ServiceModel.ServiceHostingEnvironment>
