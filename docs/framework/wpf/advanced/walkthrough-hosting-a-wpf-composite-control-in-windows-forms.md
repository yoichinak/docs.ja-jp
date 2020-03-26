---
title: Windows フォームで WPF 複合コントロールをホストする
titleSuffix: ''
ms.date: 03/30/2017
helpviewer_keywords:
- hosting WPF content in Windows Forms [WPF]
ms.assetid: 0ac41286-4c1b-4b17-9196-d985cb844ce1
ms.openlocfilehash: 88efab8adf36989938ba5aa887a28b41eb8820f3
ms.sourcegitcommit: e48a54ebe62e874500a7043f6ee0b77a744d55b4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/26/2020
ms.locfileid: "80291619"
---
# <a name="walkthrough-hosting-a-wpf-composite-control-in-windows-forms"></a>チュートリアル: Windows フォームでの WPF 複合コントロールのホスト
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] は、アプリケーションの作成に適した環境を提供します。 ただし、Windows フォーム コードに多大な投資を行う場合は、既存の[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]Windows フォーム アプリケーションを最初から書き直すよりも、より効果的に拡張できます。 一般的なシナリオは、Windows フォーム アプリケーション内で実装された[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]1 つ以上のコントロールを埋め込む場合です。 WPF コントロールのカスタマイズの詳細については、「[コントロールのカスタマイズ](../controls/control-customization.md)」を参照してください。  
  
 このチュートリアルでは、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]複合コントロールをホストするアプリケーションを手順を実行して、Windows フォーム アプリケーションでデータ入力を実行します。 複合コントロールは DLL にパッケージ化されています。 この一般的な手順は、より複雑なアプリケーションやコントロールに拡張することができます。 このチュートリアルは、外観と機能が[、チュートリアル: WPF での Windows フォーム複合コントロールのホスト](walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)とほとんど同じであることを想定しています。 主な違いは、ホストする側とされる側が逆であることです。  
  
 このチュートリアルは、2 つのセクションに分かれています。 最初のセクションでは、複合コントロールの実装について簡単[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]に説明します。 2 番目のセクションでは、複合コントロールを Windows フォーム アプリケーションでホストし、コントロールからイベントを受け取り、コントロールのプロパティの一部にアクセスする方法について詳しく説明します。  
  
 このチュートリアルでは、以下のタスクを行います。  
  
- WPF 複合コントロールを実装する。  
  
