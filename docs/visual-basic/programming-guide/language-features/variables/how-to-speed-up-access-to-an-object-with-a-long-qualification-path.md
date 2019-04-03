---
title: '方法: 長い修飾パス (Visual Basic) のオブジェクトへのアクセスを高速化します。'
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], accessing
- variables [Visual Basic], object
- With statement [Visual Basic]
- With block
- object variables [Visual Basic], accessing
ms.assetid: 3eb7657f-c9fe-4e05-8bc3-4bb14d5ae585
ms.openlocfilehash: b10876c22d2f6dd5832baa0d498db7c4205a3fcb
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58816292"
---
# <a name="how-to-speed-up-access-to-an-object-with-a-long-qualification-path-visual-basic"></a>方法: 長い修飾パス (Visual Basic) のオブジェクトへのアクセスを高速化します。
いくつかのメソッドとプロパティの修飾パスを必要とするオブジェクトを頻繁にアクセスする場合は、修飾パスを繰り返さないこと、コードを短縮できます。  
  
 修飾パスの繰り返しを回避できます 2 つの方法はあります。 オブジェクトを変数に割り当てることができますかで使用できる、 `With`.`End With`ブロックします。  
  
### <a name="to-speed-up-access-to-a-heavily-qualified-object-by-assigning-it-to-a-variable"></a>高速化するアクセス頻度の高い修飾オブジェクトを変数に代入することで  
  
1.  頻繁にアクセスしているオブジェクトの型の変数を宣言します。 宣言の初期化の部分で修飾パスを指定します。  
  
    ```  
    Dim ctrlActv As Control = someForm.ActiveForm.ActiveControl  
    ```  
  
2.  オブジェクトのメンバーにアクセスするのにには、変数を使用します。  
  
    ```  
    ctrlActv.Text = "Test"  
    ctrlActv.Location = New Point(100, 100)  
    ctrlActv.Show()  
    ```  
  
### <a name="to-speed-up-access-to-a-heavily-qualified-object-by-using-a-withend-with-block"></a>高速化するアクセス頻度の高い修飾オブジェクトに、With を使用しています.End With ブロック  
  
1.  修飾パスを配置、`With`ステートメント。  
  
    ```  
    With someForm.ActiveForm.ActiveControl  
    ```  
  
2.  内のオブジェクトのメンバーにアクセス、`With`前に、ブロック、`End With`ステートメント。  
  
    ```  
        .Text = "Test"  
        .Location = New Point(100, 100)  
        .Show()  
    End With  
    ```  
  
## <a name="see-also"></a>関連項目

- [オブジェクト変数](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [With...End With ステートメント](../../../../visual-basic/language-reference/statements/with-end-with-statement.md)
