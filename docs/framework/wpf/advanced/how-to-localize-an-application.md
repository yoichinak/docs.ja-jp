---
title: '方法 : アプリケーションをローカライズする'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- localization [WPF], applications
- LocBaml tool [WPF]
- applications [WPF], localizing
ms.assetid: 5001227e-9326-48a4-9dcd-ba1b89ee6653
ms.openlocfilehash: f2e7e5e8879e89806cfd457a1af80f51b91871cb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174213"
---
# <a name="how-to-localize-an-application"></a>方法 : アプリケーションをローカライズする
このチュートリアルでは、LocBaml ツールを使用して、ローカライズされたアプリケーションを作成する方法について説明します。  
  
> [!NOTE]
> LocBaml ツールは、実稼働可能なアプリケーションではありません。 それはローカリゼーション API の一部を使用するサンプルとして提供されており、ローカリゼーション ツールを記述する方法を例示します。  
  
<a name="Introduction"></a>
## <a name="overview"></a>概要  
 この説明では、アプリケーションのローカリゼーションの手順を段階を追って示します。 最初に、翻訳されるテキストを抽出できるようにアプリケーションを準備します。 テキストの翻訳後、翻訳されたテキストを元のアプリケーションの新しいコピーにマージします。  
  
<a name="Requirements"></a>
## <a name="requirements"></a>必要条件  
 この説明の過程で、コマンド ラインから実行されるコンパイラである Microsoft ビルド エンジン (MSBuild) を使用します。  
  
 また、プロジェクト ファイルを使用するよう指示されます。 MSBuild ファイルとプロジェクト ファイルの使用方法については、「[ビルドと配置](../app-development/building-and-deploying-wpf-applications.md)」を参照してください。  
  
 この説明のすべての例では、カルチャとして en-US (英語-米国) を使用します。 別の言語をインストールしなくても、この例の手順全体の作業を行えます。  
  
