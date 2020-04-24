---
title: ユーザー入力の検証
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, validating user input
- validation [Windows Forms], Windows Forms user input
- user input [Windows Forms], validating in Windows Forms
- validating user input [Windows Forms], Windows Forms
ms.assetid: 4ec07681-1dee-4bf9-be5e-718f635a33a1
ms.openlocfilehash: eafbf54552566011fef9d2dbeb5e9f9fa3facabd
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/20/2020
ms.locfileid: "81646300"
---
# <a name="user-input-validation-in-windows-forms"></a>Windows フォームでのユーザー入力の検証
ユーザーがアプリケーションにデータを入力する場合、アプリケーションで使用する前に、データが有効であることを確認する必要があります。 テキスト フィールドの長さが 0 でない場合、フィールドが電話番号またはその他の形式のデータとして書式設定されている場合、またはデータベースのセキュリティを損なう可能性のある安全でない文字が文字列に含まれていないことを要求する場合があります。 Windows フォームには、アプリケーション内の入力を検証するためのいくつかの方法があります。  
  
## <a name="validation-with-the-maskedtextbox-control"></a>マスクテキスト ボックス コントロールを使用した検証  
 電話番号や部品番号など、明確に定義された形式でデータを入力する必要がある場合は、<xref:System.Windows.Forms.MaskedTextBox>コントロールを使用して、最小限のコードですばやくこれを実現できます。 *マスク*は、テキスト ボックス内の任意の位置に入力できる文字を指定する、マスク言語の文字で構成される文字列です。 コントロールは、ユーザーに対して一連のプロンプトを表示します。 たとえば、ユーザーが数字が必要なときに文字を入力すると、ユーザーが入力を自動的に拒否します。  
  
 で<xref:System.Windows.Forms.MaskedTextBox>使用されるマスキング言語は非常に柔軟です。 必須の文字、省略可能な文字、ハイフンやかっこなどのリテラル文字、通貨記号、および日付区切り記号を指定できます。 コントロールは、データ ソースにバインドされている場合にも適しています。 データ<xref:System.Windows.Forms.Binding.Format>バインディングのイベントを使用して、入力データをマスクに準拠するように再フォーマットすることができ、<xref:System.Windows.Forms.Binding.Parse>このイベントを使用して、データ フィールドの仕様に準拠するように送信データを再フォーマットできます。  
  
 詳細については、「 [MaskedTextBox コントロール](./controls/maskedtextbox-control-windows-forms.md)」を参照してください。  
  
## <a name="event-driven-validation"></a>イベント駆動型検証  
 プログラムによる検証の完全な制御を必要とする場合、または複雑な検証チェックを実行する必要がある場合は、ほとんどの Windows フォーム コントロールに組み込まれている検証イベントを使用する必要があります。 自由形式のユーザー入力を受け入れる各コントロール<xref:System.Windows.Forms.Control.Validating>には、コントロールがデータの入力規則を必要とするたびに発生するイベントがあります。 <xref:System.Windows.Forms.Control.Validating>イベント処理メソッドでは、ユーザー入力を検証する方法がいくつかあります。 たとえば、郵便番号を含むテキスト ボックスがある場合は、次の方法で検証を実行できます。  
  
- 郵便番号が特定の郵便番号グループに属している必要がある場合は、入力に対して文字列比較を実行して、ユーザーが入力したデータを検証できます。 たとえば、郵便番号が {10001、10002、10003} のセットに含まれている必要がある場合、文字列比較を使用してデータを検証できます。  
  
- 郵便番号を特定の形式にする必要がある場合は、正規表現を使用して、ユーザーが入力したデータを検証できます。 たとえば、フォーム`#####`を検証するには、`#####-####`または の正規表現`^(\d{5})(-\d{4})?$`を使用します。 フォーム`A#A #A#`を検証するには、 正規表現`[A-Z]\d[A-Z] \d[A-Z]\d`を使用します。 正規表現の詳細については、「 [.NET Framework 正規表現](../../standard/base-types/regular-expressions.md)と[正規表現の例](../../standard/base-types/regular-expression-example-scanning-for-hrefs.md)」を参照してください。  
  
