---
title: データ サービスの構成 (WCF Data Services)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, configuring
ms.assetid: 59efd4c8-cc7a-4800-a0a4-d3f8abe6c55c
ms.openlocfilehash: dec42a19f3e265f440ec03164ebc1ece9b6d5ce3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61793498"
---
# <a name="configuring-the-data-service-wcf-data-services"></a>データ サービスの構成 (WCF Data Services)
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]、公開するデータ サービスを作成する[!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)]フィードします。 これらのフィードには、さまざまなデータ ソースからのデータが含まれることがあります。 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] このデータとして公開するデータ プロバイダーを使用して、[!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]フィードします。 これらのプロバイダーには、[!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)] プロバイダー、リフレクション プロバイダー、およびカスタム データ サービス プロバイダー インターフェイスのセットがあります。 プロバイダーの実装は、サービスのデータ モデルを定義します。 詳細については、次を参照してください。[データ サービス プロバイダー](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md)します。  
  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] では、データ サービスは、データ サービスの種類がデータ モデルのエンティティ コンテナーである <xref:System.Data.Services.DataService%601> クラスから継承するクラスです。 このエンティティ コンテナーには、データ モデルのエンティティ セットにアクセスするために使用される <xref:System.Linq.IQueryable%601> を返す 1 つ以上のプロパティがあります。  
  
 データ サービスの動作は、<xref:System.Data.Services.DataServiceConfiguration> クラスのメンバー、および <xref:System.Data.Services.DataServiceBehavior> クラスの <xref:System.Data.Services.DataServiceConfiguration.DataServiceBehavior%2A> プロパティからアクセスされる <xref:System.Data.Services.DataServiceConfiguration> クラスのメンバーによって定義されます。 <xref:System.Data.Services.DataServiceConfiguration> クラスは、Northwind データ サービスの次の実装のように、データ サービスによって実装される `InitializeService` メソッドに提供されます。  
  
