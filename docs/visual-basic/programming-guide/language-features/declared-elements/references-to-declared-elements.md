---
title: 宣言された要素の参照 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- declared elements [Visual Basic]
- references [Visual Basic], declared elements
- qualified names [Visual Basic]
ms.assetid: d6301709-f4cc-4b7a-b8ba-80898f14ab46
ms.openlocfilehash: 5aea43c2dab4eb44ab40449ee6e970a28fdc4abb
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58821453"
---
# <a name="references-to-declared-elements-visual-basic"></a>宣言された要素の参照 (Visual Basic)
宣言された要素をコードが参照されているとき、Visual Basic コンパイラはその名前の適切な宣言に、参照内の名前と一致します。 参照することはそれらの要素を制御するには 1 つ以上の要素が同じ名前で宣言されている場合*条件を満たす*の名前。  
  
 コンパイラが名の宣言でへの参照を名前を照合しようとした場合、*最も狭いスコープ*します。 これは、参照するコードから開始して、下位レベルの要素を含むを通じてに向かってを意味します。  
  
 次の例では、同じ名前の 2 つの変数への参照を示します。 例では、2 つの変数を宣言して、各名前付き`totalCount`、モジュール内のスコープのさまざまなレベルで`container`します。 ときに、プロシージャ`showCount`が表示されます`totalCount`Visual Basic コンパイラが、最も狭いスコープ、ローカル宣言内 namely で宣言への参照を解決する限定なく`showCount`します。 適用されるときに`totalCount`を含んでいるモジュール`container`コンパイラがより広いスコープで宣言への参照を解決します。  
  
```vb  
' Assume these two modules are both in the same assembly.  
Module container  
    Public totalCount As Integer = 1  
    Public Sub showCount()  
        Dim totalCount As Integer = 6000  
        ' The following statement displays the local totalCount (6000).  
        MsgBox("Unqualified totalCount is " & CStr(totalCount))  
        ' The following statement displays the module's totalCount (1).  
        MsgBox("container.totalCount is " & CStr(container.totalCount))  
    End Sub  
End Module  
Module callingModule  
    Public Sub displayCount()  
        container.showCount()  
        ' The following statement displays the containing module's totalCount (1).  
        MsgBox("container.totalCount is " & CStr(container.totalCount))  
    End Sub  
End Module  
```  
  
## <a name="qualifying-an-element-name"></a>要素名の修飾  
 この検索処理をオーバーライドしより広い範囲での名前を宣言する必要がありますを指定する場合*修飾*より広いスコープの親要素と名前。 場合によっては、コンテナーの要素を修飾する必要がありますも。  
  
 ターゲット要素が定義されているかを識別する情報、ソース ステートメントの前に、名前手段を修飾します。 この情報と呼ばれる、*修飾文字列*します。 1 つ含めることができます、または複数の名前空間とモジュールの場合、クラスまたは構造体します。  
  
 修飾文字列には、モジュール、クラス、または対象の要素を含む構造体を指定する必要があります明確にします。 コンテナーは、別のコンテナー要素名前空間には、通常で順番にある可能性があります。 修飾文字列にいくつかのコンテナー要素を含めることがあります。  
  
#### <a name="to-access-a-declared-element-by-qualifying-its-name"></a>その名前を修飾することによって宣言された要素にアクセスするには  
  
1.  要素が定義されている場所を決定します。 名前空間、または名前空間の階層も可能性があります。 最下位レベルの名前空間内では、モジュール、クラスまたは構造体の要素を含める必要があります。  
  
    ```vb  
    ' Assume the following hierarchy exists outside your code.  
    Namespace outerSpace  
        Namespace innerSpace  
            Module holdsTotals  
                Public Structure totals  
                    Public thisTotal As Integer  
                    Public Shared grandTotal As Long  
                End Structure  
            End Module  
        End Namespace  
    End Namespace  
    ```  
  
2.  ターゲット要素の場所に基づく修飾パスを決定します。 最上位レベルの名前空間を持つ開始、最下位レベルの名前空間に進むし、モジュール、クラス、または対象の要素を含む構造体と終了します。 パス内の各要素には、それに続く要素を含める必要があります。  
  
     `outerSpace` → `innerSpace` → `holdsTotals` → `totals`  
  
