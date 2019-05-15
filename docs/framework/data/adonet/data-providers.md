---
title: .NET Framework データ プロバイダー
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 03a9fc62-2d24-491a-9fe6-d6bdb6dcb131
ms.openlocfilehash: 9fead8a5d54fba7232831bba349f27b7eed4657b
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/14/2019
ms.locfileid: "65583791"
---
# <a name="net-framework-data-providers"></a>.NET Framework データ プロバイダー
.NET Framework データ プロバイダーは、データベースへの接続、コマンドの実行と結果の取得に使用されます。 その結果は、直接処理されるか、必要に応じてユーザーに公開されるように <xref:System.Data.DataSet> に格納されるか、取得したデータセットを複数のソースからのデータと組み合わせるか、または、層間でリモート処理されます。 .NET framework データ プロバイダーは、データ ソースとコード間の最小限の層を作成するには、機能を損なうことがなくパフォーマンスの向上、軽量です。  
  
 次の表には、.NET Framework に含まれているデータ プロバイダーが一覧表示します。  
  
|.NET Framework データ プロバイダー|説明|  
|-------------------------------------------------------------------------------|-----------------|  
|.NET Framework SQL Server 用データ プロバイダー|Microsoft SQL Server へのデータ アクセスを提供します。 <xref:System.Data.SqlClient> 名前空間を使用してください。|  
|.NET Framework Data Provider for OLE DB|OLE DB を使用して公開されるデータ ソースに対応。 <xref:System.Data.OleDb> 名前空間を使用してください。|  
|.NET Framework Data Provider for ODBC|ODBC を使用して公開されるデータ ソースに対応。 <xref:System.Data.Odbc> 名前空間を使用してください。|  
|.NET Framework Oracle 用データ プロバイダー|Oracle データ ソースに対応。 .NET Framework Data Provider for Oracle サポートの Oracle クライアント ソフトウェア version 8.1.7 以降を使用して、<xref:System.Data.OracleClient>名前空間。|  
|EntityClient プロバイダー|エンティティ データ モデル (EDM) アプリケーションにデータ アクセスを提供します。 <xref:System.Data.EntityClient> 名前空間を使用してください。|  
|.NET framework Data Provider for SQL Server Compact 4.0。|Microsoft SQL Server Compact 4.0 のデータ アクセスを提供します。 [System.Data.SqlServerCe](https://docs.microsoft.com/previous-versions/sql/compact/sql-server-compact-4.0/ec4st0e3(v=vs.100)) 名前空間を使用します。|  
  
## <a name="core-objects-of-net-framework-data-providers"></a>.NET Framework Data Providers の核となるオブジェクト  
 次の表では、.NET Framework データ プロバイダーを構成する 4 つの主要なオブジェクトについて説明します。  
  
|Object|説明|  
|------------|-----------------|  
|`Connection`|特定のデータ ソースへの接続を確立します。 すべての `Connection` オブジェクトの基本クラスは <xref:System.Data.Common.DbConnection> クラスです。|  
|`Command`|データ ソースに対してコマンドを実行します。 `Parameters` を公開し、`Transaction` から `Connection` のスコープ内で実行できます。 すべての `Command` オブジェクトの基本クラスは <xref:System.Data.Common.DbCommand> クラスです。|  
|`DataReader`|データ ソースから、前方参照専用で読み取り専用のデータ ストリームを読み取ります。 すべての `DataReader` オブジェクトの基本クラスは <xref:System.Data.Common.DbDataReader> クラスです。|  
|`DataAdapter`|`DataSet` にデータ ソースのデータを読み込んだり、データ ソースの更新内容を解決したりします。 すべての `DataAdapter` オブジェクトの基本クラスは <xref:System.Data.Common.DbDataAdapter> クラスです。|  
  
 コア クラスは、このドキュメントで前述の表に、.NET Framework データ プロバイダーには、次の表に記載されているクラスも含まれています。  
  
|Object|説明|  
|------------|-----------------|  
|`Transaction`|データ ソースでトランザクション内にコマンドを追加します。 すべての `Transaction` オブジェクトの基本クラスは <xref:System.Data.Common.DbTransaction> クラスです。 ADO.NET は、 <xref:System.Transactions> 名前空間のクラスを使ったトランザクションもサポートします。|  
|`CommandBuilder`|`DataAdapter` のコマンド プロパティを自動的に生成したり、ストアド プロシージャからパラメーター情報を取得したり、`Parameters` オブジェクトの `Command` コレクションにパラメーターを設定したりするためのヘルパー オブジェクトです。 すべての `CommandBuilder` オブジェクトの基本クラスは <xref:System.Data.Common.DbCommandBuilder> クラスです。|  
|`ConnectionStringBuilder`|`Connection` オブジェクトが使用する接続文字列を簡単に作成および管理するためのヘルパー オブジェクトです。 すべての `ConnectionStringBuilder` オブジェクトの基本クラスは <xref:System.Data.Common.DbConnectionStringBuilder> クラスです。|  
|`Parameter`|コマンドやストアド プロシージャの入力パラメーター、出力パラメーター、および戻り値パラメーターを定義します。 すべての `Parameter` オブジェクトの基本クラスは <xref:System.Data.Common.DbParameter> クラスです。|  
|`Exception`|データ ソースでエラーが検出されたときに返されます。 クライアントで検出されたエラー、.NET Framework データ プロバイダーは、.NET Framework の例外をスローします。 すべての `Exception` オブジェクトの基本クラスは <xref:System.Data.Common.DbException> クラスです。|  
|`Error`|データ ソースから返された警告またはエラー情報を公開します。|  
|`ClientPermission`|.NET Framework データ プロバイダーのコード アクセス セキュリティ属性に対して用意されています。 すべての `ClientPermission` オブジェクトの基本クラスは <xref:System.Data.Common.DBDataPermission> クラスです。|  
  
## <a name="net-framework-data-provider-for-sql-server-sqlclient"></a>SQL Server (SqlClient) の .NET framework Data Provider  
 For SQL Server (SqlClient) には、.NET Framework Data Provider は、SQL Server との通信に独自のプロトコルを使用します。 これは軽量は OLE DB、またはオープン データベース コネクティビティ (ODBC) のレイヤーを追加せずに直接 SQL Server へのアクセスに最適化されるためを実行します。 次の図は、for SQL Server、.NET Framework Data Provider、.NET Framework Data Provider for OLE DB 対照的です。 .NET Framework Data Provider for OLE DB 接続プールを提供する OLE DB サービス コンポーネントと、トランザクション サービスとデータ ソースの OLE DB プロバイダーの両方で、OLE DB データ ソースと通信します。  
  
> [!NOTE]
>  .NET Framework Data Provider for ODBC は、for OLE DB に、.NET Framework Data Provider に同様のアーキテクチャを持つたとえば、ODBC Service コンポーネントを呼び出します。  
  
 ![データ プロバイダー](../../../../docs/framework/data/adonet/media/netdataproviders-bpuedev11.gif "NETDataProviders_bpuedev11")  
.NET Framework Data Provider for SQL Server と .NET Framework Data Provider for OLE DB の比較  
  
 SQL Server クラスの .NET Framework データ プロバイダーにある、<xref:System.Data.SqlClient>名前空間。  
  
 .NET Framework Data Provider for SQL Server では、ローカルおよび分散トランザクションをサポートします。 分散トランザクションの場合、.NET Framework Data Provider for SQL Server を既定では、自動的にトランザクションに参加し、Windows コンポーネント サービスからトランザクションの詳細を取得または<xref:System.Transactions>します。 詳細については、次を参照してください。[トランザクションと同時実行](../../../../docs/framework/data/adonet/transactions-and-concurrency.md)します。  
  
 名前空間 `System.Data.SqlClient` をユーザーのアプリケーションにインクルードする方法を次のコード サンプルで示します。  
  
```vb  
Imports System.Data.SqlClient  
```  
  
```csharp  
using System.Data.SqlClient;  
```  
  
## <a name="net-framework-data-provider-for-ole-db"></a>.NET Framework Data Provider for OLE DB  
 .NET Framework Data Provider for OLE DB (OleDb) では、COM 相互運用機能を介してネイティブ OLE DB を使用して、データ アクセスを有効にします。 .NET Framework Data Provider for OLE DB では、ローカルおよび分散トランザクションをサポートします。 分散トランザクションの場合、.NET Framework Data Provider for OLE DB、既定では自動的にトランザクションに参加し、Windows コンポーネント サービスからトランザクションの詳細を取得します。 詳細については、次を参照してください。[トランザクションと同時実行](../../../../docs/framework/data/adonet/transactions-and-concurrency.md)します。  
  
 [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)]とのテストが完了しているプロバイダーを次の表に示します。  
  
