---
title: データベースからの単一の値の取得
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b38526cd-a62a-48cb-822a-e91dfa68e02d
ms.openlocfilehash: fb43d21546a0e98e87aab23db9213309b62320b9
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/07/2019
ms.locfileid: "70794752"
---
# <a name="obtaining-a-single-value-from-a-database"></a>データベースからの単一の値の取得
テーブルやデータ ストリームの形式ではなく、単に 1 つの値をデータベース情報として返すことが必要な場合があります。 たとえば、COUNT (\*)、SUM (Price)、AVG (Quantity) などの集計関数の結果を返すことができます。 **Command**オブジェクトは、 **ExecuteScalar**メソッドを使用して単一の値を返す機能を提供します。 **ExecuteScalar**メソッドは、結果セットの最初の行の最初の列の値として、スカラー値としてを返します。  
  
 <xref:System.Data.SqlClient.SqlCommand> を使用して新しい値をデータベースに挿入するコード サンプルを次に示します。 挿入したレコードの ID 列の値を取得するために、<xref:System.Data.SqlClient.SqlCommand.ExecuteScalar%2A> メソッドが使用されています。  
  
 [!code-csharp[DataWorks SqlCommand.ExecuteScalar#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlCommand.ExecuteScalar/CS/source.cs#1)]
 [!code-vb[DataWorks SqlCommand.ExecuteScalar#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlCommand.ExecuteScalar/VB/source.vb#1)]  
  
## <a name="see-also"></a>関連項目

- [コマンドおよびパラメーター](commands-and-parameters.md)
- [コマンドの実行](executing-a-command.md)
- [DbConnection、DbCommand、および DbException](dbconnection-dbcommand-and-dbexception.md)
- [ADO.NET の概要](ado-net-overview.md)
