---
title: System.ServiceModel.Channels.MsmqMessageDropped
ms.date: 03/30/2017
ms.assetid: 8b6e644d-fa68-4be7-abe9-3659671a37c1
ms.openlocfilehash: e80fecf508158dcb53f08b75c8f9486c13e403a4
ms.sourcegitcommit: 515469828d0f040e01bde01df6b8e4eb43630b06
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2020
ms.locfileid: "78674796"
---
# <a name="systemservicemodelchannelsmsmqmessagedropped"></a>System.ServiceModel.Channels.MsmqMessageDropped
MSMQ はメッセージを破棄しました。  
  
## <a name="description"></a>説明  
 このトレースは、MSMQ メッセージが破棄されたことを示します。 MSMQ メッセージは、Windows 通信ファウンデーション (WCF) (NetMsmqBinding または MsmqIntegrationBinding で使用される) がそれらを処理できない場合にドロップできます。 このようなメッセージは、有害メッセージと呼ばれます。  
  
 有害メッセージは、NetMsmqBinding または MsmqIntegrationBinding の `ReceiveErrorHandling` プロパティが `Drop` に設定されていると破棄されます。 破棄されたメッセージはキューから削除され、元に戻すことはできません。  
  
 メッセージが有害になるタイミングと、メッセージを適切に処理するようにサービスを設定する方法の詳細については、「 [Poison-Message の処理](../../feature-details/poison-message-handling.md)」を参照してください。  
  
## <a name="see-also"></a>関連項目

- [トレース](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [トレースを使用したアプリケーションのトラブルシューティング](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [管理と診断](../../../../../docs/framework/wcf/diagnostics/index.md)
- [有害メッセージの処理](../../feature-details/poison-message-handling.md)
