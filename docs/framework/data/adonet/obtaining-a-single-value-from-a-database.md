---
title: データベースからの単一の値の取得
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b38526cd-a62a-48cb-822a-e91dfa68e02d
ms.openlocfilehash: 5eb81fd2a64f06f1252f71e251e58df568e7407c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59120680"
---
# <a name="obtaining-a-single-value-from-a-database"></a>データベースからの単一の値の取得
テーブルやデータ ストリームの形式ではなく、単に 1 つの値をデータベース情報として返すことが必要な場合があります。 たとえば、数などの集約関数の結果を返すようにする可能性があります (\*)、SUM(Price)、または AVG(Quantity) します。 **コマンド**オブジェクトを使用して 1 つの値を返す機能を提供する、 **ExecuteScalar**メソッド。 **ExecuteScalar**メソッドはスカラー値、結果セットの最初の行の最初の列の値として返します。  
  
 <xref:System.Data.SqlClient.SqlCommand> を使用して新しい値をデータベースに挿入するコード サンプルを次に示します。 挿入したレコードの ID 列の値を取得するために、<xref:System.Data.SqlClient.SqlCommand.ExecuteScalar%2A> メソッドが使用されています。  
  
 [!code-csharp[DataWorks SqlCommand.ExecuteScalar#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlCommand.ExecuteScalar/CS/source.cs#1)]
 [!code-vb[DataWorks SqlCommand.ExecuteScalar#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlCommand.ExecuteScalar/VB/source.vb#1)]  
  
## <a name="see-also"></a>関連項目

- [コマンドおよびパラメーター](../../../../docs/framework/data/adonet/commands-and-parameters.md)
- [コマンドの実行](../../../../docs/framework/data/adonet/executing-a-command.md)
- [DbConnection、DbCommand、および DbException](../../../../docs/framework/data/adonet/dbconnection-dbcommand-and-dbexception.md)
- [ADO.NET のマネージド プロバイダーと DataSet デベロッパー センター](https://go.microsoft.com/fwlink/?LinkId=217917)
