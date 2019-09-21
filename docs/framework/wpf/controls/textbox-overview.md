---
title: TextBox の概要
ms.date: 03/30/2017
helpviewer_keywords:
- controls [WPF], TextBox
- TextBox control [WPF], about TextBox control
ms.assetid: 1ba6dc5b-11a7-4247-9213-36c6729ee35f
ms.openlocfilehash: 46600fd1a3023a80d49fae6f020279be6131916a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69951489"
---
# <a name="textbox-overview"></a>TextBox の概要
クラス<xref:System.Windows.Controls.TextBox>を使用すると、書式設定されていないテキストを表示または編集できます。 の一般的な使用方法<xref:System.Windows.Controls.TextBox>は、書式設定されていないテキストをフォームで編集することです。 たとえば、ユーザーの名前や電話番号などを要求するフォームは、テキスト入力に<xref:System.Windows.Controls.TextBox>コントロールを使用します。 このトピックでは<xref:System.Windows.Controls.TextBox> 、クラスについて説明し、とC#の両方[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]で使用する方法の例を示します。  

<a name="textbox_or_richtextbox"></a>   
## <a name="textbox-or-richtextbox"></a>TextBox か RichTextBox か  
 と<xref:System.Windows.Controls.TextBox>は<xref:System.Windows.Controls.RichTextBox>どちらも、ユーザーがテキストを入力できるようにしますが、2つのコントロールはさまざまなシナリオで使用されます。 で<xref:System.Windows.Controls.TextBox>は、必要な<xref:System.Windows.Controls.RichTextBox>システムリソースが少なくて済みます。そのため、プレーンテキストのみを編集する必要がある場合 (つまり、フォーム内で使用する場合) に最適です。 <xref:System.Windows.Controls.RichTextBox>は、ユーザーが書式設定されたテキスト、画像、テーブル、またはその他のサポートされるコンテンツを編集する必要がある場合に適しています。 たとえば、書式設定や画像などを必要とするドキュメント、記事、ブログを編集する場合は、を<xref:System.Windows.Controls.RichTextBox>使用することをお勧めします。 次の表は、と<xref:System.Windows.Controls.TextBox> <xref:System.Windows.Controls.TextBox>の主な機能をまとめたものです。  
  
|コントロール|リアルタイム スペル チェック|コンテキスト メニュー|(Ctr + <xref:System.Windows.Documents.EditingCommands.ToggleBold%2A> B) のような書式設定コマンド|<xref:System.Windows.Documents.FlowDocument>画像、段落、テーブルなどのコンテンツ|  
|-------------|------------------------------|------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|  
|<xref:System.Windows.Controls.TextBox>|[はい]|[はい]|いいえ|No.|  
|<xref:System.Windows.Controls.RichTextBox>|[はい]|[はい]|はい (「[RichTextBox の概要](richtextbox-overview.md)」を参照)|はい (「[RichTextBox の概要](richtextbox-overview.md)」を参照)|  
  
> [!NOTE]
> は (Ctr + B) のような<xref:System.Windows.Documents.EditingCommands.ToggleBold%2A>書式設定関連の編集コマンドをサポートしていませんが、の<xref:System.Windows.Documents.EditingCommands.MoveToLineEnd%2A>ような多くの基本的なコマンドが両方のコントロールでサポートされています。 <xref:System.Windows.Controls.TextBox> 詳細については、「<xref:System.Windows.Documents.EditingCommands>」を参照してください。  
  
 で<xref:System.Windows.Controls.TextBox>サポートされている機能については、以下のセクションで説明します。 の詳細<xref:System.Windows.Controls.RichTextBox>については、「 [RichTextBox の概要](richtextbox-overview.md)」を参照してください。  
  
### <a name="real-time-spellchecking"></a>リアルタイム スペル チェック  
 リアルタイムスペルチェックは、 <xref:System.Windows.Controls.TextBox>または<xref:System.Windows.Controls.RichTextBox>で有効にすることができます。 スペル チェックをオンにすると、スペル ミスの語句の下に赤色の線が表示されます (下図を参照)。  
  
 ![スペル チェックを含む Textbox](./media/editing-textbox-with-spellchecking.png "Editing_TextBox_with_Spellchecking")  
  
 スペル チェックを有効にする方法については、「[テキスト編集コントロールでスペル チェックを有効にする](how-to-enable-spell-checking-in-a-text-editing-control.md)」を参照してください。  
  
