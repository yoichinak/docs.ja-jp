---
title: '@ (応答ファイルの指定) (Visual Basic)'
ms.date: 03/13/2018
helpviewer_keywords:
- '@ (Specify Response File) compiler option [Visual Basic]'
ms.assetid: a6847eaa-e5f9-4303-9421-45b55484b9ca
ms.openlocfilehash: 6b993a6399eec4e203821109db153aadf246cbac
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "58838119"
---
# <a name="-specify-response-file-visual-basic"></a>@ (応答ファイルの指定) (Visual Basic)
コンパイラ オプションを含むファイルをコンパイルするソース コード ファイルを指定します。  
  
## <a name="syntax"></a>構文  
  
```  
@response_file  
```  
  
## <a name="arguments"></a>引数  
 `response_file`  
 必須。 コンパイラ オプションやコンパイルするソース コード ファイルを一覧表示するファイルです。 ファイル名を引用符で囲みます ("")、スペースが含まれている場合。  
  
## <a name="remarks"></a>Remarks  
 コンパイラでは、コンパイラ オプションと、コマンドラインで指定した場合、応答ファイルで指定されたソース コード ファイルを処理します。  
  
 コンパイル時に 1 つ以上の応答ファイルを指定するには、次などの複数の応答ファイル オプションを指定します。  
  
```  
@file1.rsp @file2.rsp  
```  
  
 応答ファイルでは、複数のコンパイラ オプションおよびソース コード ファイルは、1 つの行に表示できます。 コンパイラ オプションの 1 つの仕様は、1 つの行 (複数行にまたがることはできません) に表示する必要があります。 応答ファイルで始まるコメントを持つことができます、`#`シンボル。  
  
 オプションを 1 つまたは複数の応答ファイルで指定したコマンドラインで指定されたオプションを組み合わせることができます。 コンパイラは、それらが発生すると、コマンド オプションを処理します。 そのため、コマンドライン引数は、応答ファイルに指定したオプションをオーバーライドできます。 逆に、応答ファイル内のオプションは、コマンドラインで、または他の応答ファイルで、上記のオプションをオーバーライドします。  
  
 Visual Basic では、Vbc.exe ファイルと同じディレクトリにある Vbc.rsp ファイルを提供します。 しない限り、既定では、Vbc.rsp ファイルが含まれている、`-noconfig`オプションを使用します。 詳細については、次を参照してください。 [-noconfig](../../../visual-basic/reference/command-line-compiler/noconfig.md)します。  
  
> [!NOTE]
>  `@`オプションは、Visual Studio 開発環境内からは使用できません。 コマンドラインからコンパイルする場合にのみ使用可能なです。  
  
## <a name="example"></a>例  
 サンプルの応答ファイルは、次の行です。  
  
```console
# build the first output file  
-target:exe   
-out:MyExe.exe  
source1.vb   
source2.vb  
```  
  
## <a name="example"></a>例  
 次の例では、使用する方法、`@`という名前の応答ファイル オプション`File1.rsp`します。  
  
```console
vbc @file1.rsp  
```  
  
## <a name="see-also"></a>関連項目

- [Visual Basic のコマンド ライン コンパイラ](../../../visual-basic/reference/command-line-compiler/index.md)
- [-noconfig](../../../visual-basic/reference/command-line-compiler/noconfig.md)
- [コンパイル コマンド ラインのサンプル](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
