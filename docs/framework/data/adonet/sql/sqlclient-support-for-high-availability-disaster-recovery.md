---
title: 高可用性障害復旧のための SqlClient サポート
ms.date: 03/30/2017
ms.assetid: 61e0b396-09d7-4e13-9711-7dcbcbd103a0
ms.openlocfilehash: 104fdd78ce3f4b9c18f09fc41fddebe46815d217
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69938474"
---
# <a name="sqlclient-support-for-high-availability-disaster-recovery"></a>高可用性障害復旧のための SqlClient サポート
このトピックでは、高可用性、ディザスターリカバリー、AlwaysOn 可用性グループのための SqlClient サポート (.NET Framework 4.5 で追加) について説明します。  AlwaysOn 可用性グループ機能が SQL Server 2012 に追加されました。 AlwaysOn 可用性グループの詳細については、「SQL Server オンラインブック」を参照してください。  
  
 接続プロパティで、(高可用性、ディザスターリカバリー) 可用性グループ (AG)、または SQL Server 2012 フェールオーバークラスターインスタンスの可用性グループリスナーを指定できるようになりました。 フェールオーバーが発生した AlwaysOn データベースに SqlClient アプリケーションが接続される場合、元の接続が途切れるため、アプリケーションがフェールオーバーの後に処理を続行するには、新しい接続を開く必要があります。  
  
 可用性グループリスナーまたは SQL Server 2012 フェールオーバークラスターインスタンスに接続しておらず、複数の IP アドレスがホスト名に関連付けられている場合、SqlClient は DNS エントリに関連付けられているすべての IP アドレスを順番に反復処理します。 これは、DNS サーバーによって返された最初の IP アドレスがネットワーク インターフェイス カード (NIC) にバインドされていない場合、時間がかかります。 可用性グループリスナーまたは SQL Server 2012 フェールオーバークラスターインスタンスに接続しようとすると、SqlClient はすべての IP アドレスへの接続を並行して確立しようとします。接続試行が成功すると、ドライバーは保留中の接続をすべて破棄しますログオン.  
  
> [!NOTE]
> 接続タイムアウトの増加および接続の再試行ロジックの実装により、アプリケーションが可用性グループに接続する可能性は向上します。 また、接続がフェールオーバーによって失敗する可能性があるので、接続の再試行ロジックの実装は、失敗した接続が再接続するまで試行されるようにする必要があります。  
  
 .NET Framework 4.5 の SqlClient に次の接続プロパティが追加されました:  
  
- `ApplicationIntent`  
  
- `MultiSubnetFailover`  
  
 プログラムによって、これらの接続文字列キーワードを次のとおりに変更できます。  
  
1. <xref:System.Data.SqlClient.SqlConnectionStringBuilder.ApplicationIntent%2A>  
  
2. <xref:System.Data.SqlClient.SqlConnectionStringBuilder.MultiSubnetFailover%2A>  

> [!NOTE]
> .NET Framework `MultiSubnetFailover` 4.6.1 `true`以降のバージョンでは、をに設定する必要はありません。
  
## <a name="connecting-with-multisubnetfailover"></a>MultiSubnetFailover を使用した接続  
 SQL Server 2012 `MultiSubnetFailover=True`可用性グループリスナーまたは SQL Server 2012 フェールオーバークラスターインスタンスに接続する場合は、必ずを指定します。 `MultiSubnetFailover`SQL Server 2012 のすべての可用性グループとフェールオーバークラスターインスタンスの高速フェールオーバーを有効にします。これにより、単一およびマルチサブネットの AlwaysOn トポロジのフェールオーバー時間が大幅に短縮されます。 複数のサブネットのフェールオーバーでは、クライアントは並列接続を試みます。 サブネットのフェールオーバー中に、積極的に TCP 接続を再試行します。  
  
 `MultiSubnetFailover`接続プロパティは、アプリケーションが可用性グループまたは2012フェールオーバークラスターインスタンス SQL Server に配置されていて、SqlClient がプライマリ SQL Server インスタンスのデータベースへの接続を試行することを示します。すべての IP アドレスに接続します。 `MultiSubnetFailover=True` を接続に指定すると、クライアントは、オペレーティング システムの既定の TCP 再転送間隔よりも高速に接続試行を再試行します。 これは、AlwaysOn 可用性グループまたは AlwaysOn フェールオーバー クラスター インスタンスのフェールオーバー後のより高速な再接続を可能にし、単一および複数のサブネットの可用性グループおよびフェールオーバー クラスター インスタンスの両方に適用可能です。  
  
 SqlClient の接続文字列キーワードの詳細については、<xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A> を参照してください。  
  
 可用性`MultiSubnetFailover=True`グループリスナーまたは SQL Server 2012 フェールオーバークラスターインスタンス以外に接続するときにを指定すると、パフォーマンスに悪影響が生じる可能性があり、サポートされていません。  
  
 次のガイドラインを使用して、可用性グループまたは SQL Server 2012 フェールオーバークラスターインスタンスのサーバーに接続します。  
  
- 単一のサブネットまたは複数のサブネットへの接続時には、`MultiSubnetFailover` 接続プロパティを使用します。これにより、両方の場合でパフォーマンスが向上します。  
  
- 可用性グループに接続するには、使用する接続文字列でサーバーとして可用性グループの可用性グループ リスナーを指定します。  
  
