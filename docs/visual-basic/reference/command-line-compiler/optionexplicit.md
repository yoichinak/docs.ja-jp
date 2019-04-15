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
ms.openlocfilehash: 54d438541e8840e4394b24b20b4f394ff8cdb820
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/09/2019
ms.locfileid: "59332392"
---
# <a name="-optionexplicit"></a>-optionexplicit
使用されるように、変数が宣言されていない場合は、コンパイラ エラーを報告します。  
  
## <a name="syntax"></a>構文  
  
```  
-optionexplicit[+ | -]  
```  
  
## <a name="arguments"></a>引数  
 `+` &#124; `-`  
 任意。 指定`-optionexplicit+`変数の明示的な宣言を要求します。 `-optionexplicit+`オプションと同じですが、既定`-optionexplicit`します。 `-optionexplicit-`オプションは、変数の暗黙的な宣言を使用できます。  
  
## <a name="remarks"></a>Remarks  
 ソース コード ファイルが含まれている場合、 [Option Explicit ステートメント](../../../visual-basic/language-reference/statements/option-explicit-statement.md)、ステートメントよりも優先、`-optionexplicit`コマンド ライン コンパイラを設定します。  
  
### <a name="to-set--optionexplicit-in-the-visual-studio-ide"></a>Visual Studio IDE で-optionexplicit を設定するには  
  
1. **ソリューション エクスプローラー**でプロジェクトを選択します。 **[プロジェクト]** メニューの **[プロパティ]** をクリックします。   
  
2. **[コンパイル]** タブをクリックします。  
  
3. 値を変更、 **Option Explicit**ボックス。  
  
## <a name="example"></a>例  
 ときに、次のコードがコンパイル`-optionexplicit-`使用されます。  
  
 [!code-vb[VbVbalrCompiler#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/OptionExplicitOff.vb#5)]  
  
## <a name="see-also"></a>関連項目

- [Visual Basic のコマンド ライン コンパイラ](../../../visual-basic/reference/command-line-compiler/index.md)
- [-optioncompare](../../../visual-basic/reference/command-line-compiler/optioncompare.md)
- [-optionstrict](../../../visual-basic/reference/command-line-compiler/optionstrict.md)
- [-optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md)
- [コンパイル コマンド ラインのサンプル](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [Option Explicit ステートメント](../../../visual-basic/language-reference/statements/option-explicit-statement.md)
- [[Visual Basic の既定値] ([オプション] ダイアログ ボックス - [プロジェクト])](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
