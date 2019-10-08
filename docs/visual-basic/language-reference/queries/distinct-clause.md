---
title: Distinct 句 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.QueryDistinct
helpviewer_keywords:
- Distinct clause [Visual Basic]
- Distinct statement [Visual Basic]
- queries [Visual Basic], Distinct
ms.assetid: 86f42614-0d8f-4ffc-b888-ce8a37a8d36a
ms.openlocfilehash: e8d3e38261a04c4d29faab351d24d6710413b09a
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/07/2019
ms.locfileid: "72004795"
---
# <a name="distinct-clause-visual-basic"></a>Distinct 句 (Visual Basic)
現在の範囲変数の値を制限して、後続のクエリ句で重複する値を削除します。  
  
## <a name="syntax"></a>構文  
  
```vb  
Distinct  
```  
  
## <a name="remarks"></a>コメント  
 @No__t-0 句を使用すると、一意の項目の一覧を返すことができます。 @No__t-0 句を実行すると、クエリで重複するクエリ結果が無視されます。 @No__t-0 句は、`Select` 句で指定されたすべての戻り値フィールドに対して重複する値に適用されます。 @No__t-0 句が指定されていない場合、`Distinct` 句は `From` 句で特定されたクエリの範囲変数に適用されます。 範囲変数が変更できない型である場合、クエリでは、型のすべてのメンバーが既存のクエリの結果と一致する場合にのみ、クエリの結果が無視されます。  
  
## <a name="example"></a>例  
 次のクエリ式では、顧客の一覧と顧客の注文リストを結合します。 @No__t-0 句は、一意の顧客名と注文日の一覧を返すために含まれています。  
  
 [!code-vb[VbSimpleQuerySamples#20](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#20)]  
  
## <a name="see-also"></a>関連項目

- [Visual Basic における LINQ の概要](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [クエリ](../../../visual-basic/language-reference/queries/index.md)
- [From 句](../../../visual-basic/language-reference/queries/from-clause.md)
- [Select 句](../../../visual-basic/language-reference/queries/select-clause.md)
- [Where 句](../../../visual-basic/language-reference/queries/where-clause.md)
