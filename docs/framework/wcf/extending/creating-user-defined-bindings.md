---
title: ユーザー定義バインディングの作成
ms.date: 03/30/2017
helpviewer_keywords:
- user-defined bindings [WCF]
ms.assetid: c4960675-d701-4bc9-b400-36a752fdd08b
ms.openlocfilehash: 54a1c8e06991729ea8556d82d31897c522f6d173
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59188722"
---
# <a name="creating-user-defined-bindings"></a>ユーザー定義バインディングの作成
システムから提供されないバインディングを作成する方法はいくつかあります。  
  
-   バインド要素を格納するコンテナーである <xref:System.ServiceModel.Channels.CustomBinding> クラスに基づいてカスタム バインディングを作成します。 次に、カスタム バインディングをサービス エンドポイントに追加します。 カスタム バインディングは、プログラムで作成することも、アプリケーションの構成ファイルに作成することもできます。 アプリケーション構成ファイルのバインド要素を使用するには、バインド要素で <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> を拡張する必要があります。 カスタム バインドの詳細については、次を参照してください。[カスタム バインド](../../../../docs/framework/wcf/extending/custom-bindings.md)と<xref:System.ServiceModel.Channels.CustomBinding>します。  
  
-   標準バインディングの派生クラスを作成できます。 たとえば、<xref:System.ServiceModel.WSHttpBinding> の派生クラスを作成して <xref:System.ServiceModel.Channels.CustomBinding.CreateBindingElements%2A> メソッドをオーバーライドし、バインド要素を取得してカスタム バインドを挿入したり、セキュリティ用の特定の値を確立したりできます。  
  
-   新しい <xref:System.ServiceModel.Channels.Binding> 型を作成して、バインディング実装全体を完全に制御することができます。  
  
## <a name="the-order-of-binding-elements"></a>バインド要素の順序  
 各バインド要素は、メッセージの送信または受信時の処理手順を表します。 実行時に、バインド要素により、送受信チャネル スタックの作成に必要なチャネルとリスナーが作成されます。  
  
 バインド要素の次の 3 つの主な種類があります。プロトコルの要素、エンコーディング バインド要素、およびトランスポート バインド要素をバインドします。  
  
 プロトコル バインド要素 : この要素はメッセージで動作する上位処理ステップを表します。 このバインド要素で作成したチャネルとリスナーを使って、メッセージ内容の追加、削除、変更が可能です。 特定のバインディングには、それぞれが <xref:System.ServiceModel.Channels.BindingElement> を継承する任意の数のプロトコル バインド要素を含めることができます。 Windows Communication Foundation (WCF) など、いくつかのプロトコル バインド要素が含まれています、 <xref:System.ServiceModel.Channels.ReliableSessionBindingElement> 、<xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>します。  
  
 エンコーディング バインド要素 : この要素は、メッセージとネットワーク転送が可能なエンコーディングとの間の変換を表します。 一般的な WCF バインドには、1 つのエンコーディング バインド要素が含まれます。 エンコーディング バインド要素の例として、<xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement>、<xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>、<xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> などがあります。 エンコーディング バインド要素がバインディングに指定されていない場合、既定のエンコーディングが使用されます。 既定値は、トランスポートが HTTP の場合はテキスト、それ以外の場合はバイナリです。  
  
 トランスポート バインド要素 : この要素は、トランスポート プロトコルでのエンコーディング メッセージの送信を表します。 一般的な WCF バインドを継承する、1 つのトランスポート バインド要素を含める<xref:System.ServiceModel.Channels.TransportBindingElement>します。 トランスポート バインド要素の例として、<xref:System.ServiceModel.Channels.TcpTransportBindingElement>、<xref:System.ServiceModel.Channels.HttpTransportBindingElement>、<xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement> などがあります。  
  
 新しいバインディングを作成する場合、バインド要素の追加順序が重要になります。 バインド要素は必ず次の順序で追加します。  
  
|レイヤー|オプション|必須|  
|-----------|-------------|--------------|  
|トランザクション フロー|<xref:System.ServiceModel.Channels.TransactionFlowBindingElement?displayProperty=nameWithType>|Ｘ|  
|信頼性|<xref:System.ServiceModel.Channels.ReliableSessionBindingElement?displayProperty=nameWithType>|Ｘ|  
|セキュリティ|<xref:System.ServiceModel.Channels.SecurityBindingElement?displayProperty=nameWithType>|Ｘ|  
|複合二重|<xref:System.ServiceModel.Channels.CompositeDuplexBindingElement?displayProperty=nameWithType>|Ｘ|  
|エンコーディング|テキスト、バイナリ、MTOM、カスタム|○*|  
|Transport|TCP、名前付きパイプ、HTTP、HTTPS、MSMQ、およびカスタム|[はい]|  
  
 * エンコーディングに必要なため、各バインド エンコーディングが指定されていない場合、WCF は既定エンコーディングを追加します。 既定値は、HTTP および HTTPS トランスポートの場合はテキスト/XML、それ以外の場合はバイナリです。  
  
