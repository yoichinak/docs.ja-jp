---
title: '方法: 簡単なバインディングを作成する'
ms.date: 03/30/2017
helpviewer_keywords:
- simple binding [WPF], creating
- data binding [WPF], creating simple bindings
- binding data [WPF], creating
ms.assetid: 69b80f72-6259-44cb-8294-5bdcebca1e08
ms.openlocfilehash: d617c8b97aa679398ed2d061a652f5164f1e499b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59094386"
---
# <a name="how-to-create-a-simple-binding"></a>方法: 簡単なバインディングを作成する
この例、単純なを作成する方法を示します<xref:System.Windows.Data.Binding>します。  
  
## <a name="example"></a>例  
 この例である、`Person`という名前の文字列プロパティを持つオブジェクト`PersonName`します。 `Person`という名前空間でオブジェクトが定義されている`SDKSample`します。  
  
 強調表示された行を含む、`<src>`次の例では、内の要素をインスタンス化、`Person`オブジェクトを`PersonName`プロパティの値`Joe`します。 これを行う、`Resources`セクションし、割り当てられている、`x:Key`します。  
  
 [!code-xaml[SimpleBinding](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Page1.xaml?highlight=9,37)]  
  
 強調表示された行を含む、`<TextBlock>`要素にバインドし、<xref:System.Windows.Controls.TextBlock>への制御、`PersonName`プロパティ。 結果として、 <xref:System.Windows.Controls.TextBlock> "Joe"の値が表示されます。  
  
## <a name="see-also"></a>関連項目

- [データ バインディングの概要](data-binding-overview.md)
- [方法トピック](data-binding-how-to-topics.md)
