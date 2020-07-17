---
title: リソース管理:Use キーワード
description: F#キーワード ' use ' と ' using ' 関数について説明します。この関数は、リソースの初期化と解放を制御できます。
ms.date: 05/16/2016
ms.openlocfilehash: 5e0838401bee02050343b2f6dcc646a8dc8b4dc0
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/30/2019
ms.locfileid: "68627255"
---
# <a name="resource-management-the-use-keyword"></a>リソース管理:Use キーワード

このトピック`use` `using`では、リソースの初期化と解放を制御できるキーワードと関数について説明します。

## <a name="resources"></a>リソース

*リソース*という用語は、複数の方法で使用されます。 はい。リソースは、文字列やグラフィックスなど、アプリケーションで使用されるデータにすることができますが、このコンテキストでは、*リソース*とは、グラフィックスデバイスコンテキスト、ファイルハンドル、ネットワーク、データベースなどのソフトウェアまたはオペレーティングシステムのリソースを指します。接続、待機ハンドルなどの同時実行オブジェクトなど。 これらのリソースをアプリケーションで使用するには、オペレーティングシステムまたは他のリソースプロバイダーからリソースを取得した後、リソースの新しいリリースをプールに渡して、別のアプリケーションに提供できるようにします。 アプリケーションがリソースを共通プールに解放しないと、問題が発生します。

## <a name="managing-resources"></a>リソースの管理

アプリケーションのリソースを効率的かつ確実に管理するには、リソースを迅速かつ予測可能な方法で解放する必要があります。 .NET Framework を使用すると、 `System.IDisposable`インターフェイスを提供してこれを行うことができます。 を実装`System.IDisposable`する型に`System.IDisposable.Dispose`は、リソースを正しく解放するメソッドがあります。 適切に記述された`System.IDisposable.Dispose`アプリケーションは、リソースが制限されているオブジェクトが不要になったときに、すぐに呼び出されることを保証します。 さいわい、ほとんどの .NET 言語が、簡単に確認するサポートを提供し、F# には例外はありません。 Dispose パターンをサポートする便利な言語構成要素`use` `using`として、バインディングと関数の2つがあります。

## <a name="use-binding"></a>バインドを使用する

キーワードには、 `let`バインドの形式に似た形式があります。 `use`

*値* = *式*を使用する

`let`バインディングと同じ機能を提供しますが、値がスコープ`Dispose`外になったときにの呼び出しを値に追加します。 コンパイラは値に null チェックを挿入するため、値が`null`の場合、へ`Dispose`の呼び出しは試行されません。

次の例は、 `use`キーワードを使用してファイルを自動的に閉じる方法を示しています。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6301.fs)]

> [!NOTE]
> コンピュテーション式で`use`を使用できます。この場合、 `use`式のカスタマイズされたバージョンが使用されます。 詳細については、「[シーケンス](sequences.md)、[非同期ワークフロー](asynchronous-workflows.md)、および[コンピュテーション式](computation-expressions.md)」を参照してください。

## <a name="using-function"></a>関数の使用

関数`using`の形式は次のとおりです。

`using`(*expression1*)*関数または-ラムダ*

式では、expression1 は、破棄する必要があるオブジェクトを作成します。 `using` *Expression1* (破棄する必要があるオブジェクト) の結果は、引数、*値*、*またはラムダ*になります。これは、によって*生成される値に一致する型の1つの残りの引数を期待する関数です。expression1*、またはその型の引数を予期するラムダ式。 関数の実行が終了すると、ランタイムはリソースを呼び出し`Dispose` 、解放します (値が`null`の場合を除きます。この場合、Dispose への呼び出しは試行されません)。

次の例では`using` 、ラムダ式を含む式を示します。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6302.fs)]

次の例は、 `using`関数を使用した式を示しています。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6303.fs)]

関数は、いくつかの引数が既に適用されている関数である可能性があることに注意してください。 次のコード例はこの処理方法を示しています。 この例では、文字列`XYZ`を含むファイルを作成します。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6304.fs)]

`using` 関数`use`とバインディングは、同じことを実現するためのほぼ同じ方法です。 キーワード`using`を使用すると、が`Dispose`呼び出されるタイミングをより細かく制御できます。 を使用`using`すると`Dispose` 、関数またはラムダ式の末尾でが呼び出され`use`ます。キーワードを使用する`Dispose`と、が格納されているコードブロックの末尾でが呼び出されます。 一般に、 `using`関数の代わりにを`use`使用することをお勧めします。

## <a name="see-also"></a>関連項目

- [F# 言語リファレンス](index.md)
