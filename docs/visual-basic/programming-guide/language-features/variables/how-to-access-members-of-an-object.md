---
title: '方法: オブジェクト (Visual Basic) のメンバーへのアクセス'
ms.date: 07/20/2015
helpviewer_keywords:
- members [Visual Basic], accessing
- object variables [Visual Basic], accessing members
ms.assetid: a0072514-6a79-4dd6-8d03-ca8c13e61ddc
ms.openlocfilehash: 46c5eb9bc79b3a408a5a4fc9f40fee7391937c58
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2019
ms.locfileid: "64663601"
---
# <a name="how-to-access-members-of-an-object-visual-basic"></a>方法: オブジェクト (Visual Basic) のメンバーへのアクセス
オブジェクトを参照するオブジェクト変数がある場合は、多くの場合、メソッド、プロパティ、フィールド、イベントなど、そのオブジェクトのメンバーを操作します。 たとえば、1 回作成した新しい<xref:System.Windows.Forms.Form>オブジェクトを設定することがあります、<xref:System.Windows.Forms.Control.Text%2A>プロパティまたは呼び出しの<xref:System.Windows.Forms.Control.Focus%2A>メソッド。  
  
## <a name="accessing-members"></a>メンバーへのアクセス  
 オブジェクトのメンバーにアクセスするを参照する変数を使用します。  
  
#### <a name="to-access-members-of-an-object"></a>オブジェクトのメンバーにアクセスするには  
  
- メンバー アクセス演算子を使用して (`.`) オブジェクトの変数名とメンバー名の間。  
  
    ```  
    currentText = newForm.Text  
    ```  
  
     メンバーが場合[Shared](../../../../visual-basic/language-reference/modifiers/shared.md)変数にアクセスする必要はありません。  
  
## <a name="accessing-members-of-an-object-of-known-type"></a>既知の型のオブジェクトのメンバーへのアクセス  
 コンパイル時に、オブジェクトの型を認識する場合を使用できます*事前バインディング*変数に参照されています。  
  
#### <a name="to-access-members-of-an-object-for-which-you-know-the-type-at-compile-time"></a>コンパイル時に、型を認識するオブジェクトのメンバーにアクセスするには  
  
1. 変数に代入するオブジェクトの型のオブジェクト変数を宣言します。  
  
    ```  
    Dim extraForm As System.Windows.Forms.Form  
    ```  
  
     `Option Strict On`、のみ割り当てることができます<xref:System.Windows.Forms.Form>オブジェクト (から派生した型のオブジェクトまたは<xref:System.Windows.Forms.Form>) に`extraForm`します。 クラスまたは拡大と構造体を定義しているかどうか`CType`への変換<xref:System.Windows.Forms.Form>、そのクラスを割り当てるか、構造体をすることができますも`extraForm`します。  
  
2. メンバー アクセス演算子を使用して (`.`) オブジェクトの変数名とメンバー名の間。  
  
    ```  
    extraForm.Show()  
    ```  
  
     メソッドとプロパティに固有のすべてにアクセスすることができます、<xref:System.Windows.Forms.Form>何であっても、クラス、`Option Strict`設定です。  
  
## <a name="accessing-members-of-an-object-of-unknown-type"></a>不明な型のオブジェクトのメンバーへのアクセス  
 使用する必要があるコンパイル時に、オブジェクトの型がわからない場合*遅延バインディング*それを参照しているすべての変数にします。  
  
#### <a name="to-access-members-of-an-object-for-which-you-do-not-know-the-type-at-compile-time"></a>対象のわからない型コンパイル時にオブジェクトのメンバーにアクセスするには  
  
1. オブジェクト変数を宣言、 [Object Data Type](../../../../visual-basic/language-reference/data-types/object-data-type.md)します。 (として変数を宣言する`Object`として宣言することと同じ<xref:System.Object?displayProperty=nameWithType>)。  
  
    ```  
    Dim someControl As Object  
    ```  
  
     `Option Strict On`で定義されているメンバーのみにアクセスすることができます、<xref:System.Object>クラス。  
  
2. メンバー アクセス演算子を使用して (`.`) オブジェクトの変数名とメンバー名の間。  
  
    ```  
    someControl.GetType()  
    ```  
  
     オブジェクト変数に代入する任意のオブジェクトのメンバーにアクセスできるようにするには、設定する必要があります`Option Strict Off`します。 これを行うと、コンパイラが特定のメンバーが、変数に代入するオブジェクトによって公開されることを保証することはできません。 オブジェクトが、アクセスしようとするメンバーを公開しない場合、<xref:System.MemberAccessException>例外が発生します。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Object>
- <xref:System.Windows.Forms.Form>
- <xref:System.MemberAccessException>
- [オブジェクト変数](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [オブジェクト変数の宣言](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)
- [Object 型](../../../../visual-basic/language-reference/data-types/object-data-type.md)
- [Option Strict ステートメント](../../../../visual-basic/language-reference/statements/option-strict-statement.md)
