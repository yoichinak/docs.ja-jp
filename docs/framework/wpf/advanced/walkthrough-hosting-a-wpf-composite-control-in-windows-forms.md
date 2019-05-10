---
title: 'チュートリアル: Windows フォームでの WPF 複合コントロールのホスト'
ms.date: 03/30/2017
helpviewer_keywords:
- hosting WPF content in Windows Forms [WPF]
ms.assetid: 0ac41286-4c1b-4b17-9196-d985cb844ce1
ms.openlocfilehash: 24eaccb1aad7f9d592cbc4c92d960b7dcea0c5ee
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2019
ms.locfileid: "64605450"
---
# <a name="walkthrough-hosting-a-wpf-composite-control-in-windows-forms"></a>チュートリアル: Windows フォームでの WPF 複合コントロールのホスト
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] は、アプリケーションの作成に適した環境を提供します。 ただしがある場合、かなりの投資[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]コード、ことができます、既存の拡張をより効果的な[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]アプリケーションを[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]ではなく最初から修正します。 一般的なシナリオで実装したコントロールを 1 つを埋め込む、または場合に、 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Windows フォーム アプリケーション内で。 WPF コントロールをカスタマイズする方法の詳細については、次を参照してください。[コントロールのカスタマイズ](../controls/control-customization.md)します。  
  
 このチュートリアル手順について説明するアプリケーションをホストする、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]複合コントロールを Windows フォーム アプリケーションでデータ入力を実行します。 複合コントロールは DLL にパッケージ化されています。 この一般的な手順は、より複雑なアプリケーションやコントロールに拡張することができます。 このチュートリアルの外観と機能をほぼ同じにする目的は[チュートリアル。WPF で複合コントロールをフォーム、Windows をホストしている](walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)します。 主な違いは、ホストする側とされる側が逆であることです。  
  
 このチュートリアルは、2 つのセクションに分かれています。 最初のセクションでは、実装について簡単に説明します、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]複合コントロール。 2 番目のセクションは、Windows フォーム アプリケーションで複合コントロールをホスト、コントロールからイベントを受信して、コントロールのプロパティの一部にアクセスする方法の詳細について説明します。  
  
 このチュートリアルでは、以下のタスクを行います。  
  
- WPF 複合コントロールを実装する。  
  
- Windows フォーム ホスト アプリケーションを実装する。  
  
 このチュートリアルで示すタスクの完全なコード一覧については、次を参照してください。 [Windows フォームのサンプルでの WPF 複合コントロールをホストしている](https://go.microsoft.com/fwlink/?LinkID=159996)します。  
  
## <a name="prerequisites"></a>必須コンポーネント  

このチュートリアルを完了するには Visual Studio が必要です。  
  
## <a name="implementing-the-wpf-composite-control"></a>WPF 複合コントロールの実装  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]この例で使用される複合コントロールは、ユーザーの名前とアドレスを受け取る単純なデータ入力フォームです。 ユーザーが 2 つのボタンのいずれかをクリックして入力操作が終了したことを示すと、コントロールはカスタム イベントを発生させて入力情報をホストに返します。 次の図はレンダリングされたコントロールを示しています。 

 次の図は、WPF 複合コントロールを示しています。 

 ![単純な WPF コントロールを示すスクリーン ショット。](./media/walkthrough-hosting-a-wpf-composite-control-in-windows-forms/windows-presentation-foundation-composite-control.png)  
  
### <a name="creating-the-project"></a>プロジェクトの作成  
 プロジェクトを開始するには  
  
1. 起動[!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)]を開き、**新しいプロジェクト** ダイアログ ボックス。  
  
2. Visual c# および Windows のカテゴリを選択して、 **WPF ユーザー コントロール ライブラリ**テンプレート。  
  
3. 新しいプロジェクトに `MyControls` という名前を付けます。  
  
4. など指定便利な名前付きの最上位フォルダーの場所`WindowsFormsHostingWpfControl`します。 このフォルダーには後でホスト アプリケーションも配置します。  
  
5. **[OK]** をクリックして、プロジェクトを作成します。 既定のプロジェクトには、という名前の 1 つのコントロールが含まれています。`UserControl1`します。  
  
6. ソリューション エクスプローラで、名前を変更`UserControl1`に`MyControl1`します。  
  
 プロジェクトは、以下のシステム DLL を参照している必要があります。 これらの DLL のいずれかが既定で含まれていない場合は、プロジェクトに追加します。  
  
- PresentationCore  
  
