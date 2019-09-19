---
title: '方法: コマンドラインコンパイラ (Visual Basic) を起動します。'
ms.date: 07/20/2015
helpviewer_keywords:
- command-line arguments
- vbc.exe
- Visual Basic compiler, starting
- command line [Visual Basic], arguments
ms.assetid: 0fd9a8f6-f34e-4c35-a49d-9b9bbd8da4a9
ms.openlocfilehash: a81d5b4f4eae76b0306e2d27475cb8527bda0ff2
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/17/2019
ms.locfileid: "71054215"
---
# <a name="how-to-invoke-the-command-line-compiler-visual-basic"></a>方法: コマンドラインコンパイラ (Visual Basic) を起動します。

コマンドラインコンパイラを起動するには、実行可能ファイルの名前をコマンドラインに入力します (MS-DOS プロンプトとも呼ばれます)。 既定の Windows コマンドプロンプトからコンパイルする場合は、実行可能ファイルへの完全修飾パスを入力する必要があります。 この既定の動作をオーバーライドするには、Visual Studio の開発者コマンドプロンプトを使用するか、または PATH 環境変数を変更します。 どちらの方法でも、コンパイラ名を入力するだけで、任意のディレクトリからコンパイルできます。

[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]

## <a name="to-invoke-the-compiler-using-the-developer-command-prompt-for-visual-studio"></a>Visual Studio の開発者コマンドプロンプトを使用してコンパイラを呼び出すには

1. Microsoft Visual Studio プログラムグループ内の Visual Studio Tools program フォルダーを開きます。

2. Visual studio がインストールされている場合は、Visual Studio の開発者コマンドプロンプトを使用して、コンピューター上の任意のディレクトリからコンパイラにアクセスできます。

3. Visual Studio の開発者コマンドプロンプトを起動します。

4. コマンドラインで、「 `vbc.exe` *sourcefilename* 」と入力し、enter キーを押します。

    たとえば、というディレクトリにソースコードを格納した場合`SourceFiles`は、コマンドプロンプトを開き、「」 `cd SourceFiles`と入力してそのディレクトリに変更します。 ディレクトリにという名前のソースファイル`Source.vb`が含まれている場合は`vbc.exe Source.vb`、「」と入力してコンパイルできます。

## <a name="to-set-the-path-environment-variable-to-the-compiler-for-the-windows-command-prompt"></a>Windows のコマンドプロンプト用に PATH 環境変数をコンパイラに設定するには

1. Windows 検索機能を使用して、ローカルディスクで Vbc.exe を検索します。

    コンパイラが配置されているディレクトリの正確な名前は、Windows ディレクトリの場所とインストールされている ".NET Framework" のバージョンによって異なります。 ".NET Framework" の複数のバージョンがインストールされている場合は、使用するバージョン (通常は最新バージョン) を決定する必要があります。

2. **[スタート]** メニューの **[マイコンピューター]** を右クリックし、ショートカットメニューの **[プロパティ]** をクリックします。

3. **[詳細設定]** タブをクリックし、 **[環境変数]** をクリックします。

4. **[システム]** 変数 ペインで、一覧から **[パス]** を選択し、 **[編集]** をクリックします。

5. システム変数の **[編集]** ダイアログボックスで、 **[変数の値]** フィールドの文字列の末尾にカーソルを移動し、セミコロン (;) を入力します。の後に、手順 1. で見つかった完全なディレクトリ名を指定します。

6. **[OK]** をクリックして編集内容を確認し、ダイアログボックスを閉じます。

     PATH 環境変数を変更した後、コンピューター上の任意のディレクトリから Windows コマンドプロンプトで Visual Basic コンパイラを実行できます。

## <a name="to-invoke-the-compiler-using-the-windows-command-prompt"></a>Windows のコマンドプロンプトを使用してコンパイラを呼び出すには

1. **[スタート]** メニューの **[アクセサリ]** フォルダーをクリックし、 **Windows コマンドプロンプト**を開きます。

2. コマンドラインで、「 `vbc.exe` *sourcefilename* 」と入力し、enter キーを押します。

     たとえば、というディレクトリにソースコードを格納した場合`SourceFiles`は、コマンドプロンプトを開き、「」 `cd SourceFiles`と入力してそのディレクトリに変更します。 ディレクトリにという名前のソースファイル`Source.vb`が含まれている場合は`vbc.exe Source.vb`、「」と入力してコンパイルできます。

## <a name="see-also"></a>関連項目

- [Visual Basic のコマンド ライン コンパイラ](../../../visual-basic/reference/command-line-compiler/index.md)
- [条件付きコンパイル](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)
