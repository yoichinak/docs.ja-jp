---
title: TryCast 演算子 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.trycast
- trycast
helpviewer_keywords:
- TryCast keyword [Visual Basic]
ms.assetid: d1ef5d47-fef4-491e-b014-1d910628f65c
ms.openlocfilehash: c0eea4565d5040bb00743fc7864ac15b0fccdea9
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58831593"
---
# <a name="trycast-operator-visual-basic"></a>TryCast 演算子 (Visual Basic)
例外をスローしない型変換操作について説明します。  
  
## <a name="remarks"></a>Remarks  
 変換が失敗した場合、`CType`と`DirectCast`スロー両方、<xref:System.InvalidCastException>エラー。 これは、アプリケーションのパフォーマンスに悪影響を与える。 `TryCast` 返します[Nothing](../../../visual-basic/language-reference/nothing.md)、可能性のある例外を処理するのではなく、に対して返された結果をテストする必要がありますのみように`Nothing`します。  
  
 使用する、`TryCast`キーワードを使用する場合と同様、 [CType Function](../../../visual-basic/language-reference/functions/ctype-function.md)と[DirectCast 演算子](../../../visual-basic/language-reference/operators/directcast-operator.md)キーワード。 最初の引数と 2 番目の引数は変換する型として式を指定します。 `TryCast` クラスやインターフェイスなど、参照型に対してのみ動作します。 2 つの型の間の継承または実装のリレーションシップが必要です。 つまり 1 つの型が継承または他の実装する必要があります。  
  
## <a name="errors-and-failures"></a>エラーと障害  
 `TryCast` 継承または実装のリレーションシップが存在しないことが検出された場合は、コンパイラ エラーを生成します。 コンパイラ エラーがないことに成功した変換が保証されません。 必要な変換を縮小すると、実行時に失敗する可能性が。 この場合、`TryCast`返します[Nothing](../../../visual-basic/language-reference/nothing.md)します。  
  
## <a name="conversion-keywords"></a>変換キーワード  
 型変換のキーワードの比較は次のとおりです。  
  
|キーワード|データの種類|引数の関係|実行時エラー|  
|---|---|---|---|  
|[CType 関数](../../../visual-basic/language-reference/functions/ctype-function.md)|すべてのデータ型|2 つのデータ型の間で拡大または縮小変換を定義する必要があります。|スローされます。 <xref:System.InvalidCastException>|  
|[DirectCast 演算子](../../../visual-basic/language-reference/operators/directcast-operator.md)|すべてのデータ型|1 つの型を継承またはその他の型を実装する必要があります。|スローされます。 <xref:System.InvalidCastException>|  
|`TryCast`|参照型のみ|1 つの型を継承またはその他の型を実装する必要があります。|返します[Nothing](../../../visual-basic/language-reference/nothing.md)|  
  
## <a name="example"></a>例  
 次の例は、`TryCast` を使用する方法を示しています。  
  
 [!code-vb[VbVbalrKeywords#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class1.vb#6)]  
  
## <a name="see-also"></a>関連項目

- [拡大変換と縮小変換](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [暗黙の型変換と明示的な型変換](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