## <a name="creating-a-new-binding-element"></a>新しいバインド要素の作成  
 派生した型だけでなく<xref:System.ServiceModel.Channels.BindingElement>は、WCF によって、独自のバインド要素を作成できます。 これにより、他のシステムが提供する型を使ってスタックに組み込むことのできる独自の <xref:System.ServiceModel.Channels.BindingElement> を作成して、バインディングのスタックを作成する方法や、バインディングのスタックに追加するコンポーネントをカスタマイズできます。  
  
 たとえば、メッセージをデータベースに記録する機能を持つ `LoggingBindingElement` を実装する場合、それをチャネル スタックのトランスポート チャネルの上に配置する必要があります。 この場合、アプリケーションでは、次の例に示すように、`LoggingBindingElement` と共に `TcpTransportBindingElement` が組み込まれたカスタム バインディングが作成されます。  
  
```csharp  
Binding customBinding = new CustomBinding(  
  new LoggingBindingElement(),   
  new TcpTransportBindingElement()  
);  
```  
  
 新しいバインド要素を記述する方法は、機能性の詳細によって異なります。 このサンプルでは、いずれか[トランスポート。UDP](../../../../docs/framework/wcf/samples/transport-udp.md)、1 つの種類のバインド要素を実装する方法の詳細な説明を提供します。  
  
## <a name="creating-a-new-binding"></a>新しいバインディングの作成  
 ユーザーが作成するバインド要素は、2 つの方法で使用できます。 前のセクションでは、カスタム バインディングを使用する 1 番目の方法が説明されています。 カスタム バインディングを使用すれば、バインド要素の任意のセットに基づいて独自のバインディングを作成できます。ユーザーが作成するバインディング エレメントもこれに含まれます。  
  
 2 つ以上のアプリケーションでバインディングを使用する場合、独自のバインディングを作成し、<xref:System.ServiceModel.Channels.Binding> を拡張します。 これにより、カスタム バインディングを使う必要があるたびに、手動でカスタム バインディングを作成する必要性を回避できます。 ユーザー定義のバインディングを使用して、バインディングの動作を定義したり、ユーザー定義のバインド要素を格納することができます。 *事前パッケージング*: を使用するたびに、バインドを再構築する必要はありません。  
  
 ユーザー定義のバインディングは、少なくとも <xref:System.ServiceModel.Channels.Binding.CreateBindingElements%2A> メソッドと <xref:System.ServiceModel.Channels.Binding.Scheme%2A> プロパティを実装する必要があります。  
  
 <xref:System.ServiceModel.Channels.Binding.CreateBindingElements%2A> メソッドは、バインディングのバインド要素を格納している新しい <xref:System.ServiceModel.Channels.BindingElementCollection> を返します。 このコレクションは順序付けられており、始めにプロトコル バインド要素を格納し、次にエンコーディング バインド要素、その次にトランスポート バインド要素を格納する必要があります。 WCF システム指定のバインディング要素を使用する場合は、バインド要素の順序で指定されたルールを従う必要があります[カスタム バインド](../../../../docs/framework/wcf/extending/custom-bindings.md)します。 このコレクションから、ユーザー定義のバインディング クラス内で参照されるオブジェクトを参照すべきではありません。このため、バインディングの作成者は、<xref:System.ServiceModel.Channels.Binding.CreateBindingElements%2A> を呼び出すたびに <xref:System.ServiceModel.Channels.BindingElementCollection> の `Clone()` を返す必要があります。  
  
 <xref:System.ServiceModel.Channels.Binding.Scheme%2A> プロパティは、バインディングで使用するトランスポート プロトコルの URI スキームを表します。 たとえば、 *WSHttpBinding*と*NetTcpBinding*から、それぞれ"http"および"net.tcp"を返します<xref:System.ServiceModel.Channels.Binding.Scheme%2A>プロパティ。  
  
 ユーザー定義バインディングのオプション メソッドとプロパティの完全な一覧については、<xref:System.ServiceModel.Channels.Binding> を参照してください。  
  
### <a name="example"></a>例  
 このサンプルでは、プロファイル バインディングを、`SampleProfileUdpBinding` から派生した <xref:System.ServiceModel.Channels.Binding> に実装します。 `SampleProfileUdpBinding`に最大 4 つのバインド要素が含まれています。 ユーザーが作成した 1 つ`UdpTransportBindingElement`; システム指定の 3 つ: `TextMessageEncodingBindingElement`、 `CompositeDuplexBindingElement`、と`ReliableSessionBindingElement`。  
  
