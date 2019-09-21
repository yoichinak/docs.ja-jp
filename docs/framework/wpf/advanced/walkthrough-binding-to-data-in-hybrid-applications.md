---
title: 'チュートリアル: ハイブリッド アプリケーションでのデータへのバインディング'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hybrid applications [WPF interoperability]
- data binding [WPF interoperability]
ms.assetid: 18997e71-745a-4425-9c69-2cbce1d8669e
ms.openlocfilehash: ef5f14cdbecab8bc780cb7b2a642429970a25316
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/13/2019
ms.locfileid: "68972275"
---
# <a name="walkthrough-binding-to-data-in-hybrid-applications"></a>チュートリアル: ハイブリッド アプリケーションでのデータへのバインディング

データソースをコントロールにバインドすることは、ユーザーがまたは[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]を使用しているかどうかにかかわらず、基になるデータにアクセスできるようにするために不可欠です。 このチュートリアルでは、との両方[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]のコントロールを含むハイブリッドアプリケーションでデータバインディングを使用する方法について[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]説明します。

このチュートリアルでは、以下のタスクを行います。

- プロジェクトの作成。

- データテンプレートを定義しています。

- フォームレイアウトを指定します。

- データバインディングを指定します。

- 相互運用を使用してデータを表示する。

- プロジェクトにデータソースを追加しています。

- データソースにバインドしています。

このチュートリアルで示すタスクの完全なコード一覧については、「[ハイブリッドアプリケーションでのデータバインディングのサンプル](https://go.microsoft.com/fwlink/?LinkID=159983)」を参照してください。

完了すると、ハイブリッドアプリケーションのデータバインディング機能について理解できるようになります。

## <a name="prerequisites"></a>必須コンポーネント

このチュートリアルを実行するには、次のコンポーネントが必要です。

- Visual Studio

- Microsoft SQL Server で実行されている Northwind サンプルデータベースへのアクセス。

## <a name="creating-the-project"></a>プロジェクトの作成

### <a name="to-create-and-set-up-the-project"></a>プロジェクトを作成し、設定するには

1. という名前`WPFWithWFAndDatabinding`の WPF アプリケーションプロジェクトを作成します。

2. ソリューション エクスプローラーで、次のアセンブリへの参照を追加します。

    - WindowsFormsIntegration

    - System.Windows.Forms

3. で Mainwindow.xaml を開き[!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)]ます。

4. 要素に、次[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]の名前空間マッピングを追加します。 <xref:System.Windows.Window>

    ```xaml
    xmlns:wf="clr-namespace:System.Windows.Forms;assembly=System.Windows.Forms"
    ```

