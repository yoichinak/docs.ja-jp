---
title: -sdkpath
ms.date: 07/20/2015
f1_keywords:
- sdkpath
- -sdkpath
helpviewer_keywords:
- -sdkpath compiler option [Visual Basic]
- /sdkpath compiler option [Visual Basic]
- sdkpath compiler option [Visual Basic]
ms.assetid: fec8a3f1-b791-4a37-8af7-344859f8212d
ms.openlocfilehash: 91f64756b2fbf14dc96550420cd936973e6bec87
ms.sourcegitcommit: 4c41ec195caf03d98b7900007c3c8e24eba20d34
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/20/2019
ms.locfileid: "67268294"
---
# <a name="-sdkpath"></a>-sdkpath
Mscorlib.dll および Microsoft.VisualBasic.dll の位置を指定します。  
  
## <a name="syntax"></a>構文  
  
```  
-sdkpath:path  
```  
  
## <a name="arguments"></a>引数  
 `path`  
 Mscorlib.dll および Microsoft.VisualBasic.dll のコンパイルに使用するのバージョンを含むディレクトリ。 それが読み込まれるまで、このパスは検証されません。 ディレクトリ名を引用符で囲みます ("")、スペースが含まれている場合。  
  
## <a name="remarks"></a>Remarks  
 このオプションは、既定以外の場所から mscorlib.dll および Microsoft.VisualBasic.dll のファイルを読み込む Visual Basic コンパイラに指示します。 `-sdkpath`で使用するオプションが設計されました[-netcf](../../../visual-basic/reference/command-line-compiler/netcf.md)します。 これらの .NET Compact Framework は異なるバージョンの種類と、デバイスで見つからない言語機能の使用を回避するためにライブラリをサポートしています。  
  
> [!NOTE]
>  `-sdkpath`オプションは、Visual Studio 開発環境内からは使用できません。 コマンドラインからコンパイルする場合にのみ使用可能なです。 `-sdkpath` Visual Basic プロジェクトのデバイスが読み込まれるときにオプションを設定します。  
  
 使用して、コンパイラが、Visual Basic ランタイム ライブラリを参照しないでコンパイルを指定することができます、`-vbruntime`コンパイラ オプション。 詳細については、次を参照してください。 [-vbruntime](../../../visual-basic/reference/command-line-compiler/vbruntime.md)します。  
  
## <a name="example"></a>例  
 次のコードのコンパイル`Myfile.vb`C ドライブ上の .NET Compact Framework の既定のインストール ディレクトリで見つかった Mscorlib.dll および Microsoft.VisualBasic.dll のバージョンを使用して、.NET Compact Framework を使用します。 通常、.NET Compact Framework の最新バージョンを使用するとします。  
  
```console
vbc -netcf -sdkpath:"c:\Program Files\Microsoft Visual Studio .NET 2003\CompactFrameworkSDK\v1.0.5000\Windows CE " myfile.vb  
```  
  
## <a name="see-also"></a>関連項目

- [Visual Basic のコマンド ライン コンパイラ](../../../visual-basic/reference/command-line-compiler/index.md)
- [コンパイル コマンド ラインのサンプル](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [-netcf](../../../visual-basic/reference/command-line-compiler/netcf.md)
- [-vbruntime](../../../visual-basic/reference/command-line-compiler/vbruntime.md)