- 郵便番号が有効な米国の郵便番号である必要がある場合は、郵便番号 Web サービスを呼び出して、ユーザーが入力したデータを検証できます。  
  
 イベント<xref:System.Windows.Forms.Control.Validating>は、 型のオブジェクトを<xref:System.ComponentModel.CancelEventArgs>提供します。 コントロールのデータが無効であると判断した場合は、このオブジェクトの<xref:System.Windows.Forms.Control.Validating><xref:System.ComponentModel.CancelEventArgs.Cancel%2A>プロパティを に設定してイベントを`true`キャンセルできます。 このプロパティを<xref:System.ComponentModel.CancelEventArgs.Cancel%2A>設定しない場合、Windows フォームはそのコントロールの検証に成功したと見なし、イベント<xref:System.Windows.Forms.Control.Validated>を発生させます。  
  
 の電子メール アドレスを検証するコード例については<xref:System.Windows.Controls.TextBox>、「 」<xref:System.Windows.Forms.Control.Validating>を参照してください。  
  
### <a name="data-binding-and-event-driven-validation"></a>データ バインディングとイベント ドリブン検証  
 検証は、コントロールをデータベース テーブルなどのデータ ソースにバインドしている場合に非常に便利です。 検証を使用すると、コントロールのデータがデータ ソースに必要な形式を満たしていること、および安全でない可能性のある引用符やバックスラッシュなどの特殊文字が含まれていないことを確認できます。  
  
 データ バインディングを使用すると、コントロール内のデータはイベントの実行中にデータ ソースと同期されます<xref:System.Windows.Forms.Control.Validating>。 イベントを<xref:System.Windows.Forms.Control.Validating>キャンセルすると、データはデータ ソースと同期されません。  
  
> [!IMPORTANT]
> <xref:System.Windows.Forms.Control.Validating>イベントの後にカスタム検証が行われる場合、データ バインディングには影響しません。 たとえば、データ バインディングを<xref:System.Windows.Forms.Control.Validated>取り消そうとするイベントにコードがある場合でも、データ バインディングは引き続き実行されます。 この<xref:System.Windows.Forms.Control.Validated>場合、イベントで検証を実行するには、コントロールの **[データ ソース更新モード**] プロパティ **([(データバインディング)]**\\(**詳細) )** を **[OnValidation]** から **[Never]** に変更し *、Control*`.DataBindings["`*\<YOURFIELD>*`"].WriteValue()`を検証コードに追加します。  
  
### <a name="implicit-and-explicit-validation"></a>暗黙的および明示的な検証  
 では、コントロールのデータはいつ検証されるのでしょうか。 これは開発者次第です。 アプリケーションのニーズに応じて、暗黙的または明示的な検証を使用できます。  
  
#### <a name="implicit-validation"></a>暗黙的な検証  
 暗黙的な検証アプローチでは、ユーザーが入力したデータを検証します。 データがコントロールに入力されたときに、キーを押したときに読み取るか、ユーザーが入力フォーカスを 1 つのコントロールから離して次のコントロールに移動する場合に、より一般的にデータを検証できます。 この方法は、作業中のデータに関するフィードバックをユーザーに直接提供する場合に便利です。  
  
 コントロールに対して暗黙の検証を使用する場合は、そのコントロールの<xref:System.Windows.Forms.ContainerControl.AutoValidate%2A>プロパティを or <xref:System.Windows.Forms.AutoValidate.EnablePreventFocusChange> <xref:System.Windows.Forms.AutoValidate.EnableAllowFocusChange>に設定する必要があります。 イベントを<xref:System.Windows.Forms.Control.Validating>キャンセルすると、コントロールの動作は<xref:System.Windows.Forms.ContainerControl.AutoValidate%2A>、 に割り当てた値によって決まります。 を割り<xref:System.Windows.Forms.AutoValidate.EnablePreventFocusChange>当てた場合、イベントをキャンセルすると<xref:System.Windows.Forms.Control.Validated>イベントが発生しません。 ユーザーがデータを有効な入力に変更するまで、入力フォーカスは現在のコントロールに残ります。 を割り<xref:System.Windows.Forms.AutoValidate.EnableAllowFocusChange>当てた<xref:System.Windows.Forms.Control.Validated>場合、イベントをキャンセルしてもイベントは発生しませんが、フォーカスは次のコントロールに変わります。  
  
 プロパティに<xref:System.Windows.Forms.AutoValidate.Disable>割り<xref:System.Windows.Forms.ContainerControl.AutoValidate%2A>当てると、暗黙的な検証が完全に行われるのを防ぐことができます。 コントロールを検証するには、明示的な検証を使用する必要があります。  
  
