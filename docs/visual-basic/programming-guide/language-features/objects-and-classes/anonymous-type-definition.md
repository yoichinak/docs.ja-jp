---
title: 匿名型の定義 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- anonymous types [Visual Basic], type definition
ms.assetid: 7a8a0ddc-55ba-4d67-869e-87a84d938bac
ms.openlocfilehash: 5f6486965d9e44524420975523e10ded32a135b7
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/10/2019
ms.locfileid: "67755216"
---
# <a name="anonymous-type-definition-visual-basic"></a>匿名型の定義 (Visual Basic)

匿名型のインスタンスの宣言に応答してでは、コンパイラは、型の指定したプロパティを格納する新しいクラス定義を作成します。

## <a name="compiler-generated-code"></a>コンパイラによって生成されたコード

次の定義の`product`、コンパイラは、プロパティを格納する新しいクラス定義を作成します。 `Name`、 `Price`、と`OnHand`します。

[!code-vb[VbVbalrAnonymousTypes#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#25)]

クラス定義には、次のようなプロパティの定義が含まれています。 あることに注意してくださいありません`Set`メソッド主要なプロパティ。 キー プロパティの値とは、読み取り専用です。

```vb
Public Class $Anonymous1
    Private _name As String
    Private _price As Double
    Private _onHand As Integer
     Public ReadOnly Property Name() As String
        Get
            Return _name
        End Get
    End Property

    Public ReadOnly Property Price() As Double
        Get
            Return _price
        End Get
    End Property

    Public Property OnHand() As Integer
        Get
            Return _onHand
        End Get
        Set(ByVal Value As Integer)
            _onHand = Value
        End Set
    End Property

End Class
```

さらに、匿名型の定義には、パラメーターなしのコンス トラクターが含まれます。 パラメーターを必要とするコンス トラクターが許可されていません。

型定義から継承された 3 つのメンバーよりも優先される場合、匿名型の宣言には、少なくとも 1 つのキー プロパティが含まれています、 <xref:System.Object>: <xref:System.Object.Equals%2A>、 <xref:System.Object.GetHashCode%2A>、および<xref:System.Object.ToString%2A>します。 キー プロパティが宣言されていない場合、のみ<xref:System.Object.ToString%2A>オーバーライドされます。 上書きは、次の機能を提供します。

- `Equals` 返します`True`匿名型の 2 つのインスタンスが、同じインスタンスである場合、または、次の条件を満たしている場合。

  - 同じ数のプロパティがあります。

  - プロパティが同じ名前を持つ、同じ順序で宣言されているし、推論された型が同じです。 名前の比較は区別されません。

  - キー プロパティでは、少なくとも 1 つのプロパティと`Key`キーワードは、同じのプロパティに適用されます。

  - キー プロパティの対応する各ペアの比較を返します`True`します。

    たとえば、次の例についてで`Equals`返します`True`のみ`employee01`と`employee08`。 各行の新しいインスタンスが一致しない理由理由を指定する前にコメント`employee01`します。

    [!code-vb[VbVbalrAnonymousTypes#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#24)]

- `GetHashcode` 適切に一意の GetHashCode アルゴリズムを提供します。 アルゴリズムでは、キー プロパティだけを使用して、ハッシュ コードを計算します。

- `ToString` 次の例に示すように、連結されたプロパティの値の文字列を返します。 キーとキー以外のプロパティの両方が含まれます。

  [!code-vb[VbVbalrAnonymousTypes#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#29)]

生成されたこれらのメソッドと競合する、匿名型のプロパティを明示的に指定できません。 つまり、使用することはできません`.Equals`、 `.GetHashCode`、または`.ToString`にプロパティの名前します。

匿名型の定義には少なくとも 1 つ含まれているキー プロパティも実装、<xref:System.IEquatable%601?displayProperty=nameWithType>インターフェイス、場所`T`匿名型の種類です。

> [!NOTE]
> 同じアセンブリで発生した、そのプロパティは、同じ名前を持つと推論された型が同じ、プロパティを同じ順序で宣言および同じプロパティがキー プロパティとしてマークされている場合にのみ、匿名型の宣言は、同じ匿名型を作成します。

## <a name="see-also"></a>関連項目

- [匿名型](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)
- [方法: 匿名型の宣言におけるプロパティ名と型を推論します。](../../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)
