---
title: '方法: 一方向コントラクトを作成する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 85084cd9-31cc-4e95-b667-42ef01336622
ms.openlocfilehash: a4996dc963c572e2aeb14b9b366af33b8f23d480
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59208658"
---
# <a name="how-to-create-a-one-way-contract"></a>方法: 一方向コントラクトを作成する
ここでは、一方向コントラクトを使用するメソッドを作成するための基本手順を示します。 このようなメソッドは、クライアントからの Windows Communication Foundation (WCF) サービスで操作を呼び出すが、応答を予期しません。 この種のコントラクトは、たとえば、多数のサブスクライバーに対して通知を発行するために使用できます。 一方向コントラクトは、二重のコントラクトを作成する場合にも使用できます。その場合は、クライアントとサーバーが互いに独立して通信できるため、どちらからでも相手の呼び出しを開始できます。 これにより、特にサーバーは、クライアントがイベントとして処理できる一方向の呼び出しをクライアントに対して実行できます。 一方向メソッドの指定の詳細については、<xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> プロパティおよび <xref:System.ServiceModel.OperationContractAttribute> クラスのトピックを参照してください。  
  
 双方向コントラクトのクライアント アプリケーションの作成の詳細については、次を参照してください。[方法。一方向のサービスにアクセスし、要求/応答コントラクト](../../../../docs/framework/wcf/feature-details/how-to-access-wcf-services-with-one-way-and-request-reply-contracts.md)します。 実際のサンプルでは、次を参照してください。、[一方向](../../../../docs/framework/wcf/samples/one-way.md)サンプル。  
  
### <a name="to-create-a-one-way-contract"></a>一方向コントラクトを作成するには  
  
1.  サービスにより実装されるメソッドを定義するインターフェイスに <xref:System.ServiceModel.ServiceContractAttribute> クラスを適用することにより、サービス コントラクトを作成します。  
  
2.  <xref:System.ServiceModel.OperationContractAttribute> クラスをメソッドに適用する際に、クライアントが呼び出すことのできるインターフェイスのメソッドを指定します。  
  
3.  <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> プロパティを `true` に設定することにより、出力を行わない (戻り値および出力または参照パラメーターを持たない) 一方向の操作を指定します。 <xref:System.ServiceModel.OperationContractAttribute> プロパティの既定値は <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> であるため、`false` クラスを持つ操作では、既定で要求/応答コントラクトが満たされることに注意してください。 したがって、このメソッドに一方向コントラクトが必要な場合は、この属性プロパティの値を明示的に `true` に指定する必要があります。  
  
## <a name="example"></a>例  
 複数の一方向メソッドを含むサービスのコントラクトを定義する方法を次のコード例に示します。 `Equals` (既定で応答/要求コントラクトに設定され、結果を返します) を除き、すべてのメソッドは一方向コントラクトを持ちます。  
  
 [!code-csharp[S_Service_Session#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_service_session/cs/service.cs#1)]
 [!code-vb[S_Service_Session#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_service_session/vb/service.vb#1)]  
  
## <a name="see-also"></a>関連項目

- <xref:System.ServiceModel.ServiceContractAttribute>
- <xref:System.ServiceModel.OperationContractAttribute>
- [サービスの設計と実装](../../../../docs/framework/wcf/designing-and-implementing-services.md)
- [方法: サービス コントラクトを定義する](../../../../docs/framework/wcf/how-to-define-a-wcf-service-contract.md)
- [セッション](../../../../docs/framework/wcf/samples/session.md)
- [方法: 双方向コントラクトを作成する](../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md)