#### <a name="explicit-validation"></a>明示的な検証  
 明示的な検証アプローチでは、データを一度に検証します。 [保存] ボタンや [次へ] リンクをクリックするなど、ユーザーの操作に応じてデータを検証できます。 ユーザーアクションが発生すると、次のいずれかの方法で明示的な検証をトリガーできます。  
  
- フォーカス<xref:System.Windows.Forms.ContainerControl.Validate%2A>を失った最後のコントロールを検証する呼び出し。  
  
- フォーム<xref:System.Windows.Forms.ContainerControl.ValidateChildren%2A>コントロールまたはコンテナコントロール内のすべての子コントロールを検証する呼び出し。  
  
- コントロールのデータを手動で検証するカスタム メソッドを呼び出します。  
  
#### <a name="default-implicit-validation-behavior-for-windows-forms-controls"></a>Windows フォーム コントロールの既定の暗黙的な検証動作  
 Windows フォーム コントロールによって、<xref:System.Windows.Forms.ContainerControl.AutoValidate%2A>プロパティの既定値が異なります。 次の表は、最も一般的なコントロールとその既定値を示しています。  
  
|コントロール|既定の検証動作|  
|-------------|---------------------------------|  
|<xref:System.Windows.Forms.ContainerControl>|<xref:System.Windows.Forms.AutoValidate.Inherit>|  
|<xref:System.Windows.Forms.Form>|<xref:System.Windows.Forms.AutoValidate.EnableAllowFocusChange>|  
|<xref:System.Windows.Forms.PropertyGrid>|プロパティが Visual Studio で公開されていません。|  
|<xref:System.Windows.Forms.ToolStripContainer>|プロパティが Visual Studio で公開されていません。|  
|<xref:System.Windows.Forms.SplitContainer>|<xref:System.Windows.Forms.AutoValidate.Inherit>|  
|<xref:System.Windows.Forms.UserControl>|<xref:System.Windows.Forms.AutoValidate.EnableAllowFocusChange>|  
  
## <a name="closing-the-form-and-overriding-validation"></a>フォームを閉じると検証をオーバーライドします。  
 コントロールに含まれるデータが無効であるためにフォーカスが保持されている場合、通常の方法のいずれかで親フォームを閉じることは不可能です。  
  
- **閉じる**ボタンをクリックします。  
  
- **システム**メニューで**閉じる**を選択します。  
  
- プログラムでメソッド<xref:System.Windows.Forms.Form.Close%2A>を呼び出します。  
  
 ただし、場合によっては、コントロールの値が有効かどうかに関係なく、ユーザーにフォームを閉じさせる必要があります。 フォームの<xref:System.Windows.Forms.Form.FormClosing>イベントのハンドラーを作成することにより、検証をオーバーライドして、無効なデータが含まれているフォームを閉じることができます。 イベントで、プロパティを<xref:System.ComponentModel.CancelEventArgs.Cancel%2A>に`false`設定します。 これにより、フォームが強制的に閉じされます。 使用例を含む詳細については、「<xref:System.Windows.Forms.Form.FormClosing?displayProperty=nameWithType>」を参照してください。  
  
> [!NOTE]
> この方法でフォームを強制的に閉じると、フォームのコントロール内のデータが、まだ保存されていない場合は失われます。 また、モーダル フォームは、コントロールが閉じられたときに、コントロールの内容を検証しません。 コントロールの検証を使用してコントロールにフォーカスをロックすることはできますが、フォームの閉じに関連する動作を気にする必要はありません。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.Control.Validating?displayProperty=nameWithType>
- <xref:System.Windows.Forms.Form.FormClosing?displayProperty=nameWithType>
- <xref:System.Windows.Forms.FormClosingEventArgs?displayProperty=nameWithType>
- [MaskedTextBox コントロール](./controls/maskedtextbox-control-windows-forms.md)
- [正規表現の例](../../standard/base-types/regular-expression-example-scanning-for-hrefs.md)
