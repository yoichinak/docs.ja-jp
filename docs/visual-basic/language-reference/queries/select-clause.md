---
title: Select 句 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.QuerySelect
helpviewer_keywords:
- Select statement [Visual Basic]
- Select clause [Visual Basic]
- queries [Visual Basic], Select
ms.assetid: 27a3f61c-5960-4692-9b91-4d0c4b6178fe
ms.openlocfilehash: 367d810c2358963bfe2f092a390443eccdc66941
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "58814446"
---
# <a name="select-clause-visual-basic"></a>Select 句 (Visual Basic)
クエリの結果を定義します。  
  
## <a name="syntax"></a>構文  
  
```  
Select [ var1 = ] fieldName1 [, [ var2 = ] fieldName2 [...] ]  
```  
  
## <a name="parts"></a>指定項目  
 `var1`  
 省略可能です。 列の式の結果を参照に使用できるエイリアスです。  
  
 `fieldName1`  
 必須。 クエリ結果を返すフィールドの名前。  
  
## <a name="remarks"></a>Remarks  
 使用することができます、`Select`クエリから返される結果を定義する句。 これにより、クエリによって作成される新しい匿名型のメンバーを定義するか、またはクエリによって返される名前付きの型のメンバーを対象にすることができます。 `Select`句はクエリの必要はありません。 ない場合は`Select`句を指定すると、クエリは、現在のスコープで特定された範囲変数のすべてのメンバーに基づいて型を返します。 詳細については、「[匿名型](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)」を参照してください。 クエリでは、名前付きの型を作成するときに型の結果が返されます。<xref:System.Collections.Generic.IEnumerable%601>場所`T`は、作成した型です。  
  
 `Select`句は、現在のスコープ内の変数を参照できます。 識別される範囲変数が含まれます、`From`句 (または`From`句)。 エイリアスによって作成された新しい変数も含まれています、 `Aggregate`、 `Let`、 `Group By`、または`Group Join`句、または以前から変数`Select`クエリ式の句。 `Select`句は、静的な値を含めることもできます。 次のコード例は、クエリ式を示しますなど、`Select`句は、4 つのメンバーを持つ新しい匿名型として、クエリの結果を定義します: `ProductName`、 `Price`、 `Discount`、および`DiscountedPrice`します。 `ProductName`と`Price`メンバー値で定義されている製品の範囲変数から取得されます、`From`句。 `DiscountedPrice`でメンバーの値が計算されます、`Let`句。 `Discount`メンバーが静的な値。  
  
 [!code-vb[VbSimpleQuerySamples#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#27)]  
  
 `Select`句には、以降のクエリ句の範囲変数の新しいセットが導入されて、前の範囲変数は、不要になったスコープとします。 最後の`Select`句はクエリ式では、クエリの戻り値を決定します。 たとえば、次のクエリは、名前と注文合計が 500 を超えるすべての顧客注文 ID、会社返します。 最初の`Select`句の範囲変数を識別する、`Where`句と、2 つ目`Select`句。 2 番目の`Select`句は、新しい匿名型として、クエリによって返される値を識別します。  
  
 [!code-vb[VbSimpleQuerySamples#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#28)]  
  
 場合、`Select`句を返す 1 つの項目を識別する、クエリ式は、その 1 つの項目の種類のコレクションを返します。 場合、`Select`句を返す複数の項目を識別する、クエリ式は、選択したアイテムに基づいて、新しい匿名型のコレクションを返します。 たとえば、次の 2 つのクエリがに基づいて 2 つの異なる型のコレクションを返す、`Select`句。 最初のクエリでは、会社名の文字列としてのコレクションを返します。 2 番目のクエリのコレクションを返します`Customer`会社名とアドレス情報を含むオブジェクト。  
  
 [!code-vb[VbSimpleQuerySamples#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#29)]  
  
## <a name="example"></a>例  
 次のクエリ式は、`From`範囲変数を宣言する句`cust`の`customers`コレクション。 `Select`句は、顧客名と ID 値を選択し、設定します、`CompanyName`と`CustomerID`新しい範囲変数の列。 `For Each`ステートメント返された各オブジェクトに対してループ処理し、表示、`CompanyName`と`CustomerID`各レコードの列。  
  
 [!code-vb[VbSimpleQuerySamples#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#30)]  
  
## <a name="see-also"></a>関連項目

- [Visual Basic における LINQ の概要](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [クエリ](../../../visual-basic/language-reference/queries/index.md)
- [From 句](../../../visual-basic/language-reference/queries/from-clause.md)
- [Where 句](../../../visual-basic/language-reference/queries/where-clause.md)
- [Order By 句](../../../visual-basic/language-reference/queries/order-by-clause.md)
- [匿名型](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)
