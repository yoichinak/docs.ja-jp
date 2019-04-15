---
title: クライアント:チャネル ファクトリとチャネル
ms.date: 03/30/2017
ms.assetid: ef245191-fdab-4468-a0da-7c6f25d2110f
ms.openlocfilehash: bfa5d2478d5c12f16c2d9531de02e1c868eab560
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59166258"
---
# <a name="client-channel-factories-and-channels"></a>クライアント:チャネル ファクトリとチャネル
ここでは、チャネル ファクトリとチャネルの作成について説明します。  
  
## <a name="channel-factories-and-channels"></a>チャネル ファクトリとチャネル  
 チャネル ファクトリには、チャネルを作成する役割があります。 チャネル ファクトリによって作成されるチャネルは、メッセージの送信に使用されます。 このチャネルは、上の層からメッセージを取得し、必要な処理を実行し、そのメッセージを下の層に送信する必要があります。 このプロセスを説明する図を次に示します。  
  
 ![クライアント ファクトリおよびチャネル](../../../../docs/framework/wcf/extending/media/wcfc-wcfchannelsigure2highlevelfactgoriesc.gif "wcfc_WCFChannelsigure2HIghLevelFactgoriesc")  
チャネル ファクトリがチャネルを作成します。  
  
 終了時に、チャネル ファクトリは、作成したチャネルのうちまだ閉じていないチャネルを閉じる必要があります。 チャネル リスナーを閉じたとき、新しいチャネルの受け入れだけが停止され、既存のチャネルは開いたままで、メッセージの受信を続行できるので、ここに示すモデルは非対称です。  
  
 WCF では、このプロセスの基本クラス ヘルパーを提供します。 (このトピックで説明するチャネル ヘルパー クラスの図では、次を参照してください[チャネル モデルの概要](../../../../docs/framework/wcf/extending/channel-model-overview.md)。)。  
  
-   <xref:System.ServiceModel.Channels.CommunicationObject>クラスが実装する<xref:System.ServiceModel.ICommunicationObject>および適用のステップ 2 で説明されているステート マシン[開発チャネル](../../../../docs/framework/wcf/extending/developing-channels.md)します。  
  
-   <xref:System.ServiceModel.Channels.ChannelManagerBase> クラスには <xref:System.ServiceModel.Channels.CommunicationObject> が実装され、<xref:System.ServiceModel.Channels.ChannelFactoryBase?displayProperty=nameWithType> と <xref:System.ServiceModel.Channels.ChannelListenerBase?displayProperty=nameWithType> の統合基本クラスが提供されます。 <xref:System.ServiceModel.Channels.ChannelManagerBase> クラスは、<xref:System.ServiceModel.Channels.ChannelBase> を実装する基本クラスである <xref:System.ServiceModel.Channels.IChannel> との組み合わせによって動作します。
  
-   <xref:System.ServiceModel.Channels.ChannelFactoryBase>クラスが実装する<xref:System.ServiceModel.Channels.ChannelManagerBase>と<xref:System.ServiceModel.Channels.IChannelFactory>し、統合、`CreateChannel`を 1 つにオーバー ロード`OnCreateChannel`抽象メソッド。
  
-   <xref:System.ServiceModel.Channels.ChannelListenerBase> クラスは、<xref:System.ServiceModel.Channels.IChannelListener> を実装しています。 基本状態管理を行います。 
  
 次の説明がに基づいて、[トランスポート。UDP](../../../../docs/framework/wcf/samples/transport-udp.md)サンプル。  
  
### <a name="creating-a-channel-factory"></a>チャネル ファクトリの作成  
 `UdpChannelFactory` は <xref:System.ServiceModel.Channels.ChannelFactoryBase> から派生します。 サンプルでは、<xref:System.ServiceModel.Channels.ChannelFactoryBase.GetProperty%2A> をオーバーライドして、メッセージ エンコーダーのメッセージ バージョンにアクセスできるようにします。 さらに、<xref:System.ServiceModel.Channels.ChannelFactoryBase.OnClose%2A> をオーバーライドして、ステート マシンの移行時に <xref:System.ServiceModel.Channels.BufferManager> のインスタンスを破棄します。  
  
#### <a name="the-udp-output-channel"></a>UDP 出力チャネル  
 `UdpOutputChannel` では、<xref:System.ServiceModel.Channels.IOutputChannel> が実装されます。 このコンストラクターは、引数を検証し、渡される <xref:System.Net.EndPoint> に基づいて出力先の <xref:System.ServiceModel.EndpointAddress> オブジェクトを構築します。  
  
 <xref:System.ServiceModel.Channels.CommunicationObject.OnOpen%2A> のオーバーライドによって、この <xref:System.Net.EndPoint> にメッセージを送信するために使用されるソケットが作成されます。  
  
 ```csharp 
this.socket = new Socket(  
this.remoteEndPoint.AddressFamily,
   SocketType.Dgram,
   ProtocolType.Udp
);  
```  

 チャネルが閉じる際には、正常終了することも異常終了することもあります。 チャネルが正常に閉じた場合はソケットも終了し、基本クラスの `OnClose` メソッドが呼び出されます。 このときに例外がスローされると、インフラストラクチャによって `Abort` が呼び出され、チャネルがクリーンアップされます。  
  
```csharp  
this.socket.Close();  
base.OnClose(timeout);  
```  
  
 実装`Send()`と`BeginSend()` /`EndSend()`します。 この実装は、2 つの主要セクションに分かれます。 最初に、メッセージを次のようにシリアル化してバイト配列で表します。  
  
```csharp  
ArraySegment<byte> messageBuffer = EncodeMessage(message);  
```  
  
 次に、結果として生成されたデータを次のようにネットワークに送信します。  
  
```csharp  
this.socket.SendTo(  
  messageBuffer.Array,   
  messageBuffer.Offset,   
  messageBuffer.Count,   
  SocketFlags.None,   
  this.remoteEndPoint  
);  
```  
  
## <a name="see-also"></a>関連項目

- [チャネルの開発](../../../../docs/framework/wcf/extending/developing-channels.md)
