---
title: SQL Server データ型と ADO.NET
ms.date: 03/30/2017
ms.assetid: 81b43550-23e8-43bb-b460-7eb8ac825c33
ms.openlocfilehash: 9e81e54f223d35a3db9c943edf6f9f9b24110faa
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59326308"
---
# <a name="sql-server-data-types-and-adonet"></a>SQL Server データ型と ADO.NET
SQL Server と .NET Framework は異なる型システムに基づいているので、両者間でデータ損失が発生する可能性があります。 データの整合性を維持するために、.NET Framework Data Provider for SQL Server (<xref:System.Data.SqlClient>) では、SQL Server データを処理するための型指定されたアクセサー メソッドが提供されています。 <xref:System.Data.SqlDbType> クラスの列挙値を使用して、<xref:System.Data.SqlClient.SqlParameter> データ型を指定できます。  
  
 詳細については、SQL Server と .NET Framework データ型間のデータ型マッピングを説明した表を参照してください。 [SQL Server データ型のマッピング](../../../../../docs/framework/data/adonet/sql-server-data-type-mappings.md)します。  
  
 SQL Server 2008 では、業務上のニーズに対応して、日時データ、構造化データ、半構造化データ、および非構造化データを扱うための新しいデータ型が導入されました。 新しいデータ型は、SQL Server 2008 オンライン ブックで説明されています。  
  
 アプリケーションで使用可能な SQL Server のデータ型は、使用する SQL Server のバージョンによって異なります。 詳細については、次の表にある各バージョンの SQL Server オンライン ブックを参照してください。  
  
 **SQL Server オンライン ブック**  
  
1. [データ型 (データベース エンジン)](https://go.microsoft.com/fwlink/?LinkID=107468)  
  
## <a name="in-this-section"></a>このセクションの内容  
 [SqlTypes と DataSet](../../../../../docs/framework/data/adonet/sql/sqltypes-and-the-dataset.md)  
 `SqlTypes` 内の `DataSet` に対する型のサポートについて説明します。  
  
 [null 値の処理](../../../../../docs/framework/data/adonet/sql/handling-null-values.md)  
 null 値と 3 値ロジックの使用例を示します。  
  
 [GUID と uniqueidentifier 値の比較](../../../../../docs/framework/data/adonet/sql/comparing-guid-and-uniqueidentifier-values.md)  
 SQL Server と .NET Framework での GUID および uniqueidentifier 値の使用例を示します。  
  
 [日付と時刻のデータ](../../../../../docs/framework/data/adonet/sql/date-and-time-data.md)  
 SQL Server 2008 で導入された新しい日付と時刻のデータ型の使用方法について説明します。  
  
 [大きな UDT](../../../../../docs/framework/data/adonet/sql/large-udts.md)  
 SQL Server 2008 で導入された大きな値の UDT からデータを取り出す方法の例を示します。  
  
 [SQL Server における XML データ](../../../../../docs/framework/data/adonet/sql/xml-data-in-sql-server.md)  
 SQL Server から取得した XML データを使用する方法について説明します。  
  
## <a name="reference"></a>参照  
 <xref:System.Data.DataSet>  
 `DataSet` クラスおよびそのすべてのメンバーについて説明します。  
  
 <xref:System.Data.SqlTypes>  
 `SqlTypes` 名前空間およびそのすべてのメンバーについて説明します。  
  
 <xref:System.Data.SqlDbType>  
 `SqlDbType` 列挙型およびそのすべてのメンバーについて説明します。  
  
 <xref:System.Data.DbType>  
 `DbType` 列挙型およびそのすべてのメンバーについて説明します。  
  
## <a name="see-also"></a>関連項目

- [SQL Server データ型のマッピング](../../../../../docs/framework/data/adonet/sql-server-data-type-mappings.md)
- [パラメーターおよびパラメーター データ型の構成](../../../../../docs/framework/data/adonet/configuring-parameters-and-parameter-data-types.md)
- [テーブル値パラメーター](../../../../../docs/framework/data/adonet/sql/table-valued-parameters.md)
- [SQL Server のバイナリ データと大きな値のデータ](../../../../../docs/framework/data/adonet/sql/sql-server-binary-and-large-value-data.md)
- [ADO.NET のマネージド プロバイダーと DataSet デベロッパー センター](https://go.microsoft.com/fwlink/?LinkId=217917)
