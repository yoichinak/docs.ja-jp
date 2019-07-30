---
title: 例外:try...with 式
description: 例外処理の F# の 'try...with' 式を使用する方法について説明します。
ms.date: 05/16/2016
ms.openlocfilehash: e4d615086a93e26b76cca460e797659ca13792b5
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630252"
---
# <a name="exceptions-the-trywith-expression"></a>例外:try...with 式

このトピックで説明します、`try...with`式、F# 言語での例外処理に使用される式。

## <a name="syntax"></a>構文

```fsharp
try
    expression1
with
| pattern1 -> expression2
| pattern2 -> expression3
...
```

## <a name="remarks"></a>Remarks

式`try...with`は、でF#例外を処理するために使用されます。 これは、の`try...catch` C#ステートメントに似ています。 前の構文では、 *expression1*のコードが例外を生成する場合があります。 式`try...with`は値を返します。 例外がスローされない場合、式全体が*expression1*の値を返します。 例外がスローされた場合は、各*パターン*が例外で比較され、最初に一致するパターンについて、その分岐の*例外ハンドラー*と呼ばれる対応する*式*が実行され、全体の式が実行されます。この例外ハンドラーの式の値を返します。 一致するパターンがない場合、例外は、一致するハンドラーが見つかるまで呼び出し履歴を上位に伝達します。 例外ハンドラー内の各式から返される値の型は、 `try`ブロック内の式から返される型と一致する必要があります。

多くの場合、エラーが発生したという事実は、各例外ハンドラーの式から返される有効な値がないことを意味します。 よく使用されるパターンは、式の型がオプション型であることです。 次のコード例は、このパターンを示しています。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5601.fs)]

例外は、.NET 例外か F# の例外になることができます。 `exception`キーワードを使用F#して例外を定義できます。

さまざまなパターンを使用して、例外の種類やその他の条件をフィルター処理できます。次の表に、オプションの概要を示します。

|パターン|説明|
|-------|-----------|
|:? *exception-type*|指定された .NET 例外の種類と一致します。|
|:? *例外-* *識別子*としての型|指定された .NET 例外の種類と一致しますが、例外には名前付きの値が与えられます。|
|*例外-名前*(*引数*)|は、 F#例外の種類と一致し、引数をバインドします。|
|*identifier*|任意の例外を一致させ、その名前を例外オブジェクトにバインドします。 **これはと等価です。System.exception_識別子_とし**ての例外|
|*条件*の場合の*識別子*|条件が true の場合、すべての例外に一致します。|

## <a name="examples"></a>使用例

次のコード例は、さまざまな例外ハンドラーパターンの使用方法を示しています。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5602.fs)]

> [!NOTE]
> コンストラクトは、式と`try...finally`は別の式です。 `try...with` したがって、コードに`with`ブロック`finally`とブロックの両方が必要な場合は、2つの式を入れ子にする必要があります。

> [!NOTE]
> は、非同期`try...with`ワークフローやその他の計算式で使用できます。その場合、 `try...with`式のカスタマイズされたバージョンが使用されます。 詳細については、「[非同期ワークフロー](../asynchronous-workflows.md)」と「[コンピュテーション式](../computation-expressions.md)」を参照してください。

## <a name="see-also"></a>関連項目

- [例外処理](index.md)
- [例外の種類](exception-types.md)
- [例外: `try...finally`式](the-try-finally-expression.md)
