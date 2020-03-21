---
title: 参照戻り値
ms.date: 04/28/2017
helpviewer_keywords:
- variables [Visual Basic]
- ref return values [Visual Basic]
- ref returns [Visual Basic]
ms.assetid: 5ef0cc69-eb3a-4a67-92a2-78585f223cb5
ms.openlocfilehash: f2a92c584dbb12a322e28435d797fa4d7c2f6dbb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186933"
---
# <a name="support-for-reference-return-values-visual-basic"></a>参照の戻り値のサポート

C# 7.0 以降、C# 言語では*参照戻り値*がサポートされています。 参照の戻り値を理解する 1 つの方法は、参照によってメソッドに渡される引数とは逆であるということです。 参照によって渡された引数が変更されると、その変更は呼び出し元の変数の値に反映されます。 メソッドが呼び出し元に参照戻り値を提供すると、呼び出し元が参照戻り値に加えた変更が呼び出されたメソッドのデータに反映されます。

Visual Basic では、参照戻り値を使用してメソッドを作成することはできませんが、参照の戻り値を使用できます。 つまり、参照の戻り値を持つメソッドを呼び出して、その戻り値を変更すると、参照の戻り値への変更が呼び出されたメソッドのデータに反映されます。

## <a name="modifying-the-ref-return-value-directly"></a>ref 戻り値を直接変更する

常に成功し、パラメーターを持`ByRef`たないメソッドの場合は、参照の戻り値を直接変更できます。 これは、参照の戻り値を返す式に新しい値を代入することによって行います。

次の C# の`NumericValue.IncrementValue`例では、内部値をインクリメントし、それを参照戻り値として返すメソッドを定義します。

[!code-csharp[Ref-Return](../../../../../samples/snippets/visualbasic/programming-guide/language-features/procedures/ref-returns1.cs)]

次の Visual Basic の例では、参照の戻り値が呼び出し元によって変更されます。 メソッド呼び出しを`NumericValue.IncrementValue`行う行では、メソッドに値が割り当てられていないことに注意してください。 代わりに、メソッドによって返される参照戻り値に値を代入します。

[!code-vb[Ref-Return](../../../../../samples/snippets/visualbasic/programming-guide/language-features/procedures/use-ref-returns1.vb)]

## <a name="using-a-helper-method"></a>ヘルパー メソッドの使用

また、メソッド呼び出しの参照戻り値を直接変更する場合も、必ずしも望ましいとは限りません。 たとえば、文字列を返す検索メソッドは、必ずしも一致するものを見つけるとは限りません。 その場合、検索が成功した場合にのみ参照戻り値を変更します。

次の C# の例は、このシナリオを示しています。 C#`Sentence`で記述されたクラスには、`FindNext`指定された部分文字列で始まる文の次の単語を検索するメソッドが含まれていることを定義します。 文字列は参照戻り値として返され、参照によりメソッドに渡される `Boolean` 変数は検索が成功したかどうかを示します。 参照の戻り値は、戻り値の読み取りに加えて、呼び出し元が値を変更できること、およびクラスに内部に`Sentence`含まれるデータに変更が反映されることを示します。

[!code-csharp[Ref-Return](../../../../../samples/snippets/visualbasic/getting-started/ref-returns.cs)]

この場合、参照戻り値を直接変更することは、メソッド呼び出しが一致するものを見つけて文の最初の単語を返すことができない可能性があるため、信頼できません。 その場合、呼び出し元は誤って文の最初の単語を変更します。 これは、呼び出し元が`null`(または`Nothing`Visual Basic で) を返すことによって防止できます。 しかし、その場合、値がスローされる`Nothing`文字列を変更しようとすると、 <xref:System.NullReferenceException>. 呼び出し元が を返<xref:System.String.Empty?displayProperty=nameWithType>しても防ぐことが可能ですが、この場合は、呼び出<xref:System.String.Empty?displayProperty=nameWithType>し元が値を持つ文字列変数を定義する必要があります。 呼び出し元はその文字列を変更できますが、変更された文字列はクラスによって格納されている文の単語と関係がないため、変更自体は目的を`Sentence`果たしません。

このシナリオを処理する最善の方法は、参照によって参照の戻り値をヘルパー メソッドに渡す方法です。 ヘルパー メソッドには、メソッド呼び出しが成功したかどうかを判断するロジックが含まれます。 次の例では、実装可能な実装を示します。

[!code-vb[Ref-Return](../../../../../samples/snippets/visualbasic/getting-started/ref-return-helper.vb#1)]

## <a name="see-also"></a>関連項目

- [値と参照による引数の受け渡し](passing-arguments-by-value-and-by-reference.md)
- [Visual Basic におけるプロシージャ](index.md)
