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
ms.openlocfilehash: aa971f194b29096245ea8fe94ba96cc5e0cd763b
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2019
ms.locfileid: "64605493"
---
# <a name="walkthrough-hosting-a-windows-forms-composite-control-in-wpf"></a>チュートリアル: WPF での Windows フォーム複合コントロールのホスト
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] は、アプリケーションの作成に適した環境を提供します。 ただしがある場合、かなりの投資[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]コードをより効果的か以上で再利用するには、そのコードの一部、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]アプリケーションではなく最初から修正します。 最も一般的なシナリオでは、既存の Windows フォーム コントロールがある場合です。 場合によってもがありませんこれらのコントロールのソース コードにアクセスします。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] このようなコントロールをホストするため、簡単な手順を提供する[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]アプリケーション。 たとえば、使用することができます[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]、特殊なをホストしているときに、プログラミングの大部分の<xref:System.Windows.Forms.DataGridView>コントロール。  
  
 このチュートリアルでのデータ入力を実行する Windows フォーム複合コントロールをホストするアプリケーションを通じて、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]アプリケーション。 複合コントロールは DLL にパッケージ化されています。 この一般的な手順は、より複雑なアプリケーションやコントロールに拡張することができます。 このチュートリアルの外観と機能をほぼ同じにする目的は[チュートリアル。Windows フォームでの WPF 複合コントロールをホストしている](walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)します。 主な違いは、ホストする側とされる側が逆であることです。  
  
 このチュートリアルは、2 つのセクションに分かれています。 最初のセクションでは、Windows フォーム複合コントロールの実装について簡単に説明します。 2 番目のセクションで詳細に複合コントロールをホストする方法について説明します、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]アプリケーションでは、コントロールからイベントを受信し、コントロールのプロパティの一部にアクセスします。  
  
 このチュートリアルでは、以下のタスクを行います。  
  
- Windows フォーム複合コントロールを実装します。  
  
- WPF ホスト アプリケーションの実装。  
  
 このチュートリアルで示すタスクの完全なコード一覧については、次を参照してください。 [WPF サンプル Windows フォーム複合コントロールをホストしている](https://go.microsoft.com/fwlink/?LinkID=159999)します。  
  
## <a name="prerequisites"></a>必須コンポーネント  

このチュートリアルを完了するには Visual Studio が必要です。
  
## <a name="implementing-the-windows-forms-composite-control"></a>Windows フォーム複合コントロールを実装します。  
 この例で使用される Windows フォーム複合コントロールは、単純なデータ入力フォームです。 このフォームは、ユーザーの名前とアドレスを受け取るし、カスタム イベントを使用してホストにその情報を返します。 次の図はレンダリングされたコントロールを示しています。  

 次の図は、Windows フォーム複合コントロールを示しています。  

 ![シンプルな Windows フォーム コントロールを示すスクリーン ショット。](./media/walkthrough-hosting-a-windows-forms-composite-control-in-wpf/windows-forms-control.gif)  
  
### <a name="creating-the-project"></a>プロジェクトの作成  
 プロジェクトを開始するには  
  
1. 起動[!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)]を開き、**新しいプロジェクト** ダイアログ ボックス。  
  
2. ウィンドウのカテゴリの選択、 **Windows フォーム コントロール ライブラリ**テンプレート。  
  
3. 新しいプロジェクトに `MyControls` という名前を付けます。  
  
4. など指定便利な名前付きの最上位フォルダーの場所`WpfHostingWindowsFormsControl`します。 このフォルダーには後でホスト アプリケーションも配置します。  
  
5. **[OK]** をクリックして、プロジェクトを作成します。 既定のプロジェクトには、という名前の 1 つのコントロールが含まれています。`UserControl1`します。  
  
6. ソリューション エクスプローラで、名前を変更`UserControl1`に`MyControl1`します。  
  
 プロジェクトは、以下のシステム DLL を参照している必要があります。 既定で含まれていないこれらの Dll のいずれかの場合は、プロジェクトに追加します。  
  
- システム  
  
- System.Data  
  
- System.Drawing  
  
- System.Windows.Forms  
  
- System.Xml  
  
### <a name="adding-controls-to-the-form"></a>フォームへのコントロールの追加  
 コントロールをフォームに追加します。  
  
- 開いている`MyControl1`デザイナー。  
  
 5 つ追加<xref:System.Windows.Forms.Label>コントロールとそれに対応する<xref:System.Windows.Forms.TextBox>コントロール、サイズ、およびフォーム上の図のように配置されます。 例では、<xref:System.Windows.Forms.TextBox>コントロールの名前が付けられます。  
  
