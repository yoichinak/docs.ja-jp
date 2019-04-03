---
title: 例外:try...with 式
description: 例外処理の F# の 'try...with' 式を使用する方法について説明します。
ms.date: 05/16/2016
ms.openlocfilehash: 742e0b595525c69b83a55682c3c8b9b650326ac7
ms.sourcegitcommit: fa38fe76abdc8972e37138fcb4dfdb3502ac5394
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/19/2018
ms.locfileid: "53614429"
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

`try...with`で例外を処理する式が使用されるF#します。 似ています、 `try...catch` (C#) ステートメント。 上記の構文では、コードでは、 *expression1*例外を生成する可能性があります。 `try...with`式が値を返します。 全体の式の値を返しますの例外がスローされない場合*expression1*します。 例外がスローされた場合、各*パターン*がさらに、例外とは、対応する、最初の一致するパターンの比較*式*と呼ばれる、*例外ハンドラー*、その分岐が実行され、全体的な式は、その例外ハンドラーで、式の値を返します。 パターンが一致しない場合、例外は、一致するハンドラーが見つかるまで呼び出し履歴を伝達します。 例外ハンドラー内の各式から返される値の型が式から返される型と一致する必要があります、`try`ブロックします。

多くの場合、エラーが発生するという事実は、各例外ハンドラー内の式から返される有効な値がないことを意味します。 一般的なパターンとしてオプション型である式の型です。 次のコード例は、このパターンを示しています。

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5601.fs)]

例外は、.NET 例外か F# の例外になることができます。 定義できますF#例外を使用して、`exception`キーワード。

例外の種類とその他の条件でフィルター処理するさまざまなパターンを使用することができます。オプションは、次の表にまとめたものです。

|パターン|説明|
|-------|-----------|
|:? *例外の種類*|指定した種類の .NET 例外に一致します。|
|:? *例外の種類*として*識別子*|指定された .NET 例外の種類と一致するが、例外の名前付きの値を示します。|
|*例外名*(*引数*)|一致するF#例外の種類と、引数をバインドします。|
|*identifier*|任意の例外に一致し、例外オブジェクトに名前をバインドします。 等価 **: でしょうか。System.Exception として**_識別子_|
|*識別子*とき*条件*|条件が true の場合、すべての例外と一致します。|

## <a name="examples"></a>使用例

次のコード例では、さまざまな例外ハンドラー パターンの使用を示します。

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5602.fs)]

> [!NOTE]
> `try...with`コンス トラクターは、個別の式から、`try...finally`式。 そのため、コードでは、両方が必要な場合、`with`ブロックと`finally`ブロック、2 つの式を入れ子にする必要があります。

> [!NOTE]
> 使用することができます`try...with`非同期ワークフローでおよびその他のコンピュテーション式でのカスタマイズされたバージョンの場合、`try...with`式を使用します。 詳細については、[非同期ワークフロー](../asynchronous-workflows.md)、および[コンピュテーション式](../computation-expressions.md)を参照してください。

## <a name="see-also"></a>関連項目

- [例外処理](index.md)
- [例外の種類](exception-types.md)
- [例外処理:`try...finally`式](the-try-finally-expression.md)