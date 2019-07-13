---
title: -optionstrict
ms.date: 07/20/2015
f1_keywords:
- -optionstrict
helpviewer_keywords:
- -optionstrict compiler option [Visual Basic]
- optionstrict compiler option [Visual Basic]
- /optionstrict compiler option [Visual Basic]
ms.assetid: c7b10086-0fa4-49db-b3c8-4ae0db5957da
ms.openlocfilehash: 22423877325806e6e6abe535ad98530eb924780e
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2019
ms.locfileid: "64625908"
---
# <a name="-optionstrict"></a>-optionstrict
暗黙の型変換を制限するための厳密な型のセマンティクスを適用します。  
  
## <a name="syntax"></a>構文  
  
```  
-optionstrict[+ | -]  
-optionstrict[:custom]  
```  
  
## <a name="arguments"></a>引数  
 `+` &#124; `-`  
 省略可能です。 `-optionstrict+`オプションは、暗黙的な型変換を制限します。 このオプションの既定値は`-optionstrict-`します。 `-optionstrict+`オプションは、同じ`-optionstrict`します。 制限の緩やかな型のセマンティクスの両方を使用することができます。  
  
 `custom`  
 必須。 厳密な言語セマンティクスが守られていない場合に警告します。  
  
## <a name="remarks"></a>Remarks  
 ときに`-optionstrict+`は実際には拡大の唯一の型変換は暗黙的に行われたことができます。 暗黙的な縮小の割り当てなどの型変換を`Decimal`オブジェクトを整数型のオブジェクトを入力、エラーとして報告されます。  
  
 暗黙的な縮小の型変換の警告を生成する`-optionstrict:custom`します。 使用`-nowarn:numberlist`特定の警告を無視して`-warnaserror:numberlist`特定の警告をエラーとして処理します。  
  
### <a name="to-set--optionstrict-in-the-visual-studio-ide"></a>Visual Studio IDE で-optionstrict を設定するには  
  
1. **ソリューション エクスプローラー**でプロジェクトを選択します。 **プロジェクト** メニューのをクリックして**プロパティ。**   
  
2. **[コンパイル]** タブをクリックします。  
  
3. 値を変更、 **Option Strict**ボックス。  
  
### <a name="to-set--optionstrict-programmatically"></a>-Optionstrict をプログラムで設定するには  
  
- 参照してください[Option Strict ステートメント](../../../visual-basic/language-reference/statements/option-strict-statement.md)します。  
  
## <a name="example"></a>例  
 次のコードのコンパイル`Test.vb`厳密な型のセマンティクスを使用しています。  
  
```console
vbc -optionstrict+ test.vb  
```  
  
## <a name="see-also"></a>関連項目

- [Visual Basic のコマンド ライン コンパイラ](../../../visual-basic/reference/command-line-compiler/index.md)
- [-optioncompare](../../../visual-basic/reference/command-line-compiler/optioncompare.md)
- [-optionexplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md)
- [-optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md)
- [-nowarn](../../../visual-basic/reference/command-line-compiler/nowarn.md)
- [-warnaserror (Visual Basic)](../../../visual-basic/reference/command-line-compiler/warnaserror.md)
- [コンパイル コマンド ラインのサンプル](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [Option Strict ステートメント](../../../visual-basic/language-reference/statements/option-strict-statement.md)
- [[Visual Basic の既定値] ([オプション] ダイアログ ボックス - [プロジェクト])](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
