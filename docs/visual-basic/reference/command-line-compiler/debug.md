---
title: /debug (Visual Basic)
ms.date: 03/10/2018
helpviewer_keywords:
- debug compiler switches
- /debug compiler option [Visual Basic]
- -debug compiler option [Visual Basic]
- debug compiler option [Visual Basic]
ms.assetid: c2b0bea5-1d5e-499f-9bd5-4f6c6b715ea2
ms.openlocfilehash: 9bf7170cee31f92481b15fb1227f21895cd3734d
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "58827979"
---
# <a name="-debug-visual-basic"></a>-デバッグ (Visual Basic)
コンパイラにデバッグ情報が生成され、出力ファイルに格納します。  
  
## <a name="syntax"></a>構文  
  
```  
-debug[+ | -]  
' -or-  
-debug:[full | pdbonly]  
```  
  
## <a name="arguments"></a>引数  
  
|用語|定義|  
|---|---|  
|`+` &#124; `-`|任意。 指定する`+`または`/debug`コンパイラがデバッグ情報を生成して .pdb ファイルに配置します。 指定する`-`指定しない場合と同じ効果`/debug`します。|  
|`full` &#124; `pdbonly`|任意。 コンパイラによって生成されるデバッグ情報の種類を指定します。 指定しない場合`/debug:pdbonly`、既定値は`full`、実行中のプログラムにデバッガーをアタッチできます。 `pdbonly`引数により、ソース コードのデバッグ、デバッガーでプログラムを開始、実行中のプログラムがデバッガーにアタッチされている場合にのみ、アセンブリ言語のコードを表示します。|  
  
## <a name="remarks"></a>Remarks  
 このオプションを使用してデバッグ ビルドを作成します。 指定しない場合`/debug`、 `/debug+`、または`/debug:full`プログラムの出力ファイルをデバッグすることはできません。  
  
 既定では、デバッグ情報が出力されない (`/debug-`)。 デバッグ情報を出力する次のように指定します。`/debug`または`/debug+`します。  
  
 アプリケーションのデバッグ パフォーマンスを構成する方法については、「[イメージのデバッグの簡略化](../../../framework/debug-trace-profile/making-an-image-easier-to-debug.md)」を参照してください。  
  
|設定するには、Visual Studio 統合開発環境でデバッグします。|  
|---|  
|1.**ソリューション エクスプ ローラー**でプロジェクトを選択し、 **[プロジェクト]** メニューの **[プロパティ]** をクリックします。 <br />2.**[コンパイル]** タブをクリックします。<br />3.**[詳細コンパイル オプション]** をクリックします。<br />4.値を変更、**デバッグ情報の生成**ボックス。|  
  
## <a name="example"></a>例  
 次の例では、デバッグ情報を出力ファイルに`App.exe`します。  
  
```  
vbc -debug -out:app.exe test.vb  
```  
  
## <a name="see-also"></a>関連項目

- [Visual Basic のコマンド ライン コンパイラ](../../../visual-basic/reference/command-line-compiler/index.md)
- [/bugreport](../../../visual-basic/reference/command-line-compiler/bugreport.md)
- [コンパイル コマンド ラインのサンプル](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
