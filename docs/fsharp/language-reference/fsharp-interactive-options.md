---
title: F# Interactive オプション
description: サポートされているコマンド ライン オプションについて説明しますF#対話形式で、fsi.exe します。
ms.date: 05/16/2016
ms.openlocfilehash: cca1ef6671878acb1b837d6590139d5de7b7167d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61996802"
---
# <a name="f-interactive-options"></a>F# Interactive オプション

> [!NOTE]
> この記事では、現時点の Windows のエクスペリエンスについてのみ説明します。  書き換えられる予定です。

このトピックでは、F# Interactive (`fsi.exe`) でサポートされるコマンド ライン オプションについて説明します。 F# Interactive では、F# コンパイラと同じコマンド ライン オプションを数多く使用できますが、その他にもいくつかのオプションを使用できます。

## <a name="using-f-interactive-for-scripting"></a>F# Interactive を使用したスクリプトの実行
F#対話型、`fsi.exe`対話形式で起動することや、スクリプトを実行するコマンドラインから起動できます。 コマンド ラインの構文は次のとおりです。

```
> fsi.exe [options] [ script-file [arguments] ]
```

F# スクリプト ファイルのファイル拡張子は `.fsx` です。

## <a name="table-of-f-interactive-options"></a>F# Interactive のオプションの表
次の表は、F# Interactive でサポートされるオプションの一覧です。 これらのオプションをコマンド ラインまたは Visual Studio IDE で設定できます。 Visual Studio IDE でこれらのオプションを設定するには、開く、**ツール**メニューの **オプション.** の順に展開、  **F#ツール**ノード **F# Interactive**します。

F# Interactive オプションの引数でリストを指定する場合は、リストの要素をセミコロン (`;`) で区切ります。

