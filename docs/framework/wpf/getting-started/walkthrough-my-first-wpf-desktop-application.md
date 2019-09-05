---
title: Visual Studio で WPF アプリケーションを作成する
ms.date: 03/20/2019
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
ms.openlocfilehash: 4919424339df1f8d2c68465bd9f9af42f344fe37
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/04/2019
ms.locfileid: "70254067"
---
# <a name="walkthrough-my-first-wpf-desktop-application"></a>チュートリアル: 初めての WPF デスクトップ アプリケーション

この記事では、ほとんどの WPF アプリケーションに共通の要素を含む Windows Presentation Foundation (WPF) デスクトップアプリケーションを開発する方法について説明します。Extensible Application Markup Language (XAML) マークアップ、分離コード、アプリケーション定義、コントロール、レイアウト、データバインディング、およびスタイル。 アプリケーションを開発するには、Visual Studio を使用します。 

このチュートリアルでは、次の手順について説明します。

- XAML を使用して、アプリケーションのユーザーインターフェイス (UI) の外観をデザインします。

- アプリケーションの動作を構築するコードを記述します。

- アプリケーションを管理するためのアプリケーション定義を作成します。

- コントロールを追加し、レイアウトを作成してアプリケーション UI を作成します。

- アプリケーションの UI 全体で一貫した外観のスタイルを作成します。

- Ui にデータを設定し、データと UI の同期を保つために、UI をデータにバインドします。

チュートリアルを終了すると、選択したユーザーの経費報告書をユーザーが表示できるスタンドアロン Windows アプリケーションが作成されます。 アプリケーションは、ブラウザースタイルのウィンドウでホストされるいくつかの WPF ページで構成されています。

> [!TIP]
> このチュートリアルのビルドに使用されるサンプルコードは、Visual Basic とC# [チュートリアルの WPF アプリのサンプルコード](https://github.com/Microsoft/WPF-Samples/tree/master/Getting%20Started/WalkthroughFirstWPFApp)の両方で使用できます。
>
> この記事の右上隅にあるC# **\<ドロップダウンを使用/>** して、と Visual Basic の間でサンプルコードのコード言語を切り替えることができます。

## <a name="prerequisites"></a>必須コンポーネント

- Visual Studio 2017 以降 (この記事では Visual Studio 2019 を使用します)

   最新バージョンの Visual Studio をインストールする方法の詳細については、「 [Visual studio のインストール](/visualstudio/install/install-visual-studio)」を参照してください。

## <a name="create-the-application-project"></a>アプリケーションプロジェクトを作成する

最初の手順では、アプリケーションの定義、2つのページ、およびイメージを含むアプリケーションインフラストラクチャを作成します。

1. Visual Basic または Visual C# のという名前で新しい WPF アプリケーション プロジェクトを作成する **`ExpenseIt`** :

   1. Visual Studio を開き、 **[作業の開始]** メニューの **[新しいプロジェクトの作成]** を選択します。

      **[新しいプロジェクトの作成]** ダイアログボックスが表示されます。

   2. **言語** ドロップダウンで、 **C#**  または  **Visual Basic** を選択します。
      
   3. **[WPF アプリ (.NET Framework)]** テンプレートを選択し、 **[次へ]** を選択します。 
     
      ![[新しいプロジェクトの作成] ダイアログ](./media/walkthrough-my-first-wpf-desktop-application/create-new-project-dialog.png)
    
      **[新しいプロジェクトの構成]** ダイアログボックスが開きます。

   4. プロジェクト名を入力 **`ExpenseIt`** 選び **作成** です。

      ![[新しいプロジェクトの構成] ダイアログ](./media/walkthrough-my-first-wpf-desktop-application/configure-new-project-dialog.png)

      Visual Studio によってプロジェクトが作成され、 **mainwindow.xaml**という名前の既定のアプリケーションウィンドウのデザイナーが開きます。

