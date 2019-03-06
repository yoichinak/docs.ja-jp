---
title: '方法: データ CollectionView のオブジェクト間を移動する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- CollectionView [WPF], navigating through objects
- data binding [WPF], navigating through objects in data CollectionView
- navigating through objects in data CollectionView [WPF]
ms.assetid: fcd37590-bce1-4ac9-8b74-3b96c7458b8a
ms.openlocfilehash: 9272a2f635a62abdac2746f2c8cce515812706f6
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2019
ms.locfileid: "57355780"
---
# <a name="how-to-navigate-through-the-objects-in-a-data-collectionview"></a>方法: データ CollectionView のオブジェクト間を移動する
ビューでは、並べ替え、フィルター処理、またはグループ化に応じて、さまざまな方法で表示する同じデータ収集を許可します。 ビューは、現在のレコード ポインターの概念を提供し、ポインターの移動を有効にします。 この例で提供される機能を使用してデータ コレクションのオブジェクト間を移動するほか、現在のオブジェクトを取得する方法を示しています、<xref:System.Windows.Data.CollectionView>クラス。  
  
## <a name="example"></a>例  
 この例で`myCollectionView`は、<xref:System.Windows.Data.CollectionView>ビューでバインドされたコレクションであるオブジェクト。  
  
 次の例では、`OnButton`のイベント ハンドラー、`Previous`と`Next`により、ユーザー データのコレクションを移動するボタンであるアプリケーションでは、ボタン。 なお、<xref:System.Windows.Data.CollectionView.IsCurrentBeforeFirst%2A>と<xref:System.Windows.Data.CollectionView.IsCurrentAfterLast%2A>プロパティを報告するかどうか、現在のレコード ポインターに来た、先頭と末尾のリストのそれぞれためを<xref:System.Windows.Data.CollectionView.MoveCurrentToFirst%2A>と<xref:System.Windows.Data.CollectionView.MoveCurrentToLast%2A>として適切に呼び出すことができます。  
  
 <xref:System.Windows.Data.CollectionView.CurrentItem%2A>としてキャストは、ビューのプロパティ、`Order`コレクション内の現在の注文アイテムを返します。  
  
 [!code-csharp[CollectionView#OnButton](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionView/CSharp/Page1.xaml.cs#onbutton)]
 [!code-vb[CollectionView#OnButton](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CollectionView/VisualBasic/Page1.xaml.vb#onbutton)]  
  
## <a name="see-also"></a>関連項目
- [データ バインディングの概要](data-binding-overview.md)
- [ビュー内のデータの並べ替え](how-to-sort-data-in-a-view.md)
- [ビュー内のデータをフィルター処理する](how-to-filter-data-in-a-view.md)
- [XAML でビューを使用してデータの並べ替えおよびグループ化を行う](how-to-sort-and-group-data-using-a-view-in-xaml.md)
- [方法トピック](data-binding-how-to-topics.md)
