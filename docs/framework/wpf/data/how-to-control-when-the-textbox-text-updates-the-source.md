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
ms.openlocfilehash: d1d624d7550a1135431b7fffc7450e3a510855a7
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69966447"
---
# <a name="how-to-control-when-the-textbox-text-updates-the-source"></a>方法: TextBox テキストでソースを更新するタイミングを制御する
このトピックでは、 <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A>プロパティを使用して、バインディングソースの更新のタイミングを制御する方法について説明します。 このトピックでは<xref:System.Windows.Controls.TextBox> 、例としてコントロールを使用します。  
  
## <a name="example"></a>例  
 <xref:System.Windows.Controls.TextBox>.<xref:System.Windows.Controls.TextBox.Text%2A> プロパティの<xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> <xref:System.Windows.Data.UpdateSourceTrigger.LostFocus>既定値はです。 これは、アプリケーションがデータバインド<xref:System.Windows.Controls.TextBox> <xref:System.Windows.Controls.TextBox>を持つを持っている場合を意味します。<xref:System.Windows.Controls.TextBox.Text%2A> プロパティ。に入力<xref:System.Windows.Controls.TextBox>したテキストは、が<xref:System.Windows.Controls.TextBox>フォーカスを失うまで (たとえば、をクリック<xref:System.Windows.Controls.TextBox>したとき)、ソースを更新しません。  
  
 入力時にソースを更新する場合は、バインディング<xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A>のをに<xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>設定します。 次の例では、強調表示`Text` <xref:System.Windows.Controls.TextBlock>されているコード行に、 <xref:System.Windows.Controls.TextBox>との両方のプロパティが同じソースプロパティにバインドされていることが示されています。 バインディングのプロパティがに<xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>設定されています。 <xref:System.Windows.Controls.TextBox>  
  
 [!code-xaml[SimpleBinding#USTHowTo](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleBinding/VisualBasic/Page1.xaml?highlight=33-39,41-42)]  
  
 その結果、次の<xref:System.Windows.Controls.TextBlock>サンプルのスクリーンショットに示すように、は、ユーザーが<xref:System.Windows.Controls.TextBox>にテキストを入力したときに (ソースが変更されたため) 同じテキストを表示します。  
  
 ![単純なデータバインディングを示すスクリーンショット。](./media/how-to-control-when-the-textbox-text-updates-the-source/data-binding-simple-binding-sample.png)  
  
 ダイアログまたはユーザーが編集可能なフォームがあり、ユーザーがフィールドの編集を完了して [OK] をクリックするまでソースの更新を延期する場合は<xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> 、次の例に<xref:System.Windows.Data.UpdateSourceTrigger.Explicit>示すように、バインドの値をに設定します。  
  
 [!code-xaml[UpdateSource#2](~/samples/snippets/csharp/VS_Snippets_Wpf/UpdateSource/CSharp/Window1.xaml#2)]  
  
 <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A>値をに<xref:System.Windows.Data.UpdateSourceTrigger.Explicit>設定すると、アプリケーションがメソッドを<xref:System.Windows.Data.BindingExpression.UpdateSource%2A>呼び出した場合にのみ、ソース値が変更されます。 次の例は、を<xref:System.Windows.Data.BindingExpression.UpdateSource%2A> `itemNameTextBox`呼び出す方法を示しています。  
  
 [!code-csharp[UpdateSource#1](~/samples/snippets/csharp/VS_Snippets_Wpf/UpdateSource/CSharp/Window1.xaml.cs#1)]
 [!code-vb[UpdateSource#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/UpdateSource/VisualBasic/Window1.xaml.vb#1)]  
  
> [!NOTE]
> 他のコントロールのプロパティにも同じ手法を使用でき<xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>ますが、その他のほとんどのプロパティには既定値が設定されていることに注意してください。 詳細については、 <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A>プロパティページを参照してください。  
  
> [!NOTE]
> プロパティ<xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A>はソースの更新を処理するため、または<xref:System.Windows.Data.BindingMode.TwoWay> <xref:System.Windows.Data.BindingMode.OneWayToSource>バインドにのみ関連します。 <xref:System.Windows.Data.BindingMode.TwoWay> および<xref:System.Windows.Data.BindingMode.OneWayToSource>バインドを機能させるには、ソースオブジェクトがプロパティ変更通知を提供する必要があります。 詳しくは、このトピック内にあるサンプルをご覧ください。 また、「[方法 : プロパティの変更通知を実装する](how-to-implement-property-change-notification.md)」もご覧ください。  
  
## <a name="see-also"></a>関連項目

- [方法トピック](data-binding-how-to-topics.md)
