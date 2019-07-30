---
title: '方法: 長い修飾パスを使用してオブジェクトへのアクセスを高速化する (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], accessing
- variables [Visual Basic], object
- With statement [Visual Basic]
- With block
- object variables [Visual Basic], accessing
ms.assetid: 3eb7657f-c9fe-4e05-8bc3-4bb14d5ae585
ms.openlocfilehash: a8e50a2ed04037b48091321dc0c9ac2ea1db35f4
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/30/2019
ms.locfileid: "68631101"
---
# <a name="how-to-speed-up-access-to-an-object-with-a-long-qualification-path-visual-basic"></a>方法: 長い修飾パスを使用してオブジェクトへのアクセスを高速化する (Visual Basic)

複数のメソッドおよびプロパティの修飾パスを必要とするオブジェクトに頻繁にアクセスする場合は、修飾パスを繰り返さないことでコードを高速化できます。

修飾パスの繰り返しを回避するには、2つの方法があります。 オブジェクトは変数に割り当てることができます。または、 `With`...`End With`ブロック。

### <a name="to-speed-up-access-to-a-heavily-qualified-object-by-assigning-it-to-a-variable"></a>変数に割り当てて、高い修飾オブジェクトへのアクセスを高速化するには

1. 頻繁にアクセスするオブジェクトの型の変数を宣言します。 宣言の初期化部分に修飾パスを指定します。

    ```vb
    Dim ctrlActv As Control = someForm.ActiveForm.ActiveControl
    ```

2. オブジェクトのメンバーにアクセスするには、変数を使用します。

    ```vb
    ctrlActv.Text = "Test"
    ctrlActv.Location = New Point(100, 100)
    ctrlActv.Show()
    ```

### <a name="to-speed-up-access-to-a-heavily-qualified-object-by-using-a-withend-with-block"></a>With... を使用して、高い修飾オブジェクトへのアクセスを高速化するには末尾をブロックにする

1. `With`ステートメントに修飾パスを配置します。

    ```vb
    With someForm.ActiveForm.ActiveControl
    ```

2. ステートメントの`With` `End With`前に、ブロック内のオブジェクトのメンバーにアクセスします。

    ```vb
        .Text = "Test"
        .Location = New Point(100, 100)
        .Show()
    End With
    ```

## <a name="see-also"></a>関連項目

- [オブジェクト変数](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [With...End With ステートメント](../../../../visual-basic/language-reference/statements/with-end-with-statement.md)