|ドライバー|プロバイダー|  
|------------|--------------|  
|SQLOLEDB|Microsoft OLE DB provider for SQL Server|  
|MSDAORA|Microsoft OLE DB Provider for Oracle|  
|Microsoft.Jet.OLEDB.4.0|OLE DB Provider for Microsoft Jet|  
  
> [!NOTE]
>  [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] アプリケーションなどのマルチスレッド アプリケーションのデータ ソースとして Access (Jet) データベースを使用することはお勧めできません。 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] アプリケーションのデータ ソースとして Jet を使用する必要がある場合、 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] アプリケーションから Access データベースへの接続で問題が発生することがあるので注意してください。  
  
 .NET Framework Data Provider for OLE DB は、OLE DB バージョン 2.5 のインターフェイスをサポートしていません。 OLE DB プロバイダーを OLE DB 2.5 インターフェイスのサポートを必要とするが正しく機能しないと、.NET Framework Data Provider for OLE DB。 これには Microsoft OLE DB Provider for Exchange および Microsoft OLE DB Provider for Internet Publishing が含まれます。  
  
 .NET Framework Data Provider for OLE DB は、OLE DB provider for ODBC (MSDASQL) では機能しません。 ODBC データ ソースを使用してをアクセスする[!INCLUDE[vstecado](../../../../includes/vstecado-md.md)]、for ODBC、.NET Framework Data Provider を使用します。  
  
 OLE DB クラス用の .NET framework データ プロバイダーにある、<xref:System.Data.OleDb>名前空間。 名前空間 `System.Data.OleDb` をユーザーのアプリケーションにインクルードする方法を次のコード サンプルで示します。  
  
