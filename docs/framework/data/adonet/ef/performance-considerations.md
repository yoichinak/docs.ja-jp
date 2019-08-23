---
title: パフォーマンスに関する考慮事項 (Entity Framework)
ms.date: 03/30/2017
ms.assetid: 61913f3b-4f42-4d9b-810f-2a13c2388a4a
ms.openlocfilehash: 4836125205f3d4cbbe852c92f2a88aca331ded70
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69962249"
---
# <a name="performance-considerations-entity-framework"></a>パフォーマンスに関する考慮事項 (Entity Framework)
このトピックでは、ADO.NET Entity Framework のパフォーマンス特性を示し、Entity Framework アプリケーションのパフォーマンスを向上させるために役立つ注意事項について説明します。  
  
## <a name="stages-of-query-execution"></a>クエリ実行の段階  
 Entity Framework でのクエリのパフォーマンスをより深く理解するには、概念モデルに対して実行されたクエリがデータをオブジェクトとして返す際の動作を知る必要があります。 この一連の動作を次の表に示します。  
  
|操作|相対コスト|頻度|コメント|  
|---------------|-------------------|---------------|--------------|  
|メタデータの読み込み|中|各アプリケーション ドメイン内で 1 回|Entity Framework が使用するモデルとマッピングのメタデータが、<xref:System.Data.Metadata.Edm.MetadataWorkspace> に読み込まれます。 このメタデータはグローバルにキャッシュされ、同じアプリケーション ドメイン内にある <xref:System.Data.Objects.ObjectContext> の他のインスタンスも使用できるようになります。|  
|データベース接続を開く|中<sup>1</sup>|必要時|開いているデータベースへの接続によって貴重なリソース[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]が消費されるため、は必要な場合にのみデータベース接続を開き、閉じます。 接続は、明示的に開くこともできます。 詳細については、「[接続とトランザクションの管理](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896325(v=vs.100))」を参照してください。|  
|ビューの生成|High|各アプリケーション ドメイン内で 1 回 (事前生成可能)|Entity Framework が、概念モデルに対してクエリを実行したり変更内容をデータ ソースに保存したりできるようになるには、データベースにアクセスするためのローカル クエリ ビューのセットを事前に生成しておく必要があります。 このビューを生成する際のコストは高いため、デザイン時にビューを事前に作成してプロジェクトに追加しておくことができます。 詳細については、「[方法 :クエリのパフォーマンス](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896240(v=vs.100))を向上させるためにビューを事前に生成します。|  
|クエリの準備|中<sup>2</sup>|各一意のクエリに対して 1 回|クエリ コマンドを作成したり、モデルとマッピングのメタデータに基づいてコマンド ツリーを生成したり、返されるデータの形状を定義したりするためのコストが含まれます。 Entity SQL と LINQ の両方のクエリ コマンドがキャッシュされるため、同じクエリであれば、後続の実行は短時間で済みます。 後続の実行でさらにコストを削減するためにコンパイル済み LINQ クエリを使用でき、コンパイル済みクエリが自動的にキャッシュされる LINQ クエリよりも効率的である場合があります。 詳細については、「[コンパイル済みクエリ (LINQ to Entities)](../../../../../docs/framework/data/adonet/ef/language-reference/compiled-queries-linq-to-entities.md)」を参照してください。 LINQ クエリの実行に関する一般的な情報については、「 [LINQ to Entities](../../../../../docs/framework/data/adonet/ef/language-reference/linq-to-entities.md)」を参照してください。 **注:** メモリ内コレクションへ `Enumerable.Contains` 演算子を追加する LINQ to Entities クエリは自動的にキャッシュされません。 またコンパイル済み LINQ クエリのメモリ内コレクションをパラメーターで表すことは許可されていません。|  
|クエリの実行|低<sup>2</sup>|各クエリに対して 1 回|ADO.NET データ プロバイダーを使用してデータ ソースに対してコマンドを実行するコスト。 大半のデータ ソースではクエリ プランがキャッシュされるため、同じクエリであれば、後続の実行は短時間で済むことがあります。|  
|型の読み込みと検証|低<sup>3</sup>|各 <xref:System.Data.Objects.ObjectContext> インスタンスに対して 1 回|型が読み込まれ、概念モデルが定義する型に照らし合わせて検証されます。|  
|追跡|低<sup>3</sup>|クエリが返す各オブジェクトに対して 1 回 <sup>4</sup>|クエリが <xref:System.Data.Objects.MergeOption.NoTracking> のマージ オプションを使用する場合には、この段階でパフォーマンスが低下することはありません。<br /><br /> クエリが <xref:System.Data.Objects.MergeOption.AppendOnly>、<xref:System.Data.Objects.MergeOption.PreserveChanges>、または <xref:System.Data.Objects.MergeOption.OverwriteChanges> のいずれかのマージ オプションを使用する場合には、クエリ結果が <xref:System.Data.Objects.ObjectStateManager> で追跡されます。 クエリが返す追跡対象の各オブジェクトに対して <xref:System.Data.EntityKey> が生成され、<xref:System.Data.Objects.ObjectStateEntry> に <xref:System.Data.Objects.ObjectStateManager> を作成するために使用されます。 <xref:System.Data.Objects.ObjectStateEntry> に対応する既存の <xref:System.Data.EntityKey> がある場合には、既存のオブジェクトが返されます。 <xref:System.Data.Objects.MergeOption.PreserveChanges> または <xref:System.Data.Objects.MergeOption.OverwriteChanges> オプションが指定されている場合、オブジェクトは更新後に返されます。<br /><br /> 詳細については、「 [Id 解決、状態管理、および Change Tracking](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896269(v=vs.100))」を参照してください。|  
|オブジェクトの具体化|中程度<sup>3</sup>|クエリが返す各オブジェクトに対して 1 回 <sup>4</sup>|返された <xref:System.Data.Common.DbDataReader> オブジェクトを読み取ったり、オブジェクトを作成してプロパティ値を設定したりするプロセス。プロパティ値は、<xref:System.Data.Common.DbDataRecord> クラスの各インスタンスの値に基づきます。 オブジェクトが <xref:System.Data.Objects.ObjectContext> に既に存在しており、クエリに <xref:System.Data.Objects.MergeOption.AppendOnly> または <xref:System.Data.Objects.MergeOption.PreserveChanges> マージ オプションが指定されている場合、この段階でパフォーマンスを低下することはありません。 詳細については、「 [Id 解決、状態管理、および Change Tracking](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896269(v=vs.100))」を参照してください。|  
  
 <sup>1</sup>データソースプロバイダーが接続プールを実装する場合、接続を開くコストはプール全体に分散されます。 .NET Provider for SQL Server は、接続プールをサポートしています。  
  
 <sup>2</sup>コストは、クエリの複雑さが増加して増加します。  
  
 <sup>3</sup>合計コストは、クエリによって返されるオブジェクトの数に比例して増加します。  
  
 <sup>4</sup>このオーバーヘッドは、entityclient クエリには必要ありません。 <xref:System.Data.EntityClient.EntityDataReader> entityclient クエリでは、オブジェクトではなくが返されるからです。 詳細については、「 [Entity Framework 用の EntityClient プロバイダー](../../../../../docs/framework/data/adonet/ef/entityclient-provider-for-the-entity-framework.md)」を参照してください。  
  
