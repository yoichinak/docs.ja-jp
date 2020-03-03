---
title: オブジェクト変数または With ブロック変数が設定されていません。
ms.date: 07/20/2015
f1_keywords:
- vbrID91
ms.assetid: 2f03e611-f0ed-465c-99a2-a816e034faa3
ms.openlocfilehash: 07c215d373e4ac1cbadf82a48b8cb3d90efdbdb4
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2019
ms.locfileid: "70040555"
---
# <a name="object-variable-or-with-block-variable-not-set"></a>オブジェクト変数または With ブロック変数が設定されていません。
無効なオブジェクト変数が参照されています。   このエラーが発生する原因は複数あります。

- 型を指定せずに変数が宣言されました。 変数が型を指定せずに宣言されている場合`Object`、既定値は型になります。

    たとえば、で`Dim x`宣言さ`String`れた変数の型は`Object;` 、で`Dim x As String`宣言された変数の型になります。

    > [!TIP]
    > ステートメント`Option Strict`では、 `Object`型を生成する暗黙的な型指定が禁止されています。 型を省略すると、コンパイル時エラーが発生します。 「 [Option Strict ステートメント](../../../visual-basic/language-reference/statements/option-strict-statement.md)」を参照してください。

- に`Nothing`設定されているオブジェクトを参照しようとしています。

- 正しく宣言されていない配列変数の要素にアクセスしようとしています。

    たとえば、として`products() As String`宣言された配列は、配列`products(3) = "Widget"`の要素を参照しようとした場合にエラーをトリガーします。 配列には要素がなく、オブジェクトとして扱われます。

- ブロックが初期化される前に、 `With...End With`ブロック内のコードにアクセスしようとしています。   ブロック`With...End With`は、ステートメントの`With`エントリポイントを実行して初期化する必要があります。

> [!NOTE]
> 以前のバージョンの Visual Basic または VBA では、このエラーは、 `Set` (`x = "name"`では`Set x = "name"`なく) キーワードを使用せずに変数に値を割り当てることによってもトリガーされました。 キーワード`Set`は Visual Basic .net では無効になりました。

## <a name="to-correct-this-error"></a>このエラーを解決するには

1. ファイル`Option Strict`の`On`先頭に次のコードを追加することにより、をに設定します。

    ```vb
    Option Strict On
    ```

    プロジェクトを実行すると、型が指定されていない変数の**エラー一覧**にコンパイラエラーが表示されます。

2. を有効`Option Strict`にしない場合は、(`Dim x`では`Dim x As String`なく) 型を指定せずに指定された変数をコードで検索し、目的の型を宣言に追加します。

3. に`Nothing`設定されているオブジェクト変数を参照していないことを確認します。  コード内でキーワード`Nothing`を検索し、参照するまでオブジェクトがに`Nothing`設定されないようにコードを修正します。

4. 配列変数にアクセスする前に、それらの変数を使用していることを確認してください。 最初に配列を作成するときに (`Dim x(5) As String`では`Dim x() As String`なく`ReDim` ) ディメンションを割り当てるか、またはキーワードを使用して、最初に配列にアクセスする前に配列の次元を設定できます。

5. ステートメントの`With` `With`エントリポイントを実行して、ブロックが初期化されていることを確認します。

## <a name="see-also"></a>関連項目

- [オブジェクト変数の宣言](../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)
- [ReDim ステートメント](../../../visual-basic/language-reference/statements/redim-statement.md)
- [With...End With ステートメント](../../../visual-basic/language-reference/statements/with-end-with-statement.md)
