---
title: チャネルの開発
ms.date: 03/30/2017
ms.assetid: 0513af9f-a0c2-457b-9a50-5b6bfee48513
ms.openlocfilehash: 44fb0da52c60b900c41b7b497861c12ed72d8ffc
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61858066"
---
# <a name="developing-channels"></a>チャネルの開発
Windows Communication Foundation (WCF) で使用できるプロトコルまたはトランスポート チャネルの開発には、アプリケーション層には、いくつかの手順が必要です。 このトピックでは、これらの手順について説明し、詳細情報の参照先となる特定のトピックを示します。 チャネル モデルと、このトピックに記載されているさまざまな種類についてを参照してください。[チャネル モデルの概要](../../../../docs/framework/wcf/extending/channel-model-overview.md)します。 完全なトランスポート チャネルのサンプルでは、次を参照してください。[トランスポート。UDP](../../../../docs/framework/wcf/samples/transport-udp.md)します。  
  
## <a name="the-channel-development-task-list"></a>チャネル開発タスクの一覧  
 ユーザー定義チャネルを作成する手順は、次のとおりです。 すべてのチャネルで、次の手順が必要です。  
  
1. <xref:System.ServiceModel.Channels.IOutputChannel> と <xref:System.ServiceModel.Channels.IInputChannel> で、チャネルのメッセージ交換パターン (<xref:System.ServiceModel.Channels.IDuplexChannel>、<xref:System.ServiceModel.Channels.IRequestChannel>、<xref:System.ServiceModel.Channels.IReplyChannel>、<xref:System.ServiceModel.Channels.IChannelFactory>、または <xref:System.ServiceModel.Channels.IChannelListener>) のうちのどれをサポートするか、また、選択したパターンでこれらのインターフェイスのセッションの多いバリエーションをサポートするかどうかを決定します。 詳細については、次を参照してください。[メッセージ交換パターンの選択](../../../../docs/framework/wcf/extending/choosing-a-message-exchange-pattern.md)します。  
  
2. 選択したメッセージ交換パターンをサポートするチャネル ファクトリおよびリスナー (<xref:System.ServiceModel.Channels.IChannelFactory> および <xref:System.ServiceModel.Channels.IChannelListener>) を作成します。 ファクトリの開発に関する詳細については、次を参照してください。[クライアント。チャネル ファクトリとチャネル](../../../../docs/framework/wcf/extending/client-channel-factories-and-channels.md)します。 リスナーの開発に関する詳細については、次を参照してください。[サービス。チャネル リスナーとチャネル](../../../../docs/framework/wcf/extending/service-channel-listeners-and-channels.md)します。  
  
3. ネットワーク固有の例外が、<xref:System.TimeoutException?displayProperty=nameWithType> の適切な派生クラスまたは <xref:System.ServiceModel.CommunicationException> に標準化されていることを確認します。 詳細については、次を参照してください。[例外の処理とエラー](../../../../docs/framework/wcf/extending/handling-exceptions-and-faults.md)します。  
  
4. アプリケーション レイヤーから使用できるようにするには、カスタム チャネルを追加する <xref:System.ServiceModel.Channels.BindingElement> をチャネル スタックに追加します。 詳細については、次を参照してください。 [BindingElement の作成](../../../../docs/framework/wcf/extending/creating-a-bindingelement.md)です。  
  
 アプリケーション レイヤーでより完全なサポートを実現するには、次の追加手順が必要です。  
  
1. バインド要素拡張セクションを追加して、新しいバインド要素を構成システムに公開します。 詳細については、次を参照してください。[構成とメタデータのサポート](../../../../docs/framework/wcf/extending/configuration-and-metadata-support.md)します。  
  
2. 他のエンドポイントに機能を伝達するメタデータ拡張を追加します。 詳細については、次を参照してください。[構成とメタデータのサポート](../../../../docs/framework/wcf/extending/configuration-and-metadata-support.md)します。  
  
3. 適切に定義されたプロファイルに従って、バインド要素のスタックを事前構成するバインディングを追加します。 詳細については、次を参照してください。[ユーザー定義バインディング](../../../../docs/framework/wcf/extending/creating-user-defined-bindings.md)します。  
  
4. 構成システムにバインディングを開示する、バインディング セクションおよびバインド構成要素を追加します。 詳細については、次を参照してください。[構成とメタデータのサポート](../../../../docs/framework/wcf/extending/configuration-and-metadata-support.md)します。  
  
## <a name="see-also"></a>関連項目

- [バインディングの拡張](../../../../docs/framework/wcf/extending/extending-bindings.md)
