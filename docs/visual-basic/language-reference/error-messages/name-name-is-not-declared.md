---
title: 名前 '<name>' は宣言されていません。
ms.date: 10/10/2018
f1_keywords:
- bc30451
- vbc30451
helpviewer_keywords:
- BC30451
ms.assetid: 765f099b-e21e-47c6-a906-a065444e56b3
ms.openlocfilehash: 3aadc49f91021409123550ba2712f1acf5b99d83
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61651026"
---
# <a name="name-name-is-not-declared"></a>名前 '\<名 >' が宣言されていません
ステートメントがプログラミング要素の場合を参照しますが、コンパイラは、正確な名前を持つ要素を見つけることができません。  
  
 **エラー ID:** BC30451  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
1. 参照元のステートメントで名前のスペルを確認します。 Visual Basic では、大文字と小文字が、スペルにその他の違いは完全に別の名前と見なされます。 アンダースコア (`_`) も名前の一部であり、スペルに含まれます。  
  
2. メンバー アクセス演算子があることを確認 (`.`) オブジェクトとメンバーの間。 たとえば、 <xref:System.Windows.Forms.TextBox> という名前の `TextBox1`コントロールがある場合、このコントロールの <xref:System.Windows.Forms.TextBoxBase.Text%2A> プロパティにアクセスするには、「 `TextBox1.Text`」と入力する必要があります。 代わりに「 `TextBox1Text`」と入力した場合、別の名前と見なされます。  
  
3. スペルが正しいことと、オブジェクト メンバー アクセスの構文が正しくの場合は、要素が宣言されていることを確認します。 詳細については、次を参照してください。 [Declared Elements](../../programming-guide/language-features/declared-elements/index.md)します。  
  
4. プログラミング要素が宣言されている場合は、スコープ内にあることを確認します。 参照元のステートメントがプログラミング要素が宣言領域の外側にある場合は、要素名を修飾する必要があります。 詳細については、「 [Scope in Visual Basic](../../programming-guide/language-features/declared-elements/scope.md)」を参照してください。  

5. 完全修飾型または型およびメンバーの名前を使用しない場合 (たとえば、コードがプロパティとして`MethodInfo.Name`の代わりに`System.Reflection.MethodInfo.Name`)、追加、 [Imports ステートメント](../statements/imports-statement-net-namespace-and-type.md)します。

6. SDK スタイル プロジェクトをコンパイルしようとしているかどうか (のプロジェクトを\*.vbproj ファイル、行で始まる`<Project Sdk="Microsoft.NET.Sdk">`)、およびエラー メッセージが参照型または Microsoft.VisualBasic.dll アセンブリ内のメンバーに、アプリケーションへの構成Visual Basic ランタイム ライブラリへの参照を使用してコンパイルします。 既定では、ライブラリのサブセットは SDK スタイル プロジェクトでアセンブリに埋め込まれます。

   たとえば、次の例のため、コンパイルが失敗した、<xref:Microsoft.VisualBasic.CompilerServices.Conversions.ToInteger%2A?displayProperty=fullName>メソッドが見つかりません。 アプリケーションに含まれている Visual Basic ランタイムのサブセットでは埋め込まれません。  

   [!code-vb[BC30451](~/samples/snippets/visualbasic/language-reference/error-messages/bc30451/program1.vb)]

   このエラーに対処するための追加、`<VBRuntime>Default</VBRuntime>`要素をプロジェクトに`<PropertyGroup>`セクションを次の Visual Basic プロジェクト ファイルに示します。

   [!code-vb[BC30451](~/samples/snippets/visualbasic/language-reference/error-messages/bc30451/vbruntime.vbproj?highlight=6)]

## <a name="see-also"></a>関連項目

- [宣言と定数の概要](../../../visual-basic/language-reference/keywords/declarations-and-constants-summary.md)
- [Visual Basic の名前付け規則](../../../visual-basic/programming-guide/program-structure/naming-conventions.md)
- [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)
- [宣言された要素の参照](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
