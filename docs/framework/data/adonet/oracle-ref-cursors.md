---
title: Oracle REF CURSOR
ms.date: 03/30/2017
ms.assetid: c6b25b8b-0bdd-41b2-9c7c-661f070c2247
ms.openlocfilehash: 0a98bfd401aaabfb754c422cc753bc5092f9f76c
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2019
ms.locfileid: "64633336"
---
# <a name="oracle-ref-cursors"></a>Oracle REF CURSOR
.NET Framework Data Provider for Oracle のサポート、Oracle **REF CURSOR**データ型。 データ プロバイダーを使用して Oracle REF CURSOR を操作するときは、次の動作を考慮する必要があります。  
  
> [!NOTE]
>  動作の中には、Microsoft OLE DB Provider for Oracle (MSDAORA) の動作と異なるものがあります。  
  
- パフォーマンス上の理由から、Data Provider for Oracle は自動的にバインドしない**REF CURSOR**データ型は、MSDAORA よう、明示的に指定する場合を除き、します。  
  
- データ プロバイダーでは、REF CURSOR パラメーターの指定に使用する {resultset} エスケープのような、ODBC エスケープ シーケンスはサポートされていません。  
  
- REF Cursor を返すストアド プロシージャを実行するにパラメーターを定義する必要があります、<xref:System.Data.OracleClient.OracleParameterCollection>で、<xref:System.Data.OracleClient.OracleType>の**カーソル**と<xref:System.Data.OracleClient.OracleParameter.Direction%2A>の**出力**します。 データ プロバイダーでは、REF CURSOR のバインドは出力パラメーターとしてのみサポートされています。 プロバイダーは、入力パラメーターとしての REF CURSOR はサポートしていません。  
  
- パラメーター値からの <xref:System.Data.OracleClient.OracleDataReader> の取得はサポートされていません。 値は、コマンドを実行すると <xref:System.DBNull> 型になります。  
  
- 唯一**CommandBehavior**の REF Cursor で動作する列挙値 (を呼び出すときに、たとえば、 <xref:System.Data.OracleClient.OracleCommand.ExecuteReader%2A>) は**CloseConnection**; 他のすべてのユーザーは無視されます。  
  
- 内の REF Cursor の順序、 **OracleDataReader**内のパラメーターの順序によっては、 **OracleParameterCollection**します。 <xref:System.Data.OracleClient.OracleParameter.ParameterName%2A> プロパティは無視されます。  
  
- PL/SQL**テーブル**データ型はサポートされていません。 ただし、REF CURSOR は、さらに効果的です。 使用する場合、**テーブル**MSDAORA で OLE DB .NET データ プロバイダーを使用して、データ型します。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [REF CURSOR の例](../../../../docs/framework/data/adonet/ref-cursor-examples.md)  
 次の 3 つの例を使って REF CURSOR の使い方について説明します。  
  
 [OracleDataReader の REF CURSOR パラメーター](../../../../docs/framework/data/adonet/ref-cursor-parameters-in-an-oracledatareader.md)  
 REF CURSOR パラメーターを返しして値を読み取る PL/SQL ストアド プロシージャを実行する方法を示します、 **OracleDataReader**します。  
  
 [OracleDataReader を使用した複数の REF CURSOR からのデータの取得](../../../../docs/framework/data/adonet/retrieving-data-from-multiple-ref-cursors.md)  
 2 つの REF CURSOR パラメーターを返しを使用して値を読み取る PL/SQL ストアド プロシージャを実行する方法を示します、 **OracleDataReader**します。  
  
 [1 つまたは複数の REF CURSOR を使用した DataSet の値の設定](../../../../docs/framework/data/adonet/filling-a-dataset-using-one-or-more-ref-cursors.md)  
 2 つの REF CURSOR パラメーターを返し、返された行を <xref:System.Data.DataSet> に入力する、PL/SQL ストアド プロシージャを実行する方法について説明します。  
  
## <a name="see-also"></a>関連項目

- [Oracle および ADO.NET](../../../../docs/framework/data/adonet/oracle-and-adonet.md)
- [ADO.NET のマネージド プロバイダーと DataSet デベロッパー センター](https://go.microsoft.com/fwlink/?LinkId=217917)
