---
title: -keyfile
ms.date: 03/10/2018
helpviewer_keywords:
- /keyfile compiler option [Visual Basic]
- keyfile compiler option [Visual Basic]
- -keyfile compiler option [Visual Basic]
ms.assetid: ffa82a4b-517a-4c6c-9889-5bae7b534bb8
ms.openlocfilehash: 30b890cf3d523d1e33b433a1ff6109759bd9a5e3
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/13/2019
ms.locfileid: "70972330"
---
# <a name="-keyfile"></a>-keyfile
アセンブリに厳密な名前を付けるキーまたはキー ペアを含むファイルを指定します。  
  
## <a name="syntax"></a>構文  
  
``` 
-keyfile:file  
```  
  
## <a name="arguments"></a>引数  
 `file`  
 必須。 キーを含むファイル。 ファイル名にスペースが含まれている場合は、名前を引用符 ("") で囲みます。  
  
## <a name="remarks"></a>Remarks  
 コンパイラは公開キーをアセンブリマニフェストに挿入し、秘密キーを使用して最終的なアセンブリに署名します。 キー ファイルを生成するには、コマンド ラインで「`sn -k file`」と入力します。 詳細については、「 [sn.exe (厳密名ツール)](../../../framework/tools/sn-exe-strong-name-tool.md)」を参照してください。  
  
 を指定して`-target:module`コンパイルすると、キーファイルの名前がモジュールに保持され、 [/addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md)を使用してアセンブリをコンパイルするときに作成されるアセンブリに組み込まれます。  
  
 また、暗号化情報を [-keycontainer](../../../visual-basic/reference/command-line-compiler/keycontainer.md) でコンパイラに渡すことができます。 部分的に署名されたアセンブリを作成する場合は、[-delaysign](../../../visual-basic/reference/command-line-compiler/delaysign.md) を使います。  
  
 このオプションは、Microsoft 中間言語モジュールのソースコード<xref:System.Reflection.AssemblyKeyFileAttribute>でカスタム属性 () として指定することもできます。  
  
 同じコンパイルで`-keyfile` (コマンドラインオプションまたはカスタム属性によって) と[-keycontainer](../../../visual-basic/reference/command-line-compiler/keycontainer.md)の両方が指定されている場合、コンパイラは最初にキーコンテナーを試行します。 それが成功すると、アセンブリはキー コンテナーの情報で署名されます。 キーコンテナーが見つからない場合、コンパイラはで`-keyfile`指定されたファイルを試行します。 これが成功した場合、アセンブリはキーファイルの情報で署名され、キー情報はキーコンテナー (に`sn -i`似ています) にインストールされるため、次のコンパイル時にキーコンテナーが有効になります。  
  
 キー ファイルには公開キーだけが含まれる場合があることに注意してください。  
  
 アセンブリに署名する方法の詳細については、「[厳密な名前付きアセンブリの作成と使用](../../../standard/assembly/create-use-strong-named.md)」を参照してください。  
  
> [!NOTE]
> この`-keyfile`オプションは、Visual Studio 開発環境内からは使用できません。コマンドラインからコンパイルする場合にのみ使用できます。  
  
## <a name="example"></a>例  
 次のコードでは、 `Input.vb`ソースファイルをコンパイルし、キーファイルを指定しています。  
  
```console  
vbc -keyfile:myfile.sn input.vb  
```  
  
## <a name="see-also"></a>関連項目

- [.NET のアセンブリ](../../../standard/assembly/index.md)
- [Visual Basic のコマンド ライン コンパイラ](../../../visual-basic/reference/command-line-compiler/index.md)
- [-reference (Visual Basic)](../../../visual-basic/reference/command-line-compiler/reference.md)
- [コンパイル コマンド ラインのサンプル](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
