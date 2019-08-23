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
ms.openlocfilehash: 25368d23c398fb3674d5c2d75d4997f917a1c3d6
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69937354"
---
# <a name="-sdkpath"></a>-sdkpath
Mscorlib.dll と、mscorlib.dll の場所を指定します。  
  
## <a name="syntax"></a>構文  
  
```  
-sdkpath:path  
```  
  
## <a name="arguments"></a>引数  
 `path`  
 コンパイルに使用する mscorlib.dll と Microsoft のバージョンを格納しているディレクトリ。 このパスは、読み込まれるまで検証されません。 スペースが含まれている場合は、ディレクトリ名を引用符 ("") で囲みます。  
  
## <a name="remarks"></a>Remarks  
 このオプションは、Visual Basic コンパイラに対して、既定以外の場所から mscorlib.dll ファイルと Microsoft ファイルの .dll ファイルを読み込むように指示します。 この`-sdkpath`オプションは、 [-netcf](../../../visual-basic/reference/command-line-compiler/netcf.md)と共に使用するように設計されています。 .NET Compact Framework では、これらのサポートライブラリのさまざまなバージョンを使用して、デバイスでは検出されない型と言語機能を使用しないようにしています。  
  
> [!NOTE]
> この`-sdkpath`オプションは、Visual Studio 開発環境内からは使用できません。コマンドラインからコンパイルする場合にのみ使用できます。 この`-sdkpath`オプションは、Visual Basic デバイスプロジェクトが読み込まれるときに設定されます。  
  
 コンパイラオプションを使用して、コンパイラが Visual Basic ランタイムライブラリへの参照を使用`-vbruntime`せずにコンパイルするように指定できます。 詳細については、「 [-vbruntime](../../../visual-basic/reference/command-line-compiler/vbruntime.md)」を参照してください。  
  
## <a name="example"></a>例  
 次のコードは`Myfile.vb` 、C ドライブ上の .NET Compact Framework の既定のインストールディレクトリにある mscorlib.dll と Microsoft. .dll のバージョンを使用して、.NET Compact Framework でコンパイルします。 通常は、最新バージョンの .NET Compact Framework を使用します。  
  
```console
vbc -netcf -sdkpath:"c:\Program Files\Microsoft Visual Studio .NET 2003\CompactFrameworkSDK\v1.0.5000\Windows CE " myfile.vb  
```  
  
## <a name="see-also"></a>関連項目

- [Visual Basic のコマンド ライン コンパイラ](../../../visual-basic/reference/command-line-compiler/index.md)
- [コンパイル コマンド ラインのサンプル](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [-netcf](../../../visual-basic/reference/command-line-compiler/netcf.md)
- [-vbruntime](../../../visual-basic/reference/command-line-compiler/vbruntime.md)
