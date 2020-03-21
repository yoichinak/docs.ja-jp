---
title: System.ServiceModel.Channels.MsmqPoisonMessageRejected
ms.date: 03/30/2017
ms.assetid: 0e64b9bd-1f12-43df-a189-d7be3c2bace1
ms.openlocfilehash: 6b0e6e3ebcf5d414e9dbbcecd09ba2e8bb3ddd3a
ms.sourcegitcommit: 515469828d0f040e01bde01df6b8e4eb43630b06
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2020
ms.locfileid: "78674808"
---
# <a name="systemservicemodelchannelsmsmqpoisonmessagerejected"></a>System.ServiceModel.Channels.MsmqPoisonMessageRejected
有害メッセージは拒否されました。  
  
## <a name="description"></a>説明  

 このトレースは、有害メッセージが検出され、続いて拒否されたことを示します。 これは、NetMsmqBinding または MsmqIntegrationBinding の `ReceiveErrorHandling` プロパティが `Reject` に設定されると発生します。 拒否されたメッセージは、送信者の[配信不能キュー](../../feature-details/using-dead-letter-queues-to-handle-message-transfer-failures.md)に戻されます。  
  
 メッセージが有害になるタイミングと、メッセージを適切に処理するようにサービスを設定する方法の詳細については、「 [Poison-Message の処理](../../feature-details/poison-message-handling.md)」を参照してください。 拒否されたメッセージが MSMQ で何を意味するかの詳細については[、「MQMarkMessageRejected」を参照](https://docs.microsoft.com/previous-versions/windows/desktop/msmq/ms707071(v%3dvs.85))してください。  
  
## <a name="see-also"></a>関連項目

- [トレース](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [トレースを使用したアプリケーションのトラブルシューティング](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [管理と診断](../../../../../docs/framework/wcf/diagnostics/index.md)
- [有害メッセージの処理](../../feature-details/poison-message-handling.md)
- [拒否されたメッセージ](https://docs.microsoft.com/previous-versions/windows/desktop/msmq/ms707071(v%3dvs.85))
