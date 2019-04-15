---
title: TextBox の概要
ms.date: 03/30/2017
helpviewer_keywords:
- controls [WPF], TextBox
- TextBox control [WPF], about TextBox control
ms.assetid: 1ba6dc5b-11a7-4247-9213-36c6729ee35f
ms.openlocfilehash: 577a12a0c04e5e3bfbfecb2c45263b684f0ffc17
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59162647"
---
# <a name="textbox-overview"></a>TextBox の概要
<xref:System.Windows.Controls.TextBox>クラスでは、書式設定されていないテキストを編集または表示することができます。 一般的な用途、<xref:System.Windows.Controls.TextBox>がフォームで書式設定されていないテキストを編集します。 たとえば、ユーザーの名前、電話番号の場合は、入力を求めるフォームなどは使用<xref:System.Windows.Controls.TextBox>のテキスト入力コントロール。 このトピックでは、<xref:System.Windows.Controls.TextBox>クラスし、両方で使用する方法の例を示します[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]とC#します。  

<a name="textbox_or_richtextbox"></a>   
## <a name="textbox-or-richtextbox"></a>TextBox か RichTextBox か  
 両方<xref:System.Windows.Controls.TextBox>と<xref:System.Windows.Controls.RichTextBox>テキストを入力するユーザーがさまざまなシナリオの 2 つのコントロールを使用します。 A<xref:System.Windows.Controls.TextBox>システム リソースが必要です、<xref:System.Windows.Controls.RichTextBox>ので、プレーン テキストのみを編集する必要がある場合に最適です (つまり、フォームでの使用)。 A<xref:System.Windows.Controls.RichTextBox>コンテンツを書式設定されたテキスト、イメージ、テーブルを編集する必要がありますまたはその他のサポートされているときに適していますが。 たとえば、イメージ ドキュメント、記事、または書式設定、必要とするブログを編集などを使用して最適な実行、<xref:System.Windows.Controls.RichTextBox>します。 次の表は、の主な機能をまとめたものです。<xref:System.Windows.Controls.TextBox>と<xref:System.Windows.Controls.TextBox>します。  
  
