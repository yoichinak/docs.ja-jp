---
title: Windows フォーム コントロールの機能別一覧
ms.date: 03/30/2017
helpviewer_keywords:
- controls [Windows Forms], by function
- Windows Forms, controls by function
- Windows Forms controls, list of
ms.assetid: 5e65a6c3-5d6f-480d-beb8-b28f865f07e3
ms.openlocfilehash: 3a82642c985b7ec1cee885cdda7b054adbe3dfee
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59115480"
---
# <a name="windows-forms-controls-by-function"></a>Windows フォーム コントロールの機能別一覧
Windows フォームでは、多数の関数を実行するコントロールとコンポーネントを提供します。 次の表は、Windows フォーム コントロールおよび一般的な関数に応じたコンポーネントを示します。 さらに、複数のコントロールが存在する同じ機能を提供、推奨されるコントロールは、置き換えられるコントロールについての注釈を表示されています。 別の後続のテーブルに置き換えられるコントロールは、その推奨される代替と共に一覧表示されます。  
  
> [!NOTE]
>  すべてのコントロールや Windows フォームで使用できるコンポーネントを加えない、次の表詳細な一覧を参照してください[Windows フォームで使用するコントロール。](controls-to-use-on-windows-forms.md)  
  
## <a name="recommended-controls-and-components-by-function"></a>推奨されるコントロールとコンポーネント別関数  
  
