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
ms.openlocfilehash: 719ca45403ea56a655f06dbfea7c0fb7e32b34f7
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2019
ms.locfileid: "70046429"
---
# <a name="building-from-the-command-line-visual-basic"></a>コマンド ラインからのビルド (Visual Basic)

Visual Basic のプロジェクトは、1つまたは複数の個別のソースファイルで構成されます。 コンパイルと呼ばれるプロセスでは、これらのファイルが1つのパッケージ (アプリケーションとして実行できる1つの実行可能ファイル) にまとめられます。

Visual Basic は、Visual Studio 統合開発環境 (IDE) 内からプログラムをコンパイルする代わりに、コマンドラインコンパイラを提供します。 コマンドラインコンパイラは、システムメモリまたは記憶域スペースが制限されているコンピューターを使用したり、書き込みを行ったりする場合など、IDE のすべての機能を必要としない場合に適しています。

Visual Studio IDE 内からソースファイルをコンパイルするには、 **[ビルド]** メニューの **[ビルド]** をクリックします。

> [!TIP]
> Visual Studio IDE を使用してプロジェクトファイルをビルドする場合、関連付けられている**vbc.exe**コマンドとそのスイッチに関する情報を出力ウィンドウに表示できます。 この情報を表示するには、[オプション] ダイアログボックス、[プロジェクトとソリューション]、[ビルドと実行](/visualstudio/ide/reference/options-dialog-box-projects-and-solutions-build-and-run)] の順に開き、 **MSBuild プロジェクトのビルド出力の詳細**レベルを **[標準]** または [高レベルの詳細 に設定します。 詳細については、「[方法 :ビルドログファイル](/visualstudio/ide/how-to-view-save-and-configure-build-log-files)を表示、保存、および構成します。

MSBuild を使用してコマンド プロンプトで、プロジェクト (.vbproj) ファイルをコンパイルすることができます。 詳細については、次を参照してください。[コマンド ライン リファレンス](/visualstudio/msbuild/msbuild-command-line-reference)と[チュートリアル:MSBuild の使用](/visualstudio/msbuild/walkthrough-using-msbuild)に関するページを参照してください。

## <a name="in-this-section"></a>このセクションの内容

[方法: コマンドラインコンパイラを起動します。](../../../visual-basic/reference/command-line-compiler/how-to-invoke-the-command-line-compiler.md) \
MS-DOS プロンプトまたは特定のサブディレクトリからコマンドラインコンパイラを呼び出す方法について説明します。

[コンパイルコマンドラインのサンプル](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md) \
独自に使用するために変更できるサンプルコマンドラインの一覧を示します。

## <a name="related-sections"></a>関連項目

[Visual Basic のコマンド ライン コンパイラ](../../../visual-basic/reference/command-line-compiler/index.md) \
アルファベット順または目的別に構成された、コンパイラオプションの一覧を提供します。

[条件付きコンパイル](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md) \
コードの特定のセクションをコンパイルする方法について説明します。

[Visual Studio でのプロジェクトとソリューションのビルドおよびクリーン](/visualstudio/ide/building-and-cleaning-projects-and-solutions-in-visual-studio) \
さまざまなビルドに含まれる内容を整理し、プロジェクトのプロパティを選択し、プロジェクトが正しい順序でビルドされるようにする方法について説明します。
