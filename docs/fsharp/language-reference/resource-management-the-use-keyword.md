---
title: リソースの管理:Use キーワード
description: については、F#キーワード 'use' と 'using' の関数は、初期化とリソースの解放を制御できます。
ms.date: 05/16/2016
ms.openlocfilehash: 127877a3823faade9bc3c6aefea655c86cc348e7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61770488"
---
# <a name="resource-management-the-use-keyword"></a>リソースの管理:Use キーワード

このトピックで説明、キーワード`use`と`using`関数で、初期化とリソースの解放を制御できます。

## <a name="resources"></a>リソース

用語*リソース*は、複数の方法で使用されます。 はい、リソースが文字列、グラフィックス、like などが、このコンテキストで、アプリケーションが使用するデータを指定できます*リソース*グラフィックス デバイス コンテキスト、ファイル ハンドル、ネットワークなどのソフトウェアやオペレーティング システムのリソースへの参照データベースの接続、待機ハンドルなどの同時実行オブジェクト。 アプリケーションがこれらのリソースの使用には、オペレーティング システムまたは別のアプリケーションに提供するようにプールに、リソースの今後のリリースを続けて、その他のリソース プロバイダーからリソースの取得が含まれます。 アプリケーションが共通のプールに戻すリソースを解放しないと、問題が発生します。

## <a name="managing-resources"></a>リソースの管理

をアプリケーション内のリソースを効率的に責任を持って管理するには、を予測可能な方法で迅速にリソースを解放する必要があります。 .NET Framework では、このことで実行できます。、`System.IDisposable`インターフェイス。 実装する型`System.IDisposable`が、`System.IDisposable.Dispose`メソッドで、誤ってリソースを解放します。 適切に記述されたアプリケーションを保証する`System.IDisposable.Dispose`限られたリソースを保持する任意のオブジェクトが不要になったときに迅速に呼び出されます。 さいわい、ほとんどの .NET 言語が、簡単に確認するサポートを提供し、F# には例外はありません。 Dispose パターンをサポートする 2 つの便利な言語構造がある:`use`バインドと`using`関数。

## <a name="use-binding"></a>バインディングを使用します。

`use`キーワードには、フォームのような`let`バインド。

使用して、*値* = *式*

同じ機能を提供します、`let`バインドしますが、への呼び出しを追加します`Dispose`値がスコープ外になる値。 場合に、値は、コンパイラは、値の null チェックを挿入します。 注`null`、への呼び出し`Dispose`は行われません。

次の例を使用してファイルを自動的に閉じる方法を示しています、`use`キーワード。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6301.fs)]

> [!NOTE]
> 使用することができます`use`計算式で、カスタマイズされたバージョンの場合、`use`式を使用します。 詳細については、次を参照してください。[シーケンス](sequences.md)、[非同期ワークフロー](asynchronous-workflows.md)、および[コンピュテーション式](computation-expressions.md)します。

## <a name="using-function"></a>関数を使用してください。

`using`関数には、次の形式。

`using` (*expression1*) *function-or-lambda*

`using`式、 *expression1*破棄する必要がありますオブジェクトを作成します。 結果*expression1* (破棄する必要がありますオブジェクト) が、引数*値*を*関数またはラムダ*、1 つが必要とする関数によって生成された値に一致する型の引数の残り*expression1*、またはその型の引数を受け取るラムダ式。 ランタイムが呼び出す関数の実行の最後に、`Dispose`リソースを解放し、(値がない限り`null`、後者 Dispose の呼び出しは行われません)。

次の例で、`using`ラムダ式を持つ式。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6302.fs)]

例を次に示します、`using`関数を使用した式。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6303.fs)]

関数は既に適用されるいくつかの引数を持つ関数である可能性がありますに注意してください。 次のコード例はこの処理方法を示しています。 文字列を含むファイルが作成されます`XYZ`します。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6304.fs)]

`using`関数と`use`バインディングは同じことを実現するほぼ同等の方法です。 `using`キーワードは、時に詳細に制御を提供します。`Dispose`が呼び出されます。 使用すると`using`、`Dispose`を使用するときに、関数またはラムダ式の最後に呼び出されますが、`use`キーワード、`Dispose`要素を含むコード ブロックの最後に呼び出されます。 一般に、使用を希望する必要があります`use`の代わりに、`using`関数。

## <a name="see-also"></a>関連項目

- [F# 言語リファレンス](index.md)