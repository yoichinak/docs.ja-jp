---
title: 継承の基本 (Visual Basic)
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
ms.openlocfilehash: a31f69459465368dc7519b5126c6c4eb72e25d29
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2019
ms.locfileid: "64663006"
---
# <a name="inheritance-basics-visual-basic"></a>継承の基本 (Visual Basic)
`Inherits`ステートメントを使用して、という新しいクラスを宣言、*クラスを派生*と呼ばれる、既存のクラスに基づいて、*基本クラス*します。 派生クラスでは、継承、およびプロパティ、メソッド、イベント、フィールド、および基底クラスで定義された定数は、拡張できます。 次のセクションでは、いくつかの継承のルールについて説明し、方法クラスを変更する際、修飾子を継承または継承されます。  
  
- 既定では、すべてのクラスは継承とマークされていない限り、`NotInheritable`キーワード。 クラスは、プロジェクト内の他のクラスとは、プロジェクトを参照するその他のアセンブリのクラスから継承できます。  
  
- 複数の継承を許可する言語とは異なり Visual Basic では単一継承のみです。派生クラスでは、1 つだけの基本クラスを持つことができます。 クラスには、多重継承することはできません、クラスは、同じ結果を効果的に実現できますが、複数のインターフェイスを実装できます。  
  
- 基底クラスでの制限付きの項目を公開することを防ぐためには、派生クラスのアクセスの種類に等しくないか、基底クラスよりもより制限の厳しいする必要があります。 など、`Public`クラスは継承できません、`Friend`または`Private`クラス、および`Friend`クラスは継承できません、`Private`クラス。  
  
## <a name="inheritance-modifiers"></a>継承修飾子  
 Visual Basic では、次のクラス レベルのステートメントと継承をサポートする修飾子が導入されています。  
  
- `Inherits` ステートメント: 基本クラスを指定します。  
  
- `NotInheritable` 修飾子: プログラマがクラスの基底クラスとして使用するを防ぎます。  
  