[!code-csharp[Astoria Northwind Service#DataServiceConfigComplete](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_service/cs/northwind.svc.cs#dataserviceconfigcomplete)]  
[!code-vb[Astoria Northwind Service#DataServiceConfigComplete](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_service/vb/northwind.svc.vb#dataserviceconfigcomplete)]  
  
## <a name="data-service-configuration-settings"></a>データ サービス構成設定  
 <xref:System.Data.Services.DataServiceConfiguration> クラスでは、以下のデータ サービスの動作を指定できます。  
  
|メンバー|動作|  
|------------|--------------|  
|<xref:System.Data.Services.DataServiceBehavior.AcceptCountRequests%2A>|`$count` パス セグメントおよび `$inlinecount` クエリ オプションを使用してデータ サービスに送信したカウント要求を無効にできます。 詳細については、次を参照してください[OData:。URI 規則](https://go.microsoft.com/fwlink/?LinkId=185564)します。|  
|<xref:System.Data.Services.DataServiceBehavior.AcceptProjectionRequests%2A>|`$select` クエリ オプションを使用してデータ サービスに送信された要求のデータ プロジェクションのサポートを無効にできます。 詳細については、次を参照してください[OData:。URI 規則](https://go.microsoft.com/fwlink/?LinkId=185564)します。|  
|<xref:System.Data.Services.DataServiceConfiguration.EnableTypeAccess%2A>|<xref:System.Data.Services.Providers.IDataServiceMetadataProvider> インターフェイスを使用して定義された動的メタデータ プロバイダーのメタデータでデータ型を公開します。|  
|<xref:System.Data.Services.DataServiceConfiguration.EnableTypeConversion%2A>|ペイロードに含まれている型を、要求で指定された実際のプロパティ型にデータ サービス ランタイムで変換するかどうかを指定できます。|  
|<xref:System.Data.Services.DataServiceBehavior.InvokeInterceptorsOnLinkDelete%2A>|2 つのエンティティ間のリレーションシップ リンクを削除するときに、関連エンティティで登録済みの変更インターセプターを呼び出すかどうかを指定できます。|  
|<xref:System.Data.Services.DataServiceConfiguration.MaxBatchCount%2A>|単一のバッチで許可される変更セットおよびクエリ操作の数を制限できます。 詳細については、次を参照してください[OData:。バッチ](https://go.microsoft.com/fwlink/?LinkId=185602)と[操作をバッチ処理](../../../../docs/framework/data/wcf/batching-operations-wcf-data-services.md)します。|  
|<xref:System.Data.Services.DataServiceConfiguration.MaxChangesetCount%2A>|単一の変更セットに含めることができる変更の数を制限できます。 詳細については、「[方法 :データ サービス結果のページングを有効にする](../../../../docs/framework/data/wcf/how-to-enable-paging-of-data-service-results-wcf-data-services.md)します。|  
|<xref:System.Data.Services.DataServiceConfiguration.MaxExpandCount%2A>|`$expand` クエリ演算子を使用して 1 つの要求に含めることのできる関連エンティティの数を制限することによって応答のサイズを制限できます。 詳細については、次を参照してください[OData:。URI 規則](https://go.microsoft.com/fwlink/?LinkId=185564)と[遅延コンテンツの読み込み](../../../../docs/framework/data/wcf/loading-deferred-content-wcf-data-services.md)します。|  
|<xref:System.Data.Services.DataServiceConfiguration.MaxExpandDepth%2A>|`$expand` クエリ演算子を使用して 1 つの要求に含めることのできる関連エンティティのグラフの深度を制限することによって応答のサイズを制限できます。 詳細については、次を参照してください[OData:。URI 規則](https://go.microsoft.com/fwlink/?LinkId=185564)と[遅延コンテンツの読み込み](../../../../docs/framework/data/wcf/loading-deferred-content-wcf-data-services.md)します。|  
|<xref:System.Data.Services.DataServiceConfiguration.MaxObjectCountOnInsert%2A>|1 つの POST 要求に挿入できるエンティティの数を制限できます。|  
|<xref:System.Data.Services.DataServiceBehavior.MaxProtocolVersion%2A>|データ サービスによって使用される Atom プロトコルのバージョンを定義します。 <xref:System.Data.Services.DataServiceBehavior.MaxProtocolVersion%2A> に <xref:System.Data.Services.Common.DataServiceProtocolVersion> の最大値よりも低い値を設定した場合、[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] の最新の機能はデータ サービスにアクセスするクライアントで使用できなくなります。 詳細については、次を参照してください。[データ サービスのバージョン管理](../../../../docs/framework/data/wcf/data-service-versioning-wcf-data-services.md)します。|  
|<xref:System.Data.Services.DataServiceConfiguration.MaxResultsPerCollection%2A>|データ フィードとして返される各エンティティ セットのエンティティの数を制限することによって応答のサイズを制限できます。|  
|<xref:System.Data.Services.DataServiceConfiguration.RegisterKnownType%2A>|データ サービスで認識される型のリストにデータ型を追加します。|  
|<xref:System.Data.Services.DataServiceConfiguration.SetEntitySetAccessRule%2A>|データ サービスで使用可能なエンティティ セット リソースへのアクセス権を設定します。 アスタリスク (`*`) 値を名前パラメーターに使用すると、残りのすべてのエンティティ セットへのアクセスを同じレベルに設定できます。 エンティティ セットへのアクセスを設定する場合は、クライアント アプリケーションに必要なデータ サービス リソースへの最小アクセス特権を設定することをお勧めします。 詳細については、「 [Securing WCF Data Services](../../../../docs/framework/data/wcf/securing-wcf-data-services.md)」を参照してください。 特定の URI および HTTP アクションに必要な最低限のアクセス権の例については、表を参照して、[最小リソース アクセス要件](../../../../docs/framework/data/wcf/configuring-the-data-service-wcf-data-services.md#accessRequirements)セクション。|  
|<xref:System.Data.Services.DataServiceConfiguration.SetEntitySetPageSize%2A>|エンティティ セット リソースの最大ページ サイズを設定します。 詳細については、「[方法 :データ サービス結果のページングを有効にする](../../../../docs/framework/data/wcf/how-to-enable-paging-of-data-service-results-wcf-data-services.md)します。|  
|<xref:System.Data.Services.DataServiceConfiguration.SetServiceOperationAccessRule%2A>|データ サービスで定義されるサービス操作へのアクセス権を設定します。 詳細については、次を参照してください。[サービス操作](../../../../docs/framework/data/wcf/service-operations-wcf-data-services.md)します。 アスタリスク (`*`) 値を名前パラメーターに使用すると、残りのすべてのサービス操作へのアクセスを同じレベルに設定できます。 サービス操作へのアクセスを設定する場合は、クライアント アプリケーションに必要なデータ サービス リソースへの最小アクセス特権を設定することをお勧めします。 詳細については、「 [Securing WCF Data Services](../../../../docs/framework/data/wcf/securing-wcf-data-services.md)」を参照してください。|  
|<xref:System.Data.Services.DataServiceConfiguration.UseVerboseErrors%2A>|この構成プロパティを使用すると、エラー応答メッセージで多くの情報を返すことによってデータ サービスのトラブルシューティングを容易にすることができます。 このオプションは、運用環境で使用することを目的としたものではありません。 詳細については、次を参照してください。[を開発し、WCF Data Services の展開](../../../../docs/framework/data/wcf/developing-and-deploying-wcf-data-services.md)します。|  
  
<a name="accessRequirements"></a>   
## <a name="minimum-resource-access-requirements"></a>最小限のリソース アクセス要件  
 次の表に、特定の操作を実行するために付与されている必要があるエンティティ セットの最小限の権限を示します。 パスの例を完了するときに作成される Northwind データ サービスに基づいています、[クイック スタート](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md)します。 <xref:System.Data.Services.EntitySetRights> 列挙体および <xref:System.Data.Services.ServiceOperationRights> 列挙体は <xref:System.FlagsAttribute> を使用して定義されているので、論理和演算子を使用して 1 つのエンティティ セットまたは操作に複数のアクセス許可を指定できます。 詳細については、「[方法 :データ サービスへのアクセスを有効にする](../../../../docs/framework/data/wcf/how-to-enable-access-to-the-data-service-wcf-data-services.md)します。  
  
|パス/アクション|`GET`|`DELETE`|`MERGE`|`POST`|`PUT`|  
|------------------|-----------|--------------|-------------|------------|-----------|  
|`/Customers`|<xref:System.Data.Services.EntitySetRights.ReadMultiple>|サポートなし|サポートなし|<xref:System.Data.Services.EntitySetRights.WriteAppend>|サポートなし|  
|`/Customers('ALFKI')`|<xref:System.Data.Services.EntitySetRights.ReadSingle>|<xref:System.Data.Services.EntitySetRights.ReadSingle> および <xref:System.Data.Services.EntitySetRights.WriteDelete>|<xref:System.Data.Services.EntitySetRights.ReadSingle> および <xref:System.Data.Services.EntitySetRights.WriteMerge>|N/A|<xref:System.Data.Services.EntitySetRights.ReadSingle> および <xref:System.Data.Services.EntitySetRights.WriteReplace>|  
|`/Customers('ALFKI')/Orders`|`Customers`: <xref:System.Data.Services.EntitySetRights.ReadSingle><br /><br /> および<br /><br /> `Orders`: <xref:System.Data.Services.EntitySetRights.ReadMultiple>|サポートなし|サポートなし|`Customers`: <xref:System.Data.Services.EntitySetRights.ReadSingle> および <xref:System.Data.Services.EntitySetRights.WriteMerge> または <xref:System.Data.Services.EntitySetRights.WriteReplace><br /><br /> および<br /><br /> `Orders` `:` そして <xref:System.Data.Services.EntitySetRights.WriteAppend>|サポートなし|  
|`/Customers('ALFKI')/Orders(10643)`|`Customers`: <xref:System.Data.Services.EntitySetRights.ReadSingle><br /><br /> および<br /><br /> `Orders`: <xref:System.Data.Services.EntitySetRights.ReadSingle>|`Customers`: <xref:System.Data.Services.EntitySetRights.ReadSingle><br /><br /> および<br /><br /> `Orders`: <xref:System.Data.Services.EntitySetRights.ReadSingle> および <xref:System.Data.Services.EntitySetRights.WriteDelete>|`Customers`: <xref:System.Data.Services.EntitySetRights.ReadSingle><br /><br /> および<br /><br /> `Orders`: <xref:System.Data.Services.EntitySetRights.ReadSingle> および <xref:System.Data.Services.EntitySetRights.WriteMerge>|サポートなし|`Customers`: <xref:System.Data.Services.EntitySetRights.ReadSingle><br /><br /> および<br /><br /> `Orders`: <xref:System.Data.Services.EntitySetRights.ReadSingle> および <xref:System.Data.Services.EntitySetRights.WriteReplace>|  
|`/Orders(10643)/Customer`|`Customers`: <xref:System.Data.Services.EntitySetRights.ReadSingle><br /><br /> および<br /><br /> `Orders`: <xref:System.Data.Services.EntitySetRights.ReadSingle>|`Customers`: <xref:System.Data.Services.EntitySetRights.ReadSingle> および <xref:System.Data.Services.EntitySetRights.WriteDelete><br /><br /> および<br /><br /> `Orders`: <xref:System.Data.Services.EntitySetRights.ReadSingle>|`Customers`: <xref:System.Data.Services.EntitySetRights.ReadSingle> および <xref:System.Data.Services.EntitySetRights.WriteMerge><br /><br /> および<br /><br /> `Orders`: <xref:System.Data.Services.EntitySetRights.ReadSingle>|`Customers`: <xref:System.Data.Services.EntitySetRights.WriteAppend><br /><br /> および<br /><br /> `Orders`: <xref:System.Data.Services.EntitySetRights.WriteAppend> および <xref:System.Data.Services.EntitySetRights.ReadSingle>|サポートなし|  
|`/Customers('ALFKI')/$links/Orders`|`Customers`: <xref:System.Data.Services.EntitySetRights.ReadSingle><br /><br /> および<br /><br /> `Orders`: <xref:System.Data.Services.EntitySetRights.ReadMultiple>|サポートなし|サポートなし|`Customers`: <xref:System.Data.Services.EntitySetRights.ReadSingle> および <xref:System.Data.Services.EntitySetRights.WriteMerge> または <xref:System.Data.Services.EntitySetRights.WriteReplace><br /><br /> および<br /><br /> `Orders`: <xref:System.Data.Services.EntitySetRights.ReadSingle>|サポートなし|  
|`/Customers('ALFKI')/$links/Orders(10643)`|`Customers`: <xref:System.Data.Services.EntitySetRights.ReadSingle><br /><br /> および<br /><br /> `Orders`: <xref:System.Data.Services.EntitySetRights.ReadSingle>|`Customers`: <xref:System.Data.Services.EntitySetRights.ReadSingle> および <xref:System.Data.Services.EntitySetRights.WriteMerge> または <xref:System.Data.Services.EntitySetRights.WriteReplace><br /><br /> および<br /><br /> `Orders`: <xref:System.Data.Services.EntitySetRights.ReadSingle>|サポートなし|サポートなし|サポートなし|  
|`/Orders(10643)/$links/Customer`|`Customers`: <xref:System.Data.Services.EntitySetRights.ReadSingle><br /><br /> および<br /><br /> `Orders`: <xref:System.Data.Services.EntitySetRights.ReadSingle>|`Orders`: <xref:System.Data.Services.EntitySetRights.ReadSingle> および <xref:System.Data.Services.EntitySetRights.WriteMerge> または <xref:System.Data.Services.EntitySetRights.WriteReplace>|`Customers`: <xref:System.Data.Services.EntitySetRights.ReadSingle><br /><br /> および<br /><br /> `Orders`: <xref:System.Data.Services.EntitySetRights.ReadSingle> および <xref:System.Data.Services.EntitySetRights.WriteMerge>|サポートなし|`Customers`: <xref:System.Data.Services.EntitySetRights.ReadSingle>;<br /><br /> および<br /><br /> `Orders`: <xref:System.Data.Services.EntitySetRights.ReadSingle> および <xref:System.Data.Services.EntitySetRights.WriteReplace>|  
|`/Customers/$count`|<xref:System.Data.Services.EntitySetRights.ReadMultiple>|サポートなし|サポートなし|サポートなし|サポートなし|  
|`/Customers('ALFKI')/ContactName`|<xref:System.Data.Services.EntitySetRights.ReadSingle>|サポートなし|<xref:System.Data.Services.EntitySetRights.WriteMerge>|サポートなし|<xref:System.Data.Services.EntitySetRights.WriteReplace>|  
|`/Customers('ALFKI')/Address/StreetAddress/$value` <sup>1</sup>|<xref:System.Data.Services.EntitySetRights.ReadSingle>|<xref:System.Data.Services.EntitySetRights.WriteDelete>|サポートなし|サポートなし|サポートなし|  
|`/Customers('ALFKI')/ContactName/$value`|<xref:System.Data.Services.EntitySetRights.ReadSingle>|<xref:System.Data.Services.EntitySetRights.ReadSingle> および <xref:System.Data.Services.EntitySetRights.WriteDelete>|<xref:System.Data.Services.EntitySetRights.WriteMerge>|サポートなし|<xref:System.Data.Services.EntitySetRights.WriteReplace>|  
|`/Customers('ALFKI')/$value` <sup>2</sup>|<xref:System.Data.Services.EntitySetRights.ReadSingle>|サポートなし|サポートなし|サポートなし|<xref:System.Data.Services.EntitySetRights.WriteReplace>|  
|`/Customers?$select=Orders/*&$expand=Orders`|`Customers`: <xref:System.Data.Services.EntitySetRights.ReadSingle><br /><br /> および<br /><br /> `Orders`: <xref:System.Data.Services.EntitySetRights.ReadMultiple>|サポートなし|サポートなし|`Customers`: <xref:System.Data.Services.EntitySetRights.WriteAppend>|サポートなし|  
|`/Customers('ALFKI')?$select=Orders/*&$expand=Orders`|`Customers`: <xref:System.Data.Services.EntitySetRights.ReadSingle><br /><br /> および<br /><br /> `Orders`: <xref:System.Data.Services.EntitySetRights.ReadMultiple>|サポートなし|サポートなし|サポートなし|サポートなし|  
  
 <sup>1</sup>この例で`Address`の複合型プロパティを表す、`Customers`をという名前のプロパティを持つエンティティ`StreetAddress`します。 Northwind データ サービスによって使用されるモデルでは、この複合型は明示的に定義されていません。 [!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)] プロバイダーを使用してデータ モデルを定義している場合、[!INCLUDE[adonet_edm](../../../../includes/adonet-edm-md.md)] ツールを使用して、このような複合型を定義できます。 詳細については、「[方法 :作成し、複合型を変更](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd456820(v=vs.100))します。  
  
 <sup>2</sup>バイナリ ラージ オブジェクト (BLOB) を返すプロパティが、ここではメディア リンク エントリであるエンティティに属するメディア リソースとして定義されている場合、この URI はサポートされて`Customers`します。 詳細については、次を参照してください。[ストリーミング プロバイダー](../../../../docs/framework/data/wcf/streaming-provider-wcf-data-services.md)します。  
  
<a name="versioning"></a>   
## <a name="versioning-requirements"></a>バージョン管理の要件  
 次のデータ サービス構成の動作には、[!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] プロトコルのバージョン 2 またはそれ以降のバージョンが必要です。  
  
- カウント要求のサポート。  
  
- 射影の $select クエリ オプションのサポート。  
  
 詳細については、次を参照してください。[データ サービスのバージョン管理](../../../../docs/framework/data/wcf/data-service-versioning-wcf-data-services.md)します。  
  
## <a name="see-also"></a>関連項目

- [WCF Data Services の定義](../../../../docs/framework/data/wcf/defining-wcf-data-services.md)
- [データ サービスのホスティング](../../../../docs/framework/data/wcf/hosting-the-data-service-wcf-data-services.md)
