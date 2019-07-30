---
title: '方法: オブジェクトのメンバーにアクセスする (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- members [Visual Basic], accessing
- object variables [Visual Basic], accessing members
ms.assetid: a0072514-6a79-4dd6-8d03-ca8c13e61ddc
ms.openlocfilehash: 882046b829ade2da7c10b3db4c0d6c9ca9f3d579
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630835"
---
# <a name="how-to-access-members-of-an-object-visual-basic"></a>方法: オブジェクトのメンバーにアクセスする (Visual Basic)

オブジェクトを参照するオブジェクト変数がある場合は、そのオブジェクトのメソッド、プロパティ、フィールド、イベントなどのメンバーを使用することがよくあります。 たとえば、新しい<xref:System.Windows.Forms.Form>オブジェクトを作成した後で、その<xref:System.Windows.Forms.Control.Text%2A>オブジェクトのプロパティを設定したり、 <xref:System.Windows.Forms.Control.Focus%2A>メソッドを呼び出したりすることができます。

## <a name="accessing-members"></a>メンバーへのアクセス

オブジェクトのメンバーにアクセスするには、それを参照する変数を使用します。

#### <a name="to-access-members-of-an-object"></a>オブジェクトのメンバーにアクセスするには

- オブジェクト変数名とメンバー名の`.`間には、メンバーアクセス演算子 () を使用します。

    ```vb
    currentText = newForm.Text
    ```

    メンバーが[共有](../../../../visual-basic/language-reference/modifiers/shared.md)されている場合は、そのメンバーにアクセスするための変数は必要ありません。

## <a name="accessing-members-of-an-object-of-known-type"></a>既知の型のオブジェクトのメンバーへのアクセス

コンパイル時にオブジェクトの型がわかっている場合は、それを参照する変数に*事前バインディング*を使用できます。

#### <a name="to-access-members-of-an-object-for-which-you-know-the-type-at-compile-time"></a>コンパイル時に型がわかっているオブジェクトのメンバーにアクセスするには

1. 変数に割り当てるオブジェクトの型として、オブジェクト変数を宣言します。

    ```vb
    Dim extraForm As System.Windows.Forms.Form
    ```

    で`Option Strict On`は、オブジェクト (また<xref:System.Windows.Forms.Form>はから<xref:System.Windows.Forms.Form>派生した型のオブジェクト) のみを`extraForm`に割り当てることができます。 へ`CType` `extraForm`の拡大変換でクラスまたは構造体を定義している場合は、そのクラスまたは構造体をに割り当てることもできます。 <xref:System.Windows.Forms.Form>

2. オブジェクト変数名とメンバー名の`.`間には、メンバーアクセス演算子 () を使用します。

    ```vb
    extraForm.Show()
    ```

    設定`Option Strict`がどのようなものであっても、 <xref:System.Windows.Forms.Form>クラスに固有のすべてのメソッドとプロパティにアクセスできます。

## <a name="accessing-members-of-an-object-of-unknown-type"></a>不明な型のオブジェクトのメンバーへのアクセス

コンパイル時にオブジェクトの型がわからない場合は、そのオブジェクトを参照する任意の変数に対して*遅延バインディング*を使用する必要があります。

#### <a name="to-access-members-of-an-object-for-which-you-do-not-know-the-type-at-compile-time"></a>コンパイル時に型がわからないオブジェクトのメンバーにアクセスするには

1. オブジェクトの[データ型](../../../../visual-basic/language-reference/data-types/object-data-type.md)であるオブジェクト変数を宣言します。 (変数をと`Object`して宣言することは、と<xref:System.Object?displayProperty=nameWithType>して宣言するのと同じです)。

    ```vb
    Dim someControl As Object
    ```

    で`Option Strict On`は、 <xref:System.Object>クラスで定義されているメンバーのみにアクセスできます。

2. オブジェクト変数名とメンバー名の`.`間には、メンバーアクセス演算子 () を使用します。

    ```vb
    someControl.GetType()
    ```

    オブジェクト変数に割り当てるオブジェクトのメンバーにアクセスできるようにするには、を設定`Option Strict Off`する必要があります。 この場合、コンパイラは、変数に割り当てたオブジェクトによって、特定のメンバーが公開されることを保証できません。 アクセスしようとしたメンバーがオブジェクトによって公開され<xref:System.MemberAccessException>ていない場合は、例外が発生します。

## <a name="see-also"></a>関連項目

- <xref:System.Object>
- <xref:System.Windows.Forms.Form>
- <xref:System.MemberAccessException>
- [オブジェクト変数](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [オブジェクト変数の宣言](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)
- [Object 型](../../../../visual-basic/language-reference/data-types/object-data-type.md)
- [Option Strict ステートメント](../../../../visual-basic/language-reference/statements/option-strict-statement.md)
