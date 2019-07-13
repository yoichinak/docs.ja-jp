---
title: データ サービス コンテキストの管理 (WCF Data Services)
ms.date: 03/30/2017
ms.assetid: 15b19d09-7de7-4638-9556-6ef396cc45ec
ms.openlocfilehash: 329e3ee222b8375d82e6d1234dd89b4fa2c6c7c0
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/14/2019
ms.locfileid: "65582662"
---
# <a name="managing-the-data-service-context-wcf-data-services"></a>データ サービス コンテキストの管理 (WCF Data Services)
<xref:System.Data.Services.Client.DataServiceContext> クラスは、特定のデータ サービスに対してサポートされている操作をカプセル化します。 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] サービスはステートレスですが、コンテキストはステートレスではありません。 そのため、使用することができます、<xref:System.Data.Services.Client.DataServiceContext>変更管理などの機能をサポートするために、データ サービスとの対話操作間におけるクライアントの状態を維持するクラス。 このクラスは、ID の管理と変更の追跡も行います。  
  
## <a name="merge-options-and-identity-resolution"></a>マージ オプションおよび ID 解決  
 <xref:System.Data.Services.Client.DataServiceQuery%601> が実行されると、応答フィードのエンティティはオブジェクトに具体化されます。 詳細については、次を参照してください。[オブジェクトの具体化](../../../../docs/framework/data/wcf/object-materialization-wcf-data-services.md)します。 応答メッセージのエントリがオブジェクトに具体化される方法は、ID 解決に基づいて実行され、クエリが実行された際のマージ オプションによって決まります。 複数のクエリまたは読み込み要求が単一の <xref:System.Data.Services.Client.DataServiceContext> のスコープで実行される場合、[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] クライアントは特定のキー値を持つオブジェクトの単一のインスタンスのみを追跡します。 このキーは、ID 解決の実行に使用され、エンティティを一意に識別します。  
  
 既定では、クライアントは <xref:System.Data.Services.Client.DataServiceContext> によってまだ追跡されていないエンティティのオブジェクトに応答フィードのエントリを具体化するだけです。 これは、既にキャッシュ内にあるオブジェクトに対する変更は上書きされないことを意味します。 この動作は、クエリおよび読み込み操作に <xref:System.Data.Services.Client.MergeOption> 値を指定することによって制御されます。 このオプションを指定するには、<xref:System.Data.Services.Client.DataServiceContext.MergeOption%2A> の <xref:System.Data.Services.Client.DataServiceContext> プロパティを設定します。 既定のマージ オプションの値は <xref:System.Data.Services.Client.MergeOption.AppendOnly> です。 この既定値を設定した場合、まだ追跡されていないエンティティのオブジェクトのみが具体化されます。これは、既存のオブジェクトが上書きされないことを意味します。 クライアントのオブジェクトに対する変更がデータ サービスからの更新によって上書きされないようにするもう 1 つの方法は、<xref:System.Data.Services.Client.MergeOption.PreserveChanges> を指定する方法です。 <xref:System.Data.Services.Client.MergeOption.OverwriteChanges> を指定した場合、クライアントのオブジェクトの値は、既に変更が加えられていても、応答フィードのエントリの最新の値によって置換されます。 <xref:System.Data.Services.Client.MergeOption.NoTracking> マージ オプションを使用する場合、<xref:System.Data.Services.Client.DataServiceContext> はクライアント オブジェクトに加えられた変更をデータ サービスに送信できません。 このオプションを使用すると、変更は常にデータ サービスの値によって上書きされます。  
  
## <a name="managing-concurrency"></a>コンカレンシーの管理  
 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] 更新の競合を検出するために、データ サービスにより、オプティミスティック同時実行制御をサポートしています。 データ サービス プロバイダーは、データ サービスでコンカレンシー トークンを使用してエンティティへの変更をチェックするように構成できます。 このトークンには、リソースが変更されているかどうかを決定するためにデータ サービスによって検証されるエンティティ型の 1 つ以上のプロパティが含まれています。 要求およびデータ サービスからの応答の eTag ヘッダーに含まれている、同時実行制御トークンがによって管理されている、[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]クライアント。 詳細については、次を参照してください。[データ サービスの更新](../../../../docs/framework/data/wcf/updating-the-data-service-wcf-data-services.md)します。  
  
 <xref:System.Data.Services.Client.DataServiceContext> は、<xref:System.Data.Services.Client.DataServiceContext.AddObject%2A>、<xref:System.Data.Services.Client.DataServiceContext.UpdateObject%2A>、および <xref:System.Data.Services.Client.DataServiceContext.DeleteObject%2A> を使用して手動で報告しているか、または <xref:System.Data.Services.Client.DataServiceCollection%601> によって報告されているオブジェクトへの変更を追跡します。 <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A> メソッドを呼び出すと、クライアントはデータ サービスに変更を送り返します。 <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A> は、クライアントでのデータ変更がデータ サービスでの変更と競合する場合に失敗する可能性があります。 このような状況が発生した場合、エンティティ リソースに対してクエリを再度実行し、更新データを受信する必要があります。 データ サービスの変更を上書きするには、<xref:System.Data.Services.Client.MergeOption.PreserveChanges> マージ オプションを使用してクエリを実行します。 <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A> を再度呼び出すと、データ サービスのリソースに対してその他の変更がまだ行われていない場合に限り、クライアントに保存されている変更がデータ サービスに永続化されます。  
  
