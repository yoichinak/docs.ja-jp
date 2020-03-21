---
title: TextBox の概要
ms.date: 03/30/2017
helpviewer_keywords:
- controls [WPF], TextBox
- TextBox control [WPF], about TextBox control
ms.assetid: 1ba6dc5b-11a7-4247-9213-36c6729ee35f
ms.openlocfilehash: 9fbae5ac4de4c78a1086bcbd9bfc9e01eb597fb8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186644"
---
# <a name="textbox-overview"></a>TextBox の概要
この<xref:System.Windows.Controls.TextBox>クラスでは、書式設定されていないテキストを表示または編集できます。 一般的な使用<xref:System.Windows.Controls.TextBox>は、フォーム内の書式設定されていないテキストを編集することです。 たとえば、ユーザーの名前や電話番号などを尋ねるフォームでは、テキスト入力用のコントロールを<xref:System.Windows.Controls.TextBox>使用します。 このトピックでは、<xref:System.Windows.Controls.TextBox>クラスを紹介し、C# との両方[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]で使用する方法の例を示します。  

<a name="textbox_or_richtextbox"></a>
## <a name="textbox-or-richtextbox"></a>TextBox または RichTextBox  
 両方<xref:System.Windows.Controls.TextBox>とも<xref:System.Windows.Controls.RichTextBox>、ユーザーがテキストを入力できるようにするが、2 つのコントロールは、異なるシナリオに使用されます。 A<xref:System.Windows.Controls.TextBox>は必要なシステム<xref:System.Windows.Controls.RichTextBox>リソースが少ないので、プレーンテキストだけを編集する必要がある場合 (つまり、フォームでの使用法) が理想的です。 A<xref:System.Windows.Controls.RichTextBox>は、書式設定されたテキスト、画像、表、またはその他のサポートされているコンテンツをユーザーが編集する必要がある場合に適しています。 たとえば、書式設定や画像などを必要とするドキュメント、記事、ブログの編集は、 を使用して行う<xref:System.Windows.Controls.RichTextBox>のが最善です。 次の表は、 と<xref:System.Windows.Controls.TextBox><xref:System.Windows.Controls.TextBox>の主な機能をまとめたものです。  
  
|コントロール|リアルタイム スペル チェック|コンテキスト メニュー|(Ctr+B) のようなコマンドの<xref:System.Windows.Documents.EditingCommands.ToggleBold%2A>書式設定|<xref:System.Windows.Documents.FlowDocument>画像、段落、表などのコンテンツ|  
|-------------|------------------------------|------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|  
|<xref:System.Windows.Controls.TextBox>|はい|はい|いいえ|いいえ。|  
|<xref:System.Windows.Controls.RichTextBox>|はい|はい|はい (「[RichTextBox の概要](richtextbox-overview.md)」を参照)|はい (「[RichTextBox の概要](richtextbox-overview.md)」を参照)|  
  
> [!NOTE]
> (Ctr+B)のような<xref:System.Windows.Controls.TextBox><xref:System.Windows.Documents.EditingCommands.ToggleBold%2A>編集コマンドの書式設定はサポートしていませんが、多くの基本的なコマンドは、 などの<xref:System.Windows.Documents.EditingCommands.MoveToLineEnd%2A>両方のコントロールでサポートされています。 詳細については、「 <xref:System.Windows.Documents.EditingCommands> 」を参照してください。  
  
 で<xref:System.Windows.Controls.TextBox>サポートされる機能については、以下のセクションで説明します。 詳細については、「<xref:System.Windows.Controls.RichTextBox>リッチ[テキスト ボックスの概要](richtextbox-overview.md)」を参照してください。  
  
