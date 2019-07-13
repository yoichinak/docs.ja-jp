---
title: From 句 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.QueryFrom
- vb.QueryFromIn
- vb.QueryFromLet
helpviewer_keywords:
- queries [Visual Basic], From
- From clause [Visual Basic]
- From statement [Visual Basic]
ms.assetid: 83e3665e-68a0-4540-a3a3-3d777a0f95d5
ms.openlocfilehash: 23b277b2eb14ea6722295aab8d7190d78def6f36
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2019
ms.locfileid: "64639633"
---
# <a name="from-clause-visual-basic"></a>From 句 (Visual Basic)
1 つまたは複数の範囲変数とクエリのコレクションを指定します。  
  
## <a name="syntax"></a>構文  
  
```  
From element [ As type ] In collection [ _ ]  
  [, element2 [ As type2 ] In collection2 [, ... ] ]  
```  
  
## <a name="parts"></a>指定項目  
  
|用語|定義|  
|---|---|  
|`element`|必須。 A*範囲変数*コレクションの要素を反復処理するために使用します。 各メンバーを参照する範囲変数が使用される、`collection`を反復処理、クエリと、`collection`します。 列挙可能な型である必要があります。|  
|`type`|省略可能です。 `element` の型。 ない場合は`type`を指定の種類`element`から推論されます`collection`します。|  
|`collection`|必須。 クエリを実行するコレクションを参照します。 列挙可能な型である必要があります。|  
  
## <a name="remarks"></a>Remarks  
 `From`句をクエリし、ソース コレクションから要素を指すために使用されている変数のソース データを識別するために使用します。 これらの変数と呼ばれます*範囲変数*します。 `From`句が必要な場合を除き、クエリ、`Aggregate`句を返しますが、結果の集計をのみこと、クエリを識別するために使用します。 詳細については、次を参照してください。 [Aggregate 句](../../../visual-basic/language-reference/queries/aggregate-clause.md)します。  
  
 複数を指定する`From`参加する複数のコレクションを識別するために、クエリ内の句。 複数のコレクションを指定すると、これらは別々 に反復処理、または関連している場合に参加することができます。 使用してコレクションに暗黙的に参加することができます、`Select`句、またはを使用して明示的に、`Join`または`Group Join`句。 代わりに、指定できます複数の範囲変数およびコレクション 1 つの`From`句は、各関連の範囲変数と、他のユーザーから、コンマで区切られたコレクションを使用します。 次のコード例は、両方の構文のオプションを示しています、`From`句。  
  
 [!code-vb[VbSimpleQuerySamples#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#21)]  
  
 `From`句のスコープに似ていますが、クエリのスコープを定義する、`For`ループします。 そのため、各`element`のクエリ スコープの範囲変数は、一意の名前をいる必要があります。 複数を指定するため、 `From` 、クエリは、後続の句`From`句で範囲変数を参照できます、`From`句、または、以前の範囲変数に参照できます`From`句。 たとえば、次の例では、表示、入れ子になった`From`2 つ目の句では、コレクションは、最初の句の範囲変数のプロパティをに基づいて句。  
  
 [!code-vb[VbSimpleQuerySamples#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#22)]  
  
 各`From`句の後に、クエリを絞り込むの追加のクエリ句の任意の組み合わせをできます。 次の方法でクエリを絞り込むことができます。  
  
- 使用して暗黙的に複数のコレクションを組み合わせる、`From`と`Select`句、またはを使用して明示的に、`Join`または`Group Join`句。  
  
- 使用して、`Where`句をクエリの結果をフィルター処理します。  
  
- 使用して、結果を並べ替える、`Order By`句。  
  
- 使用して同様の結果をグループ化、`Group By`句。  
  
- 使用して、`Aggregate`句全体のクエリの結果を評価する集計関数を識別します。  
  
- 使用して、`Let`句を反復変数の値は、コレクションではなく式によって決定されます。  
  
- 使用して、`Distinct`重複するクエリの結果を無視する句。  
  
- 使用して返される結果の部分を特定、 `Skip`、 `Take`、 `Skip While`、および`Take While`句。  
  
## <a name="example"></a>例  
 次のクエリ式は、`From`範囲変数を宣言する句`cust`各`Customer`オブジェクト、`customers`コレクション。 `Where`句では、範囲変数を使用して、指定されたリージョンからお客様に、出力を制限します。 `For Each`ループは、クエリ結果の各顧客の会社名を表示します。  
  
 [!code-vb[VbSimpleQuerySamples#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#23)]  
  
## <a name="see-also"></a>関連項目

- [クエリ](../../../visual-basic/language-reference/queries/index.md)
- [Visual Basic における LINQ の概要](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [For Each...Next ステートメント](../../../visual-basic/language-reference/statements/for-each-next-statement.md)
- [For...Next ステートメント](../../../visual-basic/language-reference/statements/for-next-statement.md)
- [Select 句](../../../visual-basic/language-reference/queries/select-clause.md)
- [Where 句](../../../visual-basic/language-reference/queries/where-clause.md)
- [Aggregate 句](../../../visual-basic/language-reference/queries/aggregate-clause.md)
- [Distinct 句](../../../visual-basic/language-reference/queries/distinct-clause.md)
- [Join 句](../../../visual-basic/language-reference/queries/join-clause.md)
- [Group Join 句](../../../visual-basic/language-reference/queries/group-join-clause.md)
- [Order By 句](../../../visual-basic/language-reference/queries/order-by-clause.md)
- [Let 句](../../../visual-basic/language-reference/queries/let-clause.md)
- [Skip 句](../../../visual-basic/language-reference/queries/skip-clause.md)
- [Take 句](../../../visual-basic/language-reference/queries/take-clause.md)
- [Skip While 句](../../../visual-basic/language-reference/queries/skip-while-clause.md)
- [Take While 句](../../../visual-basic/language-reference/queries/take-while-clause.md)
