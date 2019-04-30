---
title: Microsoft.Transactions.TransactionBridge.PreparedMessageRetry
ms.date: 03/30/2017
ms.assetid: 2194292d-bf5f-4aef-9336-cd3c4795cb71
ms.openlocfilehash: d8acdb2f94e752860025ee2963aa78682b43b079
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61997894"
---
# <a name="microsofttransactionstransactionbridgepreparedmessageretry"></a>Microsoft.Transactions.TransactionBridge.PreparedMessageRetry
準備メッセージの再試行は、応答しないコーディネーターに送信されました。  
  
## <a name="description"></a>説明  
 ローカル トランザクション マネージャーが一定時間内に応答を受信せず、上位のコーディネーターに準備メッセージを再送信する必要があった場合にトレースされます。  
  
## <a name="troubleshooting"></a>トラブルシューティング  
 応答が時間どおりに配信されない原因となっている可能性のあるネットワークや製品の問題について調査します。  このメッセージが多数表示される場合、インフラストラクチャに問題があるか、または応答時間が異常にかかっていることを示します。 いずれの問題によっても、システム内のトランザクションのスループットが大幅に低下します。  
  
## <a name="see-also"></a>関連項目

- [トレース](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [トレースを使用したアプリケーションのトラブルシューティング](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [管理と診断](../../../../../docs/framework/wcf/diagnostics/index.md)
