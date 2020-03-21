---
title: 継承の基本
ms.date: 07/20/2015
helpviewer_keywords:
- derived classes [Visual Basic], inheritance
- MyClass keyword [Visual Basic], using
- MyBase keyword [Visual Basic], using
- Inherits statement [Visual Basic], inheritance
- overriding, Overridable keyword
- MustInherit keyword [Visual Basic], using
- Overrides keyword [Visual Basic], using
- inheritance
- MustInherit classes [Visual Basic]
- MustOverride keyword [Visual Basic], using
- classes [Visual Basic], derived
- NotInheritable keyword [Visual Basic], using
- base classes [Visual Basic], extending properties and methods [Visual Basic]
- NotOverridable keyword [Visual Basic], using
- base classes [Visual Basic], inheritance
- abstract classes [Visual Basic], inheritance
- overriding, Overrides keyword
ms.assetid: dfc8deba-f5b3-4d1d-a937-7cb826446fc5
ms.openlocfilehash: 89fcf2a14d8938d536aa72628218242811baa1a2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/14/2020
ms.locfileid: "79401461"
---
# <a name="inheritance-basics-visual-basic"></a>継承の基本 (Visual Basic)

この`Inherits`ステートメントは、*基本*クラス と呼ばれる既存のクラスに基づいて、*派生クラス*と呼ばれる新しいクラスを宣言するために使用されます。 派生クラスは、基本クラスで定義されたプロパティ、メソッド、イベント、フィールド、および定数を継承し、拡張できます。 次のセクションでは、継承の規則と、クラスの継承または継承方法を変更するために使用できる修飾子について説明します。

- デフォルトでは、キーワードでマークしない限り、すべてのクラス`NotInheritable`を継承できます。 クラスは、プロジェクト内の他のクラスから継承することも、プロジェクトが参照する他のアセンブリのクラスから継承することもできます。

- 複数の継承を許可する言語とは異なり、Visual Basic ではクラス内で単一の継承のみが許可されます。つまり、派生クラスは 1 つの基本クラスしか持てないです。 クラスでは多重継承は許可されていませんが、クラスは複数のインターフェイスを実装できるため、同じ目的を効果的に実現できます。

- 制限された項目が基本クラスに公開されないようにするには、派生クラスのアクセス型は、基本クラスと同じか、その基底クラスよりも制限の厳しい型である必要があります。 たとえば、クラスは`Public`クラスまたは`Friend`クラスを`Private`継承できず、クラス`Friend`はクラスを`Private`継承できません。

## <a name="inheritance-modifiers"></a>継承修飾子

Visual Basic では、継承をサポートするために、次のクラス レベルのステートメントと修飾子が導入されています。

- `Inherits`文 — 基本クラスを指定します。

- `NotInheritable`修飾子 — プログラマがクラスを基本クラスとして使用できないようにします。

