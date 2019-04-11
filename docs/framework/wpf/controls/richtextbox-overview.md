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
ms.openlocfilehash: 9aa0d33b3cb2c15ba9c1cb7e7d7be9a3125f66d3
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59162712"
---
# <a name="richtextbox-overview"></a>RichTextBox の概要
<xref:System.Windows.Controls.RichTextBox>コントロールでは、段落、イメージ、テーブル、およびなどのフロー コンテンツを編集または表示することができます。 このトピックでは、<xref:System.Windows.Controls.TextBox>クラスし、両方で使用する方法の例を示します[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]とC#します。  

<a name="textbox_or_richtextbox"></a>   
## <a name="textbox-or-richtextbox"></a>TextBox か RichTextBox か  
 両方<xref:System.Windows.Controls.RichTextBox>と<xref:System.Windows.Controls.TextBox>テキストを編集できるように、ただし、2 つのコントロールがさまざまなシナリオで使用します。 A<xref:System.Windows.Controls.RichTextBox>は、ユーザーが書式設定されたテキスト、イメージ、テーブル、またはその他のリッチ コンテンツを編集するために必要なときに、ことをお勧めします。 たとえば、イメージ ドキュメント、記事、または書式設定、必要とするブログを編集などを使用して最適な実行、<xref:System.Windows.Controls.RichTextBox>します。 A<xref:System.Windows.Controls.TextBox>システム リソースが必要です、<xref:System.Windows.Controls.RichTextBox>するニーズをプレーン テキストのみ (つまりフォームで使用) を編集する際に最適です。 参照してください[TextBox の概要](textbox-overview.md)の詳細については<xref:System.Windows.Controls.TextBox>します。 次の表は、の主な機能をまとめたものです。<xref:System.Windows.Controls.TextBox>と<xref:System.Windows.Controls.RichTextBox>します。  
  
