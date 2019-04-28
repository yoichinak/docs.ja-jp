---
title: WSTrustChannelFactory および WSTrustChannel
ms.date: 03/30/2017
ms.assetid: 96cec467-e963-4132-b18b-7d0b3a2e979f
author: BrucePerlerMS
ms.openlocfilehash: ecc62292b2b064219127c369f43141a31ffe606d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61780069"
---
# <a name="wstrustchannelfactory-and-wstrustchannel"></a>WSTrustChannelFactory および WSTrustChannel
Windows Communication Foundation (WCF) をよくご存じの方は、WCF クライアントが既にフェデレーションに対応していることを理解されていると思います。 <xref:System.ServiceModel.WSFederationHttpBinding> または同様のカスタム バインドを使用して WCF クライアントを構成することで、サービスに対するフェデレーション認証を有効にすることができます。

 WCF は、背後でセキュリティ トークン サービス (STS) によって発行されるトークンを取得し、このトークンを使用してサービスに対する認証を行います。 この方法の主要な制限は、クライアントのサーバーとの通信に可視性がないことです。 WCF は、バインドの発行済みトークンのパラメーターに基づいて、STS へのセキュリティ トークン要求 (RST) を自動的に生成します。 つまり、クライアントは、要求ごとに RST パラメーターを変更したり、表示クレームなどの情報を取得するためにセキュリティ トークン要求に対する応答 (RSTR) を調べたりできません。また、トークンを後で使用できるようにキャッシュできません。

 現在、WCF クライアントは基本的なフェデレーション シナリオに適しています。 ただし、Windows Identity Foundation (WIF) によってサポートされる主要なシナリオの 1 つでは、WCF で簡単に実現できないレベルで RST を制御する必要があります。 このため、WIF には、STS との通信をより細かく制御できる機能が追加されています。

 WIF は、次のフェデレーション シナリオをサポートします。

- WIF の依存関係のない WCF クライアントを使用して、フェデレーション サービスに対して認証を行う。

- WCF クライアントで WIF を有効にして、ActAs 要素または OnBehalfOf 要素を STS への RST に挿入する。