|オプション|説明|
|------|-----------|
|**--**|よう指示するために使用F#Interactive コマンドライン引数として残りの引数を処理する、F#プログラムまたはスクリプトで、一覧を使用してコードでアクセスできる**fsi.CommandLineArgs**します。|
|**--checked**[**+**&#124;**-**]|同じ、 **fsc.exe**コンパイラ オプション。 詳細については、「[コンパイラ オプション](compiler-options.md)」を参照してください。|
|**--codepage:&lt;int&gt;**|同じ、 **fsc.exe**コンパイラ オプション。 詳細については、「[コンパイラ オプション](compiler-options.md)」を参照してください。|
|**--consolecolors**[**+**&#124;**-**]|警告の出力とエラー メッセージを色付きでします。|
|**--crossoptimize**[**+**&#124;**-**]|モジュール間の最適化を有効または無効にします。|
|**--debug**[**+**&#124;**-**]<br /><br />**--debug:**[**full**&#124;**pdbonly**&#124;**portable**&#124;**embedded**]<br /><br />**-g**[**+**&#124;**-**]<br /><br />**-g:**[**full**&#124;**pdbonly**&#124;**portable**&#124;**embedded**]|同じ、 **fsc.exe**コンパイラ オプション。 詳細については、「[コンパイラ オプション](compiler-options.md)」を参照してください。|
|**--define:&lt;string&gt;**|同じ、 **fsc.exe**コンパイラ オプション。 詳細については、「[コンパイラ オプション](compiler-options.md)」を参照してください。|
|**--deterministic**[**+**&#124;**-**]|(モジュールのバージョン GUID、タイムスタンプを含む) の決定論的アセンブリを生成します。|
|**--exec**|ファイルを読み込んだ後、またはコマンド ラインで指定したスクリプトを実行した後に F# Interactive を終了するように指示します。|
|**--fullpaths**|同じ、 **fsc.exe**コンパイラ オプション。 詳細については、「[コンパイラ オプション](compiler-options.md)」を参照してください。|
|**--gui**[**+**&#124;**-**]|Windows フォーム イベントのループを有効または無効にします。 既定ではオンです。|
|**--help**<br /><br />**-?**|各オプションのコマンド ライン構文と簡単な説明を表示するために使用します。|
|**--lib:&lt;folder-list&gt;**<br /><br />**-I:&lt;folder-list&gt;**|同じ、 **fsc.exe**コンパイラ オプション。 詳細については、「[コンパイラ オプション](compiler-options.md)」を参照してください。|
|**--load:&lt;filename&gt;**|指定したソース コードを起動時にコンパイルし、コンパイルされた F# の構成要素をセッションに読み込みます。 など、ターゲットのソースにスクリプト ディレクティブが含まれている場合 **#use**または **#load**、使用する必要がありますし、 **--を使用して、** または **#use** ではなく **--読み込む**または **#load**します。|
|**--mlcompatibility**|同じ、 **fsc.exe**コンパイラ オプション。 詳細については、「[コンパイラ オプション](compiler-options.md)」を参照してください。|
|**--noframework**|同じ、 **fsc.exe**コンパイラ オプション。 詳細については、次を参照してください[コンパイラ オプション。](compiler-options.md)|
|**--nologo**|同じ、 **fsc.exe**コンパイラ オプション。 詳細については、「[コンパイラ オプション](compiler-options.md)」を参照してください。|
|**--nowarn:&lt;warning-list&gt;**|同じ、 **fsc.exe**コンパイラ オプション。 詳細については、「[コンパイラ オプション](compiler-options.md)」を参照してください。|
|**--optimize**[**+**&#124;**-**]|同じ、 **fsc.exe**コンパイラ オプション。 詳細については、「[コンパイラ オプション](compiler-options.md)」を参照してください。|
|**--preferreduilang:&lt;lang&gt;**| (たとえば、ES-ES、JA-JP) 出力用言語のカルチャ名を指定します。 |
|**--quiet**|抑制F#対話型の出力を**stdout**ストリーム。|
|**--quotations-debug**|追加のデバッグ情報が F# 引用符リテラルとリフレクション定義から派生した式に対して生成されるように指定します。 デバッグ情報は F# 式ツリー ノードのカスタム属性に追加されます。 参照してください[コード クォート](code-quotations.md)と[Expr.CustomAttributes](https://msdn.microsoft.com/library/eb89943f-5f5b-474e-b125-030ca412edb3)します。|
|**--readline**[**+**&#124;**-**]|対話モードでのタブ補完を有効または無効にします。|
|**-参照:&lt;ファイル名&gt;**<br /><br />**-r:&lt;filename&gt;**|同じ、 **fsc.exe**コンパイラ オプション。 詳細については、「[コンパイラ オプション](compiler-options.md)」を参照してください。|
|**--shadowcopyreferences**[**+**&#124;**-**]|によってロックされてからの参照を防止、F#対話型プロセス。|
|**--simpleresolution**|MSBuild の解決方法ではなくディレクトリ ベースのルールを使用して、アセンブリ参照を解決します。|
|**--tailcalls**[**+**&#124;**-**]|tail IL 命令の使用を有効または無効にします。有効にすると、スタック フレームが tail 再帰関数で再利用されます。 既定では、このオプションは有効になっています。|
|**--targetprofile:&lt;string&gt;**|このアセンブリのターゲット フレームワーク プロファイルを指定します。 有効な値は、mscorlib、netcore または netstandard は。  既定では、mscorlib です。|
|**-使用:&lt;ファイル名&gt;**|指定したファイルを起動時に最初の入力として使用するよう、インタープリターに指示します。|
|**--utf8output**|fsc.exe コンパイラ オプションと同じです。 詳細については、「[コンパイラ オプション](compiler-options.md)」を参照してください。|
|**-警告:&lt;警告レベル&gt;**|同じ、 **fsc.exe**コンパイラ オプション。 詳細については、「[コンパイラ オプション](compiler-options.md)」を参照してください。|
|**--warnaserror**[**+**&#124;**-**]|同じ、 **fsc.exe**コンパイラ オプション。 詳細については、「[コンパイラ オプション](compiler-options.md)」を参照してください。|
|**--warnaserror**[**+**&#124;**-**]:**&lt;int-list&gt;**|同じ、 **fsc.exe**コンパイラ オプション。 詳細については、「[コンパイラ オプション](compiler-options.md)」を参照してください。|

## <a name="related-topics"></a>関連トピック

|タイトル|説明|
|-----|-----------|
|[コンパイラ オプション](compiler-options.md)|使用できるコマンド ライン オプションについて説明します、F#コンパイラ、 **fsc.exe**します。|
