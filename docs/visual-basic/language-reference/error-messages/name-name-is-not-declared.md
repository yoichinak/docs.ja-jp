---
title: 名前 '<name>' は宣言されていません。
ms.date: 10/10/2018
f1_keywords:
- bc30451
- vbc30451
helpviewer_keywords:
- BC30451
ms.assetid: 765f099b-e21e-47c6-a906-a065444e56b3
ms.openlocfilehash: dfa1d1600c7943e503b4f5ec2e2b8ecd6fbb9fe0
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/04/2019
ms.locfileid: "70254201"
---
# <a name="name-name-is-not-declared"></a>名前 '\<name > ' は宣言されていません
ステートメントがプログラミング要素を参照していますが、その正確な名前を持つ要素をコンパイラが見つけることができません。  
  
 **エラー ID:** BC30451  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
1. 参照元のステートメントで名前のスペルを確認します。 Visual Basic では大文字と小文字が区別されませんが、スペルのその他のバリエーションはまったく別の名前と見なされます。 アンダースコア (`_`) も名前の一部であり、スペルに含まれます。  
  
2. オブジェクトとそのメンバーの間にメンバーアクセス`.`演算子 () があることを確認します。 たとえば、 <xref:System.Windows.Forms.TextBox> という名前の `TextBox1`コントロールがある場合、このコントロールの <xref:System.Windows.Forms.TextBoxBase.Text%2A> プロパティにアクセスするには、「 `TextBox1.Text`」と入力する必要があります。 代わりに「 `TextBox1Text`」と入力した場合、別の名前と見なされます。  
  
3. スペルが正しく、オブジェクトメンバーアクセスの構文が正しい場合は、要素が宣言されていることを確認します。 詳細については、「宣言された[要素](../../programming-guide/language-features/declared-elements/index.md)」を参照してください。  
  
4. プログラミング要素が宣言されている場合は、スコープ内にあることを確認します。 参照元のステートメントがプログラミング要素を宣言している領域の外部にある場合は、要素名を修飾する必要があります。 詳細については、「 [Scope in Visual Basic](../../programming-guide/language-features/declared-elements/scope.md)」を参照してください。  

5. 完全修飾型または型とメンバー名を使用していない場合 (たとえば、コードがの`MethodInfo.Name` `System.Reflection.MethodInfo.Name`代わりにプロパティを参照している場合) は、 [Imports ステートメント](../statements/imports-statement-net-namespace-and-type.md)を追加します。

6. SDK スタイルのプロジェクト (行\* `<Project Sdk="Microsoft.NET.Sdk">`で始まる .vbproj ファイルを含むプロジェクト) をコンパイルしようとしているときに、エラーメッセージが、Microsoft のアセンブリ内の型またはメンバーを参照している場合は、アプリケーションをVisual Basic ランタイムライブラリへの参照を使用してコンパイルします。 既定では、ライブラリのサブセットは、SDK スタイルのプロジェクトのアセンブリに埋め込まれます。

   たとえば、次の例では、 <xref:Microsoft.VisualBasic.CompilerServices.Conversions.ChangeType%2A?displayProperty=fullName>メソッドが見つからないため、コンパイルに失敗します。 アプリケーションに含まれている Visual Basic ランタイムのサブセットには埋め込まれていません。  

   [!code-vb[BC30451](~/samples/snippets/visualbasic/language-reference/error-messages/bc30451/program1.vb?highlight=7)]

   このエラーに対処するには`<VBRuntime>Default</VBRuntime>` 、次の Visual Basic `<PropertyGroup>`プロジェクトファイルに示すように、要素を projects セクションに追加します。

   [!code-xml[BC30451](~/samples/snippets/visualbasic/language-reference/error-messages/bc30451/vbruntime.vbproj?highlight=6)]

## <a name="see-also"></a>関連項目

- [宣言と定数の概要](../../../visual-basic/language-reference/keywords/declarations-and-constants-summary.md)
- [Visual Basic 名前付け規則](../../../visual-basic/programming-guide/program-structure/naming-conventions.md)
- [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)
- [宣言された要素の参照](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
