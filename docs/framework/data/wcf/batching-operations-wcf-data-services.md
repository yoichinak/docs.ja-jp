---
title: バッチ処理 (WCF Data Services)
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, client library
ms.assetid: 962a49d1-cc11-4b96-bc7d-071dd6607d6c
ms.openlocfilehash: a9f74f025af6dfc5737ea9f4971f68c5ad913e8b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59133602"
---
# <a name="batching-operations-wcf-data-services"></a>バッチ処理 (WCF Data Services)
[!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)]バッチへの要求の処理をサポートしています、 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]-ベースのサービスです。 詳細については、次を参照してください[OData:。バッチ処理](https://go.microsoft.com/fwlink/?LinkId=186075)します。 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]、使用する各操作、<xref:System.Data.Services.Client.DataServiceContext>クエリを実行するなど、別のデータ サービスに送信される要求の結果の変更を保存します。 操作セットの論理スコープを維持するために、操作バッチを明示的に定義する必要があります。 これにより、バッチ内のすべての操作に 1 つの HTTP 要求でデータ サービスに送信されますし、により、操作をアトミックに、処理サーバーと、データ サービスへのラウンド トリップの数が減ること。  
  
## <a name="batching-query-operations"></a>クエリ操作のバッチ処理  
 複数のクエリを 1 つのバッチで実行するには、バッチ内の各クエリを <xref:System.Data.Services.Client.DataServiceRequest%601> クラスの個別のインスタンスとして作成する必要があります。 この方法でクエリ要求を作成すると、クエリ自身が URI として定義されます。このクエリは、リソースのアドレス指定のルールに従います。 詳細については、次を参照してください。[にアクセスするデータ サービス リソース](../../../../docs/framework/data/wcf/accessing-data-service-resources-wcf-data-services.md)します。 バッチ化されたクエリ要求は、クエリ要求オブジェクトを含む <xref:System.Data.Services.Client.DataServiceContext.ExecuteBatch%2A> メソッドが呼び出されたときにデータ サービスに送信されます。 このメソッドは、<xref:System.Data.Services.Client.DataServiceResponse> オブジェクトを返します。このオブジェクトは、バッチ内の個々の要求への応答を表す <xref:System.Data.Services.Client.QueryOperationResponse%601> オブジェクトのコレクションです。個々のオブジェクトには、クエリによって返されるオブジェクトのコレクションまたはエラー情報が含まれます。 バッチ内のいずれかのクエリ操作が失敗した場合、<xref:System.Data.Services.Client.QueryOperationResponse%601> オブジェクトで失敗した操作のエラー情報が返され、残りの操作は引き続き実行されます。 詳細については、「[方法 :クエリをバッチで実行](../../../../docs/framework/data/wcf/how-to-execute-queries-in-a-batch-wcf-data-services.md)します。  
  
 バッチ クエリは、非同期で実行することもできます。 詳細については、次を参照してください。[非同期操作](../../../../docs/framework/data/wcf/asynchronous-operations-wcf-data-services.md)します。  
  
## <a name="batching-the-savechanges-operation"></a>変更の保存操作のバッチ処理  
 呼び出すと、<xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A>メソッドは、トラックとして送信される REST ベースの操作に変換するコンテキストを要求するすべての変更、[!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]サービス。 既定では、これらの変更は 1 つの要求メッセージで送信されません。 すべての変更を 1 つの要求で送信することが必要なを呼び出す必要がある、<xref:System.Data.Services.Client.DataServiceContext.SaveChanges%28System.Data.Services.Client.SaveChangesOptions%29>メソッドの値を含める<xref:System.Data.Services.Client.SaveChangesOptions.Batch>で、<xref:System.Data.Services.Client.SaveChangesOptions>メソッドに指定する列挙。  
  
 バッチ処理された変更を非同期で保存することもできます。 詳細については、次を参照してください。[非同期操作](../../../../docs/framework/data/wcf/asynchronous-operations-wcf-data-services.md)します。  
  
## <a name="see-also"></a>関連項目

- [WCF Data Services クライアント ライブラリ](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)
