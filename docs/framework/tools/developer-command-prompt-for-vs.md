---
title: Visual Studio 用開発者コマンド プロンプト
ms.date: 08/14/2018
helpviewer_keywords:
- command prompt, Windows SDK
- Visual Studio command prompt
- command prompt, Visual Studio
- SDK command prompt
- tools [.NET Framework], setting environment variables
- environment variables, setting for tools
- developer command prompt
ms.assetid: 94fcf524-9045-4993-bfb2-e2d8bad44219
author: mairaw
ms.author: mairaw
ms.openlocfilehash: cc88106a54a00b4b12e5043da7961791a98102c0
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59344365"
---
# <a name="developer-command-prompt-for-visual-studio"></a>Visual Studio 用開発者コマンド プロンプト

Visual Studio 用開発者コマンド プロンプトでは、.NET Framework ツールをもっと簡単に使用できます。 それは、特定の環境変数を自動的に設定するコマンド プロンプトです。

> [!div class="button"]
> [Visual Studio のダウンロード](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2019)

## <a name="search-for-the-command-prompt-on-your-machine"></a>コンピューター上でのコマンド プロンプトの検索

Visual Studio のバージョンと、インストールした追加の SDK に応じて、複数のコマンド プロンプトがある場合があります。 たとえば、Visual Studio の 64 ビット バージョンには、32 ビットと 64 ビットのコマンド プロンプトが用意されています (ほとんどのツールでは、32 ビット バージョンと 64 ビット バージョンに違いはありませんが、一部のツールでは、32 ビット環境と 64 ビット環境に固有の変更が加えられています)。次の手順でうまくいかない場合は、「[コンピューター上のファイルを手動で探す](#manually-locate-the-files-on-your-machine)」または「[Visual Studio 内からコマンド プロンプトを実行する](#run-the-command-prompt-from-inside-visual-studio)」を試してください。

### <a name="in-windows-10"></a>Windows 10 の場合

1. タスクバーの検索ボックスに、`dev` や `developer command prompt` など、ツールの名前を入力します。 検索パターンに一致する、インストールされているアプリの一覧が表示されます。 別のコマンド プロンプトを探す場合は、別の検索語句 (「`prompt`」など) を入力してください。

2. **Visual Studio 用開発者コマンド プロンプト** (または、使用するコマンド プロンプト) を選択します。

### <a name="in-windows-81"></a>Windows 8.1 の場合

1. キーボードの Windows ロゴ キー ![Windows ロゴ](../get-started/media/windowskeyboardlogo.png "Windowskeyboardlogo") を押すなどして、**[スタート]** 画面に移動します。

2. **[スタート]** 画面で、**Ctrl**+**Tab** キーを押して **[アプリ]** の一覧を開き、`V`.と入力します。 インストールされているすべての Visual Studio コマンド プロンプトが含まれた一覧が表示されます。

3. **[開発者コマンド プロンプト]** (または、使用するコマンド プロンプト) を選択します。

### <a name="in-windows-8"></a>Windows 8 の場合

1. キーボードの Windows ロゴ キー ![Windows ロゴ](../get-started/media/windowskeyboardlogo.png "Windowskeyboardlogo") を押すなどして、**[スタート]** 画面に移動します。

2. **[スタート]** 画面で、Windows ロゴ キー ![Windows ロゴ](../get-started/media/windowskeyboardlogo.png "Windowskeyboardlogo") `+ Z` を押します。

3. 画面下部にある**アプリ ビュー** アイコンを選択し、「`V`」と入力します。 インストールされているすべての Visual Studio コマンド プロンプトが含まれた一覧が表示されます。

4. **[開発者コマンド プロンプト]** (または、使用するコマンド プロンプト) を選択します。

### <a name="in-windows-7"></a>Windows 7 の場合

1. **[スタート]** を選択し、**[すべてのプログラム]**、**[Microsoft Visual Studio]** の順に展開します。

2. インストールされている Visual Studio のバージョンに応じて、**[Visual Studio Tools]**、**[Visual Studio コマンド プロンプト]**、または使用するコマンド プロンプトを選択します。

[Windows 10 SDK](https://developer.microsoft.com/windows/downloads/windows-10-sdk) や[それ以前のバージョン](https://developer.microsoft.com/windows/downloads/sdk-archive)など、他の SDK をインストールしている場合、ARM、x86、または x64 の各アーキテクチャ用のコマンド プロンプトがさらに表示されることがあります。 各ツールのドキュメントを参照して、どのバージョンのコマンド プロンプトを使用する必要があるかを確認してください。

## <a name="manually-locate-the-files-on-your-machine"></a>コンピューター上のファイルを手動で探す

インストール済みのコマンド プロンプトのショートカットは、通常 Visual Studio の **[スタート] メニュー**用のフォルダー (C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Visual Studio 2017\Visual Studio Tools 内など) にあります。 ただし、コマンド プロンプトを探しても、何らかの理由によって期待した結果を得られない場合は、コンピューター上でそのショートカットを手動で探すことができます。 *VsDevCmd.bat* などのコマンド プロンプトのファイル名を検索するか、または Tools フォルダー (C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\Common7\Tools など) に移動します (パスは、Visual Studio のバージョン、エディション、およびインストール先に応じて変わります)。

## <a name="run-the-command-prompt-from-inside-visual-studio"></a>Visual Studio 内からコマンド プロンプトを実行する

簡単にアクセスできるように、Visual Studio の開発者コマンド プロンプトまたは他のコマンド プロンプトを Visual Studio の **[ツール]** メニューに追加することができます。 ツールを使用できるようにするには、外部ツール一覧にそれを追加します。 次に手順を示します。

1. Visual Studio を開きます。

2. **[ツール]** メニューを選択し、**[外部ツール]** を選択します。

3. **[外部ツール]** ダイアログ ボックスで、**[追加]** ボタンをクリックします。 新しいエントリが表示されます。

4. 新しいメニュー項目の **[タイトル]** を入力します (「`Command Prompt`」など)。

5. **[コマンド]** フィールドに、起動するファイル (`%comspec%` や `C:\Windows\System32\cmd.exe` など) を指定します。

6. **[引数]** フィールドに、使用する特定のコマンド プロンプトのある場所を指定します (`/k "C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\Common7\Tools\VsDevCmd.bat"` など。このコマンドでは、Visual Studio 2017 Enterprise でインストールされた開発者コマンド プロンプトが起動されます)。 この値は、Visual Studio のバージョン、エディション、インストール先に応じて変更します。

7. **[初期ディレクトリ]** フィールドの値 (**[プロジェクト ディレクトリ]** など) を選択します。

8. **[OK]** を選択します。

   新しいメニュー項目が追加され、このコマンド プロンプトに **[ツール]** メニューからアクセスできるようになります。

   ![Visual Studio でのコマンド プロンプト メニュー項目](media/command-prompt-vs-menu.png)

## <a name="see-also"></a>関連項目

- [ツール](../../../docs/framework/tools/index.md)
- [Visual Studio の外部ツール](/visualstudio/ide/managing-external-tools)
