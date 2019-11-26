---
title: Join 句
ms.date: 07/20/2015
f1_keywords:
- vb.QueryJoinIn
- vb.QueryJoin
- vb.QueryJoinOn
helpviewer_keywords:
- queries [Visual Basic], Join
- Join statement [Visual Basic]
- Join clause [Visual Basic]
ms.assetid: 6dd37936-b27c-4e00-98ad-154b23f4de64
ms.openlocfilehash: b0baca9f897a00b3c6c67699629477ff385d6ef7
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/22/2019
ms.locfileid: "74353265"
---
# <a name="join-clause-visual-basic"></a>Join 句 (Visual Basic)

2 つのコレクションを単一のコレクションに結合します。 The join operation is based on matching keys and uses the `Equals` operator.

## <a name="syntax"></a>構文

```vb
Join element In collection _
  [ joinClause _ ]
  [ groupJoinClause ... _ ]
On key1 Equals key2 [ And key3 Equals key4 [... ]
```

## <a name="parts"></a>指定項目

`element` 必須。 The control variable for the collection being joined.

`collection`  
必須です。 The collection to combine with the collection identified on the left side of the `Join` operator. A `Join` clause can be nested in another `Join` clause, or in a `Group Join` clause.

`joinClause`  
省略可能です。 One or more additional `Join` clauses to further refine the query.

`groupJoinClause`  
省略可能です。 One or more additional `Group Join` clauses to further refine the query.

`key1` `Equals` `key2`  
必須です。 Identifies keys for the collections being joined. You must use the `Equals` operator to compare keys from the collections being joined. You can combine join conditions by using the `And` operator to identify multiple keys. `key1` must be from the collection on the left side of the `Join` operator. `key2` must be from the collection on the right side of the `Join` operator.

The keys used in the join condition can be expressions that include more than one item from the collection. However, each key expression can contain only items from its respective collection.

## <a name="remarks"></a>Remarks

The `Join` clause combines two collections based on matching key values from the collections being joined. The resulting collection can contain any combination of values from the collection identified on the left side of the `Join` operator and the collection identified in the `Join` clause. The query will return only results for which the condition specified by the `Equals` operator is met. This is equivalent to an `INNER JOIN` in SQL.

You can use multiple `Join` clauses in a query to join two or more collections into a single collection.

You can perform an implicit join to combine collections without the `Join` clause. To do this, include multiple `In` clauses in your `From` clause and specify a `Where` clause that identifies the keys that you want to use for the join.

You can use the `Group Join` clause to combine collections into a single hierarchical collection. This is like a `LEFT OUTER JOIN` in SQL.

## <a name="example"></a>例

The following code example performs an implicit join to combine a list of customers with their orders.

[!code-vb[VbSimpleQuerySamples#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#13)]

## <a name="example"></a>例

The following code example joins two collections by using the `Join` clause.

[!code-vb[VbSimpleQuerySamples#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples2.vb#12)]

This example will produce output similar to the following:

`winlogon (968), Windows Logon`

`explorer (2424), File Explorer`

`cmd (5136), Command Window`

## <a name="example"></a>例

The following code example joins two collections by using the `Join` clause with two key columns.

[!code-vb[VbSimpleQuerySamples#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples3.vb#17)]

The example will produce output similar to the following:

`winlogon (968), Windows Logon, Priority = 13`

`cmd (700), Command Window, Priority = 8`

`explorer (2424), File Explorer, Priority = 8`

## <a name="see-also"></a>関連項目

- [Visual Basic における LINQ の概要](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [クエリ](../../../visual-basic/language-reference/queries/index.md)
- [Select 句](../../../visual-basic/language-reference/queries/select-clause.md)
- [From 句](../../../visual-basic/language-reference/queries/from-clause.md)
- [Group Join 句](../../../visual-basic/language-reference/queries/group-join-clause.md)
- [WHERE 句](../../../visual-basic/language-reference/queries/where-clause.md)
