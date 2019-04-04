---
title: メッセージ セキュリティと匿名クライアント
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: cad53e1a-b7c9-4064-bc87-508c3d1dce49
ms.openlocfilehash: 613b85e18109faa2a4386090e91aaddcfd8e0b68
ms.sourcegitcommit: 58fc0e6564a37fa1b9b1b140a637e864c4cf696e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/08/2019
ms.locfileid: "57680310"
---
# <a name="message-security-with-an-anonymous-client"></a>メッセージ セキュリティと匿名クライアント

次のシナリオでは、クライアントと Windows Communication Foundation (WCF) メッセージ セキュリティで保護されたサービスを説明します。 設計目標は、トランスポート セキュリティではなくメッセージ セキュリティを使用することです。これによって将来、多様なクレームに基づくモデルをサポートできます。 承認に多様なクレームの使用に関する詳細については、[管理クレームと Id モデルでの承認](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md)を参照してください。

サンプル アプリケーションでは、[メッセージ セキュリティ匿名](../../../../docs/framework/wcf/samples/message-security-anonymous.md)を参照してください。

![メッセージ セキュリティと匿名クライアント](../../../../docs/framework/wcf/feature-details/media/b361a565-831c-4c10-90d7-66d8eeece0a1.gif "b361a565-831c-4c10-90d7-66d8eeece0a1")

|特徴|説明|
|--------------------|-----------------|
|セキュリティ モード|メッセージ|
|相互運用性|WCF のみ|
|認証 (サーバー)|初期ネゴシエーションには、サーバー認証が必要ですが、クライアント認証は不要です|
|認証 (クライアント)|なし|
|整合性|はい、共有のセキュリティ コンテキストを使用します|
|機密性|はい、共有のセキュリティ コンテキストを使用します|
|Transport|HTTP|

## <a name="service"></a>サービス

次のコードと構成は、別々に実行します。 次のいずれかの操作を行います。

- 構成を使用せずに、コードを使用してスタンドアロン サービスを作成します。

- 提供された構成を使用してサービスを作成しますが、エンドポイントを定義しません。

### <a name="code"></a>コード

次のコードは、メッセージ セキュリティを使用するサービス エンドポイントの作成方法を示します。

[!code-csharp[C_SecurityScenarios#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#8)]
[!code-vb[C_SecurityScenarios#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#8)]

### <a name="configuration"></a>構成

コードの代わりに次の構成を使用できます。 サービス動作要素を使用して、クライアントに対するサービスの認証に使用する証明書を指定します。 サービス要素は、`behaviorConfiguration` 属性を使用して動作を指定する必要があります。 バインド要素で、クライアント資格情報の種類が `None` であることを指定します。この資格情報の種類では、匿名クライアントがサービスを使用できます。

```xml
<?xml version="1.0" encoding="utf-8"?>
<configuration>
  <system.serviceModel>
    <behaviors>
      <serviceBehaviors>
        <behavior name="ServiceCredentialsBehavior">
          <serviceCredentials>
            <serviceCertificate findValue="contoso.com"
                                storeLocation="LocalMachine"
                                storeName="My" />
          </serviceCredentials>
        </behavior>
      </serviceBehaviors>
    </behaviors>
    <services>
      <service behaviorConfiguration="ServiceCredentialsBehavior"
               name="ServiceModel.Calculator">
        <endpoint address="http://localhost/Calculator"
                  binding="wsHttpBinding"
                  bindingConfiguration="WSHttpBinding_ICalculator"
                  name="CalculatorService"
                  contract="ServiceModel.ICalculator" />
      </service>
    </services>
    <bindings>
      <wsHttpBinding>
        <binding name="WSHttpBinding_ICalculator" >
          <security mode="Message">
            <message clientCredentialType="None" />
          </security>
        </binding>
      </wsHttpBinding>
    </bindings>
    <client />
  </system.serviceModel>
</configuration>
```

## <a name="client"></a>Client

次のコードと構成は、別々に実行します。 次のいずれかの操作を行います。

- コード (およびクライアント コード) を使用してスタンドアロン クライアントを作成します。

- エンドポイント アドレスを定義しないクライアントを作成します。 代わりに、引数として構成名を受け取るクライアント コンストラクターを使用します。 次に例を示します。

    [!code-csharp[C_SecurityScenarios#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#0)]
    [!code-vb[C_SecurityScenarios#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#0)]

### <a name="code"></a>コード

クライアントのインスタンスを作成するコード例を次に示します。 バインディングはメッセージ モード セキュリティを使用し、クライアント資格情報の種類は None に設定されます。

[!code-csharp[C_SecurityScenarios#15](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#15)]
[!code-vb[C_SecurityScenarios#15](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#15)]

### <a name="configuration"></a>構成

クライアントを構成する場合のコード例を次に示します。

```xml
<?xml version="1.0" encoding="utf-8"?>
<configuration>
  <system.serviceModel>
    <bindings>
      <wsHttpBinding>
        <binding name="WSHttpBinding_ICalculator" >
          <security mode="Message">
            <message clientCredentialType="None" />
          </security>
        </binding>
      </wsHttpBinding>
    </bindings>
    <client>
      <endpoint address="http://machineName/Calculator"
        binding="wsHttpBinding"
        bindingConfiguration="WSHttpBinding_ICalculator"
        contract="ICalculator"
        name="WSHttpBinding_ICalculator">
        <identity>
          <dns value="contoso.com" />
        </identity>
      </endpoint>
    </client>
  </system.serviceModel>
</configuration>
```

## <a name="see-also"></a>関連項目

- [セキュリティの概要](../../../../docs/framework/wcf/feature-details/security-overview.md)
- [分散アプリケーションのセキュリティ](../../../../docs/framework/wcf/feature-details/distributed-application-security.md)
- [メッセージ セキュリティ匿名](../../../../docs/framework/wcf/samples/message-security-anonymous.md)
- [サービス ID と認証](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)
- [Windows Server App Fabric のセキュリティ モデル](https://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
