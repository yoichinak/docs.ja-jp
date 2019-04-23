---
title: -target:exe (C# コンパイラ オプション)
ms.date: 07/20/2015
f1_keywords:
- /exe
helpviewer_keywords:
- target compiler options [C#], /target:exe
- /target compiler options [C#], /target:exe
- -target compiler options [C#], /target:exe
ms.assetid: bda5717d-1b91-4848-956b-fcf85c30e432
ms.openlocfilehash: 7d34a25fd614a209761714e1f4eff3042ca240c0
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59331313"
---
# <a name="-targetexe-c-compiler-options"></a>-target:exe (C# コンパイラ オプション)
**-target:exe** オプションを指定した場合、コンパイラは実行可能な (EXE) コンソール アプリケーションを作成します。  
  
## <a name="syntax"></a>構文  
  
```console  
-target:exe  
```  
  
## <a name="remarks"></a>解説  
 **-target:exe** オプションは既定で有効になっています。 実行可能ファイルは、.exe という拡張子で作成されます。  
  
 Windows プログラムの実行可能ファイルを作成する場合は、[-target:winexe](../../../csharp/language-reference/compiler-options/target-winexe-compiler-option.md) を使用します。  
  
 [-out](../../../csharp/language-reference/compiler-options/out-compiler-option.md) オプションで指定しない限り、出力ファイル名は [Main](../../../csharp/programming-guide/main-and-command-args/index.md) メソッドを含む入力ファイルと同じになります。  
  
 コマンド ラインで指定すると、次の **-out** または **-target:module** オプションまでのすべてのファイルが .exe ファイルを作成するために使用されます。  
  
 **Main** メソッドは、.exe ファイルにコンパイルされるソース コード ファイル内に 1 つだけ必要です。 コードに **Main** メソッドを含むクラスが複数ある場合は、[-main](../../../csharp/language-reference/compiler-options/main-compiler-option.md) コンパイラ オプションを使用して、**Main** メソッドを含めるクラスを指定できます。  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 開発環境でこのコンパイラ オプションを設定するには  
  
1. プロジェクトの **[プロパティ]** ページを開きます。  
  
2. **[アプリケーション]** プロパティ ページをクリックします。  
  
3. **[出力の種類]** プロパティを変更します。  
  
 このコンパイラ オプションをプログラムで設定する方法については、「 <xref:VSLangProj80.ProjectProperties3.OutputType%2A>」をご覧ください。  
  
## <a name="example"></a>例  
 次のコマンド ラインのいずれかで `in.cs` がコンパイルされ、`in.exe` が作成されます。  
  
```console  
csc -target:exe in.cs  
csc in.cs  
```  
  
## <a name="see-also"></a>関連項目

- [-target (C# コンパイラ オプション)](../../../csharp/language-reference/compiler-options/target-compiler-option.md)
- [C# コンパイラ オプション](../../../csharp/language-reference/compiler-options/index.md)
