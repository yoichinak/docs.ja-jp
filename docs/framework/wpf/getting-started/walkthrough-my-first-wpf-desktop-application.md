---
title: Visual Studio での WPF アプリケーションを作成します。
ms.date: 10/26/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- getting started [WPF], WPF
- WPF [WPF], getting started
ms.assetid: b96bed40-8946-4285-8fe4-88045ab854ed
author: mairaw
ms.author: mairaw
ms.custom: vs-dotnet
ms.openlocfilehash: dbfc40bd1fcc97810ea1397731bd8c232297cbd1
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59055249"
---
# <a name="walkthrough-my-first-wpf-desktop-application"></a>チュートリアル: 初めての WPF デスクトップ アプリケーション

この記事では、ほとんどの WPF アプリケーションに共通する要素を含む単純な Windows Presentation Foundation (WPF) アプリケーションを開発する方法を示します。Extensible Application Markup Language (XAML) マークアップ、分離コード、アプリケーション定義、コントロール、レイアウト、データ バインド、およびスタイル。

このチュートリアルには、次の手順が含まれています。

- XAML を使用して、アプリケーションのユーザー インターフェイス (UI) の外観をデザインします。

- アプリケーションの動作を構築するコードを記述します。

- アプリケーションを管理するアプリケーション定義を作成します。

- コントロールを追加し、アプリケーションの UI を作成するレイアウトを作成します。

- アプリケーションの UI 全体で一貫した外観のスタイルを作成します。

- UI をデータから UI を設定して、データと UI の同期を維持するデータにバインドします。

チュートリアルの目的は、スタンドアロンのユーザーを選択したユーザーの経費報告書を表示できる Windows アプリケーションを構築したします。 アプリケーションは、ブラウザー スタイルのウィンドウでホストされているいくつかの WPF ページで構成されます。

> [!TIP]
> このチュートリアルの構築に使用するサンプル コードでは、Visual Basic と C# で使用可能な[Introduction to Building WPF Applications](https://go.microsoft.com/fwlink/?LinkID=160008)します。

## <a name="prerequisites"></a>必須コンポーネント

- Visual Studio 2017 またはそれ以降

   最新バージョンの Visual Studio のインストールの詳細については、次を参照してください。 [Visual Studio のインストール](/visualstudio/install/install-visual-studio)します。

## <a name="create-the-application-project"></a>アプリケーション プロジェクトを作成します。

最初の手順では、アプリケーションの定義を 2 つのページとイメージを含むアプリケーション インフラストラクチャを作成します。

1. Visual Basic または Visual C# のという名前で新しい WPF アプリケーション プロジェクトを作成する **`ExpenseIt`** :

   1. Visual Studio を開き、選択**ファイル** > **新規** > **プロジェクト**します。

      **新しいプロジェクト**ダイアログ ボックスが開きます。

   2. 下、**インストール済み**カテゴリで、いずれかを展開、 **Visual C#** または**Visual Basic**ノードをクリックして**Windows デスクトップ**します。

   3. 選択、 **WPF アプリ (.NET Framework)** テンプレート。 名前を入力します **`ExpenseIt`** 選び**OK**します。

      ![選択した WPF アプリで新しいプロジェクト ダイアログ ボックス](./media/new-project-dialog.png)

      Visual Studio は、プロジェクトを作成し、という名前の既定アプリケーション ウィンドウのデザイナーが開きます**MainWindow.xaml**します。

   > [!NOTE]
   > このチュートリアルでは、<xref:System.Windows.Controls.DataGrid>以降、.NET Framework 4 で利用可能であるコントロール。 プロジェクトが、.NET Framework 4 を対象とすることを確認以降に。 詳細については、「[方法 :.NET Framework のターゲット バージョンを指定する](/visualstudio/ide/how-to-target-a-version-of-the-dotnet-framework)」を参照してください。

