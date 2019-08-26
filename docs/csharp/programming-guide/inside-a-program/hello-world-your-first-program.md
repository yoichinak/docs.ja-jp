---
title: Hello World -- 最初のプログラム - C# プログラミング ガイド
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- cs.program
- vs.csharp.startpage.firstapplication
helpviewer_keywords:
- examples [C#], Hello World
- Hello World example [C#]
ms.assetid: 6493182a-b0b6-4539-a719-518a168cb730
ms.openlocfilehash: 9a50de0bb583a1dfccfa609be1cca732868505ba
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/19/2019
ms.locfileid: "69589374"
---
# <a name="hello-world----your-first-program-c-programming-guide"></a>Hello World -- 最初のプログラム (C# プログラミング ガイド)

次の手順では、従来の "Hello World!" プログラムの C# バージョンを 作成します。 このプログラムでは `Hello World!` という文字列を表示します。

基本概念の例については、「[Visual C# と Visual Basic の概要](/visualstudio/ide/getting-started-with-visual-csharp-and-visual-basic)」を参照してください。

[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]

## <a name="to-create-and-run-a-console-application"></a>コンソール アプリケーションを作成し、実行するには

1. Visual Studio を起動します。

2. メニュー バーで、 **[ファイル]** 、 **[新規作成]** 、 **[プロジェクト]** の順にクリックします。

     **[新しいプロジェクト]** ダイアログ ボックスが表示されます。

3. **[インストール済み]** 、 **[テンプレート]** 、 **[Visual C#]** の順に展開し、 **[コンソール アプリケーション]** を選択します。

4. **[名前]** ボックスにプロジェクト名を指定し、 **[OK]** をクリックします。

     **ソリューション エクスプローラー**に新しいプロジェクトが表示されます。

5. **コード エディター**で Program.cs が開いていない場合は、**ソリューション エクスプローラー**で **Program.cs** のショートカットメニューを開き、 **[コードの表示]** をクリックします。

6. Program.cs の内容を次のコードに置き換えます。

     [!code-csharp[csProgGuide#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#21)]

7. F5 キーを押してプロジェクトを実行します。 `Hello World!` という行を含むコマンド プロンプト ウィンドウが表示されます。

次に、このプログラムの重要な部分を調べます。

## <a name="comments"></a>説明

最初の行はコメントになっています。 「`//`」という文字があると、これ以降その行はコメントになります。

 [!code-csharp[csProgGuide#32](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#32)]

テキスト ブロックを `/*` 文字と `*/` 文字で囲んでコメントにすることもできます。 これを次の例に示します。

 [!code-csharp[csProgGuide#33](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#33)]

## <a name="main-method"></a>Main メソッド

C# コンソールアプリケーションには、`Main` メソッドが必要です。このメソッドの中で制御を開始して終了します。 `Main` メソッドでは、オブジェクトを作成し、ほかのメソッドを実行します。

`Main` メソッドはクラスまたは構造体の中に存在する [static](../../language-reference/keywords/static.md) メソッドです。 前の "Hello World!" の 例では、`Hello` という名前のクラスに存在していました。 次の方法のいずれかで `Main` メソッドを宣言できます。

- `void` 型を返すことができます。

     [!code-csharp[csProgGuideMain#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#12)]

- 整数を返すこともできます。

     [!code-csharp[csProgGuideMain#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#13)]

- どちらの戻り値の型でも、次のように引数を受け取ることができます。

     [!code-csharp[csProgGuideMain#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#19)]

     または

     [!code-csharp[csProgGuideMain#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#18)]

`Main` メソッドのパラメーターである `args` は、`string` の配列で、プログラムの実行時に使用したコマンドライン引数を含みます。 C++ とは異なり、この配列には実行可能 (exe) ファイルの名前は含まれていません。

コマンドライン引数の使用方法の詳細については、「[Main() とコマンドライン引数](../main-and-command-args/index.md)」および「[方法: コマンドラインを使用してアセンブリを作成および使用する](../concepts/assemblies-gac/how-to-create-and-use-assemblies-using-the-command-line.md)」に記載されている例をご覧ください。

<xref:System.Console.ReadKey%2A> メソッドの末尾で `Main` を呼び出すと、F5 キーを押してデバッグモードでプログラムを実行するときに、出力を読み取る前にコンソールウィンドウが終了することを回避できます。

## <a name="input-and-output"></a>入出力

C# プログラムは、普通、.NET Framework のランタイムライブラリが提供する入出力サービスを使用します。 `System.Console.WriteLine("Hello World!");` 命令文では、<xref:System.Console.WriteLine%2A> メソッドを使用しています。 これは、ランタイム ライブラリの <xref:System.Console> クラスの出力メソッドの 1 つです。 文字列パラメーターを標準出力ストリームに出力し、最後に改行を付け加えます。 別の入出力操作には、他の <xref:System.Console> メソッドを使用できます。 `using System;` ディレクティブをプログラムの開始時にインクルードした場合は、完全に修飾せずに <xref:System> クラスおよびメソッドを直接使用できます。 たとえば、`Console.WriteLine` の代わりに `System.Console.WriteLine` を呼び出すことができます。

 [!code-csharp[csProgGuide#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/using.cs#1)]

 [!code-csharp[csProgGuide#23](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#23)]

入出力メソッドの詳細については、「<xref:System.IO>」を参照してください。

## <a name="command-line-compilation-and-execution"></a>コマンドラインコンパイルと実行

"Hello World!" プログラムは、 Visual Studio 統合開発環境 (IDE) の代わりに、コマンドラインを使用してコンパイルできます。

### <a name="to-compile-and-run-from-a-command-prompt"></a>コマンドプロンプトからコンパイルおよび実行するには

1. 前の手順のコードをテキスト エディターに貼り付け、テキスト ファイルとして保存します。 そのファイルに `Hello.cs` という名前を付けます。 C# のソース コード ファイルでは、`.cs` という拡張子を使います。

2. 次のいずれかの手順を実行してコマンド プロンプト ウィンドウを開きます。

    - Windows 10 の場合、 **[スタート]** メニューで `Developer Command Prompt` を検索し、 **[開発者コマンド プロンプト for VS 2017]** をタップまたは選択します。

         [開発者コマンド プロンプト] ウィンドウが表示されます。

    - Windows 7 の場合、 **[スタート]** メニューを開き、Visual Studio の現在のバージョンのフォルダーを展開し、 **[Visual Studio Tools]** のショートカット メニューを開いて、 **[開発者コマンド プロンプト for VS 2017]** をクリックします。

         [開発者コマンド プロンプト] ウィンドウが表示されます。

    - 標準のコマンドプロンプトウィンドウからコマンド ライン ビルドを有効にします。

         「[方法 : Visual Studio のコマンドラインのための環境変数を設定する](../../language-reference/compiler-options/how-to-set-environment-variables-for-the-visual-studio-command-line.md)」をご覧ください。

3. コマンドプロンプトウィンドウで、`Hello.cs` ファイルが格納されているフォルダーに移動します。

4. `Hello.cs` をコンパイルするには、次のコマンドを入力します。

     `csc Hello.cs`

     プログラムにコンパイル エラーがない場合、`Hello.exe` という名前の実行可能ファイルが作成されます。

5. コマンド プロンプトで、次のコマンドを入力してプログラムを実行します。

     `Hello`

 C# コンパイラとそのオプションの詳細については、「[C# コンパイラ オプション](../../language-reference/compiler-options/index.md)」を参照してください。

## <a name="see-also"></a>関連項目

- [C# プログラミング ガイド](../index.md)
- [インサイド C# プログラム](./index.md)
- [文字列](../strings/index.md)
- [サンプルおよびチュートリアル](../../../samples-and-tutorials/index.md)
- [C# リファレンス](../../language-reference/index.md)
- [Main() とコマンドライン引数](../main-and-command-args/index.md)
- [Visual C# と Visual Basic の概要](/visualstudio/ide/getting-started-with-visual-csharp-and-visual-basic)
