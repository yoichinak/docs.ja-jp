---
title: '方法: クライアント要求のヘッダーを設定する (WCF Data Services)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, customizing requests
ms.assetid: 3d55168d-5901-4f48-8117-6c93da3ab5ae
ms.openlocfilehash: 9267f0e5b68823516764891a40e1435c1325b77f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174343"
---
# <a name="how-to-set-headers-in-the-client-request-wcf-data-services"></a>方法: クライアント要求のヘッダーを設定する (WCF Data Services)
オープン データ プロトコル (OData) をサポートするデータ サービスにアクセスするのには WCF データ サービス クライアント ライブラリを使用すると、クライアント ライブラリは自動的にデータ サービスに送信される要求メッセージに必要な HTTP ヘッダーを設定します。 ただし、クライアント ライブラリでは、データ サービスがクレーム ベース認証やクッキーを要求する場合など、特定の場合に必要とされるメッセージ ヘッダーを設定することはできません。 詳細については、「 [Securing WCF Data Services](securing-wcf-data-services.md#clientAuthentication)」を参照してください。 このような場合は、要求メッセージを送信する前にそのメッセージ ヘッダーを手動で設定する必要があります。 このトピックの例では、<xref:System.Data.Services.Client.DataServiceContext.SendingRequest> イベントを処理して、要求メッセージをデータ サービスに送信する前に新しいヘッダーを要求メッセージに追加する方法を示します。  
  
 このトピックの例では、Northwind サンプル データ サービスおよび自動生成されたクライアント データ サービス クラスを使用します。 このサービスとクライアント データ クラスは、 WCF[データ サービスのクイック スタート](quickstart-wcf-data-services.md)を完了したときに作成されます。 OData Web サイトに公開されている[ノースウィンド サンプル データ サービス](https://services.odata.org/Northwind/Northwind.svc/)を使用することもできます。このサンプル データ サービスは読み取り専用であり、変更を保存しようとするとエラーが返されます。 OData Web サイトのサンプル データ サービスでは、匿名認証が許可されています。  
  
## <a name="example"></a>例  
 次の例では、<xref:System.Data.Services.Client.DataServiceContext.SendingRequest> イベントのハンドラーを登録し、データ サービスに対してクエリを実行します。  
  
> [!NOTE]
> 要求ごとにメッセージ ヘッダーを手動で設定することがデータ サービスで必要とされる場合は、データ サービスを表すエンティティ コンテナー (この場合は <xref:System.Data.Services.Client.DataServiceContext.SendingRequest>) で `OnContextCreated` 部分メソッドをオーバーライドして、`NorthwindEntities` イベントのハンドラーを登録することを検討してください。  
  
[!code-csharp[Astoria Northwind Client#RegisterHeadersQuery](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#registerheadersquery)]
[!code-vb[Astoria Northwind Client#RegisterHeadersQuery](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#registerheadersquery)]
  
## <a name="example"></a>例  
 次のメソッドは、<xref:System.Data.Services.Client.DataServiceContext.SendingRequest> イベントを処理し、認証ヘッダーを要求に追加します。  
  
 [!code-csharp[Astoria Northwind Client#OnSendingRequest](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#onsendingrequest)]  
 [!code-vb[Astoria Northwind Client#OnSendingRequest](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#onsendingrequest)]  
  
## <a name="see-also"></a>関連項目

- [WCF Data Services のセキュリティ保護](securing-wcf-data-services.md)
- [WCF Data Services クライアント ライブラリ](wcf-data-services-client-library.md)
