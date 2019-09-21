---
title: 'チュートリアル: WPF での Windows フォーム複合コントロールのホスト'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hosting Windows Forms control in WPF [WPF]
- composite controls [WPF], hosting in WPF
ms.assetid: 96fcd78d-1c77-4206-8928-3a0579476ef4
ms.openlocfilehash: e4c1de17b131ee68c6e6fce0035b703eb5b489a0
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/14/2019
ms.locfileid: "70991882"
---
# <a name="walkthrough-hosting-a-windows-forms-composite-control-in-wpf"></a>チュートリアル: WPF での Windows フォーム複合コントロールのホスト
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] は、アプリケーションの作成に適した環境を提供します。 ただし、コードに[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]多大な投資をしている場合は、最初から書き換えるのではなく、少なくともそのコードの一部を[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]アプリケーションで再利用する方が効果的です。 最も一般的なシナリオは、既存の Windows フォームコントロールがある場合です。 場合によっては、これらのコントロールのソースコードにアクセスできないこともあります。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)][!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]アプリケーションでこのようなコントロールをホストするための簡単な手順を示します。 たとえば、特定<xref:System.Windows.Forms.DataGridView>のコントロールを[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]ホストするときに、ほとんどのプログラミングにを使用できます。  
  
 このチュートリアルでは、 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]アプリケーションでデータ入力を実行するために Windows フォーム複合コントロールをホストするアプリケーションについて説明します。 複合コントロールは DLL にパッケージ化されています。 この一般的な手順は、より複雑なアプリケーションやコントロールに拡張することができます。 このチュートリアルは、次のチュートリアルに[似た外観と機能を持つように設計されています。Windows フォーム](walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)での WPF 複合コントロールのホスト。 主な違いは、ホストする側とされる側が逆であることです。  
  
 このチュートリアルは、2 つのセクションに分かれています。 最初のセクションでは、Windows フォーム複合コントロールの実装について簡単に説明します。 2番目のセクションでは、 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]アプリケーションで複合コントロールをホストする方法、コントロールからイベントを受信する方法、およびコントロールのプロパティの一部にアクセスする方法の詳細について説明します。  
  
 このチュートリアルでは、以下のタスクを行います。  
  
- Windows フォーム複合コントロールの実装。  
  
- WPF ホストアプリケーションの実装。  
  
 このチュートリアルで示すタスクの完全なコード一覧については、「 [WPF での Windows フォーム複合コントロールのホスト](https://go.microsoft.com/fwlink/?LinkID=159999)」のサンプルを参照してください。  
  
## <a name="prerequisites"></a>必須コンポーネント  

このチュートリアルを完了するには Visual Studio が必要です。
  
## <a name="implementing-the-windows-forms-composite-control"></a>Windows フォーム複合コントロールの実装  
 この例で使用される複合コントロール Windows フォームは、単純なデータ入力フォームです。 このフォームは、ユーザーの名前とアドレスを受け取り、カスタムイベントを使用してその情報をホストに返します。 次の図はレンダリングされたコントロールを示しています。  

 次の図は Windows フォーム複合コントロールを示しています。  

 ![単純な Windows フォームコントロールを示すスクリーンショット。](./media/walkthrough-hosting-a-windows-forms-composite-control-in-wpf/windows-forms-control.gif)  
  
### <a name="creating-the-project"></a>プロジェクトの作成  
 プロジェクトを開始するには  
  
1. を[!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)]起動し、 **[新しいプロジェクト]** ダイアログボックスを開きます。  
  
2. ウィンドウ カテゴリで、 **Windows フォームコントロールライブラリ** テンプレートを選択します。  
  
3. 新しいプロジェクトに `MyControls` という名前を付けます。  
  
4. [場所] には、など、便利な最上位レベルのフォルダー `WpfHostingWindowsFormsControl`を指定します。 このフォルダーには後でホスト アプリケーションも配置します。  
  
5. **[OK]** をクリックして、プロジェクトを作成します。 既定のプロジェクトには、という`UserControl1`名前のコントロールが1つ含まれています。  
  
6. ソリューションエクスプローラーで、の`UserControl1`名前`MyControl1`をに変更します。  
  
 プロジェクトは、以下のシステム DLL を参照している必要があります。 これらの Dll のいずれかが既定で含まれていない場合は、プロジェクトに追加します。  
  
- システム  
  
- System.Data  
  
- System.Drawing  
  
- System.Windows.Forms  
  
- System.Xml  
  
### <a name="adding-controls-to-the-form"></a>フォームへのコントロールの追加  
 フォームにコントロールを追加するには、次のようにします。  
  
