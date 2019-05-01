---
title: オブジェクト変数または With ブロック変数が設定されていません。
ms.date: 07/20/2015
f1_keywords:
- vbrID91
ms.assetid: 2f03e611-f0ed-465c-99a2-a816e034faa3
ms.openlocfilehash: 766b95163f164ec76135b964115069b6855ceebf
ms.sourcegitcommit: 89fcad7e816c12eb1299128481183f01c73f2c07
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/24/2019
ms.locfileid: "63807872"
---
# <a name="object-variable-or-with-block-variable-not-set"></a>オブジェクト変数または With ブロック変数が設定されていません。
無効なオブジェクト変数が参照されています。   このエラーが発生する原因は複数あります。

- 変数は、型を指定せずに宣言されました。 型を指定せずに宣言された変数は場合、既定値は入力`Object`します。

    たとえば、変数を使用して宣言`Dim x`型になります`Object;`で宣言された変数`Dim x As String`型になります`String`します。

    > [!TIP]
    >  `Option Strict`ステートメントは、暗黙の型の指定を許可しません、`Object`型。 型を省略すると、コンパイル時エラーが発生します。 参照してください[Option Strict ステートメント](../../../visual-basic/language-reference/statements/option-strict-statement.md)します。

- 設定されているオブジェクトを参照しようとして`Nothing`します。

- 適切に宣言されていない配列変数の要素にアクセスしようとしました。

    たとえば、配列として宣言されている`products() As String`配列の要素を参照しようとする場合、エラーをトリガーする`products(3) = "Widget"`。 配列は要素が存在しないと、オブジェクトとして扱われます。

- アクセス コード内にしようとしています、`With...End With`ブロックが初期化されている前にブロックします。   A`With...End With`ブロックを実行することによって初期化する必要があります、`With`ステートメントのエントリ ポイント。

> [!NOTE]
> 以前のバージョンの Visual Basic または VBA でこのエラーを使用せず、変数に値を割り当てることによってもにトリガーされる、`Set`キーワード (`x = "name"`の代わりに`Set x = "name"`)。 `Set`キーワードは Visual Basic .Net で無効になりました。

## <a name="to-correct-this-error"></a>このエラーを解決するには

1. 設定`Option Strict`に`On`ファイルの先頭に次のコードを追加することで。

    ```vb
    Option Strict On
    ```

    プロジェクトを実行すると、コンパイラ エラーに表示されます、**エラー一覧**せず、型が指定されているすべての変数にします。

2. 有効にしたくない場合`Option Strict`、せず、型指定されている変数がある場合、コードを検索 (`Dim x`の代わりに`Dim x As String`) し、目的の型を宣言に追加します。

3. 設定されているオブジェクト変数を参照していないことを確認`Nothing`します。  コード内のキーワードの`Nothing`、オブジェクトに設定されていないように、コードの修正と`Nothing`を参照した後になるまでです。

4. アクセスする前に、配列変数の寸法はことを確認します。 最初に、配列を作成するときに、ディメンションを割り当てることができますか (`Dim x(5) As String`の代わりに`Dim x() As String`)、またはを使用して、`ReDim`キーワードを最初にアクセスする前に、配列の次元を設定します。

5. 必ず、`With`ブロックが実行することによって初期化されて、`With`ステートメントのエントリ ポイント。

## <a name="see-also"></a>関連項目

- [オブジェクト変数の宣言](../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)
- [ReDim ステートメント](../../../visual-basic/language-reference/statements/redim-statement.md)
- [With...End With ステートメント](../../../visual-basic/language-reference/statements/with-end-with-statement.md)
