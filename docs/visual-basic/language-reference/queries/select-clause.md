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
ms.openlocfilehash: 087472c51d203be083fea0d39ade6f12066cfcb4
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/07/2019
ms.locfileid: "72004738"
---
# <a name="select-clause-visual-basic"></a>Select 句 (Visual Basic)
クエリの結果を定義します。  
  
## <a name="syntax"></a>構文  
  
```vb  
Select [ var1 = ] fieldName1 [, [ var2 = ] fieldName2 [...] ]  
```  
  
## <a name="parts"></a>指定項目  
 `var1`  
 任意。 列式の結果を参照するために使用できる別名。  
  
 `fieldName1`  
 必須。 クエリ結果に返されるフィールドの名前。  
  
## <a name="remarks"></a>コメント  
 @No__t-0 句を使用すると、クエリから返される結果を定義できます。 これにより、クエリによって作成された新しい匿名型のメンバーを定義することも、クエリによって返される名前付きの型のメンバーを対象にすることもできます。 @No__t-0 句は、クエリには必要ありません。 @No__t-0 句が指定されていない場合、クエリは、現在のスコープで特定された範囲変数のすべてのメンバーに基づいて型を返します。 詳細については、「[匿名型](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)」を参照してください。 クエリで名前付きの型を作成すると、型 <xref:System.Collections.Generic.IEnumerable%601> の結果が返されます。この場合、`T` は作成された型です。  
  
 @No__t-0 句は、現在のスコープ内の任意の変数を参照できます。 これには、`From` 句 (または @no__t 句) で識別される範囲変数が含まれます。 また、別名を使用して作成された新しい変数も、`Aggregate`、`Let`、`Group By`、または `Group Join` の各句、またはクエリ式の前の `Select` 句の変数によって作成されます。 @No__t-0 句には、静的な値を含めることもできます。 たとえば、次のコード例では、`Select` 句でクエリ結果を、4つのメンバーを持つ新しい匿名型として定義するクエリ式を示します。 `ProductName`、`Price`、`Discount`、および `DiscountedPrice` です。 @No__t-0 および `Price` メンバーの値は、`From` 句で定義されている製品範囲変数から取得されます。 @No__t 0 のメンバー値は、`Let` 句で計算されます。 @No__t 0 のメンバーは静的な値です。  
  
 [!code-vb[VbSimpleQuerySamples#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#27)]  
  
 @No__t-0 句は、後続のクエリ句に対して範囲変数の新しいセットを導入し、以前の範囲変数はスコープに含まれなくなりました。 クエリ式の最後の `Select` 句によって、クエリの戻り値が決まります。 たとえば、次のクエリでは、合計が500を超えるすべての顧客注文の会社名と注文 ID が返されます。 最初の `Select` 句は、`Where` 句の範囲変数と2番目の `Select` 句を識別します。 2番目の `Select` 句は、クエリによって返された値を新しい匿名型として識別します。  
  
 [!code-vb[VbSimpleQuerySamples#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#28)]  
  
 @No__t-0 句によって返される1つの項目が識別される場合、クエリ式はその1つの項目の型のコレクションを返します。 @No__t-0 句によって返される複数の項目が識別される場合、クエリ式は、選択した項目に基づいて、新しい匿名型のコレクションを返します。 たとえば、次の2つのクエリは、`Select` 句に基づいて2つの異なる型のコレクションを返します。 最初のクエリでは、会社名のコレクションが文字列として返されます。 2番目のクエリは、会社名と住所情報を入力した @no__t 0 オブジェクトのコレクションを返します。  
  
 [!code-vb[VbSimpleQuerySamples#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#29)]  
  
## <a name="example"></a>例  
 次のクエリ式では、`From` 句を使用して、`customers` コレクションの範囲変数 `cust` を宣言しています。 @No__t-0 句は、customer name と ID 値を選択し、新しい範囲変数の `CompanyName` と `CustomerID` 列を設定します。 @No__t-0 ステートメントは、返された各オブジェクトをループし、各レコードに対して `CompanyName` と `CustomerID` の列を表示します。  
  
 [!code-vb[VbSimpleQuerySamples#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#30)]  
  
## <a name="see-also"></a>関連項目

- [Visual Basic における LINQ の概要](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [クエリ](../../../visual-basic/language-reference/queries/index.md)
- [From 句](../../../visual-basic/language-reference/queries/from-clause.md)
- [Where 句](../../../visual-basic/language-reference/queries/where-clause.md)
- [Order By 句](../../../visual-basic/language-reference/queries/order-by-clause.md)
- [匿名型](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)
