---
title: エントリ ポイント
description: 実行が正式に開始、実行可能ファイルとしてコンパイルされた F# プログラムのエントリ ポイントを設定する方法について説明します。
ms.date: 05/16/2016
ms.openlocfilehash: c7aedda5834fb224507bfcecd4688978efa26547
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/15/2019
ms.locfileid: "65645452"
---
# <a name="entry-point"></a>エントリ ポイント

このトピックでは、F# プログラムのエントリ ポイントの設定を使用する方法について説明します。

## <a name="syntax"></a>構文

```fsharp
[<EntryPoint>]
let-function-binding
```

## <a name="remarks"></a>Remarks

前の構文で*let-関数-バインド*内の関数の定義には、`let`バインド。

実行可能ファイルの実行が正式な開始位置としてコンパイルされるプログラムへのエントリ ポイント。 適用することによって F# アプリケーションへのエントリ ポイントを指定する、`EntryPoint`属性をプログラムの`main`関数。 この関数 (を使用して作成、`let`バインディング) コンパイルの最後のファイルの最後の関数でなければなりません。 最後のコンパイル済みファイルは、プロジェクトの最後のファイルまたはコマンドラインに渡される最後のファイルです。

エントリ ポイント関数が型`string array -> int`します。 コマンドラインで指定された引数が渡される、`main`文字列の配列内の関数。 配列の最初の要素は、最初の引数他の言語であるために、実行可能ファイルの名前は、配列に含まれていません。 戻り値は、プロセスの終了コードとして使用されます。 0 は、成功した場合、通常、ことを示します。0 以外の値は、エラーを示します。 0 以外のリターン コードの特定の意味の規則はありません。リターン コードの意味では、アプリケーション固有です。

次の例では、単純な`main`関数。

[!code-fsharp[Main](../../../../samples/snippets/fsharp/entry-point/snippet501.fs)]

コマンドラインを使用したこのコードが実行されると`EntryPoint.exe 1 2 3`出力は次のようにします。

```console
Arguments passed to function : [|"1"; "2"; "3"|]
```

## <a name="implicit-entry-point"></a>暗黙的なエントリ ポイント

プログラムがにない場合**EntryPoint**エントリ ポイントでコンパイルする最後のファイルの最上位レベルのバインドを明示的に示す属性は、エントリ ポイントとして使用されます。

## <a name="see-also"></a>関連項目

- [関数](index.md)
- [let バインド](let-bindings.md)
