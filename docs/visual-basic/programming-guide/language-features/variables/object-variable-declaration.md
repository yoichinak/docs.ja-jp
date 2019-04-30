---
title: オブジェクト変数の宣言 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- early binding [Visual Basic]
- declarations [Visual Basic], class
- classes [Visual Basic], declaring
- binding [Visual Basic], late and early
- object variables [Visual Basic], declaring
- variables [Visual Basic], object
- declaring variables [Visual Basic], object variables
- declaring classes [Visual Basic]
- late binding [Visual Basic]
ms.assetid: 2a5a41a3-1aa8-4236-b1f0-2382af7bf715
ms.openlocfilehash: 4a3ef3a8254153fa8695ffacd9829ca9316d77a5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61959979"
---
# <a name="object-variable-declaration-visual-basic"></a>オブジェクト変数の宣言 (Visual Basic)
オブジェクト変数を宣言するのにには、通常の宣言ステートメントを使用します。 どちらかのデータ型を指定する`Object`(つまり、[オブジェクト データ型](../../../../visual-basic/language-reference/data-types/object-data-type.md)) または固有のオブジェクトの作成元のクラス。  
  
 として変数を宣言する`Object`として宣言することと同じ<xref:System.Object?displayProperty=nameWithType>します。  
  
 特定のオブジェクト クラスを使用して変数を宣言するときに、すべてのメソッドとそのクラスと継承するクラスによって公開されるプロパティにアクセスできます。 使用して変数を宣言する場合<xref:System.Object>のメンバーだけにアクセスできる、<xref:System.Object>クラスにしない限り`Option Strict Off`遅延バインドできるようにします。  
  
## <a name="declaration-syntax"></a>宣言の構文  
 オブジェクト変数を宣言するのにには、次の構文を使用します。  
  
```vb  
Dim variablename As [New] { objectclass | Object }  
```  
  
 指定することも[パブリック](../../../../visual-basic/language-reference/modifiers/public.md)、 [Protected](../../../../visual-basic/language-reference/modifiers/protected.md)、[フレンド](../../../../visual-basic/language-reference/modifiers/friend.md)、 `Protected Friend`、[プライベート](../../../../visual-basic/language-reference/modifiers/private.md)、 [Shared](../../../../visual-basic/language-reference/modifiers/shared.md)、または[静的](../../../../visual-basic/language-reference/modifiers/static.md)で宣言します。 次の例の宣言は有効です。  
  
```vb  
Private objA As Object  
Static objB As System.Windows.Forms.Label  
Dim objC As System.OperatingSystem  
```  
  
## <a name="late-binding-and-early-binding"></a>遅延バインディングと、事前バインディング  
 場合があります、特定のクラスが、コードが実行されるまで不明です。 この場合でオブジェクト変数を宣言する必要があります、`Object`データ型。 これは、オブジェクトの任意の型への参照を一般的なをで作成され、特定のクラスは、実行時に割り当てられています。 これは呼び出されます*遅延バインディング*します。 遅延バインディングには、追加の実行時間が必要です。 メソッドとそれに割り当てる最も最近クラスのプロパティに、コードも制限されます。 これにより、別のクラスのメンバーにアクセスしようとすると、コード実行時エラーが発生することができます。  
  
 コンパイル時に特定のクラスを認識する場合は、そのクラスのオブジェクト変数を宣言する必要があります。 これは、*事前バインディング*と呼ばれます。 事前バインディングでは、パフォーマンスが向上し、すべてのメソッドおよび特定のクラスのプロパティへのアクセスをコードが保証されます。 変数の場合は前の例を宣言で`objA`クラスのオブジェクトのみを使用して<xref:System.Windows.Forms.Label?displayProperty=nameWithType>、指定する必要があります`As System.Windows.Forms.Label`で宣言します。  
  
### <a name="advantages-of-early-binding"></a>事前バインディングの利点  
 特定のクラスとしてオブジェクト変数を宣言するにはいくつかの利点。  
  
- 自動的な型チェック  
  
- 特定のクラスのすべてのメンバーへのアクセスを保証  
  
- コード エディターで Microsoft IntelliSense サポート  
  
- コードの読みやすくします。  
  
- コードのエラーの減少  
  
- エラーが検出は、コンパイル時ではなく実行時間  
  
- コードの実行を高速化  
  