2. *アプリケーション .xaml* (Visual Basic) または*app.xaml* (C#) を開きます。

    この XAML ファイルは、WPF アプリケーションとすべてのアプリケーションリソースを定義します。 また、このファイルを使用して、アプリケーションの起動時に自動的に表示される UI (この場合は Mainwindow.xaml) を指定し*ます*。

    XAML は、Visual Basic では次のようになります。

    [!code-xaml[ExpenseIt#1_A](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/Application.xaml#1_a)]

    およびでは、次C#のようになります。

    [!code-xaml[ExpenseIt#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/App.xaml#1)]

3. *MainWindow.xaml*を開きます。

    この XAML ファイルは、アプリケーションのメインウィンドウであり、ページで作成されたコンテンツを表示します。 クラス<xref:System.Windows.Window>は、タイトル、サイズ、アイコンなどのウィンドウのプロパティを定義し、終了や非表示などのイベントを処理します。

4. <xref:System.Windows.Navigation.NavigationWindow>.xaml の<xref:System.Windows.Window>要素を、次に示すように変更します。

   ```xaml
   <NavigationWindow x:Class="ExpenseIt.MainWindow"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        ...
   </NavigationWindow>
   ```

   このアプリは、ユーザーの入力に応じてさまざまなコンテンツに移動します。 そのため、メイン ウィンドウを<xref:System.Windows.Window>から<xref:System.Windows.Navigation.NavigationWindow>に変更する必要があります。 <xref:System.Windows.Navigation.NavigationWindow>  は、<xref:System.Windows.Window>のすべてのプロパティを継承しています。 XAML ファイルの<xref:System.Windows.Navigation.NavigationWindow> 要素によって、クラスのインスタンスが作成<xref:System.Windows.Navigation.NavigationWindow>されます。 詳細については、「[ナビゲーションの概要](../app-development/navigation-overview.md)」を参照してください。

5. タグ間の<xref:System.Windows.Controls.Grid>要素を削除<xref:System.Windows.Navigation.NavigationWindow>します。

6. <xref:System.Windows.Navigation.NavigationWindow>要素の XAML コードで、次のプロパティを変更します。

    - プロパティを "`ExpenseIt`" に設定します。 <xref:System.Windows.Window.Title%2A>

    - <xref:System.Windows.FrameworkElement.Height%2A>プロパティを350ピクセルに設定します。

    - <xref:System.Windows.FrameworkElement.Width%2A>プロパティを500ピクセルに設定します。

    XAML は、Visual Basic に対して次のようになります。

    [!code-xaml[ExpenseIt#2_A](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt/MainWindow.xaml#2_a)]

    では、次のC#ようになります。

    [!code-xaml[ExpenseIt#2](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/MainWindow.xaml#2)]

7. *Mainwindow.xaml*または*MainWindow.xaml.cs*を開きます。

    このファイルは、 *mainwindow.xaml*で宣言されたイベントを処理するコードを含む分離コードファイルです。 このファイルには、XAML で定義されたウィンドウの部分クラスが含まれています。

8. を使用してC#いる場合は`MainWindow` 、から<xref:System.Windows.Navigation.NavigationWindow>派生するようにクラスを変更します。 (Visual Basic では、XAML でウィンドウを変更すると、自動的にこの処理が行われます)。コードC#は次のようになります。

   [!code-csharp[ExpenseIt#3](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/MainWindow.xaml.cs?highlight=21)]

## <a name="add-files-to-the-application"></a>アプリケーションへのファイルの追加

このセクションでは、アプリケーションに 2 つのページと 1 つのイメージを追加します。

1. プロジェクトに新しいページを追加し、名前 *`ExpenseItHome.xaml`* :

   1. **ソリューション エクスプ ローラー**を右クリックし、 **`ExpenseIt`** プロジェクト ノード**追加** > **ページ**します。

   1. **[新しい項目の追加]** ダイアログでは、 **[ページ (WPF)]** テンプレートは既に選択されています。 名前を入力します **`ExpenseItHome`** 、し、**追加**します。

    このページは、アプリケーションの起動時に表示される最初のページです。 このレポートには、の経費明細書を表示するために選択する相手の一覧が表示されます。

1. 開いている *`ExpenseItHome.xaml`* します。

1. <xref:System.Windows.Controls.Page.Title%2A>を"`ExpenseIt - Home`" に設定します。

1. を350ピクセル`DesignWidth`に、を500ピクセルに設定します。 `DesignHeight`

    XAML は、Visual Basic に対して次のように表示されるようになりました。

    [!code-xaml[ExpenseIt#6_A](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseItHome.xaml#6_a)]

    では、次のC#ようになります。

    [!code-xaml[ExpenseIt#6](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt2/ExpenseItHome.xaml#6)]

1. *MainWindow.xaml*を開きます。

1. 要素にプロパティを<xref:System.Windows.Navigation.NavigationWindow.Source%2A>追加し、それを "`ExpenseItHome.xaml`" に設定します。 <xref:System.Windows.Navigation.NavigationWindow>

    これにより設定 *`ExpenseItHome.xaml`* アプリケーションの起動時を開く最初のページになります。 

    Visual Basic の XAML の例:

    [!code-xaml[ExpenseIt#7_A](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/MainWindow.xaml#7_a)]

    および C# の場合。

    [!code-xaml[ExpenseIt#7](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt2/MainWindow.xaml#7)]

   > [!TIP]
   > また、 **[プロパティ]** ウィンドウの **[その他]** カテゴリで、 **[ソース]** プロパティを設定することもできます。
   >
   > ![プロパティウィンドウのソースプロパティ](./media/properties-source.png)

1. 別の新しい WPF ページをプロジェクトに追加し、次*のように*名前を指定します。

   1. **ソリューション エクスプ ローラー**を右クリックし、 **`ExpenseIt`** プロジェクト ノード**追加** > **ページ**します。

   1. **[新しい項目の追加]** ダイアログで、 **[ページ (WPF)]** テンプレートを選択します。 [名前の指定] をクリック**し、[** **追加**] を選択します。

    このページで選択されているユーザーの経費報告書が表示されます、 **`ExpenseItHome`** ページ。

1. *ExpenseReportPage.xaml*を開きます。

1. <xref:System.Windows.Controls.Page.Title%2A>を"`ExpenseIt - View Expense`" に設定します。

1. を350ピクセル`DesignWidth`に、を500ピクセルに設定します。 `DesignHeight` 

    Visual Basic では、この*xaml*は次のようになります。

    [!code-xaml[ExpenseIt#4_A](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseReportPage.xaml#4_a)]

    およびでは、次C#のようになります。

    [!code-xaml[ExpenseIt#4](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/ExpenseReportPage.xaml#4)]

1. *Expenseithome.xaml*を開き、 *ExpenseItHome.xaml.cs* 、または ExpenseReportPage.xaml.cs *、また*はを開きます。

    新しいページファイルを作成すると、Visual Studio によってその*分離コード*ファイルが自動的に作成されます。 これらの分離コード ファイルでは、ユーザー入力に対応するためのロジックを処理します。

    コードは、次のようになります **`ExpenseItHome`** :

    [!code-csharp[ExpenseIt#2_5](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt2/ExpenseItHome.xaml.cs#2_5)]

    [!code-vb[ExpenseIt#2_5](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseItHome.xaml.vb#2_5)]

    また、次のような**ページ**があります。

    [!code-csharp[ExpenseIt#5](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/ExpenseReportPage.xaml.cs#5)]

    [!code-vb[ExpenseIt#5](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseReportPage.xaml.vb#5)]

1. *透かし*という名前のイメージをプロジェクトに追加します。 独自のイメージを作成したり、サンプルコードからファイルをコピーしたり、[ここで](https://raw.githubusercontent.com/microsoft/WPF-Samples/master/Getting%20Started/WalkthroughFirstWPFApp/csharp/watermark.png)取得したりすることができます。

    1. プロジェクトノードを右クリックし、[**既存項目**の**追加** > ] を選択するか、 **Shift**+**Alt**+**A**キーを押します。

    2. **[既存項目の追加]** ダイアログボックスで、すべての **[ファイル]** または **[イメージファイル]** のいずれかにファイルフィルターを設定し、使用するイメージファイルを参照して **[追加]** を選択します。

## <a name="build-and-run-the-application"></a>アプリケーションのビルドと実行

1. アプリケーションをビルドして実行するには、 **F5**キーを押すか、 **[デバッグ]** メニューの **[デバッグの開始]** をクリックします。

    次の図は、 <xref:System.Windows.Navigation.NavigationWindow>ボタンを使用したアプリケーションを示しています。

    ![アプリケーションをビルドして実行します。](./media/walkthrough-my-first-wpf-desktop-application/build-run-application.png)

2. アプリケーションを閉じて、Visual Studio に戻ります。

## <a name="create-the-layout"></a>レイアウトを作成する

レイアウトは、UI 要素を配置するための順序付けされた方法を提供し、UI のサイズが変更されたときの要素のサイズと位置も管理します。 通常、レイアウトを作成するには、次のいずれかのレイアウト コントロールを使用します。

- <xref:System.Windows.Controls.Canvas>-キャンバス領域に対する相対座標を使用して子要素を明示的に配置できる領域を定義します。
- <xref:System.Windows.Controls.DockPanel>-子要素を水平方向または垂直方向に整列できる領域を定義します。
- <xref:System.Windows.Controls.Grid>-列と行で構成される柔軟性のあるグリッド領域を定義します。
- <xref:System.Windows.Controls.StackPanel>-子要素を水平方向または垂直方向の単一行に整列します。
- <xref:System.Windows.Controls.VirtualizingStackPanel>-水平方向または垂直方向の単一行でコンテンツを整列し、仮想化します。
- <xref:System.Windows.Controls.WrapPanel>-左から右へ順番に子要素を配置し、格納ボックスの端の次の行にコンテンツを分割します。 後続の順序付けは、Orientation プロパティの値に応じて、上から下または右から左に順番に行われます。

これらの各レイアウトコントロールは、その子要素に対して特定の種類のレイアウトをサポートしています。 `ExpenseIt`ページのサイズを変更できます。また、各ページには、水平方向および垂直方向に他の要素と共に配置された要素があります。 この例<xref:System.Windows.Controls.Grid>では、アプリケーションのレイアウト要素としてが使用されています。

> [!TIP]
> <xref:System.Windows.Controls.Panel>要素の詳細については、「[パネルの概要](../controls/panels-overview.md)」を参照してください。 レイアウトの詳細については、「 [layout](../advanced/layout.md)」を参照してください。

このセクションで作成する単一列テーブル 10 ピクセルの余白を 3 行の列と行の定義を追加することによって、<xref:System.Windows.Controls.Grid>で *`ExpenseItHome.xaml`* します。

1. *`ExpenseItHome.xaml`* 、設定、<xref:System.Windows.FrameworkElement.Margin%2A>プロパティを<xref:System.Windows.Controls.Grid>「10,0,10,10」は、左、上、右、下の余白に対応する要素。

   ```xaml
   <Grid Margin="10,0,10,10">
   ```

   > [!TIP]
   > また、 **[プロパティ]** ウィンドウの **[レイアウト]** カテゴリで、**余白**の値を設定することもできます。
   >
   > ![プロパティウィンドウの余白の値](./media/properties-margin.png)

2. 次の XAML をタグの<xref:System.Windows.Controls.Grid>間に追加して、行と列の定義を作成します。

    [!code-xaml[ExpenseIt#8](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt3/ExpenseItHome.xaml#8)]

    2 <xref:System.Windows.Controls.RowDefinition.Height%2A>つの行のはに<xref:System.Windows.GridLength.Auto%2A>設定されます。つまり、行のサイズは、行のコンテンツに基づいて決定されます。 既定値<xref:System.Windows.Controls.RowDefinition.Height%2A>は<xref:System.Windows.GridUnitType.Star>サイズ変更です。これは、行の高さが使用可能な領域の重み付け比率であることを意味します。 たとえば、2つの行のそれぞれ<xref:System.Windows.Controls.RowDefinition.Height%2A>に "*" が含まれている場合、それぞれの行の高さは使用可能な領域の半分になります。

    に<xref:System.Windows.Controls.Grid>は、次の XAML が含まれています。

    [!code-xaml[ExpenseIt#9](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt3/ExpenseItHome.xaml#9)]

## <a name="add-controls"></a>コントロールの追加

このセクションでは、ホームページの UI を更新して、人の一覧を表示します。ここでは、1人のユーザーを選択して経費報告書を表示します。 コントロールとは、ユーザーがアプリケーションと対話できるようにする UI オブジェクトのことです。 詳しくは、「 [コントロール](../controls/index.md)」をご覧ください。

この UI を作成するには、次の要素を追加します *`ExpenseItHome.xaml`* :

- <xref:System.Windows.Controls.ListBox> (People の一覧の場合)。
- <xref:System.Windows.Controls.Label> (リストヘッダーの場合)。
- <xref:System.Windows.Controls.Button> (クリックすると、一覧で選択されているユーザーの経費明細書が表示されます)。

各コントロールは、 <xref:System.Windows.Controls.Grid> <xref:System.Windows.Controls.Grid.Row%2A?displayProperty=nameWithType>添付プロパティを設定することによって、の行に配置されます。 添付プロパティの詳細については、「[添付プロパティの概要](../advanced/attached-properties-overview.md)」を参照してください。

1. で *`ExpenseItHome.xaml`* 、タグの<xref:System.Windows.Controls.Grid>間に次の XAML を追加します。

   [!code-xaml[ExpenseIt#10](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt4/ExpenseItHome.xaml#10)]

   > [!TIP]
   > コントロールは、 **[ツールボックス]** ウィンドウからデザインウィンドウにドラッグして、 **[プロパティ]** ウィンドウでプロパティを設定することによって作成することもできます。

2. アプリケーションをビルドして実行します。

    次の図は、作成したコントロールを示しています。

![名前の一覧を表示している、このサンプルスクリーンショット](./media/walkthrough-my-first-wpf-desktop-application/add-application-controls.png)

## <a name="add-an-image-and-a-title"></a>イメージとタイトルを追加する

このセクションでは、ホームページの UI をイメージとページタイトルで更新します。

1. で *`ExpenseItHome.xaml`* 、230ピクセルの固定<xref:System.Windows.Controls.ColumnDefinition.Width%2A>の<xref:System.Windows.Controls.Grid.ColumnDefinitions%2A>を使用して、に別の列を追加します。

    [!code-xaml[ExpenseIt#11](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseItHome.xaml?highlight=52-55)]

2. に<xref:System.Windows.Controls.Grid.RowDefinitions%2A>次の行を追加します。合計4行になります。

    [!code-xaml[ExpenseIt#11b](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseItHome.xaml?highlight=57-62)]

3. コントロールを2番目の列に移動する<xref:System.Windows.Controls.Grid.Column%2A?displayProperty=nameWithType>には、3つのコントロール (Border、ListBox、および Button) のそれぞれで、プロパティを1に設定します。

4. 各コントロールを1行下に移動し<xref:System.Windows.Controls.Grid.Row%2A?displayProperty=nameWithType>ます。そのためには、3つのコントロール (border、ListBox、および Button) と border 要素のそれぞれの値を1ずつインクリメントします。

   3つのコントロールの XAML は、次のようになります。

    [!code-xaml[ExpenseIt#12](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#12)]

5. <xref:System.Windows.Controls.Panel.Background%2A?displayProperty=nameWithType>タグ`<Grid>`とタグ`</Grid>`の間に次の XAML を追加して、プロパティを*ウォーターマークの .png*画像ファイルに設定します。

    [!code-xaml[ExpenseIt#14](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#14)]

6. 要素の<xref:System.Windows.Controls.Border>前に、「 <xref:System.Windows.Controls.Label>経費報告書の表示」という内容のを追加します。 このラベルはページのタイトルです。

    [!code-xaml[ExpenseIt#13](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#13)]

7. アプリケーションをビルドして実行します。

次の図は、先ほど追加したものの結果を示しています。

![新しいイメージの背景とページのタイトルを示す、ページのサンプルスクリーンショット](./media/walkthrough-my-first-wpf-desktop-application/add-application-image-title.png)

## <a name="add-code-to-handle-events"></a>イベントを処理するコードを追加する

1. で *`ExpenseItHome.xaml`* <xref:System.Windows.Controls.Primitives.ButtonBase.Click> 、要素<xref:System.Windows.Controls.Button>にイベントハンドラーを追加します。 詳細については、「[方法 :単純なイベントハンドラー](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/bb675300(v=vs.100))を作成します。

    [!code-xaml[ExpenseIt#15](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt6/ExpenseItHome.xaml#15)]

2. 開いている *`ExpenseItHome.xaml.vb`* または *`ExpenseItHome.xaml.cs`* します。

3. 次のコードを`ExpenseItHome`クラスに追加して、ボタンクリックイベントハンドラーを追加します。 イベントハンドラーによって、[処理された**Sereportpage** ] ページが開きます。

    [!code-csharp[ExpenseIt#16](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt6/ExpenseItHome.xaml.cs#16)]
    [!code-vb[ExpenseIt#16](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt6/ExpenseItHome.xaml.vb#16)]

## <a name="create-the-ui-for-expensereportpage"></a>[印刷] ページの UI を作成する

*ExpenseReportPage.xaml*で選択されている個人の経費報告書が表示されます、 **`ExpenseItHome`** ページ。 このセクションでは、[の使用]**ページ**の UI を作成します。 また、さまざまな UI 要素に背景色と塗りつぶしの色を追加します。

1. *ExpenseReportPage.xaml*を開きます。

2. タグの<xref:System.Windows.Controls.Grid>間に次の XAML を追加します。

    [!code-xaml[ExpenseIt#17](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt6/ExpenseReportPage.xaml#17)]

    この UI はのような *`ExpenseItHome.xaml`* でレポート データが表示される点を除いて、<xref:System.Windows.Controls.DataGrid>します。

3. アプリケーションをビルドして実行します。

4. **[表示]** ボタンを選択します。

    経費明細書ページが表示されます。 また、[戻る] ナビゲーションボタンが有効になっていることにも注意してください。

次の図は、*ページ*に追加された UI 要素を示しています。

![このページでは、[ページの作成] で作成した UI を示しています。](./media/walkthrough-my-first-wpf-desktop-application/create-application-ui.png)

## <a name="style-controls"></a>スタイルコントロール

多くの場合、UI で同じ種類のすべての要素に対して、さまざまな要素の外観が同じになります。 UI では、[スタイル](../controls/styling-and-templating.md)を使用して、複数の要素間で外観を再利用できるようにします。 スタイルの再利用性により、XAML の作成と管理が簡単になります。 このセクションでは、これまでの手順で定義した要素ごとの属性を、スタイルに置き換えます。

1. *アプリケーション .xaml* *または app.xaml を*開きます。

2. タグの<xref:System.Windows.Application.Resources%2A?displayProperty=nameWithType>間に次の XAML を追加します。

    [!code-xaml[ExpenseIt#18](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt7/App.xaml#18)]

    この XAML は、次のスタイルを追加します。

    - `headerTextStyle`:ページタイトル<xref:System.Windows.Controls.Label>の書式を設定します。

    - `labelStyle`:コントロールの<xref:System.Windows.Controls.Label>書式を設定します。

    - `columnHeaderStyle`:の書式を<xref:System.Windows.Controls.Primitives.DataGridColumnHeader>設定する場合は。

    - `listHeaderStyle`:リストヘッダー <xref:System.Windows.Controls.Border>コントロールの書式を設定する場合は。

    - `listHeaderTextStyle`:リストヘッダー <xref:System.Windows.Controls.Label>の書式を設定します。

    - `buttonStyle`:を<xref:System.Windows.Controls.Button> に`ExpenseItHome.xaml`設定します。

    スタイルは、 <xref:System.Windows.Application.Resources%2A?displayProperty=nameWithType>プロパティ要素のリソースと子であることに注意してください。 ここでは、スタイルはアプリケーション内のすべての要素に適用されます。 .NET アプリでのリソースの使用例については、「[アプリケーションリソースの使用](../advanced/how-to-use-application-resources.md)」を参照してください。

3. で *`ExpenseItHome.xaml`* は<xref:System.Windows.Controls.Grid> 、要素間のすべてを次の XAML に置き換えます。

    [!code-xaml[ExpenseIt#19](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt7/ExpenseItHome.xaml#19)]

    各コントロールの外観を定義する <xref:System.Windows.VerticalAlignment> や <xref:System.Windows.Media.FontFamily> などのプロパティは、これらのスタイルを適用することで、削除されて置き換えられます。 たとえば`headerTextStyle` 、は "経費報告書の表示" <xref:System.Windows.Controls.Label>に適用されます。

4. *ExpenseReportPage.xaml*を開きます。

5. <xref:System.Windows.Controls.Grid>要素間のすべてを次の XAML に置き換えます。

    [!code-xaml[ExpenseIt#20](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt7/ExpenseReportPage.xaml#20)]

    この XAML は<xref:System.Windows.Controls.Label> 、要素と<xref:System.Windows.Controls.Border>要素にスタイルを追加します。

6. アプリケーションをビルドして実行します。 ウィンドウの外観は、以前と同じです。

    ![前回のセクションと同じ外観の、このサンプルスクリーンショット。](./media/walkthrough-my-first-wpf-desktop-application/create-application-ui.png)

7. アプリケーションを閉じて、Visual Studio に戻ります。

## <a name="bind-data-to-a-control"></a>コントロールへのデータのバインド

このセクションでは、さまざまなコントロールにバインドされている XML データを作成します。

1. で *`ExpenseItHome.xaml`* 、開始<xref:System.Windows.Controls.Grid>要素の後に<xref:System.Windows.Data.XmlDataProvider>次の XAML を追加して、各ユーザーのデータを含むを作成します。

    [!code-xaml[ExpenseIt#23](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml?range=13,16-40,49)]

    データは<xref:System.Windows.Controls.Grid>リソースとして作成されます。 通常、このデータはファイルとして読み込まれますが、わかりやすくするために、データはインラインで追加されます。

2. 要素内に次`<xref:System.Windows.DataTemplate>`の要素を追加します。この要素は、要素の`<XmlDataProvider>`後<xref:System.Windows.Controls.ListBox>に、のデータを表示する方法を定義します。 `<Grid.Resources>`

    [!code-xaml[ExpenseIt#24](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml?range=13,43-46,49)]

    データテンプレートの詳細については、「データテンプレートの[概要](../data/data-templating-overview.md)」を参照してください。

3. 既存<xref:System.Windows.Controls.ListBox>のを次の XAML に置き換えます。

    [!code-xaml[ExpenseIt#25](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#25)]

    この XAML は、 <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> <xref:System.Windows.Controls.ListBox>のプロパティをデータソースにバインドし、データテンプレート<xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A>をとして適用します。

## <a name="connect-data-to-controls"></a>コントロールへのデータの接続

次で選択されている名前を取得するコードを追加します、 **`ExpenseItHome`** ページし、のコンストラクターに渡す**ExpenseReportPage**します。 [調整された**Sereportpage** ] は、渡された項目を使用してそのデータコンテキストを設定します。これは、"*ページ*のバインド先" に定義されているコントロールです。

1. *ExpenseReportPage.xaml.vb* または *ExpenseReportPage.xaml.cs*を開きます。

2. オブジェクトを取得するコンストラクターを追加して、選択した個人の経費報告書データを渡せるようにします。

    [!code-csharp[ExpenseIt#26](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseReportPage.xaml.cs#26)]
    [!code-vb[ExpenseIt#26](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt8/ExpenseReportPage.xaml.vb#26)]

3. 開いている *`ExpenseItHome.xaml.vb`* または *`ExpenseItHome.xaml.cs`* します。

4. 選択し<xref:System.Windows.Controls.Primitives.ButtonBase.Click>たユーザーの経費報告書データを渡す新しいコンストラクターを呼び出すように、イベントハンドラーを変更します。

    [!code-csharp[ExpenseIt#27](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml.cs#27)]
    [!code-vb[ExpenseIt#27](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt8/ExpenseItHome.xaml.vb#27)]

## <a name="style-data-with-data-templates"></a>データテンプレートを使用したデータのスタイル

このセクションでは、データテンプレートを使用して、データバインドリストの各項目の UI を更新します。

1. *ExpenseReportPage.xaml*を開きます。

2. "Name" 要素と "Department" <xref:System.Windows.Controls.Label>要素の内容を適切なデータソースプロパティにバインドします。 データバインディングの詳細については、「[データバインディングの概要](../data/data-binding-overview.md)」を参照してください。

    [!code-xaml[ExpenseIt#31](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseReportPage.xaml#31)]

3. 開い<xref:System.Windows.Controls.Grid>ている要素の後に、経費報告書データの表示方法を定義する次のデータテンプレートを追加します。

    [!code-xaml[ExpenseIt#30](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseReportPage.xaml#30)]

4. 要素のをに<xref:System.Windows.Controls.DataGridTemplateColumn> <xref:System.Windows.Controls.DataGrid>置き換え、テンプレートを適用します。 <xref:System.Windows.Controls.DataGridTextColumn>

    [!code-xaml[ExpenseIt#32](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseReportPage.xaml#32)]

5. アプリケーションをビルドして実行します。

6. ユーザーを選択し、 **[表示]** ボタンを選択します。

次の図は、適用され`ExpenseIt`たコントロール、レイアウト、スタイル、データバインディング、およびデータテンプレートを使用したアプリケーションの両方のページを示しています。

![名前の一覧と経費報告書を表示するアプリの両方のページ。](./media/walkthrough-my-first-wpf-desktop-application/application-data-templates.png)

> [!NOTE]
> このサンプルでは、WPF の特定の機能について説明します。セキュリティ、ローカライズ、アクセシビリティなどのベストプラクティスについては説明しません。 WPF と .NET アプリ開発のベストプラクティスの包括的な説明については、次のトピックを参照してください。
>
> - [ユーザー補助](../../ui-automation/accessibility-best-practices.md)
>
> - [セキュリティ](../security-wpf.md)
>
> - [WPF のグローバリゼーションおよびローカリゼーションの概要](../advanced/wpf-globalization-and-localization-overview.md)
>
> - [WPF のパフォーマンス](../advanced/optimizing-wpf-application-performance.md)

## <a name="next-steps"></a>次の手順

このチュートリアルでは、Windows Presentation Foundation (WPF) を使用して UI を作成するためのいくつかの手法について学習しました。 これで、データバインドされた .NET アプリの構成要素についての基本的な理解ができました。 WPF のアーキテクチャおよびプログラミング モデルの詳細については、次のトピックを参照してください。

- [WPF のアーキテクチャ](../advanced/wpf-architecture.md)
- [XAML の概要 (WPF)](../advanced/xaml-overview-wpf.md)
- [依存関係プロパティの概要](../advanced/dependency-properties-overview.md)
- [レイアウト](../advanced/layout.md)

アプリケーションの作成の詳細については、次のトピックを参照してください。

- [アプリケーション開発](../app-development/index.md)
- [コントロール](../controls/index.md)
- [データバインディングの概要](../data/data-binding-overview.md)
- [グラフィックスとマルチメディア](../graphics-multimedia/index.md)
- [WPF のドキュメント](../advanced/documents-in-wpf.md)

## <a name="see-also"></a>関連項目

- [パネルの概要](../controls/panels-overview.md)
- [データテンプレートの概要](../data/data-templating-overview.md)
- [WPF アプリケーションのビルド](../app-development/building-a-wpf-application-wpf.md)
- [スタイルとテンプレート](../controls/styles-and-templates.md)
