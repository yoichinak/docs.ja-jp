---
title: '方法: ビュー内のデータの並べ替え'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data binding [WPF], sorting data in views
- data binding [WPF], grouping data in views
- grouping data in views [WPF]
- views [WPF], sorting data
- views [WPF], grouping data
- sorting data in views [WPF]
ms.assetid: f4c43578-01b7-4774-a953-acb95a13b94a
ms.openlocfilehash: 41ee5cded04559acac5e7270c5e1a2450c70a5aa
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2019
ms.locfileid: "57377120"
---
# <a name="how-to-sort-data-in-a-view"></a>方法: ビュー内のデータの並べ替え
この例では、ビュー内のデータを並べ替える方法について説明します。  
  
## <a name="example"></a>例  
 次の例では、単純な<xref:System.Windows.Controls.ListBox>と<xref:System.Windows.Controls.Button>:  
  
 [!code-xaml[ListBoxSort_snip#HowTo](~/samples/snippets/csharp/VS_Snippets_Wpf/ListBoxSort_snip/CSharp/Window1.xaml#howto)]  
  
 <xref:System.Windows.Controls.Primitives.ButtonBase.Click>ボタンのイベント ハンドラーには内の項目の並べ替えにロジックが含まれています、<xref:System.Windows.Controls.ListBox>降順にします。 これを行うために項目を追加、<xref:System.Windows.Controls.ListBox>この方法を追加すること、<xref:System.Windows.Controls.ItemCollection>の<xref:System.Windows.Controls.ListBox>、および<xref:System.Windows.Controls.ItemCollection>から派生した、<xref:System.Windows.Data.CollectionView>クラス。 バインドしている場合、<xref:System.Windows.Controls.ListBox>を使用してコレクションに、<xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>プロパティの並べ替えには同じ手法を使用することができます。  
  
 [!code-csharp[ListBoxSort_snip#HowToCode](~/samples/snippets/csharp/VS_Snippets_Wpf/ListBoxSort_snip/CSharp/Window1.xaml.cs#howtocode)]
 [!code-vb[ListBoxSort_snip#HowToCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ListBoxSort_snip/visualbasic/window1.xaml.vb#howtocode)]  
  
 ビューのオブジェクトへの参照がある限り、他のコレクション ビューのコンテンツを並べ替えるには同じ手法を使用できます。 ビューを取得する方法の例は、次を参照してください。[データ コレクションの既定のビューを取得](how-to-get-the-default-view-of-a-data-collection.md)します。 別の例では、次を参照してください。[を GridView の列のヘッダーがクリックされたときの並べ替え](../controls/how-to-sort-a-gridview-column-when-a-header-is-clicked.md)します。 ビューの詳細については、コレクションへのバインドを参照してください。[データ バインディングの概要](data-binding-overview.md)します。  
  
 並べ替えのロジックを適用する方法の例については[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]を参照してください[並べ替えとグループを使用して XAML でビューをデータ](how-to-sort-and-group-data-using-a-view-in-xaml.md)します。  
  
## <a name="see-also"></a>関連項目
- <xref:System.Windows.Data.ListCollectionView.CustomSort%2A>
- [ヘッダーがクリックされたときに GridView 列を並べ替える](../controls/how-to-sort-a-gridview-column-when-a-header-is-clicked.md)
- [データ バインディングの概要](data-binding-overview.md)
- [ビュー内のデータをフィルター処理する](how-to-filter-data-in-a-view.md)
- [方法トピック](data-binding-how-to-topics.md)
