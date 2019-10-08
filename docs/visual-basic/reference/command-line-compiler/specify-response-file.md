---
title: '@ (応答ファイルの指定) (Visual Basic)'
ms.date: 03/13/2018
helpviewer_keywords:
- '@ (Specify Response File) compiler option [Visual Basic]'
ms.assetid: a6847eaa-e5f9-4303-9421-45b55484b9ca
ms.openlocfilehash: deab111cc669941a1cd7dc143dd699b6521221bb
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/07/2019
ms.locfileid: "72004991"
---
# <a name="-specify-response-file-visual-basic"></a>@ (応答ファイルの指定) (Visual Basic)
コンパイルするコンパイラオプションとソースコードファイルを含むファイルを指定します。  
  
## <a name="syntax"></a>構文  
  
```console  
@response_file  
```  
  
## <a name="arguments"></a>引数  
 `response_file`  
 必須。 コンパイルするコンパイラオプションまたはソースコードファイルの一覧を示すファイル。 ファイル名にスペースが含まれている場合は、ファイル名を引用符 ("") で囲みます。  
  
## <a name="remarks"></a>コメント  
 コンパイラは、応答ファイルで指定されたコンパイラオプションとソースコードファイルを、コマンドラインで指定されているかのように処理します。  
  
 1つのコンパイルで複数の応答ファイルを指定するには、次のような複数の応答ファイルオプションを指定します。  
  
```console  
@file1.rsp @file2.rsp  
```  
  
 応答ファイルでは、複数のコンパイラオプションとソースコードファイルを1行に記述できます。 1つのコンパイラオプションの指定は、1行に記述する必要があります (複数行にまたがることはできません)。 応答ファイルには、@no__t 0 記号で始まるコメントを含めることができます。  
  
 コマンドラインで指定されたオプションを1つ以上の応答ファイルで指定されたオプションと組み合わせることができます。 コンパイラは、コマンドオプションが検出されたときにそのオプションを処理します。 したがって、コマンドライン引数を使用すると、応答ファイルの以前に一覧表示されたオプションをオーバーライドできます。 反対に、応答ファイルのオプションは、コマンドラインまたは他の応答ファイルで前述したオプションよりも優先されます。  
  
 Visual Basic には、Vbc.exe ファイルと同じディレクトリにある Vbc.exe ファイルが用意されています。 @No__t-0 オプションを使用しない限り、Vbc.exe ファイルは既定で含まれます。 詳細については、「 [-noconfig](../../../visual-basic/reference/command-line-compiler/noconfig.md)」を参照してください。  
  
> [!NOTE]
> @No__t-0 オプションは、Visual Studio 開発環境内からは使用できません。これは、コマンドラインからコンパイルする場合にのみ使用できます。  
  
## <a name="example"></a>例  
 次の行は、応答ファイルの例です。  
  
```console
# build the first output file  
-target:exe   
-out:MyExe.exe  
source1.vb   
source2.vb  
```  
  
## <a name="example"></a>例  
 次の例では、`@` オプションを `File1.rsp` という名前の応答ファイルと共に使用する方法を示します。  
  
```console
vbc @file1.rsp  
```  
  
## <a name="see-also"></a>関連項目

- [Visual Basic のコマンド ライン コンパイラ](../../../visual-basic/reference/command-line-compiler/index.md)
- [-noconfig](../../../visual-basic/reference/command-line-compiler/noconfig.md)
- [コンパイル コマンド ラインのサンプル](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
