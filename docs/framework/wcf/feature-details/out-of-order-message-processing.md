---
title: 順番を無視したメッセージの処理
ms.date: 03/30/2017
ms.assetid: 33fc62a5-5d59-461c-a37a-0e1b51ac763d
ms.openlocfilehash: 4e1864b25a4dbe8192cd5c692c75645bebbb92d2
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59141402"
---
# <a name="out-of-order-message-processing"></a>順番を無視したメッセージの処理
ワークフロー サービスは、特定の順序で送信されるメッセージに依存する場合があります。 ワークフロー サービスには 1 つ以上の <xref:System.ServiceModel.Activities.Receive> アクティビティが含まれ、それぞれの <xref:System.ServiceModel.Activities.Receive> アクティビティは特定のメッセージに対応しています。 特定のトランスポート配信保証がないと、クライアントから送信されるメッセージに遅延が生じ、それによって、ワークフロー サービスが予期しない順序でメッセージが配信されることがあります。 特定の順序でメッセージが送信されることを必要としないワークフローは、通常、Parallel アクティビティを使用して実装されます。 アプリケーション プロトコルがより複雑な場合は、ワークフローがすぐに複雑になります。  Windows Communication Foundation (WCF) 機能の処理順序のメッセージの入れ子になった並列アクティビティの複雑さがすべてないこのようなワークフローを作成することができます。 順序のメッセージの処理のみをサポートするチャネルでサポートされて<xref:System.ServiceModel.Channels.ReceiveContext>WCF MSMQ バインディングなど。  
  
## <a name="enabling-out-of-order-message-processing"></a>順番を無視したメッセージ処理の有効化  
 順番を無視したメッセージ処理は、ワークフロー サービスで <xref:System.ServiceModel.Activities.WorkflowService.AllowBufferedReceive%2A> プロパティを `true` に設定することで有効化できます。 次の例は、コードで <xref:System.ServiceModel.Activities.WorkflowService.AllowBufferedReceive%2A> プロパティを設定する方法を示しています。  
  
```csharp  
// Code: Opt-in to Buffered Receive processing...  
WorkflowService service = new WorkflowService  
{  
    Name="MyService",  
    Body = workflow,  
    AllowBufferedReceive = true  
};  
```  
  
 また、次の例に示すように、XAML で `AllowBufferedReceive` 属性をワークフロー サービスに適用することもできます。  
  
```xaml  
// Xaml: Opt-in to Buffered Receive processing...  
<WorkflowService AllowBufferedReceive="True">  
   <!--the actual children activities -->  
</Sequence>  
```  
  
## <a name="see-also"></a>関連項目

- <xref:System.ServiceModel.Channels.ReceiveContext>
- [ワークフロー サービス](../../../../docs/framework/wcf/feature-details/workflow-services.md)
- [キューと信頼できるセッション](../../../../docs/framework/wcf/feature-details/queues-and-reliable-sessions.md)
