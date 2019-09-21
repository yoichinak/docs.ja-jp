---
title: '方法: イベントを使用してロールオーバー効果を作成する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- colors of elements [WPF], changing
- rollover effect [WPF]
- element colors [WPF], changing
ms.assetid: 3b20d028-6f1c-4b25-95d2-fa68cefbdb4c
ms.openlocfilehash: 3996a3b9bb976dd5f2e5b675de3894bbaba7d9d3
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69960387"
---
# <a name="how-to-create-a-rollover-effect-using-events"></a>方法: イベントを使用してロールオーバー効果を作成する
この例では、マウスポインターが要素によって占有されている領域を離れるときに、要素の色を変更する方法を示します。  
  
 この例は、 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]ファイルと分離コードファイルで構成されています。  
  
> [!NOTE]
> この例では、イベントの使用方法を示していますが、これと同じ効果を<xref:System.Windows.Trigger>得るには、スタイルでを使用することをお勧めします。 詳しくは、「 [スタイルとテンプレート](../controls/styling-and-templating.md)」をご覧ください。  
  
## <a name="example"></a>例  
 [!INCLUDE[TLA2#tla_titlexaml](../../../../includes/tla2sharptla-titlexaml-md.md)]次の例では、の<xref:System.Windows.Input.Mouse.MouseEnter> <xref:System.Windows.Controls.Border>周囲<xref:System.Windows.Controls.TextBlock>で構成されるユーザーインターフェイスを作成<xref:System.Windows.Controls.Border>し<xref:System.Windows.UIElement.MouseLeave> 、にイベントハンドラーとイベントハンドラーをアタッチします。  
  
 [!code-xaml[mouseenterMouseleave#MouseEnterLeaveSampleXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/mouseenterMouseleave/CSharp/Window1.xaml#mouseenterleavesamplexaml)]  
  
 次のコードでは、 <xref:System.Windows.UIElement.MouseEnter>イベント<xref:System.Windows.UIElement.MouseLeave>ハンドラーとイベントハンドラーを作成します。  マウスポインターがに<xref:System.Windows.Controls.Border>入ると、 <xref:System.Windows.Controls.Border>の背景が赤に変更されます。  マウスポインターがから<xref:System.Windows.Controls.Border>離れると、 <xref:System.Windows.Controls.Border>の背景が白に戻されます。  
  
 [!code-csharp[mouseenterMouseleave#MouseEnterLeaveSampleEventHandlers](~/samples/snippets/csharp/VS_Snippets_Wpf/mouseenterMouseleave/CSharp/Window1.xaml.cs#mouseenterleavesampleeventhandlers)]
 [!code-vb[mouseenterMouseleave#MouseEnterLeaveSampleEventHandlers](~/samples/snippets/visualbasic/VS_Snippets_Wpf/mouseenterMouseleave/VisualBasic/Window1.xaml.vb#mouseenterleavesampleeventhandlers)]
