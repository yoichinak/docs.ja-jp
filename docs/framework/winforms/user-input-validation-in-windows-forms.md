---
title: Windows フォームでのユーザー入力の検証
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, validating user input
- validation [Windows Forms], Windows Forms user input
- user input [Windows Forms], validating in Windows Forms
- validating user input [Windows Forms], Windows Forms
ms.assetid: 4ec07681-1dee-4bf9-be5e-718f635a33a1
ms.openlocfilehash: fb804e6596de14d93ec6f0405480b60c03c7cbf9
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/09/2019
ms.locfileid: "57711318"
---
# <a name="user-input-validation-in-windows-forms"></a>Windows フォームでのユーザー入力の検証
ユーザーがアプリケーションにデータを入力すると、アプリケーションが使用する前に、データが有効であることを確認したい場合があります。 特定のテキスト フィールドである長さがゼロで電話番号または正しい形式のデータの他の種類として、フィールドの形式、または文字列にデータベースのセキュリティを侵害される可能性があります安全でない文字が含まれていない場合があります。 Windows フォームでは、アプリケーションでの入力を検証するためのいくつかの方法を提供します。  
  
## <a name="validation-with-the-maskedtextbox-control"></a>MaskedTextBox コントロールによる検証  
 電話番号や部品番号などの明確に定義された形式でデータを入力するように要求する必要がある場合は、これを行う手早く、最小限のコードを使用して、<xref:System.Windows.Forms.MaskedTextBox>コントロール。 A*マスク*文字列で、所定の位置でテキスト ボックスに入力できる文字を指定するマスク言語の文字で構成されます。 コントロールには、ユーザーに一連のプロンプトが表示されます。 場合は、ユーザーは、正しくないエントリが、たとえば、1 桁の数字が必要な場合、文字を入力、コントロールは、入力を自動的に拒否します。  
  
 によって使用されるマスク言語<xref:System.Windows.Forms.MaskedTextBox>は非常に柔軟です。 必要な文字、省略可能な文字、ハイフン、かっこなどのリテラル文字、通貨記号、および日付の区切り記号を指定することができます。 コントロールも、データ ソースにバインドした場合でも機能します。 <xref:System.Windows.Forms.Binding.Format>データ バインディングでのイベントを使用して、マスクに準拠する受信データを再フォーマットと<xref:System.Windows.Forms.Binding.Parse>イベントを使用して、データ フィールドの仕様に準拠する送信データを再フォーマットします。  
  
 詳細については、次を参照してください。 [MaskedTextBox コントロール](./controls/maskedtextbox-control-windows-forms.md)します。  
  
## <a name="event-driven-validation"></a>イベント ドリブンの検証  
 検証をプログラムにより完全に制御するか、または複雑な検証チェックを実行する必要がある場合は、ほとんどの Windows フォーム コントロールに組み込まれている検証イベントを使用する必要があります。 自由形式のユーザー入力を受け付ける各コントロールには、<xref:System.Windows.Forms.Control.Validating>コントロール データの検証に必要なときに発生するイベントです。 <xref:System.Windows.Forms.Control.Validating>イベント処理メソッドをいくつかの方法で入力するユーザーを検証することができます。 たとえば、郵便番号コードを含める必要があるテキスト ボックスがある場合は、次の方法で検証を実行できます。  
  
-   郵便番号は、郵便番号の特定のグループに属している必要がある場合、ユーザーが入力したデータを検証する入力文字列の比較を実行できます。 たとえば、郵便番号は、{10001、10002、10003} のセットである必要がある場合は、データを検証する文字列比較を使用できます。  
  
-   特定の形式である必要があります、郵便場合は、ユーザーが入力データを検証する正規表現を使用できます。 たとえば、フォームを検証する`#####`または`#####-####`、正規表現を使用する`^(\d{5})(-\d{4})?$`します。 フォームを検証する`A#A #A#`、正規表現を使用する`[A-Z]\d[A-Z] \d[A-Z]\d`します。 正規表現の詳細については、次を参照してください。 [.NET Framework の正規表現](../../standard/base-types/regular-expressions.md)と[正規表現の例](../../standard/base-types/regular-expression-examples.md)します。  
  
