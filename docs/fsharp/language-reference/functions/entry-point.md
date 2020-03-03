---
title: エントリ ポイント
description: 実行が正式に開始、実行可能ファイルとしてコンパイルされた F# プログラムのエントリ ポイントを設定する方法について説明します。
ms.date: 05/16/2016
ms.openlocfilehash: 5e13416131d4dfd22583439fedf51f18f7a461da
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630523"
---
# <a name="entry-point"></a>エントリ ポイント

このトピックでは、F# プログラムのエントリ ポイントの設定を使用する方法について説明します。

## <a name="syntax"></a>構文

```fsharp
[<EntryPoint>]
let-function-binding
```

## <a name="remarks"></a>Remarks

前の構文では、 *let-binding*は`let`バインド内の関数の定義です。

実行可能ファイルとしてコンパイルされるプログラムへのエントリポイントとして、実行が正式に開始されます。 適用することによって F# アプリケーションへのエントリ ポイントを指定する、`EntryPoint`属性をプログラムの`main`関数。 ( `let`バインディングを使用して作成された) この関数は、最後にコンパイルされたファイルの最後の関数である必要があります。 最後にコンパイルされたファイルは、プロジェクトの最後のファイル、またはコマンドラインに渡される最後のファイルです。

エントリポイント関数の型`string array -> int`はです。 コマンドラインに指定された引数は、文字列`main`の配列内の関数に渡されます。 最初の引数は、配列の最初の要素です。実行可能ファイルの名前は、他の言語のものであるため、配列には含まれません。 戻り値は、プロセスの終了コードとして使用されます。 通常、ゼロは成功を示します。0以外の値はエラーを示します。 0以外のリターンコードの特定の意味に関する規則はありません。リターンコードの意味は、アプリケーションによって異なります。

単純`main`な関数の例を次に示します。

[!code-fsharp[Main](~/samples/snippets/fsharp/entry-point/snippet501.fs)]

このコードをコマンドライン`EntryPoint.exe 1 2 3`で実行すると、出力は次のようになります。

```console
Arguments passed to function : [|"1"; "2"; "3"|]
```

## <a name="implicit-entry-point"></a>暗黙的なエントリポイント

エントリポイントを明示的に示す**EntryPoint**属性がプログラムにない場合は、最後にコンパイルされるファイル内の最上位レベルのバインドがエントリポイントとして使用されます。

## <a name="see-also"></a>関連項目

- [関数](index.md)
- [let バインド](let-bindings.md)
