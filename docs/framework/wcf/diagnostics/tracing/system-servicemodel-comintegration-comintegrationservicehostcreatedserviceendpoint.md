---
title: System.ServiceModel.Channels.MsmqMoveOrDeleteAttemptFailed
ms.date: 03/30/2017
ms.assetid: d75d39da-7502-4a6a-91b9-eaa05b8e24d5
ms.openlocfilehash: f89dd1373d67714046f8cb958582c3a5dea04456
ms.sourcegitcommit: 515469828d0f040e01bde01df6b8e4eb43630b06
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2020
ms.locfileid: "78674790"
---
# <a name="systemservicemodelchannelsmsmqmoveordeleteattemptfailed"></a>System.ServiceModel.Channels.MsmqMoveOrDeleteAttemptFailed
メッセージを移動または削除できません。  
  
## <a name="description"></a>説明  
 このトレースは、MSMQ メッセージの移動、削除、または拒否の試行中にエラーが発生したことを示しています。  
  
 MSMQ メッセージは、Windows コミュニケーション ファウンデーション (WCF) によって使用されます (NetMsmq バインドまたは Msmq 統合バインドのいずれかで使用される場合)。このトレースは、NetMsmqBinding または`ReceiveErrorHandling`MsmqIntegrationBinding で選択されたプロパティの値に関連付けられています。  
  
 このトレースはシステム全体についてのエラーを示すものではありません。 ただし、選択した有害メッセージの処置に失敗したことを示しています。 メッセージが有害になるタイミングと、メッセージを適切に処理するようにサービスを設定する方法の詳細については、「 [Poison-Message の処理](../../feature-details/poison-message-handling.md)」を参照してください。  
  
## <a name="see-also"></a>関連項目

- [トレース](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [トレースを使用したアプリケーションのトラブルシューティング](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [管理と診断](../../../../../docs/framework/wcf/diagnostics/index.md)
