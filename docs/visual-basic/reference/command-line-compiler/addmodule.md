---
title: -addmodule
ms.date: 03/09/2018
helpviewer_keywords:
- /addmodule compiler option [Visual Basic]
- addmodule compiler option [Visual Basic]
- -addmodule compiler option [Visual Basic]
ms.assetid: fb4b89d4-4926-4f20-868d-427fa28497b2
ms.openlocfilehash: 0e0915a2534f950cec074632a59750c3f96b679d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69962456"
---
# <a name="-addmodule"></a>-addmodule
指定ファイル内のすべての型情報を現在のコンパイル対象のプロジェクトで使用できるようにします。  
  
## <a name="syntax"></a>構文  
  
```  
-addmodule:fileList  
```  
  
## <a name="arguments"></a>引数  
 `fileList`  
 必須。 メタデータが含まれているものの、アセンブリマニフェストが含まれていないファイルのコンマ区切りのリスト。 スペースを含むファイル名は引用符 ("") で囲む必要があります。  
  
## <a name="remarks"></a>Remarks  
 `fileList`パラメーターによって一覧表示されるファイルは、 `-target:module`オプションを使用して作成するか、 `-target:module`と同じ別のコンパイラを使用して作成する必要があります。  
  
 で`-addmodule`追加されたすべてのモジュールは、実行時に出力ファイルと同じディレクトリに存在する必要があります。 つまり、コンパイル時に任意のディレクトリにモジュールを指定できますが、モジュールは実行時にアプリケーションディレクトリに存在する必要があります。 そうでない場合は、 <xref:System.TypeLoadException>エラーが表示されます。  
  
 (暗黙的または明示的に) を指定した場合を除き`-target:module` `-addmodule`、[-target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md)オプションを指定`-addmodule`すると、に渡すファイルはプロジェクトのアセンブリの一部になります。 アセンブリは、で`-addmodule`追加された1つ以上のファイルを含む出力ファイルを実行するために必要です。  
  
 アセンブリを含むファイルからメタデータをインポートするには、 [/reference (Visual Basic)](../../../visual-basic/reference/command-line-compiler/reference.md)を使用します。  
  
> [!NOTE]
> この`-addmodule`オプションは、Visual Studio 開発環境内からは使用できません。コマンドラインからコンパイルする場合にのみ使用できます。  
  
## <a name="example"></a>例  
 次のコードでは、モジュールを作成します。  
  
 [!code-vb[VbVbalrCompiler#47](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/OptionStrictOff.vb#47)]  
  
 次のコードは、モジュールの型をインポートします。  
  
 [!code-vb[VbVbalrCompiler#48](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/OptionStrictOff.vb#48)]  
  
 を実行`t1`すると、が`802`出力されます。  
  
## <a name="see-also"></a>関連項目

- [Visual Basic のコマンド ライン コンパイラ](../../../visual-basic/reference/command-line-compiler/index.md)
- [-target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md)
- [-reference (Visual Basic)](../../../visual-basic/reference/command-line-compiler/reference.md)
- [コンパイル コマンド ラインのサンプル](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