-   郵便番号は有効な米国郵便である必要があります、ユーザーが入力データを検証する郵便番号/zip code Web サービスを呼び出すことでした。  
  
 <xref:System.Windows.Forms.Control.Validating>イベントが指定された型のオブジェクト<xref:System.ComponentModel.CancelEventArgs>します。 キャンセルすることができます、コントロールのデータが無効であると判断した場合、<xref:System.Windows.Forms.Control.Validating>するには、このオブジェクトのイベント<xref:System.ComponentModel.CancelEventArgs.Cancel%2A>プロパティを`true`します。 設定しない場合、<xref:System.ComponentModel.CancelEventArgs.Cancel%2A>プロパティ、Windows フォームは、そのコントロールが正常に検証を前提としていて、発生させる、<xref:System.Windows.Forms.Control.Validated>イベント。  
  
 電子メール アドレスを検証するコード例については、<xref:System.Windows.Controls.TextBox>を参照してください<xref:System.Windows.Forms.Control.Validating>します。  
  
### <a name="data-binding-and-event-driven-validation"></a>データ バインディングとイベント ドリブンの検証  
 検証は、データベース テーブルなどのデータ ソースにコントロールをバインドした場合に非常に便利です。 確認することができます、検証を使用して、コントロールのデータは、データ ソースで必要な形式を満たすことにはない引用符などの特殊文字を含めることとできない可能性がありますセーフ。  
  
 実行中に、データ ソースと、コントロール内のデータが同期されるデータ バインディングを使用するときに、<xref:System.Windows.Forms.Control.Validating>イベント。 キャンセルした場合、<xref:System.Windows.Forms.Control.Validating>イベント、データは、データ ソースと同期されません。  
  
> [!IMPORTANT]
>  カスタムの検証後に行われる必要がある場合、<xref:System.Windows.Forms.Control.Validating>イベントには、データ バインディングで影響しません。 コードがある場合など、<xref:System.Windows.Forms.Control.Validated>イベント データ バインディングをキャンセルしようとしているデータ バインディングはでも実行されます。 検証を実行するのには、この場合で、<xref:System.Windows.Forms.Control.Validated>イベント、変更、コントロールの**データ ソース更新モード**プロパティ (**(Databindings) **\\ **(詳細)**) から **[onvalidation]** に**Never**、追加*コントロール*`.DataBindings["`*\<YOURFIELD >* `"].WriteValue()`検証コードにします。  
  
### <a name="implicit-and-explicit-validation"></a>明示的および暗黙的な検証  
 これはコントロールのデータを取得検証ときでしょうか。 これは、ユーザー、開発者が決定できます。 アプリケーションのニーズに応じて、暗黙的または明示的のいずれかの検証を使用することができます。  
  
#### <a name="implicit-validation"></a>暗黙的な検証  
 暗黙的な検証方法は、ユーザーが入力するようにデータを検証します。 データは、ユーザーが 1 つのコントロールから入力フォーカスを受け取るし、次に移動されるたびによくが押されたキーを読み取ることによって、コントロール、または複数の入力としてデータを検証できます。 この方法は、作業しているように、データに関するユーザーの即時フィードバックを提供する場合に便利です。  
  
 コントロールの暗黙的な検証を使用する場合は、そのコントロールを設定する必要があります<xref:System.Windows.Forms.ContainerControl.AutoValidate%2A>プロパティを`true`します。 キャンセルした場合、<xref:System.Windows.Forms.Control.Validating>イベント、コントロールの動作に割り当てられている値によって決定されます<xref:System.Windows.Forms.ContainerControl.AutoValidate%2A>します。 割り当てた場合<xref:System.Windows.Forms.AutoValidate.EnablePreventFocusChange>、イベントをキャンセルすると、<xref:System.Windows.Forms.Control.Validated>イベントが発生するされません。 ユーザーが有効な入力データを変更するまで、現在のコントロールに入力フォーカスが残ります。 割り当てた場合<xref:System.Windows.Forms.AutoValidate.EnableAllowFocusChange>、<xref:System.Windows.Forms.Control.Validated>イベントはイベントをキャンセルするが、次のコントロールにフォーカスを移動も発生しません。  
  
 割り当てる<xref:System.Windows.Forms.AutoValidate.Disable>を<xref:System.Windows.Forms.ContainerControl.AutoValidate%2A>プロパティ暗黙的な検証はまったく行われません。 コントロールを検証するには、明示的な検証を使用する必要があります。  
  
