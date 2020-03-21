---
title: サービス操作の呼び出し (WCF Data Services)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1767f3a7-29d2-4834-a763-7d169693fa8b
ms.openlocfilehash: 41aac38cec97ae1afdd3c3c051d04ff242e7729d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174356"
---
# <a name="calling-service-operations-wcf-data-services"></a>サービス操作の呼び出し (WCF Data Services)
オープン データ プロトコル (OData) は、データ サービスのサービス操作を定義します。 WCF データ サービスでは、データ サービスのメソッドなどの操作を定義できます。 他のデータ サービス リソースと同様に、これらのサービス操作は URI によってアドレス指定できます。 サービス操作では、エンティティ型のコレクション、1 つのエンティティ型のインスタンス、およびプリミティブ型 (整数、文字列など) を返すことができます。 さらに、サービス操作では、`null` (Visual Basic の場合は `Nothing`) を返すこともできます。 WCF データ サービス クライアント ライブラリを使用して、HTTP GET 要求をサポートするサービス操作にアクセスできます。 この種のサービス操作は、<xref:System.ServiceModel.Web.WebGetAttribute> が適用されたメソッドとして定義されます。 詳細については、「[サービス操作](service-operations-wcf-data-services.md)」を参照してください。  
  
 サービス操作は、OData を実装するデータ サービスによって返されるメタデータで公開されます。 メタデータ内で、サービス操作は、`FunctionImport` 要素として表されます。 厳密に型指定された <xref:System.Data.Services.Client.DataServiceContext> を生成するとき、この要素は "サービス参照の追加" と DataSvcUtil.exe ツールで無視されます。 このため、サービス操作を直接呼び出すために使用できるコンテキストにはメソッドはありません。 ただし、WCF データ サービス クライアントを使用して、次の 2 つの方法のいずれかでサービス操作を呼び出すことができます。  
  
- <xref:System.Data.Services.Client.DataServiceContext.Execute%2A> で <xref:System.Data.Services.Client.DataServiceContext> メソッドを呼び出し、サービス操作の URI をその他のパラメーターと共に指定します。 このメソッドは、GET サービス操作の呼び出しに使用されます。  
  
- <xref:System.Data.Services.Client.DataServiceContext.CreateQuery%2A> の <xref:System.Data.Services.Client.DataServiceContext> メソッドを使用して、<xref:System.Data.Services.Client.DataServiceQuery%601> オブジェクトを作成します。 <xref:System.Data.Services.Client.DataServiceContext.CreateQuery%2A> を呼び出すとき、サービス操作の名前が `entitySetName` パラメーターに渡されます。 このメソッドは、列挙されたときまたは <xref:System.Data.Services.Client.DataServiceQuery%601> メソッドが呼び出されたときにサービス操作を呼び出す <xref:System.Data.Services.Client.DataServiceQuery%601.Execute%2A> オブジェクトを返します。 このメソッドは、コレクションを返す GET サービス操作の呼び出しに使用されます。 1 つのパラメーターは、<xref:System.Data.Services.Client.DataServiceQuery%601.AddQueryOption%2A> メソッドを使用して指定することができます。 このメソッドによって返される <xref:System.Data.Services.Client.DataServiceQuery%601> オブジェクトは、クエリ オブジェクトのようにさらに構成できます。 詳細については、「[データ サービスのクエリ 」](querying-the-data-service-wcf-data-services.md)を参照してください。  
  
## <a name="considerations-for-calling-service-operations"></a>サービス操作の呼び出しに関する考慮事項  
 WCF データ サービス クライアントを使用してサービス操作を呼び出す場合は、次の考慮事項が適用されます。  
  
- データ サービスに非同期でアクセスする場合は、 で同等の<xref:System.Data.Services.Client.DataServiceContext.BeginExecute%2A>/<xref:System.Data.Services.Client.DataServiceContext.EndExecute%2A>非同期メソッド<xref:System.Data.Services.Client.DataServiceContext>を使用<xref:System.Data.Services.Client.DataServiceQuery%601.BeginExecute%2A>/<xref:System.Data.Services.Client.DataServiceQuery%601.EndExecute%2A>するか、<xref:System.Data.Services.Client.DataServiceQuery%601>または のメソッドを使用する必要があります。  
  
- WCF データ サービス クライアント ライブラリでは、プリミティブ型のコレクションを返すサービス操作からの結果を具体化できません。  
  
- WCF データ サービス クライアント ライブラリは、POST サービス操作の呼び出しをサポートしていません。 HTTP POST によって呼び出されるサービス操作は、<xref:System.ServiceModel.Web.WebInvokeAttribute> に `Method="POST"` パラメーターを使用して定義します。 HTTP POST 要求を使用してサービス操作を呼び出すには、代わりに <xref:System.Net.HttpWebRequest> を使用する必要があります。  
  
