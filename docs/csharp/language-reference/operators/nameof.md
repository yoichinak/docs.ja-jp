---
title: nameof 式 - C# リファレンス
ms.date: 07/12/2019
f1_keywords:
- nameof_CSharpKeyword
- nameof
helpviewer_keywords:
- nameof expression [C#]
ms.assetid: 33601bf3-cc2c-4496-846d-f9679bccf2a7
ms.openlocfilehash: 5a68161be7bb03122d2a63ccef4365c5853862b2
ms.sourcegitcommit: 2514f4e3655081dcfe1b22470c0c28500f952c42
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/18/2020
ms.locfileid: "79507140"
---
# <a name="nameof-expression-c-reference"></a>nameof 式 (C# リファレンス)

`nameof` 式を使うと、変数、型、またはメンバーの名前が文字列定数として生成されます。

[!code-csharp-interactive[nameof expression](snippets/NameOfOperator.cs#Examples)]

前の例で示されているように、型と名前空間の場合、生成される名前は通常[完全修飾](~/_csharplang/spec/basic-concepts.md#fully-qualified-names)ではありません。

`nameof` 式はコンパイル時に評価され、実行時には影響を与えません。

`nameof` 式を使って、引数をチェックするコードの保守性を高めることができます。

[!code-csharp[nameof and argument check](snippets/NameOfOperator.cs#ExceptionMessage)]

`nameof` 式は C# 6 以降で使用できます。

## <a name="c-language-specification"></a>C# 言語仕様

詳細については、[C# 言語仕様](~/_csharplang/spec/introduction.md)の「[Nameof 式](~/_csharplang/spec/expressions.md#nameof-expressions)」セクションをご覧ください。

## <a name="see-also"></a>関連項目

- [C# リファレンス](../index.md)
- [C# 演算子](index.md)
