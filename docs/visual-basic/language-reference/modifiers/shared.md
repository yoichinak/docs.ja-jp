---
title: Shared
ms.date: 07/20/2015
f1_keywords:
- vb.Shared
helpviewer_keywords:
- Shared keyword [Visual Basic]
- members [Visual Basic], shared
- shared members
- nonshared
- shared [elements VB]
- elements [Visual Basic], shared
ms.assetid: 2bf7cf2c-b0dd-485e-8749-b5d674dab4cd
ms.openlocfilehash: 98fa25d2283408dfb80e82fbc620a1b284e5c530
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349124"
---
# <a name="shared-visual-basic"></a>Shared (Visual Basic)
1 つ以上の宣言されたプログラミング要素が、クラスまたは構造体の特定のインスタンスではなく、クラスまたは構造体全体に関連付けられることを指定します。  
  
## <a name="remarks"></a>Remarks  
  
## <a name="when-to-use-shared"></a>Shared を使用する場面  
 クラスまたは構造体のメンバーを共有すると、各インスタンスが独自のコピーを維持する *nonshared* と異なり、すべてのインスタンスでそれを使用できるようになります。 これは、変数の値をアプリケーション全体に適用する場合などに便利です。 この変数を `Shared` として宣言すると、すべてのインスタンスが同じストレージの場所にアクセスするため、1 つのインスタンスで変数の値が変更されると、すべてのインスタンスが更新された値にアクセスするようになります。  
  
 共有によってメンバーのアクセス レベルが変更されることはありません。 たとえば、クラス メンバーには、共有とプライベート (クラス内からのみアクセス可能)、または非共有とパブリックを指定できます。 詳しくは、「[Visual Basic でのアクセス レベル](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)」をご覧ください。  
  
## <a name="rules"></a>ルール  
  
- **宣言コンテキスト。** `Shared` は、モジュール レベルでのみ使用できます。 つまり、`Shared` 要素の宣言コンテキストは、クラスまたは構造体にする必要があり、ソース ファイル、名前空間、プロシージャにすることはできません。  
  
- **結合された修飾子。** `Shared` は、同じ宣言内で、[Overrides](../../../visual-basic/language-reference/modifiers/overrides.md)、[Overridable](../../../visual-basic/language-reference/modifiers/overridable.md)、[NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md)、[MustOverride](../../../visual-basic/language-reference/modifiers/mustoverride.md)、または [Static](../../../visual-basic/language-reference/modifiers/static.md) と一緒に指定することはできません。  
  
- **アクセス。** 共有要素にアクセスするには、そのクラスまたは構造体の特定のインスタンスの変数名ではなく、そのクラスまたは構造体の名前で修飾します。 その共有メンバーにアクセスするために、クラスまたは構造体のインスタンスを作成する必要もありません。  
  
     次の例では、<xref:System.Double> 構造体によって公開された <xref:System.Double.IsNaN%2A> 共有プロシージャを呼び出しています。  
  
     `If Double.IsNaN(result) Then MsgBox("Result is mathematically undefined.")`  
  
- **暗黙的共有。** [Const ステートメント](../../../visual-basic/language-reference/statements/const-statement.md)では `Shared` 修飾子を使用できませんが、定数は暗黙的に共有されます。 同様に、モジュールまたはインターフェイスのメンバーを `Shared` として宣言できませんが、それらは暗黙的に共有されます。  
  
## <a name="behavior"></a>動作  
  
- **ストレージ。** 共有変数またはイベントは、そのクラスまたは構造体の、作成するインスタンスの数に関係なく、メモリに 1 回だけ格納されます。 同様に、共有プロシージャまたはプロパティは、ローカル変数のセットを 1 つだけ保持します。  
  
- **インスタンス変数によるアクセス。** 共有要素にアクセスするには、そのクラスまたは構造体の特定のインスタンスを格納する変数の名前でそれを修飾します。 これは通常、想定どおりに動作しますが、コンパイラでは警告メッセージが生成され、変数ではなくクラスまたは構造体の名前によってアクセスが行われます。  
  
- **インスタンス式によるアクセス。** クラスまたは構造体のインスタンスを返す式によって共有要素にアクセスする場合、コンパイラでは、式を評価するのではなく、クラスまたは構造体の名前によってアクセスが行われます。 これにより、式でインスタンスを返すことに加えて、他のアクションを実行することを意図した場合に、予期しない結果が発生します。 次に例を示します。  
  
    ```vb
    Sub main()  
        shareTotal.total = 10  
        ' The preceding line is the preferred way to access total.  
        Dim instanceVar As New shareTotal  
        instanceVar.total += 100  
        ' The preceding line generates a compiler warning message and  
        ' accesses total through class shareTotal instead of through  
        ' the variable instanceVar. This works as expected and adds  
        ' 100 to total.  
        returnClass().total += 1000  
        ' The preceding line generates a compiler warning message and  
        ' accesses total through class shareTotal instead of calling  
        ' returnClass(). This adds 1000 to total but does not work as  
        ' expected, because the MsgBox in returnClass() does not run.  
        MsgBox("Value of total is " & CStr(shareTotal.total))  
    End Sub  
    Public Function returnClass() As shareTotal  
        MsgBox("Function returnClass() called")  
        Return New shareTotal  
    End Function  
    Public Class shareTotal  
        Public Shared total As Integer  
    End Class  
    ```  
  
     前の例では、コードがインスタンス経由で共有変数 `total` にアクセスするどちらのときも、コンパイラによって警告メッセージが生成されます。 いずれの場合も、クラス `shareTotal` 経由で直接アクセスが行われ、インスタンスが使用されません。 プロシージャ `returnClass` への意図した呼び出しの場合、これは `returnClass` への呼び出しも生成されないことを意味するため、"Function returnClass() called" を表示する追加のアクションが実行されません。  
  
 `Shared` 修飾子は、次のコンテキストで使用できます。  
  
 [Dim ステートメント](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [Event ステートメント](../../../visual-basic/language-reference/statements/event-statement.md)  
  
 [Function ステートメント](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [Operator ステートメント](../../../visual-basic/language-reference/statements/operator-statement.md)  
  
 [Property ステートメント](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [Sub ステートメント](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a>関連項目

- [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md)
- [Static](../../../visual-basic/language-reference/modifiers/static.md)
- [Visual Basic における有効期間](../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md)
- [手順](../../../visual-basic/programming-guide/language-features/procedures/index.md)
- [構造体](../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [クラスとオブジェクト](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