- <xref:System.Data.Services.Client.DataServiceContext.CreateQuery%2A> を使用して、エンティティまたはプリミティブ型の単一の結果を返す GET サービス操作または 1 つ以上の入力パラメーターを必要とする GET サービス操作を呼び出すことはできません。 代わりに <xref:System.Data.Services.Client.DataServiceContext.Execute%2A> メソッドを呼び出す必要があります。  
  
- ツールによって生成される厳密に型指定された <xref:System.Data.Services.Client.DataServiceContext> 部分クラスで <xref:System.Data.Services.Client.DataServiceContext.CreateQuery%2A> メソッドまたは <xref:System.Data.Services.Client.DataServiceContext.Execute%2A> メソッドを使用してサービス操作を呼び出す拡張メソッドを作成することを検討してください。 これにより、コンテキストから直接サービス操作を呼び出すことができます。 詳細については、ブログの投稿[サービス操作と WCF データ サービス クライアントを参照してください](https://docs.microsoft.com/archive/blogs/astoriateam/service-operations-and-the-wcf-data-services-client)。  
  
- サービス<xref:System.Data.Services.Client.DataServiceContext.CreateQuery%2A>操作を呼び出すときに、クライアント ライブラリは、予約された文字 (<xref:System.Data.Services.Client.DataServiceQuery%601.AddQueryOption%2A>アンパサンド (&) などのパーセントエンコーディングを実行し、文字列内の単一引用符をエスケープすることによって、指定された文字を自動的にエスケープします。 ただし、サービス操作を呼び出すために*Execute*メソッドのいずれかを呼び出すときは、ユーザーが指定した文字列値のエスケープを実行することを忘れないでください。 URI 内の単一引用符は、単一引用符のペアとしてエスケープされます。  
  
## <a name="examples-of-calling-service-operations"></a>サービス操作の呼び出しの例  
 このセクションでは、WCF データ サービス クライアント ライブラリを使用してサービス操作を呼び出す方法の次の例が含まれています。  
  
- [エンティティの&lt;コレクション&gt;を返すために実行 T を呼び出す](calling-service-operations-wcf-data-services.md#ExecuteIQueryable)  
  
- [CreateQuery&lt;T&gt;を使用してエンティティのコレクションを返す](calling-service-operations-wcf-data-services.md#CreateQueryIQueryable)  
  
- [単一&lt;の&gt;エンティティを返すために実行 T を呼び出す](calling-service-operations-wcf-data-services.md#ExecuteSingleEntity)  
  
- [プリミティブ値&lt;の&gt;コレクションを返すために実行 T を呼び出す](calling-service-operations-wcf-data-services.md#ExecutePrimitiveCollection)  
  
- [単一&lt;の&gt;プリミティブ値を返すために実行 T を呼び出す](calling-service-operations-wcf-data-services.md#ExecutePrimitiveValue)  
  
- [データを返さないサービス操作を呼び出す](calling-service-operations-wcf-data-services.md#ExecuteVoid)  
  
- [サービス操作を非同期に呼び出す](calling-service-operations-wcf-data-services.md#ExecuteAsync)  
  
<a name="ExecuteIQueryable"></a>
### <a name="calling-executet-to-return-a-collection-of-entities"></a>エンティティの\<コレクションを返す実行 T>の呼び出し  
 次の例では、文字列パラメーター `city` を受け取り、<xref:System.Linq.IQueryable%601> を返す、GetOrdersByCity という名前のサービス操作を呼び出します。  
  
 [!code-csharp[Astoria Northwind Client#CallServiceOperationIQueryable](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#callserviceoperationiqueryable)]
 [!code-vb[Astoria Northwind Client#CallServiceOperationIQueryable](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#callserviceoperationiqueryable)]  
  
 この例では、サービス操作は、`Order` オブジェクトのコレクションを関連する `Order_Detail` オブジェクトと共に返します。  
  
<a name="CreateQueryIQueryable"></a>
### <a name="using-createqueryt-to-return-a-collection-of-entities"></a>CreateQuery\<T>を使用してエンティティのコレクションを返す  
 次の例では、<xref:System.Data.Services.Client.DataServiceContext.CreateQuery%2A> を使用して、同じ GetOrdersByCity サービス操作を呼び出すために使用される <xref:System.Data.Services.Client.DataServiceQuery%601> を返します。  
  
 [!code-csharp[Astoria Northwind Client#CallServiceOperationCreateQuery](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#callserviceoperationcreatequery)]
 [!code-vb[Astoria Northwind Client#CallServiceOperationCreateQuery](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#callserviceoperationcreatequery)]  
  
 この例では、<xref:System.Data.Services.Client.DataServiceQuery%601.AddQueryOption%2A> メソッドを使用してクエリにパラメーターを追加し、<xref:System.Data.Services.Client.DataServiceQuery%601.Expand%2A> メソッドを使用して関連する Order_Details オブジェクトを結果に含めています。  
  
<a name="ExecuteSingleEntity"></a>
### <a name="calling-executet-to-return-a-single-entity"></a>単一\<のエンティティを返す実行 T>の呼び出し  
 次の例では、単一の Order エンティティのみを返す、GetNewestOrder という名前のサービス操作を呼び出します。  
  
 [!code-csharp[Astoria Northwind Client#CallServiceOperationSingleEntity](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#callserviceoperationsingleentity)]
 [!code-vb[Astoria Northwind Client#CallServiceOperationSingleEntity](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#callserviceoperationsingleentity)]  
  
 この例では、<xref:System.Linq.Enumerable.FirstOrDefault%2A> メソッドを使用して、実行時に単一の Order エンティティのみを要求します。  
  
<a name="ExecutePrimitiveCollection"></a>
### <a name="calling-executet-to-return-a-collection-of-primitive-values"></a>プリミティブ値\<のコレクションを返す実行 T>の呼び出し  
 次の例では、文字列値のコレクションを返すサービス操作を呼び出します。  
  
 [!code-csharp[Astoria Northwind Client#CallServiceOperationEnumString](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#callserviceoperationenumstring)]  
  
<a name="ExecutePrimitiveValue"></a>
### <a name="calling-executet-to-return-a-single-primitive-value"></a>単一\<のプリミティブ値を返す実行 T>を呼び出す  
 次の例では、単一の文字列値を返すサービス操作を呼び出します。  
  
 [!code-csharp[Astoria Northwind Client#CallServiceOperationSingleInt](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#callserviceoperationsingleint)]
 [!code-vb[Astoria Northwind Client#CallServiceOperationSingleInt](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#callserviceoperationsingleint)]  
  
 この例において、<xref:System.Linq.Enumerable.FirstOrDefault%2A> メソッドを使用して、実行時に単一の整数値のみを要求しています。  
  
<a name="ExecuteVoid"></a>
### <a name="calling-a-service-operation-that-returns-no-data"></a>データを返さないサービス操作を呼び出す  
 次の例では、データを返さないサービス操作を呼び出します。  
  
 [!code-csharp[Astoria Northwind Client#CallServiceOperationVoid](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#callserviceoperationvoid)]
 [!code-vb[Astoria Northwind Client#CallServiceOperationVoid](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#callserviceoperationvoid)]  
  
 データが返されないため、実行の値は割り当てられません。 要求が成功したことを示す唯一の印は、<xref:System.Data.Services.Client.DataServiceQueryException> が発生しないことです。  
  
<a name="ExecuteAsync"></a>
### <a name="calling-a-service-operation-asynchronously"></a>サービス操作を非同期に呼び出す  
 次の例では、<xref:System.Data.Services.Client.DataServiceContext.BeginExecute%2A> と <xref:System.Data.Services.Client.DataServiceContext.EndExecute%2A> を呼び出してサービス操作を非同期に呼び出しています。  
  
 [!code-csharp[Astoria Northwind Client#CallServiceOperationAsync](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#callserviceoperationasync)]
 [!code-vb[Astoria Northwind Client#CallServiceOperationAsync](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#callserviceoperationasync)]  
  
 [!code-csharp[Astoria Northwind Client#OnAsyncExecutionComplete](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#onasyncexecutioncomplete)]
 [!code-vb[Astoria Northwind Client#OnAsyncExecutionComplete](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#onasyncexecutioncomplete)]  
  
 データが返されないため、実行によって返される値は割り当てられません。 要求が成功したことを示す唯一の印は、<xref:System.Data.Services.Client.DataServiceQueryException> が発生しないことです。  
  
 次の例では、<xref:System.Data.Services.Client.DataServiceContext.CreateQuery%2A> を使用して同じサービス操作を非同期に呼び出しています。  
  
 [!code-csharp[Astoria Northwind Client#CallServiceOperationQueryAsync](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#callserviceoperationqueryasync)]
 [!code-vb[Astoria Northwind Client#CallServiceOperationQueryAsync](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#callserviceoperationqueryasync)]  
  
 [!code-csharp[Astoria Northwind Client#OnAsyncQueryExecutionComplete](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#onasyncqueryexecutioncomplete)]
 [!code-vb[Astoria Northwind Client#OnAsyncQueryExecutionComplete](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#onasyncqueryexecutioncomplete)]  
  
## <a name="see-also"></a>関連項目

- [WCF Data Services クライアント ライブラリ](wcf-data-services-client-library.md)
