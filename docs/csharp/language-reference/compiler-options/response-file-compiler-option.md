---
title: '@ (C# コンパイラ オプション)'
ms.date: 07/20/2015
f1_keywords:
- '@'
helpviewer_keywords:
- response files, specifying for compilation [C#]
- '@ compiler option'
ms.assetid: dda4fa9f-a02c-400f-8b6a-d58834e13d7f
ms.openlocfilehash: 1884230f1779f9d425ef6e54cda6967c8e51d985
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/19/2019
ms.locfileid: "69602484"
---
# <a name="-c-compiler-options"></a>@ (C# コンパイラ オプション)
@ オプションを使用すると、コンパイラ オプションおよびコンパイルするソース コード ファイルを含むファイルを指定できます。  
  
## <a name="syntax"></a>構文  
  
```  
@response_file  
```  
  
## <a name="arguments"></a>引数  
 `response_file`  
 コンパイラ オプションやコンパイルするソース コード ファイルの一覧を含むファイルです。  
  
## <a name="remarks"></a>解説  
 コンパイラ オプションとソース コード ファイルは、コマンド ラインで指定した場合と同じように、コンパイラによって処理されます。  
  
 コンパイル時に複数の応答ファイルを指定するには、複数の応答ファイル オプションを指定します。 次に例を示します。  
  
```  
@file1.rsp @file2.rsp  
```  
  
 応答ファイルでは、複数のコンパイラ オプションとソース コード ファイルを 1 行に記述できます。 1 つのコンパイラ オプションは 1 行に指定する必要があり、複数行にわたって指定できません。 応答ファイルには、シャープ記号 (#) で始まるコメントを記述できます。  
  
 応答ファイルでのコンパイラ オプションの指定方法は、コマンド ラインでのコンパイラ オプションの指定方法と同じです。 詳細については、「[Building from the Command Line](./how-to-set-environment-variables-for-the-visual-studio-command-line.md)」(コマンド ラインからのビルド) を参照してください。  
  
 コンパイラは、検出した順にコマンド オプションを処理します。 このため、コマンド ライン引数によって、応答ファイルで先に指定したオプションをオーバーライドできます。 逆に、応答ファイルのオプションが、コマンド ラインや他の応答ファイルで先に指定したオプションをオーバーライドすることもあります。  
  
 C# では、csc.exe ファイルと同じディレクトリに csc.rsp ファイルがあります。 csc.rsp の詳細については、「[-noconfig](./noconfig-compiler-option.md)」を参照してください。  
  
 このコンパイラ オプションは、Visual Studio 開発環境で設定することはできません。また、プログラムで変更することもできません。  
  
## <a name="example"></a>例  
 サンプルの応答ファイルの一部を次に示します。  
  
```console  
# build the first output file  
-target:exe -out:MyExe.exe source1.cs source2.cs  
```  
  
## <a name="see-also"></a>関連項目

- [C# コンパイラ オプション](./index.md)
