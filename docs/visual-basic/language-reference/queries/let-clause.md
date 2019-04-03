---
title: Let 句 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.QueryLet
helpviewer_keywords:
- queries [Visual Basic], Let
- Let clause [Visual Basic]
- Let statement [Visual Basic]
ms.assetid: 981aa516-16eb-4c53-b1f1-5aa3e82f316e
ms.openlocfilehash: ff298f001a2d865446436e8099a2fbbef593a00a
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58828710"
---
# <a name="let-clause-visual-basic"></a>Let 句 (Visual Basic)
値を計算し、クエリ内で新しい変数に代入します。  
  
## <a name="syntax"></a>構文  
  
```  
Let variable = expression [, ...]  
```  
  
## <a name="parts"></a>指定項目  
  
|用語|定義|  
|---|---|  
|`variable`|必須。 指定された式の結果を参照に使用できるエイリアスです。|  
|`expression`|必須。 評価し、指定された変数に代入する式。|  
  
## <a name="remarks"></a>Remarks  
 `Let`句では、コンピューティングの各値がクエリの結果と、エイリアスを使用してそれらを参照することができます。 別名をなど、他の句で使用することができます、`Where`句。 `Let`句では、クエリに含まれる式の句の別名を指定でき、式の句が使用されるたびに、エイリアスを置き換えるため、読みやすくクエリ ステートメントを作成することができます。  
  
 任意の数を含めることができます`variable`と`expression`で割り当て、`Let`句。 各割り当てをコンマ (,) で区切ります。  
  
## <a name="example"></a>例  
 次のコード例では、`Let`製品の 10% の割引を計算する句。  
  
 [!code-vb[VbSimpleQuerySamples#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#16)]  
  
## <a name="see-also"></a>関連項目

- [Visual Basic における LINQ の概要](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [クエリ](../../../visual-basic/language-reference/queries/index.md)
- [Select 句](../../../visual-basic/language-reference/queries/select-clause.md)
- [From 句](../../../visual-basic/language-reference/queries/from-clause.md)
- [Where 句](../../../visual-basic/language-reference/queries/where-clause.md)