5. プロパティを<xref:System.Windows.Controls.Grid> `mainGrid` 割り当てることによって、既定の要素に名前を<xref:System.Windows.FrameworkElement.Name%2A>指定します。

     [!code-xaml[WPFWithWFAndDatabinding#8](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml#8)]

## <a name="defining-the-data-template"></a>データテンプレートの定義

顧客のマスターリストが<xref:System.Windows.Controls.ListBox>コントロールに表示されます。 次のコード例では<xref:System.Windows.DataTemplate> 、 <xref:System.Windows.Controls.ListBox>コントロール`ListItemsTemplate`のビジュアルツリーを制御するという名前のオブジェクトを定義します。 これ<xref:System.Windows.DataTemplate>は、 <xref:System.Windows.Controls.ListBox>コントロールの<xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A>プロパティに割り当てられます。

### <a name="to-define-the-data-template"></a>データテンプレートを定義するには

- 次の XAML を<xref:System.Windows.Controls.Grid>要素の宣言にコピーします。

     [!code-xaml[WPFWithWFAndDatabinding#3](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml#3)]

## <a name="specifying-the-form-layout"></a>フォームレイアウトの指定

フォームのレイアウトは、3つの行と3つの列を持つグリッドによって定義されます。 <xref:System.Windows.Controls.Label>Customers テーブルの各列を識別するためのコントロールが用意されています。

### <a name="to-set-up-the-grid-layout"></a>グリッドレイアウトを設定するには

- 次の XAML を<xref:System.Windows.Controls.Grid>要素の宣言にコピーします。

     [!code-xaml[WPFWithWFAndDatabinding#4](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml#4)]

### <a name="to-set-up-the-label-controls"></a>ラベルコントロールを設定するには

- 次の XAML を<xref:System.Windows.Controls.Grid>要素の宣言にコピーします。

     [!code-xaml[WPFWithWFAndDatabinding#5](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml#5)]

## <a name="specifying-data-bindings"></a>データバインディングの指定

顧客のマスターリストが<xref:System.Windows.Controls.ListBox>コントロールに表示されます。 アタッチさ`ListItemsTemplate`れた<xref:System.Windows.Controls.TextBlock>は、データベース`ContactName`のフィールドにコントロールをバインドします。

各顧客レコードの詳細が、いくつか<xref:System.Windows.Controls.TextBox>のコントロールに表示されます。

### <a name="to-specify-data-bindings"></a>データバインディングを指定するには

- 次の XAML を<xref:System.Windows.Controls.Grid>要素の宣言にコピーします。

     クラス<xref:System.Windows.Data.Binding>は、 <xref:System.Windows.Controls.TextBox>コントロールをデータベース内の適切なフィールドにバインドします。

     [!code-xaml[WPFWithWFAndDatabinding#6](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml#6)]

## <a name="displaying-data-by-using-interoperation"></a>相互運用を使用したデータの表示

選択した顧客に対応する注文が、と<xref:System.Windows.Forms.DataGridView?displayProperty=nameWithType>いう名前`dataGridView1`のコントロールに表示されます。 `dataGridView1`コントロールは、分離コードファイル内のデータソースにバインドされます。 コントロールは、この[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]コントロールの親です。 <xref:System.Windows.Forms.Integration.WindowsFormsHost>

### <a name="to-display-data-in-the-datagridview-control"></a>DataGridView コントロールにデータを表示するには

- 次の XAML を<xref:System.Windows.Controls.Grid>要素の宣言にコピーします。

     [!code-xaml[WPFWithWFAndDatabinding#7](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml#7)]

## <a name="adding-the-data-source-to-the-project"></a>プロジェクトへのデータソースの追加

Visual Studio を使用すると、データソースを簡単にプロジェクトに追加できます。 この手順では、厳密に型指定されたデータセットをプロジェクトに追加します。 選択した各テーブルのテーブルアダプターなど、他のいくつかのサポートクラスも追加されています。

### <a name="to-add-the-data-source"></a>データ ソースを追加するには

1. **[データ]** メニューの **[新しいデータソースの追加]** をクリックします。

2. **データソース構成ウィザード**で、データセットを使用して Northwind データベースへの接続を作成します。 詳細については、「[方法 :データベース](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/fxk9yw1t(v=vs.120))内のデータに接続します。

3. **データソース構成ウィザード**によってメッセージが表示されたら、接続文字列`NorthwindConnectionString`をとして保存します。

4. データベースオブジェクトの選択を求めるメッセージが表示されたら`Customers` 、 `Orders`テーブルおよびテーブルを選択し、生成`NorthwindDataSet`されたデータセットに名前を指定します。

## <a name="binding-to-the-data-source"></a>データソースへのバインド

コンポーネント<xref:System.Windows.Forms.BindingSource?displayProperty=nameWithType>は、アプリケーションのデータソースに対して統一されたインターフェイスを提供します。 データソースへのバインドは、分離コードファイルに実装されています。

### <a name="to-bind-to-the-data-source"></a>データソースにバインドするには

1. Mainwindow.xaml または MainWindow.xaml.cs という名前の分離コードファイルを開きます。

2. 次のコードを`MainWindow`クラス定義にコピーします。

     このコードは、 <xref:System.Windows.Forms.BindingSource>データベースに接続するコンポーネントと関連付けられたヘルパークラスを宣言します。

     [!code-csharp[WPFWithWFAndDatabinding#11](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml.cs#11)]
     [!code-vb[WPFWithWFAndDatabinding#11](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFWithWFAndDatabinding/VisualBasic/WPFWithWFAndDatabinding/Window1.xaml.vb#11)]

3. 次のコードをコンストラクターにコピーします。

     このコードでは、コンポーネント<xref:System.Windows.Forms.BindingSource>を作成して初期化します。

     [!code-csharp[WPFWithWFAndDatabinding#12](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml.cs#12)]
     [!code-vb[WPFWithWFAndDatabinding#12](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFWithWFAndDatabinding/VisualBasic/WPFWithWFAndDatabinding/Window1.xaml.vb#12)]

4. MainWindow.xaml を開きます。

5. デザインビューまたは XAML ビューで、 <xref:System.Windows.Window>要素を選択します。

6. プロパティウィンドウで、 **[イベント]** タブをクリックします。

7. イベントを<xref:System.Windows.FrameworkElement.Loaded>ダブルクリックします。

8. <xref:System.Windows.FrameworkElement.Loaded>イベントハンドラーに次のコードをコピーします。

     このコードは、 <xref:System.Windows.Forms.BindingSource>コンポーネントをデータコンテキスト`Customers`として割り当て、 `Orders`およびアダプターオブジェクトを設定します。

     [!code-csharp[WPFWithWFAndDatabinding#13](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml.cs#13)]
     [!code-vb[WPFWithWFAndDatabinding#13](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFWithWFAndDatabinding/VisualBasic/WPFWithWFAndDatabinding/Window1.xaml.vb#13)]

9. 次のコードを`MainWindow`クラス定義にコピーします。

     このメソッドは、 <xref:System.Windows.Data.CollectionView.CurrentChanged>イベントを処理し、データバインディングの現在の項目を更新します。

     [!code-csharp[WPFWithWFAndDatabinding#14](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml.cs#14)]
     [!code-vb[WPFWithWFAndDatabinding#14](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFWithWFAndDatabinding/VisualBasic/WPFWithWFAndDatabinding/Window1.xaml.vb#14)]

10. F5 キーを押してアプリケーションをビルドし、実行します。

## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [Visual Studio で XAML をデザインする](/visualstudio/designers/designing-xaml-in-visual-studio)
- [ハイブリッドアプリケーションでのデータバインディングのサンプル](https://go.microsoft.com/fwlink/?LinkID=159983)
- [チュートリアル: WPF での Windows フォーム複合コントロールのホスト](walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)
- [チュートリアル: Windows フォームでの WPF 複合コントロールのホスト](walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
