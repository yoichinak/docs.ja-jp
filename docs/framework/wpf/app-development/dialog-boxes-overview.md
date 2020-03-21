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
ms.openlocfilehash: c98d6a45d151d4b683a21e48eaeb5f4a19eaadb1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187450"
---
# <a name="dialog-boxes-overview"></a>ダイアログ ボックスの概要
スタンドアロン アプリケーションには、通常、メイン ウィンドウがあり、アプリケーションが動作するメイン データを表示し、メニュー バー、ツール[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]バー、ステータス バーなどのメカニズムを通じてそのデータを処理する機能を公開します。 重要なアプリケーションは、次のようなことをするための追加のウィンドウを表示することもあります。  
  
- 固有の情報をユーザーに表示する。  
  
- ユーザーから情報を収集する。  
  
- 情報の表示と収集の両方を行う。  
  
 この種類のウィンドウはダイアログ*ボックス*と呼ばれ、モーダルとモードレスの 2 種類があります。  
  
 モー*ダル*ダイアログ ボックスは、関数が続行するためにユーザーからの追加データを必要とする場合に、関数によって表示されます。 機能は、モーダル ダイアログ ボックスに依存してデータを収集するため、モーダル ダイアログ ボックスが開いている間、ユーザーはアプリケーション内の他のウィンドウをアクティブ化することはできません。 ほとんどの場合、モーダル ダイアログ ボックスを使用すると、ユーザーは **[OK]** または [**キャンセル]** ボタンを押して、モーダル ダイアログ ボックスが終了したときに通知を行うことができます。 **[OK] ボタン**を押すと、ユーザーがデータを入力し、そのデータの処理を続行することを望んでいます。 **[キャンセル]** ボタンを押すと、ユーザーは関数の実行を完全に停止します。 モーダル ダイアログ ボックスの最も一般的な例は、データを開く、保存する、および印刷するために表示されます。  
  
 一方、*モードレス*ダイアログ ボックスは、ユーザーが開いている間に他のウィンドウをアクティブにすることを防ぐものではありません。 たとえば、ユーザーがドキュメント内の特定の単語の出現箇所を検索する場合、メイン ウィンドウは、多くの場合、ダイアログ ボックスを開いて、検索する単語をユーザーに尋ねます。 しかし、単語の検索中もユーザーはドキュメントを編集できるため、ダイアログ ボックスがモーダルである必要はありません。 モードレス ダイアログ ボックスには、少なくともダイアログ ボックスを閉じるには **[閉じる**] ボタンが用意されており、単語検索の検索条件に一致する次の単語を検索する [**次を検索**] ボタンなど、特定の機能を実行するための追加のボタンが用意されている場合があります。  
  
 Windows プレゼンテーションファンデーション (WPF) では、メッセージ ボックス、コモン ダイアログ ボックス、カスタム ダイアログ ボックスなど、さまざまな種類のダイアログ ボックスを作成できます。 このトピックでは、それぞれについて説明し、[ダイアログ ボックスのサンプル](https://github.com/Microsoft/WPF-Samples/tree/master/Windows/DialogBox)では、一致する例を示します。  

<a name="Message_Boxes"></a>
## <a name="message-boxes"></a>メッセージ ボックス  
 *メッセージ ボックス*は、テキスト情報を表示したり、ユーザーがボタンを使用して決定を下したりするために使用できるダイアログ ボックスです。 次の図は、テキスト情報と質問を表示して、ユーザーが質問に回答するための 3 つのボタンを表示するメッセージ ボックスを示しています。  
  
 ![アプリケーションを閉じる前に文書に対する変更を保存するかどうかを確認する [ワード プロセッサ] ダイアログ ボックス。](./media/dialog-boxes-overview/word-processor-dialog.png)  
  
 メッセージ ボックスを作成するには、 クラス<xref:System.Windows.MessageBox>を使用します。 <xref:System.Windows.MessageBox>では、次のようなコードを使用して、メッセージ ボックスのテキスト、タイトル、アイコン、およびボタンを構成できます。  
  
 [!code-csharp[DialogBoxesOverviewSnippets#MsgBoxConfigureCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/CSharp/Window1.xaml.cs#msgboxconfigurecodebehind)]
 [!code-vb[DialogBoxesOverviewSnippets#MsgBoxConfigureCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/VisualBasic/window1.xaml.vb#msgboxconfigurecodebehind)]  
  
 メッセージ ボックスを表示するには、次の`static`<xref:System.Windows.MessageBox.Show%2A>コードに示すように、メソッドを呼び出します。  
  
 [!code-csharp[DialogBoxesOverviewSnippets#MsgBoxShowCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/CSharp/Window1.xaml.cs#msgboxshowcodebehind)]
 [!code-vb[DialogBoxesOverviewSnippets#MsgBoxShowCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/VisualBasic/window1.xaml.vb#msgboxshowcodebehind)]  
  
 メッセージ ボックスを表示するコードで、ユーザーの決定 (どのボタンが押されたか) を検出して処理する必要があるときには、コードは、次のコードに示されているように、メッセージ ボックスの結果を検査できます。  
  
 [!code-csharp[DialogBoxesOverviewSnippets#MsgBoxShowAndResultCODEBEHIND1](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/CSharp/Window1.xaml.cs#msgboxshowandresultcodebehind1)]
 [!code-vb[DialogBoxesOverviewSnippets#MsgBoxShowAndResultCODEBEHIND1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/VisualBasic/window1.xaml.vb#msgboxshowandresultcodebehind1)]  
  
 メッセージ ボックスの使用方法の詳細については、「 <xref:System.Windows.MessageBox> [」を](https://github.com/Microsoft/WPF-Samples/tree/master/Windows/MessageBox)参照[してください。](https://github.com/Microsoft/WPF-Samples/tree/master/Windows/DialogBox)  
  
 単純<xref:System.Windows.MessageBox>なダイアログ ボックスのユーザー エクスペリエンスを提供する場合でも<xref:System.Windows.MessageBox>、使用の利点は、部分信頼セキュリティ サンドボックス内で実行されるアプリケーションで表示できる唯一のウィンドウです ([セキュリティ](../security-wpf.md)を参照) XAML ブラウザー アプリケーション (XAAP) など)。  
  
 ほとんどのダイアログ ボックスは、テキスト、選択 (チェック ボックス)、相互に排他的な選択 (オプション ボタン)、リスト選択 (リスト ボックス、コンボ ボックス、ドロップダウン リスト ボックス) など、メッセージ ボックスの結果よりも複雑なデータを表示し、収集します。 これらの場合、Windows プレゼンテーション ファンデーション (WPF) では、いくつかの共通ダイアログ ボックスが用意されており、独自のダイアログ ボックスを作成できます。  
  
<a name="Common_Dialogs"></a>
## <a name="common-dialog-boxes"></a>コモン ダイアログ ボックス  
 Windows では、ファイルを開く、ファイルを保存する、印刷するためのダイアログ ボックスなど、すべてのアプリケーションに共通するさまざまな再利用可能なダイアログ ボックスが実装されています。 これらのダイアログ ボックスはオペレーティング システムによって実装されるため、そのオペレーティング システム上で実行するすべてのアプリケーション間で共有でき、ユーザー エクスペリエンスの一貫性を保つことができます。ユーザーが 1 つのアプリケーションで、オペレーティング システムによって提供されるダイアログ ボックスの使用に慣れると、他のアプリケーションでも、そのダイアログ ボックスの使用法を学ぶ必要はありません。 これらのダイアログ ボックスはすべてのアプリケーションで使用でき、一貫したユーザー エクスペリエンスを提供するために役立つため、*コモン ダイアログ ボックス*と呼ばれます。  
  
 Windows プレゼンテーション ファンデーション (WPF) は、開いているファイル、ファイルの保存、および共通のダイアログ ボックスの印刷をカプセル化し、スタンドアロン アプリケーションで使用するためのマネージ クラスとして公開します。 このトピックでは、それぞれの概要を簡単に説明します。  
  
<a name="Open_File_Dialog"></a>
### <a name="open-file-dialog"></a>[ファイルを開く] ダイアログ  
 [ファイルを開く] ダイアログ ボックスは、次の図に示されているように、開くファイルの名前を取得するために、ファイルを開く機能によって使用されます。  
  
 ![ファイルを取得する場所を示す [開く] ダイアログ ボックス。](./media/dialog-boxes-overview/open-file-dialog-box.png)  
  
 共通のファイルを開くダイアログ ボックスは<xref:Microsoft.Win32.OpenFileDialog>、クラスとして実装され、名前空間<xref:Microsoft.Win32>に配置されます。 次のコードは、[ファイルを開く] ダイアログ ボックスの作成、構成、および表示の方法と、結果を処理する方法を示しています。  
  
 [!code-csharp[DialogBoxesOverviewSnippets#OpenFileDialogBoxCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/CSharp/Window1.xaml.cs#openfiledialogboxcodebehind)]
 [!code-vb[DialogBoxesOverviewSnippets#OpenFileDialogBoxCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/VisualBasic/window1.xaml.vb#openfiledialogboxcodebehind)]  
  
 [ファイルを開く] ダイアログ ボックスの<xref:Microsoft.Win32.OpenFileDialog?displayProperty=nameWithType>詳細については、「」を参照してください。  
  
> [!NOTE]
> <xref:Microsoft.Win32.OpenFileDialog>部分信頼で実行されているアプリケーションによってファイル名を安全に取得するために使用できます[(Security](../security-wpf.md)を参照)。  
  
<a name="Save_File_Dialog"></a>
### <a name="save-file-dialog-box"></a>[ファイルの保存] ダイアログ ボックス  
 [ファイルの保存] ダイアログ ボックスは、次の図に示されているように、保存するファイルの名前を取得するために、ファイルを保存する機能によって使用されます。  
  
 ![ファイルを保存する場所を示す [名前を付けて保存] ダイアログ ボックス。](./media/dialog-boxes-overview/save-file-dialog-box.png)  
  
 共通の保存ファイル ダイアログ ボックスは<xref:Microsoft.Win32.SaveFileDialog>、クラスとして実装され、名前空間に<xref:Microsoft.Win32>配置されます。 次のコードは、[ファイルを開く] ダイアログ ボックスの作成、構成、および表示の方法と、結果を処理する方法を示しています。  
  
 [!code-csharp[DialogBoxesOverviewSnippets#SaveFileDialogBoxCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/CSharp/Window1.xaml.cs#savefiledialogboxcodebehind)]
 [!code-vb[DialogBoxesOverviewSnippets#SaveFileDialogBoxCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/VisualBasic/window1.xaml.vb#savefiledialogboxcodebehind)]  
  
 [ファイルの保存] ダイアログ ボックスの詳細<xref:Microsoft.Win32.SaveFileDialog?displayProperty=nameWithType>については、「」を参照してください。  
  
<a name="Print_Dialog"></a>
### <a name="print-dialog-box"></a>[印刷] ダイアログ ボックス

次の図に示されているように、[印刷] ダイアログ ボックスは、ユーザーがデータを印刷するプリンターを選択し、構成するために、印刷機能によって使用されます。  
  
![[印刷] ダイアログ ボックスを示すスクリーンショット。](./media/dialog-boxes-overview/print-data-dialog-box.png)  
  
共通の印刷ダイアログ ボックスは<xref:System.Windows.Controls.PrintDialog>クラスとして実装され、名前空間に<xref:System.Windows.Controls>配置されます。 次のコードは、[印刷] ダイアログ ボックスの作成、構成、および表示の方法を示しています。  
  
 [!code-csharp[DialogBoxesOverviewSnippets#PrintDialogBoxCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/CSharp/Window1.xaml.cs#printdialogboxcodebehind)]
 [!code-vb[DialogBoxesOverviewSnippets#PrintDialogBoxCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/VisualBasic/window1.xaml.vb#printdialogboxcodebehind)]  
  
 印刷ダイアログ ボックスの詳細については、「」を<xref:System.Windows.Controls.PrintDialog?displayProperty=nameWithType>参照してください。 WPF での印刷の詳細については、「[印刷の概要](../advanced/printing-overview.md)」を参照してください。  
  
<a name="Custom_Dialog_Boxes"></a>
## <a name="custom-dialog-boxes"></a>カスタム ダイアログ ボックス

コモン ダイアログ ボックスは便利であり、可能なときにはコモン ダイアログ ボックスを使用する必要がありますが、ドメイン固有のダイアログ ボックスの要件はサポートしていません。 このような場合は、独自のダイアログ ボックスを作成する必要があります。 これから説明するように、ダイアログ ボックスは、特殊な動作を持つウィンドウです。 <xref:System.Windows.Window>これらの動作を実装し、その結果、カスタム モー<xref:System.Windows.Window>ダルおよびモードレス ダイアログ ボックスを作成するために使用します。  
  
<a name="Creating_a_Modal_Custom_Dialog_Box"></a>
### <a name="creating-a-modal-custom-dialog-box"></a>モーダル カスタム ダイアログ ボックスの作成

ここでは、ダイアログ ボックスを<xref:System.Windows.Window>例として使用して、標準的なモーダル ダイアログ`Margins`ボックスの実装を作成する方法を示します (「[ダイアログ ボックスのサンプル](https://github.com/Microsoft/WPF-Samples/tree/master/Windows/DialogBox)」を参照)。 ダイアログ`Margins`ボックスを次の図に示します。  
  
 ![[余白] ダイアログ ボックスで、左余白、上余白、右余白、および下余白を定義するフィールドを指定します。](./media/dialog-boxes-overview/margin-size-dialog-box.png)  
  
#### <a name="configuring-a-modal-dialog-box"></a>モーダル ダイアログ ボックスの構成

一般的なダイアログ ボックスのユーザー インターフェイスには、次の項目が含まれます。  
  
- 必要なデータを収集するために必要なさまざまなコントロール。  
  
- ユーザーがクリックしてダイアログ ボックスを閉じ、関数に戻り、処理を続行する **[OK]** ボタン。  
  
- ユーザーがクリックしてダイアログ ボックスを閉じ、関数の処理を中止する **[キャンセル]** ボタン。  
  
- タイトル バーの**閉じる**ボタン。  
  
- アイコン。  
  
- **最小化**、**最大化**、および**復元**の各ボタン。  
  
- ダイアログ ボックスを最小化、最大化、復元、および閉じる**システム**メニュー。  
  
- ダイアログ ボックスを開いたウィンドウの上および中央の位置。  
  
- ダイアログ ボックスが小さすぎるのを防ぐために可能な場合にサイズを変更する機能と、ユーザーに便利な既定のサイズを提供する機能。 これには、既定の寸法と最小の寸法の両方を設定する必要があります。  
  
- Esc キーを押すと、**キャンセル**ボタンが押されます。 この操作を行うには、[<xref:System.Windows.Controls.Button.IsCancel%2A>**キャンセル]** ボタンのプロパティ`true`を に設定します。  
  
- ENTER キー (RETURN キー) をキーボード ショートカットとして押すと **、[OK]** ボタンが押されます。 これは、 **[** OK <xref:System.Windows.Controls.Button.IsDefault%2A> ] ボタン`true`のプロパティを設定することによって行います。  
  
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

ここでは、既定の情報 (現在の余白) をダイアログ ボックスに渡します。 また、ダイアログ<xref:System.Windows.Window.Owner%2A?displayProperty=nameWithType>ボックスを表示しているウィンドウへの参照を使用してプロパティを設定します。 一般に、すべてのダイアログ ボックスに共通するウィンドウ状態に関連する動作を提供するには、ダイアログ ボックスの所有者を常に設定する必要があります (詳細については[、「WPF Windows の概要](wpf-windows-overview.md)」を参照してください)。

> [!NOTE]
> ダイアログ ボックスのユーザー インターフェイス (UI) オートメーションをサポートする所有者を指定する必要があります[(「UI オートメーションの概要](../../ui-automation/ui-automation-overview.md)」を参照)。

ダイアログ ボックスを構成すると、メソッドを呼び出すことによってモーダル<xref:System.Windows.Window.ShowDialog%2A>に表示されます。  
  
#### <a name="validating-user-provided-data"></a>ユーザーが指定したデータの検証

ダイアログ ボックスが開かれ、ユーザーが必要なデータを指定すると、ダイアログ ボックスは、指定されたデータが有効であることを確認する必要があります。これは、次のような理由からです。  
  
- セキュリティの観点から、すべての入力を検証する必要があります。  
  
- ドメイン固有の観点から、データの検証は、誤ったデータがコードによって処理されて、例外がスローされるのを防ぎます。  
  
- ユーザー エクスペリエンスの観点から、ダイアログ ボックスは、入力したデータが無効であることを示すことによって、ユーザーを支援できます。  
  
- パフォーマンスの観点から、多層アプリケーションでのデータの検証は、特に、アプリケーションが Web サービスまたはサーバーベースのデータベースで構成される場合、クライアント層とアプリケーション層の間のラウンド トリップの回数を減らすことができます。  

WPF でバインドされたコントロールを検証するには、検証規則を定義し、バインドに関連付ける必要があります。 検証規則は、 から<xref:System.Windows.Controls.ValidationRule>派生するカスタム クラスです。 次の例は、`MarginValidationRule`バインドされた値が<xref:System.Double>指定された範囲内にあるかどうかをチェックする検証規則を示しています。  

[!code-csharp[Margin validation rules](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginValidationRule.cs)]
[!code-vb[Margin validation rules](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MarginValidationRule.vb)]  

このコードでは、検証規則の検証ロジックは、<xref:System.Windows.Controls.ValidationRule.Validate%2A>メソッドをオーバーライドして実装され、メソッドはデータを検証し、適切な<xref:System.Windows.Controls.ValidationResult>を返します。  

検証規則をバインド コントロールに関連付けるには、次のマークアップを使用します。  
  
[!code-xaml[Associating a validation rule with a control](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml?range=1-16,57-68,111-112)]

検証規則が関連付けられると、バインドされたコントロールにデータが入力されると、WPF によって自動的に適用されます。 コントロールに無効なデータが含まれている場合、次の図に示すように、無効なコントロールの周りに赤い枠線が表示されます。  
  
![無効な左余白の値の周りに赤い枠線が表示された [余白] ダイアログ ボックス](./media/dialog-boxes-overview/invalid-left-margin-dialog.png)  

WPF では、ユーザーが有効なデータを入力するまで、無効なコントロールにユーザーを制限しません。 これは、ダイアログ ボックスとして適切な動作です。データが有効かどうかにかかわらず、ユーザーはダイアログ ボックス内のコントロールを自由に移動できる必要があります。 ただし、これはユーザーが無効なデータを入力して **[OK]ボタン**を押すことができるという意味です。 このため、<xref:System.Windows.Controls.Primitives.ButtonBase.Click>イベントを処理して **[OK]** ボタンを押したときに、ダイアログ ボックス内のすべてのコントロールを検証する必要もあります。  
  
[!code-csharp[Validating all controls in a dialog box](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml.cs?range=1-8,26-29,33-68)]
[!code-vb[Validating all controls in a dialog box](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MarginsDialogBox.xaml.vb?range=1-8,27-29,33-62)]  

このコードは、ウィンドウ上のすべての依存関係オブジェクトを列挙し、無効な場合 (無効な<xref:System.Windows.Controls.Validation.GetHasError%2A>コントロールがフォーカスを取得し、`IsValid`メソッドが返`false`し、ウィンドウが無効と見なされます)。  
  
ダイアログ ボックスが有効な場合は、安全に閉じて、戻ることができます。 復帰プロセスの一環として、呼び出し元の機能に結果を返す必要があります。  
  
#### <a name="setting-the-modal-dialog-result"></a>モーダル ダイアログ結果の設定

を使用して<xref:System.Windows.Window.ShowDialog%2A>ダイアログ ボックスを開くことは、メソッドを呼び出すのと基本的に似<xref:System.Windows.Window.ShowDialog%2A>ています:<xref:System.Windows.Window.ShowDialog%2A>戻るまで待機を使用してダイアログ ボックスを開いたコード。 返<xref:System.Windows.Window.ShowDialog%2A>されるときに、呼び出したコードは、ユーザーが **[OK]** ボタンを押したか **、[キャンセル]** ボタンを押したかに基づいて、処理を続行するか停止するかを決定する必要があります。 この決定を容易にするために、ダイアログ ボックスは、メソッドから返される値としてユーザー<xref:System.Boolean>の選択を<xref:System.Windows.Window.ShowDialog%2A>返す必要があります。  

**[OK]** ボタンをクリックすると<xref:System.Windows.Window.ShowDialog%2A>、`true`が戻ります。 これは **、[OK]** ボタン<xref:System.Windows.Window.DialogResult%2A>をクリックしたときにダイアログ ボックスのプロパティを設定することで実現されます。  

[!code-csharp[Responding to the OK button](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml.cs?range=1-8,25-27,32-33,67-68)]
[!code-vb[Responding to the OK button](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MarginsDialogBox.xaml.vb?range=1-8,27,31-33,61-62)]  

このプロパティを<xref:System.Windows.Window.DialogResult%2A>設定すると、ウィンドウが自動的に閉じ、明示的に呼び出す<xref:System.Windows.Window.Close%2A>必要が軽減されることに注意してください。  
  
**[キャンセル**] ボタンをクリックすると<xref:System.Windows.Window.ShowDialog%2A>、`false`が返されます<xref:System.Windows.Window.DialogResult%2A>。  
  
[!code-csharp[Responding to the Cancel button](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml.cs?range=1-8,19-24,67-68)]
[!code-vb[Responding to the Cancel button](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MarginsDialogBox.xaml.vb?range=1-8,22-25,61-62)]  

ボタン<xref:System.Windows.Controls.Button.IsCancel%2A>のプロパティが`true`に設定され、ユーザーが**キャンセル**ボタンまたは Esc キーを押すと、<xref:System.Windows.Window.DialogResult%2A>自動的に に`false`に 設定されます。 次のマークアップは、<xref:System.Windows.Controls.Primitives.ButtonBase.Click>前のコードと同じ結果になり、イベントを処理する必要はありません。  
  
[!code-xaml[Markup instead of handling the Click event](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml#L109-L109)]  

ユーザーがタイトル バー`false`の **[閉じる**] ボタンを押すか、[**システム**] メニューの [**閉じる**] メニュー項目をクリックすると、ダイアログ ボックスが自動的に表示されます。  

#### <a name="processing-data-returned-from-a-modal-dialog-box"></a>モーダル ダイアログ ボックスから返されるデータの処理  

ダイアログ<xref:System.Windows.Window.DialogResult%2A>ボックスで設定すると、ダイアログ ボックスを開いた関数は、プロパティが返されたときに<xref:System.Windows.Window.DialogResult%2A><xref:System.Windows.Window.ShowDialog%2A>検査を行うことで、ダイアログ ボックスの結果を取得できます。  
  
[!code-csharp[Processing data returned from the modal dialog box](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml.cs?range=1-10,77-79,89-96,194-195)]
[!code-vb[Processing data returned from the modal dialog box](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MainWindow.xaml.vb?range=1-9,58,69-73,131-132)]

ダイアログの結果が`true`の場合、関数は、ユーザーが提供するデータを取得して処理するためのキューとしてそれを使用します。  
  
> [!NOTE]
> 戻<xref:System.Windows.Window.ShowDialog%2A>った後で、ダイアログ ボックスを再度開くことはできません。 代わりに、新しいインスタンスを作成する必要があります。

ダイアログの結果が`false`の場合、関数は処理を適切に終了する必要があります。  
  
<a name="Creating_a_Modeless_Custom_Dialog_Box"></a>
### <a name="creating-a-modeless-custom-dialog-box"></a>モードレスカスタム ダイアログ ボックスの作成

次の図に示されている [検索] ダイアログ ボックスなどのモードレス ダイアログ ボックスは、基本的な外観はモーダル ダイアログ ボックスと同じです。  

![[検索] ダイアログ ボックスを示すスクリーンショット。](./media/dialog-boxes-overview/find-modeless-dialog-box.png)  

しかし、次のセクションで説明するように、動作は少し異なります。  
  
#### <a name="opening-a-modeless-dialog-box"></a>モードレス ダイアログ ボックスを開く

メソッドを呼び出すと、モードレス<xref:System.Windows.Window.Show%2A>ダイアログ ボックスが開きます。  

[!code-xaml[XAML to define a modeless dialog box](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml#L21-L22)]  

[!code-csharp[Opening a modeless dialog box](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml.cs?range=1-10,65-76,194-195)]
[!code-vb[Openng a modeless dialog box](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MainWindow.xaml.vb?range=1-9,18-23,131,132)]  

と<xref:System.Windows.Window.ShowDialog%2A>は<xref:System.Windows.Window.Show%2A>異なり、 はすぐに戻ります。 その結果、呼び出し元のウィンドウは、モードレス ダイアログ ボックスが閉じられたことを知ることができず、したがって、ダイアログ ボックスの結果を確認するタイミングを判断したり、ダイアログ ボックスからデータを取得して、さらに処理したりすることができません。 代わりに、ダイアログ ボックスは、別の方法を作成して、呼び出し元のウィンドウに処理用のデータを返す必要があります。  
  
#### <a name="processing-data-returned-from-a-modeless-dialog-box"></a>モードレス ダイアログ ボックスから返されたデータの処理  

この例では、`FindDialogBox`は、特定の頻度を指定せずに検索されるテキストに応じて、1 つ以上の検索結果をメイン ウィンドウに返します。 モーダル ダイアログ ボックスと同様、モードレス ダイアログ ボックスは、プロパティを使用して結果を返すことができます。 ただし、ダイアログ ボックスを所有しているウィンドウは、それらのプロパティを確認するタイミングを知る必要があります。 これを可能にする方法の 1 つは、ダイアログ ボックスで、テキストが見つかったときに発生するイベントを実装することです。 `FindDialogBox`は、この`TextFoundEvent`目的のために実装します。  

[!code-csharp[The TextFoundEventHandler delegate](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/TextFoundEventHandler.cs)]
[!code-vb[The TextFoundEventHandler delegate](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/TextFoundEventHandler.vb)]  

デリゲートを`TextFoundEventHandler`使用して`FindDialogBox`、 を`TextFoundEvent`実装します。
  
[!code-csharp[The TextFound event](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/FindDialogBox.xaml.cs?range=1-17,125-126)]
[!code-vb[The TextFound event](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/FindDialogBox.xaml.vb?range=1-15,102-103)]

結果として、`Find`検索結果が見つかったときにイベントを発生させることができます。  
  
[!code-csharp[Raising the TextFound event](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/FindDialogBox.xaml.cs?range=1-9,50-52,91-94,124-127)]
[!code-vb[Raising the TextFound event](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/FindDialogBox.xaml.vb?range=1-9,15,60-64,102-103)]  

そのとき、所有者ウィンドウは、このイベントを登録し、処理する必要があります。

[!code-csharp[Registering and handling the event](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml.cs?range=1-10,184-195)]
[!code-vb[Registering and handling the event](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MainWindow.xaml.vb?range=1-9,126-132)]  

#### <a name="closing-a-modeless-dialog-box"></a>モードレス ダイアログ ボックスを閉じる

設定<xref:System.Windows.Window.DialogResult%2A>する必要がないため、システム提供機構を使用してモードレスダイアログを閉じることができます。  
  
- タイトル バーの **[閉じる**] ボタンをクリックします。  
  
- Alt キーを押しながら F4 キーを押す。  
  
- [システム] メニューから **[閉じる**]**を選択**します。  
  
または、[**閉じる**] ボタン<xref:System.Windows.Window.Close%2A>がクリックされたときにコードを呼び出すことができます。  

[!code-csharp[Calling the Close method](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/FindDialogBox.xaml.cs?range=1-9,119-126)]
[!code-vb[Calling the Close method](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/FindDialogBox.xaml.vb?range=1-9,99-103)]  

## <a name="see-also"></a>関連項目

- [ポップアップの概要](../controls/popup-overview.md)
- [ダイアログ ボックスのサンプル](https://github.com/Microsoft/WPF-Samples/tree/master/Windows/DialogBox)
