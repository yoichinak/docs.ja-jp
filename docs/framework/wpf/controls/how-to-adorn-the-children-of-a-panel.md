---
title: '方法: パネルの子を装飾する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- adorners [WPF], binding to children of Panels
- Panel control [WPF], binding adorners to children
ms.assetid: 4cc9b972-b472-4e5c-bdf3-3702d7fbb1f5
ms.openlocfilehash: 746f197a5132934f94a678dc3b5e2a1f65eb93bd
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62019023"
---
# <a name="how-to-adorn-the-children-of-a-panel"></a>方法: パネルの子を装飾する
この例は、プログラムで、指定した子に装飾をバインドする方法を示しています。<xref:System.Windows.Controls.Panel>します。  
  
## <a name="example"></a>例  
 子に装飾をバインドする、 <xref:System.Windows.Controls.Panel>、これらの手順に従います。  
  
1. 新しい宣言<xref:System.Windows.Documents.AdornerLayer>オブジェクトと呼び出し、 `static` <xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A>メソッドを持つ子が装飾対象要素の装飾層が見つかりません。  
  
2. 呼び出し、親要素の子を列挙、<xref:System.Windows.Documents.AdornerLayer.Add%2A>メソッドを各子要素に装飾をバインドします。  
  
 次の例は、simplecircleadorner 参照の子に (上記) を連結、<xref:System.Windows.Controls.StackPanel>という*myStackPanel*します。  
  
 [!code-csharp[Adorners_SimpleCircleAdorner#_AdornChildren](~/samples/snippets/csharp/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/CSharp/Window1.xaml.cs#_adornchildren)]
 [!code-vb[Adorners_SimpleCircleAdorner#_AdornChildren](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/VisualBasic/Window1.xaml.vb#_adornchildren)]  
  
> [!NOTE]
>  [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] を使用して、装飾を別の要素にバインドする方法は、現在サポートされていません。  
  
## <a name="see-also"></a>関連項目

- [装飾の概要](adorners-overview.md)
