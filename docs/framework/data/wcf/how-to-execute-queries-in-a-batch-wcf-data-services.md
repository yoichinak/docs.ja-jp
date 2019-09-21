---
title: '方法: バッチでクエリを実行する (WCF Data Services)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, batch requests
ms.assetid: 3b4db7df-bd33-43a1-8ea4-63a18e131f97
ms.openlocfilehash: a825fe83ff62d935740fb69871ba2d1e2120e9ec
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/07/2019
ms.locfileid: "70790494"
---
# <a name="how-to-execute-queries-in-a-batch-wcf-data-services"></a>方法: バッチでクエリを実行する (WCF Data Services)
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]クライアントライブラリを使用すると、データサービスに対して複数のクエリを1つのバッチで実行できます。 詳細については、「[バッチ処理操作](batching-operations-wcf-data-services.md)」を参照してください。  
  
 このトピックの例では、Northwind サンプル データ サービスおよび自動生成されたクライアント データ サービス クラスを使用します。 このサービスとクライアントデータクラスは、 [WCF Data Services のクイックスタート](quickstart-wcf-data-services.md)を完了したときに作成されます。  
  
## <a name="example"></a>例  
 次の例は、<xref:System.Data.Services.Client.DataServiceContext.ExecuteBatch%2A> メソッドを呼び出して、<xref:System.Data.Services.Client.DataServiceRequest%601> オブジェクトと `Customers` オブジェクトの両方を Northwind データ サービスから返すクエリを含む `Products` オブジェクトの配列を実行する方法を示します。 返された <xref:System.Data.Services.Client.QueryOperationResponse%601> 内の <xref:System.Data.Services.Client.DataServiceResponse> オブジェクトのコレクションが列挙され、各 <xref:System.Data.Services.Client.QueryOperationResponse%601> に含まれるオブジェクトのコレクションも列挙されます。  
  
 [!code-csharp[Astoria Northwind Client#BatchQuery](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#batchquery)]
 [!code-vb[Astoria Northwind Client#BatchQuery](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#batchquery)]  
  
## <a name="see-also"></a>関連項目

- [WCF Data Services クライアント ライブラリ](wcf-data-services-client-library.md)
