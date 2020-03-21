---
title: Visual Studio 2019 で初めての WPF アプリを作成する - .NET フレームワーク
titleSuffix: ''
ms.date: 09/06/2019
dev_langs:
- csharp
- vb
helpviewer_keywords:
- getting started [WPF], WPF
- WPF [WPF], getting started
ms.assetid: b96bed40-8946-4285-8fe4-88045ab854ed
ms.topic: tutorial
ms.custom: mvc,vs-dotnet
ms.openlocfilehash: 65b6fe31e86380162e90820c2cf118a9d1b96b4a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186582"
---
# <a name="tutorial-create-your-first-wpf-application-in-visual-studio-2019"></a>チュートリアル: Visual Studio 2019 で最初の WPF アプリケーションを作成する

この記事では、WPF アプリケーションの大部分に共通する要素を含む Windows プレゼンテーション ファンデーション (WPF) デスクトップ アプリケーションを開発する方法を示します。コントロール、レイアウト、データ バインディング、およびスタイル。 アプリケーションを開発するには、Visual Studio を使用します。

このチュートリアルでは、以下の内容を学習します。
> [!div class="checklist"]
>
> - WPF プロジェクトを作成します。
> - XAML を使用して、アプリケーションのユーザー インターフェイス (UI) の外観をデザインします。
> - アプリケーションの動作をビルドするコードを記述します。
> - アプリケーションを管理するアプリケーション定義を作成します。
> - コントロールを追加し、レイアウトを作成してアプリケーション UI を構成します。
> - アプリケーションの UI 全体で一貫した外観を実現するためのスタイルを作成します。
> - データから UI を設定し、データと UI の同期を維持するために、UI をデータにバインドします。

このチュートリアルの最後に、ユーザーが選択したユーザーの経費報告書を表示できるスタンドアロンの Windows アプリケーションを構築します。 アプリケーションは、ブラウザー スタイルのウィンドウでホストされている複数の WPF ページで構成されます。

