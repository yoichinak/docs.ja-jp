---
title: 高可用性障害復旧のための SqlClient サポート
ms.date: 03/30/2017
ms.assetid: 61e0b396-09d7-4e13-9711-7dcbcbd103a0
ms.openlocfilehash: 40054378319b81113dcb8f40cb82a8b1d02fc594
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/09/2019
ms.locfileid: "59307611"
---
# <a name="sqlclient-support-for-high-availability-disaster-recovery"></a>高可用性障害復旧のための SqlClient サポート
このトピックでは、高可用性、ディザスター リカバリーのための SqlClient サポート ([!INCLUDE[net_v45](../../../../../includes/net-v45-md.md)] に追加) である AlwaysOn 可用性グループについて説明します。  AlwaysOn 可用性グループ機能は、SQL Server 2012 に追加されました。 AlwaysOn 可用性グループの詳細については、SQL Server オンライン ブックを参照してください。  
  
 可用性グループ リスナーを指定できるようになりました (高可用性と災害復旧) 可用性グループ (AG) または接続プロパティで SQL Server 2012 フェールオーバー クラスター インスタンス。 フェールオーバーが発生した AlwaysOn データベースに SqlClient アプリケーションが接続される場合、元の接続が途切れるため、アプリケーションがフェールオーバーの後に処理を続行するには、新しい接続を開く必要があります。  
  
 可用性グループ リスナーまたは SQL Server 2012 フェールオーバー クラスター インスタンスに接続していないと、複数の IP アドレスが、ホスト名に関連付けられている場合は、SqlClient は、反復順番に DNS エントリに関連付けられているすべての IP アドレス。 これは、DNS サーバーによって返された最初の IP アドレスがネットワーク インターフェイス カード (NIC) にバインドされていない場合、時間がかかります。 SqlClient が並列ですべての IP アドレスへの接続を確立しようとしたに可用性グループ リスナーまたは SQL Server 2012 フェールオーバー クラスター インスタンスに接続するときに、接続試行が成功すると、ドライバーは、保留中の接続が破棄されます。しようとします。  
  
> [!NOTE]
>  接続タイムアウトの増加および接続の再試行ロジックの実装により、アプリケーションが可用性グループに接続する可能性は向上します。 また、接続がフェールオーバーによって失敗する可能性があるので、接続の再試行ロジックの実装は、失敗した接続が再接続するまで試行されるようにする必要があります。  
  
 次の接続プロパティが、[!INCLUDE[net_v45](../../../../../includes/net-v45-md.md)] の SqlClient に追加されました。  
  
-   `ApplicationIntent`  
  
-   `MultiSubnetFailover`  
  
 プログラムによって、これらの接続文字列キーワードを次のとおりに変更できます。  
  
1. <xref:System.Data.SqlClient.SqlConnectionStringBuilder.ApplicationIntent%2A>  
  
2. <xref:System.Data.SqlClient.SqlConnectionStringBuilder.MultiSubnetFailover%2A>  

> [!NOTE]
>  設定`MultiSubnetFailover`に`true`が必要でない[!INCLUDE[net_v461](../../../../../includes/net-v461-md.md)]以降のバージョン。
  
## <a name="connecting-with-multisubnetfailover"></a>MultiSubnetFailover を使用した接続  
 常に指定`MultiSubnetFailover=True`SQL Server 2012 可用性グループ リスナーまたは SQL Server 2012 フェールオーバー クラスター インスタンスに接続するとき。 `MultiSubnetFailover` 単一サブネットおよびマルチ サブネットの AlwaysOn トポロジにおけるフェールオーバー時間を大幅に短縮され、SQL Server 2012 フェールオーバー クラスター インスタンスからすべての可用性グループをやは、高速フェールオーバーを有効にします。 複数のサブネットのフェールオーバーでは、クライアントは並列接続を試みます。 サブネットのフェールオーバー中に、積極的に TCP 接続を再試行します。  
  
 `MultiSubnetFailover`接続プロパティは、可用性グループまたは SQL Server 2012 フェールオーバー クラスター インスタンスで、アプリケーションが配置されていることと、SqlClient はしようとして、プライマリ SQL Server インスタンス上のデータベースに接続しようとしていることを示します。すべての IP アドレスに接続します。 `MultiSubnetFailover=True` を接続に指定すると、クライアントは、オペレーティング システムの既定の TCP 再転送間隔よりも高速に接続試行を再試行します。 これは、AlwaysOn 可用性グループまたは AlwaysOn フェールオーバー クラスター インスタンスのフェールオーバー後のより高速な再接続を可能にし、単一および複数のサブネットの可用性グループおよびフェールオーバー クラスター インスタンスの両方に適用可能です。  
  
 SqlClient の接続文字列キーワードの詳細については、<xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A> を参照してください。  
  
 指定する`MultiSubnetFailover=True`ときに可用性グループ リスナーまたは SQL Server 2012 フェールオーバー クラスター インスタンス以外の何かに接続と可能性がある、負の値のパフォーマンスに影響はサポートされていません。  
  
 可用性グループ内のサーバーまたは SQL Server 2012 フェールオーバー クラスター インスタンスに接続するには、次のガイドラインを使用します。  
  
