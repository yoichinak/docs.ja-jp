---
title: '方法: バインディングの方向を指定する'
ms.date: 03/30/2017
helpviewer_keywords:
- direction of binding [WPF]
- binding direction [WPF]
- data binding [WPF], direction of binding
ms.assetid: 37334478-028b-4514-86c9-1420709f4818
ms.openlocfilehash: 023cd42ad5fb321e7ffa65f08673cb4145f49af4
ms.sourcegitcommit: 10736f243dd2296212e677e207102c463e5f143e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/06/2019
ms.locfileid: "68817912"
---
# <a name="how-to-specify-the-direction-of-the-binding"></a>方法: バインディングの方向を指定します

この例では、バインドの更新先 (バインディング ターゲット (ターゲット) のプロパティのみ、バインディング ソース (ソース) のプロパティのみ、またはターゲットのプロパティとソースのプロパティの両方) を指定する方法を示します。  
  
## <a name="example"></a>例  
 バインディングの方向<xref:System.Windows.Data.Binding.Mode%2A?displayProperty=nameWithType>を指定するには、プロパティを使用します。 更新プログラムのバインドに使用できるオプションを次に示します。  
  
- <xref:System.Windows.Data.BindingMode.TwoWay?displayProperty=nameWithType>ターゲットプロパティまたはソースプロパティが変更されるたびに、ターゲットプロパティまたはプロパティを更新します。  
  
- <xref:System.Windows.Data.BindingMode.OneWay?displayProperty=nameWithType>ソースプロパティが変更された場合にのみ、ターゲットプロパティを更新します。  
  
- <xref:System.Windows.Data.BindingMode.OneTime?displayProperty=nameWithType>アプリケーションが開始されたとき、またはが<xref:System.Windows.FrameworkElement.DataContext%2A>変更を行ったときにのみ、ターゲットプロパティを更新します。  
  
- <xref:System.Windows.Data.BindingMode.OneWayToSource?displayProperty=nameWithType>ターゲットプロパティが変更されたときに、source プロパティを更新します。  
  
- <xref:System.Windows.Data.BindingMode.Default?displayProperty=nameWithType>ターゲットプロパティの<xref:System.Windows.Data.Binding.Mode%2A>既定値が使用されます。  
  
 詳細については、<xref:System.Windows.Data.BindingMode> 列挙型のページをご覧ください。  
  
 <xref:System.Windows.Data.Binding.Mode%2A> プロパティを設定する方法を次の例に示します。  
  
 [!code-xaml[DirectionalBinding#4](~/samples/snippets/csharp/VS_Snippets_Wpf/DirectionalBinding/CSharp/Page1.xaml#4)]  
  
 ソースの変更 (および<xref:System.Windows.Data.BindingMode.OneWay> <xref:System.Windows.Data.BindingMode.TwoWay>バインドに適用可能) を検出するには、ソースがなど<xref:System.ComponentModel.INotifyPropertyChanged>の適切なプロパティ変更通知機構を実装する必要があります。 <xref:System.ComponentModel.INotifyPropertyChanged>実装の例については、「[プロパティ変更通知の実装](how-to-implement-property-change-notification.md)」を参照してください。  
  
 また<xref:System.Windows.Data.BindingMode.TwoWay>は<xref:System.Windows.Data.BindingMode.OneWayToSource>のバインドでは、 <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A>プロパティを設定することによって、ソースの更新のタイミングを制御できます。 詳細については、「<xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A>」を参照してください。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Data.Binding>
- [データ バインディングの概要](data-binding-overview.md)
- [方法トピック](data-binding-how-to-topics.md)
