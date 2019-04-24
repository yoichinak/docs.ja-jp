---
title: BindingElement の作成
ms.date: 03/30/2017
ms.assetid: 01a35307-a41f-4ef6-a3db-322af40afc99
ms.openlocfilehash: 600bf9b394078ffc1b1bc97390bd0de406d64338
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59115168"
---
# <a name="creating-a-bindingelement"></a>BindingElement の作成
バインディングとバインド要素 (オブジェクトを拡張する<xref:System.ServiceModel.Channels.Binding?displayProperty=nameWithType>と<xref:System.ServiceModel.Channels.BindingElement?displayProperty=nameWithType>、それぞれ) は、Windows Communication Foundation (WCF) アプリケーション モデルがチャネル ファクトリとチャネル リスナーに関連付けられている場所。 なしのバインド、カスタム チャネルを使用する必要がありますチャネル レベルでのプログラミング」の説明に従って[サービス チャネル レベルのプログラミング](../../../../docs/framework/wcf/extending/service-channel-level-programming.md)と[クライアント チャネル レベルのプログラミング](../../../../docs/framework/wcf/extending/client-channel-level-programming.md)します。 このトピックでは、wcf での開発、チャネルを使用して有効にする最小要件を説明します、<xref:System.ServiceModel.Channels.BindingElement>の手順 4 で説明したように、アプリケーションから使用可能にする、チャネル、[開発チャネル](../../../../docs/framework/wcf/extending/developing-channels.md)します。  
  
## <a name="overview"></a>概要  
 作成、 <xref:System.ServiceModel.Channels.BindingElement> WCF アプリケーションで使用する開発者は、チャネルの。 <xref:System.ServiceModel.Channels.BindingElement> オブジェクトを使用する、<xref:System.ServiceModel.ServiceHost?displayProperty=nameWithType>クラスをチャネルの正確な型情報をしなくても、WCF アプリケーションをチャネルを接続します。  
  
 1 回、<xref:System.ServiceModel.Channels.BindingElement>が作成されると、次で説明されている残りのチャネル開発手順によって、要件に応じて複数の機能を有効にできます[開発チャネル](../../../../docs/framework/wcf/extending/developing-channels.md)します。  
  
## <a name="adding-a-binding-element"></a>バインド要素の追加  
 カスタムの <xref:System.ServiceModel.Channels.BindingElement> を実装するには、<xref:System.ServiceModel.Channels.BindingElement> を継承するクラスを記述します。 たとえば、サイズの大きいメッセージをチャンクに分割し、接続先で元のメッセージを再構築できる `ChunkingChannel` を開発している場合、<xref:System.ServiceModel.Channels.BindingElement> を実装してこれを使用するようにバインディングを構成することによって、任意のバインディングでこのチャネルを使用できるようになります。 このトピックの残りの部分では、`ChunkingChannel` を例にして、バインド要素を実装する際の要件を示します。  
  
 `ChunkingBindingElement` は、`ChunkingChannelFactory` および `ChunkingChannelListener` を作成します。 このバインド要素は、<xref:System.ServiceModel.Channels.BindingElement.CanBuildChannelFactory%2A> 実装および <xref:System.ServiceModel.Channels.BindingElement.CanBuildChannelListener%2A> 実装をオーバーライドし、型パラメーターが <xref:System.ServiceModel.Channels.IDuplexSessionChannel> (この例では、これが `ChunkingChannel` でサポートされる唯一のチャネル形状です) であることと、バインディングの他のバインド要素がこのチャネル形状をサポートすることを確認します。  
  
 <xref:System.ServiceModel.Channels.BindingElement.BuildChannelFactory%2A> は、要求されたチャネル形状を構築できることをまず確認し、次にチャンク対象のメッセージ アクションのリストを取得します。 さらに、新しい `ChunkingChannelFactory` を作成してこれに内部チャネル ファクトリを渡します  (トランスポート バインド要素を作成する場合、これはバインディング スタック内の最後の要素となるため、チャネル リスナーとチャネル ファクトリを作成する必要があります)。  
  
 <xref:System.ServiceModel.Channels.BindingElement.BuildChannelListener%2A> には、`ChunkingChannelListener` を作成してこれに内部チャネル リスナーを渡す同様の実装があります。  
  
 トランスポート チャネルを使用して別の例として、[トランスポート。UDP](../../../../docs/framework/wcf/samples/transport-udp.md)サンプルは次のオーバーライドを提供します。  
  
 このサンプルでは、バインド要素は `UdpTransportBindingElement` で、<xref:System.ServiceModel.Channels.TransportBindingElement> から派生しています。 このバインド要素は、チャネルに関連付けられているファクトリを作成する、次のメソッドをオーバーライドします。  
  
```csharp  
public IChannelFactory<TChannel> BuildChannelFactory<TChannel>(BindingContext context)  
{  
    return (IChannelFactory<TChannel>)(object)new UdpChannelFactory(this, context);  
}  
  
public IChannelListener<TChannel> BuildChannelListener<TChannel>(BindingContext context)  
{  
    return (IChannelListener<TChannel>)(object)new UdpChannelListener(this, context);  
}  
```  
  
 また、この要素には、`BindingElement` を複製したり、スキーム (soap.udp) を返したりするためのメンバーも含まれます。  
  
