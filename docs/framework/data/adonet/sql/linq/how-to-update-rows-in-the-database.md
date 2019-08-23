---
title: '方法: データベースの行を更新する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a2b5c90f-6cc3-4128-bfab-1db488d5af26
ms.openlocfilehash: 2819cd5d2533e8e289735c3df2b39df952968e66
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69938733"
---
# <a name="how-to-update-rows-in-the-database"></a>方法: データベースの行を更新する
データベース内の行を更新するには、 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Table%601>コレクションに関連付けられているオブジェクトのメンバー値を変更してから、変更をデータベースに送信します。 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]では、変更内容が適切`UPDATE`な SQL コマンドに変換されます。  
  
> [!NOTE]
> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] の `Insert`、`Update`、および `Delete` の既定のデータベース操作メソッドはオーバーライドできます。 詳細については、「[挿入、更新、および削除の操作をカスタマイズ](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md)する」を参照してください。  
>   
>  Visual Studio を使用する開発者は、オブジェクトリレーショナルデザイナーを使用して、同じ目的でストアドプロシージャを開発できます。  
  
 以下の手順では、有効な <xref:System.Data.Linq.DataContext> で Northwind データベースに接続されるものと想定しています。 詳細については、「[方法 :データベース](../../../../../../docs/framework/data/adonet/sql/linq/how-to-connect-to-a-database.md)に接続します。  
  
### <a name="to-update-a-row-in-the-database"></a>データベースの行を更新するには  
  
1. データベースで更新する行をクエリします。  
  
2. 結果として得られた [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] オブジェクトのメンバー値に、必要な変更を加えます。  
  
3. データベースに変更内容を送信します。  
  
## <a name="example"></a>例  
 次の例では、データベースの注文 #11000 をクエリし、結果として得られた `ShipName` オブジェクトの `ShipVia` と `Order` の値を変更します。 次に、これらのメンバー値の変更内容を、`ShipName` 列と `ShipVia` 列に対する変更としてデータベースに送信します。  
  
 [!code-csharp[System.Data.Linq.Table#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.table/cs/program.cs#2)]
 [!code-vb[System.Data.Linq.Table#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.table/vb/module1.vb#2)]  
  
## <a name="see-also"></a>関連項目

- [方法: 変更の競合を管理する](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)
- [方法: 更新、挿入、および削除を実行するストアド プロシージャを割り当てる (O/R デザイナー)](/visualstudio/data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer)
- [データの変更と変更の送信](../../../../../../docs/framework/data/adonet/sql/linq/making-and-submitting-data-changes.md)
