---
title: インスタンスを経由する共有メンバーへのアクセスです。正規の式は評価されません。
ms.date: 07/20/2015
f1_keywords:
- vbc42025
- BC42025
helpviewer_keywords:
- BC42025
ms.assetid: db3337e5-c349-42bf-86df-d9c1e00952a5
ms.openlocfilehash: 8e6ddab16c59d7ce95d96b377e3f372f6ebe5278
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61751606"
---
# <a name="access-of-shared-member-through-an-instance-qualifying-expression-will-not-be-evaluated"></a>インスタンスを経由する共有メンバーへのアクセスです。正規の式は評価されません。
クラスまたは構造体のインスタンス変数を使用するアクセス、`Shared`変数、プロパティ、プロシージャ、またはそのクラスまたは構造体で定義されているイベント。 この警告は、インスタンス変数をクラスまたは構造体、定数または列挙型、または入れ子になったクラスまたは構造体などの暗黙的な共有メンバーへのアクセスに使用する場合にも発生します。  
  
 メンバーの共有の目的は、そのメンバーのコピーが 1 つだけを作成し、その 1 つのコピーのクラスまたは構造体が宣言されているすべてのインスタンスを使用できるようにすること。 アクセスするには、この目的で矛盾がある、`Shared`メンバーがそのクラスまたは構造体の個々 のインスタンスを保持する変数ではなく、クラスまたは構造の名前を使用します。  
  
 アクセス、`Shared`インスタンス変数によるメンバーが難しく、コード、メンバーであるという事実を隠すことで理解する`Shared`します。 さらに、このようなアクセスが式の一部である場合、ように、他のアクションを実行するには`Function`共有メンバーのインスタンスを返すプロシージャでは、Visual Basic は、式とそれ以外の場合、その他のアクションをバイパスします。  
  
 詳細と例では、次を参照してください。 [Shared](../../../visual-basic/language-reference/modifiers/shared.md)します。  
  
 既定では、このメッセージは警告です。 警告を表示しない方法や、警告をエラーとして扱う方法の詳細については、「 [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic)」を参照してください。  
  
 **エラー ID:** BC42025  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
- クラスまたは定義する構造体の名前を使用して、`Shared`に次の例に示すように、アクセスするメンバー。  
  
```vb  
Public Class testClass  
    Public Shared Sub sayHello()  
        MsgBox("Hello")  
    End Sub  
End Class  
  
Module testModule  
    Public Sub Main()  
        ' Access a shared method through an instance variable.  
        ' This generates a warning.  
        Dim tc As New testClass  
        tc.sayHello()  
  
        ' Access a shared method by using the class name.  
        ' This does not generate a warning.  
        testClass.sayHello()  
    End Sub  
End Module  
```  
  
> [!NOTE]
>  2 つのプログラミング要素が同じ名前を持つ場合は、スコープの影響についてアラートが。 使用してインスタンスを宣言する場合、前の例で`Dim testClass as testClass = Nothing`、コンパイラを呼び出す`testClass.sayHello()`クラス名、および警告なしでメソッドのアクセスが発生するとします。  
  
## <a name="see-also"></a>関連項目

- [Shared](../../../visual-basic/language-reference/modifiers/shared.md)
- [Visual Basic におけるスコープ](../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)
