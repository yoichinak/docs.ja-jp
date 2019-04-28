---
title: '方法: サービスのメッセージを検査および変更する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 9c5b1cc7-84f3-45f8-9226-d59c278e8c42
ms.openlocfilehash: 87f9cf5040ffb757799c51d598d0755847c5bfd9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61767092"
---
# <a name="how-to-inspect-and-modify-messages-on-the-service"></a>方法: サービスのメッセージを検査および変更する
検査または実装することで、Windows Communication Foundation (WCF) クライアントの受信または送信メッセージを変更することができます、<xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector?displayProperty=nameWithType>をサービス ランタイムに挿入します。 詳細については、次を参照してください。[ディスパッチャーの拡張](../../../../docs/framework/wcf/extending/extending-dispatchers.md)します。 サービスの同等の機能は、<xref:System.ServiceModel.Dispatcher.IClientMessageInspector?displayProperty=nameWithType> です。  
  
### <a name="to-inspect-or-modify-messages"></a>メッセージを検査または変更するには  
  
1. <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector?displayProperty=nameWithType> インターフェイスを実装します。  
  
2. サービス メッセージ インスペクターを容易に挿入したいスコープに応じて、<xref:System.ServiceModel.Description.IServiceBehavior?displayProperty=nameWithType>、<xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=nameWithType>、または <xref:System.ServiceModel.Description.IContractBehavior?displayProperty=nameWithType> インターフェイスを実装します。  
  
3. <xref:System.ServiceModel.ICommunicationObject.Open%2A?displayProperty=nameWithType> で <xref:System.ServiceModel.ServiceHost?displayProperty=nameWithType> メソッドを呼び出す前に、動作を挿入します。 詳細については、次を参照してください。[構成と、ランタイムの動作を拡張](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)します。  
  
## <a name="example"></a>例  
 下のコード例では、次の項目を順番に示しています。  
  
- サービス インスペクターの実装  
  
- インスペクターを挿入するサービス動作  
  
- サービス アプリケーションに動作を読み込んで実行する構成ファイル  
  
 [!code-csharp[Interceptors#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/interceptors/cs/interceptors.cs#7)]
 [!code-vb[Interceptors#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/interceptors/vb/interceptors.vb#7)]  
  
 [!code-csharp[Interceptors#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/interceptors/cs/insertingbehaviors.cs#8)]
 [!code-vb[Interceptors#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/interceptors/vb/insertingbehaviors.vb#8)]  
  
 [!code-xml[Interceptors#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/interceptors/cs/hostapplication.exe.config#9)]  
  
## <a name="see-also"></a>関連項目

- <xref:System.ServiceModel.Dispatcher.IClientMessageInspector?displayProperty=nameWithType>
- <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector?displayProperty=nameWithType>
- [動作を使用したランタイムの構成と拡張](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)
