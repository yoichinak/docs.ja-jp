---
title: ループの境界とステップの句が同じ型に変換されないため、'<variablename>' の型を推論できません
ms.date: 07/20/2015
f1_keywords:
- bc30982
- vbc30982
helpviewer_keywords:
- BC30982
ms.assetid: 741e85d9-a747-42ad-a1e1-a3f1928aaff5
ms.openlocfilehash: c3086f79fb71693810bc8f14e8c0f493aa1e6515
ms.sourcegitcommit: 463f3f050cecc0b6403e67f19a61f870fb8e7b7d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/26/2019
ms.locfileid: "68512704"
---
# <a name="type-of-variablename-cannot-be-inferred-because-the-loop-bounds-and-the-step-variable-do-not-widen-to-the-same-type"></a>ループの境界\<とステップの変数が同じ型に拡大変換されないため、' variablename > ' の型を推論できません

次の条件が`For...Next`満たされているため、コンパイラが loop コントロール変数のデータ型を推論できないループが記述されました。

- ループ コントロール変数のデータ型が `As` 句で指定されていません。

- ループ境界とステップ変数に少なくとも 2 つのデータ型が含まれています。

- データ型の間に標準変換は存在しません。

 そのため、コンパイラは、ループのコントロール変数のデータ型を推論できません。

 次の例では、ステップ変数は文字で、ループの境界は両方とも整数です。 文字と整数の間に標準の変換がないため、このエラーが報告されます。

```vb
Dim stepVar = "1"c
Dim m = 0
Dim n = 20

' Not valid.
' For i = 1 To 10 Step stepVar
    ' Loop processing
' Next
```

**エラー ID:** BC30982

## <a name="to-correct-this-error"></a>このエラーを解決するには

- ループの境界とステップの変数の型を必要に応じて変更して、そのうち少なくとも1つが、他の型が拡大する型になるようにします。 前の例では、の`stepVar`型をに`Integer`変更します。

  ```vb
  Dim stepVar = 1
  ```

  \- または -

  ```vb
  Dim stepVar As Integer = 1
  ```

- 明示的な変換関数を使用して、ループの境界とステップ変数を適切な型に変換します。 前の例では、 `Val`関数をに`stepVar`適用します。

  ```vb
  For i = 1 To 10 Step Val(stepVar)
      ' Loop processing
  Next
  ```

## <a name="see-also"></a>関連項目

- <xref:Microsoft.VisualBasic.Conversion.Val%2A>
- [For...Next ステートメント](../../../visual-basic/language-reference/statements/for-next-statement.md)
- [暗黙の型変換と明示的な型変換](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
- [ローカル型の推論](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [Option Infer ステートメント](../../../visual-basic/language-reference/statements/option-infer-statement.md)
- [データ型変換関数](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [拡大変換と縮小変換](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
