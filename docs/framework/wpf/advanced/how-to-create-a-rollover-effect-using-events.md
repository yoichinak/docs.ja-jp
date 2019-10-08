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
ms.openlocfilehash: 806056397200fa5c567e83227499ba721544f523
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005181"
---
# <a name="how-to-create-a-rollover-effect-using-events"></a>方法: イベントを使用してロールオーバー効果を作成する
この例では、マウスポインターが要素によって占有されている領域を離れるときに、要素の色を変更する方法を示します。  
  
 この例は、@no__t 0 ファイルと分離コードファイルで構成されています。  
  
> [!NOTE]
> この例では、イベントの使用方法を示していますが、これと同じ効果を得るには、スタイルで <xref:System.Windows.Trigger> を使用することをお勧めします。 詳しくは、「 [スタイルとテンプレート](../controls/styling-and-templating.md)」をご覧ください。  
  
## <a name="example"></a>例  
 次の XAML は、<xref:System.Windows.Controls.TextBlock> の <xref:System.Windows.Controls.Border> で構成されるユーザーインターフェイスを作成し、<xref:System.Windows.Input.Mouse.MouseEnter> および <xref:System.Windows.UIElement.MouseLeave> のイベントハンドラーを @no__t にアタッチします。  
  
 [!code-xaml[mouseenterMouseleave#MouseEnterLeaveSampleXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/mouseenterMouseleave/CSharp/Window1.xaml#mouseenterleavesamplexaml)]  
  
 次のコードでは、<xref:System.Windows.UIElement.MouseEnter> と <xref:System.Windows.UIElement.MouseLeave> のイベントハンドラーを作成します。  マウスポインターが @no__t 0 に入ると、@no__t の背景が赤に変更されます。  マウスポインターが @no__t 0 から出ると、@no__t の背景が白に戻されます。  
  
 [!code-csharp[mouseenterMouseleave#MouseEnterLeaveSampleEventHandlers](~/samples/snippets/csharp/VS_Snippets_Wpf/mouseenterMouseleave/CSharp/Window1.xaml.cs#mouseenterleavesampleeventhandlers)]
 [!code-vb[mouseenterMouseleave#MouseEnterLeaveSampleEventHandlers](~/samples/snippets/visualbasic/VS_Snippets_Wpf/mouseenterMouseleave/VisualBasic/Window1.xaml.vb#mouseenterleavesampleeventhandlers)]
