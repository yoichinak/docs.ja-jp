---
title: インスタンスを経由する共有メンバーへのアクセスです。正規の式は評価されません。
ms.date: 07/20/2015
f1_keywords:
- vbc42025
- BC42025
helpviewer_keywords:
- BC42025
ms.assetid: db3337e5-c349-42bf-86df-d9c1e00952a5
ms.openlocfilehash: 773a97c301e7cb5bec0234ae466d487ec9716437
ms.sourcegitcommit: d7c298f6c2e3aab0c7498bfafc0a0a94ea1fe23e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/10/2019
ms.locfileid: "72250345"
---
# <a name="access-of-shared-member-through-an-instance-qualifying-expression-will-not-be-evaluated"></a>インスタンスを経由する共有メンバーへのアクセスです。正規の式は評価されません。

クラスまたは構造体のインスタンス変数は、そのクラスまたは構造体で定義されている @no__t 0 の変数、プロパティ、プロシージャ、またはイベントにアクセスするために使用されます。 この警告は、クラスまたは構造体の暗黙的に共有されるメンバー (定数、列挙型、または入れ子になったクラスまたは構造体) へのアクセスにインスタンス変数が使用されている場合にも発生することがあります。

メンバーを共有する目的は、そのメンバーのコピーを1つだけ作成し、そのコピーを、宣言されているクラスまたは構造体のすべてのインスタンスで使用できるようにすることです。 クラスまたは構造体の個々のインスタンスを保持する変数を使用するのではなく、クラスまたは構造体の名前を使用して @no__t 0 のメンバーにアクセスするために、この目的と一貫性があります。

インスタンス変数を使用して @no__t 0 のメンバーにアクセスすると、メンバーが-1 @no__t ことを隠すことで、コードを理解しやすくなります。 さらに、このようなアクセスが、共有メンバーのインスタンスを返す @no__t 0 プロシージャなどの他のアクションを実行する式の一部である場合、Visual Basic は式およびそれ以外で実行されるその他のアクションをバイパスします。  
  
詳細と例については、「[共有](../modifiers/shared.md)」を参照してください。  
  
既定では、このメッセージは警告です。 警告を表示しない方法や、警告をエラーとして扱う方法の詳細については、「 [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic)」を参照してください。  
  
**エラー ID:** BC42025  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
次の例に示すように、@no__t 0 のメンバーを定義するクラスまたは構造体の名前を使用してアクセスします。
  
```vb
Public Class TestClass
    Public Shared Sub SayHello()
        MsgBox("Hello")
    End Sub
End Class
  
Module Program
    Public Sub Main()  
        ' Access a shared method through an instance variable.  
        ' This generates a warning.  
        Dim tc As New TestClass()
        tc.SayHello()
  
        ' Access a shared method by using the class name.  
        ' This does not generate a warning.  
        TestClass.SayHello()
    End Sub  
End Module  
```  
  
> [!NOTE]
> 2つのプログラミング要素が同じ名前の場合に、スコープの効果に関する警告を出します。 前の例では、`Dim testClass as testClass = Nothing` を使用してインスタンスを宣言する場合、コンパイラは、クラス名を使用してメソッドへのアクセスとして `testClass.sayHello()` の呼び出しを処理し、警告は発生しません。
  
## <a name="see-also"></a>関連項目

- [Shared](../modifiers/shared.md)
- [Visual Basic 内のスコープ](../../programming-guide/language-features/declared-elements/scope.md)
