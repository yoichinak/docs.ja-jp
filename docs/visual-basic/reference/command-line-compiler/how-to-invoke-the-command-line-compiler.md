---
title: '方法: コマンド ライン コンパイラ (Visual Basic) を呼び出す'
ms.date: 07/20/2015
helpviewer_keywords:
- command-line arguments
- vbc.exe
- Visual Basic compiler, starting
- command line [Visual Basic], arguments
ms.assetid: 0fd9a8f6-f34e-4c35-a49d-9b9bbd8da4a9
ms.openlocfilehash: 67cad0df3f10ff1fa1f6a58546fe150232fe1283
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/09/2019
ms.locfileid: "59302804"
---
# <a name="how-to-invoke-the-command-line-compiler-visual-basic"></a>方法: コマンド ライン コンパイラ (Visual Basic) を呼び出す
コマンドライン プロンプトとも呼ばれますにその実行可能ファイルの名前を入力して、コマンド ライン コンパイラを呼び出すことができます。 既定の Windows コマンド プロンプトからコンパイルする場合は、実行可能ファイルへの完全修飾パスを入力する必要があります。 この既定の動作を上書きするには、for Visual Studio は、開発者コマンド プロンプトを使用するか、PATH 環境変数を変更します。 コンパイラの名前を入力するだけで、任意のディレクトリからコンパイルをどちらもができます。  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-invoke-the-compiler-using-the-developer-command-prompt-for-visual-studio"></a>Visual Studio 用開発者コマンド プロンプトを使用してコンパイラを起動するには  
  
1. Microsoft Visual Studio のプログラム グループ内の Visual Studio Tools のプログラム フォルダーを開きます。  
  
2. Visual Studio がインストールされている場合は、任意のディレクトリからコンピューターには、コンパイラにアクセスする Visual Studio 用開発者コマンド プロンプトを使用できます。  
  
3. Visual Studio 用開発者コマンド プロンプトを呼び出します。  
  
4. コマンドラインで「 `vbc.exe` *sourceFileName*し、ENTER キーを押します。  
  
     という名前のディレクトリで、ソース コードが格納されている場合など、 `SourceFiles`、コマンド プロンプトと種類を開くと`cd SourceFiles`そのディレクトリに変更します。 ディレクトリには、という名前のソース ファイルが含まれている場合`Source.vb`、」と入力してコンパイルする`vbc.exe Source.vb`します。  
  
### <a name="to-set-the-path-environment-variable-to-the-compiler-for-the-windows-command-prompt"></a>Windows コマンド プロンプトをコンパイラに PATH 環境変数を設定するには  
  
1. Windows Search の機能を使用して、ローカル ディスク上の Vbc.exe を検索します。  
  
     コンパイラがあるディレクトリの正確な名前は、Windows ディレクトリの場所とインストール".NET Framework"のバージョンによって異なります。 ".NET Framework"インストールされているは、複数のバージョンがあれば、(通常は最新のバージョン) を使用するバージョンを決定する必要があります。  
  
2. **開始** メニューを右クリックして**マイ コンピューター**、順にクリックします**プロパティ**ショートカット メニューから。  
  
3. をクリックして、**詳細** タブをクリックして**環境変数**します。  
  
4. **システム**変数ウィンドウで、**パス** をクリックし、リストから**編集**します。  
  
5. **編集システム**変数 ダイアログ ボックスで文字列の末尾にカーソルを移動、**変数値**フィールドし、セミコロン (;) を入力後に手順 1. で見つかった完全なディレクトリ名。  
  
6. クリックして**OK**を編集内容を確認し、ダイアログ ボックスを閉じます。  
  
     PATH 環境変数を変更した後行うことができます、Visual Basic コンパイラ、Windows コマンド プロンプトで任意のディレクトリからコンピューターにします。  
  
### <a name="to-invoke-the-compiler-using-the-windows-command-prompt"></a>Windows コマンド プロンプトを使用してコンパイラを起動するには  
  
1. **開始** メニューをクリックして、**アクセサリ**フォルダー、および順に開いて、 **Windows コマンド プロンプト**。  
  
2. コマンドラインで「 `vbc.exe` *sourceFileName*し、ENTER キーを押します。  
  
     という名前のディレクトリで、ソース コードが格納されている場合など、 `SourceFiles`、コマンド プロンプトと種類を開くと`cd SourceFiles`そのディレクトリに変更します。 ディレクトリには、という名前のソース ファイルが含まれている場合`Source.vb`、」と入力してコンパイルする`vbc.exe Source.vb`します。  
  
## <a name="see-also"></a>関連項目

- [Visual Basic のコマンド ライン コンパイラ](../../../visual-basic/reference/command-line-compiler/index.md)
- [条件付きコンパイル](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)