- `txtName`  
  
- `txtAddress`  
  
- `txtCity`  
  
- `txtState`  
  
- `txtZip`  
  
 2 つ追加<xref:System.Windows.Forms.Button>というラベルの付いたコントロール**OK**と**キャンセル**します。 この例では、ボタン名は`btnOK`と`btnCancel`、それぞれします。  
  
### <a name="implementing-the-supporting-code"></a>サポート コードを実装します。  
 コード ビューで、フォームを開きます。 コントロールがそのホストにカスタムを発生させることによって、収集したデータを返します`OnButtonClick`イベント。 データは、イベント引数オブジェクトに含まれます。 次のコードでは、イベントとデリゲートの宣言を示します。  
  
 `MyControl1` クラスに次のコードを追加します。  
  
 [!code-csharp[WpfHostingWindowsFormsControl#2](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/MyControls/MyControl1.cs#2)]
 [!code-vb[WpfHostingWindowsFormsControl#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/VisualBasic/MyControls/MyControl1.vb#2)]

 `MyControlEventArgs`クラスには、ホストに返される情報が含まれています。

 フォームに次のクラスを追加します。

 [!code-csharp[WpfHostingWindowsFormsControl#3](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/MyControls/MyControl1.cs#3)]
 [!code-vb[WpfHostingWindowsFormsControl#3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/VisualBasic/MyControls/MyControl1.vb#3)]

 ユーザーがクリックすると、 **ok**または**キャンセル** ボタン、<xref:System.Windows.Forms.Control.Click>イベント ハンドラーを作成、`MyControlEventArgs`データを格納しているオブジェクトさせ、`OnButtonClick`イベント。 2 つのハンドラーの唯一の違いは、イベント引数の`IsOK`プロパティ。 このプロパティは、どのボタンがクリックされたかを判断するホストを使用できます。 設定されている`true`の **[ok]** ボタン、および`false`の**キャンセル**ボタンをクリックします。 次のコードは、2 つのボタン ハンドラーを示しています。

 `MyControl1` クラスに次のコードを追加します。

 [!code-csharp[WpfHostingWindowsFormsControl#4](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/MyControls/MyControl1.cs#4)]
 [!code-vb[WpfHostingWindowsFormsControl#4](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/VisualBasic/MyControls/MyControl1.vb#4)]

### <a name="giving-the-assembly-a-strong-name-and-building-the-assembly"></a>アセンブリに厳密な名前を付けると、アセンブリのビルド
 このアセンブリによって参照されるの[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]アプリケーションでは、厳密な名前必要があります。 厳密な名前を作成するには、Sn.exe でキー ファイルを作成し、プロジェクトに追加します。

1. [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)] のコマンド プロンプトを開きます。 これを行うには、クリックして、**開始**] メニューの [クリックして**すべてのプログラムまたは Microsoft Visual Studio 2010 または Visual Studio ツール/visual Studio コマンド プロンプト**。 これは、カスタマイズされた環境変数のコンソール ウィンドウを起動します。

2. コマンド プロンプトを使用して、`cd`コマンドをプロジェクト フォルダーに移動します。

3. 次のコマンドを実行して MyControls.snk をという名前のキー ファイルを生成します。

    ```
    Sn.exe -k MyControls.snk
    ```

4. キー ファイルをプロジェクトに含めるにソリューション エクスプ ローラーでプロジェクト名を右クリックし をクリックし、**プロパティ**します。 プロジェクト デザイナーで、クリックして、**署名**] タブで、[、**アセンブリに署名**チェック ボックスをオンし、キー ファイルを参照します。

5. ソリューションをビルドします。 ビルドでは、MyControls.dll という名前の DLL が生成されます。

## <a name="implementing-the-wpf-host-application"></a>WPF ホスト アプリケーションの実装
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]ホスト アプリケーションで使用する、<xref:System.Windows.Forms.Integration.WindowsFormsHost>コントロールをホストに`MyControl1`します。 アプリケーションのハンドル、`OnButtonClick`コントロールからデータを受信するイベントです。 コントロールのプロパティの一部を変更するためのオプション ボタンのコレクションがあります、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]アプリケーション。 次の図は、完成したアプリケーションを示します。

次の図は、WPF アプリケーションに埋め込まれたコントロールを含む、完全なアプリケーションを示しています。

 ![コントロールを示すスクリーン ショットは、WPF ページに埋め込まれます。](./media/walkthrough-hosting-a-windows-forms-composite-control-in-wpf/windows-presentation-foundation-page-control.gif)

### <a name="creating-the-project"></a>プロジェクトの作成
 プロジェクトを開始するには

1. 開いている[!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)]、選択および**新しいプロジェクト**します。

2. ウィンドウのカテゴリの選択、 **WPF アプリケーション**テンプレート。

3. 新しいプロジェクトに `WpfHost` という名前を付けます。

4. 配置場所として、MyControls の配置先と同じ最上位フォルダーを指定します。

5. **[OK]** をクリックして、プロジェクトを作成します。

 含んでいる DLL への参照を追加する必要があります`MyControl1`およびその他のアセンブリ。

1. ソリューション エクスプ ローラーでプロジェクト名を右クリックして**参照の追加**します。

2. をクリックして、**参照**タブをクリックし、MyControls.dll を含むフォルダーを参照します。 このチュートリアルの場合は、MyControls\bin\Debug フォルダーです。

3. MyControls.dll を選択し、クリックして**OK**します。

4. これは、WindowsFormsIntegration.dll がという名前 WindowsFormsIntegration アセンブリへの参照を追加します。

### <a name="implementing-the-basic-layout"></a>基本的なレイアウトを実装します。
 [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] MainWindow.xaml で、ホストのアプリケーションを実装します。 このファイルを含む[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]レイアウトを定義し、Windows フォーム コントロールをホストするマークアップ。 アプリケーションは、3 つのリージョンに分かれています。

- **コントロール プロパティ**パネルで、ホストされるコントロールのさまざまなプロパティを変更に使用できるオプション ボタンのコレクションが含まれています。

- **コントロールからのデータ**パネルで、いくつか含む<xref:System.Windows.Controls.TextBlock>ホストされるコントロールからデータを表示する要素が返されます。

- ホストされるコントロール自体。

 次の XAML は、基本的なレイアウトに表示されます。 ために必要なマークアップをホストに`MyControl1`をこの例から省略するは、後ほど説明します。

 MainWindow.xaml で XAML を次のように置き換えます。 Visual Basic を使用している場合にクラスを変更`x:Class="MainWindow"`します。

 [!code-xaml[WpfHostingWindowsFormsControl#100](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/WpfHost/Page1.xaml#100)]

 最初の<xref:System.Windows.Controls.StackPanel>要素には、複数のセットが含まれています。<xref:System.Windows.Controls.RadioButton>ホストされるコントロールのさまざまな既定のプロパティを変更できるようにするコントロール。 これは、後は、<xref:System.Windows.Forms.Integration.WindowsFormsHost>要素、どのホスト`MyControl1`します。 最終的な<xref:System.Windows.Controls.StackPanel>要素がいくつか含まれています<xref:System.Windows.Controls.TextBlock>ホストされるコントロールによって返されるデータを表示する要素。 要素の順序と<xref:System.Windows.Controls.DockPanel.Dock%2A>と<xref:System.Windows.FrameworkElement.Height%2A>属性の設定では、ウィンドウにホストされるコントロールを埋め込むギャップやゆがみがないです。

#### <a name="hosting-the-control"></a>コントロールをホストしています。
 次の編集したバージョン以前の XAML のために必要な要素について重点的にホスト`MyControl1`します。

 [!code-xaml[WpfHostingWindowsFormsControl#101](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/WpfHost/Page1.xaml#101)]
[!code-xaml[WpfHostingWindowsFormsControl#102](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/WpfHost/Page1.xaml#102)]

 `xmlns`マッピング属性の名前空間への参照を作成し、`MyControls`ホストされるコントロールを含む名前空間。 このマッピングを使用すると、表す`MyControl1`で[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]として`<mcl:MyControl1>`します。

 2 つの要素、XAML では、ホスティングを処理します。

- `WindowsFormsHost` 表す、<xref:System.Windows.Forms.Integration.WindowsFormsHost>要素での Windows フォーム コントロールをホストすることができます、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]アプリケーション。

- `mcl:MyControl1`を表す`MyControl1`、に追加されます、<xref:System.Windows.Forms.Integration.WindowsFormsHost>要素の子のコレクション。 一部としてこの Windows フォーム コントロールを表示する結果として、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]ウィンドウ、およびするが、アプリケーションからコントロールと通信できます。

### <a name="implementing-the-code-behind-file"></a>分離コード ファイルの実装
 MainWindow.xaml.vb または MainWindow.xaml.cs で、分離コード ファイルには機能を実装する手続き型コードが含まれています、[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]前のセクションで説明します。 主な作業は次のとおりです。

- イベント ハンドラーをアタッチする`MyControl1`の`OnButtonClick`イベント。

- さまざまなプロパティを変更する`MyControl1`オプション ボタンのコレクションの設定方法に基づいて、します。

- コントロールによって収集されたデータを表示します。

#### <a name="initializing-the-application"></a>アプリケーションの初期化
 ウィンドウのイベント ハンドラーの初期化コードが含まれている<xref:System.Windows.FrameworkElement.Loaded>イベントをコントロールのイベント ハンドラーをアタッチおよび`OnButtonClick`イベント。

 MainWindow.xaml.vb または MainWindow.xaml.cs で次のコードを追加、`MainWindow`クラス。

 [!code-csharp[WpfHostingWindowsFormsControl#11](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/WpfHost/Page1.xaml.cs#11)]
 [!code-vb[WpfHostingWindowsFormsControl#11](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/VisualBasic/WpfHost/Page1.xaml.vb#11)]

 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]以前に追加した説明`MyControl1`を<xref:System.Windows.Forms.Integration.WindowsFormsHost>キャストする要素の子要素のコレクション、<xref:System.Windows.Forms.Integration.WindowsFormsHost>要素の<xref:System.Windows.Forms.Integration.WindowsFormsHost.Child%2A>への参照を取得する`MyControl1`します。 イベント ハンドラーをアタッチするその参照を使用することができますし`OnButtonClick`します。

 コントロール自体への参照を提供するだけでなく<xref:System.Windows.Forms.Integration.WindowsFormsHost>多数のアプリケーションから操作できるコントロールのプロパティを公開します。 初期化コードでは、プライベートのグローバル変数を後で、アプリケーションで使用するこれらの値を割り当てます。

 内の型を簡単にアクセスできるように、 `MyControls` DLL では、次の追加`Imports`または`using`ファイルの先頭にステートメント。

```vb
Imports MyControls
```

```csharp
using MyControls;
```

#### <a name="handling-the-onbuttonclick-event"></a>OnButtonClick のイベントを処理します。
 `MyControl1` 発生させる、`OnButtonClick`イベントかのコントロールのボタンをクリックするとします。

 `MainWindow` クラスに次のコードを追加します。

 [!code-csharp[WpfHostingWindowsFormsControl#12](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/WpfHost/Page1.xaml.cs#12)]
 [!code-vb[WpfHostingWindowsFormsControl#12](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/VisualBasic/WpfHost/Page1.xaml.vb#12)]

 テキスト ボックス内のデータをまとめ、`MyControlEventArgs`オブジェクト。 ユーザーがクリックした場合、 **OK**ボタン、イベント ハンドラーは、データを抽出し、下のパネルに表示します`MyControl1`。

#### <a name="modifying-the-controls-properties"></a>コントロールのプロパティの変更
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>要素がいくつかのホストされるコントロールの既定のプロパティを公開します。 その結果、アプリケーションのスタイルをより厳密に一致するようにコントロールの外観を変更できます。 左側のパネルのオプション ボタンのセットは、いくつかの色とフォントのプロパティを変更するユーザーを有効にします。 ボタンの各セットのハンドラーがある、<xref:System.Windows.Controls.Primitives.ButtonBase.Click>イベントでは、ユーザーのオプション ボタンの選択を検出し、コントロールに対応するプロパティを変更します。

 `MainWindow` クラスに次のコードを追加します。

 [!code-csharp[WpfHostingWindowsFormsControl#13](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/WpfHost/Page1.xaml.cs#13)]
 [!code-vb[WpfHostingWindowsFormsControl#13](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/VisualBasic/WpfHost/Page1.xaml.vb#13)]  
  
 アプリケーションをビルドして実行します。 Windows フォーム複合コントロールでテキストを追加し、クリックして**OK**します。 そのテキストがラベルに表示されます。 コントロールに影響を表示するさまざまなオプション ボタンをクリックします。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [Visual Studio で XAML をデザインする](/visualstudio/designers/designing-xaml-in-visual-studio)
- [チュートリアル: WPF での Windows フォーム コントロールのホスト](walkthrough-hosting-a-windows-forms-control-in-wpf.md)
- [チュートリアル: Windows フォームでの WPF 複合コントロールをホストしています。](walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