3.  ターゲット要素の修飾文字列を準備します。 ピリオドを挿入 (`.`)、パス内のすべての要素の後にします。 アプリケーション、修飾文字列内のすべての要素へのアクセスが必要です。  
  
    ```vb  
    outerSpace.innerSpace.holdsTotals.totals.  
    ```  
  
4.  式または代入ステートメントの通常の方法で、ターゲット要素に参照を記述します。  
  
    ```vb  
    grandTotal = 9000  
    ```  
  
5.  修飾文字列をターゲット要素名を前します。 名前は、期間直後にする必要があります (`.`) モジュール、クラス、または、要素を含む構造体に依存しています。  
  
    ```vb  
    ' Assume the following module is part of your code.  
    Module accessGrandTotal  
        Public Sub setGrandTotal()  
            outerSpace.innerSpace.holdsTotals.totals.grandTotal = 9000  
        End Sub  
    End Module  
    ```  
  
6.  コンパイラでは、修飾文字列を使用して、ターゲット要素の参照を一致する明確であいまいさのない宣言を見つけます。  
  
 アプリケーションに同じ名前を持つ 1 つ以上のプログラミング要素へのアクセスがある場合は、名前の参照を修飾するためにもあります。 たとえば、<xref:System.Windows.Forms>と<xref:System.Web.UI.WebControls>両方名前空間が含まれて、`Label`クラス (<xref:System.Windows.Forms.Label?displayProperty=nameWithType>と<xref:System.Web.UI.WebControls.Label?displayProperty=nameWithType>)。 アプリケーションは、両方を使用する場合、または独自に定義している場合`Label`クラス、さまざまなを区別する必要があります`Label`オブジェクト。 変数の宣言には、名前空間やインポート エイリアスを含めます。 次の例では、インポート エイリアスを使用します。  
  
```vb  
' The following statement must precede all your declarations.  
Imports win = System.Windows.Forms, web = System.Web.UI.WebControls  
' The following statement references the Windows.Forms.Label class.  
Dim winLabel As New win.Label()  
```  
  
## <a name="members-of-other-containing-elements"></a>コンテナー要素の他のメンバー  
 別のクラスまたは構造体の非共有メンバーを使用して、最初に、変数またはクラスまたは構造体のインスタンスを指す式を使用して、メンバー名を修飾する必要があります。 次の例では、`demoClass`という名前のクラスのインスタンスである`class1`します。  
  
```vb  
Dim demoClass As class1 = New class1()  
demoClass.someSub[(argumentlist)]  
```  
  
 ないメンバーを修飾するために、クラス名自体を使用することはできません[Shared](../../../../visual-basic/language-reference/modifiers/shared.md)します。 まず、オブジェクト変数にインスタンスを作成する必要があります (ここで`demoClass`) して、変数名で参照します。  
  
 クラスまたは構造体がある場合、 `Shared` 、メンバー クラスまたは構造体の名前を持つか、変数またはインスタンスを指す式では、そのメンバーを修飾することができます。  
  
 モジュールには、個別のインスタンスはありませんし、そのすべてのメンバーは`Shared`既定。 そのため、モジュール名を持つモジュール メンバーを修飾します。  
  
 次の例では、モジュール メンバー プロシージャへの修飾参照を示します。 2 つの例では、宣言しています`Sub`という名前の手順、`perform`プロジェクト内の異なるモジュールでします。 それぞれは独自のモジュール内で修飾なしを指定できますが、その他の場所から参照されている場合に修飾する必要があります。 参照して、最終的なため`module3`修飾していない`perform`コンパイラは、その参照を解決できません。  
  
```vb  
' Assume these three modules are all in the same assembly.  
Module module1  
    Public Sub perform()  
        MsgBox("module1.perform() now returning")  
    End Sub  
End Module  
Module module2  
    Public Sub perform()  
        MsgBox("module2.perform() now returning")  
    End Sub  
    Public Sub doSomething()  
        ' The following statement calls perform in module2, the active module.  
        perform()  
        ' The following statement calls perform in module1.  
        module1.perform()  
    End Sub  
End Module  
Module module3  
    Public Sub callPerform()  
        ' The following statement calls perform in module1.  
        module1.perform()  
        ' The following statement makes an unresolvable name reference  
        ' and therefore generates a COMPILER ERROR.  
        perform() ' INVALID statement  
    End Sub  
End Module  
```  
  