<a name="create_sample_app"></a>
## <a name="create-a-sample-application"></a>サンプルのアプリケーションの作成  
 このステップでは、ローカリゼーション用のアプリケーションを準備します。 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] のサンプルでは、この説明のコード サンプルで使用される HelloApp のサンプルが提供されています。 このサンプルを使用する場合は[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)][、LocBaml ツールサンプル](https://github.com/microsoft/WPF-Samples/tree/master/Tools/LocBaml)からファイルをダウンロードします。  
  
1. ローカリゼーションを開始するポイントまで、アプリケーションを開発します。  
  
2. MSBuild がメイン アセンブリとサテライト アセンブリ (.resources.dll 拡張子を持つファイル) を生成してニュートラル言語リソースを含めるように、プロジェクト ファイルで開発言語を指定します。 HelloApp サンプルのプロジェクト ファイルは HelloApp.csproj です。 このファイルに、以下のように特定される開発言語があります。  
  
     `<UICulture>en-US</UICulture>`  
  
3. [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ファイルに UID を追加します。 UID は、ファイルへの変更を追跡して、翻訳する必要がある項目を識別するために使用されます。 ファイルに Uid を追加するには、プロジェクト ファイルで**updateuid**を実行します。  
  
     **msbuild -t:アップデートイドハローアプリ.csproj**  
  
     Uid が見つからないか重複していないかどうかを確認するには **、checkuid**を実行します。  
  
     **msbuild -t:チェックイド・ハローアプリ.csproj**  
  
     **updateuid**を実行した後、ファイルに Uid が含まれている必要があります。 たとえば、HelloApp の Pane1.xaml ファイルに、以下の内容があるはずです。  
  
     `<StackPanel x:Uid="StackPanel_1">`  
  
     `<TextBlock x:Uid="TextBlock_1">Hello World</TextBlock>`  
  
     `<TextBlock x:Uid="TextBlock_2">Goodbye World</TextBlock>`  
  
     `</StackPanel>`  
  
<a name="create_dll"></a>
## <a name="create-the-neutral-language-resources-satellite-assembly"></a>ニュートラル言語リソースのサテライト アセンブリを作成する  
 ニュートラル言語リソースのサテライト アセンブリを生成するようにアプリケーションを構成した後、アプリケーションをビルドします。 これにより、メイン アプリケーション アセンブリだけでなく、ローカリゼーションで LocBaml が必要とするニュートラル言語リソースのサテライト アセンブリが生成されます。 アプリケーションをビルドするには:  
  
1. HelloApp をコンパイルしてダイナミック リンク ライブラリ (DLL) を作成します。  
  
     **msbuild helloapp.csproj**  
  
2. 新規作成されたメインのアプリケーション アセンブリ HelloApp.exe は、次のフォルダーに作成されます。  
  
     `C:\HelloApp\Bin\Debug\`  
  
3. 新規作成されたニュートラル言語リソースのサテライト アセンブリ HelloApp.resources.dll は次のフォルダーに作成されます。  
  
     `C:\HelloApp\Bin\Debug\en-US\`  
  
<a name="build_locbaml"></a>
## <a name="build-the-locbaml-tool"></a>LocBaml ツールをビルドする  
  
1. LocBaml のビルドに必要なすべてのファイルは [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] サンプルに配置されています。 [LocBaml ツールサンプル](https://github.com/microsoft/WPF-Samples/tree/master/Tools/LocBaml)から C# ファイルをダウンロードします。  
  
2. ツールをビルドするには、コマンド ラインでプロジェクト ファイル (locbaml.csproj) を実行します。  
  
     **msbuild locbaml.csproj**  
  
3. 新しく作成された実行可能ファイル (locbaml.exe) を検索するには、bin \release ディレクトリに移動します。 例: C:\LocBaml\Bin\Release\locbaml.exe  
  
4. LocBaml を実行するときに指定できるオプションは、次のとおりです。  
  
    - **解析**または **-p:** Baml、リソース、または DLL ファイルを解析して.csv ファイルまたは .txt ファイルを生成します。  
  
    - **生成**または **-g:** 翻訳されたファイルを使用して、ローカライズされたバイナリ ファイルを生成します。  
  
    - **out**または **-o** {*ファイルディレクトリ*] **:** 出力ファイル名。  
  
    - **カルチャ**または **-cul** {*カルチャ*] **:** 出力アセンブリのロケール。  
  
    - **翻訳**または **-trans** {*translation.csv*] **:** 翻訳されたファイルまたはローカライズされたファイル。  
  
    - **asmpath**または **-asmpath:** {*ファイルディレクトリ*] **:** コードにカスタム コントロールが[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]含まれている場合は、カスタム コントロール アセンブリに**asmpath**を指定する必要があります。  
  
    - **nologo:** ロゴまたは著作権情報は表示されません。  
  
    - **verbose:** 詳細モードの情報が表示されます。  
  
    > [!NOTE]
    > ツールを実行するときにオプションの一覧が必要な場合は **、LocBaml.exe**と入力して Enter キーを押します。  
  
<a name="parse_dll"></a>
## <a name="use-locbaml-to-parse-a-file"></a>LocBaml を使用してファイルを解析する  
 LocBaml ツールが作成されたので、これを使用して HelloApp.resources.dll を解析し、ローカライズするテキスト コンテンツを抽出できる状態になりました。  
  
1. LocBaml.exe を、メインのアプリケーション アセンブリが作成された、アプリケーションの bin \debug フォルダーにコピーします。  
  
2. サテライト アセンブリ ファイルを解析して、.csv ファイルとして出力を格納するには、次のコマンドを使用します。  
  
     **LocBaml.exe /parse HelloApp.resources.dll /out:Hello.csv**  
  
    > [!NOTE]
    > 入力ファイル HelloApp.resources.dll が LocBaml.exe と同じディレクトリに存在しない場合は、いずれかのファイルを移動して両方のファイルが同じディレクトリにあるようにします。  
  
3. LocBaml を実行してファイルを解析する際、出力はコンマ区切り (.csv ファイル) またはタブ区切り (.txt ファイル) された 7 つのフィールドで構成されます。 HelloApp.resources.dll の解析済みの .csv ファイルを次に示します。

   | |
   |-|
   |HelloApp.g.en-US.resources:window1.baml,Stack1:System.Windows.Controls.StackPanel.$Content,Ignore,FALSE, FALSE,,#Text1;#Text2;|
   |HelloApp.g.en-US.resources:window1.baml,Text1:System.Windows.Controls.TextBlock.$Content,None,TRUE, TRUE,,Hello World|
   |HelloApp.g.en-US.resources:window1.baml,Text2:System.Windows.Controls.TextBlock.$Content,None,TRUE, TRUE,,Goodbye World|

   7 つのフィールドは、次のとおりです。  
  
   1. **BAML 名**. ソース言語のサテライト アセンブリに関する BAML リソースの名前。  
  
   2. **リソース キー**: ローカライズされたリソースの識別子。  
  
   3. **カテゴリ**。 値の型です。 [ローカリゼーション属性とコメントを](localization-attributes-and-comments.md)参照してください。  
  
   4. **読みやすさ**。 ローカライザーによって値が読み取れるかどうか。 [ローカリゼーション属性とコメントを](localization-attributes-and-comments.md)参照してください。  
  
   5. **変更可能性**。 ローカライザーによって値が変更できるかどうか。 [ローカリゼーション属性とコメントを](localization-attributes-and-comments.md)参照してください。  
  
   6. **コメント**. 値をローカライズする方法を決定するための値の追加の説明。 [ローカリゼーション属性とコメントを](localization-attributes-and-comments.md)参照してください。  
  
   7. **値**。 目的のカルチャに翻訳するテキストの値。  
  
   次の表は、.csv ファイルの区切り記号付きの値にこれらのフィールドをマップする方法を示しています。  
  
   |BAML 名|リソース キー|カテゴリ|読みやすさ|変更可能性|説明|Value|  
   |---------------|------------------|--------------|-----------------|-------------------|--------------|-----------|
   |HelloApp.g.en-US.resources:window1.baml|Stack1:System.Windows.Controls.StackPanel.$Content|Ignore|FALSE|FALSE||#Text1;#Text2|
   |HelloApp.g.en-US.resources:window1.baml|Stack1:System.Windows.Controls.StackPanel.$Content|なし|TRUE|TRUE||Hello World|
   |HelloApp.g.en-US.resources:window1.baml|Stack1:System.Windows.Controls.StackPanel.$Content|なし|TRUE|TRUE||Goodbye World|
  
   **[コメント]** フィールドのすべての値に値が含まれていないことに注意してください。フィールドに値がない場合は、空になります。 また、最初の行の項目は読み取りも変更もできませんが、**その Category**値として "Ignore" が含まれています。  
  
4. 解析されたファイル (特に大きなファイル) でローカライズ可能なアイテムを簡単に検出するには、**カテゴリ**、**読みやすさ**、および**変更可能性**を使用してアイテムを並べ替えたり、フィルタ処理したりできます。 たとえば、読み取りも変更もできない値をフィルター処理することができます。  
  
<a name="translate_loc_content"></a>
## <a name="translate-the-localizable-content"></a>ローカライズ可能なコンテンツを翻訳する  
 抽出されたコンテンツを翻訳するために使用可能な任意のツールを使用します。 これを行う良い方法は、リソースを .csv ファイルに書き込み、Microsoft Excel で表示し、最後の列 (値) に変換を変更することです。  
  
<a name="merge_translations"></a>
## <a name="use-locbaml-to-generate-a-new-resourcesdll-file"></a>LocBaml を使用して新しい .resources.dll ファイルを生成する  
 LocBaml で HelloApp.resources.dll を解析して識別されたコンテンツは翻訳済みであり、元のアプリケーションにマージする必要があります。 新しい .resources.dll ファイルを生成するには、**生成**オプションまたは **-g**オプションを使用します。  
  
1. 新しい HelloApp.resources.dll ファイルを生成するには、次の構文を使用します。 カルチャを en-US (/cul:en-US) としてマークします。  
  
     **ロックバml.exe /生成ハローアプリ.リソース.dll /トランス:こんにちは.csv /出力:c:\ /cul:en-US**  
  
    > [!NOTE]
    > 入力ファイル Hello.csv が実行可能ファイル LocBaml.exe と同じディレクトリに存在しない場合は、いずれかのファイルを移動して、両方のファイルが同じディレクトリにあるようにします。  
  
2. C:\HelloApp\Bin\Debug\en-US\HelloApp.resources.dll ディレクトリにある古い HelloApp.resources.dll ファイルを新規作成した HelloApp.resources.dll ファイルに置き換えます。  
  
3. ここで "Hello World" と "Goodbye World" をアプリケーション内で翻訳する必要があります。  
  
4. 別のカルチャに翻訳するには、翻訳先の言語のカルチャを使用します。 フランス語 (カナダ) に翻訳する方法の例を次に示します。  
  
     **LocBaml.exe /generate HelloApp.resources.dll /trans:Hellofr-CA.csv /out:c:\ /cul:fr-CA**  
  
5. メイン アプリケーション アセンブリと同じアセンブリで、新しいサテライト アセンブリを格納するために、新しいカルチャ固有のフォルダーを作成します。 フランス語 (カナダ) のフォルダーは "fr-CA" となります。  
  
6. 新しいフォルダーに生成されたサテライト アセンブリをコピーします。  
  
7. 新しいサテライト アセンブリをテストするには、アプリケーションが実行するカルチャを変更する必要があります。 これは、次の 2 つの方法のいずれかで行うことができます。  
  
    - オペレーティング システムの地域設定を変更する (**コントロール パネル**&#124; [**地域と言語のオプション**] &#124; [ コントロール パネル ] を**クリック**します)。  
  
    - アプリケーションで、次のコードを App.xaml.cs に追加します。  
  
   [!code-xaml[LocBamlChangeCultureSnippets#LocBamlChangeCultureMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/LocBamlChangeCultureSnippets/CSharp/App.xaml#locbamlchangeculturemarkup)]
   [!code-csharp[LocBamlChangeCultureSnippets#LocBamlChangeCultureCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/LocBamlChangeCultureSnippets/CSharp/App.xaml.cs#locbamlchangeculturecodebehind)]
   [!code-vb[LocBamlChangeCultureSnippets#LocBamlChangeCultureCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/LocBamlChangeCultureSnippets/VisualBasic/Application.xaml.vb#locbamlchangeculturecodebehind)]  
  
<a name="Some_Tips_for_Using_LocBaml"></a>
## <a name="some-tips-for-using-locbaml"></a>LocBaml を使用するためのヒント  
  
- カスタム コントロールを定義するすべての依存アセンブリを LocBaml のローカル ディレクトリにコピーするか、GAC にインストールする必要があります。 これは、ローカライズ API がバイナリ XAML (BAML) を読み取るときに依存アセンブリにアクセスする必要があるため、必要です。  
  
- メインのアセンブリが署名済みの場合は、生成されたリソース DLL も読み込むために署名されている必要があります。  
  
- ローカライズされたリソースの DLL は、メインのアセンブリと同期する必要があります。  
  
<a name="Whats_Next"></a>
## <a name="whats-next"></a>参照トピック  
 これで、LocBaml ツールの使用方法に関する基本的な知識が得られました。  UID を含むファイルを作成できるようになりました。 LocBaml ツールを使用することで、ローカライズ可能なコンテンツを抽出するファイルを解析できます。コンテンツを翻訳すると、翻訳済みのコンテンツをマージする .resources.dll ファイルを生成できます。 このトピックには、可能性のあるすべての詳細情報は含まれていませんが、LocBaml を使用してアプリケーションをローカライズするために必要な知識は得られました。  
  
## <a name="see-also"></a>関連項目

- [WPF のグローバリゼーション](globalization-for-wpf.md)
- [自動レイアウトの使用の概要](use-automatic-layout-overview.md)
