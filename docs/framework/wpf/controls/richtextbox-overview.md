---
title: RichTextBox の概要
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [WPF], RichTextBox
- RichTextBox control [WPF], about RichTextBox control
ms.assetid: c94548b2-c1e9-4b62-b10c-dd8740eb23d8
ms.openlocfilehash: bfed42bcf3693ef744b3ed2b54ebe070931513a9
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855735"
---
# <a name="richtextbox-overview"></a>RichTextBox の概要

<xref:System.Windows.Controls.RichTextBox>コントロールを使用すると、段落、画像、テーブルなどのフローコンテンツを表示または編集できます。 このトピックでは<xref:System.Windows.Controls.TextBox> 、クラスについて説明し、とC#の両方[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]で使用する方法の例を示します。

<a name="textbox_or_richtextbox"></a>

## <a name="textbox-or-richtextbox"></a>TextBox か RichTextBox か

<xref:System.Windows.Controls.RichTextBox> と<xref:System.Windows.Controls.TextBox>はどちらもテキストの編集を許可しますが、2つのコントロールはさまざまなシナリオで使用されます。 は<xref:System.Windows.Controls.RichTextBox> 、ユーザーが書式設定されたテキスト、画像、テーブル、またはその他のリッチコンテンツを編集する必要がある場合に適しています。 たとえば、書式設定や画像などを必要とするドキュメント、記事、ブログを編集する場合は、を<xref:System.Windows.Controls.RichTextBox>使用することをお勧めします。 には、 <xref:System.Windows.Controls.RichTextBox>より少ないシステムリソースが必要です。また、プレーンテキストのみを編集する必要がある場合(フォームの使用状況など)に最適です。<xref:System.Windows.Controls.TextBox> の<xref:System.Windows.Controls.TextBox>詳細については、「[テキストボックスの概要](textbox-overview.md)」を参照してください。 次の表は、と<xref:System.Windows.Controls.TextBox> <xref:System.Windows.Controls.RichTextBox>の主な機能をまとめたものです。

|コントロール|リアルタイム スペル チェック|コンテキスト メニュー|(Ctr + <xref:System.Windows.Documents.EditingCommands.ToggleBold%2A> B) のような書式設定コマンド|<xref:System.Windows.Documents.FlowDocument>画像、段落、テーブルなどのコンテンツ|
|-------------|------------------------------|------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|<xref:System.Windows.Controls.TextBox>|[はい]|[はい]|いいえ|No.|
|<xref:System.Windows.Controls.RichTextBox>|[はい]|はい|はい|[はい]|

> [!NOTE]
> は (Ctr + B) のよう<xref:System.Windows.Documents.EditingCommands.ToggleBold%2A>な書式設定関連のコマンドをサポートしていませんが、の<xref:System.Windows.Documents.EditingCommands.MoveToLineEnd%2A>ような多くの基本的なコマンドが両方のコントロールでサポートされています。 <xref:System.Windows.Controls.TextBox>

上の表の機能については、後で詳しく説明します。

<a name="creating_a_richtextbox"></a>

## <a name="creating-a-richtextbox"></a>RichTextBox の作成

次のコードは、 <xref:System.Windows.Controls.RichTextBox>ユーザーがのリッチコンテンツを編集できるを作成する方法を示しています。