### <a name="context-menu"></a>コンテキスト メニュー  
 既定では、 <xref:System.Windows.Controls.TextBox>と<xref:System.Windows.Controls.RichTextBox>の両方に、ユーザーがコントロール内を右クリックしたときに表示されるコンテキストメニューがあります。 コンテキスト メニューでは、切り取り、コピー、または貼り付けをできます (下図を参照)。  
  
 ![コンテキスト メニューを含む TextBox](./media/editing-textbox-with-context-menu.png "Editing_TextBox_with_Context_Menu")  
  
 既定の動作をオーバーライドする独自のカスタム コンテキスト メニューを作成できます。 詳細については、「[TextBox でカスタム コンテキスト メニューを使用する](how-to-use-a-custom-context-menu-with-a-textbox.md)」を参照してください。  
  
<a name="creating_textboxes"></a>   
## <a name="creating-textboxes"></a>TextBox の作成  
 は<xref:System.Windows.Controls.TextBox> 、1行の高さにすることも、複数の行を構成することもできます。 単一行<xref:System.Windows.Controls.TextBox>は、少量のプレーンテキストを入力する場合に最適です (つまり、「名前」、「電話番号」などのフォームへの入力)。 次の例では、単一行<xref:System.Windows.Controls.TextBox>を作成する方法を示します。  
  
 [!code-xaml[TextBoxMiscSnippets_snip#BasicTextBoxExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBoxMiscSnippets_snip/csharp/basictextboxexample.xaml#basictextboxexamplewholepage)]  
  
 また、ユーザーが複数<xref:System.Windows.Controls.TextBox>行のテキストを入力できるようにするを作成することもできます。 たとえば、ユーザーの経歴スケッチを求めるフォームが表示された場合は、複数行のテキスト<xref:System.Windows.Controls.TextBox>をサポートするを使用します。 次の例は、を使用[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]して、 <xref:System.Windows.Controls.TextBox>複数行のテキストに合わせて自動的に拡張されるコントロールを定義する方法を示しています。  
  
 [!code-xaml[TextBox_MiscCode#_MultilineTextBoxXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_multilinetextboxxaml)]  
  
 属性をに設定`Wrap`すると、 <xref:System.Windows.Controls.TextBox>コントロールの端に達したときにテキストが新しい行に折り返され、必要<xref:System.Windows.Controls.TextBox>に応じて、新しい行のスペースが含まれるようにコントロールが自動的に拡張されます。 <xref:System.Windows.Controls.TextBox.TextWrapping%2A>  
  
 属性をに設定`true`すると、RETURN キーが押されたときに新しい行が挿入されます。 <xref:System.Windows.Controls.TextBox>また、必要に応じて、を自動的に拡張して、新しい行にスペースが含まれるようにします。 <xref:System.Windows.Controls.Primitives.TextBoxBase.AcceptsReturn%2A>  
  
 属性<xref:System.Windows.Controls.Primitives.TextBoxBase.VerticalScrollBarVisibility%2A>は、 <xref:System.Windows.Controls.TextBox>にスクロールバーを追加します。これにより、 <xref:System.Windows.Controls.TextBox>が、フレームまたはウィンドウ<xref:System.Windows.Controls.TextBox>のサイズを超えて拡大した場合に、の内容をスクロールできるようになります。  
  
 の<xref:System.Windows.Controls.TextBox>使用に関連するさまざまなタスクの詳細については、「[操作方法に関するトピック](textbox-how-to-topics.md)」を参照してください。  
  
<a name="editing_commands"></a>   
## <a name="detect-when-content-changes"></a>内容が変更されたときに検出する  
 通常、 <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged>イベントは<xref:System.Windows.Controls.RichTextBox> 、または<xref:System.Windows.Controls.TextBox>のテキストが必要に応じて変更されるたびに検出するために使用します。<xref:System.Windows.UIElement.KeyDown> 例については、「[TextBox のテキストがいつ変更されたかを検出する](how-to-detect-when-text-in-a-textbox-has-changed.md)」を参照してください。  
  
## <a name="see-also"></a>関連項目

- [方法トピック](textbox-how-to-topics.md)
- [RichTextBox の概要](richtextbox-overview.md)