2. 開いている*Application.xaml* (Visual Basic) または*App.xaml* (c#)。

    この XAML ファイルでは、WPF アプリケーションとすべてのアプリケーション リソースを定義します。 ときに自動的に表示する UI を指定することもこのファイルを使用するアプリケーションを起動します。この場合、 *MainWindow.xaml*します。

    このよう Visual Basic では、XAML になります。

    [!code-xaml[ExpenseIt#1_A](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/Application.xaml#1_a)]

    C# では、次のようになります。

    [!code-xaml[ExpenseIt#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/App.xaml#1)]

3. *MainWindow.xaml*を開きます。

    この XAML ファイルは、アプリケーションのメイン ウィンドウであるため、ページで作成されたコンテンツを表示します。 <xref:System.Windows.Window>クラスは、タイトル、サイズ、アイコンなど、ウィンドウのプロパティを定義し、閉じるか、非表示などのイベントを処理します。

4. <xref:System.Windows.Navigation.NavigationWindow>.xaml の<xref:System.Windows.Window>要素を、次に示すように変更します。

   ```xaml
   <NavigationWindow x:Class="ExpenseIt.MainWindow"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        ...
   </NavigationWindow>
   ```

   このアプリは、ユーザーの入力に応じてさまざまなコンテンツに移動します。 そのため、メイン ウィンドウを<xref:System.Windows.Window>から<xref:System.Windows.Navigation.NavigationWindow>に変更する必要があります。 <xref:System.Windows.Navigation.NavigationWindow>  は、<xref:System.Windows.Window>のすべてのプロパティを継承しています。 <xref:System.Windows.Navigation.NavigationWindow> XAML ファイル内の要素のインスタンスを作成する、<xref:System.Windows.Navigation.NavigationWindow>クラス。 詳細については、次を参照してください。[ナビゲーションの概要](../app-development/navigation-overview.md)します。

5. 次のプロパティを変更、<xref:System.Windows.Navigation.NavigationWindow>要素。

    - 設定、<xref:System.Windows.Window.Title%2A>プロパティを"`ExpenseIt`"。

    - 設定、<xref:System.Windows.FrameworkElement.Width%2A>プロパティを 500 ピクセルにします。

    - 設定、<xref:System.Windows.FrameworkElement.Height%2A>プロパティを 350 ピクセル、高さ。

    - 削除、<xref:System.Windows.Controls.Grid>間の要素、<xref:System.Windows.Navigation.NavigationWindow>タグ。

    このよう Visual Basic では、XAML になります。

    [!code-xaml[ExpenseIt#2_A](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt/MainWindow.xaml#2_a)]

    C# では、次のようになります。

    [!code-xaml[ExpenseIt#2](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/MainWindow.xaml#2)]

6. 開いている*MainWindow.xaml.vb*または*MainWindow.xaml.cs*します。

    このファイルは、分離コード ファイルで宣言されたイベントを処理するコードを含む*MainWindow.xaml*します。 このファイルには、XAML で定義されたウィンドウの部分クラスが含まれています。

7. C# を使用している場合は、変更、`MainWindow`クラスから派生する<xref:System.Windows.Navigation.NavigationWindow>します。 (Visual basic の場合は、これは XAML でウィンドウを変更するときにします。)

   コードについては、次のようになります。

   [!code-csharp[ExpenseIt#3](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/MainWindow.xaml.cs#3)]
   [!code-vb[ExpenseIt#3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/MainWindow.xaml.vb#3)]

   > [!TIP]
   > C# と Visual Basic でのサンプル コードのコード言語を切り替えることができます、**言語**この記事の右上隅のドロップダウン リスト。

## <a name="add-files-to-the-application"></a>ファイルをアプリケーションに追加します。

このセクションでは、アプリケーションに 2 つのページと 1 つのイメージを追加します。

1. 新しい WPF ページをプロジェクトに追加し、名前 *`ExpenseItHome.xaml`* :

   1. **ソリューション エクスプ ローラー**を右クリックし、 **`ExpenseIt`** プロジェクト ノード**追加** > **ページ**します。

   1. **新しい項目の追加**ダイアログ ボックスで、**ページ (WPF)** テンプレートは既に選択されています。 名前を入力します **`ExpenseItHome`** 、し、**追加**します。

    このページは、アプリケーションの起動時に表示される最初のページです。 経費報告書を表示するからを選択するユーザーの一覧表示されます。

2. 開いている *`ExpenseItHome.xaml`* します。

3. 設定、<xref:System.Windows.Controls.Page.Title%2A>に"`ExpenseIt - Home`"。

    このよう Visual Basic では、XAML になります。

    [!code-xaml[ExpenseIt#6_A](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseItHome.xaml#6_a)]

    C# では、次のようになります。

    [!code-xaml[ExpenseIt#6](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt2/ExpenseItHome.xaml#6)]

4. *MainWindow.xaml*を開きます。

5. 設定、<xref:System.Windows.Navigation.NavigationWindow.Source%2A>プロパティを<xref:System.Windows.Navigation.NavigationWindow>に"`ExpenseItHome.xaml`"。

    これにより設定 *`ExpenseItHome.xaml`* アプリケーションの起動時を開く最初のページになります。 このよう Visual Basic では、XAML になります。

    [!code-xaml[ExpenseIt#7_A](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/MainWindow.xaml#7_a)]

    C# では、次のようになります。

    [!code-xaml[ExpenseIt#7](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt2/MainWindow.xaml#7)]

   > [!TIP]
   > 設定することも、**ソース**プロパティ、 **[その他]** のカテゴリ、**プロパティ**ウィンドウ。
   >
   > ![プロパティ ウィンドウで、ソース プロパティ](./media/properties-source.png)

6. もう 1 つの新しい WPF ページをプロジェクトに追加し、名前*ExpenseReportPage.xaml*:。

   1. **ソリューション エクスプ ローラー**を右クリックし、 **`ExpenseIt`** プロジェクト ノード**追加** > **ページ**します。

   1. **新しい項目の追加**ダイアログ ボックスで、**ページ (WPF)** テンプレートは既に選択されています。 名前を入力します**ExpenseReportPage**、し、**追加**します。

    このページで選択されているユーザーの経費報告書が表示されます、 **`ExpenseItHome`** ページ。

7. *ExpenseReportPage.xaml*を開きます。

8. 設定、<xref:System.Windows.Controls.Page.Title%2A>に"`ExpenseIt - View Expense`"。

    このよう Visual Basic では、XAML になります。

    [!code-xaml[ExpenseIt#4_A](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseReportPage.xaml#4_a)]

    C# では、次のようになります。

    [!code-xaml[ExpenseIt#4](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/ExpenseReportPage.xaml#4)]

9. 開いている*ExpenseItHome.xaml.vb*と*ExpenseReportPage.xaml.vb*、または*ExpenseItHome.xaml.cs*と*ExpenseReportPage.xaml.cs*.

    Visual Studio が自動的に作成、新しいファイルを作成するときに、*コード ビハインド*ファイル。 これらの分離コード ファイルでは、ユーザー入力に対応するためのロジックを処理します。

    コードのようになります **`ExpenseItHome`** :

    [!code-csharp[ExpenseIt#2_5](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt2/ExpenseItHome.xaml.cs#2_5)]
    [!code-vb[ExpenseIt#2_5](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseItHome.xaml.vb#2_5)]

    このような**ExpenseReportPage**:

    [!code-csharp[ExpenseIt#5](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/ExpenseReportPage.xaml.cs#5)]
    [!code-vb[ExpenseIt#5](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseReportPage.xaml.vb#5)]

10. という名前のイメージを追加*watermark.png*をプロジェクトにします。 独自のイメージを作成、サンプル コードからファイルをコピーまたは入手[ここ](https://github.com/dotnet/docs/blob/master/docs/framework/wpf/getting-started/./media/watermark.png)します。

    1. プロジェクト ノードを右クリックして**追加** > **既存項目の**、またはキーを押します**Shift**+**Alt**+ **A**します。

    2. **既存項目の追加**ダイアログを使用して、選択するイメージ ファイルを見つけます**追加**します。

## <a name="build-and-run-the-application"></a>アプリケーションのビルドと実行

1. ビルド、アプリケーションを実行し、キーを押します**F5**選択または**デバッグの開始**から、**デバッグ**メニュー。

    次の図は、使用してアプリケーションを<xref:System.Windows.Navigation.NavigationWindow>ボタン。

    ![ExpenseIt のサンプルのスクリーン ショット](./media/gettingstartedfigure1.png)

2. Visual Studio に戻るにアプリケーションを閉じます。

## <a name="create-the-layout"></a>レイアウトを作成します。

レイアウトは、順序付けられた UI 要素を配置する方法を提供し、UI のサイズを変更したときに、それらの要素の位置とサイズも管理します。 通常、レイアウトを作成するには、次のいずれかのレイアウト コントロールを使用します。

- <xref:System.Windows.Controls.Canvas>
- <xref:System.Windows.Controls.DockPanel>
- <xref:System.Windows.Controls.Grid>
- <xref:System.Windows.Controls.StackPanel>
- <xref:System.Windows.Controls.VirtualizingStackPanel>
- <xref:System.Windows.Controls.WrapPanel>

これらの各レイアウト コントロールは、その子要素に対する特別な種類のレイアウトをサポートしています。 `ExpenseIt` ページのサイズを変更できる、および各ページが他の要素の横の水平および垂直に配置された要素があります。 その結果、<xref:System.Windows.Controls.Grid>は、アプリケーションの最適なレイアウト要素です。

> [!TIP]
> 詳細については<xref:System.Windows.Controls.Panel>、要素を参照してください[パネルの概要](../controls/panels-overview.md)します。 レイアウトの詳細については、次を参照してください。[レイアウト](../advanced/layout.md)します。

セクションで、単一列テーブル 3 つの行と 10 ピクセルの余白を追加して作成する列と行の定義を<xref:System.Windows.Controls.Grid>で *`ExpenseItHome.xaml`* します。

1. 開いている *`ExpenseItHome.xaml`* します。

2. 設定、<xref:System.Windows.FrameworkElement.Margin%2A>プロパティを<xref:System.Windows.Controls.Grid>「10,0,10,10」は、左、上、右、下の余白に対応する要素。

   ```xaml
   <Grid Margin="10,0,10,10">
   ```

   > [!TIP]
   > 設定することも、**余白**値、**プロパティ**ウィンドウで、**レイアウト**カテゴリ。
   >
   > ![[プロパティ] ウィンドウの余白の値](./media/properties-margin.png)

3. 間で次の XAML を追加、<xref:System.Windows.Controls.Grid>行と列の定義を作成するタグ。

    [!code-xaml[ExpenseIt#8](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt3/ExpenseItHome.xaml#8)]

    <xref:System.Windows.Controls.RowDefinition.Height%2A> 2 つの行に設定されて<xref:System.Windows.GridLength.Auto%2A>行の内容に基づいて、行のサイズを調整することを意味します。 既定の<xref:System.Windows.Controls.RowDefinition.Height%2A>は<xref:System.Windows.GridUnitType.Star>サイズ変更は、行の高さが使用可能な領域の加重比率であることを意味します。 たとえば 2 つの行がある場合、<xref:System.Windows.Controls.RowDefinition.Height%2A>の"*"、それぞれがある使用可能な領域の半分の高さ。

    <xref:System.Windows.Controls.Grid> XAML を次のようになります。

    [!code-xaml[ExpenseIt#9](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt3/ExpenseItHome.xaml#9)]

## <a name="add-controls"></a>コントロールを追加します。

このセクションでは、ホーム ページの経費レポートを表示するユーザーが選択できるユーザーの一覧を表示する UI を更新します。 コントロールとは、ユーザーがアプリケーションと対話できるようにする UI オブジェクトのことです。 詳しくは、「 [コントロール](../controls/index.md)」をご覧ください。

この UI を作成するには、次の要素を追加します *`ExpenseItHome.xaml`* :

- <xref:System.Windows.Controls.ListBox> (用のユーザーの一覧)。
- <xref:System.Windows.Controls.Label> (一覧のヘッダーとして)。
- <xref:System.Windows.Controls.Button> (クリックする一覧で選択されているユーザーの経費報告書を表示する)。

行の各コントロールを配置、<xref:System.Windows.Controls.Grid>を設定して、<xref:System.Windows.Controls.Grid.Row%2A?displayProperty=nameWithType>添付プロパティ。 添付プロパティの詳細については、次を参照してください。[添付プロパティの概要](../advanced/attached-properties-overview.md)します。

1. 開いている *`ExpenseItHome.xaml`* します。

2. 追加する、次 XAML どこかの間、<xref:System.Windows.Controls.Grid>タグ。

   [!code-xaml[ExpenseIt#10](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt4/ExpenseItHome.xaml#10)]

   > [!TIP]
   > ドラッグしてから、コントロールを作成することも、**ツールボックス**デザイン ウィンドウとでプロパティを設定し、ウィンドウ、**プロパティ**ウィンドウ。

3. アプリケーションをビルドして実行します。

次の図は、作成したコントロールを示しています。

![ExpenseIt のサンプルのスクリーン ショット](./media/gettingstartedfigure2.png)

## <a name="add-an-image-and-a-title"></a>イメージとタイトルを追加します。

このセクションでは、イメージとページ タイトル、ホーム ページの UI を更新します。

1. 開いている *`ExpenseItHome.xaml`* します。

2. もう 1 つの列を追加、<xref:System.Windows.Controls.Grid.ColumnDefinitions%2A>固定<xref:System.Windows.Controls.ColumnDefinition.Width%2A>230 ピクセルの。

    [!code-xaml[ExpenseIt#11](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#11)]

3. 別の行を追加、 <xref:System.Windows.Controls.Grid.RowDefinitions%2A>、4 つの行の合計。

    [!code-xaml[ExpenseIt#11b](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#11b)]

4. 2 番目の列に設定して、コントロールを移動、<xref:System.Windows.Controls.Grid.Column%2A?displayProperty=nameWithType>を 1 に 3 つのコントロール (枠線、ListBox、およびボタン) の各プロパティ。

5. 下の行をインクリメントして各コントロールを移動、<xref:System.Windows.Controls.Grid.Row%2A?displayProperty=nameWithType>を 1 つの値。

   3 つのコントロールの XAML は、次のようになります。

    [!code-xaml[ExpenseIt#12](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#12)]

6. 設定、<xref:System.Windows.Controls.Panel.Background%2A>の<xref:System.Windows.Controls.Grid>する、 *watermark.png* 、次 XAML どこかの間に追加することで、イメージ ファイル、`<Grid>`と`</Grid>`タグ。

    [!code-xaml[ExpenseIt#14](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#14)]

7. 前に、<xref:System.Windows.Controls.Border>要素を追加、 <xref:System.Windows.Controls.Label> "View Expense Report"の内容。 これは、ページのタイトルです。

    [!code-xaml[ExpenseIt#13](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#13)]

8. アプリケーションをビルドして実行します。

次の図は、追加したものの結果を示しています。

![ExpenseIt のサンプルのスクリーン ショット](./media/gettingstartedfigure3.png)

## <a name="add-code-to-handle-events"></a>イベントを処理するコードを追加します。

1. 開いている *`ExpenseItHome.xaml`* します。

2. 追加、<xref:System.Windows.Controls.Primitives.ButtonBase.Click>イベント ハンドラーを<xref:System.Windows.Controls.Button>要素。 詳細については、「[方法 :単純なイベント ハンドラーを作成](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/bb675300(v=vs.100))です。

    [!code-xaml[ExpenseIt#15](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt6/ExpenseItHome.xaml#15)]

3. 開いている *`ExpenseItHome.xaml.vb`* または *`ExpenseItHome.xaml.cs`* します。

4. 次のコードを追加、`ExpenseItHome`ボタンを追加するクラス イベント ハンドラーをクリックします。 イベント ハンドラーが表示されます、 **ExpenseReportPage**ページ。

    [!code-csharp[ExpenseIt#16](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt6/ExpenseItHome.xaml.cs#16)]
    [!code-vb[ExpenseIt#16](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt6/ExpenseItHome.xaml.vb#16)]

## <a name="create-the-ui-for-expensereportpage"></a>ExpenseReportPage の UI を作成します。

*ExpenseReportPage.xaml*で選択されている個人の経費報告書が表示されます、 **`ExpenseItHome`** ページ。 このセクションでは、UI を作成します**ExpenseReportPage**します。 バック グラウンドを追加し、さまざまな UI 要素の色の塗りつぶしもします。

1. *ExpenseReportPage.xaml*を開きます。

2. 間で次の XAML を追加、<xref:System.Windows.Controls.Grid>タグ。

    [!code-xaml[ExpenseIt#17](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt6/ExpenseReportPage.xaml#17)]

    この UI はのような *`ExpenseItHome.xaml`* でレポート データが表示される点を除いて、<xref:System.Windows.Controls.DataGrid>します。

3. アプリケーションをビルドして実行します。

    > [!NOTE]
    > エラーが発生する場合、<xref:System.Windows.Controls.DataGrid>が見つかりませんでしたかが存在しない、プロジェクトが .NET Framework 4 以降を対象とするかどうかを確認します。 詳細については、「[方法 :.NET Framework のターゲット バージョンを指定する](/visualstudio/ide/how-to-target-a-version-of-the-dotnet-framework)」を参照してください。

4. 選択、**ビュー**ボタンをクリックします。

    経費明細書ページが表示されます。 ナビゲーション ボタンが有効になっていることにも注目してください。

次の図は、UI 要素に追加*ExpenseReportPage.xaml*します。

![ExpenseIt のサンプルのスクリーン ショット](./media/gettingstartedfigure4.png)

## <a name="style-controls"></a>スタイルのコントロール

さまざまな要素の外観は、多くの場合、UI で同じ種類のすべての要素に対して同じです。 UI を使用して[スタイル](../controls/styling-and-templating.md)複数要素の間で外観を再利用可能なことにします。 スタイルの再利用性は、XAML の作成と管理を簡略化するのに役立ちます。 このセクションでは、これまでの手順で定義した要素ごとの属性を、スタイルに置き換えます。

1. 開いている*Application.xaml*または*App.xaml*します。

2. 間で次の XAML を追加、<xref:System.Windows.Application.Resources%2A?displayProperty=nameWithType>タグ。

    [!code-xaml[ExpenseIt#18](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt7/App.xaml#18)]

    この XAML は、次のスタイルを追加します。

    - `headerTextStyle`:ページ タイトルの書式設定<xref:System.Windows.Controls.Label>します。

    - `labelStyle`:書式設定、<xref:System.Windows.Controls.Label>コントロール。

    - `columnHeaderStyle`:書式設定、<xref:System.Windows.Controls.Primitives.DataGridColumnHeader>します。

    - `listHeaderStyle`:一覧のヘッダーを書式設定する<xref:System.Windows.Controls.Border>コントロール。

    - `listHeaderTextStyle`:一覧のヘッダーを書式設定する<xref:System.Windows.Controls.Label>します。

    - `buttonStyle`:書式設定、<xref:System.Windows.Controls.Button>で`ExpenseItHome.xaml`します。

    スタイルは、リソースとの子に注目してください、<xref:System.Windows.Application.Resources%2A?displayProperty=nameWithType>プロパティ要素。 ここでは、スタイルはアプリケーション内のすべての要素に適用されます。 .NET Framework アプリケーションでリソースの使用の例は、次を参照してください。[アプリケーション リソースを使用](../advanced/how-to-use-application-resources.md)します。

3. 開いている *`ExpenseItHome.xaml`* します。

4. 間にあるすべての置換、<xref:System.Windows.Controls.Grid>で次の XAML 要素。

    [!code-xaml[ExpenseIt#19](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt7/ExpenseItHome.xaml#19)]

    各コントロールの外観を定義する <xref:System.Windows.VerticalAlignment> や <xref:System.Windows.Media.FontFamily> などのプロパティは、これらのスタイルを適用することで、削除されて置き換えられます。 たとえば、 `headerTextStyle` "View Expense Report"に適用される<xref:System.Windows.Controls.Label>します。

5. *ExpenseReportPage.xaml*を開きます。

6. 間にあるすべての置換、<xref:System.Windows.Controls.Grid>で次の XAML 要素。

    [!code-xaml[ExpenseIt#20](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt7/ExpenseReportPage.xaml#20)]

    これにより、スタイルが <xref:System.Windows.Controls.Label> と <xref:System.Windows.Controls.Border> の要素に追加されます。

## <a name="bind-data-to-a-control"></a>データをコントロールにバインドします。

このセクションでは、さまざまなコントロールにバインドされている XML データを作成します。

1. 開いている *`ExpenseItHome.xaml`* します。

2. 開始後に<xref:System.Windows.Controls.Grid>要素を作成する次の XAML を追加、<xref:System.Windows.Data.XmlDataProvider>各人のデータを格納しています。

    [!code-xaml[ExpenseIt#21](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#21)]
    [!code-xaml[ExpenseIt#23](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#23)]
    [!code-xaml[ExpenseIt#22](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#22)]

    データとして作成、<xref:System.Windows.Controls.Grid>リソース。 通常、これはファイルとして読み込まれますが、説明を簡単にするため、データをインラインで追加します。

3. 内で、`<Grid.Resources>`要素では、次の追加<xref:System.Windows.DataTemplate>、データを表示する方法を定義する、 <xref:System.Windows.Controls.ListBox>:

    [!code-xaml[ExpenseIt#21](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#21)]
    [!code-xaml[ExpenseIt#24](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#24)]
    [!code-xaml[ExpenseIt#22](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#22)]

    データ テンプレートの詳細については、次を参照してください。[データ テンプレートの概要](../data/data-templating-overview.md)します。

4. 既存<xref:System.Windows.Controls.ListBox>次の XAML で。

    [!code-xaml[ExpenseIt#25](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#25)]

    この XAML のバインド、<xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>のプロパティ、<xref:System.Windows.Controls.ListBox>をデータ ソースとしてデータ テンプレートを適用し、 <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A>。

## <a name="connect-data-to-controls"></a>コントロールにデータを接続します。

次で選択されている名前を取得するコードを追加します、 **`ExpenseItHome`** ページし、のコンス トラクターに渡す**ExpenseReportPage**します。 **ExpenseReportPage**コントロールで定義されているは、渡された項目を使用してデータ コンテキストの設定で*ExpenseReportPage.xaml*にバインドします。

1. *ExpenseReportPage.xaml.vb* または *ExpenseReportPage.xaml.cs*を開きます。

2. オブジェクトを取得するコンストラクターを追加して、選択した個人の経費報告書データを渡せるようにします。

    [!code-csharp[ExpenseIt#26](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseReportPage.xaml.cs#26)]
    [!code-vb[ExpenseIt#26](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt8/ExpenseReportPage.xaml.vb#26)]

3. 開いている *`ExpenseItHome.xaml.vb`* または *`ExpenseItHome.xaml.cs`* します。

4. 変更、<xref:System.Windows.Controls.Primitives.ButtonBase.Click>選択した個人の経費報告書データを渡す新しいコンス トラクターを呼び出すイベント ハンドラー。

    [!code-csharp[ExpenseIt#27](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml.cs#27)]
    [!code-vb[ExpenseIt#27](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt8/ExpenseItHome.xaml.vb#27)]

## <a name="style-data-with-data-templates"></a>データ テンプレートの形式のデータ

このセクションでは、データ テンプレートを使用してデータ バインド リスト内の各項目の UI を更新します。

1. *ExpenseReportPage.xaml*を開きます。

2. "Name"および"Department"の内容をバインド<xref:System.Windows.Controls.Label>要素を適切なデータ ソースのプロパティ。 データ バインディングの詳細については、次を参照してください。[データ バインディングの概要](../data/data-binding-overview.md)します。

    [!code-xaml[ExpenseIt#31](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseReportPage.xaml#31)]

3. 開始後に<xref:System.Windows.Controls.Grid>要素、経費報告書データを表示する方法を定義する次のデータ テンプレートを追加します。

    [!code-xaml[ExpenseIt#30](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseReportPage.xaml#30)]

4. 置換、<xref:System.Windows.Controls.DataGridTextColumn>を持つ要素<xref:System.Windows.Controls.DataGridTemplateColumn>、<xref:System.Windows.Controls.DataGrid>要素とそれらにテンプレートを適用します。

    [!code-xaml[ExpenseIt#32](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseReportPage.xaml#32)]

5. アプリケーションをビルドして実行します。

6. ユーザーを選択し、選択、**ビュー**ボタンをクリックします。

次の図の両方のページ、`ExpenseIt`アプリケーションをコントロール、レイアウト、スタイル、データ バインディング、およびデータ テンプレートを適用します。

![ExpenseIt のサンプルのスクリーン ショット](./media/gettingstartedfigure5.png)

> [!NOTE]
> このサンプルでは、WPF の特定の機能について説明し、セキュリティ、ローカリゼーション、およびアクセシビリティなどのすべてのベスト プラクティスに従っていません。 WPF と .NET Framework アプリケーション開発のベスト プラクティスの包括的な対応は、次のトピックを参照してください。
>
> - [ユーザー補助](../../ui-automation/accessibility-best-practices.md)
>
> - [セキュリティ](../security-wpf.md)
>
> - [WPF のグローバリゼーションとローカライズ](../advanced/wpf-globalization-and-localization-overview.md)
>
> - [WPF のパフォーマンス](../advanced/optimizing-wpf-application-performance.md)

## <a name="next-steps"></a>次の手順

このチュートリアルでは、さまざまな Windows Presentation Foundation (WPF) を使用して UI を作成するための手法について説明しました。 これで、データ バインド、.NET Framework アプリケーションのビルド ブロックの基本的な理解が必要です。 WPF のアーキテクチャおよびプログラミング モデルの詳細については、次のトピックを参照してください。

- [WPF アーキテクチャ](../advanced/wpf-architecture.md)
- [XAML の概要 (WPF)](../advanced/xaml-overview-wpf.md)
- [依存関係プロパティの概要](../advanced/dependency-properties-overview.md)
- [レイアウト](../advanced/layout.md)

アプリケーションの作成の詳細については、次のトピックを参照してください。

- [アプリケーションの開発](../app-development/index.md)
- [コントロール](../controls/index.md)
- [データバインディングの概要](../data/data-binding-overview.md)
- [グラフィックスとマルチ メディア](../graphics-multimedia/index.md)
- [WPF のドキュメント](../advanced/documents-in-wpf.md)

## <a name="see-also"></a>関連項目

- [パネルの概要](../controls/panels-overview.md)
- [データ テンプレートの概要](../data/data-templating-overview.md)
- [WPF アプリケーションのビルド](../app-development/building-a-wpf-application-wpf.md)
- [スタイルとテンプレート](../controls/styles-and-templates.md)