- デザイナー `MyControl1`でを開きます。  
  
 上の<xref:System.Windows.Forms.Label>図に示すよう<xref:System.Windows.Forms.TextBox>に、5つのコントロールとそれに対応するコントロールを、フォーム上の上の図のように、サイズを調整して配置します。 この例<xref:System.Windows.Forms.TextBox>では、コントロールにという名前が付けられています。  
  
- `txtName`  
  
- `txtAddress`  
  
- `txtCity`  
  
- `txtState`  
  
- `txtZip`  
  
 OK と<xref:System.Windows.Forms.Button> **キャンセル**というラベルが付いた2つのコントロールを追加します。 この例では、ボタン名`btnOK`はそれぞれと`btnCancel`です。  
  
### <a name="implementing-the-supporting-code"></a>サポートコードの実装  
 コードビューでフォームを開きます。 コントロールは、カスタム`OnButtonClick`イベントを発生させて、収集されたデータをホストに返します。 データは、イベント引数オブジェクトに格納されます。 次のコードは、イベントとデリゲート宣言を示しています。  
  
 `MyControl1` クラスに次のコードを追加します。  
  
 [!code-csharp[WpfHostingWindowsFormsControl#2](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/MyControls/MyControl1.cs#2)]
 [!code-vb[WpfHostingWindowsFormsControl#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/VisualBasic/MyControls/MyControl1.vb#2)]

 `MyControlEventArgs`クラスには、ホストに返される情報が含まれています。

 次のクラスをフォームに追加します。

 [!code-csharp[WpfHostingWindowsFormsControl#3](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/MyControls/MyControl1.cs#3)]
 [!code-vb[WpfHostingWindowsFormsControl#3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/VisualBasic/MyControls/MyControl1.vb#3)]

 ユーザーが **[OK]** または **[キャンセル**] ボタン<xref:System.Windows.Forms.Control.Click>をクリックすると`MyControlEventArgs` 、イベントハンドラーによって、データ`OnButtonClick`を格納するオブジェクトが作成され、イベントが発生します。 2つのハンドラーの唯一の違いは、イベント引数`IsOK`のプロパティです。 このプロパティを使用すると、ホストはどのボタンがクリックされたかを判断できます。 **[OK** ] ボタン`true`と`false` **[キャンセル]** ボタンには、が設定されています。 次のコードは、2つのボタンハンドラーを示しています。

 `MyControl1` クラスに次のコードを追加します。

 [!code-csharp[WpfHostingWindowsFormsControl#4](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/MyControls/MyControl1.cs#4)]
 [!code-vb[WpfHostingWindowsFormsControl#4](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/VisualBasic/MyControls/MyControl1.vb#4)]

### <a name="giving-the-assembly-a-strong-name-and-building-the-assembly"></a>アセンブリに厳密な名前を付け、アセンブリをビルドする
 このアセンブリを[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]アプリケーションから参照するには、厳密な名前を持つ必要があります。 厳密な名前を作成するには、Sn.exe でキーファイルを作成し、プロジェクトに追加します。

1. [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)] のコマンド プロンプトを開きます。 これを行うには、 **[スタート]** メニューをクリックし、すべてのプログラム、Microsoft Visual Studio 2010、Visual Studio Tools、 **[Visual Studio コマンドプロンプト]** の順に選択します。 これにより、環境変数がカスタマイズされたコンソールウィンドウが起動します。

2. コマンドプロンプトで`cd`コマンドを使用して、プロジェクトフォルダーにアクセスします。

3. 次のコマンドを実行して、Mycontrols.dll という名前のキーファイルを生成します。

    ```console
    Sn.exe -k MyControls.snk
    ```

4. キーファイルをプロジェクトに含めるには、ソリューションエクスプローラーでプロジェクト名を右クリックし、 **[プロパティ]** をクリックします。 プロジェクトデザイナーで、 **[署名]** タブをクリックし、 **[アセンブリの署名]** チェックボックスをオンにして、キーファイルを参照します。

5. ソリューションをビルドします。 ビルドでは、MyControls.dll という名前の DLL が生成されます。

## <a name="implementing-the-wpf-host-application"></a>WPF ホストアプリケーションの実装
 ホスト[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]アプリケーションは、 <xref:System.Windows.Forms.Integration.WindowsFormsHost>コントロールを使用し`MyControl1`てをホストします。 アプリケーションは、コントロール`OnButtonClick`からデータを受信するイベントを処理します。 また、コントロールのプロパティの一部を[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]アプリケーションから変更できるようにするオプションボタンのコレクションも用意されています。 完成したアプリケーションを次の図に示します。

次の図は、WPF アプリケーションに埋め込まれたコントロールを含む、完全なアプリケーションを示しています。

 ![WPF ページに埋め込まれたコントロールを示すスクリーンショット。](./media/walkthrough-hosting-a-windows-forms-composite-control-in-wpf/windows-presentation-foundation-page-control.gif)

### <a name="creating-the-project"></a>プロジェクトの作成
 プロジェクトを開始するには

1. を[!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)]開き、 **[新しいプロジェクト]** を選択します。

2. ウィンドウ カテゴリで、 **WPF アプリケーション** テンプレートを選択します。

3. 新しいプロジェクトに `WpfHost` という名前を付けます。

4. 配置場所として、MyControls の配置先と同じ最上位フォルダーを指定します。

5. **[OK]** をクリックして、プロジェクトを作成します。

 また、および他のアセンブリを含む`MyControl1` DLL への参照を追加する必要もあります。

1. ソリューションエクスプローラーでプロジェクト名を右クリックし、 **[参照の追加]** を選択します。

2. **[参照]** タブをクリックし、mycontrols.dll が含まれているフォルダーを参照します。 このチュートリアルの場合は、MyControls\bin\Debug フォルダーです。

3. Mycontrols.dll を選択し、 **OK** をクリックします。

4. Windowsフォーム統合アセンブリへの参照を追加します。このアセンブリには、Windowsフォーム統合 dll という名前が付けられています。

### <a name="implementing-the-basic-layout"></a>基本レイアウトの実装
 ホスト[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]アプリケーションのは、mainwindow.xaml に実装されています。 このファイルに[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]は、レイアウトを定義し、Windows フォームコントロールをホストするマークアップが含まれています。 アプリケーションは、次の3つのリージョンに分割されます。

- **[コントロールのプロパティ]** パネル。このパネルには、ホストされているコントロールのさまざまなプロパティを変更するために使用できるオプションボタンのコレクションが含まれています。

- コントロールパネルの**データ**。これには、 <xref:System.Windows.Controls.TextBlock>ホストされるコントロールから返されたデータを表示する要素がいくつか含まれています。

- ホストされるコントロール自体。

 基本的なレイアウトを次の XAML に示します。 この例では、をホスト`MyControl1`するために必要なマークアップが省略されていますが、後で説明します。

 Mainwindow.xaml の XAML を次のように置き換えます。 Visual Basic を使用している場合は、クラス`x:Class="MainWindow"`をに変更します。

 [!code-xaml[WpfHostingWindowsFormsControl#100](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/WpfHost/Page1.xaml#100)]

 最初<xref:System.Windows.Controls.StackPanel>の要素には、ホスト<xref:System.Windows.Controls.RadioButton>されるコントロールのさまざまな既定のプロパティを変更できるようにするコントロールのセットがいくつか含まれています。 その後に、を<xref:System.Windows.Forms.Integration.WindowsFormsHost>ホスト`MyControl1`する要素が続きます。 最後<xref:System.Windows.Controls.StackPanel>の要素には<xref:System.Windows.Controls.TextBlock> 、ホストされるコントロールによって返されるデータを表示するいくつかの要素が含まれています。 要素の順序と<xref:System.Windows.Controls.DockPanel.Dock%2A> <xref:System.Windows.FrameworkElement.Height%2A>属性の設定によって、ホストされているコントロールがウィンドウに埋め込まれ、ギャップやゆがみは生じません。

#### <a name="hosting-the-control"></a>コントロールのホスト
 前の XAML の次の編集されたバージョンは、をホスト`MyControl1`するために必要な要素に焦点を当てています。

 [!code-xaml[WpfHostingWindowsFormsControl#101](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/WpfHost/Page1.xaml#101)]
[!code-xaml[WpfHostingWindowsFormsControl#102](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/WpfHost/Page1.xaml#102)]

 名前`xmlns`空間マッピング属性は、ホストされ`MyControls`ているコントロールを含む名前空間への参照を作成します。 このマッピングにより、で`MyControl1` [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]をと`<mcl:MyControl1>`して表すことができます。

 XAML の2つの要素は、ホストを処理します。

- `WindowsFormsHost`アプリケーションで Windows フォームコントロールをホストできるようにする要素を表します。<xref:System.Windows.Forms.Integration.WindowsFormsHost> [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]

- `mcl:MyControl1`が表す`MyControl1`は、 <xref:System.Windows.Forms.Integration.WindowsFormsHost>要素の子コレクションに追加されます。 その結果、この Windows フォームコントロールが[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]ウィンドウの一部としてレンダリングされ、アプリケーションからコントロールと通信できるようになります。

### <a name="implementing-the-code-behind-file"></a>分離コード ファイルの実装
 分離コードファイル mainwindow.xaml または MainWindow.xaml.cs には、前のセクションで[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]説明したの機能を実装する手続き型のコードが含まれています。 主なタスクは次のとおりです。

- イベントハンドラーをの`MyControl1` `OnButtonClick`イベントにアタッチしています。

- オプションボタンのコレクション`MyControl1`の設定方法に基づいて、のさまざまなプロパティを変更します。

- コントロールによって収集されたデータを表示します。

#### <a name="initializing-the-application"></a>アプリケーションの初期化
 初期化コードは、ウィンドウの<xref:System.Windows.FrameworkElement.Loaded>イベントのイベントハンドラーに含まれており、イベントハンドラーをコントロールの`OnButtonClick`イベントにアタッチします。

 Mainwindow.xaml または MainWindow.xaml.cs で、次のコードを`MainWindow`クラスに追加します。

 [!code-csharp[WpfHostingWindowsFormsControl#11](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/WpfHost/Page1.xaml.cs#11)]
 [!code-vb[WpfHostingWindowsFormsControl#11](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/VisualBasic/WpfHost/Page1.xaml.vb#11)]

 前に[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]説明した`MyControl1`が<xref:System.Windows.Forms.Integration.WindowsFormsHost>要素の<xref:System.Windows.Forms.Integration.WindowsFormsHost>子要素コレクションに追加されているため、 <xref:System.Windows.Forms.Integration.WindowsFormsHost.Child%2A>要素のをキャストし`MyControl1`てへの参照を取得できます。 その後、その参照を使用して、に`OnButtonClick`イベントハンドラーをアタッチできます。

 コントロール自体への参照を提供するだけでなく<xref:System.Windows.Forms.Integration.WindowsFormsHost> 、では、アプリケーションから操作できるコントロールのプロパティをいくつか公開しています。 初期化コードは、これらの値をプライベートグローバル変数に割り当てて、後でアプリケーションで使用できるようにします。

 `MyControls` DLL 内の型に簡単にアクセスできるようにするには、 `Imports`ファイル`using`の先頭に次のまたはステートメントを追加します。

```vb
Imports MyControls
```

```csharp
using MyControls;
```

#### <a name="handling-the-onbuttonclick-event"></a>OnButtonClick イベントの処理
 `MyControl1`ユーザーが`OnButtonClick`コントロールのボタンのいずれかをクリックしたときに、イベントを発生させます。

 `MainWindow` クラスに次のコードを追加します。

 [!code-csharp[WpfHostingWindowsFormsControl#12](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/WpfHost/Page1.xaml.cs#12)]
 [!code-vb[WpfHostingWindowsFormsControl#12](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/VisualBasic/WpfHost/Page1.xaml.vb#12)]

 テキストボックス内のデータは、 `MyControlEventArgs`オブジェクトにパックされます。 ユーザーが **[OK** ] ボタンをクリックすると、イベントハンドラーによってデータが抽出され`MyControl1`、下のパネルに表示されます。

#### <a name="modifying-the-controls-properties"></a>コントロールのプロパティの変更
 要素<xref:System.Windows.Forms.Integration.WindowsFormsHost>は、ホストされているコントロールの既定のプロパティのいくつかを公開します。 その結果、アプリケーションのスタイルに合わせてコントロールの外観を変更することができます。 左側のパネルにあるオプションボタンのセットを使用すると、ユーザーはいくつかの色とフォントのプロパティを変更できます。 各ボタンのセットには、 <xref:System.Windows.Controls.Primitives.ButtonBase.Click>イベントのハンドラーがあります。このハンドラーによって、ユーザーのオプションボタンの選択が検出され、コントロールの対応するプロパティが変更されます。

 `MainWindow` クラスに次のコードを追加します。

 [!code-csharp[WpfHostingWindowsFormsControl#13](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/WpfHost/Page1.xaml.cs#13)]
 [!code-vb[WpfHostingWindowsFormsControl#13](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/VisualBasic/WpfHost/Page1.xaml.vb#13)]  
  
 アプリケーションをビルドして実行します。 Windows フォーム複合コントロールにテキストを追加し、[ **OK]** をクリックします。 そのテキストがラベルに表示されます。 さまざまなオプションボタンをクリックして、コントロールの効果を確認します。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [Visual Studio で XAML をデザインする](/visualstudio/designers/designing-xaml-in-visual-studio)
- [チュートリアル: WPF での Windows フォームコントロールのホスト](walkthrough-hosting-a-windows-forms-control-in-wpf.md)
- [チュートリアル: Windows フォームでの WPF 複合コントロールのホスト](walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