- Windows フォーム ホスト アプリケーションを実装する。  
  
 このチュートリアルで説明するタスクの完全なコード リストについては、「 [Windows フォームのサンプルでの WPF 複合コントロールのホスト](https://github.com/microsoft/WPF-Samples/tree/master/Migration%20and%20Interoperability/WindowsFormsHostingWpfControl)」を参照してください。  
  
## <a name="prerequisites"></a>前提条件  

このチュートリアルを完了するには Visual Studio が必要です。  
  
## <a name="implementing-the-wpf-composite-control"></a>WPF 複合コントロールの実装  
 この[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]例で使用されている複合コントロールは、ユーザーの名前とアドレスを受け取る単純なデータ入力フォームです。 ユーザーが 2 つのボタンのいずれかをクリックして入力操作が終了したことを示すと、コントロールはカスタム イベントを発生させて入力情報をホストに返します。 次の図はレンダリングされたコントロールを示しています。

 次の図は、WPF 複合コントロールを示しています。

 ![単純な WPF コントロールを示すスクリーンショット。](./media/walkthrough-hosting-a-wpf-composite-control-in-windows-forms/windows-presentation-foundation-composite-control.png)  
  
### <a name="creating-the-project"></a>プロジェクトの作成  
 プロジェクトを開始するには  
  
1. Visual Studio を起動し、[**新しいプロジェクト**] ダイアログ ボックスを開きます。  
  
2. Visual C# および Windows カテゴリで **、WPF ユーザー コントロール ライブラリ**テンプレートを選択します。  
  
3. 新しいプロジェクトに `MyControls` という名前を付けます。  
  
4. 場所の場合は、便利な名前の最上位フォルダ (など`WindowsFormsHostingWpfControl`) を指定します。 このフォルダーには後でホスト アプリケーションも配置します。  
  
5. **[OK]** をクリックして、プロジェクトを作成します。 既定のプロジェクトには、 という名前`UserControl1`のコントロールが 1 つ含まれています。  
  
6. ソリューション エクスプローラで、 `UserControl1` `MyControl1`に名前を変更します。  
  
 プロジェクトは、以下のシステム DLL を参照している必要があります。 これらの DLL のいずれかが既定で含まれていない場合は、プロジェクトに追加します。  
  
- PresentationCore  
  
- PresentationFramework  
  
- システム  
  
- WindowsBase  
  
### <a name="creating-the-user-interface"></a>ユーザー インターフェイスの作成  
 複合[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]コントロールの は、 で[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]実装されます。 複合コントロール[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]は、5<xref:System.Windows.Controls.TextBox>つの要素で構成されます。 各<xref:System.Windows.Controls.TextBox>要素には、ラベル<xref:System.Windows.Controls.TextBlock>として機能する関連付けられた要素があります。 下部には<xref:System.Windows.Controls.Button>**、[OK]** と [**キャンセル]** の 2 つの要素があります。 ユーザーがいずれかのボタンをクリックすると、コントロールは情報をホストに返すカスタム イベントを発生させます。  
  
#### <a name="basic-layout"></a>基本的なレイアウト  
 要素には[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]、さまざまな要素が<xref:System.Windows.Controls.Grid>含まれています。 HTML で<xref:System.Windows.Controls.Grid>要素を使用する場合とほぼ同じ方法で複合コントロールの内容を`Table`配置するために使用できます。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]また、要素<xref:System.Windows.Documents.Table>を持っています<xref:System.Windows.Controls.Grid>が、より軽量で、単純なレイアウトタスクに適しています。  
  
 次の XAML に基本的なレイアウトを示します。 この XAML では、要素の列数と行数を指定することによって、コントロールの全体的<xref:System.Windows.Controls.Grid>な構造を定義します。  
  
 MyControl1.xaml で、で、既存の XAML を次の XAML で置き換えます。  
  
 [!code-xaml[WindowsFormsHostingWpfControl#101](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml#101)]  
[!code-xaml[WindowsFormsHostingWpfControl#102](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml#102)]  
  
#### <a name="adding-textblock-and-textbox-elements-to-the-grid"></a>TextBlock および TextBox 要素のグリッドへの追加  
 要素と[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]属性を適切な行<xref:System.Windows.Controls.Grid.RowProperty>番号と列番号に設定して<xref:System.Windows.Controls.Grid.ColumnProperty>、グリッドに要素を配置します。 行と列の番号付けは 0 から始まることに注意してください。 属性を設定することで、要素を複数の列に<xref:System.Windows.Controls.Grid.ColumnSpanProperty>またがることができます。 要素の詳細<xref:System.Windows.Controls.Grid>については、「[グリッド要素の作成](../controls/how-to-create-a-grid-element.md)」を参照してください。  
  
 次の XAML は、複合コントロール<xref:System.Windows.Controls.TextBox>と<xref:System.Windows.Controls.TextBlock>、要素を<xref:System.Windows.Controls.Grid.RowProperty>グリッド<xref:System.Windows.Controls.Grid.ColumnProperty>に適切に配置するように設定された、その属性と属性を持つ要素を示しています。  
  
 MyControl1.xaml で、要素内に次の<xref:System.Windows.Controls.Grid>XAML を追加します。  
  
 [!code-xaml[WindowsFormsHostingWpfControl#103](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml#103)]  
  
#### <a name="styling-the-ui-elements"></a>UI 要素のスタイル設定  
 データ入力フォームの多くの要素は外観が似ていますが、それは、そのいくつかのプロパティの設定が同一であることを意味しています。 前の XAML では、各要素の属性を個別に<xref:System.Windows.Style>設定するのではなく、要素のクラスの標準プロパティ設定を定義するために要素を使用しています。 この方法だと、コントロールの複雑さが軽減され、1 つのスタイル属性を使用して複数要素の外観を変更することができます。  
  
 要素<xref:System.Windows.Style>は要素の<xref:System.Windows.Controls.Grid><xref:System.Windows.FrameworkElement.Resources%2A>プロパティに含まれるため、コントロール内のすべての要素で使用できます。 スタイルに名前を付ける場合は、スタイルの名前に要素セット<xref:System.Windows.Style>を追加して、そのスタイルを要素に適用します。 名前が付いていないスタイルは、その要素の既定のスタイルになります。 スタイルの詳細[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]については、「[スタイルとテンプレート](../../../desktop-wpf/fundamentals/styles-templates-overview.md)」を参照してください。  
  
 次の XAML<xref:System.Windows.Style>は、複合コントロールの要素を示しています。 スタイルがどのように要素に適用されるかについては、前の XAML を参照してください。 たとえば、最後<xref:System.Windows.Controls.TextBlock>の要素にはスタイルがあり`inlineText`、最後<xref:System.Windows.Controls.TextBox>の要素は既定のスタイルを使用します。  
  
 MyControl1.xaml で、開始要素の直後に次<xref:System.Windows.Controls.Grid>の XAML を追加します。  
  
 [!code-xaml[WindowsFormsHostingWpfControl#104](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml#104)]  
  
#### <a name="adding-the-ok-and-cancel-buttons"></a>[OK] ボタンと [キャンセル] ボタンの追加  
 複合コントロールの最後の要素は **、OK**要素と**Cancel**<xref:System.Windows.Controls.Button>要素で、この要素の最後の行の最初<xref:System.Windows.Controls.Grid>の 2 つの列を占めます。 これらの要素は、共通のイベント`ButtonClicked`ハンドラー 、および<xref:System.Windows.Controls.Button>前の XAML で定義された既定のスタイルを使用します。  
  
 MyControl1.xaml で、最後<xref:System.Windows.Controls.TextBox>の要素の後に次の XAML を追加します。 これで[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]、複合コントロールの一部が完成しました。  
  
 [!code-xaml[WindowsFormsHostingWpfControl#105](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml#105)]  
  
### <a name="implementing-the-code-behind-file"></a>分離コード ファイルの実装  
 MyControl1.xaml.csの分離コード ファイルには、次の 3 つの重要なタスクが実装されています。
  
1. ユーザーがいずれかのボタンをクリックしたときに発生するイベントを処理します。  
  
2. 要素からデータを<xref:System.Windows.Controls.TextBox>取得し、カスタム イベント引数オブジェクトにパッケージ化します。  
  
3. カスタム`OnButtonClick`イベントを発生させます。  
  
 コントロールは、外観を変更するための色とフォントの多くのプロパティも公開します。 Windows<xref:System.Windows.Forms.Integration.WindowsFormsHost>フォーム コントロールのホストに使用される<xref:System.Windows.Forms.Integration.ElementHost>クラスとは異なり、クラスはコントロールの<xref:System.Windows.Controls.Panel.Background%2A>プロパティのみを公開します。 このコード例と「[チュートリアル: WPF での Windows フォーム複合コントロールのホスト](walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)」で説明した例との類似性を維持するために、コントロールは残りのプロパティを直接公開します。  
  
#### <a name="the-basic-structure-of-the-code-behind-file"></a>分離コード ファイルの基本構造  
 分離コード ファイルは、1 つの名前空間、2`MyControls`つのクラスを含む`MyControl1`名前空間`MyControlEventArgs`、および で構成されます。  
  
```csharp  
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
  
 最初のクラスは`MyControl1`、MyControl1.xaml で定義されている機能を実装するコード[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]を含む部分クラスです。 MyControl1.xaml が解析されると、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]は同じ部分クラスに変換され、2 つの部分クラスがマージされてコンパイル済みコントロールが形成されます。 このため、分離コード ファイル内のクラス名は MyControl1.xaml に割り当てられたクラス名と一致する必要があり、コントロールのルート要素から継承する必要があります。 2 番目の`MyControlEventArgs`クラスは、ホストにデータを返送するために使用されるイベント引数クラスです。  
  
 MyControl1.xaml.cs を開きます。 既存のクラス宣言を変更して、次の名前を持ち、<xref:System.Windows.Controls.Grid>から継承するようにします。  
  
 [!code-csharp[WindowsFormsHostingWpfControl#21](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml.cs#21)]  
  
#### <a name="initializing-the-control"></a>コントロールの初期化  
 このコードでは、次の基本タスクを実装します。  
  
- プライベート イベント 、および`OnButtonClick`関連するデリゲート`MyControlEventHandler`を宣言します。  
  
- ユーザーのデータを格納するいくつかのプライベート グローバル変数を作成します。 このデータは、対応するプロパティを通じて公開されます。  
  
- コントロールの<xref:System.Windows.FrameworkElement.Loaded>イベントのハンドラー`Init`を実装します。 このハンドラーは、MyControl1.xaml で定義された値をグローバル変数に割り当てることで、グローバル変数を初期化します。 これを行うには、一般的な<xref:System.Windows.FrameworkElement.Name%2A><xref:System.Windows.Controls.TextBlock>要素に割り当てられた`nameLabel`を使用して、その要素のプロパティ設定にアクセスします。  
  
 既存のコンストラクターを削除し、次のコードを`MyControl1`クラスに追加します。  
  
 [!code-csharp[WindowsFormsHostingWpfControl#11](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml.cs#11)]  
  
#### <a name="handling-the-buttons-click-events"></a>ボタンのクリック イベントの処理  
 ユーザーは、データ入力タスクが完了したことを示す場合は **、[OK]** ボタンまたは [**キャンセル**] ボタンをクリックします。 どちらのボタンも同じ<xref:System.Windows.Controls.Primitives.ButtonBase.Click>イベント ハンドラ`ButtonClicked`を使用します。 どちらのボタンにも、`btnOK``btnCancel``sender`引数の値を調べることによってどのボタンがクリックされたかをハンドラが判断できる名前または が付いています。 ハンドラーは次の処理を行います。  
  
- 要素の`MyControlEventArgs`データを格納するオブジェクトを作成<xref:System.Windows.Controls.TextBox>します。  
  
- ユーザーが **[キャンセル**] ボタンをクリックした`MyControlEventArgs`場合、オブジェクト`IsOK`のプロパティ`false`を に設定します。  
  
- イベントを`OnButtonClick`発生させ、ユーザーが終了したことをホストに示し、収集したデータを返します。  
  
 メソッドの後に、次`MyControl1`のコードをクラス`Init`に追加します。  
  
 [!code-csharp[WindowsFormsHostingWpfControl#12](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml.cs#12)]  
  
#### <a name="creating-properties"></a>プロパティの作成  
 クラスの残りの部分では単に、前に説明したグローバル変数に対応するプロパティを公開します。 プロパティが変更されると、set アクセサーは、対応する要素のプロパティを変更し、基になるグローバル変数を更新することによって、コントロールの外観を変更します。  
  
 次のコードをクラスに`MyControl1`追加します。  
  
 [!code-csharp[WindowsFormsHostingWpfControl#13](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml.cs#13)]  
  
#### <a name="sending-the-data-back-to-the-host"></a>ホストへのデータの返送  
 ファイルの最後のコンポーネントは`MyControlEventArgs`クラスで、収集したデータをホストに送り返すために使用されます。  
  
 名前空間に次のコードを`MyControls`追加します。 この実装は簡単なので、これ以上の説明はしません。  
  
 [!code-csharp[WindowsFormsHostingWpfControl#14](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml.cs#14)]  
  
 ソリューションをビルドします。 ビルドでは、MyControls.dll という名前の DLL が生成されます。  
  
<a name="winforms_host_section"></a>
## <a name="implementing-the-windows-forms-host-application"></a>Windows フォーム ホスト アプリケーションの実装  
 Windows フォーム ホスト アプリケーション<xref:System.Windows.Forms.Integration.ElementHost>は、オブジェクトを[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]使用して複合コントロールをホストします。 アプリケーションは、`OnButtonClick`複合コントロールからデータを受け取るイベントを処理します。 また、コントロールの外観を変更するために使用できるオプション ボタンのセットもあります。 次の図は、アプリケーションを示しています。  

次の図は、Windows フォーム アプリケーションでホストされている WPF 複合コントロールを示しています"  

 ![Windows フォーム ホスティング アバロン コントロールを示すスクリーンショット。](./media/walkthrough-hosting-a-wpf-composite-control-in-windows-forms/windows-form-hosting-avalon-control.png)  
  
### <a name="creating-the-project"></a>プロジェクトの作成  
 プロジェクトを開始するには  
  
1. Visual Studio を起動し、[**新しいプロジェクト**] ダイアログ ボックスを開きます。  
  
2. [Visual C# と Windows] カテゴリで **、[Windows フォーム アプリケーション]** テンプレートを選択します。  
  
3. 新しいプロジェクトに `WFHost` という名前を付けます。  
  
4. 配置場所として、MyControls の配置先と同じ最上位フォルダーを指定します。  
  
5. **[OK]** をクリックして、プロジェクトを作成します。  
  
 また、含まれている`MyControl1`DLL や他のアセンブリへの参照を追加する必要もあります。  
  
1. ソリューション エクスプローラでプロジェクト名を右クリックし、[**参照の追加]** を選択します。  
  
2. [**参照**] タブをクリックし、MyControls.dll が格納されているフォルダーを参照します。 このチュートリアルの場合は、MyControls\bin\Debug フォルダーです。  
  
3. [マイ コントロール.dll] を選択し **、[OK]** をクリックします。  
  
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
  
3. フォームの右上隅に、複合コントロールを<xref:System.Windows.Forms.Panel?displayProperty=nameWithType>保持するコントロールを[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]追加します。  
  
4. フォームに次<xref:System.Windows.Forms.GroupBox?displayProperty=nameWithType>のコントロールを追加します。  
  
    |名前|Text|  
    |----------|----------|  
    |groupBox1|背景色|  
    |groupBox2|前景色|  
    |groupBox3|フォント サイズ|  
    |groupBox4|フォント ファミリ|  
    |groupBox5|[スタイル]|  
    |groupBox6|フォントの太さ|  
    |groupBox7|コントロールからのデータ|  
  
5. コントロールに次<xref:System.Windows.Forms.RadioButton?displayProperty=nameWithType>のコントロールを<xref:System.Windows.Forms.GroupBox?displayProperty=nameWithType>追加します。  
  
    |GroupBox|名前|Text|  
    |--------------|----------|----------|  
    |groupBox1|radioBackgroundOriginal|変更元|  
    |groupBox1|radioBackgroundLightGreen|ライトグリーン|  
    |groupBox1|radioBackgroundLightSalmon|ライトサーモン|  
    |groupBox2|radioForegroundOriginal|変更元|  
    |groupBox2|radioForegroundRed|[赤]|  
    |groupBox2|radioForegroundYellow|黄|  
    |groupBox3|radioSizeOriginal|変更元|  
    |groupBox3|radioSizeTen|10|  
    |groupBox3|radioSizeTwelve|12|  
    |groupBox4|radioFamilyOriginal|変更元|  
    |groupBox4|radioFamilyTimes|ＭＳ Ｐゴシック|  
    |groupBox4|radioFamilyWingDings|WingDings|  
    |groupBox5|radioStyleOriginal|Normal|  
    |groupBox5|radioStyleItalic|[斜体]|  
    |groupBox6|radioWeightOriginal|変更元|  
    |groupBox6|radioWeightBold|太字|  
  
6. 最後<xref:System.Windows.Forms.GroupBox?displayProperty=nameWithType>のコントロール<xref:System.Windows.Forms.Label?displayProperty=nameWithType>に次のコントロールを追加します。 これらのコントロールは、複合コントロールから返[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]されたデータを表示します。  
  
    |GroupBox|名前|Text|  
    |--------------|----------|----------|  
    |groupBox7|lblName|名前:|  
    |groupBox7|lblAddress|番地:|  
    |groupBox7|lblCity|市区町村:|  
    |groupBox7|lblState|状態:|  
    |groupBox7|lblZip|郵便番号:|  
  
### <a name="initializing-the-form"></a>フォームの初期化  
 通常、フォームの<xref:System.Windows.Forms.Form.Load>イベント ハンドラーでホスト コードを実装します。 次のコードは、<xref:System.Windows.Forms.Form.Load>イベント ハンドラー、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]複合コントロールのイベントの<xref:System.Windows.FrameworkElement.Loaded>ハンドラー、および後で使用するいくつかのグローバル変数の宣言を示しています。  
  
 Windows フォーム デザイナーで、フォームをダブルクリックしてイベント ハンドラー<xref:System.Windows.Forms.Form.Load>を作成します。 Form1.csの上部に、次`using`のステートメントを追加します。  
  
 [!code-csharp[WindowsFormsHostingWpfControl#10](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/WFHost/Form1.cs#10)]  
  
 既存`Form1`のクラスの内容を次のコードに置き換えます。  
  
 [!code-csharp[WindowsFormsHostingWpfControl#2](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/WFHost/Form1.cs#2)]  
  
 上記`Form1_Load`のコードのメソッドは、コントロールをホストするための一般的な[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]手順を示しています。  
  
1. 新しい <xref:System.Windows.Forms.Integration.ElementHost> オブジェクトを作成します。  
  
2. コントロールの<xref:System.Windows.Forms.Control.Dock%2A>プロパティを に設定<xref:System.Windows.Forms.DockStyle.Fill?displayProperty=nameWithType>します。  
  
3. コントロールを<xref:System.Windows.Forms.Integration.ElementHost>コントロールの<xref:System.Windows.Forms.Control.Controls%2A>コレクション<xref:System.Windows.Forms.Panel>に追加します。  
  
4. コントロールのインスタンスを[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]作成します。  
  
5. コントロールの<xref:System.Windows.Forms.Integration.ElementHost.Child%2A>プロパティにコントロールを割り当てることによって、フォーム上<xref:System.Windows.Forms.Integration.ElementHost>の複合コントロールをホストします。  
  
 メソッドの残りの 2`Form1_Load`行は、ハンドラーを 2 つのコントロール イベントにアタッチします。  
  
- `OnButtonClick`は、ユーザーが **[OK]** または [**キャンセル**] ボタンをクリックしたときに複合コントロールによって発生するカスタム イベントです。 このイベントを処理してユーザーの応答を取得し、ユーザーが指定したデータをすべて収集します。  
  
- <xref:System.Windows.FrameworkElement.Loaded>は、コントロールが完全に読み込[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]まれたときに発生する標準イベントです。 ここでこのイベントを使用するのは、この例ではこのコントロールからのプロパティを使用して複数のグローバル変数を初期化する必要があるからです。 フォームの<xref:System.Windows.Forms.Form.Load>イベントの時点では、コントロールは完全には読み込まれ、これらの値はに設定されています`null`。 コントロールの<xref:System.Windows.FrameworkElement.Loaded>イベントが発生するまで待ってから、これらのプロパティにアクセスする必要があります。  
  
 イベント<xref:System.Windows.FrameworkElement.Loaded>ハンドラーは、前のコードに示します。 ハンドラー`OnButtonClick`については、次のセクションで説明します。  
  
### <a name="handling-onbuttonclick"></a>OnButtonClick の処理  
 イベント`OnButtonClick`は、ユーザーが **[OK] または**[**キャンセル**] ボタンをクリックしたときに発生します。  
  
 イベント ハンドラーは、イベント引数の`IsOK`フィールドをチェックして、クリックされたボタンを特定します。 `lbl`*データ*変数は、前述の<xref:System.Windows.Forms.Label>コントロールに対応します。 ユーザーが **[OK] ボタン**をクリックすると、コントロールのコントロールの<xref:System.Windows.Controls.TextBox>データが対応する<xref:System.Windows.Forms.Label>コントロールに割り当てられます。 ユーザーが [**キャンセル**]<xref:System.Windows.Forms.Label.Text%2A>をクリックすると、値は既定の文字列に設定されます。  
  
 次のボタンクリック イベント ハンドラー コード`Form1`をクラスに追加します。  
  
 [!code-csharp[WindowsFormsHostingWpfControl#3](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/WFHost/Form1.cs#3)]  
  
 アプリケーションをビルドして実行します。 WPF 複合コントロールにテキストを追加し **、[OK]** をクリックします。 そのテキストがラベルに表示されます。 この時点で、オプション ボタンを処理するコードは追加されていません。  
  
### <a name="modifying-the-appearance-of-the-control"></a>コントロールの外観の変更  
 フォーム<xref:System.Windows.Forms.RadioButton>上のコントロールを使用すると、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]ユーザーは複合コントロールの前景色と背景色、および複数のフォント プロパティを変更できます。 背景色は<xref:System.Windows.Forms.Integration.ElementHost>、オブジェクトによって公開されます。 残りのプロパティは、コントロールのカスタム プロパティとして公開されます。  
  
 フォーム上の各<xref:System.Windows.Forms.RadioButton>コントロールをダブルクリックして、イベント<xref:System.Windows.Forms.RadioButton.CheckedChanged>ハンドラを作成します。 イベント<xref:System.Windows.Forms.RadioButton.CheckedChanged>ハンドラーを次のコードに置き換えます。  
  
 [!code-csharp[WindowsFormsHostingWpfControl#4](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/WFHost/Form1.cs#4)]  
  
 アプリケーションをビルドして実行します。 別のオプション ボタンをクリックして、WPF 複合コントロール上の影響を確認します。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [Visual Studio で XAML をデザインする](/visualstudio/xaml-tools/designing-xaml-in-visual-studio)
- [チュートリアル: WPF での Windows フォーム複合コントロールのホスト](walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)
- [チュートリアル: Windows フォームで 3D WPF 複合コントロールをホストする](walkthrough-hosting-a-3-d-wpf-composite-control-in-windows-forms.md)
