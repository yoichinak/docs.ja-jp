---
title: '方法: 要素に装飾をバインドする'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- UIElements [WPF], binding adorners to
- adorners [WPF], binding to specified UIElements
ms.assetid: b2101611-a0ee-4137-bdb8-9b3673d2e6b9
ms.openlocfilehash: 54c9e6dfff2bbf7bfabde523b5d6ae5a623fe733
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59194722"
---
# <a name="how-to-bind-an-adorner-to-an-element"></a>方法: 要素に装飾をバインドする
この例は、プログラムで、指定された装飾をバインドする方法を示しています。<xref:System.Windows.UIElement>します。  
  
## <a name="example"></a>例  
 特定の装飾をバインドする<xref:System.Windows.UIElement>、これらの手順に従います。  
  
1.  呼び出す、`static`メソッド<xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A>を取得する、<xref:System.Windows.Documents.AdornerLayer>オブジェクト、<xref:System.Windows.UIElement>装飾対象にします。 <xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> 指定された、ビジュアル ツリーをウォーク**UIElement**、し、最初に見つかった装飾層を返します。 (装飾層が見つからない場合、メソッドにより null が返されます)。  
  
2.  呼び出す、<xref:System.Windows.Documents.AdornerLayer.Add%2A>ターゲットに装飾をバインドするメソッド**UIElement**します。  
  
 次の例では、simplecircleadorner に (上図) を参照、<xref:System.Windows.Controls.TextBox>という*myTextBox*します。  
  
 [!code-csharp[Adorners_SimpleCircleAdorner#_AdornSingleElement](~/samples/snippets/csharp/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/CSharp/Window1.xaml.cs#_adornsingleelement)]
 [!code-vb[Adorners_SimpleCircleAdorner#_AdornSingleElement](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/VisualBasic/Window1.xaml.vb#_adornsingleelement)]  
  
> [!NOTE]
>  [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] を使用して、装飾を別の要素にバインドする方法は、現在サポートされていません。  
  
## <a name="see-also"></a>関連項目

- [装飾の概要](adorners-overview.md)
