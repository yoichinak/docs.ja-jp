---
title: '方法: バインディングの検証の実装'
ms.date: 03/30/2017
helpviewer_keywords:
- validation of binding [WPF]
- data binding [WPF], validation of binding
- binding [WPF], validation of
ms.assetid: eb98b33d-9866-49ae-b981-bc5ff20d607a
ms.openlocfilehash: 3950df8b6f4b48a035c6ebf37d8d65c18cb82e1e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59197218"
---
# <a name="how-to-implement-binding-validation"></a>方法: バインディングの検証の実装
この例は、使用する方法を示します、<xref:System.Windows.Controls.Validation.ErrorTemplate%2A>し、無効な値を入力したら、ユーザーに通知する視覚的なフィードバックを提供するスタイルのトリガーのカスタム検証規則に基づいています。  
  
## <a name="example"></a>例  
 テキストの内容、<xref:System.Windows.Controls.TextBox>に次の例では、バインド、 `Age` (int 型) のプロパティをという名前のバインディング ソース オブジェクトの`ods`します。 バインディングは、`AgeRangeRule` という名前の検証規則を使用するよう設定されているため、ユーザーが数字以外の文字、または 21 から 130 の範囲外の値を入力すると、テキスト ボックスの横に赤の感嘆符が表示され、ユーザーがテキスト ボックス上にマウスを置くとエラー メッセージを含んだツール ヒントが示されます。  
  
 [!code-xaml[BindValidation#2](~/samples/snippets/csharp/VS_Snippets_Wpf/BindValidation/CSharp/Window1.xaml#2)]  
  
 次の例の実装を示しています。 `AgeRangeRule`、から継承される<xref:System.Windows.Controls.ValidationRule>と上書き、<xref:System.Windows.Controls.ValidationRule.Validate%2A>メソッド。 Int32.Parse() メソッドは、値に無効な文字が含まれていないことを確認するために、値に対して呼び出されます。 <xref:System.Windows.Controls.ValidationRule.Validate%2A>メソッドを返します。 を<xref:System.Windows.Controls.ValidationResult>値が有効である、解析中に例外をキャッチするかどうかと、保存期間の値が下限と上限の外部でがかどうかに基づいていることを示します。  
  
 [!code-csharp[BindValidation#3](~/samples/snippets/csharp/VS_Snippets_Wpf/BindValidation/CSharp/AgeRangeRule.cs#3)]  
  
 次の例は、カスタム<xref:System.Windows.Controls.ControlTemplate>`validationTemplate`検証エラーをユーザーに通知する赤い感嘆符を作成します。 コントロール テンプレートは、コントロールの外観を再定義するために使用されます。  
  
 [!code-xaml[BindValidation#4](~/samples/snippets/csharp/VS_Snippets_Wpf/BindValidation/CSharp/Window1.xaml#4)]  
  
 次の例で示すように、<xref:System.Windows.Controls.ToolTip>という名前のスタイルを使用して、エラー メッセージが作成されたことを示す`textBoxInError`します。 場合の値<xref:System.Windows.Controls.Validation.HasError%2A>は`true`、トリガー設定の現在のツール ヒント<xref:System.Windows.Controls.TextBox>をその最初の検証エラー。 <xref:System.Windows.Data.Binding.RelativeSource%2A>に設定されている<xref:System.Windows.Data.RelativeSourceMode.Self>、現在の要素を参照します。  
  
 [!code-xaml[BindValidation#5](~/samples/snippets/csharp/VS_Snippets_Wpf/BindValidation/CSharp/Window1.xaml#5)]  
  
 コード例全体については、「[バインディングの検証のサンプル](https://go.microsoft.com/fwlink/?LinkID=159972)」をご覧ください。  
  
 カスタムを指定しない場合<xref:System.Windows.Controls.Validation.ErrorTemplate%2A>検証エラーがある場合に、ユーザーに視覚的なフィードバックを提供する既定のエラー テンプレートが表示されます。 詳しくは、「[データ バインドの概要](data-binding-overview.md)」の「データの検証」をご覧ください。 さらに [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] は、バインディング ソース プロパティの更新中にスローされる例外をキャッチするための、組み込みの検証規則を提供します。 詳細については、「 <xref:System.Windows.Controls.ExceptionValidationRule> 」を参照してください。  
  
## <a name="see-also"></a>関連項目

- [データ バインディングの概要](data-binding-overview.md)
- [方法トピック](data-binding-how-to-topics.md)