## <a name="additional-considerations"></a>その他の考慮事項  
 Entity Framework アプリケーションのパフォーマンスを低下させる可能性があるその他の考慮事項を次に示します。  
  
### <a name="query-execution"></a>クエリの実行  
 クエリがリソースを大量に消費することがあるので、コード内のどの個所で、またどのコンピューター上でクエリを実行するのかを検討してください。  
  
#### <a name="deferred-versus-immediate-execution"></a>遅延実行と即時実行  
 <xref:System.Data.Objects.ObjectQuery%601> クエリまたは LINQ クエリを作成しても、すぐには実行されないことがあります。 クエリの実行は、結果が必要になるまで遅延されます。たとえば、`foreach` (C#) または `For Each` (Visual Basic) の列挙時や、<xref:System.Collections.Generic.List%601> コレクションに割り当てられた場合などです。 クエリがすぐに実行されるのは、<xref:System.Data.Objects.ObjectQuery%601.Execute%2A> 上で <xref:System.Data.Objects.ObjectQuery%601> メソッドが呼び出されたときや、単一クエリを返す LINQ メソッド (<xref:System.Linq.Enumerable.First%2A> や <xref:System.Linq.Enumerable.Any%2A> など) が呼び出されたときです。 詳細については、「[オブジェクトクエリ](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896241(v=vs.100))と[クエリ実行 (LINQ to Entities)](../../../../../docs/framework/data/adonet/ef/language-reference/query-execution.md)」を参照してください。  
  
#### <a name="client-side-execution-of-linq-queries"></a>クライアント側での LINQ クエリの実行  
 LINQ クエリの実行は、データ ソースをホストするコンピューター上で行われますが、LINQ クエリは部分的にクライアント コンピューター上で評価されることがあります。 詳細については、「[クエリの実行」 (LINQ to Entities)](../../../../../docs/framework/data/adonet/ef/language-reference/query-execution.md)のストア実行に関するセクションを参照してください。  
  
### <a name="query-and-mapping-complexity"></a>クエリとマッピングの複雑さ  
 個々のクエリの複雑さおよびエンティティ モデルのマッピングの複雑さは、クエリ パフォーマンスに大きな影響を及ぼします。  
  
#### <a name="mapping-complexity"></a>マッピングの複雑さ  
 概念モデルのエンティティとストレージ モデルのテーブルとの間で、単純な一対一より複雑なマッピングのモデルは、一対一マッピングのモデルより複雑なコマンドを生成します。  
  
#### <a name="query-complexity"></a>クエリの複雑さ  
 データソースに対して実行されるコマンド内に多数の結合を必要とするクエリや、データを大量に返すクエリは、次のようにパフォーマンスを低下させることがあります。  
  
- 単純に見える概念モデルに対してクエリを実行したところ、より複雑なクエリをデータ ソースに対して実行する結果になることがあります。 これは、Entity Framework が、概念モデルに対するクエリをデータ ソースに対する等価のクエリに変換するからです。 概念モデルの 1 つのエンティティ セットが、データ ソースの複数のテーブルにマップされている場合や、エンティティ間のリレーションシップが結合テーブルにマップされている場合には、データ ソース クエリに対して実行されるクエリ コマンドで 1 つ以上の結合が必要になる場合があります。  
  
    > [!NOTE]
    > 所定のクエリでデータ ソースに対して実行されるコマンドを表示するには、<xref:System.Data.Objects.ObjectQuery.ToTraceString%2A> クラスまたは <xref:System.Data.Objects.ObjectQuery%601> クラスの <xref:System.Data.EntityClient.EntityCommand> メソッドを使用します。 詳細については、「[方法 :ストアコマンド](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896348(v=vs.100))を表示します。  
  
- Entity SQL クエリが入れ子になっていると、サーバー上で結合が作成され、その結果多数の行が返されることがあります。  
  
     projection 句内の入れ子になったクエリの例を次に示します。  
  
    ```  
    SELECT c, (SELECT c, (SELECT c FROM AdventureWorksModel.Vendor AS c  ) As Inner2   
        FROM AdventureWorksModel.JobCandidate AS c  ) As Inner1   
        FROM AdventureWorksModel.EmployeeDepartmentHistory AS c  
    ```  
  
     さらに、このようなクエリでは、入れ子になったクエリ全体でオブジェクトを複製する単一クエリがクエリ パイプラインで生成されます。 そのため、1 つの列が複数回複製されることがあります。 SQL Server など、一部のデータベースでは、これによって TempDB テーブルのサイズが非常に大きくなり、サーバーのパフォーマンスに悪影響を及ぼす場合があります。 入れ子になったクエリを実行するときには、注意を払う必要があります。  
  
- クライアントが、結果セットのサイズに比例してリソースを消費するような操作を実行している場合、データを大量に返すクエリを実行すると、パフォーマンスが低下することがあります。 このような場合には、クエリによって返されるデータの量を制限することを検討してください。 詳細については、「[方法 :クエリ結果](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738702(v=vs.100))を表示するページ。  
  
 Entity Framework によって自動的に生成されるコマンドは、データベース開発者が明示的に記述した同様のコマンドより複雑になることがあります。 データ ソースに対して実行されるコマンドを明示的に制御する必要がある場合には、テーブル値関数またはストアド プロシージャへのマッピングを定義することを検討してください。  
  
#### <a name="relationships"></a>関係  
 クエリのパフォーマンスを最適化するには、エンティティ間のリレーションシップをエンティティ モデル内のアソシエーションとしてだけでなく、データ ソース内の論理リレーションシップとしても定義する必要があります。  
  
### <a name="query-paths"></a>クエリ パス  
 既定では、<xref:System.Data.Objects.ObjectQuery%601> を実行しても、関連オブジェクトは返されません (リレーションシップ自体を表現するオブジェクトが存在する場合でも)。 関連オブジェクトは、次の 3 つの方法のいずれかで読み込むことができます。  
  
1. <xref:System.Data.Objects.ObjectQuery%601> が実行される前にクエリ パスを設定します。  
  
2. オブジェクトが公開するナビゲーション プロパティに対して `Load` メソッドを呼び出します。  
  
3. <xref:System.Data.Objects.ObjectContextOptions.LazyLoadingEnabled%2A> で <xref:System.Data.Objects.ObjectContext> オプションを `true` に設定します。 これは、 [Entity Data Model デザイナー](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc716685(v=vs.100))を使用してオブジェクトレイヤーコードを生成するときに自動的に実行されることに注意してください。 詳細については、「[生成されるコードの概要](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc982041(v=vs.100))」を参照してください。  
  
 使用するオプションを検討する際には、データベースに対する要求数と 1 つのクエリで返されるデータ量の間でのトレードオフに注意してください。 詳細については、「[関連オブジェクトの読み込み](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896272(v=vs.100))」を参照してください。  
  
#### <a name="using-query-paths"></a>クエリ パスの使用  
 クエリ パスは、クエリによって返されるオブジェクトのグラフを定義します。 クエリ パスを定義する場合、データベースに対する 1 件の要求だけで、パスによって定義されたすべてのオブジェクトが返されます。 クエリ パスを使用すると、見かけ上は簡単なオブジェクト クエリのデータ ソースに対して複雑なコマンドが実行される可能性があります。 これは、1 つのクエリ内の関連オブジェクトを返すには、1 つまたは複数の結合が必要になるために発生します。 継承のあるエンティティや多対多のリレーションシップを含んだパスなど、複雑なエンティティ モデルに対してクエリを実行する場合は、さらに複雑になります。  
  
> [!NOTE]
> <xref:System.Data.Objects.ObjectQuery.ToTraceString%2A> によって生成されるコマンドを表示するには、<xref:System.Data.Objects.ObjectQuery%601> メソッドを使用します。 詳細については、「[方法 :ストアコマンド](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896348(v=vs.100))を表示します。  
  
 クエリ パスに含まれる関連オブジェクトが多すぎる場合や、オブジェクトに含まれる行データが多すぎる場合、データ ソースはクエリを完了できないことがあります。 これは、クエリでデータ ソースの機能を超える中間一時ストレージが必要になる場合に発生します。 この場合は、関連オブジェクトを明示的に読み込むと、データ ソース クエリの複雑さを軽減できます。  
  
#### <a name="explicitly-loading-related-objects"></a>関連オブジェクトの明示的な読み込み  
 `Load` または <xref:System.Data.Objects.DataClasses.EntityCollection%601> を返すナビゲーション プロパティ上で <xref:System.Data.Objects.DataClasses.EntityReference%601> メソッドを呼び出すことによって、関連オブジェクトを明示的に読み込むことができます。 オブジェクトを明示的に読み込むには、`Load` を呼び出すたびにデータベースへのラウンドトリップが必要になります。  
  
> [!NOTE]
> `Load` ステートメント (Visual Basic では `foreach`) を使用するときなど、返されたオブジェクトのコレクションをループ処理しながら、`For Each` を呼び出す場合、データ ソース固有のプロバイダーは 1 つの接続で複数のアクティブな結果セットをサポートする必要があります。 SQL Server データベースの場合、プロバイダー接続文字列に `MultipleActiveResultSets = true` の値を指定する必要があります。  
  
 エンティティに <xref:System.Data.Objects.ObjectContext.LoadProperty%2A> プロパティまたは <xref:System.Data.Objects.DataClasses.EntityCollection%601> プロパティがない場合は、<xref:System.Data.Objects.DataClasses.EntityReference%601> メソッドを使用することもできます。 これは、POCO エンティティを使用している場合に有効です。  
  
 関連オブジェクトを明示的に読み込むと、結合の数と冗長データの量が減少しますが、`Load` にはデータベースへの接続が繰り返し必要になります。多数のオブジェクトを明示的に読み込む場合には、高コストになることがあります。  
  
### <a name="saving-changes"></a>変更の保存  
 <xref:System.Data.Objects.ObjectContext.SaveChanges%2A> 上で <xref:System.Data.Objects.ObjectContext> メソッドを呼び出すと、コンテキスト内で追加、更新、または削除された各オブジェクトに対して独立した作成、更新、または削除のコマンドが生成されます。 このコマンドは、1 つのトランザクションのデータ ソースで実行されます。 クエリの場合と同様に、作成、更新、および削除の操作は、概念モデルのマッピングの複雑さに依存します。  
  
### <a name="distributed-transactions"></a>分散トランザクション  
 明示的トランザクションでの操作で、分散トランザクション コーディネーター (DTC: Distributed Transaction Coordinator) によって管理されるリソースが必要とされることがありますが、このような操作は DTC を必要としない同様の操作より高コストになります。 DTC への昇格は、次の状況で発生します。  
  
- 明示的トランザクションを常に DTC に昇格する SQL Server 2000 データベースやその他のデータ ソースに対して、明示的トランザクションで操作を実行する場合。  
  
- SQL Server 2005 に対して明示的トランザクションで操作を実行し、かつ接続が [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] によって管理される場合。 これは、接続が閉じられてから同じトランザクション内で再度開かれると、SQL Server 2005 が DTC に必ず昇格するためです。この動作は、[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] の既定の動作です。 この DTC 昇格は、SQL Server 2008 使用時には生じません。 SQL Server 2005 使用時にこの昇格を回避するには、トランザクション内で接続を明示的に開いて閉じる必要があります。 詳細については、「[接続とトランザクションの管理](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896325(v=vs.100))」を参照してください。  
  
 明示的トランザクションが使用されるのは、1 つの <xref:System.Transactions> トランザクション内で操作を 1 つ以上実行するときです。 詳細については、「[接続とトランザクションの管理](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896325(v=vs.100))」を参照してください。  
  
## <a name="strategies-for-improving-performance"></a>パフォーマンスを向上させるための戦略  
 次の戦略を使用すると、Entity Framework でのクエリの全体的なパフォーマンスを向上させることができます。  
  
#### <a name="pre-generate-views"></a>ビューの事前生成  
 アプリケーションがクエリを初めて実行する際、エンティティ モデルに基づいたビュー生成は高コストになります。 EdmGen.exe ユーティリティを使用して、プロジェクトに追加できる Visual Basic または C# のコード ファイルとして設計時に事前にビューを生成しておきます。 テキスト テンプレート変換ツールキットを使用して、事前にコンパイルされたビューを生成することもできます。 事前に生成したビューは、現在のバージョンの指定エンティティ モデルに対応することを確認するために、実行時に検証されます。 詳細については、「[方法 :クエリのパフォーマンス](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896240(v=vs.100))を向上させるためにビューを事前に生成します。
  
 サイズが非常に大きいモデルで作業する場合は、次の点に注意してください。  
  
 .NET メタデータ形式では、特定のバイナリ内のユーザー文字列の数が 16,777,215 (0xFFFFFF) に制限されます。 非常に大きなモデルのビューを生成しているときに、ビューファイルがこのサイズ制限に達した場合は、"他のユーザー文字列を作成する論理空間が残っていません" と表示されます。 コンパイルエラーです。 このサイズ制限は、すべてのマネージド バイナリに適用されます。 詳細については、大規模で複雑なモデルを使用する場合のエラーを回避する方法を示す[ブログ](https://go.microsoft.com/fwlink/?LinkId=201476)を参照してください。  
  
#### <a name="consider-using-the-notracking-merge-option-for-queries"></a>クエリの NoTracking マージ オプションの使用を検討する  
 オブジェクト コンテキスト内で返されたオブジェクトを追跡するにはコストが生じます。 オブジェクトに対する変更内容を検出したり、同じ論理エンティティに対する複数の要求で同じオブジェクト インスタンスが返されるようにするには、オブジェクトを <xref:System.Data.Objects.ObjectContext> インスタンスにアタッチする必要があります。 オブジェクトを更新または削除する予定がなく、id 管理を必要としない場合は、クエリ<xref:System.Data.Objects.MergeOption.NoTracking>の実行時にマージオプションを使用することを検討してください。  
  
#### <a name="return-the-correct-amount-of-data"></a>適量のデータを返す  
 シナリオによっては、<xref:System.Data.Objects.ObjectQuery%601.Include%2A> メソッドを使用してクエリ パスを指定する方がはるかに速いことがあります。データベースに対する必要なラウンド トリップ数が減るからです。 ただし、他のシナリオでは、関連オブジェクトを読み込むためにデータベースへのラウンド トリップを増やす方が速くなることがあります。これは、クエリが単純で結合数が少ないほど、データの冗長性が低下するからです。 したがって、関連オブジェクトを取得するためのさまざまな方法について、パフォーマンスをテストすることをお勧めします。 詳細については、「[関連オブジェクトの読み込み](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896272(v=vs.100))」を参照してください。  
  
 1 つのクエリで大量のデータが返されることを回避するには、クエリの結果を扱いやすいサイズのグループに分割してページングすることを検討してください。 詳細については、「[方法 :クエリ結果](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738702(v=vs.100))を表示するページ。  
  
#### <a name="limit-the-scope-of-the-objectcontext"></a>ObjectContext のスコープを制限する  
 通常は、<xref:System.Data.Objects.ObjectContext> ステートメント (Visual Basic では `using`) 内に `Using…End Using` インスタンスを作成する必要があります。 これにより、パフォーマンスが向上します。これは、コードがステートメント ブロックを終了するときに、オブジェクト コンテキストに関連付けられたリソースが自動的に廃棄されるからです。 ただし、オブジェクト コンテキストによって管理されるオブジェクトにコントロールがバインドされている場合、バインドが必要とされる間は <xref:System.Data.Objects.ObjectContext> インスタンスを保持し、手動で廃棄する必要があります。 詳細については、「[接続とトランザクションの管理](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896325(v=vs.100))」を参照してください。  
  
#### <a name="consider-opening-the-database-connection-manually"></a>データベース接続を手動で開くことを検討する  
 アプリケーションで一連のオブジェクトクエリまたは頻繁にの呼び出し<xref:System.Data.Objects.ObjectContext.SaveChanges%2A>を実行して、作成、更新、および削除の各操作を[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]データソースに保存する場合、は、データソースへの接続を継続的に開いて閉じる必要があります。 このような状況では、操作の開始時に接続を手動で開いて、操作の完了時に接続を手動で閉じるか廃棄することを検討してください。 詳細については、「[接続とトランザクションの管理](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896325(v=vs.100))」を参照してください。  
  
## <a name="performance-data"></a>パフォーマンス データ  
 Entity Framework の一部のパフォーマンスデータは、 [ADO.NET チームのブログ](https://go.microsoft.com/fwlink/?LinkId=91905)の次の投稿で公開されています。  
  
- [ADO.NET Entity Framework のパフォーマンスの調査-パート1](https://go.microsoft.com/fwlink/?LinkId=123907)  
  
- [ADO.NET Entity Framework のパフォーマンスの調査–パート2](https://go.microsoft.com/fwlink/?LinkId=123909)  
  
- [ADO.NET Entity Framework のパフォーマンスの比較](https://go.microsoft.com/fwlink/?LinkID=123913)  
  
## <a name="see-also"></a>関連項目

- [開発および配置に関する注意事項](../../../../../docs/framework/data/adonet/ef/development-and-deployment-considerations.md)
