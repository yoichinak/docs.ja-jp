---
title: LINQ to SQL クエリ
ms.date: 03/30/2017
ms.assetid: f4897aaa-7f44-4c20-a471-b948c2971aae
ms.openlocfilehash: 534da029664af0babc3dff6226ff095b7222c34d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69915844"
---
# <a name="linq-to-sql-queries"></a>LINQ to SQL クエリ
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] クエリは、[!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] クエリと同じ構文を使用して定義します。 異なる点は、クエリ内で参照されるオブジェクトがデータベース内の要素に割り当てられるという点だけです。 詳細については、「[LINQ クエリの概要 (C#)](../../../../../csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md)」を参照してください。  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] は、作成したクエリを同等の SQL クエリに変換し、それをサーバーに送って処理します。 具体的には、アプリケーションは [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] API を使用してクエリの実行を要求します。 次に、[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] プロバイダーがクエリを SQL テキストに変換し、ADO プロバイダーに実行を委任します。 ADO プロバイダーは、クエリの結果を `DataReader` として返します。 プロバイダー [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]は、ADO の結果をユーザー <xref:System.Linq.IQueryable>オブジェクトのコレクションに変換します。  
  
> [!NOTE]
> 組み込み型 .NET Framework のほとんどのメソッドと演算子は、SQL に直接翻訳されています。 [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] で変換できないものについては、ランタイム例外が発生します。 詳細については、「 [SQL-CLR 型のマッピング](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mapping.md)」を参照してください。  
  
 次の表は、[!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] クエリの項目と [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] クエリの項目の類似点と相違点を示すものです。  
  
|アイテム|LINQ クエリ|[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] クエリ|  
|----------|----------------|----------------------------------------------------------------------|  
|クエリを保持するローカル変数の戻り値の型 (シーケンスを返すクエリの場合)|ジェネリック `IEnumerable`|ジェネリック `IQueryable`|  
|データ ソースの指定|(Visual Basic `From` ) または`from` (C#) 句を使用します。|同|  
|フィルター処理|句を`Where`使用します/ `where` 。|同|  
|グループ化|句を`Group…By`使用します/ `groupby` 。|同|  
|選択 (投影)|句を`Select`使用します/ `select` 。|同|  
|遅延実行と即時実行|「 [LINQ クエリの概要 (C#)」を](../../../../../csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md)参照してください。|同|  
|結合の実装|句を`Join`使用します/ `join` 。|句を使用`Join` /できますが、より効果的に<xref:System.Data.Linq.Mapping.AssociationAttribute>属性を使用します。 `join` 詳細については、「[リレーションシップ間でのクエリ](../../../../../../docs/framework/data/adonet/sql/linq/querying-across-relationships.md)」を参照してください。|  
|リモート実行とローカル実行||詳細については[、「Remote vs」を参照してください。ローカル実行](../../../../../../docs/framework/data/adonet/sql/linq/remote-vs-local-execution.md)。|  
|ストリーミングとキャッシュ クエリ|ローカル メモリ シナリオでは適用なし||  
  
## <a name="see-also"></a>関連項目

- [LINQ クエリの概要 (C#)](../../../../../csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md)
- [LINQ クエリの基本操作](../../../../../csharp/programming-guide/concepts/linq/basic-linq-query-operations.md)
- [LINQ クエリ操作での型の関係](../../../../../csharp/programming-guide/concepts/linq/type-relationships-in-linq-query-operations.md)
- [クエリの概念](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)