- PresentationFramework  
  
- システム  
  
- WindowsBase  
  
### <a name="creating-the-user-interface"></a>ユーザー インターフェイスの作成  
 [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]で複合コントロールが実装済み[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]します。 複合コントロール[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]5 から成る<xref:System.Windows.Controls.TextBox>要素。 各<xref:System.Windows.Controls.TextBox>要素に関連付けられている<xref:System.Windows.Controls.TextBlock>ラベルとして機能する要素。 2 つ<xref:System.Windows.Controls.Button>下部にある要素**OK**と**キャンセル**。 ユーザーがいずれかのボタンをクリックすると、コントロールは情報をホストに返すカスタム イベントを発生させます。  
  
#### <a name="basic-layout"></a>基本的なレイアウト  
 さまざまな[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]要素が含まれている、<xref:System.Windows.Controls.Grid>要素。 使用することができます<xref:System.Windows.Controls.Grid>複合の内容が同じでコントロールを配置する方法が使用する、 `Table` HTML 内の要素。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Documents.Table>要素が<xref:System.Windows.Controls.Grid>より軽量で単純なレイアウト タスクに適してします。  
  
 次の XAML に基本的なレイアウトを示します。 この XAML は、列の数を指定して、コントロールの全体的な構造を定義し、内の行、<xref:System.Windows.Controls.Grid>要素。  
  
 MyControl1.xaml で、で、既存の XAML を次の XAML で置き換えます。  
  
 [!code-xaml[WindowsFormsHostingWpfControl#101](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml#101)]  
[!code-xaml[WindowsFormsHostingWpfControl#102](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml#102)]  
  
#### <a name="adding-textblock-and-textbox-elements-to-the-grid"></a>TextBlock および TextBox 要素のグリッドへの追加  
 配置する、[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]の要素の設定グリッド内の要素<xref:System.Windows.Controls.Grid.RowProperty>と<xref:System.Windows.Controls.Grid.ColumnProperty>属性を適切な行と列の数。 行と列の番号付けは 0 から始まることに注意してください。 要素を設定して複数の列にまたがって表示することがその<xref:System.Windows.Controls.Grid.ColumnSpanProperty>属性。 詳細については<xref:System.Windows.Controls.Grid>、要素を参照してください[グリッド要素を作成](../controls/how-to-create-a-grid-element.md)です。  
  
 次の XAML は、複合コントロールを示しています<xref:System.Windows.Controls.TextBox>と<xref:System.Windows.Controls.TextBlock>を持つ要素が<xref:System.Windows.Controls.Grid.RowProperty>と<xref:System.Windows.Controls.Grid.ColumnProperty>属性で、グリッドに要素を正しく配置に設定されます。  
  
 MyControl1.xaml で内で次の XAML を追加、<xref:System.Windows.Controls.Grid>要素。  
  
 [!code-xaml[WindowsFormsHostingWpfControl#103](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml#103)]  
  
#### <a name="styling-the-ui-elements"></a>UI 要素のスタイル設定  
 データ入力フォームの多くの要素は外観が似ていますが、それは、そのいくつかのプロパティの設定が同一であることを意味しています。 前の XAML を使用して各要素の属性を個別に設定するのではなく<xref:System.Windows.Style>要素のクラスの標準プロパティ設定を定義する要素。 この方法だと、コントロールの複雑さが軽減され、1 つのスタイル属性を使用して複数要素の外観を変更することができます。  
  
 <xref:System.Windows.Style>要素が含まれている、<xref:System.Windows.Controls.Grid>要素の<xref:System.Windows.FrameworkElement.Resources%2A>プロパティ、コントロール内のすべての要素が使用できるようにします。 スタイルがという名前の場合に適用する要素を追加して、<xref:System.Windows.Style>要素スタイルの名前に設定します。 名前が付いていないスタイルは、その要素の既定のスタイルになります。 詳細については[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]スタイルを参照してください[スタイルとテンプレート](../controls/styling-and-templating.md)します。  
  
 次の XAML に示す、<xref:System.Windows.Style>複合コントロールの要素。 スタイルがどのように要素に適用されるかについては、前の XAML を参照してください。 最後の例では、<xref:System.Windows.Controls.TextBlock>要素には、`inlineText`スタイル、および最後<xref:System.Windows.Controls.TextBox>要素は、既定のスタイルを使用します。  
  
 MyControl1.xaml で、次の XAML を追加した後、<xref:System.Windows.Controls.Grid>開始要素。  
  
 [!code-xaml[WindowsFormsHostingWpfControl#104](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml#104)]  
  
#### <a name="adding-the-ok-and-cancel-buttons"></a>[OK] ボタンと [キャンセル] ボタンの追加  
 複合コントロールの最後の要素が、 **OK**と**キャンセル**<xref:System.Windows.Controls.Button>の最後の行の最初の 2 つの列を占有の要素、 <xref:System.Windows.Controls.Grid>。 これらの要素が共通のイベント ハンドラーを使用して`ButtonClicked`と既定の<xref:System.Windows.Controls.Button>前の XAML で定義されたスタイル。  
  
 MyControl1.xaml で、最後の後に次の XAML を追加<xref:System.Windows.Controls.TextBox>要素。 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]複合コントロールの一部が完成しました。  
  
 [!code-xaml[WindowsFormsHostingWpfControl#105](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml#105)]  
  
### <a name="implementing-the-code-behind-file"></a>分離コード ファイルの実装  
 分離コード ファイル MyControl1.xaml.cs は、次の 3 つの基本的なタスクを実装します。
  
1. ユーザーがいずれかのボタンをクリックしたときに発生するイベントを処理します。  
  
2. データを取得、<xref:System.Windows.Controls.TextBox>要素、それをカスタム イベント引数オブジェクトにパッケージとします。  
  
3. カスタムを発生させます。`OnButtonClick`と、ユーザーが完成したデータをホストに渡すことをホストに通知するイベントです。  
  
 コントロールは、外観を変更するための色とフォントの多くのプロパティも公開します。 異なり、<xref:System.Windows.Forms.Integration.WindowsFormsHost>クラス、Windows フォーム コントロールをホストするために使用、<xref:System.Windows.Forms.Integration.ElementHost>クラスは、コントロールの公開<xref:System.Windows.Controls.Panel.Background%2A>プロパティのみです。 このコード例で説明した例の間の類似性を維持するために[チュートリアル。WPF で Windows フォーム複合コントロールをホストしている](walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)コントロールが、残りのプロパティを直接公開します。  
  
#### <a name="the-basic-structure-of-the-code-behind-file"></a>分離コード ファイルの基本構造  
 分離コード ファイルには、単一の名前空間の`MyControls`、2 つのクラスを含む`MyControl1`と`MyControlEventArgs`します。  
  
```  
namespace MyControls  
{  
  public partial class MyControl1 : Grid  
  {  
    //...  
  }  
  public class MyControlEventArgs : EventArgs  
  {  
    //...  
  }  
}  
```  
  
 最初のクラスで`MyControl1`の機能を実装するコードを格納する部分クラスには、 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] MyControl1.xaml で定義されています。 MyControl1.xaml が解析される際、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]同じ部分クラスに変換され、コンパイル済みのコントロールをフォームに 2 つの部分クラスがマージされます。 このため、分離コード ファイル内のクラス名は MyControl1.xaml に割り当てられたクラス名と一致する必要があり、コントロールのルート要素から継承する必要があります。 2 番目のクラス、`MyControlEventArgs`データをホストに送信するために使用されるイベント引数クラスです。  
  
 MyControl1.xaml.cs を開きます。 既存のクラス宣言を変更してから継承し、次の名前を持つように<xref:System.Windows.Controls.Grid>します。  
  
 [!code-csharp[WindowsFormsHostingWpfControl#21](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml.cs#21)]  
  
#### <a name="initializing-the-control"></a>コントロールの初期化  
 このコードでは、次の基本タスクを実装します。  
  
- プライベートのイベントを宣言`OnButtonClick`、および関連するデリゲート、`MyControlEventHandler`します。  
  
- ユーザーのデータを格納するいくつかのプライベート グローバル変数を作成します。 このデータは、対応するプロパティを通じて公開されます。  
  
- ハンドラーを実装する`Init`、コントロールの<xref:System.Windows.FrameworkElement.Loaded>イベント。 このハンドラーは、MyControl1.xaml で定義された値をグローバル変数に割り当てることで、グローバル変数を初期化します。 これを行うには、使用して、 <xref:System.Windows.FrameworkElement.Name%2A> 、標準的な割り当て<xref:System.Windows.Controls.TextBlock>要素、 `nameLabel`、その要素のプロパティの設定にアクセスします。  
  
 既存のコンス トラクターを削除し、次のコードを追加、`MyControl1`クラス。  
  
 [!code-csharp[WindowsFormsHostingWpfControl#11](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml.cs#11)]  
  
#### <a name="handling-the-buttons-click-events"></a>ボタンのクリック イベントの処理  
 ユーザーは、いずれかをクリックして、データ入力タスクが完了したことを示します、 **OK**ボタンまたは**キャンセル**ボタン。 両方のボタンを使用して同じ<xref:System.Windows.Controls.Primitives.ButtonBase.Click>イベント ハンドラー、`ButtonClicked`します。 両方のボタンの名前を付ける`btnOK`または`btnCancel`の値を調べることでクリックしてされたボタンを判断するハンドラーをできるようにする、`sender`引数。 ハンドラーは次の処理を行います。  
  
- 作成、`MyControlEventArgs`からデータを格納しているオブジェクト、<xref:System.Windows.Controls.TextBox>要素。  
  
- ユーザーがクリックした場合、**キャンセル**ボタン、セット、`MyControlEventArgs`オブジェクトの`IsOK`プロパティを`false`します。  
  
- 発生させる、`OnButtonClick`渡しますが、収集したデータをユーザーが完了したら、ホストすることを示すイベント。  
  
 次のコードを追加、`MyControl1`した後、クラス、`Init`メソッド。  
  
 [!code-csharp[WindowsFormsHostingWpfControl#12](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml.cs#12)]  
  
#### <a name="creating-properties"></a>プロパティの作成  
 クラスの残りの部分では単に、前に説明したグローバル変数に対応するプロパティを公開します。 プロパティが変更されると、set アクセサーは、対応する要素のプロパティを変更し、基になるグローバル変数を更新することによって、コントロールの外観を変更します。  
  
 次のコードを追加、`MyControl1`クラス。  
  
 [!code-csharp[WindowsFormsHostingWpfControl#13](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml.cs#13)]  
  
#### <a name="sending-the-data-back-to-the-host"></a>ホストへのデータの返送  
 ファイルの最後のコンポーネントは、`MyControlEventArgs`クラスは、ホストに、収集したデータを送信するために使用します。  
  
 次のコードを追加、`MyControls`名前空間。 この実装は簡単なので、これ以上の説明はしません。  
  
 [!code-csharp[WindowsFormsHostingWpfControl#14](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml.cs#14)]  
  
 ソリューションをビルドします。 ビルドでは、MyControls.dll という名前の DLL が生成されます。  
  
<a name="winforms_host_section"></a>   
## <a name="implementing-the-windows-forms-host-application"></a>Windows フォーム ホスト アプリケーションの実装  
 Windows フォーム ホスト アプリケーションで使用する、<xref:System.Windows.Forms.Integration.ElementHost>ホストへのオブジェクト、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]複合コントロール。 アプリケーションのハンドル、`OnButtonClick`複合コントロールからデータを受信するイベントです。 アプリケーションにはオプションのボタンのセットもあり、それを使用してコントロールの外観を変更することができます。 次の図は、アプリケーションを示しています。  

次の図は、Windows フォーム アプリケーションでホストされる WPF 複合コントロールを"  

 ![Windows フォームをホストしている Avalon コントロールを表示する Scteenshot します。](./media/walkthrough-hosting-a-wpf-composite-control-in-windows-forms/windows-form-hosting-avalon-control.png)  
  
### <a name="creating-the-project"></a>プロジェクトの作成  
 プロジェクトを開始するには  
  
1. 起動[!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)]を開き、**新しいプロジェクト** ダイアログ ボックス。  
  
2. Visual c# および Windows のカテゴリを選択して、 **Windows フォーム アプリケーション**テンプレート。  
  
3. 新しいプロジェクトに `WFHost` という名前を付けます。  
  
4. 配置場所として、MyControls の配置先と同じ最上位フォルダーを指定します。  
  
5. **[OK]** をクリックして、プロジェクトを作成します。  
  
 含んでいる DLL への参照を追加する必要があります`MyControl1`およびその他のアセンブリ。  
  
1. ソリューション エクスプ ローラーでプロジェクト名を右クリックして**参照の追加**します。  
  
2. をクリックして、**参照**タブをクリックし、MyControls.dll を含むフォルダーを参照します。 このチュートリアルの場合は、MyControls\bin\Debug フォルダーです。  
  
3. MyControls.dll を選択し、クリックして**OK**します。  
  
4. 次のアセンブリへの参照を追加します。  
  
    - PresentationCore  
  
    - PresentationFramework  
  
    - System.Xaml  
  
    - WindowsBase  
  
    - WindowsFormsIntegration  
  
### <a name="implementing-the-user-interface-for-the-application"></a>アプリケーションのユーザー インターフェイスの実装  
 Windows フォーム アプリケーションの UI には、WPF 複合コントロールを操作するいくつかのコントロールが含まれています。  
  
1. Windows フォーム デザイナーで、Form1 を開きます。  
  
2. コントロールを配置するためにフォームを拡大します。  
  
3. フォームの右上隅にある追加、<xref:System.Windows.Forms.Panel?displayProperty=nameWithType>コントロールを保持するために、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]複合コントロール。  
  
4. 次の追加<xref:System.Windows.Forms.GroupBox?displayProperty=nameWithType>フォームのコントロール。  
  
    |名前|テキスト|  
    |----------|----------|  
    |groupBox1|背景色|  
    |groupBox2|前景色|  
    |groupBox3|フォント サイズ|  
    |groupBox4|フォント ファミリ|  
    |groupBox5|[スタイル]|  
    |groupBox6|フォントの太さ|  
    |groupBox7|コントロールからのデータ|  
  
5. 次の追加<xref:System.Windows.Forms.RadioButton?displayProperty=nameWithType>にコントロールを<xref:System.Windows.Forms.GroupBox?displayProperty=nameWithType>コントロール。  
  
    |GroupBox|名前|テキスト|  
    |--------------|----------|----------|  
    |groupBox1|radioBackgroundOriginal|元|  
    |groupBox1|radioBackgroundLightGreen|ライトグリーン|  
    |groupBox1|radioBackgroundLightSalmon|ライトサーモン|  
    |groupBox2|radioForegroundOriginal|元|  
    |groupBox2|radioForegroundRed|赤|  
    |groupBox2|radioForegroundYellow|黄|  
    |groupBox3|radioSizeOriginal|元|  
    |groupBox3|radioSizeTen|10|  
    |groupBox3|radioSizeTwelve|12|  
    |groupBox4|radioFamilyOriginal|元|  
    |groupBox4|radioFamilyTimes|ＭＳ Ｐゴシック|  
    |groupBox4|radioFamilyWingDings|WingDings|  
    |groupBox5|radioStyleOriginal|標準|  
    |groupBox5|radioStyleItalic|[斜体]|  
    |groupBox6|radioWeightOriginal|元|  
    |groupBox6|radioWeightBold|[太字]|  
  
6. 次の追加<xref:System.Windows.Forms.Label?displayProperty=nameWithType>最後制御<xref:System.Windows.Forms.GroupBox?displayProperty=nameWithType>します。 これらのコントロールによって返されるデータの表示、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]複合コントロール。  
  
    |GroupBox|名前|テキスト|  
    |--------------|----------|----------|  
    |groupBox7|lblName|名前:|  
    |groupBox7|lblAddress|番地:|  
    |groupBox7|lblCity|市区町村:|  
    |groupBox7|lblState|都道府県:|  
    |groupBox7|lblZip|郵便番号:|  
  
### <a name="initializing-the-form"></a>フォームの初期化  
 一般に、フォームのホスティング コードを実装する<xref:System.Windows.Forms.Form.Load>イベント ハンドラー。 次のコードは、<xref:System.Windows.Forms.Form.Load>イベント ハンドラー、ハンドラーを[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]複合コントロールの<xref:System.Windows.FrameworkElement.Loaded>イベント、および後で使用されているいくつかのグローバル変数を宣言します。  
  
 Windows フォーム デザイナーで、作成するフォームをダブルクリックして、<xref:System.Windows.Forms.Form.Load>イベント ハンドラー。 Form1.cs の上部にある次のコードを追加`using`ステートメント。  
  
 [!code-csharp[WindowsFormsHostingWpfControl#10](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/WFHost/Form1.cs#10)]  
  
 既存の内容を置き換える`Form1`クラスを次のコード。  
  
 [!code-csharp[WindowsFormsHostingWpfControl#2](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/WFHost/Form1.cs#2)]  
  
 `Form1_Load`上記のコードでメソッドをホストするための一般的な手順を示しています、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]コントロール。  
  
1. 新規作成<xref:System.Windows.Forms.Integration.ElementHost>オブジェクト。  
  
2. コントロールの設定<xref:System.Windows.Forms.Control.Dock%2A>プロパティを<xref:System.Windows.Forms.DockStyle.Fill?displayProperty=nameWithType>します。  
  
3. 追加、<xref:System.Windows.Forms.Integration.ElementHost>への制御、<xref:System.Windows.Forms.Panel>コントロールの<xref:System.Windows.Forms.Control.Controls%2A>コレクション。  
  
4. インスタンスを作成、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]コントロール。  
  
5. コントロールを割り当てることで、フォーム上の複合コントロールをホスト、<xref:System.Windows.Forms.Integration.ElementHost>コントロールの<xref:System.Windows.Forms.Integration.ElementHost.Child%2A>プロパティ。  
  
 残りの 2 つの行で、`Form1_Load`メソッドは、2 つのコントロール イベントにハンドラーをアタッチします。  
  
- `OnButtonClick` カスタム イベント、ユーザーがクリックしたときに複合コントロールによって発生するは、 **[ok]** または**キャンセル**ボタンをクリックします。 このイベントを処理してユーザーの応答を取得し、ユーザーが指定したデータをすべて収集します。  
  
- <xref:System.Windows.FrameworkElement.Loaded> 標準のイベントによって発生するは、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]コントロールが完全に読み込まれる。 ここでこのイベントを使用するのは、この例ではこのコントロールからのプロパティを使用して複数のグローバル変数を初期化する必要があるからです。 フォームの時に<xref:System.Windows.Forms.Form.Load>イベント、コントロールが完全に読み込まれていないとそれらの値に設定されています`null`します。 コントロールのまで待機する必要がある<xref:System.Windows.FrameworkElement.Loaded>これらのプロパティにアクセスする前に、イベントが発生します。  
  
 <xref:System.Windows.FrameworkElement.Loaded>イベント ハンドラーは、上記のコードに示します。 `OnButtonClick`ハンドラーは、次のセクションで説明します。  
  
### <a name="handling-onbuttonclick"></a>OnButtonClick の処理  
 `OnButtonClick`イベントは、ユーザーがクリックしたときに発生します。、 **OK**または**キャンセル**ボタンをクリックします。  
  
 イベント ハンドラーは、イベント引数を確認します。`IsOK`フィールドを、どのボタンがクリックされたかを判断します。 `lbl`*データ*変数に対応、<xref:System.Windows.Forms.Label>前に説明したコントロール。 ユーザーがクリックした場合、 **OK**ボタン、コントロールからのデータ<xref:System.Windows.Controls.TextBox>、対応するコントロールが割り当てられている<xref:System.Windows.Forms.Label>コントロール。 ユーザーがクリックした場合**キャンセル**、<xref:System.Windows.Forms.Label.Text%2A>値が既定の文字列に設定されます。  
  
 次のボタンを追加するイベント ハンドラー コードをクリックして、`Form1`クラス。  
  
 [!code-csharp[WindowsFormsHostingWpfControl#3](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/WFHost/Form1.cs#3)]  
  
 アプリケーションをビルドして実行します。 WPF 複合コントロールでテキストを追加し、クリックして**OK**します。 そのテキストがラベルに表示されます。 この時点で、オプション ボタンを処理するコードは追加されていません。  
  
### <a name="modifying-the-appearance-of-the-control"></a>コントロールの外観の変更  
 <xref:System.Windows.Forms.RadioButton>フォーム上のコントロールは、ユーザーが変更を有効になります、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]複合コントロールの前景色と背景色にもいくつかのフォント プロパティ。 背景色がによって公開されている、<xref:System.Windows.Forms.Integration.ElementHost>オブジェクト。 残りのプロパティは、コントロールのカスタム プロパティとして公開されます。  
  
 それぞれダブルクリック<xref:System.Windows.Forms.RadioButton>を作成するフォーム上のコントロール<xref:System.Windows.Forms.RadioButton.CheckedChanged>イベント ハンドラー。 置換、<xref:System.Windows.Forms.RadioButton.CheckedChanged>イベント ハンドラーを次のコード。  
  
 [!code-csharp[WindowsFormsHostingWpfControl#4](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/WFHost/Form1.cs#4)]  
  
 アプリケーションをビルドして実行します。 別のオプション ボタンをクリックして、WPF 複合コントロール上の影響を確認します。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [Visual Studio で XAML をデザインする](/visualstudio/designers/designing-xaml-in-visual-studio)
- [チュートリアル: WPF で Windows フォーム複合コントロールのホスト](walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)
- [チュートリアル: Windows フォームでの 3d WPF 複合コントロールのホスト](walkthrough-hosting-a-3-d-wpf-composite-control-in-windows-forms.md)
