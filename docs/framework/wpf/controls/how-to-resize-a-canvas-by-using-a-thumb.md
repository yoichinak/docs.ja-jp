---
title: '方法: つまみを使用したキャンバスのサイズ変更'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- resizing Canvas control [WPF]
- controls [WPF], Thumb
- controls [WPF], Canvas
- Thumb control [WPF]
- Canvas control [WPF]
ms.assetid: 7dc9f435-726c-4d4d-be41-eb24cfe17bef
ms.openlocfilehash: 80b873e81acc243ff61257bc305c4f782b5bf867
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2019
ms.locfileid: "57351830"
---
# <a name="how-to-resize-a-canvas-by-using-a-thumb"></a>方法: つまみを使用したキャンバスのサイズ変更
この例は、使用する方法を示します、<xref:System.Windows.Controls.Primitives.Thumb>サイズを変更するコントロールを<xref:System.Windows.Controls.Canvas>コントロール。  
  
## <a name="example"></a>例  
 <xref:System.Windows.Controls.Primitives.Thumb>コントロールには、監視することによってコントロールのサイズを変更または移動に使用できるドラッグ機能が用意されています、 <xref:System.Windows.Controls.Primitives.Thumb.DragStarted>、<xref:System.Windows.Controls.Primitives.Thumb.DragDelta>と<xref:System.Windows.Controls.Primitives.Thumb.DragCompleted>のイベント、<xref:System.Windows.Controls.Primitives.Thumb>します。  
  
 上にマウス ポインターが一時停止すると、マウスの左ボタンを押して、ユーザーがドラッグ操作を開始、<xref:System.Windows.Controls.Primitives.Thumb>コントロール。 マウスの左ボタンが押されている限り、ドラッグ操作が続行します。 ドラッグ操作中に、<xref:System.Windows.Controls.Primitives.Thumb.DragDelta>複数回発生することができます。 これが発生するたびに、<xref:System.Windows.Controls.Primitives.DragDeltaEventArgs>クラスには、マウスの位置の変化に対応する位置の変更が用意されています。 マウスの左ボタンを離したときに、ドラッグ操作が完了しました。 ドラッグ操作では、新しい座標のみ提供します自動的に再配置されない、<xref:System.Windows.Controls.Primitives.Thumb>します。  
  
 次の例は、<xref:System.Windows.Controls.Primitives.Thumb>の子要素であるコントロール、<xref:System.Windows.Controls.Canvas>コントロール。 イベント ハンドラーの<xref:System.Windows.Controls.Primitives.Thumb.DragDelta>イベントに移動するロジックを提供する、<xref:System.Windows.Controls.Primitives.Thumb>サイズを変更して、 <xref:System.Windows.Controls.Canvas>。 イベント ハンドラー、<xref:System.Windows.Controls.Primitives.Thumb.DragStarted>と<xref:System.Windows.Controls.Primitives.Thumb.DragCompleted>の色を変更するイベント、<xref:System.Windows.Controls.Primitives.Thumb>ドラッグ操作中にします。 次の例では、定義、<xref:System.Windows.Controls.Primitives.Thumb>します。  
  
 [!code-xaml[Thumb#thumb](~/samples/snippets/csharp/VS_Snippets_Wpf/Thumb/CSharp/Pane1.xaml#thumb)]  
  
 次の例は、<xref:System.Windows.Controls.Primitives.Thumb.DragDelta>を移動するイベント ハンドラー、<xref:System.Windows.Controls.Primitives.Thumb>のサイズを変更し、<xref:System.Windows.Controls.Canvas>マウスの動きへの応答。  
  
 [!code-csharp[Thumb#2](~/samples/snippets/csharp/VS_Snippets_Wpf/Thumb/CSharp/Pane1.xaml.cs#2)]  
  
 次の例は、<xref:System.Windows.Controls.Primitives.Thumb.DragStarted>イベント ハンドラー。  
  
 [!code-csharp[Thumb#DragStartedHandler](~/samples/snippets/csharp/VS_Snippets_Wpf/Thumb/CSharp/Pane1.xaml.cs#dragstartedhandler)]
 [!code-vb[Thumb#DragStartedHandler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Thumb/VisualBasic/Pane1.xaml.vb#dragstartedhandler)]  
  
 次の例は、<xref:System.Windows.Controls.Primitives.Thumb.DragCompleted>イベント ハンドラー。  
  
 [!code-csharp[Thumb#DragCompletedHandler](~/samples/snippets/csharp/VS_Snippets_Wpf/Thumb/CSharp/Pane1.xaml.cs#dragcompletedhandler)]
 [!code-vb[Thumb#DragCompletedHandler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Thumb/VisualBasic/Pane1.xaml.vb#dragcompletedhandler)]  
  
 サンプル全体については、[Thumb ドラッグ機能のサンプル](https://go.microsoft.com/fwlink/?LinkID=160042)を参照してください。  
  
## <a name="see-also"></a>関連項目
- <xref:System.Windows.Controls.Primitives.Thumb>
- <xref:System.Windows.Controls.Primitives.Thumb.DragStarted>
- <xref:System.Windows.Controls.Primitives.Thumb.DragDelta>
- <xref:System.Windows.Controls.Primitives.Thumb.DragCompleted>