- `MustInherit` 修飾子: のみ、基本クラスとして使用するため、クラスは意図するを指定します。 インスタンス`MustInherit`クラスを直接作成することはできません。 できますのみ作成する必要が派生クラスの基本クラスのインスタンス。 (C++ などの他のプログラミング言語とC#、という用語を使用して、*抽象クラス*にこのようなクラスについて説明します)。  
  
## <a name="overriding-properties-and-methods-in-derived-classes"></a>派生クラスでプロパティとメソッドをオーバーライドします。  
 既定では、派生クラスは、その基本クラスからプロパティとメソッドを継承します。 できる場合は、継承されたプロパティまたはメソッドが派生クラスで異なった動作、*オーバーライド*します。 つまり、派生クラスでメソッドの新しい実装を定義できます。 プロパティやメソッドのオーバーライド方法を制御するには、次の修飾子を使用します。  
  
- `Overridable` 派生クラスでオーバーライドするクラスでプロパティまたはメソッドを使用します。  
  
- `Overrides` -よりも優先、`Overridable`プロパティまたはメソッドの基本クラスで定義します。  
  
- `NotOverridable` — から継承するクラスでオーバーライドされるプロパティまたはメソッドを防止します。 既定では、`Public`メソッドは`NotOverridable`します。  
  
- `MustOverride` 派生クラスでプロパティまたはメソッドをオーバーライドする必要があります。 ときに、`MustOverride`キーワードを使用して、メソッド定義から成る、 `Sub`、 `Function`、または`Property`ステートメント。 その他のステートメントは許可されずとは具体的にはない`End Sub`または`End Function`ステートメント。 `MustOverride` メソッドを宣言する必要があります`MustInherit`クラス。  
  
 給与支払いを処理するクラスを定義するとします。 ジェネリック型を定義することが`Payroll`クラスを含む、`RunPayroll`典型的な 1 週間の給与を計算するメソッド。 使用して`Payroll`のより特化された基底クラスとして`BonusPayroll`クラスは、従業員のボーナスを配布するときにされる可能性があります。  
  
 `BonusPayroll`クラスが継承、および、上書き、`PayEmployee`ベースで定義されたメソッド`Payroll`クラス。  
  
 次の例は、基底クラスを定義`Payroll,`と派生クラスでは、 `BonusPayroll`、継承されたメソッドをオーバーライドする`PayEmployee`します。 プロシージャ、`RunPayroll`を作成し、渡します、`Payroll`オブジェクトと`BonusPayroll`関数にオブジェクト`Pay`、実行する、`PayEmployee`両方のオブジェクトのメソッド。  
  
 [!code-vb[VbVbalrOOP#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#28)]  
  
## <a name="the-mybase-keyword"></a>MyBase キーワード  
 `MyBase`キーワードはクラスの現在のインスタンスの基底クラスを参照するオブジェクト変数のように動作します。 `MyBase` オーバーライドまたは派生クラスでシャドウされている基本クラスのメンバーへのアクセスによく使用されます。 具体的には、`MyBase.New`派生クラスのコンス トラクターから基本クラスのコンス トラクターを明示的に呼び出しに使用されます。  
  
 たとえば、基本クラスから継承されたメソッドをオーバーライドする派生クラスを設計するとします。 オーバーライドされたメソッドは、基本クラスのメソッドを呼び出すし、次のコード フラグメントで示すように、戻り値を変更します。  
  
 [!code-vb[VbVbalrOOP#109](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#109)]  
  
 次の一覧の使用に関する制限事項を示します`MyBase`:  
  
- `MyBase` 直接の基本クラスとその継承されたメンバーを参照します。 使用することはできませんにアクセスする`Private`クラスのメンバー。  
  
- `MyBase` キーワード、実際のオブジェクトではありません。 `MyBase` 変数に割り当てられている、プロシージャに渡されるまたはで使用されることはできません、`Is`比較します。  
  
- メソッドを`MyBase`を修飾すると、直接の基本クラスで定義する必要はありませんが間接的に継承された基本クラスで定義することがあります。 修飾された参照の順序で`MyBase`を正しくコンパイルするいくつかの基本クラスは、呼び出しに表示されるパラメーターの型と名前に一致するメソッドを含める必要があります。  
  
- 使用することはできません`MyBase`を呼び出す`MustOverride`基底クラス メソッド。  
  
- `MyBase` 自体を修飾するためには使用できません。 そのため、次のコードが無効です。  
  
     `MyBase.MyBase.BtnOK_Click()`  
  
- `MyBase` モジュールでは使用できません。  
  
- `MyBase` としてマークされている基本クラスのメンバーのアクセスに使用することはできません`Friend`基底クラスが別のアセンブリの場合。  
  
 別の例と詳細については、次を参照してください。[方法。変数にアクセスする派生クラスによって非表示に](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-access-a-variable-hidden-by-a-derived-class.md)します。  
  
## <a name="the-myclass-keyword"></a>MyClass キーワード  
 `MyClass`キーワードが最初に実装されているクラスの現在のインスタンスを参照するオブジェクト変数のように動作します。 `MyClass` よう`Me`ですべてのメソッドとプロパティを呼び出すが、`MyClass`メソッドまたはプロパティとして扱われます[NotOverridable](../../../../visual-basic/language-reference/modifiers/notoverridable.md)します。 そのため、メソッドまたはプロパティは、派生クラスでオーバーライドすることでは影響ありません。  
  
- `MyClass` キーワード、実際のオブジェクトではありません。 `MyClass` 変数に割り当てられている、プロシージャに渡されるまたはで使用されることはできません、`Is`比較します。  
  
- `MyClass` 外側のクラスとその継承されたメンバーを参照します。  
  
- `MyClass` 修飾子として使用できる`Shared`メンバー。  
  
- `MyClass` 内で使用することはできません、`Shared`メソッドがクラスの共有メンバーにアクセスするインスタンス メソッド内で使用できます。  
  
- `MyClass` 標準的なモジュールでは使用できません。  
  
- `MyClass` 基底クラスで定義されていると、そのクラスで提供されるメソッドの実装を持たないメソッドを修飾するために使用できます。 このような参照と同じ意味を持つ`MyBase.`*メソッド*します。  
  
 次の例では、比較`Me`と`MyClass`します。  
  
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
  
 場合でも`derivedClass`オーバーライド`testMethod`、`MyClass`キーワード`useMyClass`の基底クラスのバージョンへの呼び出しをオーバーライドして、コンパイラと解決の効果を null `testMethod`。  
  
## <a name="see-also"></a>関連項目

- [Inherits ステートメント](../../../../visual-basic/language-reference/statements/inherits-statement.md)
- [Me、My、MyBase、および MyClass](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
