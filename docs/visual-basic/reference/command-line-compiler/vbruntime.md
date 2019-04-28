---
title: -vbruntime
ms.date: 03/13/2018
f1_keywords:
- vbruntime
- -vbruntime
helpviewer_keywords:
- vbruntime compiler option [Visual Basic]
- -vbruntime compiler option [Visual Basic]
- /vbruntime compiler option [Visual Basic]
ms.assetid: 1aa0239e-511a-4c29-957d-fd72877b350a
ms.openlocfilehash: a1988fcd19c6629d85ae0e739681fd39fe033c0d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61796131"
---
# <a name="-vbruntime"></a>-vbruntime
コンパイラが Visual Basic Runtime Library を参照せずにコンパイルするか、特定のランタイム ライブラリを参照してコンパイルするかを指定します。  
  
## <a name="syntax"></a>構文  
  
```  
-vbruntime:{ - | + | * | path }  
```  
  
## <a name="arguments"></a>引数  
 \-  
 Visual Basic ランタイム ライブラリへの参照なしでコンパイルします。  
  
 \+  
 既定の Visual Basic ランタイム ライブラリへの参照を使用してコンパイルします。  
  
 \*  
 Visual Basic ランタイム ライブラリへの参照なしでコンパイルされ、アセンブリに、Visual Basic ランタイム ライブラリからのコア機能を埋め込みます。  
  
 `path`  
 指定したライブラリ (DLL) への参照を使用してコンパイルします。  
  
## <a name="remarks"></a>Remarks  
 `-vbruntime`コンパイラ オプションでは、コンパイラが、Visual Basic ランタイム ライブラリへの参照しないでコンパイルされていることを指定することができます。 Visual Basic ランタイム ライブラリを参照しないでコンパイルする場合は、エラーまたは警告が Visual Basic ランタイム ヘルパーへの呼び出しを生成するコードまたは言語の構造に記録されます。 (A *Visual Basic ランタイム ヘルパー*特定言語のセマンティックを実行する実行時に呼び出される Microsoft.VisualBasic.dll で定義されている関数です)。  
  
 `-vbruntime+`オプションがない場合に発生するのと同じ動作を生成`-vbruntime`スイッチを指定します。 使用することができます、`-vbruntime+`前をオーバーライドするオプション`-vbruntime`スイッチ。  
  
 ほとんどのオブジェクトの`My`型は、使用する場合は使用できません、`-vbruntime-`または`-vbruntime:path`オプション。  
  
## <a name="embedding-visual-basic-runtime-core-functionality"></a>Visual Basic ランタイムのコア機能の埋め込み  
 `-vbruntime*`オプションでは、ランタイム ライブラリへの参照なしでコンパイルすることができます。 代わりに、Visual Basic ランタイム ライブラリからのコア機能は、ユーザー アセンブリに埋め込まれます。 Visual Basic ランタイムが含まれていないプラットフォームでアプリケーションを実行している場合は、このオプションを使用できます。  
  
 次のランタイムのメンバーが埋め込まれます。  
  
- <xref:Microsoft.VisualBasic.CompilerServices.Conversions> クラス  
  
- <xref:Microsoft.VisualBasic.Strings.AscW%28System.Char%29> メソッド  
  
- <xref:Microsoft.VisualBasic.Strings.AscW%28System.String%29> メソッド  
  
- <xref:Microsoft.VisualBasic.Strings.ChrW%28System.Int32%29> メソッド  
  
- <xref:Microsoft.VisualBasic.Constants.vbBack> 定数  
  
- <xref:Microsoft.VisualBasic.Constants.vbCr> 定数  
  
- <xref:Microsoft.VisualBasic.Constants.vbCrLf> 定数  
  
- <xref:Microsoft.VisualBasic.Constants.vbFormFeed> 定数  
  
- <xref:Microsoft.VisualBasic.Constants.vbLf> 定数  
  
- <xref:Microsoft.VisualBasic.Constants.vbNewLine> 定数  
  
- <xref:Microsoft.VisualBasic.Constants.vbNullChar> 定数  
  
- <xref:Microsoft.VisualBasic.Constants.vbNullString> 定数  
  
- <xref:Microsoft.VisualBasic.Constants.vbTab> 定数  
  
- <xref:Microsoft.VisualBasic.Constants.vbVerticalTab> 定数  
  
- 一部のオブジェクトの`My`型  
  
 使用してコンパイルする場合、`-vbruntime*`オプションと、コードは、コア機能に埋め込まれていない Visual Basic ランタイム ライブラリからメンバーを参照、コンパイラには、メンバーが使用できないことを示すエラーが返されます。  
  
## <a name="referencing-a-specified-library"></a>指定したライブラリを参照します。  
 使用することができます、 `path` Visual Basic ランタイム ライブラリの既定ではなくカスタム ランタイム ライブラリへの参照を使用してコンパイルする引数。  
  
 場合の値、`path`引数は、DLL への完全修飾パスがある場合、コンパイラでは、そのファイルは、ランタイム ライブラリとして使用します。 場合の値、 `path` DLL への完全修飾パス引数が、現在のフォルダーで識別された DLL を Visual Basic コンパイラがまず検索します。 使用して指定したパスを検索し、 [-sdkpath](../../../visual-basic/reference/command-line-compiler/sdkpath.md)コンパイラ オプション。 場合、`-sdkpath`コンパイラ オプションが使用されない場合、コンパイラは、.NET Framework フォルダーで識別された DLL の検索 (`%systemroot%\Microsoft.NET\Framework\versionNumber`)。  
  
## <a name="example"></a>例  
 次の例は、使用する方法を示します、`-vbruntime`カスタム ライブラリへの参照を使用してコンパイルするにはオプションです。  
  
```console
vbc -vbruntime:C:\VBLibraries\CustomVBLibrary.dll  
```  
  
## <a name="see-also"></a>関連項目

- [Visual Basic Core-Visual Studio 2010 SP1 での新しいコンパイル モード](https://devblogs.microsoft.com/vbteam/vb-core-new-compilation-mode-in-visual-studio-2010-sp1/)
- [Visual Basic のコマンド ライン コンパイラ](../../../visual-basic/reference/command-line-compiler/index.md)
- [コンパイル コマンド ラインのサンプル](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [-sdkpath](../../../visual-basic/reference/command-line-compiler/sdkpath.md)
