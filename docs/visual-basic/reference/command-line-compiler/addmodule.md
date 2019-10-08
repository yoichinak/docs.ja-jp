---
title: -addmodule
ms.date: 03/09/2018
helpviewer_keywords:
- /addmodule compiler option [Visual Basic]
- addmodule compiler option [Visual Basic]
- -addmodule compiler option [Visual Basic]
ms.assetid: fb4b89d4-4926-4f20-868d-427fa28497b2
ms.openlocfilehash: fbe3634d1fbc03acd56ef7276d65fd54493b9806
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/07/2019
ms.locfileid: "72002418"
---
# <a name="-addmodule"></a>-addmodule
指定ファイル内のすべての型情報を現在のコンパイル対象のプロジェクトで使用できるようにします。  
  
## <a name="syntax"></a>構文  
  
```console  
-addmodule:fileList  
```  
  
## <a name="arguments"></a>引数  
 `fileList`  
 必須。 メタデータが含まれているものの、アセンブリマニフェストが含まれていないファイルのコンマ区切りのリスト。 スペースを含むファイル名は引用符 ("") で囲む必要があります。  
  
## <a name="remarks"></a>コメント  
 @No__t-0 パラメーターによって指定されたファイルは、`-target:module` オプションを使用して作成するか、別のコンパイラを `-target:module` と同等に作成する必要があります。  
  
 @No__t-0 で追加されたすべてのモジュールは、実行時に出力ファイルと同じディレクトリに存在する必要があります。 つまり、コンパイル時に任意のディレクトリにモジュールを指定できますが、モジュールは実行時にアプリケーションディレクトリに存在する必要があります。 そうでない場合は、@no__t 0 のエラーが表示されます。  
  
 @No__t-2 で `-target:module` 以外の[-target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md)オプションを指定すると、`-addmodule` に渡すファイルはプロジェクトのアセンブリの一部になります。 1つ以上のファイルが `-addmodule` で追加された出力ファイルを実行するには、アセンブリが必要です。  
  
 アセンブリを含むファイルからメタデータをインポートするには、 [/reference (Visual Basic)](../../../visual-basic/reference/command-line-compiler/reference.md)を使用します。  
  
> [!NOTE]
> @No__t-0 オプションは、Visual Studio 開発環境内からは使用できません。これは、コマンドラインからコンパイルする場合にのみ使用できます。  
  
## <a name="example"></a>例  
 次のコードでは、モジュールを作成します。  
  
 [!code-vb[VbVbalrCompiler#47](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/OptionStrictOff.vb#47)]  
  
 次のコードは、モジュールの型をインポートします。  
  
 [!code-vb[VbVbalrCompiler#48](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/OptionStrictOff.vb#48)]  
  
 @No__t-0 を実行すると、`802` が出力されます。  
  
## <a name="see-also"></a>関連項目

- [Visual Basic のコマンド ライン コンパイラ](../../../visual-basic/reference/command-line-compiler/index.md)
- [-target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md)
- [-reference (Visual Basic)](../../../visual-basic/reference/command-line-compiler/reference.md)
- [コンパイル コマンド ラインのサンプル](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