> [!TIP]
> このチュートリアルで使用するサンプル コードは、[チュートリアル WPF アプリケーションサンプル コード](https://github.com/Microsoft/WPF-Samples/tree/master/Getting%20Started/WalkthroughFirstWPFApp)で Visual Basic と C# の両方で使用できます。
>
> このページの上部にある言語セレクタを使用して、サンプル コードのコード言語を C# と Visual Basic の間で切り替えることができます。

## <a name="prerequisites"></a>必須コンポーネント

- **NET デスクトップ開発**ワークロードがインストールされた[Visual Studio 2019。](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019)

   最新バージョンの Visual Studio のインストールの詳細については、「 [Visual Studio](/visualstudio/install/install-visual-studio)のインストール 」を参照してください。

## <a name="create-the-application-project"></a>アプリケーション プロジェクトを作成する

最初の手順では、アプリケーション定義、2 ページ、およびイメージを含むアプリケーション インフラストラクチャを作成します。

1. という名前の Visual Basic または Visual C#**`ExpenseIt`** で新しい WPF アプリケーション プロジェクトを作成します。

   1. Visual Studio を開き、[**はじめに**] メニューの [**新しいプロジェクトの作成**] を選択します。

      [**新しいプロジェクトの作成**] ダイアログが開きます。

   2. [**言語**] ドロップダウンで **、[C#]** または **[Visual Basic]** を選択します。

   3. WPF**アプリケーション (.NET Framework)** テンプレートを選択し、[**次へ**] を選択します。

      ![[新しいプロジェクトの作成] ダイアログ](./media/walkthrough-my-first-wpf-desktop-application/create-new-project-dialog.png)

      [**新しいプロジェクトの構成]** ダイアログが開きます。

   4. プロジェクト名**`ExpenseIt`** を入力し、[**作成**] を選択します。

      ![新しいプロジェクトダイアログを設定する](./media/walkthrough-my-first-wpf-desktop-application/configure-new-project-dialog.png)

      プロジェクトが作成され、既定のアプリケーション ウィンドウのデザイナー**が開きます**。

2. *アプリケーション.xaml* (Visual Basic) または*App.xaml* (C#) を開きます。

    この XAML ファイルは、WPF アプリケーションとすべてのアプリケーション リソースを定義します。 このファイルを使用して、アプリケーションの起動時に自動的に表示される UI (この場合*は MainWindow.xaml)* を指定することもできます。

    XAML は、Visual Basic で次のようになります。

    [!code-xaml[ExpenseIt#1_A](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/Application.xaml#1_a)]

    C# の次のようにします。

    [!code-xaml[ExpenseIt#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/App.xaml#1)]

3. *を*開きます。

    この XAML ファイルは、アプリケーションのメイン ウィンドウであり、ページで作成されたコンテンツを表示します。 クラス<xref:System.Windows.Window>は、ウィンドウのタイトル、サイズ、アイコンなどのプロパティを定義し、閉じる、または非表示などのイベントを処理します。

4. 要素を<xref:System.Windows.Window>に変更<xref:System.Windows.Navigation.NavigationWindow>します。

   ```xaml
   <NavigationWindow x:Class="ExpenseIt.MainWindow"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        ...
   </NavigationWindow>
   ```

   このアプリは、ユーザーの入力に応じて異なるコンテンツに移動します。 これが主なもの<xref:System.Windows.Window>を に変更する必要がある理由<xref:System.Windows.Navigation.NavigationWindow>です。 <xref:System.Windows.Navigation.NavigationWindow>のプロパティをすべて継承<xref:System.Windows.Window>します。 XAML<xref:System.Windows.Navigation.NavigationWindow>ファイル内の要素は、クラスのインスタンス<xref:System.Windows.Navigation.NavigationWindow>を作成します。 詳細については、「ナビゲーションの[概要](../app-development/navigation-overview.md)」を参照してください。

5. タグの<xref:System.Windows.Controls.Grid>間から要素を<xref:System.Windows.Navigation.NavigationWindow>削除します。

6. 要素の XAML コードで次のプロパティ<xref:System.Windows.Navigation.NavigationWindow>を変更します。

    - プロパティを<xref:System.Windows.Window.Title%2A>"`ExpenseIt`" に設定します。

    - このプロパティ<xref:System.Windows.FrameworkElement.Height%2A>を 350 ピクセルに設定します。

    - プロパティを<xref:System.Windows.FrameworkElement.Width%2A>500 ピクセルに設定します。

    VISUAL Basic の XAML は次のようになります。

    [!code-xaml[ExpenseIt#2_A](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt/MainWindow.xaml#2_a)]

    C# の場合は、次のようにします。

    [!code-xaml[ExpenseIt#2](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/MainWindow.xaml#2)]

7. *を*開くか *、MainWindow.xaml.cs.*

    このファイルは *、MainWindow.xaml*で宣言されたイベントを処理するコードを含む分離コード ファイルです。 このファイルには、XAML で定義されたウィンドウの部分クラスが含まれています。

8. C# を使用している場合は、クラス`MainWindow`をから派生するように<xref:System.Windows.Navigation.NavigationWindow>変更します。 (Visual Basic では、これは XAML でウィンドウを変更すると自動的に発生します)。C# コードは次のようになります。

   [!code-csharp[ExpenseIt#3](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/MainWindow.xaml.cs?highlight=21)]

## <a name="add-files-to-the-application"></a>アプリケーションにファイルを追加する

このセクションでは、アプリケーションに 2 つのページと 1 つのイメージを追加します。

1. プロジェクトに新しいページを追加し、名前を*`ExpenseItHome.xaml`* 付けます。

   1. **ソリューション エクスプローラ**で、プロジェクト ノードを**`ExpenseIt`** 右クリックし、[**ページ**の**追加]** > を選択します。

   1. [**新しい項目の追加]** ダイアログ ボックスで、**ページ (WPF)** テンプレートが既に選択されています。 名前**`ExpenseItHome`** を入力し、[**追加**] を選択します。

    このページは、アプリケーションの起動時に表示される最初のページです。 経費精算書を表示するために選択するユーザーの一覧が表示されます。

1. を*`ExpenseItHome.xaml`* 開きます。

1. を<xref:System.Windows.Controls.Page.Title%2A>""`ExpenseIt - Home`に設定します。

1. 350`DesignHeight`ピクセル、500`DesignWidth`ピクセルに設定します。

    これで、VISUAL Basic の XAML が次のように表示されます。

    [!code-xaml[ExpenseIt#6_A](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseItHome.xaml#6_a)]

    C# の場合は、次のようにします。

    [!code-xaml[ExpenseIt#6](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt2/ExpenseItHome.xaml#6)]

1. *を*開きます。

1. 要素に<xref:System.Windows.Navigation.NavigationWindow.Source%2A>プロパティを<xref:System.Windows.Navigation.NavigationWindow>追加し、それを "`ExpenseItHome.xaml`" に設定します。

    これは、*`ExpenseItHome.xaml`* アプリケーションの起動時に最初に開かれたページになります。

    Visual Basic の XAML の例:

    [!code-xaml[ExpenseIt#7_A](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/MainWindow.xaml#7_a)]

    そしてC#で:

    [!code-xaml[ExpenseIt#7](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt2/MainWindow.xaml#7)]

   > [!TIP]
   > [プロパティ] ウィンドウの **[その他**] カテゴリで **[ソース****] プロパティ**を設定することもできます。
   >
   > ![[プロパティ] ウィンドウの [ソース] プロパティ](./media/properties-source.png)

1. プロジェクトに別の新しい WPF ページを追加し、名前*を付けます。*

   1. **ソリューション エクスプローラ**で、プロジェクト ノードを**`ExpenseIt`** 右クリックし、[**ページ**の**追加]** > を選択します。

   1. [**新しい項目の追加]** ダイアログボックスで、[**ページ (WPF)]** テンプレートを選択します。 **[経費明細書ページ]** という名前を入力し、[**追加**] を選択します。

    このページには、**`ExpenseItHome`** ページで選択したユーザーの経費精算書が表示されます。

1. *ExpenseReportPage.xaml*を開きます。

1. を<xref:System.Windows.Controls.Page.Title%2A>""`ExpenseIt - View Expense`に設定します。

1. 350`DesignHeight`ピクセル、500`DesignWidth`ピクセルに設定します。

    *現在*、ビジュアル ベーシックでは次のようになります。

    [!code-xaml[ExpenseIt#4_A](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseReportPage.xaml#4_a)]

    C# の次のようにします。

    [!code-xaml[ExpenseIt#4](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/ExpenseReportPage.xaml#4)]

1. を開きます*ExpenseReportPage.xaml.cs* *ExpenseReportPage.xaml.vb* *ExpenseItHome.xaml.cs。* *ExpenseItHome.xaml.cs*

    新しいページ ファイルを作成すると、Visual Studio によって *、その分離コード*ファイルが自動的に作成されます。 これらの分離コード ファイルでは、ユーザー入力に対応するためのロジックを処理します。

    コードは、 の**`ExpenseItHome`** 次のようになります。

    [!code-csharp[ExpenseIt#2_5](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt2/ExpenseItHome.xaml.cs#2_5)]

    [!code-vb[ExpenseIt#2_5](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseItHome.xaml.vb#2_5)]

    そして、**経費報告ページ**の次のように:

    [!code-csharp[ExpenseIt#5](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/ExpenseReportPage.xaml.cs#5)]

    [!code-vb[ExpenseIt#5](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseReportPage.xaml.vb#5)]

1. プロジェクトに*watermark.png*という名前のイメージを追加します。 独自のイメージを作成したり、サンプル コードからファイルをコピーしたり[、Microsoft/WPF-サンプル](https://raw.githubusercontent.com/microsoft/WPF-Samples/master/Getting%20Started/WalkthroughFirstWPFApp/csharp/watermark.png)GitHub リポジトリから取得したりできます。

    1. プロジェクト ノードを右クリックし、[**既存項目**の**追加** > ] を選択するか **、Shift**+Alt**A**キー**を**+押します。

    2. [**既存項目の追加]** ダイアログで、ファイル フィルタを **[すべてのファイル]** または [**イメージ ファイル]** に設定し、使用するイメージ ファイルを参照して、[**追加**] を選択します。

## <a name="build-and-run-the-application"></a>アプリケーションの構築と実行

1. アプリケーションをビルドして実行するには **、F5**キーを押すか、[**デバッグ**] メニューから **[デバッグの開始**] を選択します。

    次の図は、ボタンを持<xref:System.Windows.Navigation.NavigationWindow>つアプリケーションを示しています。

    ![ビルドして実行した後のアプリケーション。](./media/walkthrough-my-first-wpf-desktop-application/build-run-application.png)

2. アプリケーションを閉じて、Visual Studio に戻ります。

## <a name="create-the-layout"></a>レイアウトを作成する

レイアウトは、UI 要素を配置するための順序付けされた方法を提供し、UI のサイズと位置を管理します。 通常、レイアウトを作成するには、次のいずれかのレイアウト コントロールを使用します。

- <xref:System.Windows.Controls.Canvas>- キャンバス領域に対する相対座標を使用して子要素を明示的に配置できる領域を定義します。
- <xref:System.Windows.Controls.DockPanel>- 子要素を水平方向または垂直方向に配置できる領域を定義します。
- <xref:System.Windows.Controls.Grid>- 列と行で構成される柔軟なグリッド領域を定義します。
- <xref:System.Windows.Controls.StackPanel>- 子要素を、水平方向または垂直方向に配置できる単一の行に配置します。
- <xref:System.Windows.Controls.VirtualizingStackPanel>- 水平方向または垂直方向に配置された単一の行にコンテンツを配置し、仮想化します。
- <xref:System.Windows.Controls.WrapPanel>- 子要素を左から右に連続した位置に配置し、内容を含むボックスの端の次の行に分割します。 後続の順序は、Orientation プロパティの値に応じて、上から下へ、または右から左に順番に行われます。

これらのレイアウト コントロールは、子要素に対して特定の種類のレイアウトをサポートします。 `ExpenseIt`ページのサイズを変更することができ、各ページには、他の要素と並んで水平方向および垂直方向に配置された要素があります。 この例では、<xref:System.Windows.Controls.Grid>はアプリケーションのレイアウト要素として使用されます。

> [!TIP]
> 要素の詳細<xref:System.Windows.Controls.Panel>については、[パネルの概要 を](../controls/panels-overview.md)参照してください。 レイアウトの詳細については、「[レイアウト](../advanced/layout.md)」を参照してください。

このセクションでは、 に列と行の定義を追加して、3 行 10 ピクセルの余白を持つ単<xref:System.Windows.Controls.Grid>一*`ExpenseItHome.xaml`* 列テーブルを作成します。

1. では*`ExpenseItHome.xaml`*、要素の<xref:System.Windows.FrameworkElement.Margin%2A>プロパティを<xref:System.Windows.Controls.Grid>"10,0,10,10"に設定します。

   ```xaml
   <Grid Margin="10,0,10,10">
   ```

   > [!TIP]
   > [**プロパティ]** ウィンドウの **[レイアウト**] カテゴリで、**余白**の値を設定することもできます。
   >
   > ![[プロパティ] ウィンドウの余白の値](./media/properties-margin.png)

2. タグの間に次の<xref:System.Windows.Controls.Grid>XAML を追加して、行定義と列定義を作成します。

    [!code-xaml[ExpenseIt#8](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt3/ExpenseItHome.xaml#8)]

    2<xref:System.Windows.Controls.RowDefinition.Height%2A>つの行の は<xref:System.Windows.GridLength.Auto%2A>に設定され、行の内容に基づいて行のサイズが変更されます。 デフォルト<xref:System.Windows.Controls.RowDefinition.Height%2A>は<xref:System.Windows.GridUnitType.Star>サイズ変更で、行の高さは使用可能なスペースの加重比率です。 たとえば、2 つの行のそれぞれに<xref:System.Windows.Controls.RowDefinition.Height%2A>"*" がある場合、それぞれ使用可能なスペースの半分の高さがあります。

    次<xref:System.Windows.Controls.Grid>の XAML が含まれるはずです。

    [!code-xaml[ExpenseIt#9](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt3/ExpenseItHome.xaml#9)]

## <a name="add-controls"></a>コントロールの追加

このセクションでは、ホーム ページの UI を更新して、経費精算書を表示するユーザーを 1 人選択したユーザーの一覧を表示します。 コントロールとは、ユーザーがアプリケーションと対話できるようにする UI オブジェクトのことです。 詳細については、「[コントロール](../controls/index.md)」を参照してください。

この UI を作成するには、次の要素を*`ExpenseItHome.xaml`* に追加します。

- A <xref:System.Windows.Controls.ListBox> (人のリスト用)。
- A <xref:System.Windows.Controls.Label> (リスト ヘッダーの場合)。
- A <xref:System.Windows.Controls.Button> (クリックすると、一覧で選択したユーザーの経費精算書を表示します)。

各コントロールは、添付プロパティを設定することにより<xref:System.Windows.Controls.Grid>、 の<xref:System.Windows.Controls.Grid.Row%2A?displayProperty=nameWithType>行に配置されます。 添付プロパティの詳細については、「[添付プロパティの概要](../advanced/attached-properties-overview.md)」を参照してください。

1. で*`ExpenseItHome.xaml`*、タグの間に次の<xref:System.Windows.Controls.Grid>XAML を追加します。

   [!code-xaml[ExpenseIt#10](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt4/ExpenseItHome.xaml#10)]

   > [!TIP]
   > また、コントロールを作成するには、[**ツールボックス**] ウィンドウからデザイン ウィンドウにコントロールをドラッグし、[**プロパティ]** ウィンドウでプロパティを設定します。

2. アプリケーションをビルドして実行します。

    次の図は、作成したコントロールを示しています。

![名前の一覧を表示するサンプルのスクリーンショット](./media/walkthrough-my-first-wpf-desktop-application/add-application-controls.png)

## <a name="add-an-image-and-a-title"></a>画像とタイトルを追加する

このセクションでは、ホーム ページの UI を画像とページ タイトルで更新します。

1. で*`ExpenseItHome.xaml`*、固定<xref:System.Windows.Controls.Grid.ColumnDefinitions%2A><xref:System.Windows.Controls.ColumnDefinition.Width%2A>の 230 ピクセルの別の列をに追加します。

    [!code-xaml[ExpenseIt#11](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseItHome.xaml?highlight=52-55)]

2. に別の行を<xref:System.Windows.Controls.Grid.RowDefinitions%2A>追加し、合計 4 行を指定します。

    [!code-xaml[ExpenseIt#11b](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseItHome.xaml?highlight=57-62)]

3. 3 つのコントロール ([境界線]、[リスト<xref:System.Windows.Controls.Grid.Column%2A?displayProperty=nameWithType>ボックス]、および [ボタン]) のそれぞれでプロパティを 1 に設定して、コントロールを 2 番目の列に移動します。

4. 3 つのコントロール ([境界線]、[リスト<xref:System.Windows.Controls.Grid.Row%2A?displayProperty=nameWithType>ボックス]、[ボタン]) と Border 要素の値を 1 ずつ増やして、各コントロールを行の下に移動します。

   3 つのコントロールの XAML は、次のようになります。

    [!code-xaml[ExpenseIt#12](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#12)]

5. タグと<xref:System.Windows.Controls.Panel.Background%2A?displayProperty=nameWithType>タグの間に次の XAML を追加して、プロパティを*watermark.png*イメージ ファイルに`<Grid>``</Grid>`設定します。

    [!code-xaml[ExpenseIt#14](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#14)]

6. 要素の<xref:System.Windows.Controls.Border>前に、コンテンツ<xref:System.Windows.Controls.Label>「経費報告の表示」 を付けて を追加します。 このラベルはページのタイトルです。

    [!code-xaml[ExpenseIt#13](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#13)]

7. アプリケーションをビルドして実行します。

次の図は、追加した結果を示しています。

![費用新しい画像の背景とページタイトルを示すサンプルスクリーンショット](./media/walkthrough-my-first-wpf-desktop-application/add-application-image-title.png)

## <a name="add-code-to-handle-events"></a>イベントを処理するコードを追加する

1. で*`ExpenseItHome.xaml`*、要素に<xref:System.Windows.Controls.Primitives.ButtonBase.Click>イベント ハンドラーを<xref:System.Windows.Controls.Button>追加します。 詳細については、「[方法 : 簡単なイベント ハンドラを作成する](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/bb675300(v=vs.100))」を参照してください。

    [!code-xaml[ExpenseIt#15](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt6/ExpenseItHome.xaml#15)]

2. または*`ExpenseItHome.xaml.vb`**`ExpenseItHome.xaml.cs`* を開きます。

3. ボタン クリック イベント`ExpenseItHome`ハンドラーを追加するクラスに次のコードを追加します。 イベント ハンドラは **、経費レポート ページを**開きます。

    [!code-csharp[ExpenseIt#16](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt6/ExpenseItHome.xaml.cs#16)]
    [!code-vb[ExpenseIt#16](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt6/ExpenseItHome.xaml.vb#16)]

## <a name="create-the-ui-for-expensereportpage"></a>経費明細書ページの UI を作成します。

*ページで***`ExpenseItHome`** 選択した人の経費精算書が表示されます。 ここでは、**経費レポート ページ**の UI を作成します。 また、さまざまな UI 要素に背景色と塗りつぶしの色を追加します。

1. *ExpenseReportPage.xaml*を開きます。

2. タグの間に次の<xref:System.Windows.Controls.Grid>XAML を追加します。

    [!code-xaml[ExpenseIt#17](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt6/ExpenseReportPage.xaml#17)]

    この UI は*`ExpenseItHome.xaml`*、 に似ていますが、レポート<xref:System.Windows.Controls.DataGrid>データは に表示されます。

3. アプリケーションをビルドして実行します。

4. [**表示**] ボタンを選択します。

    経費明細書ページが表示されます。 また、戻るナビゲーション ボタンが有効になっていることに注意してください。

次の図は *、ExpenseReportPage.xaml*に追加された UI 要素を示しています。

![経費経費レポート ページ用に作成した UI を示すサンプル のスクリーンショットです。](./media/walkthrough-my-first-wpf-desktop-application/create-application-ui.png)

## <a name="style-controls"></a>スタイル コントロール

UI の同じ型のすべての要素で、さまざまな要素の外観が同じであることが多いです。 UI では[、スタイル](../controls/styling-and-templating.md)を使用して、複数の要素にわたって外観を再利用可能にします。 スタイルの再利用性は、XAML の作成と管理を簡略化するのに役立ちます。 このセクションでは、これまでの手順で定義した要素ごとの属性を、スタイルに置き換えます。

1. *アプリケーション.xaml*または*App.xaml*を開きます。

2. タグの間に次の<xref:System.Windows.Application.Resources%2A?displayProperty=nameWithType>XAML を追加します。

    [!code-xaml[ExpenseIt#18](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt7/App.xaml#18)]

    この XAML は、次のスタイルを追加します。

    - `headerTextStyle`: ページ タイトル <xref:System.Windows.Controls.Label>の書式を設定します。

    - `labelStyle`: <xref:System.Windows.Controls.Label> コントロールの書式を設定します。

    - `columnHeaderStyle`: <xref:System.Windows.Controls.Primitives.DataGridColumnHeader>の書式を設定します。

    - `listHeaderStyle`: リスト ヘッダーの <xref:System.Windows.Controls.Border> コントロールの書式を設定します。

    - `listHeaderTextStyle`: リストヘッダー<xref:System.Windows.Controls.Label>をフォーマットするには.

    - `buttonStyle`: on `ExpenseItHome.xaml`<xref:System.Windows.Controls.Button>をフォーマットするには.

    スタイルは<xref:System.Windows.Application.Resources%2A?displayProperty=nameWithType>プロパティ要素のリソースと子であることに注意してください。 ここでは、スタイルはアプリケーション内のすべての要素に適用されます。 NET アプリでリソースを使用する例については、「アプリケーション[リソースの使用](../advanced/how-to-use-application-resources.md)」を参照してください。

3. では*`ExpenseItHome.xaml`*、要素間のすべてのもの<xref:System.Windows.Controls.Grid>を次の XAML に置き換えます。

    [!code-xaml[ExpenseIt#19](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt7/ExpenseItHome.xaml#19)]

    各コントロールの外観を定義する <xref:System.Windows.VerticalAlignment> や <xref:System.Windows.Media.FontFamily> などのプロパティは、これらのスタイルを適用することで、削除されて置き換えられます。 たとえば、`headerTextStyle`は "経費報告の表示"<xref:System.Windows.Controls.Label>に適用されます。

4. *ExpenseReportPage.xaml*を開きます。

5. 要素間のすべてのもの<xref:System.Windows.Controls.Grid>を次の XAML に置き換えます。

    [!code-xaml[ExpenseIt#20](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt7/ExpenseReportPage.xaml#20)]

    この XAML は、 <xref:System.Windows.Controls.Label> <xref:System.Windows.Controls.Border>要素にスタイルを追加します。

6. アプリケーションをビルドして実行します。 ウィンドウの外観は、以前と同じです。

    ![経費前回のセクションと同じ外観のサンプルスクリーンショットです。](./media/walkthrough-my-first-wpf-desktop-application/create-application-ui.png)

7. アプリケーションを閉じて、Visual Studio に戻ります。

## <a name="bind-data-to-a-control"></a>コントロールにデータをバインドする

このセクションでは、さまざまなコントロールにバインドされた XML データを作成します。

1. で*`ExpenseItHome.xaml`*、開始<xref:System.Windows.Controls.Grid>要素の後に次の XAML を追加<xref:System.Windows.Data.XmlDataProvider>して、各ユーザーのデータを含む を作成します。

    [!code-xaml[ExpenseIt#23](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml?range=13,16-40,49)]

    データはリソースとして作成されます<xref:System.Windows.Controls.Grid>。 通常、このデータはファイルとしてロードされますが、わかりやすくするため、データはインラインで追加されます。

2. 要素内`<Grid.Resources>`に、要素の後`<xref:System.Windows.DataTemplate>`に<xref:System.Windows.Controls.ListBox>データを表示する方法を定義する次の要素を`<XmlDataProvider>`追加します。

    [!code-xaml[ExpenseIt#24](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml?range=13,43-46,49)]

    データ テンプレートの詳細については、「[データ テンプレートの概要」を](../data/data-templating-overview.md)参照してください。

3. 既存<xref:System.Windows.Controls.ListBox>の XAML を次の XAML に置き換えます。

    [!code-xaml[ExpenseIt#25](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#25)]

    この XAML は<xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>、のプロパティ<xref:System.Windows.Controls.ListBox>をデータ ソースにバインドし、データ テンプレート<xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A>を として適用します。

## <a name="connect-data-to-controls"></a>コントロールへのデータの接続

次に、**`ExpenseItHome`** ページで選択されている名前を取得し、**それを ExpenseReportPage**のコンストラクタに渡すコードを追加します。 **渡**された項目を使用してデータ コンテキストを設定します。 *ExpenseReportPage.xaml*

1. *ExpenseReportPage.xaml.vb* または *ExpenseReportPage.xaml.cs*を開きます。

2. オブジェクトを取得するコンストラクターを追加して、選択した個人の経費報告書データを渡せるようにします。

    [!code-csharp[ExpenseIt#26](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseReportPage.xaml.cs#26)]
    [!code-vb[ExpenseIt#26](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt8/ExpenseReportPage.xaml.vb#26)]

3. または*`ExpenseItHome.xaml.vb`**`ExpenseItHome.xaml.cs`* を開きます。

4. 選択した<xref:System.Windows.Controls.Primitives.ButtonBase.Click>ユーザーの経費報告書データを渡す新しいコンストラクターを呼び出すイベント ハンドラーを変更します。

    [!code-csharp[ExpenseIt#27](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml.cs#27)]
    [!code-vb[ExpenseIt#27](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt8/ExpenseItHome.xaml.vb#27)]

## <a name="style-data-with-data-templates"></a>データ テンプレートを使用したスタイル データ

このセクションでは、データ テンプレートを使用して、データ バインド リストの各項目の UI を更新します。

1. *ExpenseReportPage.xaml*を開きます。

2. "Name" 要素と "Department"<xref:System.Windows.Controls.Label>要素の内容を適切なデータ ソース プロパティにバインドします。 データ バインディングの詳細については、「データ バインディングの[概要](../../../desktop-wpf/data/data-binding-overview.md)」を参照してください。

    [!code-xaml[ExpenseIt#31](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseReportPage.xaml#31)]

3. 開始<xref:System.Windows.Controls.Grid>要素の後に、経費精算書データの表示方法を定義する次のデータ テンプレートを追加します。

    [!code-xaml[ExpenseIt#30](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseReportPage.xaml#30)]

4. 要素を<xref:System.Windows.Controls.DataGridTextColumn>要素の<xref:System.Windows.Controls.DataGridTemplateColumn>下<xref:System.Windows.Controls.DataGrid>に置き換え、テンプレートを適用します。

    [!code-xaml[ExpenseIt#32](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseReportPage.xaml#32)]

5. アプリケーションをビルドして実行します。

6. ユーザーを選択し、[**表示**] ボタンを選択します。

次の図は、コントロール、レイアウト`ExpenseIt`、スタイル、データ バインディング、およびデータ テンプレートが適用されたアプリケーションの両方のページを示しています。

![名前リストと経費報告書を表示するアプリの両方のページ。](./media/walkthrough-my-first-wpf-desktop-application/application-data-templates.png)

> [!NOTE]
> このサンプルでは、WPF の特定の機能を示し、セキュリティ、ローカライズ、アクセシビリティなどのベスト プラクティスに従うわけではありません。 WPF と .NET アプリ開発のベスト プラクティスの包括的なカバレッジについては、次のトピックを参照してください。
>
> - [アクセシビリティ](../../ui-automation/accessibility-best-practices.md)
> - [セキュリティ](../security-wpf.md)
> - [WPF のグローバリゼーションとローカライズ](../advanced/wpf-globalization-and-localization-overview.md)
> - [WPF のパフォーマンス](../advanced/optimizing-wpf-application-performance.md)

## <a name="next-steps"></a>次のステップ

このチュートリアルでは、Windows プレゼンテーション ファンデーション (WPF) を使用して UI を作成するためのいくつかの手法を説明しました。 これで、データ バインド .NET アプリの構成要素の基本を理解する必要があります。 WPF のアーキテクチャおよびプログラミング モデルの詳細については、次のトピックを参照してください。

- [WPF アーキテクチャ](../advanced/wpf-architecture.md)
- [XAML の概要 (WPF)](../advanced/xaml-overview-wpf.md)
- [依存関係プロパティの概要](../advanced/dependency-properties-overview.md)
- [レイアウト](../advanced/layout.md)

アプリケーションの作成の詳細については、次のトピックを参照してください。

- [アプリケーション開発](../app-development/index.md)
- [コントロール](../controls/index.md)
- [データ バインディングの概要](../../../desktop-wpf/data/data-binding-overview.md)
- [グラフィックスとマルチメディア](../graphics-multimedia/index.md)
- [WPF のドキュメント](../advanced/documents-in-wpf.md)

## <a name="see-also"></a>関連項目

- [パネルの概要](../controls/panels-overview.md)
- [データ テンプレートの概要](../data/data-templating-overview.md)
- [WPF アプリケーションをビルドする](../app-development/building-a-wpf-application-wpf.md)
- [スタイルとテンプレート](../controls/styles-and-templates.md)
