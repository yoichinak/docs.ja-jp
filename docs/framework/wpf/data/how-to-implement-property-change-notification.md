---
title: '方法: プロパティの変更通知を実装する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- notifications of change [WPF]
- data binding [WPF], property change notifications
- change notifications [WPF]
- properties [WPF], change notifications
ms.assetid: 30b59d9e-8c3a-4349-aa82-4be837e841cf
ms.openlocfilehash: d37d468acc94470be8c2afdc495b40168932ec83
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59204355"
---
# <a name="how-to-implement-property-change-notification"></a>方法: プロパティの変更通知を実装する
（たとえば、ユーザーがフォームを編集したときに自動的にプレビューペインを更新する）バインディングの動的な変更を自動的にバインディングのターゲットとなるプロパティに反映するために、<xref:System.Windows.Data.BindingMode.OneWay>または<xref:System.Windows.Data.BindingMode.TwoWay>のバインディングをサポートするには、適切なプロパティ変更通知を提供しなければなりません。 次の例は、<xref:System.ComponentModel.INotifyPropertyChanged>を実装するクラスの作り方を示します。  
  
## <a name="example"></a>例  
 <xref:System.ComponentModel.INotifyPropertyChanged>を実装するために、<xref:System.ComponentModel.INotifyPropertyChanged.PropertyChanged>イベントを宣言して、`OnPropertyChanged`メソッドを作成します。 次に、変更を通知する必要のある各プロパティについて、そのプロパティが更新されるたびに `OnPropertyChanged` を呼び出します。  
  
 [!code-csharp[SimpleBinding#PersonClass](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Person.cs#personclass)]
 [!code-vb[SimpleBinding#PersonClass](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleBinding/VisualBasic/Person.vb#personclass)]  
  
 `Person`クラスがどのように<xref:System.Windows.Data.BindingMode.TwoWay>バインドをサポートしているか、[ TextBox テキストで、ソースを更新するタイミングを制御する](how-to-control-when-the-textbox-text-updates-the-source.md)を参照して下さい。  
  
## <a name="see-also"></a>関連項目

- [バインディング ソースの概要](binding-sources-overview.md)
- [データ バインディングの概要](data-binding-overview.md)
- [方法トピック](data-binding-how-to-topics.md)