```csharp
public override BindingElementCollection CreateBindingElements()  
{     
    BindingElementCollection bindingElements = new BindingElementCollection();  
    if (ReliableSessionEnabled)  
    {  
        bindingElements.Add(session);  
        bindingElements.Add(compositeDuplex);  
    }  
    bindingElements.Add(encoding);  
    bindingElements.Add(transport);  
    return bindingElements.Clone();  
}  
```  
  
## <a name="security-restrictions-with-duplex-contracts"></a>双方向コントラクトのセキュリティ制限  
 すべてのバインド要素どうしに互換性があるわけではありません。 特に双方向コントラクトで使用する場合、セキュリティ バインド要素にはいくつかの制限があります。  
  
### <a name="one-shot-security"></a>ワンショット セキュリティ  
 すべての必要なセキュリティ資格情報を設定する 1 つのメッセージで送信する場所、「ワンショット」セキュリティを実装することができます、`negotiateServiceCredential`の属性、\<メッセージ > 構成要素を`false`します。  
  
 ワンショット認証は双方向コントラクトでは動作しません。  
  
 要求/応答コントラクトでは、セキュリティ バインド要素の下にあるバインディング スタックで <xref:System.ServiceModel.Channels.IRequestChannel> インスタンスまたは <xref:System.ServiceModel.Channels.IRequestSessionChannel> インスタンスの作成がサポートされている場合にのみ、ワンショット認証は動作します。  
  
 一方向コントラクトでは、セキュリティ バインド要素の下にあるバインディング スタックで <xref:System.ServiceModel.Channels.IRequestChannel>、<xref:System.ServiceModel.Channels.IRequestSessionChannel>、<xref:System.ServiceModel.Channels.IOutputChannel>、または <xref:System.ServiceModel.Channels.IOutputSessionChannel> の各インスタンスの作成がサポートされている場合にのみ、ワンショット認証は動作します。  
  
### <a name="cookie-mode-security-context-tokens"></a>クッキー モードのセキュリティ コンテキスト トークン  
 クッキー モードのセキュリティ コンテキスト トークンは、双方向コントラクトでは使用できません。  
  
 要求/応答コントラクトでは、セキュリティ バインド要素の下にあるバインディング スタックで <xref:System.ServiceModel.Channels.IRequestChannel> インスタンスまたは <xref:System.ServiceModel.Channels.IRequestSessionChannel> インスタンスの作成がサポートされている場合にのみ、クッキー モードのセキュリティ コンテキスト トークンは動作します。  
  
 一方向コントラクトでは、セキュリティ バインド要素の下にあるバインディング スタックで <xref:System.ServiceModel.Channels.IRequestChannel> インスタンスまたは <xref:System.ServiceModel.Channels.IRequestSessionChannel> インスタンスの作成がサポートされている場合にのみ、クッキー モードのセキュリティ コンテキスト トークンは動作します。  
  
### <a name="session-mode-security-context-tokens"></a>セッション モードのセキュリティ コンテキスト トークン  
 双方向コントラクトでは、セッション モードの SCT (セキュリティ コンテキスト トークン) は、セキュリティ バインド要素の下にあるバインディング スタックで <xref:System.ServiceModel.Channels.IDuplexChannel> インスタンスまたは <xref:System.ServiceModel.Channels.IDuplexSessionChannel> インスタンスの作成がサポートされている場合に動作します。  
  
 要求/応答コントラクトでは、セッション モードの SCT は、セキュリティ バインド要素の下にあるバインディング スタックで <xref:System.ServiceModel.Channels.IDuplexChannel>、<xref:System.ServiceModel.Channels.IDuplexSessionChannel>、<xref:System.ServiceModel.Channels.IRequestChannel>、または <xref:System.ServiceModel.Channels.IRequestSessionChannel> の各インスタンスの作成がサポートされている場合に動作します。  
  
 一方向コントラクトでは、セッション モードの SCT は、セキュリティ バインド要素の下にあるバインディング スタックで <xref:System.ServiceModel.Channels.IDuplexChannel>、<xref:System.ServiceModel.Channels.IDuplexSessionChannel>、<xref:System.ServiceModel.Channels.IRequestChannel>、または <xref:System.ServiceModel.Channels.IRequestSessionChannel> の各インスタンスの作成がサポートされている場合に動作します。  
  
## <a name="deriving-from-a-standard-binding"></a>標準バインディングからの派生  
 まったく新しいバインディング クラスを作成する代わりに、システムから提供される既存のバインディングの 1 つを拡張することができます。 前述の場合と同様、<xref:System.ServiceModel.Channels.Binding.CreateBindingElements%2A> メソッドと <xref:System.ServiceModel.Channels.Binding.Scheme%2A> プロパティをオーバーライドする必要があります。  
  
## <a name="see-also"></a>関連項目

- <xref:System.ServiceModel.Channels.Binding>
- [カスタム バインディング](../../../../docs/framework/wcf/extending/custom-bindings.md)