|関数|コントロール|説明|  
|--------------|-------------|-----------------|  
|データの表示|<xref:System.Windows.Forms.DataGridView> コントロール|<xref:System.Windows.Forms.DataGridView>コントロールでは、データを表示するカスタマイズ可能なテーブルが用意されています。 <xref:System.Windows.Forms.DataGridView>クラスは、セル、行、列、および罫線のカスタマイズを使用できます。 **注:**<xref:System.Windows.Forms.DataGridView>コントロールで不足している多数の基本と高度な機能を提供する、<xref:System.Windows.Forms.DataGrid>コントロール。 詳細については、次を参照してください[の相違点の間、Windows フォームの DataGridView コントロールと DataGrid コントロール。](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md)|  
|データのバインドとナビゲーション|<xref:System.Windows.Forms.BindingSource> コンポーネント|通貨管理、変更通知、およびその他のサービスを提供することで、データをフォームにコントロールのバインドを簡略化します。|  
||<xref:System.Windows.Forms.BindingNavigator> コントロール|フォーム上のデータを移動および操作ツールバー型インターフェイスを提供します。|  
|テキストの編集|<xref:System.Windows.Forms.TextBox> コントロール|実行時に、ユーザーが編集またはプログラムで変更できるデザイン時に入力したテキストが表示されます。|  
||<xref:System.Windows.Forms.RichTextBox> コントロール|プレーン テキストまたはリッチ テキスト形 (式 RTF) で書式設定を表示するテキストを有効にします。|  
||<xref:System.Windows.Forms.MaskedTextBox> コントロール|ユーザー入力の形式を制限します。|  
|情報の表示 (読み取り専用)|<xref:System.Windows.Forms.Label> コントロール|ユーザーが直接編集できないテキストを表示します。|  
||<xref:System.Windows.Forms.LinkLabel> コントロール|Web スタイル リンクとしてテキストを表示し、ユーザーが特別なテキストをクリックしたときにイベントをトリガーします。 通常、テキストは別のウィンドウまたは Web サイトへのリンクです。|  
||<xref:System.Windows.Forms.StatusStrip> コントロール|親フォームの下部に、通常、フレームの領域を使用して、アプリケーションの現在の状態に関する情報を表示します。|  
||<xref:System.Windows.Forms.ProgressBar> コントロール|ユーザー操作の現在の進行状況が表示されます。|  
|Web ページの表示|<xref:System.Windows.Forms.WebBrowser> コントロール|ユーザーがフォーム内で Web ページをナビゲートできるようにします。|  
|一覧から選択|<xref:System.Windows.Forms.CheckedListBox> コントロール|項目のチェック ボックスをそれぞれ付属のスクロール可能な一覧が表示されます。|  
||<xref:System.Windows.Forms.ComboBox> コントロール|項目の一覧が表示されます。|  
||<xref:System.Windows.Forms.DomainUpDown> コントロール|ユーザーがボタンと下矢印を使用してスクロールできるテキスト項目の一覧を表示します。|  
||<xref:System.Windows.Forms.ListBox> コントロール|テキストとグラフィカル項目 (アイコン) の一覧が表示されます。|  
||<xref:System.Windows.Forms.ListView> コントロール|次の 4 つの異なるビューのいずれかで項目を表示します。 ビューには、テキストのみ、小さいアイコンとテキスト、テキストと大きいアイコン、および詳細ビューが含まれます。|  
||<xref:System.Windows.Forms.NumericUpDown> コントロール|ユーザーがボタンと下矢印を使用してスクロールできる数字の一覧を表示します。|  
||<xref:System.Windows.Forms.TreeView> コントロール|テキストとオプションのチェック ボックスまたはアイコンで構成されるノード オブジェクトの階層コレクションを表示します。|  
|グラフィックを表示します。|<xref:System.Windows.Forms.PictureBox> コントロール|フレーム内には、ビットマップ、アイコンなどのグラフィック ファイルを表示します。|  
|グラフィックスのストレージ|<xref:System.Windows.Forms.ImageList> コントロール|イメージ用のリポジトリとして機能します。 <xref:System.Windows.Forms.ImageList> コントロールとが含まれているイメージは、次の 1 つのアプリケーションから再利用できます。|  
|値の設定|<xref:System.Windows.Forms.CheckBox> コントロール|チェック ボックスとテキストのラベルが表示されます。 一般にオプションを設定するために使用します。|  
||<xref:System.Windows.Forms.CheckedListBox> コントロール|項目のチェック ボックスをそれぞれ付属のスクロール可能な一覧が表示されます。|  
||<xref:System.Windows.Forms.RadioButton> コントロール|オンまたはオフになっていることができます ボタンが表示されます。|  
||<xref:System.Windows.Forms.TrackBar> コントロール|スケール沿いの「つまみ」を移動することによって、スケールに値を設定することができます。|  
|日付の設定|<xref:System.Windows.Forms.DateTimePicker> コントロール|日付または時刻を選択するためのグラフィカルなカレンダーが表示されます。|  
||<xref:System.Windows.Forms.MonthCalendar> コントロール|日付の範囲を選択できるようにするグラフィカルなカレンダーが表示されます。|  
|ダイアログ ボックス|<xref:System.Windows.Forms.ColorDialog> コントロール|ユーザー インターフェイス要素の色を設定できるカラー ピッカー ダイアログ ボックスが表示されます。|  
||<xref:System.Windows.Forms.FontDialog> コントロール|フォントとその属性を設定するユーザーを許可する ダイアログ ボックスが表示されます。|  
||<xref:System.Windows.Forms.OpenFileDialog> コントロール|移動し、ファイルを選択できるダイアログ ボックスが表示されます。|  
||<xref:System.Windows.Forms.PrintDialog> コントロール|ユーザーがプリンターを選択し、その属性を設定できるようにする ダイアログ ボックスが表示されます。|  
||<xref:System.Windows.Forms.PrintPreviewDialog> コントロール|どのコントロールを表示するダイアログ ボックスが表示されます<xref:System.Drawing.Printing.PrintDocument>印刷時にコンポーネントが表示されます。|  
||<xref:System.Windows.Forms.FolderBrowserDialog> コントロール|[参照]、作成、および最終的にフォルダーを選択できるダイアログが表示されます。|  
||<xref:System.Windows.Forms.SaveFileDialog> コントロール|ユーザー ファイルを保存することを許可 ダイアログ ボックスが表示されます。|  
|メニュー コントロール|<xref:System.Windows.Forms.MenuStrip> コントロール|カスタム メニューを作成します。 **注:**<xref:System.Windows.Forms.MenuStrip>を置き換えるに設計されていますが、<xref:System.Windows.Forms.MainMenu>コントロール。|  
||<xref:System.Windows.Forms.ContextMenuStrip> コントロール|カスタム コンテキスト メニューを作成します。 **注:**<xref:System.Windows.Forms.ContextMenuStrip>を置き換えるに設計されていますが、<xref:System.Windows.Forms.ContextMenu>コントロール。|  
|コマンド|<xref:System.Windows.Forms.Button> コントロール|開始、停止、または、プロセスを中断します。|  
||<xref:System.Windows.Forms.LinkLabel> コントロール|Web スタイル リンクとしてテキストを表示し、ユーザーが特別なテキストをクリックしたときにイベントをトリガーします。 通常、テキストは別のウィンドウまたは Web サイトへのリンクです。|  
||<xref:System.Windows.Forms.NotifyIcon> コントロール|バック グラウンドで実行されているアプリケーションを表すタスク バーの状態通知領域にアイコンが表示されます。|  
||<xref:System.Windows.Forms.ToolStrip> コントロール|Microsoft Windows XP、Microsoft Office、Microsoft Internet Explorer、またはカスタムのルック アンド フィール、テーマ、なしとやオーバーフローと実行時の項目の並べ替えをサポートできるツールバーを作成します。 **注:**<xref:System.Windows.Forms.ToolStrip>置換するコントロールがデザインされた、<xref:System.Windows.Forms.ToolBar>コントロール。|  
|ユーザー ヘルプ|<xref:System.Windows.Forms.HelpProvider> コンポーネント|コントロールのポップアップまたはオンライン ヘルプを提供します。|  
||<xref:System.Windows.Forms.ToolTip> コンポーネント|ユーザーがコントロール上にポインターを置いたときに、コントロールの用途の簡単な説明を表示するポップアップ ウィンドウを提供します。|  
|その他のコントロールをグループ化|<xref:System.Windows.Forms.Panel> コントロール|ラベルの付いていないのスクロール可能なフレーム上のコントロールのセットをグループ化します。|  
||<xref:System.Windows.Forms.GroupBox> コントロール|ラベルの付いたスクロールできないフレームでラジオ ボタン) などのコントロールのセットをグループ化します。|  
||<xref:System.Windows.Forms.TabControl> コントロール|グループ化されたオブジェクトを効率的に整理してアクセスするためのタブ付きページを提供します。|  
||<xref:System.Windows.Forms.SplitContainer> コントロール|移動可能なバーで区切られた 2 つのパネルを提供します。 **注:**<xref:System.Windows.Forms.SplitContainer>置換するコントロールがデザインされた、<xref:System.Windows.Forms.Splitter>コントロール。|  
||<xref:System.Windows.Forms.TableLayoutPanel> コントロール|内容を行と列から成るグリッドに動的にレイアウトするパネルを表します。|  
||<xref:System.Windows.Forms.FlowLayoutPanel> コントロール|水平方向または垂直方向に内容を動的にレイアウトするパネルを表します。|  
|オーディオ|<xref:System.Media.SoundPlayer> コントロール|サウンドの .wav 形式のファイルを再生します。 サウンドの読み込みまたは非同期で実行できます。|  
  
