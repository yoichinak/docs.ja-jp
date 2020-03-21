---
title: -optionexplicit
ms.date: 07/20/2015
f1_keywords:
- /optionexplicit
- -optionexplicit
helpviewer_keywords:
- /optionexplicit compiler option [Visual Basic]
- optionexplicit compiler option [Visual Basic]
- -optionexplicit compiler option [Visual Basic]
ms.assetid: 5d296ab3-bafe-4c4d-9887-78f162ed86c7
ms.openlocfilehash: 37ccd14dae0ebba2535185f2646e312d9bb70390
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/04/2020
ms.locfileid: "78266730"
---
# <a name="-optionexplicit"></a>-optionexplicit
変数が使用される前に宣言されていない場合、コンパイラがエラーを報告します。  
  
## <a name="syntax"></a>構文  
  
```console  
-optionexplicit[+ | -]  
```  
  
## <a name="arguments"></a>引数  
 `+` &#124; `-`  
 省略可能。 変数`-optionexplicit+`の明示的な宣言を要求するように指定します。 この`-optionexplicit+`オプションはデフォルトで、 と同じです`-optionexplicit`。 この`-optionexplicit-`オプションは、変数の暗黙的な宣言を有効にします。  
  
## <a name="remarks"></a>解説  
 ソース コード ファイルに[Option Explicit ステートメント](../../../visual-basic/language-reference/statements/option-explicit-statement.md)が含まれている場合`-optionexplicit`、このステートメントはコマンド ライン コンパイラ設定をオーバーライドします。  
  
### <a name="to-set--optionexplicit-in-the-visual-studio-ide"></a>オプションを明示的に設定するには  
  
1. **ソリューション エクスプローラー**でプロジェクトを選択します。 **[プロジェクト]** メニューの **[プロパティ]** をクリックします。
  
2. **[コンパイル]** タブをクリックします。  
  
3. **[オプションの明示的なオプション**] ボックスの値を変更します。  
  
## <a name="example"></a>例  
 次のコードは、使用`-optionexplicit-`時にコンパイルされます。  
  
 [!code-vb[VbVbalrCompiler#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/OptionExplicitOff.vb#5)]  
  
## <a name="see-also"></a>関連項目

- [Visual Basic のコマンド ライン コンパイラ](../../../visual-basic/reference/command-line-compiler/index.md)
- [オプション比較](../../../visual-basic/reference/command-line-compiler/optioncompare.md)
- [-オプションストリクト](../../../visual-basic/reference/command-line-compiler/optionstrict.md)
- [-オプションインファー](../../../visual-basic/reference/command-line-compiler/optioninfer.md)
- [コンパイル コマンド ラインのサンプル](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [Option Explicit ステートメント](../../../visual-basic/language-reference/statements/option-explicit-statement.md)
- [[Visual Basic の既定値] ([オプション] ダイアログ ボックス - [プロジェクト])](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
