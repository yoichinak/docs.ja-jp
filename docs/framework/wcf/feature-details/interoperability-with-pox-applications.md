---
title: POX アプリケーションとの相互運用性
ms.date: 03/30/2017
ms.assetid: 449276b8-4633-46f0-85c9-81f01d127636
ms.openlocfilehash: b7fdb4e16bce52025515ced065d0f48cffb7fa3f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62046893"
---
# <a name="interoperability-with-pox-applications"></a>POX アプリケーションとの相互運用性

"Plain Old XML"(POX) アプリケーションは、SOAP エンベロープで囲まれていない XML アプリケーション データのみを含んだ生の HTTP メッセージの交換によって通信します。 Windows Communication Foundation (WCF) には、サービスと POX メッセージを使用するクライアントの両方を提供できます。 サービスでは、Web ブラウザーなどのクライアント エンドポイントを公開するサービスと POX メッセージを送受信するためのスクリプト言語を実装するために WCF を使用できます。 クライアントでは、POX ベースのサービスと通信するクライアントを実装するために、WCF プログラミング モデルを使用できます。  
  
> [!NOTE]
> このドキュメントはもともと [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 3.0 用に書かれたものです。  [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 3.5 には POX アプリケーション用のサポートが組み込まれています。 参照の詳細については[WCF Web HTTP プログラミング モデル](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)します。
  
## <a name="pox-programming-with-wcf"></a>WCF による POX プログラミング

POX メッセージを使用して HTTP 経由で通信する WCF サービスを[ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)します。

```xml
<customBinding>
   <binding name="poxServerBinding">
       <textMessageEncoding messageVersion="None" />
       <httpTransport />
   </binding>
</customBinding>
```

このカスタム バインドには、次の 2 つの要素があります。

- [\<httpTransport>](../../../../docs/framework/configure-apps/file-schema/wcf/httptransport.md)

- [\<textMessageEncoding>](../../../../docs/framework/configure-apps/file-schema/wcf/textmessageencoding.md)

標準の WCF のテキスト メッセージ エンコーダーが使用する特別に構成された、<xref:System.ServiceModel.Channels.MessageVersion.None%2A>値で、XML メッセージ ペイロードされずに到着する SOAP エンベロープにラップを処理するようになります。

POX メッセージを使用して HTTP を介して通信する WCF クライアントは、(次の命令型コードに示す) のようなバインディングを使用します。

```csharp
private static Binding CreatePoxBinding()
{
    TextMessageEncodingBindingElement encoder =
        new TextMessageEncodingBindingElement( MessageVersion.None, Encoding.UTF8 );
    HttpTransportBindingElement transport = new HttpTransportBindingElement();
    transport.ManualAddressing = true;
    return new CustomBinding( new BindingElement[] { encoder, transport } );
}
```

POX クライアントでは、メッセージの送信先となる URI を明示的に指定する必要があるため、クライアントの <xref:System.ServiceModel.Channels.HttpTransportBindingElement> プロパティを <xref:System.ServiceModel.Channels.TransportBindingElement.ManualAddressing%2A> に設定することで、通常、`true` を手動アドレス指定モードに構成する必要があります。 これにより、アプリケーション コードによってメッセージのアドレスが明示的に指定されることになり、アプリケーションで異なる HTTP URI にメッセージを送信するたびに、新しい <xref:System.ServiceModel.ChannelFactory> を作成する必要がなくなります。

POX メッセージでは重要なプロトコル情報の搬送に SOAP ヘッダーを使用しないため、POX クライアントおよびサービスでは、メッセージの送受信に使用される、基になる HTTP 要求の情報を操作する必要が生じる場合がよく起こります。 HTTP ヘッダーやステータス コードなどの HTTP 固有のプロトコル情報は、2 つのクラスを使用して、WCF プログラミング モデルに表示されます。

- <xref:System.ServiceModel.Channels.HttpRequestMessageProperty> には、HTTP メソッドと要求ヘッダーなど、HTTP 要求についての情報が含まれます。

- <xref:System.ServiceModel.Channels.HttpResponseMessageProperty> には、HTTP ステータス コード、ステータスの説明、および任意の HTTP 応答ヘッダーなど、HTTP 応答についての情報が含まれます。
  
次のコード例は、宛先は、HTTP GET 要求メッセージを作成する方法を示します`http://localhost:8100/customers`します。

```csharp
Message request = Message.CreateMessage( MessageVersion.None, String.Empty );
request.Headers.To = "http://localhost:8100/customers";

HttpRequestMessageProperty property = new HttpRequestMessageProperty();
property.Method = "GET";
property.SuppressEntityBody = true;
request.Properties.Add( HttpRequestMessageProperty.Name, property );
```

初めに、<xref:System.ServiceModel.Channels.Message> を呼び出すことで、空の <xref:System.ServiceModel.Channels.Message.CreateMessage%28System.ServiceModel.Channels.MessageVersion%2CSystem.String%29> 要求を作成します。 <xref:System.ServiceModel.Channels.MessageVersion.None%2A> パラメーターを使用して SOAP エンベロープが不要であることを示し、<xref:System.String.Empty> パラメーターをアクションとして渡します。 次に、<xref:System.ServiceModel.Channels.MessageHeaders.To%2A> を目的の URI に設定することで、要求メッセージをアドレス指定します。 さらに、<xref:System.ServiceModel.Channels.HttpRequestMessageProperty> を作成し、<xref:System.ServiceModel.Channels.HttpRequestMessageProperty.Method%2A> を HTTP 動詞の GET メソッドに設定し、また <xref:System.ServiceModel.Channels.HttpRequestMessageProperty.SuppressEntityBody%2A> を `true` に設定して、送信 HTTP 要求メッセージの本文でデータが送信されないことを示します。 最後に、要求プロパティを要求メッセージの <xref:System.ServiceModel.Channels.Message.Properties%2A> コレクションに追加して、HTTP トランスポートによる要求の送信方法に影響を与えることができるようにします。 これで <xref:System.ServiceModel.Channels.IRequestChannel> の適切なインスタンスを使用してメッセージを送信する用意が整いました。

サービスにおいても、受信メッセージから <xref:System.ServiceModel.Channels.HttpRequestMessageProperty> を抽出して応答を構築する際に同様のテクニックを使用できます。