-   単一のサブネットまたは複数のサブネットへの接続時には、`MultiSubnetFailover` 接続プロパティを使用します。これにより、両方の場合でパフォーマンスが向上します。  
  
-   可用性グループに接続するには、使用する接続文字列でサーバーとして可用性グループの可用性グループ リスナーを指定します。  
  
-   SQL Server に接続する 64 を超える IP アドレスで構成されているインスタンスの接続エラーが発生します。  
  
-   使用するアプリケーションの動作、`MultiSubnetFailover`接続プロパティが認証の種類に基づく影響を受けません。SQL Server 認証、Kerberos 認証、または Windows 認証。  
  
-   フェールオーバー時に対応し、アプリケーションの接続の再試行を減らすには、`Connect Timeout` の値を増やします。  
  
-   分散トランザクションはサポートされていません。  
  
 読み取り専用のルーティングが有効でない場合は、セカンダリ レプリカの場所への接続は、次の場合に失敗します。  
  
1. セカンダリ レプリカの場所が接続を受け入れないように構成されている場合。  
  
2. アプリケーションが `ApplicationIntent=ReadWrite` (後で説明) を使用している場合、セカンダリ レプリカの場所は読み取り専用アクセスとして構成されます。  
  
 <xref:System.Data.SqlClient.SqlDependency> 読み取り専用のセカンダリ レプリカでサポートされていません。  
  
 プライマリ レプリカが読み取り専用のワークロードを拒否するように設定され、接続文字列が  `ApplicationIntent=ReadOnly` を含んでいる場合、接続は失敗します。  
  
## <a name="upgrading-to-use-multi-subnet-clusters-from-database-mirroring"></a>データベース ミラーリングから複数のサブネット クラスターを使用するためのアップグレード  
 接続エラー (<xref:System.ArgumentException>) は、`MultiSubnetFailover` および `Failover Partner` 接続のキーワードが接続文字列内に存在する場合や、`MultiSubnetFailover=True` および TCP 以外のプロトコルが使用された場合に発生します。 エラー (<xref:System.Data.SqlClient.SqlException>) 場合にも発生`MultiSubnetFailover`使用し、SQL Server は、データベース ミラーリング ペアの一部であることを示すフェールオーバー パートナー応答を返します。  
  
 現在データベース ミラーリングを使用している SqlClient アプリケーションを複数のサブネットのシナリオへとアップグレードする場合、`Failover Partner` 接続プロパティを削除し、`MultiSubnetFailover` に設定した `True` で置き換え、接続文字列のサーバー名を可用性グループ リスナーと置き換える必要があります。 接続文字列が `Failover Partner` および `MultiSubnetFailover=True` を使用していると、ドライバーがエラーを生成します。 ただし、接続文字列が `Failover Partner` および `MultiSubnetFailover=False` (または  `ApplicationIntent=ReadWrite`) を使用している場合、アプリケーションはデータベース ミラーリングを使用します。  
  
 データベース ミラーリングが AG のプライマリ データベースで使用される場合、および  `MultiSubnetFailover=True` が可用性グループ リスナーではなくプライマリ データベースに接続する接続文字列で使用される場合、ドライバーはエラーを返します。  
  
## <a name="specifying-application-intent"></a>アプリケーションの目的の指定  
 `ApplicationIntent=ReadOnly` の場合、クライアントは AlwaysOn が有効になったデータベースに接続する場合に、読み取られたワークロードを要求します。 サーバーは、接続時および USE データベース ステートメントの間、その目的を強制しますが、AlwaysOn が有効になったデータベースに対してのみ、これを行います。  
  
 `ApplicationIntent` キーワードは従来の読み取り専用のデータベースでは機能しません。  
  
 データベースは、対象となる AlwaysOn データベースのワークロードの読み取りを許可または拒否できます。 (これは、`ALLOW_CONNECTIONS`の句、`PRIMARY_ROLE`と`SECONDARY_ROLE`[!INCLUDE[tsql](../../../../../includes/tsql-md.md)]ステートメントです)。  
  
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
