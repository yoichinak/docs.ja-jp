---
title: Shared (Visual Basic)
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
ms.openlocfilehash: fd43ef7cb5c16995fff87a65fc0f0974d8f4a47d
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2019
ms.locfileid: "64647704"
---
# <a name="shared-visual-basic"></a>Shared (Visual Basic)
1 つまたは複数の宣言されたプログラミング要素がクラスまたは構造体全体、クラスまたは構造体の特定のインスタンスではなくと関連付けられていることを指定します。  
  
## <a name="remarks"></a>Remarks  
  
## <a name="when-to-use-shared"></a>共有を使用する場合  
 すべてのインスタンスを使用できるクラスまたは構造体のメンバーを共有するようになく*非共有*、各インスタンスが独自のコピーを保持します。 これは、変数の値は、アプリケーション全体に適用される場合に便利です。 その変数を宣言する場合`Shared`すべてのインスタンスが、同じストレージの場所にアクセスし、更新された値にアクセスするすべてのインスタンス 1 つのインスタンスには、変数の値が変更された場合。  
  
 共有メンバーのアクセス レベルは変更されません。 たとえば、クラス メンバーを共有できるとプライベート (クラス内からのみアクセスできます)、または非共有と公開。 詳細については、[ Visual Basic のアクセス レベル](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)を参照してください。  
  
## <a name="rules"></a>ルール  
  
- **宣言コンテキスト。** `Shared` は、モジュール レベルでのみ使用できます。 これは、意味の宣言のコンテキストを`Shared`要素がクラスまたは構造体にある必要があるあり、ソース ファイル、名前空間、またはプロシージャにすることはできません。  
  
- **結合された修飾子。** 指定することはできません`Shared`と共に[オーバーライド](../../../visual-basic/language-reference/modifiers/overrides.md)、 [Overridable](../../../visual-basic/language-reference/modifiers/overridable.md)、 [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md)、 [MustOverride](../../../visual-basic/language-reference/modifiers/mustoverride.md)、または[静的](../../../visual-basic/language-reference/modifiers/static.md)同じ宣言内。  
  
- **アクセスします。** 共有要素にアクセスするには、そのクラスまたは構造体の名前を持つ、そのクラスまたは構造体の特定のインスタンスの変数名ではなくを修飾します。 でも、クラスまたはその共有メンバーにアクセスする構造体のインスタンスを作成する必要はありません。  
  
     次の例では共有のプロシージャ<xref:System.Double.IsNaN%2A>によって公開されている、<xref:System.Double>構造体。  
  
     `If Double.IsNaN(result) Then MsgBox("Result is mathematically undefined.")`  
  
- **暗黙の型を共有します。** 使用することはできません、`Shared`修飾子、 [Const ステートメント](../../../visual-basic/language-reference/statements/const-statement.md)定数が暗黙的に共有しますが、できます。 同様に、するには、モジュールまたはインターフェイスのメンバーを宣言することはできません`Shared`、暗黙的に共有しますが、できます。  
  
## <a name="behavior"></a>動作  
  
- **記憶域。** 共有変数またはイベントは、そのクラスまたは構造体の作成の数またはいくつかのインスタンスに関係なく、1 回だけメモリに格納されます。 同様に、共有プロシージャまたはプロパティは、ローカル変数の 1 つだけのセットを保持します。  
  
- **インスタンス変数を通じてアクセスします。** クラスまたは構造体の特定のインスタンスを格納する変数の名前で修飾して、共有要素にアクセスすることになります。 通常、これは期待どおりに動作をコンパイラは警告メッセージを生成し、変数ではなく、クラスまたは構造体の名前を使ってアクセスします。  
  
- **インスタンス式からアクセスします。** 共有要素をそのクラスまたは構造体のインスタンスを返す式を使用してアクセスする場合、コンパイラで式を評価するのではなく、クラスまたは構造体の名前でアクセスを行います。 その他のアクション、インスタンスを返すことを実行する式を意図した場合、予期しない結果が生成されます。 次に例を示します。  
  
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
  
     前の例では、コンパイラ警告メッセージを生成、コード共有変数にアクセスする両方の回`total`インスタンスを使用します。 クラスから直接アクセスは、各ケース`shareTotal`を行わないと、インスタンスを使用します。 プロシージャに目的の呼び出しの場合`returnClass`、つまりへの呼び出しも生成しません`returnClass`ので、"関数 returnClass() と呼ばれる"を表示する追加のアクションは実行されません。  
  
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
- [Visual Basic での有効期間](../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md)
- [プロシージャ](../../../visual-basic/programming-guide/language-features/procedures/index.md)
- [構造体](../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [クラスとオブジェクト](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
