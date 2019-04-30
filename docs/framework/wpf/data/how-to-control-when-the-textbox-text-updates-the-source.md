---
title: '方法: TextBox テキストでソースを更新するタイミングを制御する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- source updates [WPF], timing of
- data binding [WPF], timing of source updates
- timing of source updates [WPF]
ms.assetid: ffb7b96a-351d-4c68-81e7-054033781c64
ms.openlocfilehash: 5272a19f69b3caf80fd7d5187c9a6a386cd44621
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62052002"
---
# <a name="how-to-control-when-the-textbox-text-updates-the-source"></a>方法: TextBox テキストでソースを更新するタイミングを制御する
このトピックでは、使用する方法を説明します、<xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A>プロパティ バインディングのソースの更新のタイミングを制御するためです。 トピックを使用して、<xref:System.Windows.Controls.TextBox>などのコントロール。  
  
## <a name="example"></a>例  
 <xref:System.Windows.Controls.TextBox>.<xref:System.Windows.Controls.TextBox.Text%2A> プロパティは、既定値を持つ<xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A>@property<xref:System.Windows.Data.UpdateSourceTrigger.LostFocus>します。 つまり、アプリケーション、<xref:System.Windows.Controls.TextBox>データ バインドで<xref:System.Windows.Controls.TextBox>します。<xref:System.Windows.Controls.TextBox.Text%2A> 入力したテキスト、プロパティ、<xref:System.Windows.Controls.TextBox>までソースを更新できません、<xref:System.Windows.Controls.TextBox>がフォーカスを失った (からクリックすると、たとえば、 <xref:System.Windows.Controls.TextBox>)。  
  
 ソースの入力を更新する場合は、設定、<xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A>へのバインドの<xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>します。 次の例で強調表示された行のコードを表示する、`Text`両方のプロパティ、 <xref:System.Windows.Controls.TextBox> 、<xref:System.Windows.Controls.TextBlock>同じソース プロパティにバインドされます。 <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A>のプロパティ、<xref:System.Windows.Controls.TextBox>にバインディングが設定されている<xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>します。  
  
 [!code-xaml[SimpleBinding#USTHowTo](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleBinding/VisualBasic/Page1.xaml?highlight=33-39,41-42)]  
  
 結果として、<xref:System.Windows.Controls.TextBlock>にテキストを入力すると、(変更) ため、同じテキストを表示、<xref:System.Windows.Controls.TextBox>サンプルの次のスクリーン ショットに示しますように。  
  
 ![単純なデータ バインド サンプルのスクリーン ショット](./media/databindingsimplebindingsample2.png "DataBindingSimpleBindingSample2")  
  
 ダイアログまたはユーザーが編集できるフォームがあると、ユーザーがフィールドの編集が完了し、[OK] をクリックするまで、ソースの更新プログラムを延期する場合、設定することができる場合、<xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A>に、バインディングの<xref:System.Windows.Data.UpdateSourceTrigger.Explicit>、次の例。  
  
 [!code-xaml[UpdateSource#2](~/samples/snippets/csharp/VS_Snippets_Wpf/UpdateSource/CSharp/Window1.xaml#2)]  
  
 設定すると、<xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A>値を<xref:System.Windows.Data.UpdateSourceTrigger.Explicit>、アプリケーションを呼び出すときにのみソース値が変更、<xref:System.Windows.Data.BindingExpression.UpdateSource%2A>メソッド。 次の例は、呼び出す方法を示しています<xref:System.Windows.Data.BindingExpression.UpdateSource%2A>の`itemNameTextBox`:。  
  
 [!code-csharp[UpdateSource#1](~/samples/snippets/csharp/VS_Snippets_Wpf/UpdateSource/CSharp/Window1.xaml.cs#1)]
 [!code-vb[UpdateSource#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/UpdateSource/VisualBasic/Window1.xaml.vb#1)]  
  
> [!NOTE]
>  他のコントロールのプロパティの同じ手法を使用できますが、既定値をその他のほとんどのプロパティがあることに注意してください<xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A>@property<xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>します。 詳細については、次を参照してください。、<xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A>プロパティ ページ。  
  
> [!NOTE]
>  <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A>プロパティ ソースの更新処理であるため、関連するのみ<xref:System.Windows.Data.BindingMode.TwoWay>または<xref:System.Windows.Data.BindingMode.OneWayToSource>バインドします。 <xref:System.Windows.Data.BindingMode.TwoWay>と<xref:System.Windows.Data.BindingMode.OneWayToSource>するには、プロパティ変更通知を提供するソース オブジェクトのニーズへのバインド。 詳しくは、このトピック内にあるサンプルをご覧ください。 また、「[方法 : プロパティの変更通知を実装する](how-to-implement-property-change-notification.md)」もご覧ください。  
  
## <a name="see-also"></a>関連項目

- [方法トピック](data-binding-how-to-topics.md)
