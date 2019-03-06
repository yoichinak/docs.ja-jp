---
title: '方法: プロパティ値が変化したときにアニメーションをトリガーする'
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], starting when property values change
- triggering animation [WPF]
- Storyboards [WPF], starting when property values change
ms.assetid: 12399c21-0300-4f4f-9e3a-d92d9907e5f5
ms.openlocfilehash: 87f7525755556301fec3f00da612fc5262f1f533
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2019
ms.locfileid: "57356144"
---
# <a name="how-to-trigger-an-animation-when-a-property-value-changes"></a>方法: プロパティ値が変化したときにアニメーションをトリガーする
この例は、使用する方法を示します、<xref:System.Windows.Trigger>を開始する、<xref:System.Windows.Media.Animation.Storyboard>プロパティ値が変更されたとき。 使用することができます、<xref:System.Windows.Trigger>内で、 <xref:System.Windows.Style>、 <xref:System.Windows.Controls.ControlTemplate>、または<xref:System.Windows.DataTemplate>します。  
  
## <a name="example"></a>例  
 次の例では、<xref:System.Windows.Trigger>をアニメーション化する、<xref:System.Windows.UIElement.Opacity%2A>の<xref:System.Windows.Controls.Button>ときにその<xref:System.Windows.UIElement.IsMouseOver%2A>プロパティになります`true`します。  
  
 [!code-xaml[AnimatePropertyStoryboards#PropertyTriggerExample](~/samples/snippets/xaml/VS_Snippets_Wpf/AnimatePropertyStoryboards/XAML/PropertyTriggerExample.xaml#propertytriggerexample)]  
  
 プロパティによって適用されるアニメーション<xref:System.Windows.Trigger>オブジェクトよりもさらに複雑な方法で動作しますが<xref:System.Windows.EventTrigger>アニメーションまたはアニメーションの開始を使用して<xref:System.Windows.Media.Animation.Storyboard>メソッド。  「ハンドオフ」アニメーションによって他の定義、<xref:System.Windows.Trigger>オブジェクトで、compose を<xref:System.Windows.EventTrigger>メソッドによってトリガーされるアニメーションです。  
  
## <a name="see-also"></a>関連項目
- <xref:System.Windows.Trigger>
- [プロパティ アニメーションの手法の概要](property-animation-techniques-overview.md)
- [ストーリーボードの概要](storyboards-overview.md)
