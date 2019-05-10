---
title: Option Compare ステートメント (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Compare
- vb.OptionCompare
helpviewer_keywords:
- case sensitivity, Option Compare statement
- Compare keyword [Visual Basic]
- binary comparison [Visual Basic]
- strings [Visual Basic], returning from functions
- binary comparison [Visual Basic], Option Compare statement
- strings [Visual Basic], comparing
- string comparison [Visual Basic], Option Compare statement
- Text keyword [Visual Basic], Option Compare statement
- Binary keyword [Visual Basic], Option Compare statement
- string comparison [Visual Basic], sorting data
- Option Compare statement [Visual Basic]
- text [Visual Basic], comparing
ms.assetid: 54e8eeeb-3b0d-4fb9-acce-fbfbd5975f6e
ms.openlocfilehash: 77f208a0ce94925f1f968d4949f591ccab43e582
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2019
ms.locfileid: "64583512"
---
# <a name="option-compare-statement"></a>Option Compare ステートメント
文字列データを比較するときに使用する既定の比較方法を宣言します。  
  
## <a name="syntax"></a>構文  
  
```  
Option Compare { Binary | Text }  
```  
  
## <a name="parts"></a>指定項目  
  
|用語|定義|  
|---|---|  
|`Binary`|省略可能です。 文字列比較は、文字の内部バイナリ表現から派生した並べ替え順序に基づきます。<br /><br /> この種類の比較は、文字列にテキストとして解釈されない文字を含めることができる場合に特に便利です。 この場合、大文字と小文字の区別など、アルファベットの等値比較にバイアスをかけないことをお勧めします。|  
|`Text`|省略可能です。 文字列比較は、システムのロケールによって決まる、大文字と小文字を区別しないテキストの並べ替え順序に基づきます。<br /><br /> この種類の比較は、文字列にすべてのテキスト文字が含まれており、大文字と小文字を区別しないことや類縁の文字など、アルファベットの等値を考慮して文字列を比較する場合に便利です。 たとえば、`A` と `a` は等しく、`Ä` と `ä` は `B` と `b` よりも前に位置すると見なされるようにできます。|  
  
## <a name="remarks"></a>Remarks  
 使用した場合、`Option Compare` ステートメントはファイル内で他のソース コード ステートメントよりも前に記述する必要があります。  
  
 `Option Compare` ステートメントでは、文字列の比較方法 (`Binary` または `Text`) を指定します。  既定のテキスト比較方法は `Binary` です。  
  
 `Binary` 比較では、各文字列の各文字の Unicode 数値が比較されます。 `Text` 比較では、現在のカルチャでの語彙的意味に基づいて各 Unicode 文字が比較されます。  
  
 Microsoft Windows では、並べ替え順序はコード ページによって決まります。 詳細については、「[コード ページ](/cpp/c-runtime-library/code-pages)」をご覧ください。  
  
 次の例では、英語/ヨーロッパ言語のコード ページ (ANSI 1252) の文字が、`Option Compare Binary` を使用して並べ替えられ、一般的なバイナリ並べ替え順序が生成されます。  
  
 `A < B < E < Z < a < b < e < z < À < Ê < Ø < à < ê < ø`  
  
 `Option Compare Text` を使用して同じコード ページの同じ文字を並べ替えると、次のテキスト並べ替え順序が生成されます。  
  
 `(A=a) < (À = à) < (B=b) < (E=e) < (Ê = ê) < (Z=z) < (Ø = ø)`  
  
## <a name="when-an-option-compare-statement-is-not-present"></a>Option Compare ステートメントが指定されていない場合  
 ソース コードが含まれていない場合、`Option Compare`ステートメントでは、 **Option Compare**の設定、 [[コンパイル] ページ、プロジェクト デザイナー (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic)使用されます。 設定が指定されたコマンド ライン コンパイラを使用する場合、 [/optioncompare](../../../visual-basic/reference/command-line-compiler/optioncompare.md)コンパイラ オプションを使用します。  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
#### <a name="to-set-option-compare-in-the-ide"></a>IDE で Option Compare を設定するには  
  
1. **ソリューション エクスプローラー**でプロジェクトを選択します。 **[プロジェクト]** メニューの **[プロパティ]** をクリックします。  
  
2. **[コンパイル]** タブをクリックします。  
  
3. 値を設定、 **Option Compare**ボックス。  
  
 プロジェクトを作成するときに、 **Option Compare**の設定、**コンパイル**タブに設定されている、 **Option Compare**での設定、**オプション**ダイアログ ボックス。 この設定を変更する、**ツール** メニューのをクリックして**オプション**します。 **[オプション]** ダイアログ ボックスの **[プロジェクトおよびソリューション]** を展開し、**[VISUAL BASIC の既定値]** をクリックします。 初期の既定の設定で**VB の既定値**は**バイナリ**します。  
  
#### <a name="to-set-option-compare-on-the-command-line"></a>コマンド ラインで Option Compare を設定するには  
  
- 含める、 [/optioncompare](../../../visual-basic/reference/command-line-compiler/optioncompare.md)コンパイラ オプションで、 **vbc**コマンド。  
  
## <a name="example"></a>例  
 次の例では、`Option Compare` ステートメントを使用して、既定の文字列比較方法としてバイナリ比較を設定します。 このコードを使用するには、`Option Compare Binary` ステートメントのコメントを解除し、ソース ファイルの先頭に配置します。  
  
 [!code-vb[VbVbalrStatements#45](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#45)]  
  
## <a name="example"></a>例  
 次の例では、`Option Compare` ステートメントを使用して、既定の文字列比較方法として大文字と小文字を区別しないテキスト並べ替え順序を設定します。 このコードを使用するには、`Option Compare Text` ステートメントのコメントを解除し、ソース ファイルの先頭に配置します。  
  
 [!code-vb[VbVbalrStatements#46](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#46)]  
  
## <a name="see-also"></a>関連項目

- <xref:Microsoft.VisualBasic.Strings.InStr%2A>
- <xref:Microsoft.VisualBasic.Strings.InStrRev%2A>
- <xref:Microsoft.VisualBasic.Strings.Replace%2A>
- <xref:Microsoft.VisualBasic.Strings.Split%2A>
- <xref:Microsoft.VisualBasic.Strings.StrComp%2A>
- [/optioncompare](../../../visual-basic/reference/command-line-compiler/optioncompare.md)
- [比較演算子](../../../visual-basic/language-reference/operators/comparison-operators.md)
- [Visual Basic における比較演算子](../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)
- [Like 演算子](../../../visual-basic/language-reference/operators/like-operator.md)
- [文字列関数](../../../visual-basic/language-reference/functions/string-functions.md)
- [Option Explicit ステートメント](../../../visual-basic/language-reference/statements/option-explicit-statement.md)
- [Option Strict ステートメント](../../../visual-basic/language-reference/statements/option-strict-statement.md)
