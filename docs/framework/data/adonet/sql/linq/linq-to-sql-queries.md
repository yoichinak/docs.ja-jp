---
title: LINQ to SQL クエリ
ms.date: 03/30/2017
ms.assetid: f4897aaa-7f44-4c20-a471-b948c2971aae
ms.openlocfilehash: 1390ca36ce9071a16ef21e32dfd7f7a6211644f2
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/23/2019
ms.locfileid: "54689667"
---
# <a name="linq-to-sql-queries"></a>LINQ to SQL クエリ
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] クエリは、[!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] クエリと同じ構文を使用して定義します。 異なる点は、クエリ内で参照されるオブジェクトがデータベース内の要素に割り当てられるという点だけです。 詳細については、「[LINQ クエリの概要 (C#)](~/docs/csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md)」を参照してください。  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] は、作成したクエリを同等の SQL クエリに変換し、それをサーバーに送って処理します。 具体的には、アプリケーションは [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] API を使用してクエリの実行を要求します。 次に、[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] プロバイダーがクエリを SQL テキストに変換し、ADO プロバイダーに実行を委任します。 ADO プロバイダーは、クエリの結果を `DataReader` として返します。 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]プロバイダーに変換する ADO の結果、<xref:System.Linq.IQueryable>ユーザー オブジェクトのコレクション。  
  
> [!NOTE]
>  [!INCLUDE[dnprdnshort](../../../../../../includes/dnprdnshort-md.md)] 組み込み型のほとんどのメソッドと演算子には、SQL に直接対応する変換が用意されています。 [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] で変換できないものについては、ランタイム例外が発生します。 詳細については、[SQL-CLR 型マッピング](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mapping.md)を参照してください。  
  
 次の表は、[!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] クエリの項目と [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] クエリの項目の類似点と相違点を示すものです。  
  
|アイテム|LINQ クエリ|[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] クエリ|  
|----------|----------------|----------------------------------------------------------------------|  
|クエリを保持するローカル変数の戻り値の型 (シーケンスを返すクエリの場合)|ジェネリック `IEnumerable`|ジェネリック `IQueryable`|  
|データ ソースの指定|使用して、 `From` (Visual Basic) または`from`(C#) 句|同|  
|フィルター処理|使用して、 `Where` / `where`句|同|  
|グループ化|使用して、 `Group…By` / `groupby`句|同|  
|選択 (投影)|使用して、 `Select` / `select`句|同|  
|遅延実行と即時実行|参照してください[LINQ クエリの概要 (C#)](~/docs/csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md)|同|  
|結合の実装|使用して、 `Join` / `join`句|使用できる、 `Join` / `join`句がより効果的に使用して、<xref:System.Data.Linq.Mapping.AssociationAttribute>属性。 詳細については、[リレーションシップ間でクエリを実行する](../../../../../../docs/framework/data/adonet/sql/linq/querying-across-relationships.md)を参照してください。|  
|リモート実行とローカル実行||詳細については、[リモート実行とを参照してください。ローカル実行](../../../../../../docs/framework/data/adonet/sql/linq/remote-vs-local-execution.md)します。|  
|ストリーミングとキャッシュ クエリ|ローカル メモリ シナリオでは適用なし||  
  
## <a name="see-also"></a>関連項目
- [LINQ クエリの概要 (C#)](~/docs/csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md)
- [LINQ クエリの基本操作](~/docs/csharp/programming-guide/concepts/linq/basic-linq-query-operations.md)
- [LINQ クエリ操作での型の関係](~/docs/csharp/programming-guide/concepts/linq/type-relationships-in-linq-query-operations.md)
- [クエリの概念](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)