### <a name="real-time-spellchecking"></a>リアルタイム スペル チェック  
 または でリアルタイムスペルチェックを<xref:System.Windows.Controls.TextBox>有効にすることができます。 <xref:System.Windows.Controls.RichTextBox> スペル チェックをオンにすると、スペル ミスの語句の下に赤色の線が表示されます (下図を参照)。  
  
 ![スペルチェック&#45;テキストボックス](./media/editing-textbox-with-spellchecking.png "Editing_TextBox_with_Spellchecking")  
  
 スペル チェックを有効にする方法については、「[テキスト編集コントロールでスペル チェックを有効にする](how-to-enable-spell-checking-in-a-text-editing-control.md)」を参照してください。  
  
### <a name="context-menu"></a>コンテキスト メニュー  
 既定では、ユーザー<xref:System.Windows.Controls.TextBox><xref:System.Windows.Controls.RichTextBox>がコントロール内を右クリックしたときに表示されるコンテキスト メニューが表示されます。 コンテキスト メニューでは、切り取り、コピー、または貼り付けをできます (下図を参照)。  
  
 ![コンテキスト メニューを含む TextBox](./media/editing-textbox-with-context-menu.png "Editing_TextBox_with_Context_Menu")  
  
 既定の動作をオーバーライドする独自のカスタム コンテキスト メニューを作成できます。 詳細については、「[TextBox でカスタム コンテキスト メニューを使用する](how-to-use-a-custom-context-menu-with-a-textbox.md)」を参照してください。  
  
<a name="creating_textboxes"></a>
## <a name="creating-textboxes"></a>TextBox の作成  
 A<xref:System.Windows.Controls.TextBox>は高さの単一行にすることも、複数の行で構成することもできます。 1 行<xref:System.Windows.Controls.TextBox>は、少量のプレーンテキスト ("名前"、"電話番号"など) を入力するのに最適です。 次の例は、単一の行<xref:System.Windows.Controls.TextBox>を作成する方法を示しています。  
  
 [!code-xaml[TextBoxMiscSnippets_snip#BasicTextBoxExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBoxMiscSnippets_snip/csharp/basictextboxexample.xaml#basictextboxexamplewholepage)]  
  
 また、ユーザーが複数<xref:System.Windows.Controls.TextBox>行のテキストを入力できるようにする を作成することもできます。 たとえば、フォームでユーザーの伝記スケッチを求められた場合、複数行のテキストをサポートする を<xref:System.Windows.Controls.TextBox>使用します。 複数行のテキスト[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]に対応するように自動的に展開<xref:System.Windows.Controls.TextBox>されるコントロールを定義する方法を次の例に示します。  
  
 [!code-xaml[TextBox_MiscCode#_MultilineTextBoxXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_multilinetextboxxaml)]  
  
 コントロールの<xref:System.Windows.Controls.TextBox.TextWrapping%2A>端に`Wrap`達したときに、コントロールの端に達したときにテキストが新しい行に折り返されるように属性を<xref:System.Windows.Controls.TextBox>設定し、必要に応じて、コントロールを自動的に展開して新しい行のスペースを含めます。 <xref:System.Windows.Controls.TextBox>  
  
 <xref:System.Windows.Controls.Primitives.TextBoxBase.AcceptsReturn%2A>この属性を設定`true`すると、Return キーが押されたときに新しい行が挿入され、必要に応じて新しい<xref:System.Windows.Controls.TextBox>行のスペースを含むように再び自動的に拡張されます。  
  
 属性<xref:System.Windows.Controls.Primitives.TextBoxBase.VerticalScrollBarVisibility%2A>は、スクロール バーを<xref:System.Windows.Controls.TextBox>に追加して、を囲むフレーム<xref:System.Windows.Controls.TextBox>またはウィンドウのサイズを超えて<xref:System.Windows.Controls.TextBox>展開した場合に、の内容をスクロールできます。  
  
 <xref:System.Windows.Controls.TextBox>の使用に関連するさまざまなタスクの詳細については、「[操作方法のトピック](textbox-how-to-topics.md)」を参照してください。  
  
<a name="editing_commands"></a>
## <a name="detect-when-content-changes"></a>内容が変更されたときに検出する  
 通常、<xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged>イベントは、期待どおりに、<xref:System.Windows.Controls.TextBox>または<xref:System.Windows.Controls.RichTextBox>内のテキストが変更<xref:System.Windows.UIElement.KeyDown>されるたびに検出するために使用する必要があります。 例については、「[TextBox のテキストがいつ変更されたかを検出する](how-to-detect-when-text-in-a-textbox-has-changed.md)」を参照してください。  
  
## <a name="see-also"></a>関連項目

- [ハウツートピック](textbox-how-to-topics.md)
- [RichTextBox の概要](richtextbox-overview.md)
