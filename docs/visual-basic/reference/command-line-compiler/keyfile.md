---
title: -keyfile
ms.date: 03/10/2018
helpviewer_keywords:
- /keyfile compiler option [Visual Basic]
- keyfile compiler option [Visual Basic]
- -keyfile compiler option [Visual Basic]
ms.assetid: ffa82a4b-517a-4c6c-9889-5bae7b534bb8
ms.openlocfilehash: cffc3c5f0ff3dd48ca2c74bde346a967b209dc5f
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/04/2020
ms.locfileid: "78266743"
---
# <a name="-keyfile"></a>-keyfile
アセンブリに厳密な名前を付けるキーまたはキー ペアを含むファイルを指定します。  
  
## <a name="syntax"></a>構文  
  
```console
-keyfile:file  
```  
  
## <a name="arguments"></a>引数  
 `file`  
 必須。 キーを含むファイル。 ファイル名にスペースが含まれている場合は、名前を引用符で囲みます (")。  
  
## <a name="remarks"></a>解説  
 コンパイラは、公開キーをアセンブリ マニフェストに挿入し、秘密キーを使用して最終的なアセンブリに署名します。 キー ファイルを生成するには、コマンド ラインで「`sn -k file`」と入力します。 詳細については、「 [Sn.exe (厳密名ツール)」](../../../framework/tools/sn-exe-strong-name-tool.md)を参照してください。  
  
 を使用して`-target:module`コンパイルする場合、キー ファイルの名前はモジュールに保持され[、-addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md)を使用してアセンブリをコンパイルするときに作成されるアセンブリに組み込まれます。  
  
 また、暗号化情報を [-keycontainer](../../../visual-basic/reference/command-line-compiler/keycontainer.md) でコンパイラに渡すことができます。 部分的に署名されたアセンブリを作成する場合は、[-delaysign](../../../visual-basic/reference/command-line-compiler/delaysign.md) を使います。  
  
 このオプションは、Microsoft 中間言語モジュールのソース<xref:System.Reflection.AssemblyKeyFileAttribute>コードでカスタム属性 ( ) として指定することもできます。  
  
 同じコンパイル`-keyfile`で (コマンド ライン オプションまたはカスタム属性によって) 両方と[-keycontainer](../../../visual-basic/reference/command-line-compiler/keycontainer.md)が指定されている場合、コンパイラは最初にキー コンテナーを試行します。 それが成功すると、アセンブリはキー コンテナーの情報で署名されます。 コンパイラがキー コンテナを見つけられない場合は、 で`-keyfile`指定されたファイルを試します。 この処理が成功すると、アセンブリはキー ファイル内の情報で署名され、キー情報はキー コンテナーにインストールされます (`sn -i`に似ています ) 、次のコンパイル時にキー コンテナーが有効になります。  
  
 キー ファイルには公開キーだけが含まれる場合があることに注意してください。  
  
 アセンブリの署名の詳細については、「[厳密な名前付きアセンブリの作成と使用](../../../standard/assembly/create-use-strong-named.md)」を参照してください。  
  
> [!NOTE]
> この`-keyfile`オプションは、Visual Studio 開発環境からは使用できません。コマンド ラインからコンパイルする場合にのみ使用できます。

## <a name="example"></a>例

次のコードは、ソース`Input.vb`ファイルをコンパイルし、キー ファイルを指定します。

```console
vbc -keyfile:myfile.sn input.vb
```

## <a name="see-also"></a>関連項目

- [.NET のアセンブリ](../../../standard/assembly/index.md)
- [Visual Basic のコマンド ライン コンパイラ](../../../visual-basic/reference/command-line-compiler/index.md)
- [-リファレンス (ビジュアルベーシック)](../../../visual-basic/reference/command-line-compiler/reference.md)
- [コンパイル コマンド ラインのサンプル](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
