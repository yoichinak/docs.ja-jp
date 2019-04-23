---
title: '方法: XAML でビューを使用してデータの並べ替えおよびグループ化を行う'
ms.date: 03/30/2017
helpviewer_keywords:
- data binding [WPF], grouping data in views in XAML
- XAML [WPF], sorting data in views
- grouping data in views in XAML [WPF]
- data binding [WPF], sorting data in views in XAML
- sorting data in views in XAML [WPF]
- XAML [WPF], grouping data in views
- views [WPF], sorting data
- views [WPF], grouping data
ms.assetid: 145c8c3f-dbdd-4d0d-816f-90b35eba7eda
ms.openlocfilehash: ca4439b574264ebebfda745f0765f750099bc95f
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59144522"
---
# <a name="how-to-sort-and-group-data-using-a-view-in-xaml"></a>方法: XAML でビューを使用してデータの並べ替えおよびグループ化を行う
この例でのデータ コレクションのビューを作成する方法を示しています。[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]します。 グループ化、並べ替え、フィルター処理、の機能と現在の項目の概念ビューを使用します。  
  
## <a name="example"></a>例  
 は、次の例では、静的リソースの名前*配置*のコレクションとして定義されて*場所*オブジェクトは、各*場所*オブジェクトは、市区町村名で構成されていましたし、状態。 プレフィックス*src*名前空間にマップされているデータ ソース*場所*が定義されています。 プレフィックス*scm*にマップ`"clr-namespace:System.ComponentModel;assembly=WindowsBase"`と*dat*マップ`"clr-namespace:System.Windows.Data;assembly=PresentationFramework"`します。  
  
 次の例では、市区町村名によって並べ替えられ、状態別にグループ化するデータ コレクションのビューを作成します。  
  
 [!code-xaml[CollectionViewSource#1](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionViewSource/CS/window1.xaml#1)]  
  
 ビューは、次の例のように、バインディング ソースに指定できます。  
  
 [!code-xaml[CollectionViewSource#2](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionViewSource/CS/window1.xaml#2)]  
  
 定義されている XML データへのバインドの<xref:System.Windows.Data.XmlDataProvider>リソース、XML 名の前に、@ 記号。  
  
 [!code-xaml[CollectionViewSource#XDPChunk](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionViewSource/CS/window1.xaml#xdpchunk)]  
  
 [!code-xaml[CollectionViewSource#Attribute](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionViewSource/CS/window1.xaml#attribute)]  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Data.CollectionViewSource>
- [データ コレクションの既定のビューを取得する](how-to-get-the-default-view-of-a-data-collection.md)
- [データ バインディングの概要](data-binding-overview.md)
- [方法トピック](data-binding-how-to-topics.md)
