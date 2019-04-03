---
title: '方法: バインディングの方向を指定する'
ms.date: 03/30/2017
helpviewer_keywords:
- direction of binding [WPF]
- binding direction [WPF]
- data binding [WPF], direction of binding
ms.assetid: 37334478-028b-4514-86c9-1420709f4818
ms.openlocfilehash: 265271cee16d203d7652281c5416b93759e66d4b
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2019
ms.locfileid: "57378220"
---
# <a name="how-to-specify-the-direction-of-the-binding"></a>方法: バインディングの方向を指定する
この例では、バインドの更新先 (バインディング ターゲット (ターゲット) のプロパティのみ、バインディング ソース (ソース) のプロパティのみ、またはターゲットのプロパティとソースのプロパティの両方) を指定する方法を示します。  
  
## <a name="example"></a>例  
 使用する、<xref:System.Windows.Data.Binding.Mode%2A>プロパティ バインディングの方向を指定します。 次の列挙リストは、バインドの更新で使用できるオプションを示しています。  
  
-   <xref:System.Windows.Data.BindingMode.TwoWay> 対象となるプロパティまたはソースのプロパティのいずれかが変更されるたびに、ターゲット プロパティまたはプロパティを更新します。  
  
-   <xref:System.Windows.Data.BindingMode.OneWay> ソース プロパティが変更された場合にのみ、ターゲット プロパティを更新します。  
  
-   <xref:System.Windows.Data.BindingMode.OneTime> アプリケーションの起動時にのみ、またはターゲット プロパティを更新、<xref:System.Windows.FrameworkElement.DataContext%2A>で変更が行われます。  
  
-   <xref:System.Windows.Data.BindingMode.OneWayToSource> ターゲット プロパティが変更されたときに、ソース プロパティを更新します。  
  
-   <xref:System.Windows.Data.BindingMode.Default> により、既定<xref:System.Windows.Data.Binding.Mode%2A>に使用するターゲット プロパティの値。  
  
 詳細については、<xref:System.Windows.Data.BindingMode> 列挙型のページをご覧ください。  
  
 <xref:System.Windows.Data.Binding.Mode%2A> プロパティを設定する方法を次の例に示します。  
  
 [!code-xaml[DirectionalBinding#4](~/samples/snippets/csharp/VS_Snippets_Wpf/DirectionalBinding/CSharp/Page1.xaml#4)]  
  
 ソースの変更を検出するために (に適用できる<xref:System.Windows.Data.BindingMode.OneWay>と<xref:System.Windows.Data.BindingMode.TwoWay>バインド) など、ソースが適切なプロパティ変更通知のメカニズムを実装する必要があります<xref:System.ComponentModel.INotifyPropertyChanged>します。 参照してください[プロパティ変更通知を実装](how-to-implement-property-change-notification.md)の例については、<xref:System.ComponentModel.INotifyPropertyChanged>実装します。  
  
 <xref:System.Windows.Data.BindingMode.TwoWay>または<xref:System.Windows.Data.BindingMode.OneWayToSource>バインドを設定して、ソースの更新のタイミングを制御することができます、<xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A>プロパティ。 詳細については、「<xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A>」を参照してください。  
  
## <a name="see-also"></a>関連項目
- <xref:System.Windows.Data.Binding>
- [データ バインディングの概要](data-binding-overview.md)
- [方法トピック](data-binding-how-to-topics.md)
