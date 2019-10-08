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
ms.openlocfilehash: 6d281fe07754f0471f8d6c0e31cf3ea890060504
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005349"
---
# <a name="-optionstrict"></a>-optionstrict
厳密な型のセマンティクスを適用して、暗黙的な型変換を制限します。  
  
## <a name="syntax"></a>構文  
  
```console  
-optionstrict[+ | -]  
-optionstrict[:custom]  
```  
  
## <a name="arguments"></a>引数  
 `+` &#124; `-`  
 任意。 @No__t-0 オプションを指定すると、暗黙的な型変換が制限されます。 このオプションの既定値は `-optionstrict-` です。 @No__t-0 オプションは `-optionstrict` と同じです。 寛容な型のセマンティクスには、両方を使用できます。  
  
 `custom`  
 必須。 厳密な言語セマンティクスが守られていない場合に警告します。  
  
## <a name="remarks"></a>コメント  
 @No__t-0 が有効な場合は、拡張型の変換のみを暗黙的に行うことができます。 整数型のオブジェクトへの @no__t 0 型オブジェクトの割り当てなど、暗黙的な縮小型変換は、エラーとして報告されます。  
  
 暗黙的な縮小の型変換に関する警告を生成するには、`-optionstrict:custom` を使用します。 @No__t-0 を使用して特定の警告を無視し、`-warnaserror:numberlist` を使用すると、特定の警告をエラーとして扱うことができます。  
  
### <a name="to-set--optionstrict-in-the-visual-studio-ide"></a>Visual Studio IDE で-optionstrict を設定するには  
  
1. **ソリューション エクスプローラー**でプロジェクトを選択します。 **プロジェクト** メニューの プロパティ をクリックし**ます。**   
  
2. **[コンパイル]** タブをクリックします。  
  
3. **[Option Strict]** ボックスの値を変更します。  
  
### <a name="to-set--optionstrict-programmatically"></a>プログラムによって-optionstrict を設定するには  
  
- 「 [Option Strict ステートメント](../../../visual-basic/language-reference/statements/option-strict-statement.md)」を参照してください。  
  
## <a name="example"></a>例  
 次のコードは、厳密な型のセマンティクスを使用して `Test.vb` をコンパイルします。  
  
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
