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
ms.openlocfilehash: c027964d185d7f69c0a56a4386bedc2d8f9d2eac
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69912337"
---
# <a name="option-explicit-statement-visual-basic"></a>Option Explicit ステートメント (Visual Basic)
ファイル内のすべての変数の明示的な宣言を強制的に実行するか、変数の暗黙的な宣言を許可します。  
  
## <a name="syntax"></a>構文  
  
```  
Option Explicit { On | Off }  
```  
  
## <a name="parts"></a>指定項目  
 `On`  
 任意。 チェック`Option Explicit`を有効にします。 `On`また`On` はが指定されていない場合、既定値はになります。`Off`  
  
 `Off`  
 任意。 チェック`Option Explicit`を無効にします。  
  
## <a name="remarks"></a>Remarks  
 また`Option Explicit On`は`Option Explicit`がファイルに含まれている場合は、 `Dim`または`ReDim`ステートメントを使用して、すべての変数を明示的に宣言する必要があります。 宣言されていない変数名を使用しようとすると、コンパイル時にエラーが発生します。 ステートメント`Option Explicit Off`では、変数を暗黙的に宣言できます。  
  
 使用した場合、`Option Explicit` ステートメントはファイル内で他のソース コード ステートメントよりも前に記述する必要があります。  
  
> [!NOTE]
> 通常`Option Explicit` 、 `Off`をに設定することはお勧めできません。 変数名のスペルを 1 か所以上間違えると、プログラムの実行時に予期しない結果を招く可能性があります。  
  
## <a name="when-an-option-explicit-statement-is-not-present"></a>Option Explicit ステートメントが存在しない場合  
 ソースコードに`Option Explicit`ステートメントが含まれていない場合は、[[コンパイル] ページ (プロジェクトデザイナー (Visual Basic))](/visualstudio/ide/reference/compile-page-project-designer-visual-basic)の [**明示的な設定] オプション**が使用されます。 コマンドラインコンパイラを使用する場合は、 [/optionexplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md)コンパイラオプションを使用します。  
  
#### <a name="to-set-option-explicit-in-the-ide"></a>IDE で Option Explicit を設定するには  
  
1. **ソリューション エクスプローラー**でプロジェクトを選択します。 **[プロジェクト]** メニューの **[プロパティ]** をクリックします。  
  
2. **[コンパイル]** タブをクリックします。  
  
3. **[Option Explicit]** ボックスに値を設定します。  
  
 新しいプロジェクトを作成する場合、 **[コンパイル]** タブの **[明示的]** な設定 オプションは、VB の **[既定値]** ダイアログボックスの **[明示的]** 設定に設定されています。 VB の **[既定値]** ダイアログボックスにアクセスするには、 **[ツール]** メニューの **[オプション]** をクリックします。 **[オプション]** ダイアログ ボックスの **[プロジェクトおよびソリューション]** を展開し、 **[VISUAL BASIC の既定値]** をクリックします。 既定では、 **VB**の既定の`On`設定はです。  
  
#### <a name="to-set-option-explicit-on-the-command-line"></a>コマンドラインで Option Explicit を設定するには  
  
- **Vbc.exe**コマンドに[/optionexplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md)コンパイラオプションを含めます。  
  
## <a name="example"></a>例  
 次の例では`Option Explicit` 、ステートメントを使用して、すべての変数の明示的な宣言を強制的に実行します。 宣言されていない変数を使用しようとすると、コンパイル時にエラーが発生します。  
  
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