- `MustInherit`modifier — クラスが基本クラスとしてのみ使用されることを指定します。 クラスの`MustInherit`インスタンスを直接作成することはできません。派生クラスの基本クラスインスタンスとしてのみ作成できます。 (C++ や C# などの他のプログラミング言語では、*抽象クラス*という用語を使用してこのようなクラスを記述します)。

## <a name="overriding-properties-and-methods-in-derived-classes"></a>派生クラスでのプロパティとメソッドのオーバーライド

既定では、派生クラスは基本クラスからプロパティとメソッドを継承します。 継承されたプロパティまたはメソッドが派生クラスで異なる動作をする*必要がある場合*は、オーバーライドできます。 つまり、派生クラスでメソッドの新しい実装を定義できます。 プロパティやメソッドのオーバーライド方法を制御するには、次の修飾子を使用します。

- `Overridable`— クラス内のプロパティまたはメソッドを派生クラスでオーバーライドできます。

- `Overrides`— 基本クラス`Overridable`で定義されたプロパティまたはメソッドをオーバーライドします。

- `NotOverridable`— 継承クラスでプロパティまたはメソッドがオーバーライドされないようにします。 既定では、`Public`メソッドは`NotOverridable`です。

- `MustOverride`— 派生クラスがプロパティまたはメソッドをオーバーライドする必要があります。 キーワードを`MustOverride`使用する場合、メソッド定義は`Sub`、 、`Function`または`Property`ステートメントだけで構成されます。 他のステートメントは許可されず、具体的にはステートメントや`End Sub``End Function`ステートメントはありません。 `MustOverride`メソッドはクラスで`MustInherit`宣言する必要があります。

給与計算を処理するクラスを定義するとします。 一般的な週の`Payroll`給与を計算する`RunPayroll`メソッドを含むジェネリック クラスを定義できます。 その後、従業員`Payroll`の賞与を配布するときに使用できる、`BonusPayroll`より専門的なクラスの基本クラスとして使用できます。

クラス`BonusPayroll`は、基本`Payroll`クラスで定義されているメソッド`PayEmployee`を継承し、オーバーライドできます。

次の例では、基本クラスと`Payroll,`、継承されたメソッド`BonusPayroll`をオーバーライドする派生クラス を定義`PayEmployee`します。 プロシージャ は`RunPayroll`、`Payroll`オブジェクトと`BonusPayroll`オブジェクトを作成し、`Pay`両方のオブジェクトの`PayEmployee`メソッドを実行する関数 に渡します。

[!code-vb[VbVbalrOOP#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#28)]

## <a name="the-mybase-keyword"></a>マイベースキーワード

キーワード`MyBase`は、クラスの現在のインスタンスの基本クラスを参照するオブジェクト変数のように動作します。 `MyBase`は、派生クラスでオーバーライドまたはシャドウされる基本クラスのメンバーにアクセスするために頻繁に使用されます。 特に、`MyBase.New`派生クラスのコンストラクターから基本クラスコンストラクターを明示的に呼び出すために使用されます。

たとえば、基本クラスから継承されたメソッドをオーバーライドする派生クラスをデザインするとします。 オーバーライドされたメソッドは、基本クラスのメソッドを呼び出し、次のコードに示すように戻り値を変更できます。

[!code-vb[VbVbalrOOP#109](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#109)]

を使用`MyBase`する場合の制限事項を次に示します。

- `MyBase`は、直接の基本クラスとその継承されたメンバーを指します。 クラスのメンバーにアクセス`Private`するために使用することはできません。

- `MyBase`はキーワードであり、実際のオブジェクトではありません。 `MyBase`変数に代入したり、プロシージャに渡したり、比較で`Is`使用することはできません。

- 修飾する`MyBase`メソッドは、直接の基本クラスで定義する必要はありません。代わりに、間接的に継承された基本クラスで定義できます。 修飾された参照を正しくコンパイル`MyBase`するためには、一部の基本クラスに、呼び出しに表示されるパラメーターの名前と型に一致するメソッドが含まれている必要があります。

- 基本クラスの`MyBase`メソッドを`MustOverride`呼び出すためには使用できません。

- `MyBase`自身を修飾するために使用することはできません。 したがって、次のコードは無効です。

  `MyBase.MyBase.BtnOK_Click()`

- `MyBase`モジュールでは使用できません。

- `MyBase`基本クラスが別のアセンブリにある場合と同様`Friend`にマークされている基本クラス のメンバーにアクセスするためには使用できません。

詳細と別の例については、「[方法 : 派生クラスによって非表示になっている変数にアクセス](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-access-a-variable-hidden-by-a-derived-class.md)する 」を参照してください。

## <a name="the-myclass-keyword"></a>マイクラスキーワード

キーワード`MyClass`は、最初に実装されたクラスの現在のインスタンスを参照するオブジェクト変数のように動作します。 `MyClass`は`Me`似ていますが、メソッドやプロパティの`MyClass`呼び出しはすべて[NotOverridable](../../../../visual-basic/language-reference/modifiers/notoverridable.md)と見なされます。 したがって、メソッドまたはプロパティは、派生クラスでオーバーライドしても影響を受けません。

- `MyClass`はキーワードであり、実際のオブジェクトではありません。 `MyClass`変数に代入したり、プロシージャに渡したり、比較で`Is`使用することはできません。

- `MyClass`は、含まれているクラスとその継承されたメンバを指します。

- `MyClass`は`Shared`、メンバーの修飾子として使用できます。

- `MyClass`メソッド内では`Shared`使用できませんが、インスタンス メソッド内でクラスの共有メンバーにアクセスするために使用できます。

- `MyClass`標準モジュールでは使用できません。

- `MyClass`は、基本クラスで定義され、そのクラスで提供されるメソッドの実装を持たないメソッドを修飾するために使用できます。 このような参照は、`MyBase.`*メソッド*と同じ意味を持ちます。

次の例では、 `Me` `MyClass`と を比較します。

```vb
Class baseClass
    Public Overridable Sub testMethod()
        MsgBox("Base class string")
    End Sub
    Public Sub useMe()
        ' The following call uses the calling class's method, even if
        ' that method is an override.
        Me.testMethod()
    End Sub
    Public Sub useMyClass()
        ' The following call uses this instance's method and not any
        ' override.
        MyClass.testMethod()
    End Sub
End Class
Class derivedClass : Inherits baseClass
    Public Overrides Sub testMethod()
        MsgBox("Derived class string")
    End Sub
End Class
Class testClasses
    Sub startHere()
        Dim testObj As derivedClass = New derivedClass()
        ' The following call displays "Derived class string".
        testObj.useMe()
        ' The following call displays "Base class string".
        testObj.useMyClass()
    End Sub
End Class
```

`testMethod`オーバーライドでも`derivedClass`、 キーワードを`MyClass``useMyClass`オーバーライドすると、オーバーライドの影響が null になり、コンパイラは、基本クラスのバージョンの`testMethod`を解決します。

## <a name="see-also"></a>関連項目

- [Inherits ステートメント](../../../../visual-basic/language-reference/statements/inherits-statement.md)
- [Me、My、MyBase、および MyClass](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