## <a name="access-to-object-variable-members"></a>オブジェクト変数のメンバーへのアクセス  
 ときに`Option Strict`なって`On`メソッドとプロパティを宣言するクラスのオブジェクト変数にアクセスできます。 次に例を示します。  
  
```vb  
' Option statements must precede all other source file lines.  
Option Strict On  
' Imports statement must precede all declarations in the source file.  
Imports System.Windows.Forms  
Public Sub accessMembers()  
    Dim p As Object  
    Dim q As System.Windows.Forms.Label  
    p = New System.Windows.Forms.Label  
    q = New System.Windows.Forms.Label  
    Dim j, k As Integer  
    ' The following statement generates a compiler ERROR.  
    j = p.Left  
    ' The following statement retrieves the left edge of the label in pixels.  
    k = q.Left  
End Sub  
```  
  
 この例の場合、 `p` で使用できるのは <xref:System.Object> クラス自体のメンバーのみです。 `Left` プロパティは含まれません。 一方、 `q` は、 <xref:System.Windows.Forms.Label>型として宣言されているため、 <xref:System.Windows.Forms.Label> 名前空間の <xref:System.Windows.Forms> クラスのすべてのメソッドとプロパティを使用できます。  
  
## <a name="flexibility-of-object-variables"></a>オブジェクト変数の柔軟性  
 継承階層内のオブジェクトを操作するときに、オブジェクト変数を宣言するために使用するクラスの選択があります。 クラスを選択するときに、クラスのメンバーへのアクセスに対してオブジェクトの割り当ての柔軟性のバランスを考慮する必要があります。 たとえば、継承階層につながる、<xref:System.Windows.Forms.Form?displayProperty=nameWithType>クラス。  
  
 <xref:System.Object>  
  
 &nbsp;&nbsp;<xref:System.MarshalByRefObject>  
  
 &nbsp;&nbsp;&nbsp;&nbsp;<xref:System.ComponentModel.Component>  
  
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<xref:System.Windows.Forms.Control>  
  
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<xref:System.Windows.Forms.ScrollableControl>  
  
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<xref:System.Windows.Forms.ContainerControl>  
  
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<xref:System.Windows.Forms.Form>  
  
 アプリケーションと呼ばれるフォーム クラスを定義するとします`specialForm`、クラスから継承される<xref:System.Windows.Forms.Form>します。 具体的を参照するオブジェクト変数を宣言する`specialForm`次の例に示すように、します。  
  
```vb  
Public Class specialForm  
    Inherits System.Windows.Forms.Form  
    ' Insert code defining methods and properties of specialForm.  
End Class  
Dim nextForm As New specialForm  
```  
  
 前の例で、宣言の制限、変数`nextForm`クラスのオブジェクトに`specialForm`がすべてのメソッドとプロパティのも、`specialForm`できる`nextForm`元となるすべてのクラスのすべてのメンバーだけでなく、`specialForm`を継承します。  
  
 宣言する型にすることによりより一般的なオブジェクト変数を行うことができます<xref:System.Windows.Forms.Form>、次の例を示しています。  
  
```vb  
Dim anyForm As System.Windows.Forms.Form  
```  
  
 上記の例では、宣言では、任意のフォームをアプリケーションを割り当てることができます`anyForm`します。 ただしが`anyForm`クラスのすべてのメンバーにアクセスできる<xref:System.Windows.Forms.Form>、追加のメソッドやプロパティなど、特定の形式の定義のいずれかを使用できません`specialForm`します。  
  
 基底クラスのすべてのメンバーは派生クラスで使用できますが、派生クラスの追加のメンバーは、基本クラスを使用できません。  
  
## <a name="see-also"></a>関連項目

- [オブジェクト変数](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [オブジェクト変数の代入](../../../../visual-basic/programming-guide/language-features/variables/object-variable-assignment.md)
- [オブジェクト変数の値](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md)
- [方法: オブジェクト変数を宣言し、Visual Basic でオブジェクトを割り当てる](../../../../visual-basic/programming-guide/language-features/variables/how-to-declare-an-object-variable-and-assign-an-object-to-it.md)
- [方法: オブジェクトのメンバーへのアクセス](../../../../visual-basic/programming-guide/language-features/variables/how-to-access-members-of-an-object.md)
- [New 演算子](../../../../visual-basic/language-reference/operators/new-operator.md)
- [Option Strict ステートメント](../../../../visual-basic/language-reference/statements/option-strict-statement.md)
- [ローカル型の推論](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
