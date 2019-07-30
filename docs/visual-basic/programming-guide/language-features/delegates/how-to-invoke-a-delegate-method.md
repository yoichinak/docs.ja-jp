---
title: '方法: デリゲートメソッドの呼び出し (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: b56866ae-abf9-4a5a-a855-486359455e9c
ms.openlocfilehash: c2bdb65c9d060e854db3319e4aa5b2e93b9681af
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/30/2019
ms.locfileid: "68629593"
---
# <a name="how-to-invoke-a-delegate-method-visual-basic"></a>方法: デリゲートメソッドの呼び出し (Visual Basic)

この例では、メソッドをデリゲートに関連付けて、デリゲートを使用してそのメソッドを呼び出す方法を示します。

### <a name="create-the-delegate-and-matching-procedures"></a>デリゲートと一致するプロシージャを作成する

1. という名前`MySubDelegate`のデリゲートを作成します。

    ```vb
    Delegate Sub MySubDelegate(ByVal x As Integer)
    ```

2. デリゲートと同じシグネチャを持つメソッドを含むクラスを宣言します。

    ```vb
    Class class1
        Sub Sub1(ByVal x As Integer)
            MsgBox("The value of x is: " & CStr(x))
        End Sub
    End Class
    ```

3. デリゲートのインスタンスを作成し、組み込み`Invoke`メソッドを呼び出すことによって、デリゲートに関連付けられているメソッドを呼び出すメソッドを定義します。

    ```vb
    Protected Sub DelegateTest()
        Dim c1 As New class1
        ' Create an instance of the delegate.
        Dim msd As MySubDelegate = AddressOf c1.Sub1
        ' Call the method.
        msd.Invoke(10)
    End Sub
    ```

## <a name="see-also"></a>関連項目

- [Delegate ステートメント](../../../../visual-basic/language-reference/statements/delegate-statement.md)
- [デリゲート](../../../../visual-basic/programming-guide/language-features/delegates/index.md)
- [イベント](../../../../visual-basic/programming-guide/language-features/events/index.md)
- [マルチスレッド アプリケーション](../../../../standard/threading/using-threads-and-threading.md)