|コントロール|リアルタイム スペル チェック|コンテキスト メニュー|書式設定コマンドのような<xref:System.Windows.Documents.EditingCommands.ToggleBold%2A>(<xref:system.windows.documents.editingcommands.togglebold%2a>(ctr + B)|<xref:System.Windows.Documents.FlowDocument> イメージ、段落、テーブルなどのコンテンツ。|  
|-------------|------------------------------|------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|  
|<xref:System.Windows.Controls.TextBox>|はい|[はい]|いいえ|いいえ。|  
|<xref:System.Windows.Controls.RichTextBox>|はい|はい|はい|はい|  
  
 **注:**<xref:System.Windows.Controls.TextBox>は書式設定などの関連コマンドをサポートしていません<xref:System.Windows.Documents.EditingCommands.ToggleBold%2A>(CTR+B) など、多くの基本的なコマンドは両方のコントロールでサポートされて<xref:System.Windows.Documents.EditingCommands.MoveToLineEnd%2A>します。  
  
 上の表の機能については、後で詳しく説明します。  
  
<a name="creating_a_richtextbox"></a>   
## <a name="creating-a-richtextbox"></a>RichTextBox の作成  
 次のコードを作成する方法を示しています、<xref:System.Windows.Controls.RichTextBox>ユーザーがリッチ コンテンツを編集できます。  
  
 [!code-xaml[RichTextBoxMiscSnippets_snip#BasicRichTextBoxExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/RichTextBoxMiscSnippets_snip/CSharp/BasicRichTextBoxExample.xaml#basicrichtextboxexamplewholepage)]  
  
 具体的には、コンテンツの編集、<xref:System.Windows.Controls.RichTextBox>フロー コンテンツは、します。 フロー コンテンツは、書式設定されたテキスト、イメージ、リスト、テーブルなどのさまざまな種類の要素を格納できます。 フロー ドキュメントの詳細については、[フロー ドキュメントの概要](../advanced/flow-document-overview.md)を参照してください。 フローのコンテンツを格納するために、<xref:System.Windows.Controls.RichTextBox>ホスト、<xref:System.Windows.Documents.FlowDocument>編集可能なコンテンツを格納するオブジェクト。 フロー コンテンツを説明するために、 <xref:System.Windows.Controls.RichTextBox>、次のコードを作成する方法を示しています、<xref:System.Windows.Controls.RichTextBox>を段落と太字で表示されるテキスト。  
  
 [!code-xaml[RichTextBoxMiscSnippets_snip#RichTextBoxWithContentExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/RichTextBoxMiscSnippets_snip/CSharp/RichTextBoxWithContentExample.xaml#richtextboxwithcontentexamplewholepage)]  
  
 [!code-csharp[RichTextBoxMiscSnippets_procedural_snip#BasicRichTextBoxWithContentCodeOnlyExample](~/samples/snippets/csharp/VS_Snippets_Wpf/RichTextBoxMiscSnippets_procedural_snip/CSharp/BasicRichTextBoxWithContentExample.cs#basicrichtextboxwithcontentcodeonlyexample)]
 [!code-vb[RichTextBoxMiscSnippets_procedural_snip#BasicRichTextBoxWithContentCodeOnlyExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/RichTextBoxMiscSnippets_procedural_snip/visualbasic/basicrichtextboxwithcontentexample.vb#basicrichtextboxwithcontentcodeonlyexample)]  
  
 次の図は、このサンプルがレンダリングする方法を示しています。  
  
 ![RichTextBox with content](./media/editing-richtextbox-with-content.png "Editing_RichTextBox_with_Content")  
  
 などの要素<xref:System.Windows.Documents.Paragraph>と<xref:System.Windows.Documents.Bold>を決定する方法、コンテンツ内を<xref:System.Windows.Controls.RichTextBox>が表示されます。 ユーザーが編集すると<xref:System.Windows.Controls.RichTextBox>このフロー コンテンツを変更するコンテンツ。 フロー コンテンツの機能およびその操作方法の詳細については、[フロー ドキュメントの概要](../advanced/flow-document-overview.md)を参照してください。  
  
 **注:** 内のコンテンツのフローを<xref:System.Windows.Controls.RichTextBox>他のコントロールに含まれるフロー コンテンツとまったく同じように動作しません。 たとえば、列ではありません、<xref:System.Windows.Controls.RichTextBox>のため自動サイズ変更なし動作とします。 また、組み込み機能など、検索、表示モード、ページ ナビゲーション、およびズームは内で使用できません、<xref:System.Windows.Controls.RichTextBox>します。  
  
<a name="realtime_spellechecking"></a>   
## <a name="real-time-spell-checking"></a>リアルタイム スペル チェック  
 リアルタイム スペル チェックを有効にすることができます、<xref:System.Windows.Controls.TextBox>または<xref:System.Windows.Controls.RichTextBox>します。 スペル チェックをオンにすると、スペル ミスの語句の下に赤色の線が表示されます (下図を参照)。  
  
 ![スペル チェックを含む Textbox](./media/editing-textbox-with-spellchecking.png "Editing_TextBox_with_Spellchecking")  
  
 スペル チェックを有効にする方法については、「[テキスト編集コントロールでスペル チェックを有効にする](how-to-enable-spell-checking-in-a-text-editing-control.md)」を参照してください。  
  
<a name="context_menu"></a>   
## <a name="context-menu"></a>コンテキスト メニュー  
 既定では、どちらも<xref:System.Windows.Controls.TextBox>と<xref:System.Windows.Controls.RichTextBox>コントロール内にユーザーを右クリックしたときに表示されるコンテキスト メニューが表示されます。 コンテキスト メニューでは、ユーザーは、切り取り、コピー、または貼り付けをできます (下図を参照)。  
  
 ![コンテキスト メニューを含む TextBox](./media/editing-textbox-with-context-menu.png "Editing_TextBox_with_Context_Menu")  
  
 独自のカスタム コンテキスト メニューを作成して、既定のコンテキスト メニューをオーバーライドできます。 詳細については、[カスタム コンテキスト メニューを RichTextBox に配置](how-to-position-a-custom-context-menu-in-a-richtextbox.md)を参照してください。  
  
<a name="detect_when_content_changes"></a>   
## <a name="editing-commands"></a>コマンドの編集  
 コマンド内で編集可能なコンテンツを書式設定を有効にするユーザーの編集、<xref:System.Windows.Controls.RichTextBox>します。 Basic だけでなく編集コマンド<xref:System.Windows.Controls.RichTextBox>を含むコマンドの書式設定<xref:System.Windows.Controls.TextBox>はサポートしていません。 例で編集するときに、<xref:System.Windows.Controls.RichTextBox>ユーザーが太字のテキストの書式設定を切り替えるには、CTR+B を押してでした。 参照してください<xref:System.Windows.Documents.EditingCommands>使用可能なコマンドの完全な一覧についてはします。 キーボード ショートカットを使用するだけでなく、ボタンのようにコマンドをフックしてその他のコントロールにすることができます。 次の例では、テキストの書式設定を変更するためにユーザーが使用できるボタンを含む簡単なツールバーを作成する方法を示します。  
  
 [!code-xaml[RichTextBox_InputPanel_snip#RichTextBoxWithToolBarExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/RichTextBox_InputPanel_snip/CS/Window1.xaml#richtextboxwithtoolbarexamplewholepage)]  
  
 次の図は、このサンプルの表示方法を示しています。  
  
 ![ツールバーを含む RichTextBox](./media/editing-richtextbox-with-toobar.gif "Editing_RichTextBox_with_TooBar")  
  
<a name="editing_commands"></a>   
## <a name="detect-when-content-changes"></a>コンテンツがいつ変更されたかの検出  
 通常、<xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged>検出されるたびにイベントを使用する必要があります内のテキストを<xref:System.Windows.Controls.TextBox>または<xref:System.Windows.Controls.RichTextBox>変更ではなく<xref:System.Windows.UIElement.KeyDown>推察のとおりです。 例については、「[TextBox のテキストがいつ変更されたかを検出する](how-to-detect-when-text-in-a-textbox-has-changed.md)」を参照してください。  
  
<a name="save_load_and_print_richtextbox_content"></a>   
## <a name="save-load-and-print-richtextbox-content"></a>RichTextBox コンテンツの保存、読み込み、および印刷  
 次の例の内容を保存する方法を示しています、<xref:System.Windows.Controls.RichTextBox>ファイルに読み込むにその内容を<xref:System.Windows.Controls.RichTextBox>、および内容を印刷します。 この例のマークアップを次に示します。  
  
 [!code-xaml[RichTextBoxMiscSnippets_snip#SaveLoadPrintRTBExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/RichTextBoxMiscSnippets_snip/CSharp/SaveLoadPrintRTB.xaml#saveloadprintrtbexamplewholepage)]  
  
 この例のコードを次に示します。  
  
 [!code-csharp[RichTextBoxMiscSnippets_snip#SaveLoadPrintRTBCodeExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/RichTextBoxMiscSnippets_snip/CSharp/SaveLoadPrintRTB.xaml.cs#saveloadprintrtbcodeexamplewholepage)]
 [!code-vb[RichTextBoxMiscSnippets_snip#SaveLoadPrintRTBCodeExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/RichTextBoxMiscSnippets_snip/VisualBasic/SaveLoadPrintRTB.xaml.vb#saveloadprintrtbcodeexamplewholepage)]  
  
## <a name="see-also"></a>関連項目

- [方法のトピック](richtextbox-how-to-topics.md)
- [TextBox の概要](textbox-overview.md)
