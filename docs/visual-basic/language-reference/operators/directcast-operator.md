---
title: DirectCast 演算子 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.directCast
- directCast
helpviewer_keywords:
- DirectCast keyword [Visual Basic]
ms.assetid: 63e5a1d0-4d9e-4732-bf8f-e90c0c8784b8
ms.openlocfilehash: 628ce4f06b91d0f514f71dea3aad8ea0fee6dccf
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58821505"
---
# <a name="directcast-operator-visual-basic"></a>DirectCast 演算子 (Visual Basic)
継承または実装に基づいて、型変換操作をについて説明します。  
  
## <a name="remarks"></a>Remarks  
 `DirectCast` 変換で多少を提供できるように、ランタイム ヘルパー ルーチンに比べてパフォーマンスが向上する Visual Basic を使用しません`CType`との間のデータ型を変換するときに`Object`します。  
  
 使用する、`DirectCast`キーワードを使用するのと同様、 [CType Function](../../../visual-basic/language-reference/functions/ctype-function.md)と[TryCast 演算子](../../../visual-basic/language-reference/operators/trycast-operator.md)キーワード。 最初の引数と 2 番目の引数は変換する型として式を指定します。 `DirectCast` 2 つの引数のデータ型の間の継承または実装のリレーションシップが必要です。 つまり 1 つの型が継承または他の実装する必要があります。  
  
## <a name="errors-and-failures"></a>エラーと障害  
 `DirectCast` 継承または実装のリレーションシップが存在しないことが検出された場合は、コンパイラ エラーを生成します。 コンパイラ エラーがないことに成功した変換が保証されません。 必要な変換を縮小すると、実行時に失敗する可能性が。 この場合、ランタイム、<xref:System.InvalidCastException>エラー。  
  
## <a name="conversion-keywords"></a>変換キーワード  
 型変換のキーワードの比較は次のとおりです。  
  
|キーワード|データの種類|引数の関係|実行時エラー|  
|---|---|---|---|  
|[CType 関数](../../../visual-basic/language-reference/functions/ctype-function.md)|すべてのデータ型|2 つのデータ型の間で拡大または縮小変換を定義する必要があります。|スローされます。 <xref:System.InvalidCastException>|  
|`DirectCast`|すべてのデータ型|1 つの型を継承またはその他の型を実装する必要があります。|スローされます。 <xref:System.InvalidCastException>|  
|[TryCast 演算子](../../../visual-basic/language-reference/operators/trycast-operator.md)|参照型のみ|1 つの型を継承またはその他の型を実装する必要があります。|返します[Nothing](../../../visual-basic/language-reference/nothing.md)|  
  
## <a name="example"></a>例  
 次の例では、2 つの用途の`DirectCast`、いずれかのいずれかの実行時に失敗するが成功するとします。  
  
 [!code-vb[VbVbalrKeywords#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class1.vb#1)]  
  
 前の例では、実行時の入力の`q`は`Double`します。 `CType` 成功`Double`に変換できる`Integer`します。 ただし、最初の`DirectCast`実行時の型であるために、実行時に失敗`Double`継承関係を持たない`Integer`変換が存在する場合でも、します。 2 番目の`DirectCast`型からに変換されるためが成功すると<xref:System.Windows.Forms.Form>を入力する<xref:System.Windows.Forms.Control>、元の<xref:System.Windows.Forms.Form>継承します。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Convert.ChangeType%2A?displayProperty=nameWithType>
- [拡大変換と縮小変換](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [暗黙の型変換と明示的な型変換](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
