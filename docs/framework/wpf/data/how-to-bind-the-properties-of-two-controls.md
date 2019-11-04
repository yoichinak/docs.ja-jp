---
title: '方法 : 2 つのコントロールのプロパティをバインドする'
ms.date: 03/30/2017
helpviewer_keywords:
- data binding [WPF], binding properties of two controls
- binding properties of two controls [WPF]
- controls [WPF], binding properties of
ms.assetid: 06318fac-6afd-4c7d-a277-6d7ef50f47bc
ms.openlocfilehash: 66c759c28747de5b0288c906f5d51e4253fb7d52
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459170"
---
# <a name="how-to-bind-the-properties-of-two-controls"></a>方法 : 2 つのコントロールのプロパティをバインドする
この例では、<xref:System.Windows.Data.Binding.ElementName%2A> プロパティを使用して、インスタンス化されたコントロールのプロパティを別のコントロールのプロパティにバインドする方法を示します。  
  
## <a name="example"></a>例  
 次の例は、<xref:System.Windows.Controls.Canvas> の <xref:System.Windows.Controls.Panel.Background%2A> プロパティを <xref:System.Windows.Controls.Primitives.Selector.SelectedItem%2A>にバインドする方法を示しています。<xref:System.Windows.Controls.ContentControl.Content%2A> <xref:System.Windows.Controls.ComboBox>のプロパティ:  
  
 [!code-xaml[BindDptoDp#1](~/samples/snippets/csharp/VS_Snippets_Wpf/BindDPtoDP/CS/Window1.xaml#1)]  
  
 この例をレンダリングすると、次のようになります。  
  
![緑色の値が選択されたコンボボックスと緑色の四角形を示すスクリーンショット。](./media/how-to-bind-the-properties-of-two-controls/data-binding-bind-background-canvas.png)

> [!NOTE]
> バインディングターゲットプロパティ (この例では <xref:System.Windows.Controls.Panel.Background%2A> プロパティ) は依存関係プロパティである必要があります。 詳しくは、「[データ バインディングの概要](../../../desktop-wpf/data/data-binding-overview.md)」をご覧ください。  
  
## <a name="see-also"></a>関連項目

- [バインディング ソースを指定する](how-to-specify-the-binding-source.md)
- [方法トピック](data-binding-how-to-topics.md)
