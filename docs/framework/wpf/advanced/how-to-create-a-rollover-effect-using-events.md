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
ms.openlocfilehash: 87740a215136863199d962a2704cf691f27fc3bc
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61776650"
---
# <a name="how-to-create-a-rollover-effect-using-events"></a>方法: イベントを使用してロールオーバー効果を作成する
この例では、マウス ポインターが要素によって占有されている領域に出入りするように、要素の色を変更する方法を示します。  
  
 この例は、[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]ファイルと分離コード ファイル。  
  
> [!NOTE]
>  この例は、イベントを使用する方法を示しますが、これと同じ効果を実現するために推奨される方法は、使用する、<xref:System.Windows.Trigger>スタイル。 詳しくは、「 [スタイルとテンプレート](../controls/styling-and-templating.md)」をご覧ください。  
  
## <a name="example"></a>例  
 次[!INCLUDE[TLA2#tla_titlexaml](../../../../includes/tla2sharptla-titlexaml-md.md)]で構成されるユーザー インターフェイスを作成します<xref:System.Windows.Controls.Border>の周囲を<xref:System.Windows.Controls.TextBlock>、アタッチと、<xref:System.Windows.Input.Mouse.MouseEnter>と<xref:System.Windows.UIElement.MouseLeave>イベント ハンドラーを<xref:System.Windows.Controls.Border>します。  
  
 [!code-xaml[mouseenterMouseleave#MouseEnterLeaveSampleXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/mouseenterMouseleave/CSharp/Window1.xaml#mouseenterleavesamplexaml)]  
  
 次のコードを作成、<xref:System.Windows.UIElement.MouseEnter>と<xref:System.Windows.UIElement.MouseLeave>イベント ハンドラー。  マウス ポインターが入ったとき、<xref:System.Windows.Controls.Border>の背景、<xref:System.Windows.Controls.Border>赤に変更されます。  マウスのポインターから離したときに、<xref:System.Windows.Controls.Border>の背景、<xref:System.Windows.Controls.Border>が白に変更します。  
  
 [!code-csharp[mouseenterMouseleave#MouseEnterLeaveSampleEventHandlers](~/samples/snippets/csharp/VS_Snippets_Wpf/mouseenterMouseleave/CSharp/Window1.xaml.cs#mouseenterleavesampleeventhandlers)]
 [!code-vb[mouseenterMouseleave#MouseEnterLeaveSampleEventHandlers](~/samples/snippets/visualbasic/VS_Snippets_Wpf/mouseenterMouseleave/VisualBasic/Window1.xaml.vb#mouseenterleavesampleeventhandlers)]
