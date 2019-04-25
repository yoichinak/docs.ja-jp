---
title: -keyfile
ms.date: 03/10/2018
helpviewer_keywords:
- /keyfile compiler option [Visual Basic]
- keyfile compiler option [Visual Basic]
- -keyfile compiler option [Visual Basic]
ms.assetid: ffa82a4b-517a-4c6c-9889-5bae7b534bb8
ms.openlocfilehash: c13f34c23cad9c909c2c5bd3447f1a8fa53f9b4d
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "58833321"
---
# <a name="-keyfile"></a>-keyfile
アセンブリに厳密な名前を付けるキーまたはキー ペアを含むファイルを指定します。  
  
## <a name="syntax"></a>構文  
  
``` 
-keyfile:file  
```  
  
## <a name="arguments"></a>引数  
 `file`  
 必須。 キーを含むファイルです。 ファイル名にスペースが含まれている場合は、名前を引用符で囲みます ("")。  
  
## <a name="remarks"></a>Remarks  
 コンパイラはアセンブリ マニフェストに公開キーを挿入し、秘密キーで最終アセンブリに署名します。 キー ファイルを生成するには、コマンド ラインで「`sn -k file`」と入力します。 詳細については、次を参照してください。 [Sn.exe (厳密名ツール)](../../../framework/tools/sn-exe-strong-name-tool.md))。  
  
 使用してコンパイルする場合`-target:module`、キー ファイルの名前がモジュールに保持され、使用してアセンブリをコンパイルするときに作成されるアセンブリに組み込まれます[/addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md)します。  
  
 また、暗号化情報を [-keycontainer](../../../visual-basic/reference/command-line-compiler/keycontainer.md) でコンパイラに渡すことができます。 部分的に署名されたアセンブリを作成する場合は、[-delaysign](../../../visual-basic/reference/command-line-compiler/delaysign.md) を使います。  
  
 カスタム属性として、このオプションを指定することもできます (<xref:System.Reflection.AssemblyKeyFileAttribute>) 任意の Microsoft intermediate language モジュールのソース コードにします。  
  
 場合両方`-keyfile`と[-keycontainer](../../../visual-basic/reference/command-line-compiler/keycontainer.md)がで指定された (コマンド ライン オプションまたはカスタム属性によって)、同じコンパイル時に、コンパイラが最初にキー コンテナーを試みます。 それが成功すると、アセンブリはキー コンテナーの情報で署名されます。 指定したファイルがしようと、コンパイラがキー コンテナーを見つけられない場合`-keyfile`します。 これが成功すると、アセンブリは、キー ファイルの情報で署名およびキーの情報がキー コンテナーにインストールされている場合 (のような`sn -i`) 次のコンパイル時にキー コンテナーが有効になるようにします。  
  
 キー ファイルには公開キーだけが含まれる場合があることに注意してください。  
  
 参照してください[の作成と using strong-named Assemblies](../../../framework/app-domains/create-and-use-strong-named-assemblies.md)アセンブリへの署名の詳細についてはします。  
  
> [!NOTE]
>  `-keyfile`オプションは、Visual Studio 開発環境内からは使用できません。 コマンドラインからコンパイルする場合にのみ使用可能なです。  
  
## <a name="example"></a>例  
 次のコードは、ソース ファイルをコンパイル`Input.vb`キー ファイルを指定します。  
  
```console  
vbc -keyfile:myfile.sn input.vb  
```  
  
## <a name="see-also"></a>関連項目

- [.NET のアセンブリ](../../../standard/assembly/index.md)
- [Visual Basic のコマンド ライン コンパイラ](../../../visual-basic/reference/command-line-compiler/index.md)
- [-参照 (Visual Basic)](../../../visual-basic/reference/command-line-compiler/reference.md)
- [コンパイル コマンド ラインのサンプル](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
