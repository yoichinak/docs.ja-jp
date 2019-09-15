---
title: -keycontainer
ms.date: 03/10/2018
helpviewer_keywords:
- -keycontainer compiler option [Visual Basic]
- keycontainer compiler option [Visual Basic]
- /keycontainer compiler option [Visual Basic]
ms.assetid: 6a9bc861-1752-4db1-9f64-b5252f0482cc
ms.openlocfilehash: ab81642cd756bfdf525f34ac675173600de5b104
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/13/2019
ms.locfileid: "70972334"
---
# <a name="-keycontainer"></a>-keycontainer
アセンブリに厳密な名前を付けるキー ペアのキー コンテナー名を指定します。  
  
## <a name="syntax"></a>構文  
  
```  
-keycontainer:container  
```  
  
## <a name="arguments"></a>引数  
  
|用語|定義|  
|---|---|  
|`container`|必須。 キーが格納されているコンテナーファイル。 名前にスペースが含まれている場合は、ファイル名を引用符 ("") で囲みます。|  
  
## <a name="remarks"></a>Remarks  
 コンパイラは公開キーをアセンブリマニフェストに挿入し、最後のアセンブリに秘密キーで署名することによって、共有可能なコンポーネントを作成します。 キー ファイルを生成するには、コマンド ラインで「`sn -k file`」と入力します。 オプション`-i`を指定すると、キーペアがコンテナーにインストールされます。 詳細については、「 [sn.exe (厳密名ツール)](../../../framework/tools/sn-exe-strong-name-tool.md)」を参照してください。  
  
 を指定して`-target:module`コンパイルすると、キーファイルの名前がモジュールに保持され、 [-addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md)を使用してアセンブリをコンパイルするときに作成されるアセンブリに組み込まれます。  
  
 このオプションは、任意の Microsoft Intermediate Language (MSIL) モジュールのソース コードで、カスタム属性 (<xref:System.Reflection.AssemblyKeyNameAttribute>) として指定することもできます。  
  
 また、暗号化情報を [-keyfile](../../../visual-basic/reference/command-line-compiler/keyfile.md) でコンパイラに渡すことができます。 部分的に署名されたアセンブリを作成する場合は、[-delaysign](../../../visual-basic/reference/command-line-compiler/delaysign.md) を使います。  
  
 アセンブリに署名する方法の詳細については、「[厳密な名前付きアセンブリの作成と使用](../../../standard/assembly/create-use-strong-named.md)」を参照してください。  
  
> [!NOTE]
> この`-keycontainer`オプションは、Visual Studio 開発環境内からは使用できません。コマンドラインからコンパイルする場合にのみ使用できます。  
  
## <a name="example"></a>例  
 次のコードでは、 `Input.vb`ソースファイルをコンパイルし、キーコンテナーを指定しています。  
  
```  
vbc -keycontainer:key1 input.vb  
```  
  
## <a name="see-also"></a>関連項目

- [.NET のアセンブリ](../../../standard/assembly/index.md)
- [Visual Basic のコマンド ライン コンパイラ](../../../visual-basic/reference/command-line-compiler/index.md)
- [-keyfile](../../../visual-basic/reference/command-line-compiler/keyfile.md)
- [コンパイル コマンド ラインのサンプル](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
