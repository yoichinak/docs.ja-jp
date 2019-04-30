---
title: メッセージング プロトコル
ms.date: 03/30/2017
ms.assetid: 5b20bca7-87b3-4c8f-811b-f215b5987104
ms.openlocfilehash: a5292914cfebc79bf8a9af1c852dd8feec99eba4
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61948123"
---
# <a name="messaging-protocols"></a>メッセージング プロトコル

Windows Communication Foundation (WCF) チャネル スタックには、内部メッセージ表現をワイヤ形式に変換し、特定のトランスポートを使用して送信するエンコーディングとトランスポート チャネルが採用しています。 Web サービスの相互運用性を確保するために、最も一般的に使用されるトランスポートは HTTP です。また、Web サービスが使用する最も一般的なエンコーディングは、XML ベースの SOAP 1.1、SOAP 1.2、および MTOM (Message Transmission Optimization Mechanism) です。

このトピックの内容で採用されている次のプロトコルの実装の詳細を WCF<xref:System.ServiceModel.Channels.HttpTransportBindingElement>します。

仕様/ドキュメント:

- [HTTP 1.1](https://www.ietf.org/rfc/rfc2616.txt)
- [SOAP 1.1 HTTP バインディング](https://www.w3.org/TR/2000/NOTE-SOAP-20000508)セクション 7
- [SOAP 1.2 HTTP バインディング](https://www.w3.org/TR/soap12-part2)セクション 7

このトピックで説明する以下のプロトコルの WCF 実装の詳細<xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>と<xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement>を使用します。

仕様/ドキュメント:

- [XML](https://www.w3.org/TR/REC-xml)
- [SOAP 1.1](https://www.w3.org/TR/2000/NOTE-SOAP-20000508/)
- [SOAP 1.2 コア](https://www.w3.org/TR/soap12-part1/)
- [Ws-addressing 2004/08](https://www.w3.org/Submission/2004/SUBM-ws-addressing-20040810/)
- [W3C Web Services Addressing 1.0 - コア](https://www.w3.org/TR/2006/REC-ws-addr-core-20060509)
- [W3C Web Services Addressing 1.0 - SOAP バインディング](https://www.w3.org/TR/2006/REC-ws-addr-soap-20060509)
- [W3C Web Services Addressing 1.0 - WSDL バインディング](https://www.w3.org/TR/2006/CR-ws-addr-wsdl-20060529/)
- [W3C Web Services Addressing 1.0 - メタデータ](https://www.w3.org/TR/ws-addr-metadata/)
- [WSDL SOAP1.1 バインディング](https://www.w3.org/TR/wsdl/)
- [WSDL SOAP1.2 バインディング](https://www.w3.org/Submission/wsdl11soap12/)

このトピックで説明する以下のプロトコルの WCF 実装の詳細<xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement>を採用しています。

仕様/ドキュメント:

- [XOP](https://www.w3.org/TR/xop10/)
- [MTOM および SOAP 1.2 バインディング](https://www.w3.org/TR/soap12-mtom/)
- [MTOM SOAP 1.1 バインディング](https://www.w3.org/Submission/soap11mtom10/)
- [MTOM Ws-policy アサーション](https://www.w3.org/Submission/2006/SUBM-WS-MTOMPolicy-20061101/)

このトピックでは、次の XML 名前空間と関連付けられたプレフィックスが使用されます。

| プレフィックス | 名前空間 URI (Uniform Resource Identifier) |
|------------|---------------------------------------------------|
| s11 | `http://schemas.xmlsoap.org/soap/envelope` |
| s12 |`http://www.w3.org/2003/05/soap-envelope` |
| wsa |`http://www.w3.org/2004/08/addressing` |
| wsam |`http://www.w3.org/2007/05/addressing/metadata` |
| wsap |`http://schemas.xmlsoap.org/ws/2004/09/policy/addressing` |
| wsa10 |`http://www.w3.org/2005/08/addressing` |
| wsaw10 |`http://www.w3.org/2006/05/addressing/wsdl` |
| xop |`http://www.w3.org/2004/08/xop/include` |
| xmime |`http://www.w3.org/2004/06/xmlmime`<br /><br /> `http://www.w3.org/2005/05/xmlmime` |
| dp |`http://schemas.microsoft.com/net/2006/06/duplex` |

## <a name="soap-11-and-soap-12"></a>SOAP 1.1 と SOAP 1.2

### <a name="envelope-and-processing-model"></a>エンベロープと処理モデル
WCF では、Basic Profile 1.1 (BP11) および Basic Profile 1.0 (SSBP10) に従って SOAP 1.1 エンベロープの処理を実装します。 SOAP 1.2 エンベロープの処理は、SOAP12-Part1 に従って実装されます。

このセクションでは、BP11 および SOAP12 パート 1 に関して、WCF によって実行される特定の実装の選択肢について説明します。

#### <a name="mandatory-header-processing"></a>必須のヘッダー処理
マークされたヘッダーの処理の規則に従います WCF`mustUnderstand`次のバリエーションと、SOAP 1.1 と SOAP 1.2 仕様で説明されています。

WCF チャネル スタックが入力したメッセージは、たとえば、関連付けられたバインド要素で構成されている個々 のチャネル、テキスト メッセージ エンコーディング、セキュリティ、信頼性の高いメッセージング、およびトランザクションで処理されます。 各チャネルは、関連付けられた名前空間からヘッダーを認識し、認識済みとしてマークします。 メッセージがディスパッチャーに入ると、操作フォーマッタは対応するメッセージ コントラクトと操作コントラクトで想定されたヘッダーを読み取り、認識済みとしてマークします。 次に、ディスパッチャーは、`mustUnderstand` としてマークされているにもかかわらず、認識されていないヘッダーが残っていないかどうかを検証し、例外をスローします。 受信者を対象とする `mustUnderstand` ヘッダーが含まれたメッセージが、受信者のアプリケーション コードで処理されることはありません。

このようなレイヤー化された処理により、SOAP ノードのインフラストラクチャ レイヤーとアプリケーション レイヤーを次のように分離することが可能になります。

- B1111:メッセージが WCF インフラストラクチャのチャネル スタックによって処理された後、アプリケーションによって処理される前に、認識されないヘッダーが検出されました

     `mustUnderstand` ヘッダーの値は、SOAP 1.1 と SOAP 1.2 で異なります。 Basic Profile 1.1 では、SOAP 1.1 メッセージの `mustUnderstand` の値が 0 または 1 である必要があります。 SOAP 1.2 では、値として 0、1、`false`、および `true` を使用できますが、`xs:boolean` 値の正規表現 (`false`、`true`) を出力することをお勧めします。

- B1112:WCF が出力`mustUnderstand`SOAP エンベロープの値を 0 と 1 を SOAP 1.1 と SOAP 1.2 の両方のバージョン。 WCF の全体の値の空白を受け入れる`xs:boolean`の`mustUnderstand`ヘッダー (0, 1, `false`、 `true`)

#### <a name="soap-faults"></a>SOAP エラー
次に特定の WCF SOAP エラー実装の一覧を示します。

- B2121:WCF は、次の SOAP 1.1 エラー コードを返します: `s11:mustUnderstand`、 `s11:Client`、および`s11:Server`します。

- B2122:WCF は、次の SOAP 1.2 エラー コードを返します: `s12:MustUnderstand`、 `s12:Sender`、および`s12:Receiver`します。

### <a name="http-binding"></a>HTTP バインディング

#### <a name="soap-11-http-binding"></a>SOAP 1.1 HTTP バインディング
WCF は、Basic Profile 1.1 仕様の説明を次のセクション 3.4 に従って、SOAP1.1 HTTP バインディングを実装します。

- B2211:WCF サービスは、HTTP POST 要求のリダイレクトを実装していません。

- B2212:WCF クライアントは、3.4.8 に従って HTTP クッキーをサポートします。

#### <a name="soap-12-http-binding"></a>SOAP 1.2 HTTP バインディング
WCF は、SOAP 1.2-part 2 (SOAP12Part2) 仕様次の説明」の説明に従って、SOAP 1.2 HTTP バインディングを実装します。

SOAP 1.2 では、`application/soap+xml` メディア タイプの省略可能なアクション パラメーターが導入されました。 このパラメーターは、WS-Addressing を使用していない場合に、SOAP メッセージの本文を解析する必要なく、メッセージ ディスパッチを最適化する際に役立ちます。

- R2221:`application/soap+xml` SOAP 1.2 要求に存在する場合、アクション パラメーターに一致する必要があります、`soapAction`属性を`wsoap12:operation`対応する WSDL バインディング内の要素。

- R2222:`application/soap+xml`が SOAP 1.2 メッセージに存在する場合、アクション パラメーターに一致する必要があります`wsa:Action`Ws-addressing 2004/08 または Ws-addressing 1.0 を使用する場合。

WS-Addressing が無効になっているときに、受信要求にアクション パラメーターが含まれていない場合、メッセージの `Action` は指定されていないものと見なされます。

## <a name="ws-addressing"></a>WS-Addressing
WCF には、3 つのバージョンの Ws-addressing が実装されています。

- WS-Addressing 2004/08

- W3C Web Services Addressing 1.0 コア (ADDR10-CORE) - SOAP バインディング (ADDR10-SOAP)

- WS-Addressing 1.0 - メタデータ

### <a name="endpoint-references"></a>エンドポイント参照
Ws-addressing の WCF 実装するすべてのバージョンでは、エンドポイント参照を使用してエンドポイントを記述します。

#### <a name="endpoint-references-and-ws-addressing-versions"></a>エンドポイント参照と WS-Addressing のバージョン
WCF は Ws-addressing を使用するためのインフラストラクチャ プロトコルの特定の数を実装して、`EndpointReference`要素と`W3C.WsAddressing.EndpointReferenceType`クラス (WS-ReliableMessaging、Ws-secureconversation、Ws-trust など)。 WCF では、どちらのバージョンの Ws-addressing を他のインフラストラクチャ プロトコルの使用をサポートします。 WCF エンドポイントは、エンドポイントごとに Ws-addressing の 1 つのバージョンをサポートします。

R3111 での名前空間、`EndpointReference`要素または WCF エンドポイントと交換されるメッセージで使用される型がこのエンドポイントで実装されている Ws-addressing のバージョンに一致する必要があります。

例では、WCF エンドポイントが WS-ReliableMessaging を実装している場合、`AcksTo`内のようなエンドポイントから返されるヘッダー `CreateSequenceResponse` Ws-addressing のバージョンを使用する、`EncodingBinding`要素は、このエンドポイントを指定します。

#### <a name="endpoint-references-and-metadata"></a>エンドポイント参照とメタデータ
多くのシナリオでは、指定されたエンドポイントのメタデータまたはメタデータへの参照を伝達する必要があります。

B3121:WCF は、Ws-metadataexchange (MEX) 仕様を値渡しまたは参照によって、エンドポイント参照のメタデータを含めるセクション 6 で説明されているメカニズムを使用します。

WCF サービスであるトークン発行者によって発行された Security Assertions Markup Language (SAML) トークンを使用して認証が必要な場合を考えます `http://sts.fabrikam123.com` です。 WCF エンドポイントを使用してこの認証要件を説明する`sp:IssuedToken`アサーションが入れ子になった`sp:Issuer`アサーション トークンの発行者をポイントします。 `sp:Issuer` アサーションにアクセスするクライアント アプリケーションは、トークン発行者のエンドポイントとの通信方法を知る必要があります。 クライアントは、トークン発行者に関するメタデータを知る必要があります。 MEX で定義されているエンドポイント参照のメタデータ拡張を使用して、WCF は、トークン発行者のメタデータへの参照を提供します。

```xml
<sp:IssuedToken>
  <sp:Issuer>
    <wsa10:Address>
      http://sts.fabrikam123.com
    </wsa10:Address>
    <wsa10:Metadata>
      <mex:Metadata>
        <mex:MetadataSection>
          <mex:MetadataReference>
            <wsa10:Address>
              http://sts.fabrikam123.com/mex
            </wsa10:Address>
          </mex:MetadataReference>
        </mex:MetadataSection>
      </mex:Metadata>
    </wsa10:Metadata>
  </sp:Issuer>
</sp:IssuedToken>
```

### <a name="message-addressing-headers"></a>メッセージのアドレス指定ヘッダー

#### <a name="message-headers"></a>メッセージ ヘッダー
両方の Ws-addressing のバージョンでは、WCF を使用して、次のメッセージ ヘッダー仕様で規定された`wsa:To`、 `wsa:ReplyTo`、 `wsa:Action`、 `wsa:MessageID`、および`wsa:RelatesTo`します。

B3211:すべての Ws-addressing のバージョンでは、WCF しますが、すぐに使える Ws-addressing メッセージ ヘッダーは生成されません`wsa:FaultTo`と`wsa:From`します。

WCF アプリケーションと対話するアプリケーションでは、これらのメッセージ ヘッダーと WCF は適切に処理を追加できます。

#### <a name="reference-parameters-and-properties"></a>参照パラメーターと参照プロパティ

WCF では、エンドポイント参照のパラメーターとそれぞれの仕様に従って参照プロパティの処理を実装します。

B3221:Ws-addressing 2004/08 を使用するよう構成する、WCF エンドポイントを区別せず参照プロパティと参照パラメーターを処理します。

### <a name="message-exchange-patterns"></a>メッセージ交換パターン
Web サービス操作の呼び出しに関連するメッセージのシーケンスとして参照されます、*メッセージ交換パターン*します。 WCF のサポートが一方向、要求/応答、および双方向メッセージ交換のパターンを実行します。 このセクションでは、使用するメッセージ交換パターンによって異なるメッセージ処理に関する WS-Addressing の要件について説明します。

このセクション全体を通して、リクエスターが最初のメッセージを送信し、レスポンダーが最初のメッセージを受信します。

#### <a name="one-way-message"></a>一方向のメッセージ
メッセージをサポートするために WCF エンドポイントを構成するとき、指定された`Action`WCF エンドポイントが、次の動作と要件に依存する一方向パターンには、します。 指定しない場合、両方のバージョンの Ws-addressing で WCF ではサポートされている動作とルールが適用されます。

- R3311:要求元を含める必要があります`wsa:To`、 `wsa:Action`、およびエンドポイント参照によって指定された参照パラメーターのすべてのヘッダー。 WS-Addressing 2004/08 を使用し、エンドポイント参照によって参照プロパティが指定されている場合、対応するヘッダーもメッセージに追加する必要があります。

- B3312:要求元を含めることができます`MessageID`、 `ReplyTo`、および`FaultTo`ヘッダー。 受信側のインフラストラクチャはこれらのヘッダーを無視し、ヘッダーはアプリケーションに渡されます。

- R3313:HTTP を使用すると、HTTP 応答レッグで送信されるメッセージがない、応答側は空の本文と HTTP 202 ステータス コードの HTTP 応答を送信する必要があります。

     HTTP トランスポートを使用しており、操作コントラクトで一方向のメッセージが宣言されている場合でも、HTTP 応答を使用してインフラストラクチャ メッセージを送信できます。たとえば、信頼できるメッセージングでは、HTTP 応答で `SequenceAcknowledgement` メッセージを送信できます。

- B3314:WCF 応答側では、一方向メッセージへの応答でエラー メッセージを送信しません。

#### <a name="request-reply"></a>要求/応答
メッセージで WCF エンドポイントを構成するときに、指定された`Action`の動作と要件を次に、要求/応答パターンは、WCF エンドポイントに依存します。 未指定の場合、両方のバージョンの Ws-addressing で WCF ではサポートされている動作とルールが適用されます。

- R3321:依頼者が要求に含める必要があります`wsa:To`、 `wsa:Action`、 `wsa:MessageID`、およびすべての参照パラメーターまたは参照プロパティ (またはその両方)、エンドポイント参照によって指定されたヘッダー。

- R3322:Ws-addressing 2004/08 を使用すると、ときに`ReplyTo`要求も含まれている必要があります。

- R3323:Ws-addressing 1.0 を使用する場合と`ReplyTo`が既定のエンドポイント参照に等しい [アドレス] プロパティを使用して、要求に存在しない`http://www.w3.org/2005/08/addressing/anonymous`使用されます。

- R3324:要求元を含める必要があります`wsa:To`、 `wsa:Action`、および`wsa:RelatesTo`のすべての参照パラメーターまたは参照プロパティ (またはその両方) で指定されたヘッダーと応答メッセージのヘッダー、`ReplyTo`要求のエンドポイント参照。

### <a name="web-services-addressing-faults"></a>Web Services Addressing エラー
R3411:WCF では、Ws-addressing 2004/08 で定義された次のエラーを生成します。

| コード | 原因 |
|----------|-----------|
| `wsa:DestinationUnreachable` | このチャネル用に確立された応答アドレスとは異なる `ReplyTo` を使用してメッセージが到着しました。To ヘッダーに指定されたアドレスをリッスンしているエンドポイントはありません。 |
| `wsa:ActionNotSupported` | `Action` ヘッダーに指定されたアクションは、エンドポイントに関連付けられたインフラストラクチャ チャネルまたはディスパッチャーによって認識されません。 |

R3412:WCF では、Ws-addressing 1.0 で定義された次のエラーを生成します。

| コード | 原因 |
|----------|-----------|
| `wsa10:InvalidAddressingHeader` | 重複する`wsa:To`、 `wsa:ReplyTo`、`wsa:From`または`wsa:MessageID`します。 重複する`wsa:RelatesTo`同じ`RelationshipType`します。 |
| `wsa10:MessageAddressingHeaderRequired` | 必須の Addressing ヘッダーがありません。 |
| `wsa10:DestinationUnreachable` | このチャネル用に確立された応答アドレスとは異なる `ReplyTo` を使用してメッセージが到着しました。 To ヘッダーに指定されたアドレスをリッスンしているエンドポイントはありません。 |
| `wsa10:ActionNotSupported` | `Action` ヘッダーに指定されたアクションは、エンドポイントに関連付けられたインフラストラクチャ チャネルまたはディスパッチャーによって認識されません。 |
| `wsa10:EndpointUnavailable` | RM チャネルは、`CreateSequence` メッセージのアドレス指定ヘッダーの検査に基づいて、エンドポイントでシーケンスが処理されないことを示すために、このエラーを返しました。 |

上記の 2 つの表に示すコードは、SOAP 1.1 の `FaultCode`、および SOAP 1.2 の `SubCode` (Code=Sender) に対応付けられています。

### <a name="wsdl-11-binding-and-ws-policy-assertions"></a>WSDL 1.1 バインディングと WS-Policy アサーション

#### <a name="indicating-use-of-ws-addressing"></a>WS-Addressing の使用の提示
WCF では、ポリシー アサーションを使用して、特定の Ws-addressing のバージョンのエンドポイントのサポートを示します。

次のポリシー アサーションには、エンドポイント ポリシー サブジェクト [WS-PA] が含まれており、そのエンドポイントで送受信されるメッセージでは WS-Addressing 2004/08 を使用する必要があることを示しています。

```xml
<wsap:UsingAddressing />
```

このポリシー アサーションは、WS-Addressing 2004/08 仕様を補うものです。

次のポリシー アサーションは、送受信されるメッセージでは WS-Addressing 1.0 を使用する必要があることを示しています。

```xml
<wsam:Addressing/>
```

次のポリシー アサーションには、エンドポイント ポリシー サブジェクト [WS-PA] が含まれており、そのエンドポイントで送受信されるメッセージでは WS-Addressing 2004/08 を使用する必要があることを示しています。

```xml
<wsaw10:UsingAddressing />
```

`wsaw10:UsingAddressing` 要素は、WS-Addressing-WSDL から借用したものです。この要素は、この仕様のセクション 3.1.2 に従って、WS-Policy のコンテキストで使用されます。

Addressing を使用しても、WSDL 1.1、SOAP 1.1、および SOAP 1.2 HTTP バインディングのセマンティクスが変更されるわけではありません。 たとえば、Addressing と WSDL SOAP 1.x HTTP バインディングを使用するエンドポイントに送信する要求に対して応答が求められている場合、この応答は HTTP 応答を使用して送信する必要があります。

HTTP 応答を使用して送信された応答の場合、WS-AM アサーションは次のようになります。

```xml
<wsam:AnonymousResponses/>
```

完全なポリシー アサーションは次のようになる場合があります。

```xml
<wsam:Addressing>
    <wsp:Policy>
        <wsam:AnonymousResponses />
    </wsp:Policy>
</wsam:Addressing>
```

ただし、リクエスターとレスポンダー間で 2 つの独立した逆方向の HTTP 接続を確立することによってメリットのあるメッセージ交換パターンがあります。たとえば、レスポンダーによって送信される要求されていない一方向のメッセージなどです。

WCF では、入力メッセージの 1 つのチャネルが使用される、他の出力メッセージを使用する複合二重チャネルを 2 つの基になるトランスポート チャネルから形成できます機能を提供します。 HTTP トランスポートの場合、複合二重によって 2 つの逆方向の HTTP 接続が実現します。 一方の接続はリクエスターがレスポンダーにメッセージを送信するために使用し、もう一方はレスポンダーがリクエスターにメッセージを返すために使用します。

個別の HTTP 要求を使用して送信された応答の場合、WS-AM アサーションは次のようになります。

```xml
<wsam:NonAnonymousResponses/>
```

完全なポリシー アサーションは次のようになる場合があります。

```xml
<wsam:Addressing>
    <wsp:Policy>
        <wsam:NonAnonymousResponses />
    </wsp:Policy>
</wsam:Addressing>
```

WSDL 1.1 SOAP 1.x HTTP バインディングを使用するエンドポイントで、エンドポイント ポリシー サブジェクト [WS-PA] を含む次のアサーションを使用する場合、リクエスターからレスポンダーおよびレスポンダーからリクエスターへのメッセージ フローにそれぞれ別の逆方向の HTTP 接続を使用する必要があります。

```xml
<cdp:CompositeDuplex/>
```

上記のステートメントにより、要求メッセージの `wsa:ReplyTo` ヘッダーに関する以下の要件が発生します。

- R3514:要求のメッセージをエンドポイントに送信する必要がありますが、`ReplyTo`ヘッダーを`[address]`プロパティが等しくない`http://www.w3.org/2005/08/addressing/anonymous`エンドポイントが WSDL 1.1 SOAP 1.x HTTP バインディングを使用して、使用ポリシー代替手段を持つ場合、`wsap10:UsingAddressing`または`wsap:UsingAddressing`アサーション組み合わせて`cdp:CompositeDuplex`アタッチします。

- R3515:要求のメッセージをエンドポイントに送信する必要がありますが、`ReplyTo`ヘッダーを`[address]`プロパティを等しく`http://www.w3.org/2005/08/addressing/anonymous`、かがありません、`ReplyTo`場合は、エンドポイントが WSDL 1.1 SOAP 1.x HTTP バインディングを使用してし、 、ポリシー代替手段を持つすべてのヘッダー`wsap10:UsingAddressing`アサーションと no`cdp:CompositeDuplex`アサーション。

- R3516:要求のメッセージをエンドポイントに送信する必要がありますが、`ReplyTo`ヘッダーを`[address]`プロパティを等しく`http://www.w3.org/2005/08/addressing/anonymous`エンドポイントが WSDL 1.1 SOAP 1.x HTTP バインディングを使用して、使用ポリシー代替手段を持つ場合`wsap:UsingAddressing`アサーションと no `cdp:CompositeDuplex`接続されているアサーションです。

WS-Addressing の WSDL 仕様では、`<wsaw:Anonymous/>` ヘッダーの要件を示す 3 つのテキスト値 (required、optional、および prohibited) を持つ `wsa:ReplyTo` 要素を導入することにより、同様のプロトコル バインディングを記述することを試みています (セクション 3.2)。 残念ながら、このような要素の定義では、要素をアサーションとして使用する代替手段の共通部分をサポートするために、ドメイン固有の拡張を必要とするため、特に WS-Policy のコンテキストではアサーションとして使用することはできません。 また、このような要素の定義は、ネットワーク上のエンドポイントの動作に相反する `ReplyTo` ヘッダーの値を示すため、HTTP トランスポートに固有のものになります。

#### <a name="action-definition"></a>アクション定義
WS-Addressing 2004/08 では、`wsa:Action` 要素の `wsdl:portType/wsdl:operation/[wsdl:input | wsdl:output | wsdl:fault]` 属性が定義されています。 WS-Addressing 1.0 WSDL バインディング (WS-ADDR10-WSDL) では、同様の属性として `wsaw10:Action` が定義されています。

この 2 つの属性の唯一の違いは、既定の Action パターンのセマンティクスです。これは、WS-ADDR のセクション 3.3.2 および WS-ADDR10-WSDL のセクション 4.4.4 にそれぞれ記載されています。

同じを共有する 2 つのエンドポイントが適切では`portType`(または WCF 用語では、コントラクト) が、異なるバージョンの Ws-addressing を使用します。 しかし、Action は `portType` によって定義され、`portType` を実装するエンドポイント間で変更できないことを考えると、両方の既定のアクション パターンをサポートすることは不可能になります。

この問題を解決するのには、WCF は、の 1 つのバージョンをサポートしています。、`Action`属性。

B3521:WCF を使用して、`wsaw10:Action`属性`wsdl:portType/wsdl:operation/[wsdl:input | wsdl:output | wsdl:fault]`WS ADDR10-WSDL を判断で定義されている要素、`Action`エンドポイントによって使用される Ws-addressing のバージョンに関係なく、対応するメッセージの URI。

#### <a name="use-endpoint-reference-inside-wsdl-port"></a>WSDL ポート内でのエンドポイント参照の使用
WS-ADDR10-WSDL のセクション 4.1 では、`wsdl:port` 要素を拡張して、WS-Addressing の観点でエンドポイントを記述する `<wsa10:EndpointReference…/>` 子要素を含めています。 WCF は Ws-addressing 2004/08 のこのユーティリティを展開できるように`<wsa:EndpointReference…/>`の子要素として表示する`wsdl:port`します。

- R3531:エンドポイントがある接続されているポリシー代替手段を持つ場合、`<wsaw10:UsingAddressing/>`ポリシー アサーションを対応する`wsdl:port`要素が子要素を含めることができます`<wsa10:EndpointReference …/>`します。

- R3532:場合、`wsdl:port`子要素を含む`<wsa10:EndpointReference …/>`、`wsa10:EndpointReference/wsa10:Address`子要素の値の値に一致する必要があります、`@address`の兄弟の属性`wsdl:port` / `wsdl:location`要素。

- R3533:エンドポイントがある接続されているポリシー代替手段を持つ場合`<wsap:UsingAddressing/>`ポリシー アサーションを対応する`wsdl:port`要素が子要素を含めることができます`<wsa:EndpointReference …/>`します。

- R3534:場合、`wsdl:port`子要素を含む`<wsa:EndpointReference …/>`、`wsa:EndpointReference/wsa:Address`子要素の値の値に一致する必要があります、`@address`の兄弟の属性`wsdl:port` / `wsdl:location`要素。

### <a name="composition-with-ws-security"></a>WS-Security によるコンポジション
WS-ADDR および WS-ADDR10 のセキュリティに関する考慮事項のセクションに従って、メッセージ本文と共にすべてのアドレス指定メッセージ ヘッダーに署名し、これらをバインドすることをお勧めします。

メッセージの整合性を保護するために WS-Security を使用する場合は、メッセージの本文と共に、WS-Addressing メッセージ ヘッダーと、参照パラメーターまたは参照プロパティ (または両方) によって生成されたヘッダーに署名する必要があります。

### <a name="examples"></a>使用例

#### <a name="one-way-message"></a>一方向のメッセージ
このシナリオでは、送信者は一方向のメッセージを受信者に送信します。 SOAP 1.2、HTTP 1.1、および W3C WS-Addressing 1.0 を使用します。

要求メッセージの構造:メッセージ ヘッダーが含まれる`wsa10:To`と`wsa10:Action`要素。 メッセージ本文には、アプリケーション名前空間の特定の `<app:Ping>` 要素が含まれます。

HTTP ヘッダー:POST の送信先の URI の一致、`wsa10:To`要素。

Content-Type ヘッダーには、SOAP 1.2 で必要とされる値 `application/soap+xml` が含まれます。 また、`charset` パラメーターと `action` パラメーターも含まれます。 Content-Type ヘッダーの `action` パラメーターは、`wsa10:Action` メッセージ ヘッダーの値に一致します。

```
POST http://fabrikam123.com/Service HTTP/1.1
Content-Type: application/soap+xml; charset=utf-8;  
              action="http://fabrikam123.com/Service/OneWay"
Host: 131.107.72.15
Content-Length: 1501
Expect: 100-continue
Proxy-Connection: Keep-Alive
<s12:Envelope>
  <s12:Header>
    <wsa10:To s12:mustUnderstand="1">
        http://fabrikam123.com/Service
    </wsa10:To>
    <wsa10:Action s12:mustUnderstand="1">
        http://fabrikam123.com/Service/OneWay 
    </wsa10:Action>
  </s12:Header>
  <s12:Body>
    <Ping xmlns="http://fabrikam123.com/Service/">
      <Text>Hello World</Text>
    </Ping>
  </s12:Body>
</s12:Envelope>
```

受信側は、空の HTTP 応答と 202 ステータスで応答します。 HTTP 応答の一例を次に示します。

```
HTTP/1.1 202 Accepted
Date: Fri, 15 Jul 2005 08:56:07 GMT
Server: Microsoft-IIS/6.0
MicrosoftOfficeWebServer: 5.0_Pub
X-Powered-By: ASP.NET
X-AspNet-Version: 2.0.50215
Cache-Control: private
Content-Length: 0
```

## <a name="soap-message-transmission-optimization-mechanism"></a>SOAP Message Transmission Optimization Mechanism
このセクションでは、HTTP SOAP MTOM の WCF 実装の詳細について説明します。 MTOM テクノロジは、従来の TEXT/XML エンコーディングまたは WCF バイナリ エンコーディングと同じクラスの SOAP メッセージのエンコーディング機構です。 MTOM には、次のような機能があります。

- XOP によって記述された XML エンコーディングおよびパッケージング機構。XOP は、Base64 で個別のバイナリ部分にエンコードされたバイナリ データを含む XML 情報項目を最適化します。

- XML Infoset と XOP パッケージの各バイナリ部分を個別の MIME パートにシリアル化する、XOP パッケージの MIME カプセル化。

- SOAP 1.x エンベロープに適用される MIME XOP エンコーディング。

- HTTP トランスポート バインディング。

WCF を使用した HTTP 以外のトランスポートで MTOM を使用することになります。 しかし、ここでは HTTP に焦点を合わせます。

MTOM 形式では、MTOM 自体、XOP、および MIME に適用されるさまざまな仕様を利用します。 この仕様セットのモジュール性により、形式と処理のセマンティクスの要件を正確に再構築することが若干難しくなります。 このセクションでは、MTOM HTTP バインディングの形式と処理の要件について説明します。

### <a name="mtom-message-encoding"></a>MTOM メッセージ エンコーディング

#### <a name="generating-mtom-messages"></a>MTOM メッセージの生成
XOP のセクション 3.1 には、Base64 値を抽象的に定義された XOP パッケージに格納する要素情報項目を使用して、XML をエンコーディングするプロセスが記載されています。

次の一連の手順は、MTOM 固有のエンコーディング プロセスを示しています。

1. エンコードする SOAP エンベロープに記述されている要素情報項目が含まれていないことを確認、`[namespace name]`の`http://www.w3.org/2004/08/xop/include`と`[local name]`の`Include`します。

2. 空の MIME パッケージを作成します。

3. 元の XML Infoset 内で、最適化する要素情報項目を特定します。 最適化されるアイテムの文字を構成する、`[children]`要素情報項目がの正規の形式である必要があります`xs:base64Binary`(XSD 2 3.2.16 参照 base64Binary) 前に、インラインで、任意の空白文字を含めることはできませんまたは次の空白以外のコンテンツ。

4. 元の SOAP エンベロープのコピーである XOP SOAP エンベロープを作成します。ただし、このコピーには、前の手順で特定した各要素情報項目の子が含まれます。これらの子は、以下の手順に従って構築された `xop:Include` 要素情報項目に置き換えられています。

    1. 置換対象の文字を Base64 でエンコードされたデータとして処理することにより、バイナリ データに変換します。

    2. R3133 および R3134 の各要件を満たす Content-ID ヘッダーの一意の値を生成します。

    3. バイナリ値を使用して、Content-Transfer-Encoding MIME ヘッダーを生成します。

    4. 最適化する要素情報項目 (新しく挿入する `xop:Include` 要素情報項目の [parent]) に、`xmime:contentType` 属性情報項目が含まれている場合、`xmime:contentType` 属性の値を使用して Content-Type MIME ヘッダーを生成します。

    5. Base64 として処理された置換対象文字からデコードされたバイナリ データ、Content-ID ヘッダー (手順 4b. で生成)、Content- Transfer-Encoding ヘッダー (手順 4c. で生成)、および Content-Type ヘッダー (手順 4d. で生成した場合) で構成されたコンテンツを含む、新しいバイナリ MIME パートを生成します。

    6. 値 cid: uri を持つ `href` 要素に `xop:Include` 属性を追加します。uri は、手順 4b. で生成した Content-ID ヘッダーの値から派生したものです。 囲んでいるを削除"\<"と">"文字を URL エスケープ文字列、およびプレフィックスを追加、残り`cid:`します。 RFC1738 と RFC2396 に従って、次の最小限の文字セットをエスケープする必要があります。 その他の文字もエスケープすることができます。

        ```
        Hexadecimal 00-1F , 7F, 20, "<" | ">" | "#" | "%" | <">
        "{" | "}" | "|" | "\" | "^" | "[" | "]" | "`" | "~" | "^"
        ```

5. 手順 4. の XOP SOAP エンベロープを含むルート MIME パートを作成します。

6. HTTP Content-Type ヘッダーなどの HTTP ヘッダーを書き込みます。

7. MIME パッケージを書き込みます。

#### <a name="processing-mtom-messages"></a>MTOM メッセージの処理
MTOM メッセージの処理は、前述の「MTOM メッセージの生成」で説明したプロセスと正反対のプロセスになります。

1. ルート MIME パートに Content-Type `application/xop+xml` が含まれていることを確認します。

2. パッケージのルート MIME パートを XML ドキュメントとして解析して、SOAP エンベロープを作成します。 文字エンコーディングは、ルート MIME パートの Content-Type の `charset` パラメーターによって決まります。

3. 作成した SOAP エンベロープ内の各要素情報項目について、以下の処理を行います。これらの要素情報項目には、[children] プロパティの唯一のメンバーとして、`xop:Include` 要素情報項目が含まれています。

    1. プレフィックス `cid:` を削除し、`@href` 要素の `xop:Include` 属性の値に含まれるすべての URI エスケープ シーケンスのエスケープを解除します (RFC 2396)。 結果の文字列を囲む"\<"、">"。

    2. Content-ID ヘッダーの値が手順 3a. で取得した文字列に一致する MIME パートを検索します。

    3. 各項目の `xop:Include` プロパティに出現する `children` 要素情報項目を、手順 3b. で特定した MIME パートのエンティティ本体の正規 Base64 エンコーディング (XSD-2 セクション 3.2.16 の base64Binary を参照) を表す文字情報項目に置き換えます (`xop:Include` 要素情報項目をパッケージ パーツから再構築したデータに効率的に置き換えます)。

#### <a name="http-content-type-header"></a>HTTP Content-Type ヘッダー
次は、SOAP 1.x MTOM でエンコードされたメッセージ、MTOM 仕様に記載された要件の HTTP Content-type ヘッダーの形式については、WCF の説明の一覧を示しますされ、MTOM および RFC 2387 から派生されます。

- R4131:マルチパート/関連 (大文字) の値とそのパラメーター、HTTP Content-type ヘッダーが必要です。 パラメーター名では、大文字と小文字は区別されません。 パラメーターの順序は重要ではありません。

- MIME メッセージの Content-Type ヘッダーのすべての Backus-Naur Form (BNF) については、RFC 2045 のセクション 5.1 に記載されています。

- R4132:HTTP Content-type ヘッダーの値の型パラメーターが必要`application/xop+xml`二重引用符で囲まれています。

ほとんどの場合などの予約文字を含むすべての multipart/related メディアの種類のパラメーターは、テキストを監視は、二重引用符を使用するという要件は RFC 2387 に明示的ではありません"\@"または「/」の二重引用符必要があります。マークを付けます。

- R4133:HTTP Content-type ヘッダーを SOAP を含む MIME パートの CONTENT-ID ヘッダーの値は、start パラメーターが必要 1.x エンベロープを二重引用符で囲まれています。 start パラメーターを省略する場合は、最初の MIME パートに SOAP 1.x エンベロープを含める必要があります。

- R4134:SOAP 1.1 MTOM でエンコードされたメッセージの HTTP Content-type ヘッダーには、text/xml を二重引用符で囲まれた値の開始情報パラメーターを含める必要があります。

- R4135:SOAP 1.2 MTOM でエンコードされたメッセージの HTTP Content-type ヘッダーの値の開始情報パラメーターを含める必要があります`application/soap+xml`二重引用符で囲んで指定します。

- R4136:SOAP 1.x MTOM でエンコードされたメッセージの HTTP Content-type ヘッダーでは、RFC 2046 のセクション 5.1.1 で定義されている BNF MIME 境界に一致する (二重引用符で囲まれた) 値を境界パラメーターがあります。

    ```
    boundary := 0*69<bchars> bcharsnospace 
    bchars := bcharsnospace / " " 
    bcharsnospace :=    DIGIT / ALPHA / "'" / "(" / ")" / "+" 
                        / "_" / "," / "-" / "." / "/" / ":" / "=" / "?"
    ```

     次に例を示します。 

     正

    ```
    Content-Type: multipart/related; type="application/xop+xml";start=" <part0@tempuri.org>";boundary="uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=1";start-info="text/xml"
    ```

     正

    ```
    Content-Type: Multipart/Related; type="application/xop+xml";start-info="text/xml";boundary="uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=1"
    ```

     誤

    ```
    Content-Type: Multipart/Related; type=application/xop+xml;start=" <part0@tempuri.org>";start-info="text/xml";boundary="uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=1" 
    ```

#### <a name="infoset-mime-part"></a>Infoset MIME パート
SOAP 1.x エンベロープは、XOP MIME パッケージのルート部分としてカプセル化され、多くの場合、`infoset` パートと呼ばれます。

- R4141:SOAP 1.x エンベロープと呼ばれる、XOP MIME パッケージのルート部分としてカプセル化する必要があります、`infoset`一部である HTTP Content-type から参照されています。

- R4142:SOAP`Infoset`部分は、次の MIME ヘッダーを含める必要があります: `Content-ID`、 `Content-Transfer-Encoding`、および`Content-Type`します。

Content-ID ヘッダーの形式は、RFC 2045 で次のように定義されています。

```
"Content-ID" ":" msg-id
```

ここで、`msg-id` は、RFC 2822 で次のように定義されています (RFC 2045 で参照されている RFC 822 は、RFC 2822 に置き換えられています)。

```
msg-id    =       [CFWS] "<" id-left "@" id-right ">" [CFWS]
```

実質的に、電子メール アドレスで囲まれたと"\<"と">"。 `[CFWS]` プレフィックスとサフィックスは、コメントを伝達するために RFC 2822 で追加されたものですが、相互運用性を維持する場合は、使用しないことをお勧めします。

R4143:Infoset MIME パートの CONTENT-ID ヘッダーの値が従う必要があります`msg-id`RFC 2822 から運用、`[CFWS]`プレフィックスとサフィックスの部分を省略するとします。

多くの MIME 実装で囲まれた値の要件を緩和する"\<"と">"電子メール アドレスを指定するために使用して`absoluteURI`で囲まれた"\<"、">"だけでなく、電子メール アドレス。 このバージョンの WCF では、フォームの CONTENT-ID MIME ヘッダーの値を使用します。

```
Content-ID: <http://tempuri.org/0> 
```

R4144:MTOM プロセッサは CONTENT-ID ヘッダーの値に一致する、次の緩和を受け入れる必要があります`msg-id`します。

```
msg-id-relaxed =     [CFWS] "<" (absoluteURI | mail-address) ">" [CFWS]
mail-address   =     id-left "@" id-right
```

MIME (RFC 2045) では、MIME パートのコンテンツのエンコーディングを伝達する Content-Transfer-Encoding ヘッダーを使用できます。 Content-Transfer-Encoding に定義されている既定値は 7 ビットですが、これはほとんどの SOAP メッセージに適していません。そのため、Content-Transfer-Encoding ヘッダーの相互運用性を高めるために、以下を行う必要があります。

- R4145:SOAP Infoset パートには、コンテンツ転送エンコード ヘッダーを含める必要があります。

- R4146:SOAP エンベロープの文字エンコーディングが utf-8 の場合、コンテンツ転送エンコード ヘッダーの値は 8 ビットである必要があります。

- R4147:SOAP エンベロープの文字エンコーディングが utf-16 の場合、コンテンツ転送エンコード ヘッダーの値はバイナリである必要があります。

- 以下の要件は、XOP のセクション 5 に基づいています。

- R4148:SOAP1.1 Infoset パートに Content-type ヘッダーのメディアの種類のアプリケーション/xop + xml を含める必要があり、パラメーターの入力"text/xml"および文字セットを =

    ```
    Content-Type: application/xop+xml;
                  charset=utf-8;type="text/xml"
    ```

- R4149:SOAP 1.2 Infoset パートは、メディアの種類のコンテンツ タイプ ヘッダーを含める必要があります`application/xop+xml`パラメーター入力 ="`application/soap+xml`"と`charset`します。

    ```
    Content-Type: application/xop+xml;
                  charset=utf-8;type="application/soap+xml"
    ```

     XOP では、`charset` の `application/xop+xml` パラメーターは省略可能と定義されていますが、`charset` メディア タイプの `text/xml` パラメーターについては、BP 1.1 の要件と同様の相互運用性が必要とされます。

- R41410:`type`と`charset`パラメーターは、SOAP 1.x Infoset パートの Content-type ヘッダーに存在する必要があります。

#### <a name="wcf-endpoint-support-for-mtom"></a>WCF エンドポイントによる MTOM のサポート
MTOM の目的は、SOAP メッセージをエンコードして、Base64 でエンコードされたデータを最適化することです。 制約は次のとおりです。

- R4151:Base64 でエンコードされたデータを含む任意の要素情報項目を最適化することがあります。

- B4152:WCF では、base64 でエンコードされたデータを含むことが 1,024 バイトの長さを超える要素情報項目を最適化します。

MTOM を使用するように構成の WCF エンドポイントでは、MTOM でエンコードされたメッセージは常に送信します。 必要な条件を満たすパートがない場合でも、メッセージは MTOM でエンコードされます (SOAP エンベロープを含む単一の MIME パートを持つ MIME パッケージとしてシリアル化されます)。

### <a name="ws-policy-assertion-for-mtom"></a>MTOM の WS-Policy アサーション
WCF では、次のポリシー アサーションを使用して、エンドポイントで MTOM の使用方法を示します。

```xml
<wsoma:OptimizedMimeSerialization ... />
```

- R4211:上記のポリシー アサーションには、エンドポイント ポリシー サブジェクトがあり、MTOM を使用して、エンドポイントから送受信されたすべてのメッセージを最適化する必要がありますを指定します。

- B4212:WCF エンドポイントが、対応する関連付けられているポリシーに MTOM ポリシー アサーションを追加します MTOM の最適化を使用するように構成、`wsdl:binding`します。

### <a name="composition-with-ws-security"></a>WS-Security によるコンポジション
MTOM は、次のような実現するエンコード メカニズム`text/xml`および WCF バイナリ XML。 MTOM は、WS-Security とその他の WS-* プロトコルによる自然なコンポジションを提供します。WS-Security を使用してセキュリティ保護されたメッセージは、MTOM を使用して最適化できます。

### <a name="examples"></a>使用例

#### <a name="wcf-soap-11-message-encoded-using-mtom"></a>MTOM を使用してエンコードされた WCF SOAP 1.1 メッセージ

```
POST http://131.107.72.15/Mtom/svc/service.svc/Soap11MtomUTF8 HTTP/1.1
SOAPAction: "http://xmlsoap.org/echoBinaryAsString"
Content-Type: multipart/related;type="application/xop+xml";
              start="<http://tempuri.org/0>";start-info="text/xml";
       boundary="uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=1"
Host: 131.107.72.15
Content-Length: 1501
--uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=1
Content-ID: <http://tempuri.org/0>
Content-Transfer-Encoding: 8bit
Content-Type: application/xop+xml;charset=utf-8;type="text/xml"
<s:Envelope xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">
  <s:Body>
    <EchoBinaryAsString xmlns="http://xmlsoap.org/Ping">
      <array>
        <xop:Include
         href="cid:http%3A%2F%2Ftempuri.org%2F1%2F632618206521093670"
         xmlns:xop="http://www.w3.org/2004/08/xop/include"/>
      </array>
    </EchoBinaryAsString>
  </s:Body>
</s:Envelope>
--uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=1
Content-ID: <http://tempuri.org/1/632618206521093670>
Content-Transfer-Encoding: binary
Content-Type: application/octet-stream
…Binary Content..
--uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=1
```

#### <a name="wcf-secure-soap-12-message-encoded-using-mtom"></a>MTOM を使用してエンコードされた WCF Secure SOAP 1.2 メッセージ
この例では、WS-Security を使用して保護されたメッセージを MTOM と SOAP 1.2 を使用してエンコードします。 エンコーディングの対象として特定されたバイナリ部分は、`BinarySecurityToken`、暗号化された署名に対応する `CipherValue` の `EncryptedData`、および暗号化された本文の内容です。 なお、`CipherValue`の`EncryptedKey`特定されなかった最適化のため、WCF、その長さが 1024 バイト未満であるためです。

```
POST http://131.107.72.15/Mtom/service.svc/Soap12MtomSecureSignEncrypt HTTP/1.1
Content-Type: multipart/related; type="application/xop+xml";
              start="<http://tempuri.org/0>";
            boundary="uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=3";
              start-info="application/soap+xml"; 
              action="http://xmlsoap.org/echoBinaryAsString"
Host: 131.107.72.15
Content-Length: 1941
--uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=3
Content-ID: <http://tempuri.org/0>
Content-Transfer-Encoding: 8bit
Content-Type: application/xop+xml;charset=utf-8;type="application/soap+xml"
<s:Envelope xmlns:s="http://schemas.xmlsoap.org/soap/envelope/" xmlns:u="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-utility-1.0.xsd">
  <s:Header>
    <o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd">
      <u:Timestamp u:Id="uuid-4d4ee765-5717-4d53-9ac9-99bddc07df6c-5">
        <u:Created>2005-09-09T06:57:32.488Z</u:Created>
        <u:Expires>2005-09-09T07:02:32.488Z</u:Expires>
      </u:Timestamp>
      <o:BinarySecurityToken u:Id="uuid-4d4ee765-5717-4d53-9ac9-99bddc07df6c-2" ValueType="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-x509-token-profile-1.0#X509v3" EncodingType="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-soap-message-security-1.0#Base64Binary">
        <xop:Include href="cid:http%3A%2F%2Ftempuri.org%2F1%2F632618206525089430" xmlns:xop="http://www.w3.org/2004/08/xop/include"/>
      </o:BinarySecurityToken>
      <e:EncryptedKey Id="_1" xmlns:e="http://www.w3.org/2001/04/xmlenc#">
        <e:EncryptionMethod Algorithm="http://www.w3.org/2001/04/xmlenc#rsa-oaep-mgf1p"/>
        <KeyInfo xmlns="http://www.w3.org/2000/09/xmldsig#">
          <o:SecurityTokenReference>
            <o:KeyIdentifier ValueType="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-x509-token-profile-1.0#X509SubjectKeyIdentifier">Xeg55vRyK3ZhAEhEf+YT0z986L0=</o:KeyIdentifier>
          </o:SecurityTokenReference>
        </KeyInfo>
        <e:CipherData>          <e:CipherValue>oQfpxwT8/SAGyZQzKE2b4yO6dXuQj7pwJ+5CGL3Rf7C06bQ5ttMoQ9GLJcQYkXTzin+WwHEgs5bj5ml9HKTW9QAU5JJ6lksdymmQvWP5ZtGPBVchO4sofEGoCKmBiZL/DYS/cnbzgnc/3a6NYnc10y2fWGaGLiqa00zijAw7o0Y=</e:CipherValue>
        </e:CipherData>
      </e:EncryptedKey>
      <c:DerivedKeyToken u:Id="_2" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc">
        <o:SecurityTokenReference>
          <o:Reference URI="#_1"/>
        </o:SecurityTokenReference>
        <c:Nonce>OrEPRX7fISIS4sXYWPMv3g==</c:Nonce>
      </c:DerivedKeyToken>
      <e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#">
        <e:DataReference URI="#_3"/>
        <e:DataReference URI="#_4"/>
      </e:ReferenceList>
      <e:EncryptedData Id="_4" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#">
        <e:EncryptionMethod Algorithm="http://www.w3.org/2001/04/xmlenc#aes256-cbc"/>
        <KeyInfo xmlns="http://www.w3.org/2000/09/xmldsig#">
          <o:SecurityTokenReference>
            <o:Reference URI="#_2"/>
          </o:SecurityTokenReference>
        </KeyInfo>
        <e:CipherData>
          <e:CipherValue>
            <xop:Include href="cid:http%3A%2F%2Ftempuri.org%2F2%2F632618206525089430" xmlns:xop="http://www.w3.org/2004/08/xop/include"/>
          </e:CipherValue>
        </e:CipherData>
      </e:EncryptedData>
    </o:Security>
  </s:Header>
  <s:Body u:Id="_0">
    <e:EncryptedData Id="_3" Type="http://www.w3.org/2001/04/xmlenc#Content" xmlns:e="http://www.w3.org/2001/04/xmlenc#">
      <e:EncryptionMethod Algorithm="http://www.w3.org/2001/04/xmlenc#aes256-cbc"/>
      <KeyInfo xmlns="http://www.w3.org/2000/09/xmldsig#">
        <o:SecurityTokenReference xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd">
          <o:Reference URI="#_2"/>
        </o:SecurityTokenReference>
      </KeyInfo>
      <e:CipherData>
        <e:CipherValue>
          <xop:Include href="cid:http%3A%2F%2Ftempuri.org%2F3%2F632618206525089430" xmlns:xop="http://www.w3.org/2004/08/xop/include"/>
        </e:CipherValue>
      </e:CipherData>
    </e:EncryptedData>
  </s:Body>
</s:Envelope>
--uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=3
Content-ID: <http://tempuri.org/1/632618206525089430>
Content-Transfer-Encoding: binary
Content-Type: application/octet-stream
...Binary content of BinarySecurityToken - X509 Certificate...
--uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=3
Content-ID: <http://tempuri.org/2/632618206525089430>
Content-Transfer-Encoding: binary
Content-Type: application/octet-stream
...Binary serialization of the encrypted primary signature...
--uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=3
Content-ID: <http://tempuri.org/3/632618206525089430>
Content-Transfer-Encoding: binary
Content-Type: application/octet-stream
...Binary serialization of the encrypted Body...
--uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=3--
```