## <a name="saving-changes"></a>変更の保存  
 変更は、<xref:System.Data.Services.Client.DataServiceContext> インスタンスで追跡されますが、サーバーには直ちに送信されません。 指定されたアクティビティに対して必要な変更が完了した後、<xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A> を呼び出して、すべての変更をデータ サービスに送信します。 <xref:System.Data.Services.Client.DataServiceResponse> 操作が完了した後、<xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A> オブジェクトが返されます。 <xref:System.Data.Services.Client.DataServiceResponse> オブジェクトには、<xref:System.Data.Services.Client.OperationResponse> オブジェクトのシーケンスが含まれます。さらに、これらの各オブジェクトには、永続化または試行された変更を表す、<xref:System.Data.Services.Client.EntityDescriptor> インスタンスまたは <xref:System.Data.Services.Client.LinkDescriptor> インスタンスのシーケンスが含まれます。 データ サービス内でエンティティが作成または変更されると、前の例で生成された <xref:System.Data.Services.Client.EntityDescriptor> 値のようなサーバー生成のプロパティ値も含めて、更新されたエンティティへの参照が `ProductID` に含められます。 クライアント ライブラリは、これらの新しい値で .NET Framework オブジェクトを自動的に更新します。  
  
 挿入操作と更新操作を適切に実行するため、その操作に関連付けられている <xref:System.Data.Services.Client.EntityDescriptor> オブジェクトまたは <xref:System.Data.Services.Client.LinkDescriptor> オブジェクトの状態プロパティが <xref:System.Data.Services.Client.EntityStates.Unchanged> に設定され、新しい値は <xref:System.Data.Services.Client.MergeOption.OverwriteChanges> を使用してマージされます。 データ サービス内で挿入、更新、または削除操作が失敗した場合、エンティティ状態は、<xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A> が呼び出される前と同じままになり、<xref:System.Data.Services.Client.OperationResponse.Error%2A> の <xref:System.Data.Services.Client.OperationResponse> プロパティは、エラーに関する情報を含む <xref:System.Data.Services.Client.DataServiceRequestException> に設定されます。 詳細については、次を参照してください。[データ サービスの更新](../../../../docs/framework/data/wcf/updating-the-data-service-wcf-data-services.md)します。  
  
### <a name="setting-the-http-method-for-updates"></a>更新用の HTTP メソッドの設定  
 既定では、更新は、.NET Framework クライアント ライブラリから既存のエンティティに MERGE 要求として送信されます。 MERGE 要求では、エンティティの選択されたプロパティが更新されますが、クライアントは、常に、変更されていないプロパティを含むすべてのプロパティを MERGE 要求に含めます。 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] プロトコルは、エンティティを更新する PUT 要求の送信もサポートしています。 PUT 要求では、既存のエンティティが、クライアントからのプロパティ値を含むエンティティの新しいインスタンスによって本質的に置き換えられます。 PUT 要求を使用するには、<xref:System.Data.Services.Client.SaveChangesOptions.ReplaceOnUpdate> を呼び出すときに <xref:System.Data.Services.Client.SaveChangesOptions> フラグを <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A> 列挙体に設定します。  
  
> [!NOTE]
>  クライアントがエンティティの一部のプロパティを認識していない場合、PUT 要求は MERGE 要求とは異なる動作になります。 この状況は、クライアントでエンティティ型を新しい型に射影する場合に発生することがあります。 また、新しいプロパティがサービス データ モデルのエンティティに追加されており、このようなクライアントのマッピング エラーを無視するように <xref:System.Data.Services.Client.DataServiceContext.IgnoreMissingProperties%2A> の <xref:System.Data.Services.Client.DataServiceContext> プロパティが `true` に設定されている場合にも発生することがあります。 この場合、PUT 要求では、クライアントが認識していないすべてのプロパティが既定値にリセットされます。  
  
### <a name="post-tunneling"></a>POST トンネリング  
 既定では、クライアント ライブラリは、作成、読み取り、更新、および削除要求を、POST、GET、PUT/MERGE/PATCH、および DELETE の対応する HTTP メソッドを使用して、[!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] サービスに送信します。 これは、Representational State Transfer (REST) の基本原則に沿った動作です。 ただし、すべての Web サーバー実装で HTTP メソッドの完全なセットがサポートされるとは限りません。 場合によっては、サポートされているメソッドが GET と POST のみに制限されていることもあります。 このような状況は、ファイアウォールのような仲介物が特定のメソッドの要求をブロックしている場合に発生します。 GET メソッドと POST メソッドは一般的にサポートされているメソッドであるため、[!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] では、サポートされていない HTTP メソッドを POST 要求を使用して実行する方法を規定しています。 呼ばれる*メソッド トンネリング*または*POST トンネリング*、これにより、クライアント ユーザー設定で指定された実際のメソッドと POST 要求を送信する`X-HTTP-Method`ヘッダー。 要求の POST トンネリングを有効にするには、<xref:System.Data.Services.Client.DataServiceContext.UsePostTunneling%2A> インスタンスの <xref:System.Data.Services.Client.DataServiceContext> プロパティを `true` に設定します。  
  
## <a name="see-also"></a>関連項目

- [WCF Data Services クライアント ライブラリ](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)
- [データ サービスの更新](../../../../docs/framework/data/wcf/updating-the-data-service-wcf-data-services.md)
- [非同期操作](../../../../docs/framework/data/wcf/asynchronous-operations-wcf-data-services.md)
- [バッチ処理](../../../../docs/framework/data/wcf/batching-operations-wcf-data-services.md)
