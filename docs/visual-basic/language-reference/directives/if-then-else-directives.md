---
title: '#もし。。。Then... #Else ディレクティブ (Visual Basic)'
ms.date: 04/11/2018
f1_keywords:
- vb.#EndIf
- '#End If'
- '#Then'
- '#ElseIf'
- vb.#ElseIf
- vb.#Else
- vb.#If
helpviewer_keywords:
- Visual Basic code, compiling
- '#If directive [Visual Basic]'
- conditional compilation [Visual Basic], directives
- '#End if directive [Visual Basic]'
- selective compiling
- else directive (#else)
- '#Else directive [Visual Basic]'
ms.assetid: 10bba104-e3fd-451b-b672-faa472530502
ms.openlocfilehash: 697521276e2d5a8d0a4aaae38789a21b7aa87fcb
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69940753"
---
# <a name="ifthenelse-directives"></a>#If...Then...#Else ディレクティブ
選択された Visual Basic コードのブロックを条件付きでコンパイルします。  
  
## <a name="syntax"></a>構文  
  
```  
#If expression Then  
   statements  
[ #ElseIf expression Then  
   [ statements ]  
...  
#ElseIf expression Then  
   [ statements ] ]  
[ #Else  
   [ statements ] ]  
#End If  
```  
  
## <a name="parts"></a>指定項目  
 `expression`  
 ステートメントおよび`#If` `#ElseIf`ステートメントには必須。他の場所では省略可能です。 または`True` `False`に評価される、1つ以上の条件付きコンパイラ定数、リテラル、および演算子で構成される任意の式。  
  
 `statements`  
 ステートメントブロック`#If`の場合は必須。他の場合は省略可能。 関連付けられた式がに`True`評価される場合にコンパイルされるプログラムラインまたはコンパイラディレクティブを Visual Basic します。  
  
 `#End If`  
 ステートメントブロック`#If`を終了します。  
  
## <a name="remarks"></a>Remarks  
 画面では、 `#If...Then...#Else`ディレクティブの動作は`If...Then...Else`ステートメントと同じになります。 ただし、 `#If...Then...#Else`ディレクティブはコンパイラによってコンパイルされた内容を`If...Then...Else`評価しますが、ステートメントは実行時に条件を評価します。  
  
 通常、条件付きコンパイルは、異なるプラットフォームに対して同じプログラムをコンパイルするために使用されます。 また、デバッグコードが実行可能ファイルに表示されないようにするためにも使用されます。 条件付きコンパイル中に除外されたコードは、最終的な実行可能ファイルから完全に省略されるため、サイズやパフォーマンスには影響しません。  
  
 評価の結果に関係なく、すべての式はを使用`Option Compare Binary`して評価されます。 ステートメントは、ステートメントおよび`#ElseIf`ステートメントの`#If`式には影響しません。 `Option Compare`  
  
> [!NOTE]
> 、 、、および`#If`ディレクティブ`#End If`の単一行形式は存在しません。 `#Else` `#ElseIf` ディレクティブと同じ行に他のコードを記述することはできません。 

条件付きコンパイルブロック内のステートメントは、完全な論理ステートメントである必要があります。 たとえば、条件付きで関数の属性のみをコンパイルすることはできませんが、その属性と共に関数を条件付きで宣言することはできます。

```vb
   #If DEBUG Then
   <WebMethod()>
   Public Function SomeFunction() As String
   #Else
   <WebMethod(CacheDuration:=86400)>
   Public Function SomeFunction() As String
   #End If
```

## <a name="example"></a>例
 この例では`#If...Then...#Else` 、コンストラクトを使用して、特定のステートメントをコンパイルするかどうかを判断します。  
  
 [!code-vb[VbVbalrConditionalComp#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConditionalComp/VB/Class1.vb#1)]  
  
## <a name="see-also"></a>関連項目

- [#Const ディレクティブ](../../../visual-basic/language-reference/directives/const-directive.md)
- [If...Then...Else ステートメント](../../../visual-basic/language-reference/statements/if-then-else-statement.md)
- [条件付きコンパイル](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)
- <xref:System.Diagnostics.ConditionalAttribute?displayProperty=nameWithType>
