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
ms.openlocfilehash: fbca9fa8aa227d8d5b6488bef179f4bda08bb38c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "58830059"
---
# <a name="distinct-clause-visual-basic"></a>Distinct 句 (Visual Basic)
次のクエリ句で、重複を排除する現在の範囲変数の値を制限します。  
  
## <a name="syntax"></a>構文  
  
```  
Distinct  
```  
  
## <a name="remarks"></a>Remarks  
 使用することができます、`Distinct`句を一意の項目の一覧を返します。 `Distinct`句によって重複するクエリの結果を無視するクエリ。 `Distinct`句は、すべての戻り値で指定されたフィールドの重複する値を適用、`Select`句。 ない場合は`Select`句が指定されて、`Distinct`で特定されたクエリの範囲変数に句が適用される、`From`句。 クエリは、範囲変数が変更不可の型でない場合、既存のクエリ結果に一致する型のすべてのメンバーである場合は、クエリ結果を無視してはのみです。  
  
## <a name="example"></a>例  
 次のクエリ式では、顧客の一覧と顧客の注文のリストを結合します。 `Distinct`句は、一意の顧客名のリストを返し、注文日に含まれています。  
  
 [!code-vb[VbSimpleQuerySamples#20](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#20)]  
  
## <a name="see-also"></a>関連項目

- [Visual Basic における LINQ の概要](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [クエリ](../../../visual-basic/language-reference/queries/index.md)
- [From 句](../../../visual-basic/language-reference/queries/from-clause.md)
- [Select 句](../../../visual-basic/language-reference/queries/select-clause.md)
- [Where 句](../../../visual-basic/language-reference/queries/where-clause.md)
