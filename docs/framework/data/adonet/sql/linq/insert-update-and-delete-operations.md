---
title: 挿入、更新、および削除の各操作
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 26a43a4f-83c9-4732-806d-bb23aad0ff6b
ms.openlocfilehash: 7dd2eb64a9320d88c7bc3b5feb6578d70f5910b7
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/23/2019
ms.locfileid: "54503665"
---
# <a name="insert-update-and-delete-operations"></a>挿入、更新、および削除の各操作
オブジェクト モデルに対してオブジェクトの追加、変更、および削除を行うには、`Insert` で `Update`、`Delete`、および [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] の各操作を実行します。 既定では、[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] によって SQL に対する操作が変換され、変更内容がデータベースに送信されます。  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 操作して、オブジェクトに加えた変更の保持に最大限の柔軟性を提供します。 クエリによって取得するか新規に作成することによりエンティティ オブジェクトが使用可能になった後で、通常のオブジェクトと同じようにそれらのオブジェクトをアプリケーションで変更できます。 つまり、その値を変更することができます、自分のコレクションに追加することができます、コレクションから削除することができます。 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] では変更履歴が保持されるため、<xref:System.Data.Linq.DataContext.SubmitChanges%2A> を呼び出すと、変更内容をデータベースに送信できます。  
  
> [!NOTE]
>  [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] は連鎖削除操作をサポートせず、認識もしません。 設定する必要がありますこれに対する制約を持つテーブルの行を削除する場合、`ON DELETE CASCADE`データベース内の外部キー制約でルールまたは独自のコードを使用して、まず親オブジェクトが削除されないようにする子オブジェクトを削除します。 それ以外の場合は、例外がスローされます。 詳細については、「[方法 :データベースから行を削除](../../../../../../docs/framework/data/adonet/sql/linq/how-to-delete-rows-from-the-database.md)します。  
  
 次の例では、Northwind サンプル データベースの `Customer` クラスと `Order` クラスを使用します。 簡潔にするため、ここではクラス定義を省いています。  
  
 [!code-csharp[DLinqCRUDOps#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCRUDOps/cs/Program.cs#1)]
 [!code-vb[DLinqCRUDOps#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCRUDOps/vb/Module1.vb#1)]  
  
 <xref:System.Data.Linq.DataContext.SubmitChanges%2A> を呼び出すと、変更内容をデータベースに送信する SQL コマンドが [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] によって自動的に生成され、実行されます。  
  
> [!NOTE]
>  独自に作成したロジック (通常はストアド プロシージャ) を使用して、この動作をオーバーライドできます。 詳細については、[開発者でオーバーライドする既定の動作の責任](../../../../../../docs/framework/data/adonet/sql/linq/responsibilities-of-the-developer-in-overriding-default-behavior.md)を参照してください。  
>   
>  Visual Studio を使用して開発者が使用できる、[!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)]この目的のストアド プロシージャを開発します。  
  
## <a name="see-also"></a>関連項目
- [サンプル データベースのダウンロード](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)
- [挿入、更新、および削除の各操作のカスタマイズ](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md)