- 64を超える IP アドレスで構成された SQL Server インスタンスに接続すると、接続エラーが発生します。  
  
- `MultiSubnetFailover`接続プロパティを使用するアプリケーションの動作は、認証の種類によっては影響を受けません。認証、Kerberos 認証、または Windows 認証を SQL Server します。  
  
- フェールオーバー時に対応し、アプリケーションの接続の再試行を減らすには、`Connect Timeout` の値を増やします。  
  
- 分散トランザクションはサポートされていません。  
  
 読み取り専用のルーティングが有効でない場合は、セカンダリ レプリカの場所への接続は、次の場合に失敗します。  
  
1. セカンダリ レプリカの場所が接続を受け入れないように構成されている場合。  
  
2. アプリケーションが `ApplicationIntent=ReadWrite` (後で説明) を使用している場合、セカンダリ レプリカの場所は読み取り専用アクセスとして構成されます。  
  
 <xref:System.Data.SqlClient.SqlDependency> は、読み取り専用のセカンダリ レプリカではサポートされていません。  
  
 プライマリ レプリカが読み取り専用のワークロードを拒否するように設定され、接続文字列が  `ApplicationIntent=ReadOnly` を含んでいる場合、接続は失敗します。  
  
## <a name="upgrading-to-use-multi-subnet-clusters-from-database-mirroring"></a>データベース ミラーリングから複数のサブネット クラスターを使用するためのアップグレード  
 接続エラー (<xref:System.ArgumentException>) は、`MultiSubnetFailover` および `Failover Partner` 接続のキーワードが接続文字列内に存在する場合や、`MultiSubnetFailover=True` および TCP 以外のプロトコルが使用された場合に発生します。 また、が<xref:System.Data.SqlClient.SqlException>使用され、SQL Server `MultiSubnetFailover`がデータベースミラーリングペアの一部であることを示すフェールオーバーパートナー応答を返す場合にも、エラー () が発生します。  
  
 現在データベース ミラーリングを使用している SqlClient アプリケーションを複数のサブネットのシナリオへとアップグレードする場合、`Failover Partner` 接続プロパティを削除し、`MultiSubnetFailover` に設定した `True` で置き換え、接続文字列のサーバー名を可用性グループ リスナーと置き換える必要があります。 接続文字列が `Failover Partner` および `MultiSubnetFailover=True` を使用していると、ドライバーがエラーを生成します。 ただし、接続文字列が `Failover Partner` および `MultiSubnetFailover=False` (または  `ApplicationIntent=ReadWrite`) を使用している場合、アプリケーションはデータベース ミラーリングを使用します。  
  
 データベース ミラーリングが AG のプライマリ データベースで使用される場合、および  `MultiSubnetFailover=True` が可用性グループ リスナーではなくプライマリ データベースに接続する接続文字列で使用される場合、ドライバーはエラーを返します。  
  
## <a name="specifying-application-intent"></a>アプリケーションの目的の指定  
 `ApplicationIntent=ReadOnly` の場合、クライアントは AlwaysOn が有効になったデータベースに接続する場合に、読み取られたワークロードを要求します。 サーバーは、接続時および USE データベース ステートメントの間、その目的を強制しますが、AlwaysOn が有効になったデータベースに対してのみ、これを行います。  
  
 `ApplicationIntent` キーワードは従来の読み取り専用のデータベースでは機能しません。  
  
 データベースは、対象となる AlwaysOn データベースのワークロードの読み取りを許可または拒否できます。 (これは、 `ALLOW_CONNECTIONS` `PRIMARY_ROLE`および`SECONDARY_ROLE`transact-sql ステートメントの句を使用して行います)。  
  
 `ApplicationIntent` キーワードは、読み取り専用のルーティングを有効にするために使用されます。  
  
## <a name="read-only-routing"></a>読み取り専用ルーティング  
 読み取り専用のルーティングはデータベースの読み取り専用のレプリカの可用性を確保できる機能です。 読み取り専用のルーティングを有効にするには次のことが必要です。  
  
1. AlwaysOn 可用性グループの可用性グループ リスナーに接続する必要があります。  
  
2. `ApplicationIntent` 接続文字列キーワードを `ReadOnly` に設定する必要があります。  
  
3. 可用性グループは、データベース管理者によって、読み取り専用のルーティングを有効にするように構成される必要があります。  
  
 読み取り専用のルーティングを使用する複数の接続のすべてが、同じ読み取り専用のレプリカに接続しないようにすることができます。 データベースの同期変更またはサーバーのルーティング構成の変更は、異なる読み取り専用のレプリカに対するクライアントの接続につながることがあります。 すべての読み取り専用の要求が、確実に同じ読み取り専用のレプリカに接続するようにするには、`Data Source` 接続文字列キーワードに可用性グループ リスナーを渡さないでください。 代わりに、読み取り専用のインスタンスの名前を指定します。  
  
 読み取り専用のルーティングでは、最初にプライマリに接続し、最適な可用性の読み取り可能なセカンダリを検索するため、プライマリに接続するよりも時間がかかる場合があります。 そのため、ログインのタイムアウトを増やす必要があります。  
  
## <a name="see-also"></a>関連項目

- [SQL Server の機能と ADO.NET](../../../../../docs/framework/data/adonet/sql/sql-server-features-and-adonet.md)
- [ADO.NET のマネージド プロバイダーと DataSet デベロッパー センター](https://go.microsoft.com/fwlink/?LinkId=217917)
