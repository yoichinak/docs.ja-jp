---
title: 'How to: Combine Data with LINQ by Using Joins'
ms.date: 07/20/2015
helpviewer_keywords:
- queries [LINQ in Visual Basic], joins
- joins [LINQ in Visual Basic]
- Join clause [LINQ in Visual Basic]
- Group Join clause [Visual Basic]
- joining [LINQ in Visual Basic]
- queries [LINQ in Visual Basic], how-to topics
ms.assetid: 5b00a478-035b-41c6-8918-be1a97728396
ms.openlocfilehash: 7279908c5d262b65f4c4da9cd9b6c1b4117bc402
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345002"
---
# <a name="how-to-combine-data-with-linq-by-using-joins-visual-basic"></a>方法 : LINQ の結合を使用してデータを結合する (Visual Basic)
Visual Basic provides the `Join` and `Group Join` query clauses to enable you to combine the contents of multiple collections based on common values between the collections. These values are known as *key* values. Developers familiar with relational database concepts will recognize the `Join` clause as an INNER JOIN and the `Group Join` clause as, effectively, a LEFT OUTER JOIN.  
  
 The examples in this topic demonstrate a few ways to combine data by using the `Join` and `Group Join` query clauses.  
  
## <a name="create-a-project-and-add-sample-data"></a>Create a Project and Add Sample Data  
  
#### <a name="to-create-a-project-that-contains-sample-data-and-types"></a>To create a project that contains sample data and types  
  
1. To run the samples in this topic, open Visual Studio and add a new Visual Basic Console Application project. Double-click the Module1.vb file created by Visual Basic.  
  
2. The samples in this topic use the `Person` and `Pet` types and data from the following code example. Copy this code into the default `Module1` module created by Visual Basic.  
  
     [!code-vb[VbLINQHowTos#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQHowTos/VB/Module1.vb#1)]  
    [!code-vb[VbLINQHowTos#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQHowTos/VB/Module1.vb#2)]  
  
## <a name="perform-an-inner-join-by-using-the-join-clause"></a>Perform an Inner Join by Using the Join Clause  
 An INNER JOIN combines data from two collections. Items for which the specified key values match are included. Any items from either collection that do not have a matching item in the other collection are excluded.  
  
 In Visual Basic, LINQ provides two options for performing an INNER JOIN: an implicit join and an explicit join.  
  
 An implicit join specifies the collections to be joined in a `From` clause and identifies the matching key fields in a `Where` clause. Visual Basic implicitly joins the two collections based on the specified key fields.  
  
 You can specify an explicit join by using the `Join` clause when you want to be specific about which key fields to use in the join. In this case, a `Where` clause can still be used to filter the query results.  
  
#### <a name="to-perform-an-inner-join-by-using-the-join-clause"></a>To perform an Inner Join by using the Join clause  
  
1. Add the following code to the `Module1` module in your project to see examples of both an implicit and explicit inner join.  
  
     [!code-vb[VbLINQHowTos#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQHowTos/VB/Module1.vb#4)]  
  
## <a name="perform-a-left-outer-join-by-using-the-group-join-clause"></a>Perform a Left Outer Join by Using the Group Join Clause  
 A LEFT OUTER JOIN includes all the items from the left-side collection of the join and only matching values from the right-side collection of the join. Any items from the right-side collection of the join that do not have a matching item in the left-side collection are excluded from the query result.  
  
 The `Group Join` clause performs, in effect, a LEFT OUTER JOIN. The difference between what is typically known as a LEFT OUTER JOIN and what the `Group Join` clause returns is that the `Group Join` clause groups results from the right-side collection of the join for each item in the left-side collection. In a relational database, a LEFT OUTER JOIN returns an ungrouped result in which each item in the query result contains matching items from both collections in the join. In this case, the items from the left-side collection of the join are repeated for each matching item from the right-side collection. You will see what this looks like when you complete the next procedure.  
  
 You can retrieve the results of a `Group Join` query as an ungrouped result by extending your query to return an item for each grouped query result. To accomplish this, you have to ensure that you query on the `DefaultIfEmpty` method of the grouped collection. This ensures that items from the left-side collection of the join are still included in the query result even if they have no matching results from the right-side collection. You can add code to your query to provide a default result value when there is no matching value from the right-side collection of the join.  
  
#### <a name="to-perform-a-left-outer-join-by-using-the-group-join-clause"></a>To perform a Left Outer Join by using the Group Join clause  
  
1. Add the following code to the `Module1` module in your project to see examples of both a grouped left outer join and an ungrouped left outer join.  
  
     [!code-vb[VbLINQHowTos#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQHowTos/VB/Module1.vb#3)]  
  
## <a name="perform-a-join-by-using-a-composite-key"></a>Perform a Join by Using a Composite Key  
 You can use the `And` keyword in a `Join` or `Group Join` clause to identify multiple key fields to use when matching values from the collections being joined. The `And` keyword specifies that all specified key fields must match for items to be joined.  
  
#### <a name="to-perform-a-join-by-using-a-composite-key"></a>To perform a Join by using a composite key  
  
1. Add the following code to the `Module1` module in your project to see examples of a join that uses a composite key.  
  
     [!code-vb[VbLINQHowTos#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQHowTos/VB/Module1.vb#5)]  
  
## <a name="run-the-code"></a>Run the Code  
  
#### <a name="to-add-code-to-run-the-examples"></a>To add code to run the examples  
  
1. Replace the `Sub Main` in the `Module1` module in your project with the following code to run the examples in this topic.  
  
     [!code-vb[VbLINQHowTos#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQHowTos/VB/Module1.vb#6)]  
  
2. Press F5 to run the examples.  
  
## <a name="see-also"></a>関連項目

- [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)
- [Visual Basic における LINQ の概要](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [Join 句](../../../../visual-basic/language-reference/queries/join-clause.md)
- [Group Join 句](../../../../visual-basic/language-reference/queries/group-join-clause.md)
- [From 句](../../../../visual-basic/language-reference/queries/from-clause.md)
- [WHERE 句](../../../../visual-basic/language-reference/queries/where-clause.md)
- [クエリ](../../../../visual-basic/language-reference/queries/index.md)
- [LINQ によるデータ変換 (C#)](../../../../csharp/programming-guide/concepts/linq/data-transformations-with-linq.md)
