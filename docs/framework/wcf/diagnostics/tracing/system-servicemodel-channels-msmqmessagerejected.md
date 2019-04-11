---
title: System.ServiceModel.Channels.MsmqMessageRejected
ms.date: 03/30/2017
ms.assetid: 9b7c10a7-2af6-44a2-8b1a-90bba0c7cf26
ms.openlocfilehash: 4feeb1b57d79c7445d51f5d688b0a9f55e761542
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59143391"
---
# <a name="systemservicemodelchannelsmsmqmessagerejected"></a>System.ServiceModel.Channels.MsmqMessageRejected
MSMQ はメッセージを拒否しました。  
  
## <a name="description"></a>説明  
 このトレースは、MSMQ メッセージが拒否されたことを示します。  
  
 Windows Communication Foundation (WCF) が (NetMsmqBinding または MsmqIntegrationBinding のいずれかで使用) が、それらを処理できない場合、MSMQ メッセージを拒否できます。 このようなメッセージは、有害メッセージと呼ばれます。 有害メッセージは、NetMsmqBinding または MsmqIntegrationBinding の `ReceiveErrorHandling` プロパティが `Reject` に設定されると拒否されます。 拒否されたメッセージは、送信者に配信されます[配信不能キュー](https://go.microsoft.com/fwlink/?LinkID=99544)します。  
  
 参照してください[有害メッセージの処理](https://go.microsoft.com/fwlink/?LinkID=99546)メッセージが有害になると、サービスを適切に処理を構成する方法の詳細についてはします。  
  
 参照してください[MQMarkMessageRejected](https://go.microsoft.com/fwlink/?LinkID=99548)拒否されたメッセージは MSMQ では意味の詳細についてはします。  
  
## <a name="see-also"></a>関連項目

- [トレース](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [トレースを使用したアプリケーションのトラブルシューティング](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [管理と診断](../../../../../docs/framework/wcf/diagnostics/index.md)
- [有害メッセージの処理](https://go.microsoft.com/fwlink/?LinkID=99546)
- [MQMarkMessageRejected](https://go.microsoft.com/fwlink/?LinkID=99548)