#### <a name="protocol-binding-elements"></a>プロトコル バインド要素  
 含まれているバインド要素を新しいバインド要素で置き換えたり補足したりすることにより、新しいトランスポート、エンコーディング、または高レベルのプロトコルを追加できます。 新しいプロトコル バインド要素を作成するには、まず <xref:System.ServiceModel.Channels.BindingElement> クラスを拡張します。 少なくともし実装する必要あります、<xref:System.ServiceModel.Channels.BindingElement.Clone%2A?displayProperty=nameWithType>を実装し、`ChannelProtectionRequirements`を使用して<xref:System.ServiceModel.Channels.IChannel.GetProperty%2A?displayProperty=nameWithType>します。 これにより、このバインド要素の <xref:System.ServiceModel.Security.ChannelProtectionRequirements> が返されます。  詳細については、「 <xref:System.ServiceModel.Security.ChannelProtectionRequirements> 」を参照してください。  
  
 <xref:System.ServiceModel.Channels.BindingElement.Clone%2A> は、このバインド要素の新しいコピーを返します。 最善の方法としては、バインド要素の作成者は基本の copy コンストラクターを呼び出す copy コンストラクターを使用して、<xref:System.ServiceModel.Channels.BindingElement.Clone%2A> を実装し、このクラスに含まれるすべての追加フィールドを複製することをお勧めします。  
  
#### <a name="transport-binding-elements"></a>トランスポート バインド要素  
 新しいトランスポート バインド要素を作成するには、<xref:System.ServiceModel.Channels.TransportBindingElement> インターフェイスを拡張します。 次に、少なくとも <xref:System.ServiceModel.Channels.BindingElement.Clone%2A> メソッドと <xref:System.ServiceModel.Channels.TransportBindingElement.Scheme%2A?displayProperty=nameWithType> プロパティを実装する必要があります。  
  
 <xref:System.ServiceModel.Channels.BindingElement.Clone%2A> - このバインド要素の新しいコピーを返します。  最善の方法としては、バインド要素の作成者は基本の copy コンストラクターを呼び出す copy コンストラクターを使用して、複製を実装し、このクラスに含まれるすべての追加フィールドを複製することをお勧めします。  
  
 <xref:System.ServiceModel.Channels.TransportBindingElement.Scheme%2A> – <xref:System.ServiceModel.Channels.TransportBindingElement.Scheme%2A> get プロパティは、バインディング要素によって表されるトランスポート プロトコルの URI スキームを返します。 たとえば、<xref:System.ServiceModel.Channels.HttpTransportBindingElement?displayProperty=nameWithType>と<xref:System.ServiceModel.Channels.TcpTransportBindingElement?displayProperty=nameWithType>から、それぞれ"http"および"net.tcp"を返します<xref:System.ServiceModel.Channels.TransportBindingElement.Scheme%2A>プロパティ。  
  
#### <a name="encoding-binding-elements"></a>エンコーディング バインド要素  
 新しいエンコーディング バインド要素を作成するには、まず <xref:System.ServiceModel.Channels.BindingElement> クラスを拡張し、<xref:System.ServiceModel.Channels.MessageEncodingBindingElement?displayProperty=nameWithType> クラスを実装します。 次に、少なくとも、<xref:System.ServiceModel.Channels.BindingElement.Clone%2A> メソッド、<xref:System.ServiceModel.Channels.MessageEncodingBindingElement.CreateMessageEncoderFactory%2A?displayProperty=nameWithType> メソッド、および <xref:System.ServiceModel.Channels.MessageEncodingBindingElement.MessageVersion%2A?displayProperty=nameWithType> プロパティを実装する必要があります。  
  
-   <xref:System.ServiceModel.Channels.BindingElement.Clone%2A>。 このバインド要素の新しいコピーを返します。 最善の方法としては、バインド要素の作成者は基本の copy コンストラクターを呼び出す copy コンストラクターを使用して、<xref:System.ServiceModel.Channels.BindingElement.Clone%2A> を実装し、このクラスに含まれるすべての追加フィールドを複製することをお勧めします。  
  
-   <xref:System.ServiceModel.Channels.MessageEncodingBindingElement.CreateMessageEncoderFactory%2A>。 <xref:System.ServiceModel.Channels.MessageEncoderFactory> を返します。これは、新しいエンコーダーを実装する実際のクラスを識別するハンドルを提供し、<xref:System.ServiceModel.Channels.MessageEncoder> を拡張します。 詳細については、次のトピックを参照してください。 <xref:System.ServiceModel.Channels.MessageEncoderFactory> および <xref:System.ServiceModel.Channels.MessageEncoder>  
  
-   <xref:System.ServiceModel.Channels.MessageEncodingBindingElement.MessageVersion%2A>。 このエンコーディングで使用する <xref:System.ServiceModel.Channels.MessageVersion> を返します。これは、使用する SOAP および WS-Addressing のバージョンを表します。  
  
 ユーザー定義エンコーディング バインド要素のオプション メソッドとプロパティの完全な一覧については、<xref:System.ServiceModel.Channels.MessageEncodingBindingElement> を参照してください。  
  
 新しいバインド要素を作成する方法の詳細については、次を参照してください。[ユーザー定義バインディング](../../../../docs/framework/wcf/extending/creating-user-defined-bindings.md)します。  
  
 チャネルのバインド要素を作成した後に戻り、[開発チャネル](../../../../docs/framework/wcf/extending/developing-channels.md)かどうかをバインド要素に構成ファイルのサポートを追加する場合と、メタデータ ドキュメントのサポートを追加する方法を表示するトピックとかどうかと、バインド要素を使用するユーザー定義のバインディングを構築する方法。  
  
## <a name="see-also"></a>関連項目

- <xref:System.ServiceModel.Channels.BindingElement>
- [チャネルの開発](../../../../docs/framework/wcf/extending/developing-channels.md)
- [トランスポート:UDP](../../../../docs/framework/wcf/samples/transport-udp.md)
