---
title: 重要なトレース
ms.date: 03/30/2017
ms.assetid: 40a1770e-3b09-4142-b0dd-f9ef73642074
ms.openlocfilehash: c230c65b4d3fd45c4905d4ae5f4cbbf90e10faad
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61784959"
---
# <a name="significant-traces"></a>重要なトレース
このトピックでは、Windows Communication Foundation (WCF) によって出力される主要なトレースの一部を示します。  
  
## <a name="significant-traces"></a>重要なトレース  
  
|トレース|説明|  
|-----------|-----------------|  
|Message Log トレース|メッセージ ログで、WCF メッセージが記録されたときに、トレースが出力されるときに 機能、`System.ServiceModel.MessageLogging`トレース ソースが有効になっています。 このトレースをクリックすると、メッセージが表示されます。 メッセージには、構成可能なログ ポイントが 4 つ (`ServiceLevelSendRequest`、`TransportSend`、`TransportReceive`、`ServiceLevelReceiveRequest`) あり、これらは、メッセージ ログ トレースの Message Source 属性にも示されます。|  
|Message Received トレース|場合、WCF メッセージが受信したときに、このトレースが出力されます、`System.ServiceModel`トレース ソースが情報レベルか verbose レベルで有効にします。 このトレースはアクティビティのグラフ ビューでメッセージの相関矢印を表示するために必要です。|  
|Message Sent トレース|場合、WCF メッセージが送信されるときに、このトレースが出力されます、`System.ServiceModel`トレース ソースが情報レベルか verbose レベルで有効にします。 このトレースはアクティビティのグラフ ビューでメッセージの相関矢印を表示するために必要です。|  
|Get ChannelEndpointElement|このトレースは、情報レベルで Construct チャネル ファクトリに出力されます。 このトレースには、クライアントが対話しているエンドポイントの説明 (リモート アドレス、バインディング、コントラクト名など) が表示されます。|  
|Get ServiceElement|このトレースは、情報レベルで Construct サービス ホストに出力されます。 サービス コントラクトとバインディングの説明が提供されます。|  
|SocketConnection Create|このトレースは、クライアントによって実行される最初の "プロセス" アクションおよびサービスの "バイトを受信" アクティビティで出力されます。 ローカルとリモートの IP アドレスを提供します。 情報レベルで出力されます。|
