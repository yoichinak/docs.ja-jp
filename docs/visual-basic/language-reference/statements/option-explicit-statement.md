---
title: Option Explicit ステートメント (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Explicit
- vb.OptionExplicit
helpviewer_keywords:
- declaring variables [Visual Basic], explicit
- forced variable declaration in Option Explicit statement [Visual Basic]
- Explicit keyword
- explicit variable declaration
- Option Explicit statement [Visual Basic]
ms.assetid: e82ac1ad-2cd3-49b2-b985-8bcf016f3fcc
ms.openlocfilehash: 19ff8cf1dbcdb941e38f23be4cb68d3a5e5b83a8
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2019
ms.locfileid: "72582577"
---
# <a name="option-explicit-statement-visual-basic"></a>Option Explicit ステートメント (Visual Basic)
ファイル内のすべての変数の明示的な宣言を強制的に実行するか、変数の暗黙的な宣言を許可します。  
  
## <a name="syntax"></a>構文  
  
```vb  
Option Explicit { On | Off }  
```  
  
## <a name="parts"></a>指定項目  
 `On`  
 省略可能です。 @No__t_0 チェックを有効にします。 @No__t_0 または `Off` が指定されていない場合、既定値は `On` になります。  
  
 `Off`  
 省略可能です。 @No__t_0 チェックを無効にします。  
  
## <a name="remarks"></a>Remarks  
 @No__t_0 または `Option Explicit` がファイルに含まれている場合は、`Dim` または `ReDim` ステートメントを使用して、すべての変数を明示的に宣言する必要があります。 宣言されていない変数名を使用しようとすると、コンパイル時にエラーが発生します。 @No__t_0 ステートメントを使用すると、変数を暗黙的に宣言できます。  
  
 使用した場合、`Option Explicit` ステートメントはファイル内で他のソース コード ステートメントよりも前に記述する必要があります。  
  
> [!NOTE]
> @No__t_0 を `Off` に設定することは、通常はお勧めできません。 変数名のスペルを 1 か所以上間違えると、プログラムの実行時に予期しない結果を招く可能性があります。  
  
## <a name="when-an-option-explicit-statement-is-not-present"></a>Option Explicit ステートメントが存在しない場合  
 ソースコードに `Option Explicit` ステートメントが含まれていない場合は、[[コンパイル] ページ (プロジェクトデザイナー (Visual Basic))](/visualstudio/ide/reference/compile-page-project-designer-visual-basic)の [**明示的な設定] オプション**が使用されます。 コマンドラインコンパイラを使用する場合は、 [/optionexplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md)コンパイラオプションを使用します。  
  
#### <a name="to-set-option-explicit-in-the-ide"></a>IDE で Option Explicit を設定するには  
  
1. **ソリューション エクスプローラー**でプロジェクトを選択します。 **[プロジェクト]** メニューの **[プロパティ]** をクリックします。  
  
2. **[コンパイル]** タブをクリックします。  
  
3. **[Option Explicit]** ボックスに値を設定します。  
  
 新しいプロジェクトを作成する場合、 **[コンパイル]** タブの **[明示的]** な設定 オプションは、VB の **[既定値]** ダイアログボックスの **[明示的]** 設定に設定されています。 VB の **[既定値]** ダイアログボックスにアクセスするには、 **[ツール]** メニューの **[オプション]** をクリックします。 **[オプション]** ダイアログ ボックスの **[プロジェクトおよびソリューション]** を展開し、 **[VISUAL BASIC の既定値]** をクリックします。 [VB の既定**値**] の初期の既定の設定は、`On` です。  
  
#### <a name="to-set-option-explicit-on-the-command-line"></a>コマンドラインで Option Explicit を設定するには  
  
- **Vbc.exe**コマンドに[/optionexplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md)コンパイラオプションを含めます。  
  
## <a name="example"></a>例  
 次の例では、`Option Explicit` ステートメントを使用して、すべての変数の明示的な宣言を強制的に実行します。 宣言されていない変数を使用しようとすると、コンパイル時にエラーが発生します。  
  
 [!code-vb[VbVbalrStatements#47](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#47)]  
  
 [!code-vb[VbVbalrStatements#48](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class2.vb#48)]  
  
## <a name="see-also"></a>関連項目

- [Dim ステートメント](../../../visual-basic/language-reference/statements/dim-statement.md)
- [ReDim ステートメント](../../../visual-basic/language-reference/statements/redim-statement.md)
- [Option Compare ステートメント](../../../visual-basic/language-reference/statements/option-compare-statement.md)
- [Option Strict ステートメント](../../../visual-basic/language-reference/statements/option-strict-statement.md)
- [/optioncompare](../../../visual-basic/reference/command-line-compiler/optioncompare.md)
- [/optionexplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md)
- [/optionstrict](../../../visual-basic/reference/command-line-compiler/optionstrict.md)
- [[Visual Basic の既定値] ([オプション] ダイアログ ボックス - [プロジェクト])](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
