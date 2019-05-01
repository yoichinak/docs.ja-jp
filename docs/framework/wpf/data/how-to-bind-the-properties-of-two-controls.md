---
title: '方法: 2 つのコントロールのプロパティをバインドする'
ms.date: 03/30/2017
helpviewer_keywords:
- data binding [WPF], binding properties of two controls
- binding properties of two controls [WPF]
- controls [WPF], binding properties of
ms.assetid: 06318fac-6afd-4c7d-a277-6d7ef50f47bc
ms.openlocfilehash: 332e8e0dfa30ff7aff27c95652f07446baf6511a
ms.sourcegitcommit: 89fcad7e816c12eb1299128481183f01c73f2c07
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/24/2019
ms.locfileid: "63809539"
---
# <a name="how-to-bind-the-properties-of-two-controls"></a>方法: 2 つのコントロールのプロパティをバインドする
この例を使用して別の 1 つのインスタンス化されたコントロールのプロパティをバインドする方法を示しています、<xref:System.Windows.Data.Binding.ElementName%2A>プロパティ。  
  
## <a name="example"></a>例  
 次の例では、バインドする方法を示しています、<xref:System.Windows.Controls.Panel.Background%2A>のプロパティを<xref:System.Windows.Controls.Canvas>を<xref:System.Windows.Controls.Primitives.Selector.SelectedItem%2A>します。<xref:System.Windows.Controls.ContentControl.Content%2A> プロパティを<xref:System.Windows.Controls.ComboBox>:  
  
 [!code-xaml[BindDptoDp#1](~/samples/snippets/csharp/VS_Snippets_Wpf/BindDPtoDP/CS/Window1.xaml#1)]  
  
 この例をレンダリングすると、次のようになります。  
  
![緑の値のボックスをオンし、緑色の四角形にコンボを示すスクリーン ショット。](./media/how-to-bind-the-properties-of-two-controls/data-binding-bind-background-canvas.png)

> [!NOTE]
> バインディング ターゲット プロパティ (この例で、<xref:System.Windows.Controls.Panel.Background%2A>プロパティ) 依存関係プロパティである必要があります。 詳しくは、「 [データ バインディングの概要](data-binding-overview.md)」をご覧ください。  
  
## <a name="see-also"></a>関連項目

- [バインディング ソースを指定する](how-to-specify-the-binding-source.md)
- [方法トピック](data-binding-how-to-topics.md)
