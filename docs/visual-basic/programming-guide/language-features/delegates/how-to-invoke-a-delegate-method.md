---
title: '方法: デリゲート メソッド (Visual Basic) を呼び出す'
ms.date: 07/20/2015
ms.assetid: b56866ae-abf9-4a5a-a855-486359455e9c
ms.openlocfilehash: ac3e32010e7c20ba76e39915d694b11ab3a65d40
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59319613"
---
# <a name="how-to-invoke-a-delegate-method-visual-basic"></a>方法: デリゲート メソッド (Visual Basic) を呼び出す
この例では、メソッドをデリゲートに関連付け、デリゲートからメソッドを呼び出す方法を示します。  
  
### <a name="create-the-delegate-and-matching-procedures"></a>デリゲートと一致するプロシージャを作成します。  
  
1. という名前のデリゲートを作成する`MySubDelegate`します。  
  
    ```  
    Delegate Sub MySubDelegate(ByVal x As Integer)  
    ```  
  
2. デリゲートと同じシグネチャを持つメソッドを含むクラスを宣言します。  
  
    ```  
    Class class1  
        Sub Sub1(ByVal x As Integer)  
            MsgBox("The value of x is: " & CStr(x))  
        End Sub  
    End Class  
    ```  
  
3. デリゲートのインスタンスを作成し、組み込みを呼び出すことによって、デリゲートに関連付けられているメソッドを呼び出し、メソッドを定義`Invoke`メソッド。  
  
    ```  
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
