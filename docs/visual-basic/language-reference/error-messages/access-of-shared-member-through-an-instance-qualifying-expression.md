---
title: インスタンスを経由する共有メンバーへのアクセスです。正規の式は評価されません。
ms.date: 07/20/2015
f1_keywords:
- vbc42025
- BC42025
helpviewer_keywords:
- BC42025
ms.assetid: db3337e5-c349-42bf-86df-d9c1e00952a5
ms.openlocfilehash: 3174d463744303e8c90ed0b2e1a4d86ed08fbcfb
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69947696"
---
# <a name="access-of-shared-member-through-an-instance-qualifying-expression-will-not-be-evaluated"></a>インスタンスを経由する共有メンバーへのアクセスです。正規の式は評価されません。
クラスまたは構造体のインスタンス変数は、そのクラスまた`Shared`は構造体で定義されている変数、プロパティ、プロシージャ、またはイベントにアクセスするために使用されます。 この警告は、クラスまたは構造体の暗黙的に共有されるメンバー (定数、列挙型、または入れ子になったクラスまたは構造体) へのアクセスにインスタンス変数が使用されている場合にも発生することがあります。  
  
 メンバーを共有する目的は、そのメンバーのコピーを1つだけ作成し、そのコピーを、宣言されているクラスまたは構造体のすべてのインスタンスで使用できるようにすることです。 クラスまたは構造体の個々のインスタンス`Shared`を保持する変数ではなく、クラスまたは構造体の名前を使用してメンバーにアクセスするために、この目的と一貫性があります。  
  
 インスタンス変数を使用して`Shared`メンバーにアクセスすると、メンバーがであるという事実を隠ぺいすることで、コードを理解しづらくなる可能性があります。`Shared` さらに、このようなアクセスが、共有メンバーのインスタンスを返す`Function`プロシージャなど、他のアクションを実行する式の一部である場合、Visual Basic は式およびそれ以外で実行されるその他のアクションをバイパスします。  
  
 詳細と例については、「[共有](../../../visual-basic/language-reference/modifiers/shared.md)」を参照してください。  
  
 既定では、このメッセージは警告です。 警告を表示しない方法や、警告をエラーとして扱う方法の詳細については、「 [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic)」を参照してください。  
  
 **エラー ID:** BC42025  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
- 次の例に示すように、アクセスする`Shared`メンバーを定義するクラスまたは構造体の名前を使用します。  
  
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
> 2つのプログラミング要素が同じ名前の場合に、スコープの効果に関する警告を出します。 前の例では、を使用`Dim testClass as testClass = Nothing`してインスタンスを宣言する場合、コンパイラはの`testClass.sayHello()`呼び出しをクラス名を通じてメソッドのアクセスとして処理しますが、警告は発生しません。  
  
## <a name="see-also"></a>関連項目

- [Shared](../../../visual-basic/language-reference/modifiers/shared.md)
- [Visual Basic 内のスコープ](../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)