```vb  
Imports System.Data.OleDb  
```  
  
```csharp  
using System.Data.OleDb;  
```  
  
## <a name="net-framework-data-provider-for-odbc"></a>.NET Framework Data Provider for ODBC  
 .NET Framework Data Provider for ODBC (Odbc) では、ネイティブ ODBC ドライバー マネージャー (DM) を使用して、データ アクセスを有効にします。 ODBC データ プロバイダーはローカル トランザクションと分散トランザクションのどちらもサポートします。 分散トランザクションの場合、既定で、ODBC データ プロバイダーは自動的にトランザクションに参加し、トランザクションの詳細を Windows コンポーネント サービスから取得します。 詳細については、次を参照してください。[トランザクションと同時実行](../../../../docs/framework/data/adonet/transactions-and-concurrency.md)します。  
  
 [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)]とのテストが完了している ODBC ドライバーを次の表に示します。  
  
|ドライバー|  
|------------|  
|SQL Server|  
|Microsoft ODBC for Oracle|  
|Microsoft Access ドライバー (*.mdb)|  
  
 .NET framework Data Provider for ODBC クラスにある、<xref:System.Data.Odbc>名前空間。  
  
 名前空間 `System.Data.Odbc` をユーザーのアプリケーションにインクルードする方法を次のコード サンプルで示します。  
  
```vb  
Imports System.Data.Odbc  
```  
  
```csharp  
using System.Data.Odbc;  
```  
  
