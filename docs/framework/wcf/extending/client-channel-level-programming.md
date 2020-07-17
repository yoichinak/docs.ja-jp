---
title: クライアントのチャネル レベルのプログラミング
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 3b787719-4e77-4e77-96a6-5b15a11b995a
ms.openlocfilehash: 4f24c558b1d5303b2417416beb14555539f498ea
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/07/2019
ms.locfileid: "70797274"
---
# <a name="client-channel-level-programming"></a>クライアントのチャネル レベルのプログラミング
このトピックでは、クラスとそれに<xref:System.ServiceModel.ClientBase%601?displayProperty=nameWithType>関連付けられているオブジェクトモデルを使用せずに、Windows Communication Foundation (WCF) クライアントアプリケーションを記述する方法について説明します。  
  
## <a name="sending-messages"></a>メッセージの送信  
 メッセージを送信し、応答を受信して処理できるようにするには、次の手順に従う必要があります。  
  
1. バインディングを作成します。  
  
2. チャネル ファクトリをビルドします。  
  
3. チャネルを作成します。  
  
4. 要求を送信し、応答を読み取ります。  
  
5. すべてのチャネル オブジェクトを閉じます。  
  
#### <a name="creating-a-binding"></a>バインディングの作成  
 受信側のケース (「[サービスチャネルレベルのプログラミング](service-channel-level-programming.md)」を参照) と同様に、メッセージの送信はバインドを作成することによって開始されます。 この例では、新しい <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType> を作成し、その要素コレクションに <xref:System.ServiceModel.Channels.HttpTransportBindingElement?displayProperty=nameWithType> を追加します。  
  
#### <a name="building-a-channelfactory"></a>ChannelFactory のビルド  
 <xref:System.ServiceModel.Channels.IChannelListener?displayProperty=nameWithType> を作成する代わりに、今回はバインディングで型パラメーターを <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType> にして <xref:System.ServiceModel.ChannelFactory.CreateFactory%2A?displayProperty=nameWithType> を呼び出すことで、<xref:System.ServiceModel.Channels.IRequestChannel?displayProperty=nameWithType> を作成します。 チャネル リスナーは受信メッセージを待機する側で使用されますが、チャネル ファクトリはチャネルを作成するために通信を開始する側で使用されます。 チャネル リスナーと同様に、チャネル ファクトリも使用する前に開く必要があります。  
  
#### <a name="creating-a-channel"></a>チャネルの作成  
 次に <xref:System.ServiceModel.ChannelFactory%601.CreateChannel%2A?displayProperty=nameWithType> を呼び出して、<xref:System.ServiceModel.Channels.IRequestChannel> を作成します。 この呼び出しには、新しく作成するチャネルを使用して通信を行う対象となるエンドポイントのアドレスを使用します。 チャネルを作成したら、このチャネルで Open を呼び出して通信できる状態にします。 この Open の呼び出しにより、トランスポートの性質に応じて、目的のエンドポイントとの接続が開始されることもあれば、ネットワーク上では何も起こらないこともあります。  
  
#### <a name="sending-a-request-and-reading-the-reply"></a>要求の送信と応答の読み取り  
 チャネルが開かれると、メッセージを作成して、チャネルの Request メソッドを使用して要求を送信し、応答が返ってくるのを待機できます。 Request メソッドが終了すると、応答メッセージを取得して読み取り、エンドポイントの応答内容を確認できます。  
  
#### <a name="closing-objects"></a>オブジェクトの終了  
 リソースのリークを避けるには、通信に使用したオブジェクトが不要になったら、これを終了します。  
  
 次のコード例に、メッセージを送信して応答を読み取るためにチャネル ファクトリを使用する基本的なクライアントを示します。  
  
 [!code-csharp[ChannelProgrammingBasic#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/channelprogrammingbasic/cs/clientprogram.cs#2)]
 [!code-vb[ChannelProgrammingBasic#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/channelprogrammingbasic/vb/clientprogram.vb#2)]
