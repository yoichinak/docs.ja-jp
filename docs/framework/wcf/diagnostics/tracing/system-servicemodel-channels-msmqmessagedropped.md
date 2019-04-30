---
title: System.ServiceModel.Channels.MsmqMessageDropped
ms.date: 03/30/2017
ms.assetid: 8b6e644d-fa68-4be7-abe9-3659671a37c1
ms.openlocfilehash: 3fa5ec62c5e8ac83f3f81fb406499b7e596b3dac
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61969508"
---
# <a name="systemservicemodelchannelsmsmqmessagedropped"></a>System.ServiceModel.Channels.MsmqMessageDropped
MSMQ はメッセージを破棄しました。  
  
## <a name="description"></a>説明  
 このトレースは、MSMQ メッセージが破棄されたことを示します。 Windows Communication Foundation (WCF) が (NetMsmqBinding または MsmqIntegrationBinding のいずれかで使用) が、それらを処理できない場合は、MSMQ メッセージを削除することができます。 このようなメッセージは、有害メッセージと呼ばれます。  
  
 有害メッセージは、NetMsmqBinding または MsmqIntegrationBinding の `ReceiveErrorHandling` プロパティが `Drop` に設定されていると破棄されます。 破棄されたメッセージはキューから削除され、元に戻すことはできません。  
  
 参照してください[有害メッセージの処理](https://go.microsoft.com/fwlink/?LinkID=99546)メッセージが有害になると、サービスを適切に処理を構成する方法の詳細についてはします。  
  
## <a name="see-also"></a>関連項目

- [トレース](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [トレースを使用したアプリケーションのトラブルシューティング](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [管理と診断](../../../../../docs/framework/wcf/diagnostics/index.md)
- [有害メッセージ処理](https://go.microsoft.com/fwlink/?LinkID=99546)