- WIF を単独で使用して、STS からトークンを取得し、WCF クライアントがこのトークンを使用して認証できるようにする。 詳細については、[ClaimsAwareWebService](https://go.microsoft.com/fwlink/?LinkID=248406) サンプルを参照してください。

 最初のシナリオでは、一目瞭然です。既存の WCF クライアントは引き続き WIF 証明書利用者および Sts を使用します。 このトピックでは、残りの 2 つのシナリオについて説明します。

## <a name="enhancing-an-existing-wcf-client-with-actas--onbehalfof"></a>ActAs または OnBehalfOf を使用した既存の WCF クライアントの拡張
一般的な ID 委任シナリオでは、クライアントは、中間層サービスを呼び出します。この中間層サービスによって、バックエンド サービスが呼び出されます。 中間層サービスは、クライアントとして、またはクライアントの代わりに機能します。

> [!TIP]
> ActAs と OnBehalfOf の違い
>
> Ws-trust プロトコルの観点: から
>
> 1. ActAs RST 要素は、要求元が 2 つの個別のエンティティに関するクレームを含んだトークンを要求していることを示します。それは、要求元と、ActAs 要素内のトークンによって表される外部エンティティです。
> 2. OnBehalfOf RST 要素は、要求元が 1 つのエンティティに関するクレームだけを含んだトークンを要求していることを示します。それは、OnBehalfOf 要素内のトークンによって表される外部エンティティです。
>
> ActAs 機能は、通常、発行されたトークンの最終受信者が委任チェーン全体を調べて、クライアントだけでなく、すべての中継者を参照できる複合委任を必要とするシナリオで使用されます。 これにより、最終受信者は、ID 委任チェーン全体に基づいてアクセス制御、監査、その他の関連アクティビティを実行できます。 ActAs 機能は、アプリケーション層/ビジネス ロジック層で ID に関する情報を渡さずに、層間で ID に関する情報を認証して渡すために多階層システムでよく使用されます。
>
> OnBehalfOf 機能は、元のクライアントの ID のみが重要であるシナリオで使用されます。この機能は、Windows で使用できる ID 偽装機能と実質的に同じです。 OnBehalfOf を使用すると、発行されたトークンの最終受信者は、元のクライアントに関するクレームのみを参照できます。中継者に関する情報は保持されません。 OnBehalfOf 機能が使用される一般的なパターンの 1 つは、クライアントが STS に直接アクセスできず、代わりにプロキシ ゲートウェイを経由して通信するプロキシ パターンです。 プロキシ ゲートウェイは、呼び出し元を認証し、RST メッセージの OnBehalfOf 要素に呼び出し元に関する情報を格納します。そのメッセージは、実際の STS に送信され、処理されます。 生成されるトークンには、プロキシのクライアントに関連するクレームだけが含まれるので、プロキシは、発行されたトークンの受信者にとって完全に透過的に機能します。WIF では、\<wsse:SecurityTokenReference> または \<wsa:EndpointReferences> を \<wst:OnBehalfOf> の子としてサポートしていません。 WS-Trust の仕様では、(プロキシが代理を務めている) 元の要求元を識別する方法が 3 つ用意されています。 これらの数値は、次のとおりです。
>
> - セキュリティ トークンの参照。 メッセージに含まれるトークンまたはアウトオブバンドで取得される可能性があるトークンへの参照。
> - エンドポイント参照。 アウトオブバンドでデータを再度検索するためにキーとして使用されます。
> - セキュリティ トークン。 元の要求元を直接識別します。
>
> WIF では、\<wst:OnBehalfOf> の直接の子要素として、(暗号化されたまたは暗号化されていない) セキュリティ トークンをサポートします。

 この情報は、RST の ActAs トークン要素と OnBehalfOf トークン要素を使用して WS-Trust 発行者に伝達されます。

 WCF では、任意の XML 要素を RST に追加できる、バインドの機能拡張ポイントを公開しています。 ただし、機能拡張ポイントはバインドに関連付けられているため、呼び出しごとに RST の内容を変更する必要があるシナリオでは、呼び出しごとにクライアントを再作成する必要があります。この場合、パフォーマンスが低下します。 WIF では、`ChannelFactory` クラスの拡張メソッドを使用して、アウトオブバンドで取得した任意のトークンを開発者が RST に添付できるようにします。 次のコード例では、クライアント (X.509、ユーザー名、SAML (Security Assertion Markup Language) トークンなど) を表すトークンを取得し、発行者に送信される RST にそれを添付する方法を示します。

```csharp
IHelloService serviceChannel = channelFactory.CreateChannelActingAs<IHelloService>(clientSamlToken);
serviceChannel.Hello("Hi!");
```

 WIF には次のような利点があります。

- RST をチャネルごとに変更できます。したがって、中間層サービスは、各クライアントのチャネル ファクトリを再作成する必要がないので、パフォーマンスが向上します。

- 既存の WCF クライアントと動作するので、ID 委任セマンティクスを有効にする必要がある既存の WCF 中間層サービスの簡単なアップグレード パスとなります。

 ただし、それでもクライアントの STS との通信に可視性はありません。 3 番目のシナリオでは、これについて説明します。

## <a name="communicating-directly-with-an-issuer-and-using-the-issued-token-to-authenticate"></a>発行者との直接通信および発行されたトークンを使った認証
一部の高度なシナリオでは、WCF クライアントを拡張するだけでは十分ではありません。 WCF だけを使用する開発者は、通常、Message In/Message Out コントラクトを使用し、発行者の応答のクライアント側解析を手動で処理します。

WIF には、クライアントが WS-Trust 発行者と直接通信できる <xref:System.ServiceModel.Security.WSTrustChannelFactory> クラスと <xref:System.ServiceModel.Security.WSTrustChannel> クラスが用意されています。 次のコード例に示すように、<xref:System.ServiceModel.Security.WSTrustChannelFactory> クラスと <xref:System.ServiceModel.Security.WSTrustChannel> クラスを使用すると、厳密に型指定された RST オブジェクトと RSTR オブジェクトをクライアントと発行者の間でやり取りできます。

```csharp
WSTrustChannelFactory trustChannelFactory = new WSTrustChannelFactory(stsBinding, stsAddress);
WSTrustChannel channel = (WSTrustChannel) trustChannelFactory.CreateChannel();
RequestSecurityToken rst = new RequestSecurityToken(RequestTypes.Issue);
rst.AppliesTo = new EndpointAddress(serviceAddress);
RequestSecurityTokenResponse rstr = null;
SecurityToken token = channel.Issue(rst, out rstr);
```

`out` メソッドで <xref:System.ServiceModel.Security.WSTrustChannel.Issue%2A> パラメーターを指定することで、クライアント側で検査するために RSTR にアクセスできます。

ここまでは、トークンを取得する方法のみを説明しました。 <xref:System.ServiceModel.Security.WSTrustChannel> オブジェクトから返されるトークンは、証明書利用者に対して認証を行うために必要な情報がすべて格納された `GenericXmlSecurityToken` オブジェクトです。 次のコード例では、このトークンを使用する方法を示します。

```csharp
IHelloService serviceChannel = channelFactory.CreateChannelWithIssuedToken<IHelloService>( token );
serviceChannel.Hello("Hi!");
```

<xref:System.ServiceModel.ChannelFactory%601.CreateChannelWithIssuedToken%2A> オブジェクトの `ChannelFactory` 拡張メソッドは、トークンをアウトオブバンドで取得したこと、発行者に対する通常の WCF 呼び出しを停止して、代わりに取得したトークンを使用して証明書利用者に対して認証を行う必要があることを WIF に示します。 これには、次のような利点があります。

- トークン発行プロセスを完全に制御できます。

- 送信 RST で ActAs または OnBehalfOf のプロパティを直接設定することで、ActAs または OnBehalfOf のシナリオをサポートします。

- 動的なクライアント側の信頼の決定を RSTR の内容に基づいて行うことができます。

- <xref:System.ServiceModel.Security.WSTrustChannel.Issue%2A> メソッドから返されたトークンをキャッシュして再利用できます。

- <xref:System.ServiceModel.Security.WSTrustChannelFactory> と <xref:System.ServiceModel.Security.WSTrustChannel> により、WCF のベスト プラクティスに従ってチャネル キャッシュ、エラー、および復元のセマンティクスを制御できます。

## <a name="see-also"></a>関連項目

- [WIF の機能](../../../docs/framework/security/wif-features.md)