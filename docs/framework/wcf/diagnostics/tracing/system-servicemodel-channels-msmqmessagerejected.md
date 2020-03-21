---
title: System.ServiceModel.Channels.MsmqMessageRejected
ms.date: 03/30/2017
ms.assetid: 9b7c10a7-2af6-44a2-8b1a-90bba0c7cf26
ms.openlocfilehash: 8f783dcd4b966ed89c24d724918a3923c5a2d0b1
ms.sourcegitcommit: 515469828d0f040e01bde01df6b8e4eb43630b06
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2020
ms.locfileid: "78674770"
---
# <a name="systemservicemodelchannelsmsmqmessagerejected"></a>System.ServiceModel.Channels.MsmqMessageRejected
MSMQ はメッセージを拒否しました。  
  
## <a name="description"></a>説明  
 このトレースは、MSMQ メッセージが拒否されたことを示します。  
  
 MSMQ メッセージは、Windows 通信ファウンデーション (WCF) (NetMsmqBinding または MsmqIntegrationBinding で使用される) がメッセージを処理できない場合に拒否できます。 このようなメッセージは、有害メッセージと呼ばれます。 有害メッセージは、NetMsmqBinding または MsmqIntegrationBinding の `ReceiveErrorHandling` プロパティが `Reject` に設定されると拒否されます。 拒否されたメッセージは、送信者の[配信不能キュー](https://docs.microsoft.com/dotnet/framework/wcf/feature-details/using-dead-letter-queues-to-handle-message-transfer-failures)に戻されます。  
  
 メッセージが有害になるタイミングと、メッセージを適切に処理するようにサービスを設定する方法の詳細については、「 [Poison-Message の処理](../../feature-details/poison-message-handling.md)」を参照してください。  
  
 拒否されたメッセージが MSMQ で何を意味するかの詳細については[、「MQMarkMessageRejected」を参照](https://docs.microsoft.com/previous-versions/windows/desktop/msmq/ms707071(v%3dvs.85))してください。  
  
## <a name="see-also"></a>関連項目

- [トレース](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [トレースを使用したアプリケーションのトラブルシューティング](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [管理と診断](../../../../../docs/framework/wcf/diagnostics/index.md)
- [有害メッセージの処理](../../feature-details/poison-message-handling.md)
- [拒否されたメッセージ](https://docs.microsoft.com/previous-versions/windows/desktop/msmq/ms707071(v%3dvs.85))
