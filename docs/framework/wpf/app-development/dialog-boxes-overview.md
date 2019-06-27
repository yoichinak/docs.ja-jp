---
title: ダイアログ ボックスの概要
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- modeless dialog boxes [WPF]
- dialog boxes [WPF]
- message boxes [WPF]
- modal dialog boxes [WPF]
ms.assetid: 0d23d544-a393-4a02-a3aa-d8cd5d3d6511
ms.openlocfilehash: 8008feb91a72353a74a647cf79bcecbf7023f962
ms.sourcegitcommit: 52e588dc2ee74d484cd07ac60076be25cbf777ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/27/2019
ms.locfileid: "67410559"
---
# <a name="dialog-boxes-overview"></a>ダイアログ ボックスの概要
スタンドアロン アプリケーションは、メインのデータをアプリケーションが動作し、使用してデータを処理する機能を公開しますが両方が表示されるメイン ウィンドウを通常がある[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]メニュー バー、ツールバー、およびステータス バーなどのメカニズムです。 重要なアプリケーションは、次のようなことをするための追加のウィンドウを表示することもあります。  
  
- 固有の情報をユーザーに表示する。  
  
- ユーザーから情報を収集する。  
  
- 情報の表示と収集の両方を行う。  
  
 これらの種類のウィンドウと呼ばれる *ダイアログ ボックス*、し、2 種類があります: モーダルとモードレスです。  
  
 A*モーダル*関数には、ユーザーに続行から追加のデータが必要がある場合、関数によってダイアログ ボックスが表示されます。 機能は、モーダル ダイアログ ボックスに依存してデータを収集するため、モーダル ダイアログ ボックスが開いている間、ユーザーはアプリケーション内の他のウィンドウをアクティブ化することはできません。 ほとんどの場合、モーダル ダイアログ ボックスにより、ユーザーを押すことによって、モーダル ダイアログ ボックスを終了するときに通知する、 **OK**または**キャンセル**ボタン。 キーを押して、 **OK**ボタンは、ユーザーがデータを入力し、関数がそのデータの処理を続行する必要があることを示します。 キーを押して、**キャンセル**ボタンは、ユーザーが、関数の実行を停止することを示します。 モーダル ダイアログ ボックスの最も一般的な例は、データを開く、保存する、および印刷するために表示されます。  
  
 A*モードレス*ダイアログ ボックスで、その一方で、できないユーザーを開いているときに、他のウィンドウをアクティブ化します。 たとえば、ユーザーがドキュメント内の特定の単語の出現箇所を検索する場合、メイン ウィンドウは、多くの場合、ダイアログ ボックスを開いて、検索する単語をユーザーに尋ねます。 しかし、単語の検索中もユーザーはドキュメントを編集できるため、ダイアログ ボックスがモーダルである必要はありません。 モードレス ダイアログ ボックスは、少なくとも、**閉じます**をダイアログ ボックスを閉じるボタンをクリックしなどの特定の機能を実行するその他のボタンを提供することがあります、**次を検索**ボタン、[次へ] を検索する単語が単語の検索の検索条件に一致します。  
  
 Windows Presentation Foundation (WPF) ダイアログ ボックスに、メッセージ ボックス、コモン ダイアログ ボックスでは、カスタム ダイアログ ボックスなどのいくつかの種類を作成することができます。 このトピックでは、それぞれ、[ダイアログ ボックスのサンプル](https://go.microsoft.com/fwlink/?LinkID=159984)一致する例を示します。  

<a name="Message_Boxes"></a>   
## <a name="message-boxes"></a>メッセージ ボックス  
 A*メッセージ ボックス*テキストの情報を表示し、ユーザーがボタンで意思決定できるようにするために使用できるダイアログ ボックスです。 次の図は、テキスト情報と質問を表示して、ユーザーが質問に回答するための 3 つのボタンを表示するメッセージ ボックスを示しています。  
  
 ![アプリケーションの前に、ドキュメントに変更を保存するかどうかたずねるワード プロセッサ ダイアログ ボックスを閉じます。](./media/dialog-boxes-overview/word-processor-dialog.png)  
  
 使用するメッセージ ボックスを作成する、<xref:System.Windows.MessageBox>クラス。 <xref:System.Windows.MessageBox> メッセージ ボックスのテキスト、タイトル、アイコン、および、次のようなコードを使用して、ボタンを構成できます。  
  
 [!code-csharp[DialogBoxesOverviewSnippets#MsgBoxConfigureCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/CSharp/Window1.xaml.cs#msgboxconfigurecodebehind)]
 [!code-vb[DialogBoxesOverviewSnippets#MsgBoxConfigureCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/VisualBasic/window1.xaml.vb#msgboxconfigurecodebehind)]  
  
 メッセージ ボックスを表示するを呼び出す、 `static` <xref:System.Windows.MessageBox.Show%2A>メソッドを次のコードに示されています。  
  
 [!code-csharp[DialogBoxesOverviewSnippets#MsgBoxShowCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/CSharp/Window1.xaml.cs#msgboxshowcodebehind)]
 [!code-vb[DialogBoxesOverviewSnippets#MsgBoxShowCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/VisualBasic/window1.xaml.vb#msgboxshowcodebehind)]  
  
 メッセージ ボックスを表示するコードで、ユーザーの決定 (どのボタンが押されたか) を検出して処理する必要があるときには、コードは、次のコードに示されているように、メッセージ ボックスの結果を検査できます。  
  
 [!code-csharp[DialogBoxesOverviewSnippets#MsgBoxShowAndResultCODEBEHIND1](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/CSharp/Window1.xaml.cs#msgboxshowandresultcodebehind1)]
 [!code-vb[DialogBoxesOverviewSnippets#MsgBoxShowAndResultCODEBEHIND1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/VisualBasic/window1.xaml.vb#msgboxshowandresultcodebehind1)]  
  
 メッセージ ボックスの使用の詳細については、次を参照してください。 <xref:System.Windows.MessageBox>、[メッセージ ボックスのサンプル](https://go.microsoft.com/fwlink/?LinkID=160023)、および[ダイアログ ボックスのサンプル](https://go.microsoft.com/fwlink/?LinkID=159984)します。  
  
 <xref:System.Windows.MessageBox>簡単なダイアログ ボックス ユーザー エクスペリエンスを使用する利点を提供できます<xref:System.Windows.MessageBox>が部分信頼セキュリティ サンド ボックス内で実行されるアプリケーションで表示できるウィンドウの唯一の種類 (を参照してください[セキュリティ](../security-wpf.md)) など[!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)]します。  
  
 ほとんどのダイアログ ボックスは、テキスト、選択 (チェック ボックス)、相互に排他的な選択 (オプション ボタン)、リスト選択 (リスト ボックス、コンボ ボックス、ドロップダウン リスト ボックス) など、メッセージ ボックスの結果よりも複雑なデータを表示し、収集します。 、これらの Windows Presentation Foundation (WPF) はいくつかのコモン ダイアログ ボックスを提供し、いずれかの使用は完全な信頼で実行されているアプリケーションに制限されますが、独自のダイアログ ボックスを作成することができます。  
  
<a name="Common_Dialogs"></a>   
## <a name="common-dialog-boxes"></a>コモン ダイアログ ボックス  
 [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] は、ファイルを開く、ファイルを保存する、印刷するためのダイアログ ボックスなど、すべてのアプリケーションに共通の、さまざまな再利用可能なダイアログ ボックスを実装します。 これらのダイアログ ボックスはオペレーティング システムによって実装されるため、そのオペレーティング システム上で実行するすべてのアプリケーション間で共有でき、ユーザー エクスペリエンスの一貫性を保つことができます。ユーザーが 1 つのアプリケーションで、オペレーティング システムによって提供されるダイアログ ボックスの使用に慣れると、他のアプリケーションでも、そのダイアログ ボックスの使用法を学ぶ必要はありません。 これらのダイアログ ボックスはすべてのアプリケーションで使用できる、一貫したユーザー エクスペリエンスを提供するのに役立つ、ために、これらと呼ばれます。*コモン ダイアログ ボックス*します。  
  
 Windows Presentation Foundation (WPF) で、開いているファイルをカプセル化しファイルを保存印刷コモン ダイアログ ボックスしそれらがスタンドアロン アプリケーションで使用するため、マネージ クラスを公開します。 このトピックでは、それぞれの概要を簡単に説明します。  
  
<a name="Open_File_Dialog"></a>   
### <a name="open-file-dialog"></a>ファイル ダイアログを開きます  
 [ファイルを開く] ダイアログ ボックスは、次の図に示されているように、開くファイルの名前を取得するために、ファイルを開く機能によって使用されます。  
  
 ![ファイルを取得する場所を示す [開く] ダイアログ ボックス。](./media/dialog-boxes-overview/open-file-dialog-box.png)  
  
 一般的なファイルを開く ダイアログ ボックスとして実装されている、<xref:Microsoft.Win32.OpenFileDialog>クラスし、は、<xref:Microsoft.Win32>名前空間。 次のコードは、[ファイルを開く] ダイアログ ボックスの作成、構成、および表示の方法と、結果を処理する方法を示しています。  
  
 [!code-csharp[DialogBoxesOverviewSnippets#OpenFileDialogBoxCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/CSharp/Window1.xaml.cs#openfiledialogboxcodebehind)]
 [!code-vb[DialogBoxesOverviewSnippets#OpenFileDialogBoxCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/VisualBasic/window1.xaml.vb#openfiledialogboxcodebehind)]  
  
 ファイルを開く ダイアログ ボックスの詳細については、次を参照してください。<xref:Microsoft.Win32.OpenFileDialog?displayProperty=nameWithType>します。  
  
> [!NOTE]
>  <xref:Microsoft.Win32.OpenFileDialog> 部分信頼で実行しているアプリケーションに安全にファイル名を取得する使用できます (を参照してください[セキュリティ](../security-wpf.md))。  
  
<a name="Save_File_Dialog"></a>   
### <a name="save-file-dialog-box"></a>[ファイルの保存] ダイアログ ボックス  
 [ファイルの保存] ダイアログ ボックスは、次の図に示されているように、保存するファイルの名前を取得するために、ファイルを保存する機能によって使用されます。  
  
 ![名前を付けて保存 ダイアログ ボックス、ファイルを保存する場所を示すです。](./media/dialog-boxes-overview/save-file-dialog-box.png)  
  
 一般的な保存ファイル ダイアログ ボックスとして実装されて、<xref:Microsoft.Win32.SaveFileDialog>クラスし、は、<xref:Microsoft.Win32>名前空間。 次のコードは、[ファイルを開く] ダイアログ ボックスの作成、構成、および表示の方法と、結果を処理する方法を示しています。  
  
 [!code-csharp[DialogBoxesOverviewSnippets#SaveFileDialogBoxCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/CSharp/Window1.xaml.cs#savefiledialogboxcodebehind)]
 [!code-vb[DialogBoxesOverviewSnippets#SaveFileDialogBoxCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/VisualBasic/window1.xaml.vb#savefiledialogboxcodebehind)]  
  
 詳細については、保存ファイル ダイアログ ボックスを参照してください<xref:Microsoft.Win32.SaveFileDialog?displayProperty=nameWithType>します。  
  
<a name="Print_Dialog"></a>   
### <a name="print-dialog-box"></a>[印刷] ダイアログ ボックス

次の図に示されているように、[印刷] ダイアログ ボックスは、ユーザーがデータを印刷するプリンターを選択し、構成するために、印刷機能によって使用されます。  
  
![印刷ダイアログ ボックスのスクリーン ショット。](./media/dialog-boxes-overview/print-data-dialog-box.png)  
  
一般的な印刷ダイアログ ボックスとして実装されて、<xref:System.Windows.Controls.PrintDialog>クラスし、は、<xref:System.Windows.Controls>名前空間。 次のコードは、[印刷] ダイアログ ボックスの作成、構成、および表示の方法を示しています。  
  
 [!code-csharp[DialogBoxesOverviewSnippets#PrintDialogBoxCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/CSharp/Window1.xaml.cs#printdialogboxcodebehind)]
 [!code-vb[DialogBoxesOverviewSnippets#PrintDialogBoxCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/VisualBasic/window1.xaml.vb#printdialogboxcodebehind)]  
  
 [印刷] ダイアログ ボックスの詳細については、次を参照してください。<xref:System.Windows.Controls.PrintDialog?displayProperty=nameWithType>します。 WPF での印刷の詳細については、次を参照してください。[印刷の概要](../advanced/printing-overview.md)します。  
  
<a name="Custom_Dialog_Boxes"></a>   
## <a name="custom-dialog-boxes"></a>カスタム ダイアログ ボックス

コモン ダイアログ ボックスは便利であり、可能なときにはコモン ダイアログ ボックスを使用する必要がありますが、ドメイン固有のダイアログ ボックスの要件はサポートしていません。 このような場合は、独自のダイアログ ボックスを作成する必要があります。 これから説明するように、ダイアログ ボックスは、特殊な動作を持つウィンドウです。 <xref:System.Windows.Window> これらの動作を実装し、その結果を使用する<xref:System.Windows.Window>カスタムのモーダルとモードレスのダイアログ ボックスを作成します。  
  
<a name="Creating_a_Modal_Custom_Dialog_Box"></a>   
### <a name="creating-a-modal-custom-dialog-box"></a>カスタムのモーダル ダイアログ ボックスを作成します。

このトピックでは、使用する方法を示します<xref:System.Windows.Window>一般的なモーダル ダイアログ ボックスの実装を作成するを使用して、 `Margins`  ダイアログ ボックスを例として (を参照してください[ダイアログ ボックスのサンプル](https://go.microsoft.com/fwlink/?LinkID=159984))。 `Margins`  ダイアログ ボックスは次の図に示します。  
  
 ![左余白、上余白、右の余白および下余白を定義するフィールドの余白 ダイアログ ボックス。](./media/dialog-boxes-overview/margin-size-dialog-box.png)  
  
#### <a name="configuring-a-modal-dialog-box"></a>モーダル ダイアログ ボックスを構成します。

一般的なダイアログ ボックスのユーザー インターフェイスには、次の項目が含まれます。  
  
- 必要なデータを収集するために必要なさまざまなコントロール。  
  
- **OK**ユーザーがクリックすると、関数に戻り、ダイアログ ボックスを閉じるし、処理を続行ボタンをクリックします。  
  
- A**キャンセル**クリックするダイアログ ボックスを閉じるし、関数の処理を停止するボタンをクリックします。  
  
- A**閉じる**タイトル バーにボタンをクリックします。  
  
- アイコン。  
  
- **最小限に抑える**、**最大化**、および**復元**ボタン。  
  
- A**システム**メニューを最小限に抑える、最大化、復元、およびダイアログ ボックスを閉じます。  
  
- 上と、ダイアログ ボックスを開いたウィンドウの中央に位置します。  
  
- 便利な既定サイズをユーザーに提供して、ダイアログ ボックスが小さすぎることを防ぐために可能なサイズを変更する権限です。 これは、既定値と最小寸法の両方を設定することが必要です。  
  
- 原因となるキーボード ショートカットとして、ESC キー、**キャンセル** ボタンを押します。 設定して、これを行う、<xref:System.Windows.Controls.Button.IsCancel%2A>のプロパティ、**キャンセル**ボタン`true`します。  
  
- ENTER (または RETURN) キーとして持つキーボード ショートカット、 **OK**  ボタンを押します。 設定して、これを行う、<xref:System.Windows.Controls.Button.IsDefault%2A>のプロパティ、 **OK**ボタン`true`します。  
  
次のコードは、この構成の例を示しています。  
  
[!code-xaml[MarginsDialogBox XAML file](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml?range=1-16,106-112)]  

[!code-csharp[MarginsDialogBox C# code-behind](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml.cs?range=1-12,67-68)]
[!code-vb[MarginsDialogBox VB code-behind](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MarginsDialogBox.xaml.vb?range=1-11,61-62)]  
  
ダイアログ ボックスのユーザー エクスペリエンスは、ダイアログ ボックスを開くウィンドウのメニュー バーにも及びます。 メニュー項目が、機能の続行には、ダイアログ ボックスでのユーザーの操作を必要とする機能を実行するときには、次に示されているように、その機能のメニュー項目の見出しに省略記号を付けます。  
  
[!code-xaml[Menu bar of MainWindow.Xaml file](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml#L26-L27)]  
  
メニュー項目が、[バージョン情報] ダイアログ ボックスなど、ユーザーの操作を必要としないダイアログ ボックスを表示する機能を実行するときには、省略記号は必要ありません。  
  
#### <a name="opening-a-modal-dialog-box"></a>モーダル ダイアログ ボックスを開く

ダイアログ ボックスは、通常、ワード プロセッサでドキュメントの余白を設定するなど、ドメイン固有の機能を実行するためにユーザーがメニュー項目を選択した結果として表示されます。 ウィンドウをダイアログ ボックスとして表示するのは、通常のウィンドウを表示するのと同様ですが、ダイアログ ボックス固有の追加の構成が必要です。 ダイアログ ボックスのインスタンス化、構成、および開くプロセスの全体を、次のコードに示します。  
  
[!code-csharp[Opening a modal dialog box](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml.cs?range=1-11,78-88,193-195)]
[!code-vb[Opening a modal dialog box](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MainWindow.xaml.vb?range=1-9,58-67,130-132)]  

ここでは、コードは、ダイアログ ボックスに既定の情報 (現在の余白) を渡します。 また、設定、 <xref:System.Windows.Window.Owner%2A?displayProperty=nameWithType>  ダイアログ ボックスが表示されているウィンドウへの参照を持つプロパティです。 一般に、すべてのダイアログ ボックスに共通するウィンドウの状態関連動作を提供するために、ダイアログ ボックスの所有者を必ず設定する必要があります (詳細については、「[WPF ウィンドウの概要](wpf-windows-overview.md)」を参照してください)。

> [!NOTE]
> ダイアログ ボックスのユーザー インターフェイス (UI) オートメーションをサポートするために所有者を指定する必要があります (を参照してください[UI オートメーションの概要](../../ui-automation/ui-automation-overview.md))。

呼び出しでモーダルとして表示されます ダイアログ ボックスを構成したら、<xref:System.Windows.Window.ShowDialog%2A>メソッド。  
  
#### <a name="validating-user-provided-data"></a>ユーザー指定のデータの検証

ダイアログ ボックスが開かれ、ユーザーが必要なデータを指定すると、ダイアログ ボックスは、指定されたデータが有効であることを確認する必要があります。これは、次のような理由からです。  
  
- セキュリティの観点から、すべての入力を検証する必要があります。  
  
- ドメイン固有の観点から、データの検証は、誤ったデータがコードによって処理されて、例外がスローされるのを防ぎます。  
  
- ユーザー エクスペリエンスの観点から、ダイアログ ボックスは、入力したデータが無効であることを示すことによって、ユーザーを支援できます。  
  
- パフォーマンスの観点から、多層アプリケーションでのデータの検証は、特に、アプリケーションが Web サービスまたはサーバーベースのデータベースで構成される場合、クライアント層とアプリケーション層の間のラウンド トリップの回数を減らすことができます。  

WPF でバインドされたコントロールを検証するには、検証規則を定義し、バインドに関連付ける必要があります。 検証規則はから派生したカスタム クラス<xref:System.Windows.Controls.ValidationRule>します。 次の例では、検証規則、 `MarginValidationRule`、バインドされている値は、ことをチェックする、<xref:System.Double>と、指定した範囲内にあります。  

[!code-csharp[Margin validation rules](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginValidationRule.cs)]
[!code-vb[Margin validation rules](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MarginValidationRule.vb)]  

このコードは、オーバーライドすることで、検証規則の検証ロジックを実装、<xref:System.Windows.Controls.ValidationRule.Validate%2A>メソッドでは、データを検証し、適切な返します<xref:System.Windows.Controls.ValidationResult>します。  

検証規則をバインド コントロールに関連付けるには、次のマークアップを使用します。  
  
[!code-xaml[Associating a validation rule with a control](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml?range=1-16,57-68,111-112)]

検証規則が関連付けられていると、WPF は自動的に適用、バインドされたコントロールにデータが入力されます。 コントロールに無効なデータが含まれている場合、WPF は次の図に示すように、無効なコントロールでは、周囲に赤い境界線を表示します。  
  
![無効な左余白の値を囲む赤い境界線付きの余白 ダイアログ ボックス。](./media/dialog-boxes-overview/invalid-left-margin-dialog.png)  

有効なデータを入力するまで、WPF は、無効なコントロールにユーザーを制限しません。 これは、ダイアログ ボックスとして適切な動作です。データが有効かどうかにかかわらず、ユーザーはダイアログ ボックス内のコントロールを自由に移動できる必要があります。 ユーザーは、無効なデータとキーを押して入力してください。 ただし、これは意味、 **OK**ボタンをクリックします。 このため、コードも必要があるダイアログ内のすべてのコントロールを検証するときにボックス、 **[ok]** ボタンを処理することによって、<xref:System.Windows.Controls.Primitives.ButtonBase.Click>イベント。  
  
[!code-csharp[Validating all controls in a dialog box](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml.cs?range=1-8,26-29,33-68)]
[!code-vb[Validating all controls in a dialog box](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MarginsDialogBox.xaml.vb?range=1-8,27-29,33-62)]  

このコードは、ウィンドウ上のすべての依存関係オブジェクトを列挙しますと、いずれかが有効でない場合 (によって返される<xref:System.Windows.Controls.Validation.GetHasError%2A>、無効なコントロールがフォーカスを取得、`IsValid`メソッドを返します。 `false`、ウィンドウは無効とみなされるとします。  
  
ダイアログ ボックスが有効な場合は、安全に閉じて、戻ることができます。 復帰プロセスの一環として、呼び出し元の機能に結果を返す必要があります。  
  
#### <a name="setting-the-modal-dialog-result"></a>モーダル ダイアログの結果を設定

使用してダイアログ ボックスを開く<xref:System.Windows.Window.ShowDialog%2A>メソッドを呼び出すようには、基本的に: を使用して、ダイアログ ボックスを開いたコード<xref:System.Windows.Window.ShowDialog%2A>まで待機<xref:System.Windows.Window.ShowDialog%2A>を返します。 ときに<xref:System.Windows.Window.ShowDialog%2A>返します、かどうかに基づくした処理を続行するか、処理を停止するかどうかを決定する必要がある呼び出し元コードには、ユーザーが押した、 **OK**ボタンまたは**キャンセル**ボタン。 として、ユーザーの選択肢を返す必要があります ダイアログ ボックスをこの決定を容易にする、<xref:System.Boolean>から返される値、<xref:System.Windows.Window.ShowDialog%2A>メソッド。  

ときに、 **OK**ボタンがクリックされた<xref:System.Windows.Window.ShowDialog%2A>返す必要があります`true`します。 これを設定することで実現されます、<xref:System.Windows.Window.DialogResult%2A>プロパティのダイアログ ボックス、 **OK**ボタンがクリックされました。  

[!code-csharp[Responding to the OK button](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml.cs?range=1-8,25-27,32-33,67-68)]
[!code-vb[Responding to the OK button](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MarginsDialogBox.xaml.vb?range=1-8,27,31-33,61-62)]  

その設定に注意してください、<xref:System.Windows.Window.DialogResult%2A>プロパティで明示的に呼び出す必要が自動的に閉じるウィンドウの指定も<xref:System.Windows.Window.Close%2A>します。  
  
ときに、**キャンセル**ボタンがクリックされた<xref:System.Windows.Window.ShowDialog%2A>返す必要があります`false`を設定する必要があります、<xref:System.Windows.Window.DialogResult%2A>プロパティ。  
  
[!code-csharp[Responding to the Cancel button](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml.cs?range=1-8,19-24,67-68)]
[!code-vb[Responding to the Cancel button](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MarginsDialogBox.xaml.vb?range=1-8,22-25,61-62)]  

ボタンの<xref:System.Windows.Controls.Button.IsCancel%2A>プロパティに設定されて`true`か押すと、**キャンセル**ボタンか ESC キー、<xref:System.Windows.Window.DialogResult%2A>に自動的に設定されている`false`します。 次のマークアップが上記のコードで処理するために必要としない場合と同様、<xref:System.Windows.Controls.Primitives.ButtonBase.Click>イベント。  
  
[!code-xaml[Markup instead of handling the Click event](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml#L109-L109)]  

ダイアログ ボックスが自動的に返します`false`ユーザーが押すと、**閉じる**タイトル バーにボタンをクリックしてまたは選択、**閉じる**からメニュー項目、**システム**メニュー。  

#### <a name="processing-data-returned-from-a-modal-dialog-box"></a>モーダル ダイアログ ボックスから返されたデータの処理  

ときに<xref:System.Windows.Window.DialogResult%2A>設定 ダイアログ ボックスで開いた関数は、検査することによってダイアログ ボックスの結果を取得できます、<xref:System.Windows.Window.DialogResult%2A>プロパティと<xref:System.Windows.Window.ShowDialog%2A>を返します。  
  
[!code-csharp[Processing data returned from the modal dialog box](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml.cs?range=1-10,77-79,89-96,194-195)]
[!code-vb[Processing data returned from the modal dialog box](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MainWindow.xaml.vb?range=1-9,58,69-73,131-132)]

ダイアログの結果が場合`true`関数を使用して、キューとを取得し、ユーザーが提供するデータを処理します。  
  
> [!NOTE]
> 後<xref:System.Windows.Window.ShowDialog%2A>が返されると、ダイアログ ボックスを再度開くことはできません。 代わりに、新しいインスタンスを作成する必要があります。

ダイアログの結果が場合`false`関数が適切に処理を終了する必要があります。  
  
<a name="Creating_a_Modeless_Custom_Dialog_Box"></a>   
### <a name="creating-a-modeless-custom-dialog-box"></a>モードレス カスタム ダイアログ ボックスの作成

次の図に示されている [検索] ダイアログ ボックスなどのモードレス ダイアログ ボックスは、基本的な外観はモーダル ダイアログ ボックスと同じです。  

![検索ダイアログ ボックスのスクリーン ショット。](./media/dialog-boxes-overview/find-modeless-dialog-box.png)  

しかし、次のセクションで説明するように、動作は少し異なります。  
  
#### <a name="opening-a-modeless-dialog-box"></a>モードレス ダイアログ ボックスを開く

モードレス ダイアログ ボックスが呼び出すことによって開かれる、<xref:System.Windows.Window.Show%2A>メソッド。  

[!code-xaml[XAML to define a modeless dialog box](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml#L21-L22)]  
 
[!code-csharp[Opening a modeless dialog box](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml.cs?range=1-10,65-76,194-195)]
[!code-vb[Openng a modeless dialog box](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MainWindow.xaml.vb?range=1-9,18-23,131,132)]  

異なり<xref:System.Windows.Window.ShowDialog%2A>、<xref:System.Windows.Window.Show%2A>が直ちに返されます。 その結果、呼び出し元のウィンドウは、モードレス ダイアログ ボックスが閉じられたことを知ることができず、したがって、ダイアログ ボックスの結果を確認するタイミングを判断したり、ダイアログ ボックスからデータを取得して、さらに処理したりすることができません。 代わりに、ダイアログ ボックスは、別の方法を作成して、呼び出し元のウィンドウに処理用のデータを返す必要があります。  
  
#### <a name="processing-data-returned-from-a-modeless-dialog-box"></a>モードレス ダイアログ ボックスから返されたデータの処理  

この例で、 `FindDialogBox` 1 つまたは複数の検索によって特定の頻度に検索されているテキストのメイン ウィンドウに結果を返す可能性があります。 モーダル ダイアログ ボックスと同様、モードレス ダイアログ ボックスは、プロパティを使用して結果を返すことができます。 ただし、ダイアログ ボックスを所有しているウィンドウは、それらのプロパティを確認するタイミングを知る必要があります。 これを可能にする方法の 1 つは、ダイアログ ボックスで、テキストが見つかったときに発生するイベントを実装することです。 `FindDialogBox` 実装して、`TextFoundEvent`この目的で、最初にデリゲートが必要です。  

[!code-csharp[The TextFoundEventHandler delegate](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/TextFoundEventHandler.cs)]
[!code-vb[The TextFoundEventHandler delegate](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/TextFoundEventHandler.vb)]  

使用して、`TextFoundEventHandler`デリゲート`FindDialogBox`実装、`TextFoundEvent`します。
  
[!code-csharp[The TextFound event](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/FindDialogBox.xaml.cs?range=1-17,125-126)]
[!code-vb[The TextFound event](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/FindDialogBox.xaml.vb?range=1-15,102-103)]

その結果、`Find`検索結果が見つかった場合は、イベントを発生させることができます。  
  
[!code-csharp[Raising the TextFound event](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/FindDialogBox.xaml.cs?range=1-9,50-52,91-94,124-127)]
[!code-vb[Raising the TextFound event](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/FindDialogBox.xaml.vb?range=1-9,15,60-64,102-103)]  

そのとき、所有者ウィンドウは、このイベントを登録し、処理する必要があります。

[!code-csharp[Registering and handling the event](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml.cs?range=1-10,184-195)]
[!code-vb[Registering and handling the event](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MainWindow.xaml.vb?range=1-9,126-132)]  

#### <a name="closing-a-modeless-dialog-box"></a>モードレス ダイアログ ボックスを閉じる

<xref:System.Windows.Window.DialogResult%2A>するシステムを使用して、モードレス ダイアログ ボックスを閉じることができますを設定する必要はありません、以下のメカニズムを提供します。  
  
- クリックすると、**閉じる**タイトル バーにボタンをクリックします。  
  
- Alt キーを押しながら F4 キーを押す。  
  
- 選択**閉じる**から、**システム**メニュー。  
  
または、コードを呼び出すことができます<xref:System.Windows.Window.Close%2A>ときに、**閉じる**ボタンをクリックします。  

[!code-csharp[Calling the Close method](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/FindDialogBox.xaml.cs?range=1-9,119-126)]
[!code-vb[Calling the Close method](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/FindDialogBox.xaml.vb?range=1-9,99-103)]  

## <a name="see-also"></a>関連項目

- [ポップアップの概要](../controls/popup-overview.md)
- [ダイアログ ボックスのサンプル](https://go.microsoft.com/fwlink/?LinkID=159984)