#### <a name="explicit-validation"></a>明示的な検証  
 明示的な検証方法では、一度に 1 つのデータを検証します。 [保存] ボタンまたは [次へ] のリンクのクリックしてなどのユーザー アクションへの応答内のデータを検証することができます。 ユーザー アクションが発生したときに、明示的な検証をトリガーするには、次の方法のいずれか。  
  
-   呼び出す<xref:System.Windows.Forms.ContainerControl.Validate%2A>フォーカスが失われた最後のコントロールを検証します。  
  
-   呼び出す<xref:System.Windows.Forms.ContainerControl.ValidateChildren%2A>フォームまたはコンテナー コントロール内のすべての子コントロールを検証します。  
  
-   コントロールのデータを手動で検証するカスタム メソッドを呼び出します。  
  
#### <a name="default-implicit-validation-behavior-for-windows-forms-controls"></a>フォーム コントロールの Windows の既定の暗黙的な検証の動作  
 別の Windows フォーム コントロールの既定値がある、<xref:System.Windows.Forms.ContainerControl.AutoValidate%2A>プロパティ。 次の表は、最も一般的なコントロールとその既定値を示します。  
  
|コントロール|既定の検証動作|  
|-------------|---------------------------------|  
|<xref:System.Windows.Forms.ContainerControl>|<xref:System.Windows.Forms.AutoValidate.Inherit>|  
|<xref:System.Windows.Forms.Form>|<xref:System.Windows.Forms.AutoValidate.EnableAllowFocusChange>|  
|<xref:System.Windows.Forms.PropertyGrid>|Visual Studio で公開されていないプロパティ|  
|<xref:System.Windows.Forms.ToolStripContainer>|Visual Studio で公開されていないプロパティ|  
|<xref:System.Windows.Forms.SplitContainer>|<xref:System.Windows.Forms.AutoValidate.Inherit>|  
|<xref:System.Windows.Forms.UserControl>|<xref:System.Windows.Forms.AutoValidate.EnableAllowFocusChange>|  
  
## <a name="closing-the-form-and-overriding-validation"></a>フォームを閉じると、検証をオーバーライドします。  
 コントロールは、含まれるデータが無効であるために、フォーカスを維持、ときに、通常の方法のいずれかで、親フォームを閉じることはできません。  
  
-   クリックして、**閉じる**ボタンをクリックします。  
  
-   選択して**閉じる**で、**システム**メニュー。  
  
-   呼び出すことによって、<xref:System.Windows.Forms.Form.Close%2A>メソッド プログラムを使用します。  
  
 ただし、場合によっては、ユーザーがコントロール内の値が有効かどうかに関係なく、フォームを閉じますできる必要があります。 検証をオーバーライドして、フォームのハンドラーを作成して、無効なデータをまだ含まれているフォームを閉じます<xref:System.Windows.Forms.Form.Closing>イベント。 イベントでは、設定、<xref:System.ComponentModel.CancelEventArgs.Cancel%2A>プロパティを`false`します。 これにより、フォームを閉じます。 使用例を含む詳細については、「<xref:System.Windows.Forms.Form.Closing?displayProperty=nameWithType>」を参照してください。  
  
> [!NOTE]
>  この方法で終了するためのフォームを強制する場合、既に保存されていないフォームのコントロール内のデータは失われます。 さらに、モーダル フォームは、閉じられるときにコントロールの内容を検証できません。 コントロールにフォーカスをロックするコントロールの検証を使用することもできますが、フォームを閉じようと関連付けられた動作を考慮する必要はありません。  
  
## <a name="see-also"></a>関連項目
- <xref:System.Windows.Forms.Control.Validating?displayProperty=nameWithType>
- <xref:System.Windows.Forms.Form.Closing?displayProperty=nameWithType>
- <xref:System.ComponentModel.CancelEventArgs?displayProperty=nameWithType>
- [MaskedTextBox コントロール](./controls/maskedtextbox-control-windows-forms.md)
- [正規表現の例](../../standard/base-types/regular-expression-examples.md)
