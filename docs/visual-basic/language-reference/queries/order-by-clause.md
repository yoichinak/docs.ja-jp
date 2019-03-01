---
title: Order By 句 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.QueryOrderBy
- vb.QueryAscending
- vb.QueryDescending
helpviewer_keywords:
- queries [Visual Basic], Order By
- Order By clause [Visual Basic]
- Order By statement [Visual Basic]
ms.assetid: fa911282-6b81-44c7-acfa-46b5bb93df75
ms.openlocfilehash: 1d9055796687f828cc173a78feb9918cbf70bbd8
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/28/2019
ms.locfileid: "56976370"
---
# <a name="order-by-clause-visual-basic"></a>Order By 句 (Visual Basic)
クエリ結果の並べ替え順序を指定します。  
  
## <a name="syntax"></a>構文  
  
```  
Order By orderExp1 [ Ascending | Descending ] [, orderExp2 [...] ]  
```  
  
## <a name="parts"></a>指定項目  
 `orderExp1`  
 必須。 1 つまたは複数のフィールド現在のクエリ結果からの返された値を並べ替える方法を識別します。 フィールド名は、コンマ (,) で区切る必要があります。 昇順または降順を使用して、ソート済みとしては、各フィールドを識別できます、`Ascending`または`Descending`キーワード。 ない場合は`Ascending`または`Descending`キーワードを指定すると、既定の並べ替え順序は昇順です。 並べ替え順序のフィールドには、左から右への優先順位が与えられます。  
  
## <a name="remarks"></a>Remarks  
 使用することができます、`Order By`句、クエリの結果を並べ替えます。 `Order By`句では、現在のスコープの範囲変数に基づく結果を並べ替えることができますのみです。 たとえば、`Select`句にそのスコープの新しい反復変数をクエリ式での新しいスコープが導入されています。 範囲変数を定義する前に、`Select`クエリ句は使用後に、`Select`句。 そのため、記載されていないフィールドで、結果の順序をする場合、`Select`句に配置する必要がある、`Order By`句の前に、`Select`句。 1 つのときにこれを行う必要があるには例が、結果の一部として返されないフィールドで、クエリの並べ替えを行うときにします。  
  
 昇順と降順の実装によって、フィールドが特定の順序、<xref:System.IComparable>フィールドのデータ型のインターフェイス。 データ型が実装していない場合、<xref:System.IComparable>インターフェイス、並べ替え順序は無視されます。  
  
## <a name="example"></a>例  
 次のクエリ式は、`From`範囲変数を宣言する句`book`の`books`コレクション。 `Order By`句で昇順に並べ替えます (既定値) の価格をクエリの結果を並べ替えます。 同じ価格ブックは、タイトルの昇順で並べ替えられます。 `Select`句を選択、`Title`と`Price`プロパティとして、クエリによって返される値。  
  
 [!code-vb[VbSimpleQuerySamples#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#24)]  
  
## <a name="example"></a>例  
 次のクエリ式は、`Order By`降順で価格をクエリ結果を並べ替えるための句。 同じ価格ブックは、タイトルの昇順で並べ替えられます。  
  
 [!code-vb[VbSimpleQuerySamples#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#25)]  
  
## <a name="example"></a>例  
 次のクエリ式は、`Select`句を書籍のタイトルを選択し、価格、発行日、作成します。 設定し、 `Title`、 `Price`、`PublishDate`と`Author`新しいスコープの範囲変数のフィールド。 `Order By`句の作成者の名前、書籍のタイトル、および価格によって新しい範囲変数の順序。 各列は、既定の順序 (昇順) で並べ替えられます。  
  
 [!code-vb[VbSimpleQuerySamples#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#26)]  
  
## <a name="see-also"></a>関連項目
- [Visual Basic における LINQ の概要](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [クエリ](../../../visual-basic/language-reference/queries/index.md)
- [Select 句](../../../visual-basic/language-reference/queries/select-clause.md)
- [From 句](../../../visual-basic/language-reference/queries/from-clause.md)
