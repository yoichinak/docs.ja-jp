---
title: '方法: 双方向コントラクトを作成する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- duplex contracts [WCF]
ms.assetid: 500a75b6-998a-47d5-8e3b-24e3aba2a434
ms.openlocfilehash: 002c94f2cb69e330e8d2796a9f93d977b10f53f9
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59078175"
---
# <a name="how-to-create-a-duplex-contract"></a>方法: 双方向コントラクトを作成する
ここでは、双方向コントラクトを使用するメソッドを作成するための基本手順を示します。 双方向コントラクトでは、クライアントとサーバーが互いに独立して通信できるため、どちらからでも相手の呼び出しを開始できます。 双方向コントラクトでは、Windows Communication Foundation (WCF) サービスで使用できる 3 つのメッセージ パターンの 1 つです。 他の 2 つのメッセージ パターンは、一方向および要求/応答です。 双方向コントラクトは、クライアントとサーバー間の 2 つの一方向コントラクトで構成され、メソッドの呼び出しが相互に関連付けられている必要はありません。 サービスでクライアントに詳細を照会したり、クライアントで明示的にイベントを発生させたりする必要がある場合は、この種のコントラクトを使用します。 双方向コントラクトのクライアント アプリケーションの作成の詳細については、次を参照してください。[方法。双方向コントラクトでサービスへのアクセス](../../../../docs/framework/wcf/feature-details/how-to-access-services-with-a-duplex-contract.md)します。 実際のサンプルでは、次を参照してください。、[双方向](../../../../docs/framework/wcf/samples/duplex.md)サンプル。  
  
### <a name="to-create-a-duplex-contract"></a>双方向コントラクトを作成するには  
  
1.  双方向コントラクトのサーバー側を構成するインターフェイスを作成します。  
  
2.  インターフェイスに <xref:System.ServiceModel.ServiceContractAttribute> クラスを適用します。  
  
     [!code-csharp[S_WS_DualHttp#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_ws_dualhttp/cs/service.cs#3)]
     [!code-vb[S_WS_DualHttp#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_ws_dualhttp/vb/service.vb#3)]  
  
3.  インターフェイスでメソッド署名を宣言します。  
  
4.  パブリック コントラクトの一部であることが必要な各メソッド シグネチャに、<xref:System.ServiceModel.OperationContractAttribute> クラスを適用します。  
  
5.  クライアントでサービスが呼び出すことができる一連の操作を定義するコールバック インターフェイスを作成します。  
  
     [!code-csharp[S_WS_DualHttp#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_ws_dualhttp/cs/service.cs#4)]
     [!code-vb[S_WS_DualHttp#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_ws_dualhttp/vb/service.vb#4)]  
  
6.  コールバック インターフェイスでメソッド署名を宣言します。  
  
7.  パブリック コントラクトの一部であることが必要な各メソッド シグネチャに、<xref:System.ServiceModel.OperationContractAttribute> クラスを適用します。  
  
8.  プライマリ インターフェイスの <xref:System.ServiceModel.ServiceContractAttribute.CallbackContract%2A> プロパティをコールバック インターフェイスの型に設定することにより、2 つのインターフェイスを双方向コントラクトにリンクします。  
  
### <a name="to-call-methods-on-the-client"></a>クライアントでメソッドを呼び出すには  
  
1.  サービスのプライマリ コントラクトの実装で、コールバック インターフェイスの変数を宣言します。  
  
2.  <xref:System.ServiceModel.OperationContext.GetCallbackChannel%2A> クラスの <xref:System.ServiceModel.OperationContext> メソッドから返されるオブジェクト参照に変数を設定します。  
  
     [!code-csharp[S_WS_DualHttp#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_ws_dualhttp/cs/service.cs#1)]
     [!code-vb[S_WS_DualHttp#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_ws_dualhttp/vb/service.vb#1)]  
  
     [!code-csharp[S_WS_DualHttp#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_ws_dualhttp/cs/service.cs#2)]
     [!code-vb[S_WS_DualHttp#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_ws_dualhttp/vb/service.vb#2)]  
  
3.  コールバック インターフェイスで定義されたメソッドを呼び出します。  
  
## <a name="example"></a>例  
 次のコード例は、双方向通信を示しています。 サービスのコントラクトには、順方向および逆方向に移動するためのサービス操作が含まれます。 クライアントのコントラクトには、位置を報告するためのサービス操作が含まれます。  
  
 [!code-csharp[S_WS_DualHttp#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_ws_dualhttp/cs/service.cs#5)]
 [!code-vb[S_WS_DualHttp#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_ws_dualhttp/vb/service.vb#5)]  
  
-   <xref:System.ServiceModel.ServiceContractAttribute> 属性と <xref:System.ServiceModel.OperationContractAttribute> 属性を適用すると、サービス コントラクトの定義を Web サービス記述言語 (WSDL) で自動的に生成できます。  
  
-   使用して、 [ServiceModel メタデータ ユーティリティ ツール (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) WSDL ドキュメントと (省略可能) コードとクライアントの構成を取得します。  
  
-   双方向サービスを公開しているエンドポイントは、セキュリティで保護されている必要があります。 サービスが双方向メッセージを受信すると、その受信メッセージの ReplyTo を参照して応答の送信先を決定します。 チャネルがセキュリティで保護されていない場合、信頼関係のないクライアントが対象コンピューターの ReplyTo を使用して悪意のあるメッセージを送信し、その対象コンピューターのサービス拒否 (DOS: Denial Of Service) を引き起こす可能性があります。 通常の要求/応答メッセージでは、ReplyTo は無視され、元のメッセージを受信したチャネルで応答が送信されます。したがって、この問題は発生しません。  
  
## <a name="see-also"></a>関連項目

- <xref:System.ServiceModel.ServiceContractAttribute>
- <xref:System.ServiceModel.OperationContractAttribute>
- [方法: 双方向コントラクトを使用してサービスにアクセスする](../../../../docs/framework/wcf/feature-details/how-to-access-services-with-a-duplex-contract.md)
- [二重](../../../../docs/framework/wcf/samples/duplex.md)
- [サービスの設計と実装](../../../../docs/framework/wcf/designing-and-implementing-services.md)
- [方法: サービス コントラクトを定義する](../../../../docs/framework/wcf/how-to-define-a-wcf-service-contract.md)
- [セッション](../../../../docs/framework/wcf/samples/session.md)