## <a name="superseded-controls-and-components-by-function"></a>コントロールと関数によってコンポーネントの置き換え  
  
|関数|置き換えられるコントロール|推奨される置換|  
|--------------|------------------------|-----------------------------|  
|データの表示|<xref:System.Windows.Forms.DataGrid>|<xref:System.Windows.Forms.DataGridView>|  
|情報の表示 (読み取り専用コントロール)|<xref:System.Windows.Forms.StatusBar>|<xref:System.Windows.Forms.StatusStrip>|  
|メニュー コントロール|<xref:System.Windows.Forms.ContextMenu>|<xref:System.Windows.Forms.ContextMenuStrip>|  
||<xref:System.Windows.Forms.MainMenu>|<xref:System.Windows.Forms.MenuStrip>|  
|コマンド|<xref:System.Windows.Forms.ToolBar>|<xref:System.Windows.Forms.ToolStrip>|  
||<xref:System.Windows.Forms.StatusBar>|<xref:System.Windows.Forms.StatusStrip>|  
|フォームのレイアウト|<xref:System.Windows.Forms.Splitter>|<xref:System.Windows.Forms.SplitContainer>|  
  
## <a name="see-also"></a>関連項目

- [Windows フォームで使用するコントロール](controls-to-use-on-windows-forms.md)
- [.NET Framework を使用したカスタム Windows フォーム コントロールの開発](developing-custom-windows-forms-controls.md)
