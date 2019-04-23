---
title: ORDER BY (Entity SQL)
ms.date: 03/30/2017
ms.assetid: c0b61572-ecee-41eb-9d7f-74132ec8a26c
ms.openlocfilehash: 4cf65637603fd6c20a33b1ae6ecd8b6ded36a246
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59328479"
---
# <a name="order-by-entity-sql"></a>ORDER BY (Entity SQL)
SELECT ステートメントで返されるオブジェクトで使用される並べ替え順を指定します。  
  
## <a name="syntax"></a>構文  
  
```  
[ ORDER BY   
   {  
      order_by_expression [SKIP n] [LIMIT n]  
      [ COLLATE collation_name ]  
      [ ASC | DESC ]  
   }  
   [ ,…n ]   
]  
```  
  
## <a name="arguments"></a>引数  
 `order_by_expression`  
 並べ替えるプロパティを指定する有効なクエリ式。 並べ替えのキーとなる式を複数指定できます。 ORDER BY 句内に記述するキー式の並び順によって、並べ替えられた結果セットの構成が決まります。  
  
 COLLATE {collation_name}  
 ORDER BY 操作が `collation_name`で指定された照合順序に従って実行されることを指定します。 COLLATE は文字列式にのみ適用できます。  
  
 ASC  
 指定したプロパティの値が昇順、つまり小さい値から大きい値へと並べ替えられます。 既定値です。  
  
 DESC  
 指定したプロパティの値が降順、つまり大きい値から小さい値へと並べ替えられます。  
  
 LIMIT `n`  
 最初の `n` 個の項目のみが選択されます。  
  
 SKIP `n`  
 最初の `n` 個の項目をスキップします。  
  
## <a name="remarks"></a>Remarks  
 ORDER BY 句は、SELECT 句の結果に論理的に適用されます。 ORDER BY 句では、別名を使用して選択リストの項目を参照できます。 ORDER BY 句は、現在スコープ内にあるその他の変数も参照できます。 ただし、SELECT 句が DISTINCT 修飾子で指定されている場合は、ORDER BY 句は SELECT 句の別名のみを参照できます。  
  
 `SELECT c AS c1 FROM cs AS c ORDER BY c1.e1, c.e2`  
  
 ORDER BY 句内の各式は、順序付けられた不等号 (より小さい、より大きいなど) について比較できる型として評価される必要があります。 通常、これらの型は数値、文字列、日付などのスカラー プリミティブです。 比較できる型の RowType は順序も比較できます。  
  
 順序付けされたセットで、最上位の投影を除きコードが反復処理を行う場合、出力でその順序が維持されることは保証されません。  
  
```  
-- In the following sample, order is guaranteed to be preserved:  
SELECT C1.FirstName, C1.LastName  
        FROM AdventureWorks.Contact as C1  
        ORDER BY C1.LastName  
```  
  
```  
-- In the following query ordering of the nested query is ignored.  
SELECT C2.FirstName, C2.LastName  
    FROM (SELECT C1.FirstName, C1.LastName  
        FROM AdventureWorks.Contact as C1  
        ORDER BY C1.LastName) as C2  
```  
  
 UNION、UNION ALL、EXCEPT、または INTERSECT 操作を順序付けするには、次のパターンを使用してください。  
  
```  
SELECT ...  
FROM ( UNION/EXCEPT/INTERSECT operation )  
ORDER BY ...  
```  
  
## <a name="restricted-keywords"></a>制限付きのキーワード  
 次のキーワードは `ORDER BY` 句で使用する場合には、引用符で囲む必要があります。  
  
-   CROSS  
  
-   FULL  
  
-   KEY  
  
-   左方向 (←) キー  
  
-   ORDER  
  
-   OUTER  
  
-   右方向 (→) キー  
  
-   ROW  
  
-   VALUE  
  
## <a name="ordering-nested-queries"></a>入れ子になったクエリの順序  
 Entity Framework では、入れ子になった式をクエリ内の任意の場所に配置できるため、入れ子になったクエリの順序は維持されません。  
  
```  
-- The following query will order the results by the last name.  
SELECT C1.FirstName, C1.LastName  
        FROM AdventureWorks.Contact as C1  
        ORDER BY C1.LastName  
```  
  
```  
-- In the following query, ordering of the nested query is ignored.  
SELECT C2.FirstName, C2.LastName  
    FROM (SELECT C1.FirstName, C1.LastName  
        FROM AdventureWorks.Contact as C1  
        ORDER BY C1.LastName) as C2  
```  
  
## <a name="example"></a>例  
 次の [!INCLUDE[esql](../../../../../../includes/esql-md.md)] クエリでは、SELECT ステートメントで返されたオブジェクトの並べ替え順序の指定に ORDER BY 演算子を使用します。 このクエリは、AdventureWorks Sales Model に基づいています。 このクエリをコンパイルして実行するには、次の手順を実行します。  
  
1. 」の手順に従って[方法。StructuralType 結果を返すクエリを実行](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md)します。  
  
2. 次のクエリを引数として `ExecuteStructuralTypeQuery` メソッドに渡します。  
  
 [!code-csharp[DP EntityServices Concepts 2#ORDERBY](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#orderby)]  
  
## <a name="see-also"></a>関連項目

- [クエリ式](../../../../../../docs/framework/data/adonet/ef/language-reference/query-expressions-entity-sql.md)
- [Entity SQL リファレンス](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
- [SKIP](../../../../../../docs/framework/data/adonet/ef/language-reference/skip-entity-sql.md)
- [LIMIT](../../../../../../docs/framework/data/adonet/ef/language-reference/limit-entity-sql.md)
- [TOP](../../../../../../docs/framework/data/adonet/ef/language-reference/top-entity-sql.md)
