---
title: Ref 戻り値 (Visual Basic)
ms.date: 04/28/2017
helpviewer_keywords:
- variables [Visual Basic]
- ref return values [Visual Basic]
- ref returns [Visual Basic]
ms.assetid: 5ef0cc69-eb3a-4a67-92a2-78585f223cb5
ms.openlocfilehash: d0600f7d9030324160343e800c37e0f5e68bff61
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59133979"
---
# <a name="support-for-reference-return-values-visual-basic"></a>参照戻り値 (Visual Basic) のサポート

以降でC#7.0 では、C#の言語サポート*戻り値の参照*します。 参照戻り値を理解する方法の 1 つは、メソッドへの参照によって渡される引数の逆であります。 参照によって渡された引数が変更されたときに、変更は、呼び出し元に、変数の値に反映されます。 参照戻り値を提供します、呼び出し元に、メソッドと、は、呼び出されたメソッドのデータで、呼び出し元が参照戻り値に加えられた変更が反映されます。

Visual Basic では、参照を持つメソッドを作成すると、戻り値が、参照戻り値を使用することは許可されません。 つまり、参照戻り値を持つメソッドを呼び出すし、その戻り値を変更し、呼び出されたメソッドのデータに参照戻り値の変更が反映されます。

## <a name="modifying-the-ref-return-value-directly"></a>Ref 戻り値を直接変更します。

常に成功し、されていないメソッドは`ByRef`パラメーター、参照戻り値を直接変更することができます。 参照戻り値を返す式に新しい値を割り当てるこれを行います。 

次C#例、`NumericValue.IncrementValue`値を返すメソッドを内部の値をインクリメントし、参照として返します。 

[!code-csharp[Ref-Return](../../../../../samples/snippets/visualbasic/programming-guide/language-features/procedures/ref-returns1.cs)]

参照は、Visual Basic の例を次に、呼び出し元によって値が変更を返します。 注意では、行、`NumericValue.IncrementValue`メソッドの呼び出しでは、メソッドには、値は割り当てません。 代わりに、メソッドによって返される参照戻り値に値を割り当てます。

[!code-vb[Ref-Return](../../../../../samples/snippets/visualbasic/programming-guide/language-features/procedures/use-ref-returns1.vb)]

## <a name="using-a-helper-method"></a>ヘルパー メソッドを使用してください。

それ以外の場合、メソッド呼び出しの参照の戻り値を直接変更常にお勧めできません。 たとえば、文字列を返す検索メソッドが常に一致が見つかりません。 その場合は、検索が成功した場合にのみ、参照戻り値を変更します。

次C#の例は、このシナリオを示しています。 定義、`Sentence`で記述されたクラスC#が含まれています、`FindNext`メソッドを指定した部分文字列で始まる文で次の単語を検索します。 文字列は参照戻り値として返され、参照によりメソッドに渡される `Boolean` 変数は検索が成功したかどうかを示します。 参照戻り値、呼び出し元できましていないのみを読み取ることを返される値。そのユーザーも変更できますとで内部に含まれるデータにその変更が反映されます、`Sentence`クラス。

[!code-csharp[Ref-Return](../../../../../samples/snippets/visualbasic/getting-started/ref-returns.cs)]

参照を直接変更する戻り値の値ここでが信頼性が高く、ために、一致が見つかるし、文の最初の単語を返すメソッドの呼び出しが失敗します。 その場合は、呼び出し元は誤って文の最初の単語を変更します。 返す、呼び出し元によってこれを回避できる可能性があります、 `null` (または`Nothing`Visual Basic で)。 その場合は、値が文字列を変更しようとしていますが、`Nothing`スロー、<xref:System.NullReferenceException>します。 場合は、呼び出し元を返すことが防止することも<xref:System.String.Empty?displayProperty=nameWithType>、呼び出し元が値が文字列変数を定義する必要がありますが、<xref:System.String.Empty?displayProperty=nameWithType>します。 変更後の文字列が格納されている文脈での単語にリレーションシップがあるないため、呼び出し元は、その文字列を変更できる、中に変更自体は目的、意味がありません、`Sentence`クラス。

このシナリオを処理する最善の方法では、参照戻り値を渡し、ヘルパー メソッドへの参照です。 ヘルパー メソッドには、メソッド呼び出しが成功したし、変更する場合と、参照戻り値かどうかを判断するロジックが含まれています。 次の例では、考えられる実装を提供します。

[!code-vb[Ref-Return](../../../../../samples/snippets/visualbasic/getting-started/ref-return-helper.vb#1)]

## <a name="see-also"></a>関連項目

- [値と参照渡しの引数を渡す](passing-arguments-by-value-and-by-reference.md)
- [Visual Basic におけるプロシージャ](index.md)