## <a name="references-to-projects"></a>プロジェクトへの参照  
 使用する[パブリック](../../../../visual-basic/language-reference/modifiers/public.md)別のプロジェクトで定義された要素は、まず、設定、*参照*にそのプロジェクトのアセンブリやタイプ ライブラリ。 参照を設定するには、次のようにクリックします。**参照の追加**上、**プロジェクト**メニュー、または使用して、 [/reference (Visual Basic)](../../../../visual-basic/reference/command-line-compiler/reference.md)コマンド ライン コンパイラ オプション。  
  
 XML オブジェクト モデルを使用するなど、[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]します。 参照を設定した場合、<xref:System.Xml>名前空間宣言し、そのクラスのいずれかのように、使う<xref:System.Xml.XmlDocument>します。 次の例では<xref:System.Xml.XmlDocument>します。  
  
```vb  
' Assume this project has a reference to System.Xml  
' The following statement creates xDoc as an XML document object.  
Dim xDoc As System.Xml.XmlDocument  
```  
  
## <a name="importing-containing-elements"></a>コンテナー要素のインポート  
 使用することができます、 [Imports ステートメント (.NET Namespace よぶ型)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)に*インポート*モジュールまたは使用するクラスを含む名前空間。 これにより、その名前を完全修飾しなくても、インポートされた名前空間で定義されている要素を参照することができます。 次の例では、リライトをインポートする前の例、<xref:System.Xml>名前空間。  
  
```vb  
' Assume this project has a reference to System.Xml  
' The following statement must precede all your declarations.  
Imports System.Xml  
' The following statement creates xDoc as an XML document object.  
Dim xDoc As XmlDocument  
```  
  
 さらに、`Imports`ステートメントを定義できます、*インポート エイリアス*名前空間ごとにインポートします。 これにより、ソース コードを短く読みやすくします。 次の例を使用する前の例を書き換える`xD`のエイリアスとして、<xref:System.Xml>名前空間。  
  
```vb  
' Assume this project has a reference to System.Xml  
' The following statement must precede all your declarations.  
Imports xD = System.Xml  
' The following statement creates xDoc as an XML document object.  
Dim xDoc As xD.XmlDocument  
```  
  
 `Imports`ステートメントは行いません他のプロジェクトから要素をアプリケーションに使用できます。 つまり、参照設定の代わりにはなりません。 だけ名前空間をインポートするには、その名前空間で定義された名前を修飾するために要件が削除されます。  
  
 使用することも、`Imports`モジュール、クラス、構造、および列挙型をインポートするステートメント。 このようなインポートされた要素の修飾なしのメンバーを使用できます。 ただし、常にクラスと構造体変数またはクラスまたは構造体のインスタンスに評価される式での非共有メンバーを修飾する必要があります。  
  
## <a name="naming-guidelines"></a>名前付けのガイドライン  
 同じ名前を持つ 2 つ以上のプログラミング要素を定義するときに、*あいまいさを名前*コンパイラがその名前への参照を解決しようとすると発生することができます。 数より多い場合、スコープ内に 1 つの定義、または、参照が解決されない場合は、定義がスコープ内ではありません。 たとえば、このヘルプ ページの「修飾参照例」を参照してください。  
  
 すべての要素に一意の名前を指定することにより、名前のあいまいさを回避できます。 名前空間、モジュール、またはクラスでは、その名前を修飾しなくても、任意の要素への参照を行うことができます。 正しくない要素を誤って参照する可能性を低くします。  
  
## <a name="shadowing"></a>シャドウ  
 2 つのプログラミング要素は、同じ名前を共有、うち 1 つが非表示できる、または*シャドウ*、もう 1 つ。 シャドウされた要素は参照できません。代わりに、コードでは、シャドウされた要素名を使用する場合、Visual Basic コンパイラに解決されますがシャドウする要素。 例を含む詳細については、[Visual Basic におけるシャドウ](../../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)を参照してください。  
  
## <a name="see-also"></a>関連項目

- [宣言された要素の名前](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)
- [宣言された要素の特性](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md)
- [プロジェクトおよびソリューションのプロパティの管理](/visualstudio/ide/managing-project-and-solution-properties)
- [変数](../../../../visual-basic/programming-guide/language-features/variables/index.md)
- [Imports ステートメント (.NET 名前空間および型)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)
- [New 演算子](../../../../visual-basic/language-reference/operators/new-operator.md)
- [Public](../../../../visual-basic/language-reference/modifiers/public.md)
