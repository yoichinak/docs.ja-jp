---
title: -optimize
ms.date: 07/20/2015
helpviewer_keywords:
- optimize compiler option [Visual Basic]
- /optimize compiler option [Visual Basic]
- optimization [Visual Basic], enabling
- -optimize compiler option [Visual Basic]
ms.assetid: fcba4a97-3622-4b87-a891-0f77deab4998
ms.openlocfilehash: eb84e0a7038e7ff8cb399ac7222b6ac1661b5bc1
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58842162"
---
# <a name="-optimize"></a>-optimize
有効またはコンパイラの最適化を無効にします。  
  
## <a name="syntax"></a>構文  
  
```  
-optimize[ + | - ]  
```  
  
## <a name="arguments"></a>引数  
  
|用語|定義|  
|---|---|  
|`+` &#124; `-`|省略可能です。 `-optimize-`オプションは、コンパイラの最適化を無効になります。 `-optimize+`最適化を有効にします。 既定では、最適化が無効になります。|  
  
## <a name="remarks"></a>Remarks  
 コンパイラを最適化すると、出力ファイルのサイズが小さくなり、動作が速くなり、処理の効率が向上します。 ただし、出力ファイルにコードが再配置の最適化を行うので、`-optimize+`デバッグが困難です。  
  
 生成されるすべてのモジュール`-target:module`アセンブリを使用する必要があります、同じ`-optimize`アセンブリとして設定します。 詳細については、[-ターゲット (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md)を参照してください。  
  
 組み合わせることができます、`-optimize`と`-debug`オプション。  
  
|Visual Studio 統合開発環境での最適化 - を設定するには|  
|---|  
|1.**ソリューション エクスプローラー**でプロジェクトを選択します。 **[プロジェクト]** メニューの **[プロパティ]** をクリックします。<br />     <br />2.**[コンパイル]** タブをクリックします。<br />3.**[詳細設定]** ボタンをクリックします。<br />4.変更、**の最適化を有効にする**チェック ボックスをオンします。|  
  
## <a name="example"></a>例  
 次のコードのコンパイル`T2.vb`でき、コンパイラの最適化。  
  
```console
vbc t2.vb -optimize  
```  
  
## <a name="see-also"></a>関連項目

- [Visual Basic のコマンド ライン コンパイラ](../../../visual-basic/reference/command-line-compiler/index.md)
- [-デバッグ (Visual Basic)](../../../visual-basic/reference/command-line-compiler/debug.md)
- [コンパイル コマンド ラインのサンプル](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [-ターゲット (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md)