|コントロール|リアルタイム スペル チェック|コンテキスト メニュー|書式設定コマンドのような<xref:System.Windows.Documents.EditingCommands.ToggleBold%2A>(<xref:system.windows.documents.editingcommands.togglebold%2a>(ctr + B)|<xref:System.Windows.Documents.FlowDocument> イメージ、段落、テーブルなどのコンテンツ。|  
|-------------|------------------------------|------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|  
|<xref:System.Windows.Controls.TextBox>|はい|[はい]|いいえ|いいえ。|  
|<xref:System.Windows.Controls.RichTextBox>|はい|[はい]|はい (「[RichTextBox の概要](richtextbox-overview.md)」を参照)|はい (「[RichTextBox の概要](richtextbox-overview.md)」を参照)|  
  
> [!NOTE]
>  <xref:System.Windows.Controls.TextBox>コマンドなどの関連の編集を書式設定はサポートされていませんが<xref:System.Windows.Documents.EditingCommands.ToggleBold%2A>(CTR+B) など、多くの基本的なコマンドは両方のコントロールでサポートされて<xref:System.Windows.Documents.EditingCommands.MoveToLineEnd%2A>します。 詳細については、「<xref:System.Windows.Documents.EditingCommands>」を参照してください。  
  
 サポートされる機能<xref:System.Windows.Controls.TextBox>は以下のセクションで説明します。 詳細については<xref:System.Windows.Controls.RichTextBox>を参照してください[RichTextBox の概要](richtextbox-overview.md)します。  
  
### <a name="real-time-spellchecking"></a>リアルタイム スペル チェック  
 リアルタイム スペル チェックを有効にすることができます、<xref:System.Windows.Controls.TextBox>または<xref:System.Windows.Controls.RichTextBox>します。 スペル チェックをオンにすると、スペル ミスの語句の下に赤色の線が表示されます (下図を参照)。  
  
 ![スペル チェックを含む Textbox](./media/editing-textbox-with-spellchecking.png "Editing_TextBox_with_Spellchecking")  
  
 スペル チェックを有効にする方法については、「[テキスト編集コントロールでスペル チェックを有効にする](how-to-enable-spell-checking-in-a-text-editing-control.md)」を参照してください。  
  
### <a name="context-menu"></a>コンテキスト メニュー  
 既定では、どちらも<xref:System.Windows.Controls.TextBox>と<xref:System.Windows.Controls.RichTextBox>コントロール内にユーザーを右クリックしたときに表示されるコンテキスト メニューが表示されます。 コンテキスト メニューでは、切り取り、コピー、または貼り付けをできます (下図を参照)。  
  
 ![コンテキスト メニューを含む TextBox](./media/editing-textbox-with-context-menu.png "Editing_TextBox_with_Context_Menu")  
  
 既定の動作をオーバーライドする独自のカスタム コンテキスト メニューを作成できます。 詳細については、「[TextBox でカスタム コンテキスト メニューを使用する](how-to-use-a-custom-context-menu-with-a-textbox.md)」を参照してください。  
  
<a name="creating_textboxes"></a>   
## <a name="creating-textboxes"></a>TextBox の作成  
 A <xref:System.Windows.Controls.TextBox> 1 行の高さにしたり、複数行を構成します。 1 行<xref:System.Windows.Controls.TextBox>(つまり、少量のプレーン テキストの入力に最適な「名前」、「電話番号」などのフォームへの入力)。 次の例は、1 つの行を作成する方法を示します<xref:System.Windows.Controls.TextBox>します。  
  
 [!code-xaml[TextBoxMiscSnippets_snip#BasicTextBoxExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBoxMiscSnippets_snip/csharp/basictextboxexample.xaml#basictextboxexamplewholepage)]  
  
 作成することも、<xref:System.Windows.Controls.TextBox>ユーザーに複数行のテキストを入力できるようにします。 たとえば、フォームのユーザーの経歴の場合が使用する、<xref:System.Windows.Controls.TextBox>複数行のテキストをサポートします。 次の例は、使用する方法を示します[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]を定義する、<xref:System.Windows.Controls.TextBox>複数行のテキストに合わせて自動的に拡張するコントロール。  
  
 [!code-xaml[TextBox_MiscCode#_MultilineTextBoxXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_multilinetextboxxaml)]  
  
 設定、<xref:System.Windows.Controls.TextBox.TextWrapping%2A>属性を`Wrap`により新しいをラップするテキストの行の端、<xref:System.Windows.Controls.TextBox>コントロールに達すると、自動的に拡大、<xref:System.Windows.Controls.TextBox>コントロールに必要な場合に、新しい行を含めます。  
  
 設定、<xref:System.Windows.Controls.Primitives.TextBoxBase.AcceptsReturn%2A>属性を`true`が再び自動的に拡大、戻り値のキーが押されたときに挿入する改行を発生させる、<xref:System.Windows.Controls.TextBox>に必要な場合に、新しい行を含めます。  
  
 <xref:System.Windows.Controls.Primitives.TextBoxBase.VerticalScrollBarVisibility%2A>属性によってスクロール バーを表示、追加、<xref:System.Windows.Controls.TextBox>いるための内容、<xref:System.Windows.Controls.TextBox>場合をスクロール、<xref:System.Windows.Controls.TextBox>フレームまたはこれを囲むウィンドウのサイズします。  
  
 使用すると、さまざまなタスクの詳細については、<xref:System.Windows.Controls.TextBox>を参照してください[方法に関するトピック](textbox-how-to-topics.md)します。  
  
<a name="editing_commands"></a>   
## <a name="detect-when-content-changes"></a>内容が変更されたときに検出する  
 通常、<xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged>検出されるたびにイベントを使用する必要があります内のテキストを<xref:System.Windows.Controls.TextBox>または<xref:System.Windows.Controls.RichTextBox>変更ではなく、<xref:System.Windows.UIElement.KeyDown>推察のとおりです。 例については、「[TextBox のテキストがいつ変更されたかを検出する](how-to-detect-when-text-in-a-textbox-has-changed.md)」を参照してください。  
  
## <a name="see-also"></a>関連項目

- [方法のトピック](textbox-how-to-topics.md)
- [RichTextBox の概要](richtextbox-overview.md)
