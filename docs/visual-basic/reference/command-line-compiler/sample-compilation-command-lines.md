---
title: コンパイル コマンド ラインのサンプル
ms.date: 03/13/2018
helpviewer_keywords:
- command line [Visual Basic], compilers
- compilation [Visual Basic], command-line
- command-line compilers
- compiling source code [Visual Basic], from command line
- Visual Basic compiler, sample command lines
ms.assetid: 5bfbb487-5f47-4267-969a-39dfb917beeb
ms.openlocfilehash: 27a20a5a3525353ffbced729b8ac9c98b3e48fc1
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350856"
---
# <a name="sample-compilation-command-lines-visual-basic"></a>コンパイル コマンド ラインのサンプル (Visual Basic)

Visual Studio 内から Visual Basic プログラムをコンパイルする代わりに、コマンド ラインからコンパイルして、実行可能 (.exe) ファイルまたはダイナミックリンク ライブラリ (.dll) ファイルを生成することができます。

Visual Basic のコマンドライン コンパイラでは、入力および出力ファイル、アセンブリ、デバッグおよびプリプロセッサ オプションを制御するオプションの完全なセットがサポートされます。 各オプションは、`-option` と `/option` の 2 つの交換可能な形式で使用できます。 このドキュメントでは、`-option` 形式のみを示します。

次の表に、自分で使用するために変更できるコマンド ラインのサンプルをいくつか一覧表示します。

|終了|使用|
|--------|---------|
|File.vb をコンパイルし、File.exe を作成する|`vbc -reference:Microsoft.VisualBasic.dll File.vb`|
|File.vb をコンパイルし、File.dll を作成する|`vbc -target:library File.vb`|
|File.vb をコンパイルし、My.exe を作成する|`vbc -out:My.exe File.vb`|
|File.vb をコンパイルし、ライブラリ、および File.dll という名前の参照アセンブリの両方を作成する|`vbc -target:library -ref:.\debug\bin\ref\file.dll File.vb`|
|最適化を有効にし、`DEBUG` シンボルを定義して、現在のディレクトリにあるすべての Visual Basic ファイルをコンパイルし、File2.exe を生成する|`vbc -define:DEBUG=1 -optimize -out:File2.exe *.vb`|
|現在のディレクトリにあるすべての Visual Basic ファイルをコンパイルし、ロゴや警告を表示せずに、File2.dll のデバッグ バージョンを生成する|`vbc -target:library -out:File2.dll -nowarn -nologo -debug *.vb`|
|現在のディレクトリにあるすべての Visual Basic ファイルをコンパイルし、Something.dll に出力する|`vbc -target:library -out:Something.dll *.vb`|

> [!TIP]
> Visual Studio IDE を使用してプロジェクトをビルドする場合、関連する **vbc** コマンドに関する情報をそのコンパイラ オプションと共に出力ウィンドウに表示できます。 この情報を表示するには、[[オプション] ダイアログ ボックス、[プロジェクトおよびソリューション]、[ビルド/実行]](/visualstudio/ide/reference/options-dialog-box-projects-and-solutions-build-and-run) の順に開き、 **[MSBuild プロジェクト ビルドの出力の詳細]** を **[通常]** またはそれ以上の詳細レベルに設定します。

## <a name="see-also"></a>関連項目

- [Visual Basic のコマンド ライン コンパイラ](../../../visual-basic/reference/command-line-compiler/index.md)
- [条件付きコンパイル](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)
