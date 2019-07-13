---
title: ADO.NET でのデータ型のマッピング
ms.date: 03/30/2017
ms.assetid: d4afab94-ada6-4c77-a73c-41f17bae6b5a
ms.openlocfilehash: 4e85db4732da664848cee2ef48f9a880a86fef18
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/14/2019
ms.locfileid: "65583760"
---
# <a name="data-type-mappings-in-adonet"></a>ADO.NET でのデータ型のマッピング
.NET Framework は共通型システムを基にしています。このシステムは実行時の型の宣言、使用、および管理方法を定義するものです。 値型と参照型の両方から構成されており、これらはすべて <xref:System.Object> 基本型から派生します。 データ ソースを操作するときは、データ型が明示的に指定されていない場合はデータ プロバイダーから推論されます。 たとえば、<xref:System.Data.DataSet> オブジェクトは、特定のデータ ソースには依存しません。 `DataSet` 内のデータはデータ ソースから取得され、変更は `DataAdapter` によってデータ ソースに反映されます。 つまり、`DataAdapter`塗りつぶします、<xref:System.Data.DataTable>で、`DataSet`内の列の結果として得られるデータ型のデータ ソースから値を持つ、`DataTable`は .NET Framework データ プロバイダーに固有の型ではなく、.NET Framework 型をデータ ソースへの接続に使用されます。  
  
 同様に、ときに、`DataReader`返しますが、結果の値のデータ ソースからの値は、.NET Framework 型を持つローカル変数に格納されます。 両方の`Fill`の操作、`DataAdapter`と`Get`のメソッド、 `DataReader`、.NET Framework の型が .NET Framework データ プロバイダーから返された値から推論されます。  
  
 返される値の型がわかっている場合は、推論されるデータ型を使用するのではなく、`DataReader` の型指定されたアクセサー メソッドを使用できます。 型指定されたアクセサー メソッドを使用すると、追加の型変換する必要がなくなります特定の .NET Framework 型として値を返すことによってパフォーマンスが向上します。  
  
> [!NOTE]
>  .NET Framework データ プロバイダーのデータ型の null 値がによって表される`DBNull.Value`します。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [SQL Server データ型のマッピング](../../../../docs/framework/data/adonet/sql-server-data-type-mappings.md)  
 推論されたデータ型マッピングおよび <xref:System.Data.SqlClient> のデータ アクセサー メソッドを一覧で示します。  
  
 [OLE DB データ型のマッピング](../../../../docs/framework/data/adonet/ole-db-data-type-mappings.md)  
 推論されたデータ型マッピングおよび <xref:System.Data.OleDb> のデータ アクセサー メソッドを一覧で示します。  
  
 [ODBC データ型のマッピング](../../../../docs/framework/data/adonet/odbc-data-type-mappings.md)  
 推論されたデータ型マッピングおよび <xref:System.Data.Odbc> のデータ アクセサー メソッドを一覧で示します。  
  
 [Oracle データ型のマッピング](../../../../docs/framework/data/adonet/oracle-data-type-mappings.md)  
 推論されたデータ型マッピングおよび <xref:System.Data.OracleClient> のデータ アクセサー メソッドを一覧で示します。  
  
 [浮動小数点数](../../../../docs/framework/data/adonet/floating-point-numbers.md)  
 開発者が浮動小数点数を扱う際の発生頻度の高い問題について説明します。  
  
## <a name="see-also"></a>関連項目

- [SQL Server データ型と ADO.NET](../../../../docs/framework/data/adonet/sql/sql-server-data-types.md)
- [パラメーターおよびパラメーター データ型の構成](../../../../docs/framework/data/adonet/configuring-parameters-and-parameter-data-types.md)
- [データベース スキーマ情報の取得](../../../../docs/framework/data/adonet/retrieving-database-schema-information.md)
- [共通型システム](../../../../docs/standard/base-types/common-type-system.md)
- [型の変換](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/t8s7t9bf(v=vs.90))
- [ADO.NET のマネージド プロバイダーと DataSet デベロッパー センター](https://go.microsoft.com/fwlink/?LinkId=217917)
