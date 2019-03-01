---
title: -addmodule
ms.date: 03/09/2018
helpviewer_keywords:
- /addmodule compiler option [Visual Basic]
- addmodule compiler option [Visual Basic]
- -addmodule compiler option [Visual Basic]
ms.assetid: fb4b89d4-4926-4f20-868d-427fa28497b2
ms.openlocfilehash: 5a6d367f4b09de600bb744aa2abed0da2c93aa0b
ms.sourcegitcommit: 41c0637e894fbcd0713d46d6ef1866f08dc321a2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/01/2019
ms.locfileid: "57202367"
---
# <a name="-addmodule"></a>-addmodule
指定ファイル内のすべての型情報を現在のコンパイル対象のプロジェクトで使用できるようにします。  
  
## <a name="syntax"></a>構文  
  
```  
-addmodule:fileList  
```  
  
## <a name="arguments"></a>引数  
 `fileList`  
 必須。 メタデータが含まれますが、アセンブリ マニフェストが含まれていないファイルのコンマ区切りリスト。 空白を含むファイル名を引用符で囲む必要があります ("")。  
  
## <a name="remarks"></a>Remarks  
 によって示されているファイル、`fileList`パラメーターを使って作成する必要があります、`-target:module`オプション、または別のコンパイラと同じ`-target:module`します。  
  
 追加したすべてのモジュール`-addmodule`実行時に出力ファイルと同じディレクトリにする必要があります。 つまり、コンパイル時に、任意のディレクトリにモジュールを指定することができますが、モジュールは実行時にアプリケーション ディレクトリに配置する必要があります。 そうでない場合、<xref:System.TypeLoadException>エラー。  
  
 (暗黙的または明示的に) を指定する場合、[-ターゲット (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md)以外のオプション`-target:module`で`-addmodule`に渡すファイル`-addmodule`プロジェクトのアセンブリの一部になります。 アセンブリがいずれかを含む出力ファイルを実行するために必要なまたは以上のファイルが追加で`-addmodule`します。  
  
 使用[/reference (Visual Basic)](../../../visual-basic/reference/command-line-compiler/reference.md)アセンブリを含むファイルからメタデータをインポートします。  
  
> [!NOTE]
>  `-addmodule`オプションは、Visual Studio 開発環境内からは使用できません。 コマンドラインからコンパイルする場合にのみ使用可能なです。  
  
## <a name="example"></a>例  
 次のコードでは、モジュールを作成します。  
  
 [!code-vb[VbVbalrCompiler#47](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/OptionStrictOff.vb#47)]  
  
 次のコードでは、モジュールの型をインポートします。  
  
 [!code-vb[VbVbalrCompiler#48](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/OptionStrictOff.vb#48)]  
  
 実行すると`t1`、出力`802`します。  
  
## <a name="see-also"></a>関連項目
- [Visual Basic のコマンド ライン コンパイラ](../../../visual-basic/reference/command-line-compiler/index.md)
- [-ターゲット (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md)
- [-参照 (Visual Basic)](../../../visual-basic/reference/command-line-compiler/reference.md)
- [コンパイル コマンド ラインのサンプル](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
