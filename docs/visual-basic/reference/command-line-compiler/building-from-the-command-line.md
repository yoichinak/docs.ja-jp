---
title: コマンド ラインからのビルド (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- builds [Visual Basic], command-line
- Visual Basic compiler, about Visual Basic compiler
- command line [Visual Basic], compilers
- command line [Visual Basic], building from
- command line [Visual Basic], builds
- compilers [Visual Basic], invoking from command line
- command-line builds
- compiling source code
- command-line compilers [Visual Basic], Visual Basic
- command line [Visual Basic], Visual Basic
ms.assetid: e61947e9-a42e-4717-a699-5f70a98cdd03
ms.openlocfilehash: 798baa90308c83e42b335635fb23a9983f5180fb
ms.sourcegitcommit: facefcacd7ae2e5645e463bc841df213c505ffd4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/05/2019
ms.locfileid: "55739476"
---
# <a name="building-from-the-command-line-visual-basic"></a>コマンド ラインからのビルド (Visual Basic)
Visual Basic プロジェクトでは、1 つ以上の別のソース ファイルの構成されます。 コンパイルと呼ばれるプロセス中にこれらのファイルが 1 つのパッケージにまとめられて — アプリケーションとして実行できる 1 つの実行可能ファイルです。  
  
 Visual Basic では、Visual Studio 統合開発環境 (IDE) 内からプログラムをコンパイルする代わりに、コマンド ライン コンパイラを提供します。 コマンド ライン コンパイラが状況を必要としない IDE の機能の完全なセット用に設計されたなどとを使用する限られたシステムのメモリまたは記憶域スペースを持つコンピューターの書き込み。  
  
  Visual Studio IDE 内からソース ファイルをコンパイルするには、選択、**ビルド**コマンドを**ビルド**メニュー。  
  
> [!TIP]
>  関連付けられているに関する情報を表示するには、Visual Studio IDE を使用してプロジェクト ファイルをビルドするときに**vbc**コマンドと、出力ウィンドウにそのスイッチ。 この情報を表示するには、開く、[オプション ダイアログ ボックス、プロジェクトとソリューションをビルドおよび実行](/visualstudio/ide/reference/options-dialog-box-projects-and-solutions-build-and-run)、し、設定、 **MSBuild プロジェクト ビルドの出力の詳細**に**標準**または、詳細度の高いレベル。 詳細については、「[方法 :ビルド ログ ファイルの構成を表示、保存、および](/visualstudio/ide/how-to-view-save-and-configure-build-log-files)します。  
  
 MSBuild を使用してコマンド プロンプトで、プロジェクト (.vbproj) ファイルをコンパイルすることができます。 詳細については、次を参照してください。[コマンド ライン リファレンス](/visualstudio/msbuild/msbuild-command-line-reference)と[チュートリアル:MSBuild の使用](/visualstudio/msbuild/walkthrough-using-msbuild)に関するページを参照してください。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [方法: コマンド ライン コンパイラを起動する](../../../visual-basic/reference/command-line-compiler/how-to-invoke-the-command-line-compiler.md)  
 MS-DOS のプロンプトで、または特定のサブディレクトリからのコマンド ライン コンパイラを起動する方法について説明します。  
  
 [コンパイル コマンド ラインのサンプル](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 独自の用途を変更するコマンドラインのサンプルの一覧を示します。  
  
## <a name="related-sections"></a>関連項目  
 [Visual Basic のコマンド ライン コンパイラ](../../../visual-basic/reference/command-line-compiler/index.md)  
 アルファベット順または目的別に整理のコンパイラ オプションの一覧を提供します。  
  
 [条件付きコンパイル](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)  
 特定のセクションのコードをコンパイルする方法について説明します。  
  
 [Visual Studio でのプロジェクトとソリューションのビルドおよびクリーン](/visualstudio/ide/building-and-cleaning-projects-and-solutions-in-visual-studio)  
 対象はさまざまなビルドに含まれます、プロジェクトのプロパティ を選択およびプロジェクトの正しい順序でビルドを整理する方法について説明します。
