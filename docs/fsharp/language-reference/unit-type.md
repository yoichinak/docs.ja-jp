---
title: Unit 型
description: 値はありませんが必要なまたは必要なときに言語の構文で値が必要な場所、場所を保持するために F# 'unit' の型を使用する多くの場合について説明します。
ms.date: 05/16/2016
ms.openlocfilehash: f1866ff12f36f4f8d3eaa1275551c42fc4ade216
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61982528"
---
# <a name="unit-type"></a>Unit 型

`unit`型は、特定の値がないことを示す型、`unit`型のみ 1 つの値を持つ、その他の値はありませんが存在するか、必要なときに、プレース ホルダーとして機能します。

## <a name="syntax"></a>構文

```fsharp
// The value of the unit type.
()
```

## <a name="remarks"></a>Remarks

すべての F# の式は、値に評価される必要があります。 型の値、目的の値を生成しない式の`unit`使用されます。 `unit`型に似ています、 `void` c# および C++ などの言語での型。

`unit`型が 1 つの値とその値は、トークンで示される`()`します。

値、`unit`型が F# 言語の構文で、値が必要な場合は、値はありませんが必要なまたは必要なときに、場所を保持するためにプログラミングでよく使用されます。 例の戻り値があります、`printf`関数。 の重要なアクション、`printf`操作が、関数で発生する関数が実際の値を返す必要はありません。 そのため、戻り値が型`unit`します。

一部のコンストラクトの期待を`unit`値。 たとえば、`do`バインドまたはモジュールの最上位レベルで、コードを評価する予定を`unit`値。 コンパイラ警告を報告するときに、`do`バインドまたはコード モジュールの最上位レベル以外の結果を生成、`unit`使用されていない、次の例に示すように値。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet901.fs)]

この警告は、関数型プログラミングの特性その他の .NET プログラミング言語では表示されません。 副作用は関数がない、純粋に機能するプログラムでは、最終的な戻り値は、関数呼び出しの結果だけが。 そのため、結果を無視すると、可能性のあるプログラミング エラーです。 F#が純粋に機能していないプログラミング言語、機能のプログラミング スタイル可能な場合に従うことをお勧めが。

## <a name="see-also"></a>関連項目

- [プリミティブ](primitive-types.md)
- [F# 言語リファレンス](index.md)