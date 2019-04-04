---
title: '方法: サービスのメッセージ検査および変更'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 9c5b1cc7-84f3-45f8-9226-d59c278e8c42
ms.openlocfilehash: 19487d3f401260a7a32e9aab63b8c2a75feccbd1
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/23/2019
ms.locfileid: "54599635"
---
# <a name="how-to-inspect-and-modify-messages-on-the-service"></a>方法: サービスのメッセージ検査および変更
検査または実装することで、Windows Communication Foundation (WCF) クライアントの受信または送信メッセージを変更することができます、<xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector?displayProperty=nameWithType>をサービス ランタイムに挿入します。 詳細については、[ディスパッチャーの拡張](../../../../docs/framework/wcf/extending/extending-dispatchers.md)を参照してください。 サービスの同等の機能は、<xref:System.ServiceModel.Dispatcher.IClientMessageInspector?displayProperty=nameWithType> です。  
  
### <a name="to-inspect-or-modify-messages"></a>メッセージを検査または変更するには  
  
1.  <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector?displayProperty=nameWithType> インターフェイスを実装します。  
  
2.  サービス メッセージ インスペクターを容易に挿入したいスコープに応じて、<xref:System.ServiceModel.Description.IServiceBehavior?displayProperty=nameWithType>、<xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=nameWithType>、または <xref:System.ServiceModel.Description.IContractBehavior?displayProperty=nameWithType> インターフェイスを実装します。  
  
3.  <xref:System.ServiceModel.ICommunicationObject.Open%2A?displayProperty=nameWithType> で <xref:System.ServiceModel.ServiceHost?displayProperty=nameWithType> メソッドを呼び出す前に、動作を挿入します。 詳細については、[構成と、ランタイムの動作を拡張](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)を参照してください。  
  
## <a name="example"></a>例  
 下のコード例では、次の項目を順番に示しています。  
  
-   サービス インスペクターの実装  
  
-   インスペクターを挿入するサービス動作  
  
-   サービス アプリケーションに動作を読み込んで実行する構成ファイル  
  
 [!code-csharp[Interceptors#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/interceptors/cs/interceptors.cs#7)]
 [!code-vb[Interceptors#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/interceptors/vb/interceptors.vb#7)]  
  
 [!code-csharp[Interceptors#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/interceptors/cs/insertingbehaviors.cs#8)]
 [!code-vb[Interceptors#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/interceptors/vb/insertingbehaviors.vb#8)]  
  
 [!code-xml[Interceptors#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/interceptors/cs/hostapplication.exe.config#9)]  
  
## <a name="see-also"></a>関連項目
- <xref:System.ServiceModel.Dispatcher.IClientMessageInspector?displayProperty=nameWithType>
- <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector?displayProperty=nameWithType>
- [動作を使用したランタイムの構成と拡張](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)