[!code-xaml[RichTextBoxMiscSnippets_snip#BasicRichTextBoxExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/RichTextBoxMiscSnippets_snip/CSharp/BasicRichTextBoxExample.xaml#basicrichtextboxexamplewholepage)]

具体的には、で<xref:System.Windows.Controls.RichTextBox>編集されるコンテンツはフローコンテンツです。 フロー コンテンツは、書式設定されたテキスト、イメージ、リスト、テーブルなどのさまざまな種類の要素を格納できます。 フロー ドキュメントの詳細については、[フロー ドキュメントの概要](../advanced/flow-document-overview.md)を参照してください。 フローコンテンツを格納するために、 <xref:System.Windows.Controls.RichTextBox>はオブジェクト<xref:System.Windows.Documents.FlowDocument>をホストします。このオブジェクトには編集可能なコンテンツが含まれています。 でのフローの<xref:System.Windows.Controls.RichTextBox>内容を示すために、次のコードは、段落と太字のテキストを使用してを<xref:System.Windows.Controls.RichTextBox>作成する方法を示しています。

[!code-xaml[RichTextBoxMiscSnippets_snip#RichTextBoxWithContentExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/RichTextBoxMiscSnippets_snip/CSharp/RichTextBoxWithContentExample.xaml#richtextboxwithcontentexamplewholepage)]

[!code-csharp[RichTextBoxMiscSnippets_procedural_snip#BasicRichTextBoxWithContentCodeOnlyExample](~/samples/snippets/csharp/VS_Snippets_Wpf/RichTextBoxMiscSnippets_procedural_snip/CSharp/BasicRichTextBoxWithContentExample.cs#basicrichtextboxwithcontentcodeonlyexample)]
[!code-vb[RichTextBoxMiscSnippets_procedural_snip#BasicRichTextBoxWithContentCodeOnlyExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/RichTextBoxMiscSnippets_procedural_snip/visualbasic/basicrichtextboxwithcontentexample.vb#basicrichtextboxwithcontentcodeonlyexample)]

次の図は、このサンプルがレンダリングする方法を示しています。

![RichTextBox with content](./media/editing-richtextbox-with-content.png "Editing_RichTextBox_with_Content")

や<xref:System.Windows.Documents.Paragraph> <xref:System.Windows.Documents.Bold>のような要素は、内のコンテンツをどのように表示するかを決定します。<xref:System.Windows.Controls.RichTextBox> ユーザーがコンテンツを<xref:System.Windows.Controls.RichTextBox>編集すると、このフローの内容が変更されます。 フロー コンテンツの機能およびその操作方法の詳細については、[フロー ドキュメントの概要](../advanced/flow-document-overview.md)を参照してください。

> [!NOTE]
> 内のフローコンテンツ<xref:System.Windows.Controls.RichTextBox>は、他のコントロールに含まれるフローコンテンツとまったく同じようには動作しません。 たとえば、に<xref:System.Windows.Controls.RichTextBox>は列がないため、自動サイズ変更の動作はありません。 また、内<xref:System.Windows.Controls.RichTextBox>では、検索、表示モード、ページナビゲーション、ズームなどの組み込み機能を使用できません。

<a name="realtime_spellechecking"></a>

## <a name="real-time-spell-checking"></a>リアルタイム スペル チェック

<xref:System.Windows.Controls.TextBox>または<xref:System.Windows.Controls.RichTextBox>でリアルタイムスペルチェックを有効にすることができます。 スペル チェックをオンにすると、スペル ミスの語句の下に赤色の線が表示されます (下図を参照)。

![スペル チェックを含む Textbox](./media/editing-textbox-with-spellchecking.png "Editing_TextBox_with_Spellchecking")

スペル チェックを有効にする方法については、「[テキスト編集コントロールでスペル チェックを有効にする](how-to-enable-spell-checking-in-a-text-editing-control.md)」を参照してください。

<a name="context_menu"></a>

## <a name="context-menu"></a>コンテキスト メニュー

既定では、 <xref:System.Windows.Controls.TextBox>と<xref:System.Windows.Controls.RichTextBox>の両方に、ユーザーがコントロール内を右クリックしたときに表示されるコンテキストメニューがあります。 コンテキスト メニューでは、ユーザーは、切り取り、コピー、または貼り付けをできます (下図を参照)。

![コンテキスト メニューを含む TextBox](./media/editing-textbox-with-context-menu.png "Editing_TextBox_with_Context_Menu")

独自のカスタム コンテキスト メニューを作成して、既定のコンテキスト メニューをオーバーライドできます。 詳細については、[カスタム コンテキスト メニューを RichTextBox に配置](how-to-position-a-custom-context-menu-in-a-richtextbox.md)を参照してください。

<a name="detect_when_content_changes"></a>

## <a name="editing-commands"></a>コマンドの編集

編集コマンドを使用すると、ユーザーが内<xref:System.Windows.Controls.RichTextBox>の編集可能なコンテンツを書式設定できます。 には、基本的な<xref:System.Windows.Controls.RichTextBox>編集コマンドに加え<xref:System.Windows.Controls.TextBox>て、でサポートされていない書式設定コマンドが含まれています。 たとえば、で編集する場合、 <xref:System.Windows.Controls.RichTextBox>ユーザーは Ctr + B キーを押して、太字のテキストの書式設定を切り替えることができます。 使用<xref:System.Windows.Documents.EditingCommands>できるコマンドの完全な一覧については、「」を参照してください。 キーボード ショートカットを使用するだけでなく、ボタンのようにコマンドをフックしてその他のコントロールにすることができます。 次の例では、テキストの書式設定を変更するためにユーザーが使用できるボタンを含む簡単なツールバーを作成する方法を示します。

[!code-xaml[RichTextBox_InputPanel_snip#RichTextBoxWithToolBarExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/RichTextBox_InputPanel_snip/CS/Window1.xaml#richtextboxwithtoolbarexamplewholepage)]

次の図は、このサンプルの表示方法を示しています。

![ツールバーを含む RichTextBox](./media/editing-richtextbox-with-toobar.gif "Editing_RichTextBox_with_TooBar")

<a name="editing_commands"></a>

## <a name="detect-when-content-changes"></a>コンテンツがいつ変更されたかの検出

通常、 <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged>イベントは、 <xref:System.Windows.Controls.TextBox>または<xref:System.Windows.Controls.RichTextBox>のテキストが必要に<xref:System.Windows.UIElement.KeyDown>応じて変更されるたびに検出するために使用します。 例については、「[TextBox のテキストがいつ変更されたかを検出する](how-to-detect-when-text-in-a-textbox-has-changed.md)」を参照してください。

<a name="save_load_and_print_richtextbox_content"></a>

## <a name="save-load-and-print-richtextbox-content"></a>RichTextBox コンテンツの保存、読み込み、および印刷

次の例は、の<xref:System.Windows.Controls.RichTextBox>コンテンツをファイルに保存し、その内容を<xref:System.Windows.Controls.RichTextBox>に読み込んでから、内容を印刷する方法を示しています。 この例のマークアップを次に示します。

[!code-xaml[RichTextBoxMiscSnippets_snip#SaveLoadPrintRTBExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/RichTextBoxMiscSnippets_snip/CSharp/SaveLoadPrintRTB.xaml#saveloadprintrtbexamplewholepage)]

この例のコードを次に示します。

[!code-csharp[RichTextBoxMiscSnippets_snip#SaveLoadPrintRTBCodeExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/RichTextBoxMiscSnippets_snip/CSharp/SaveLoadPrintRTB.xaml.cs#saveloadprintrtbcodeexamplewholepage)]
[!code-vb[RichTextBoxMiscSnippets_snip#SaveLoadPrintRTBCodeExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/RichTextBoxMiscSnippets_snip/VisualBasic/SaveLoadPrintRTB.xaml.vb#saveloadprintrtbcodeexamplewholepage)]

## <a name="see-also"></a>関連項目

- [方法トピック](richtextbox-how-to-topics.md)
- [TextBox の概要](textbox-overview.md)
