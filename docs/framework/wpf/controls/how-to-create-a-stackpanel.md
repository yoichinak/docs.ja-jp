---
title: '方法: StackPanel を作成する'
ms.date: 03/30/2017
helpviewer_keywords:
- StackPanel control [WPF], creating
ms.assetid: e7ce65cb-720a-4bb6-95b6-286b74488a58
ms.openlocfilehash: 46b037e3f1626e77a61dca787b705a63ccd28ba0
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2019
ms.locfileid: "57360443"
---
# <a name="how-to-create-a-stackpanel"></a>方法: StackPanel を作成する
この例は、作成する方法を示します、<xref:System.Windows.Controls.StackPanel>します。  
  
## <a name="example"></a>例  
 A<xref:System.Windows.Controls.StackPanel>すると、指定した方向に要素を積み重ねることができます。 定義されているプロパティを使用して<xref:System.Windows.Controls.StackPanel>、コンテンツ流し込むことができます垂直方向に、これは、既定の設定、または水平方向にします。  
  
 次の例を垂直に積み重ねます 5<xref:System.Windows.Controls.TextBlock>制御する場合に、それぞれ異なる<xref:System.Windows.Controls.Border>と<xref:System.Windows.Controls.Border.Background%2A>を使用して<xref:System.Windows.Controls.StackPanel>します。 子要素を持つ指定されていない<xref:System.Windows.FrameworkElement.Width%2A>に親ウィンドウに合わせて伸縮。 ただし、子要素がある、指定した<xref:System.Windows.FrameworkElement.Width%2A>、ウィンドウ内で中央揃えされます。  
  
 既定のスタック方向、<xref:System.Windows.Controls.StackPanel>が垂直方向。 コンテンツの流れを制御する、<xref:System.Windows.Controls.StackPanel>を使用して、<xref:System.Windows.Controls.StackPanel.Orientation%2A>プロパティ。 使用して水平方向の配置を制御することができます、<xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>プロパティ。  
  
```xaml  
<Page xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation" WindowTitle="StackPanel Sample">  
  <StackPanel>  
    <Border Background="SkyBlue" BorderBrush="Black" BorderThickness="1">  
      <TextBlock Foreground="Black" FontSize="12">Stacked Item #1</TextBlock>  
    </Border>  
    <Border Width="400" Background="CadetBlue" BorderBrush="Black" BorderThickness="1">  
      <TextBlock Foreground="Black" FontSize="14">Stacked Item #2</TextBlock>  
    </Border>  
    <Border Background="LightGoldenRodYellow" BorderBrush="Black" BorderThickness="1">  
      <TextBlock Foreground="Black" FontSize="16">Stacked Item #3</TextBlock>  
    </Border>  
    <Border Width="200" Background="PaleGreen" BorderBrush="Black" BorderThickness="1">  
      <TextBlock Foreground="Black" FontSize="18">Stacked Item #4</TextBlock>  
    </Border>  
    <Border Background="White" BorderBrush="Black" BorderThickness="1">  
      <TextBlock Foreground="Black" FontSize="20">Stacked Item #5</TextBlock>  
    </Border>  
  </StackPanel>  
</Page>  
```  
  
## <a name="see-also"></a>関連項目
- <xref:System.Windows.Controls.StackPanel>
- [パネルの概要](panels-overview.md)
- [方法トピック](stackpanel-how-to-topics.md)
