---
title: '方法: WCF エンドポイントとメッセージ キュー アプリケーションを使用してメッセージを交換する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 62210fd8-a372-4d55-ab9b-c99827d1885e
ms.openlocfilehash: 7fdcebe7ab9ee82a7283add9e0200af2ea5c94bd
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59198973"
---
# <a name="how-to-exchange-messages-with-wcf-endpoints-and-message-queuing-applications"></a>方法: WCF エンドポイントとメッセージ キュー アプリケーションを使用してメッセージを交換する
既存のメッセージ キュー (MSMQ) アプリケーションは、WCF メッセージから MSMQ メッセージの変換に、MSMQ 統合バインディングを使用して、Windows Communication Foundation (WCF) アプリケーションと統合できます。 これにより、WCF クライアントから MSMQ 受信側アプリケーションへの呼び出しと MSMQ の送信元アプリケーションから WCF サービスを呼び出すことができます。  
  
 このセクションで使用する方法を説明します<xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding>(1)、WCF クライアントと System.Messaging と (2) MSMQ アプリケーション クライアントと WCF サービスを使用して記述された MSMQ アプリケーション サービスのキューに置かれた通信します。  
  
 WCF クライアントから MSMQ 受信側のアプリケーションを呼び出す方法を示す完全なサンプルを参照してください、 [Windows Communication Foundation メッセージ キュー](../../../../docs/framework/wcf/samples/wcf-to-message-queuing.md)サンプル。  
  
 MSMQ クライアントから WCF サービスを呼び出す方法を示す完全なサンプルを参照してください、[メッセージ キューが Windows Communication Foundation](../../../../docs/framework/wcf/samples/message-queuing-to-wcf.md)サンプル。  
  
### <a name="to-create-a-wcf-service-that-receives-messages-from-a-msmq-client"></a>MSMQ クライアントからのメッセージを受信する WCF サービスを作成するには  
  
1.  次のコード例に示すように、MSMQ の送信側アプリケーションからキューに置かれたメッセージを受信する WCF サービスのサービス コントラクトを定義するインターフェイスを定義します。  
  
     [!code-csharp[S_MsmqToWcf#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmqtowcf/cs/service.cs#1)]
     [!code-vb[S_MsmqToWcf#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmqtowcf/vb/service.vb#1)]  
  
2.  次のコード例に示すように、定義したインターフェイスを実装し、<xref:System.ServiceModel.ServiceBehaviorAttribute> 属性をクラスに適用します。  
  
     [!code-csharp[S_MsmqToWcf#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmqtowcf/cs/service.cs#2)]
     [!code-vb[S_MsmqToWcf#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmqtowcf/vb/service.vb#2)]  
  
3.  <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> を指定する構成ファイルを作成します。  

4.  構成されたバインディングを使用する <xref:System.ServiceModel.ServiceHost> オブジェクトをインスタンス化します。  

### <a name="to-create-a-wcf-client-that-sends-messages-to-a-msmq-receiver-application"></a>MSMQ の受信側アプリケーションにメッセージを送信する WCF クライアントを作成するには  
  
1.  次のコード例に示すように送信しますが、MSMQ の受信側にメッセージをキューに置かれた WCF クライアントのサービス コントラクトを定義するインターフェイスを定義します。  
  
     [!code-csharp[S_WcfToMsmq#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_wcftomsmq/cs/proxy.cs#6)]
     [!code-vb[S_WcfToMsmq#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_wcftomsmq/vb/proxy.vb#6)]  
  
2.  WCF クライアントが MSMQ の受信側の呼び出しに使用されるクライアント クラスを定義します。  
  
     [!code-csharp[S_WcfToMsmq#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_wcftomsmq/cs/snippets.cs#2)]
     [!code-vb[S_WcfToMsmq#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_wcftomsmq/vb/snippets.vb#2)]  
  
3.  MsmqIntegrationBinding バインディングの使用を指定する構成を作成します。  
  
     [!code-csharp[S_WcfToMsmq#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_wcftomsmq/cs/snippets.cs#3)]
     [!code-vb[S_WcfToMsmq#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_wcftomsmq/vb/snippets.vb#3)]  
  
4.  クライアント クラスのインスタンスを作成し、メッセージ受信サービスによって定義されたメソッドを呼び出します。  
  
     [!code-csharp[S_WcfToMsmq#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_wcftomsmq/cs/client.cs#4)]  
  
## <a name="see-also"></a>関連項目

- [キューの概要](../../../../docs/framework/wcf/feature-details/queues-overview.md)
- [方法: WCF エンドポイントを使用してキューに置かれたメッセージを交換する](../../../../docs/framework/wcf/feature-details/how-to-exchange-queued-messages-with-wcf-endpoints.md)
- [Windows Communication Foundation でのメッセージ キュー](../../../../docs/framework/wcf/samples/wcf-to-message-queuing.md)
- [メッセージ キュー (MSMQ) のインストール](../../../../docs/framework/wcf/samples/installing-message-queuing-msmq.md)
- [Windows Communication Foundation へのメッセージ キュー](../../../../docs/framework/wcf/samples/message-queuing-to-wcf.md)
- [メッセージ キューを介したメッセージ セキュリティ](../../../../docs/framework/wcf/samples/message-security-over-message-queuing.md)