> [!NOTE]
>  .NET Framework Data Provider for ODBC は、MDAC 2.6 または以降のバージョンが必要です。 および、MDAC 2.8 SP1 をお勧めします。 MDAC 2.8 SP1 は「 [データ アクセスおよびストレージ デベロッパー センター](https://go.microsoft.com/fwlink/?linkid=4173)」からダウンロードできます。  
  
## <a name="net-framework-data-provider-for-oracle"></a>.NET Framework Oracle 用データ プロバイダー  
 For Oracle (OracleClient) は、.NET Framework Data Provider には、Oracle クライアント接続ソフトウェアを通じて、Oracle データ ソースへのアクセスができるようにします。 このデータ プロバイダーは Oracle クライアント ソフトウェア バージョン 8.1.7 以降をサポートしています。 データ プロバイダーはローカル トランザクションと分散トランザクションのどちらもサポートします。 詳細については、次を参照してください。[トランザクションと同時実行](../../../../docs/framework/data/adonet/transactions-and-concurrency.md)します。  
  
 .NET Framework Data Provider for Oracle では、Oracle データ ソースに接続できる前に、システムに Oracle クライアント ソフトウェア (バージョン 8.1.7 またはそれ以降のバージョン) が必要です。  
  
 .NET framework Data Provider for Oracle クラスにある、<xref:System.Data.OracleClient>に含まれている名前空間とは、`System.Data.OracleClient.dll`アセンブリ。 このデータ プロバイダーを使用するアプリケーションをコンパイルする場合は、 `System.Data.dll` と `System.Data.OracleClient.dll` の両方を参照する必要があります。  
  
 名前空間 `System.Data.OracleClient` をユーザーのアプリケーションにインクルードする方法を次のコード サンプルで示します。  
  
```vb  
Imports System.Data  
Imports System.Data.OracleClient  
```  
  
```csharp  
using System.Data;  
using System.Data.OracleClient;  
```  
  
## <a name="choosing-a-net-framework-data-provider"></a>.NET Framework データ プロバイダーの選択  
 アプリケーションのデザインとデータ ソースに依存 .NET Framework データ プロバイダーの選択はパフォーマンス、機能、およびアプリケーションの整合性を向上させることができます。 次の表では、長所と各 .NET Framework データ プロバイダーの制限事項について説明します。  
  
|プロバイダー|メモ|  
|--------------|-----------|  
|.NET Framework SQL Server 用データ プロバイダー|Microsoft SQL Server を使用する中間層アプリケーションをお勧めします。<br /><br /> Microsoft Database Engine (MSDE) または SQL Server を使用する単層アプリケーションにお勧めします。<br /><br /> 使用、OLE DB provider for SQL Server (SQLOLEDB) と、.NET Framework Data Provider for OLE DB をお勧めします。|  
|.NET Framework Data Provider for OLE DB|SQL Server では、このプロバイダーではなく、.NET Framework Data Provider for SQL Server が推奨されます。<br /><br /> Microsoft Access データベースを使用する単層アプリケーションに推奨されます。 Access データベースを中間層アプリケーションで使用することはお勧めできません。|  
|.NET Framework Data Provider for ODBC|中間層アプリケーションおよび単層アプリケーションで ODBC データ ソースを使用する場合に推奨します。|  
|.NET Framework Oracle 用データ プロバイダー|中間層アプリケーションおよび単層アプリケーションで Oracle データ ソースを使用する場合に推奨します。|  
  
## <a name="entityclient-provider"></a>EntityClient プロバイダー  
 EntityClient プロバイダーは、エンティティ データ モデル (EDM) に基づくデータ アクセスで使用されます。 他の .NET Framework データ プロバイダーとは異なり、データ ソースと直接やり取りしません。 代わりに Entity SQL を使用して、基になるデータ プロバイダーと通信します。 詳細については、次を参照してください。 [Entity Framework 用の EntityClient プロバイダー](./ef/entityclient-provider-for-the-entity-framework.md)します。  
  
## <a name="see-also"></a>関連項目

- [ADO.NET の概要](../../../../docs/framework/data/adonet/ado-net-overview.md)
- [ADO.NET でのデータの取得および変更](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)
- [ADO.NET のマネージド プロバイダーと DataSet デベロッパー センター](https://go.microsoft.com/fwlink/?LinkId=217917)
