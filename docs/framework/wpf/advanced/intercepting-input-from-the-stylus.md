---
title: スタイラスからの入力のインターセプト
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- 'architecture [WPF], '
- ', '
- ', '
- ', '
ms.assetid: 791bb2f0-4e5c-4569-ac3c-211996808d44
ms.openlocfilehash: 2547c0aa2f3a14080868c2760fa8999eb99d3d16
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2019
ms.locfileid: "70046328"
---
# <a name="intercepting-input-from-the-stylus"></a>スタイラスからの入力のインターセプト
アーキテクチャ<xref:System.Windows.Input.StylusPlugIns>は、 <xref:System.Windows.Input.Stylus>入力とデジタルインク<xref:System.Windows.Ink.Stroke>オブジェクトの作成に対して低レベルの制御を実装するためのメカニズムを提供します。 クラス<xref:System.Windows.Input.StylusPlugIns.StylusPlugIn>は、カスタム動作を実装し、最適なパフォーマンスを得るためにスタイラスデバイスから送信されるデータストリームに適用するためのメカニズムを提供します。  
  
 このトピックは、次の内容で構成されています。  
  
- [アーキテクチャ](#Architecture)  
  
- [スタイラスプラグインの実装](#ImplementingStylusPlugins)  
  
- [System.windows.controls.inkcanvas> にプラグインを追加する](#AddingYourPluginToAnInkCanvas)  
  
- [まとめ](#Conclusion)  
  
<a name="Architecture"></a>   
## <a name="architecture"></a>アーキテクチャ  
 は、 [Microsoft Windows XP Tablet PC Edition ソフトウェア開発キット 1.7](https://go.microsoft.com/fwlink/?linkid=11782&clcid=0x409)の「[ペン入力にアクセスして操作](https://go.microsoft.com/fwlink/?LinkId=50752&clcid=0x409)する」で説明されている [StylusInput](https://go.microsoft.com/fwlink/?LinkId=50753&clcid=0x409) API の進化<xref:System.Windows.Input.StylusPlugIns.StylusPlugIn>です。  
  
 各<xref:System.Windows.UIElement>には<xref:System.Windows.UIElement.StylusPlugIns%2A> 、と<xref:System.Windows.Input.StylusPlugIns.StylusPlugInCollection>いうプロパティがあります。 を要素の<xref:System.Windows.UIElement.StylusPlugIns%2A>プロパティ<xref:System.Windows.Input.StylusPlugIns.StylusPlugIn>に追加して、生成時<xref:System.Windows.Input.StylusPoint>にデータを操作できます。 <xref:System.Windows.Input.StylusPoint>データは<xref:System.Windows.Input.StylusPoint.X%2A> <xref:System.Windows.Input.StylusPoint.PressureFactor%2A> 、データだけでなく、ポイントデータも含め、システムデジタイザーによってサポートされるすべてのプロパティで構成されます。<xref:System.Windows.Input.StylusPoint.Y%2A>  
  
 オブジェクトは、 <xref:System.Windows.Input.Stylus> <xref:System.Windows.UIElement.StylusPlugIns%2A>をプロパティに追加するときに、デバイスから送信されるデータのストリームに直接挿入されます。 <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> プラグインを<xref:System.Windows.UIElement.StylusPlugIns%2A>コレクションに追加する順序によって、データを受信<xref:System.Windows.Input.StylusPoint>する順序が決まります。 たとえば、特定の領域に対する入力を制限するフィルタープラグインを追加した後、ジェスチャを認識するプラグインを追加すると、ジェスチャを認識するプラグインがフィルター処理<xref:System.Windows.Input.StylusPoint>されたデータを受信します。  
  
<a name="ImplementingStylusPlugins"></a>   
## <a name="implementing-stylus-plug-ins"></a>スタイラスプラグインの実装  
 プラグインを実装するには、から<xref:System.Windows.Input.StylusPlugIns.StylusPlugIn>クラスを派生させます。 このクラスは、 <xref:System.Windows.Input.Stylus>から取得されるデータのストリームとして適用されます。 このクラスでは、 <xref:System.Windows.Input.StylusPoint>データの値を変更できます。  
  
> [!CAUTION]
> が<xref:System.Windows.Input.StylusPlugIns.StylusPlugIn>例外をスローした場合、または例外が発生した場合、アプリケーションは終了します。 を<xref:System.Windows.Input.StylusPlugIns.StylusPlugIn>使用するコントロールを十分にテストし、が例外をスローしないことが<xref:System.Windows.Input.StylusPlugIns.StylusPlugIn>わかっている場合にのみ、コントロールを使用します。  
  
 次の例<xref:System.Windows.Input.StylusPoint.X%2A>は、 <xref:System.Windows.Input.Stylus>デバイスからの<xref:System.Windows.Input.StylusPoint>データのと<xref:System.Windows.Input.StylusPoint.Y%2A>の値を変更することによって、スタイラスの入力を制限するプラグインを示しています。  
  
 [!code-csharp[AdvancedInkTopicsSamples#19](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/DynamicRenderer.cs#19)]
 [!code-vb[AdvancedInkTopicsSamples#19](~/samples/snippets/visualbasic/VS_Snippets_Wpf/AdvancedInkTopicsSamples/VisualBasic/DynamicRenderer.vb#19)]  
[!code-csharp[AdvancedInkTopicsSamples#3](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/DynamicRenderer.cs#3)]
[!code-vb[AdvancedInkTopicsSamples#3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/AdvancedInkTopicsSamples/VisualBasic/DynamicRenderer.vb#3)]  
  
<a name="AddingYourPluginToAnInkCanvas"></a>   
## <a name="adding-your-plug-in-to-an-inkcanvas"></a>System.windows.controls.inkcanvas> にプラグインを追加する  
 カスタムプラグインを使用する最も簡単な方法は、system.windows.controls.inkcanvas> から派生するクラスを実装し、それを<xref:System.Windows.UIElement.StylusPlugIns%2A>プロパティに追加することです。  
  
 次の例は、インク<xref:System.Windows.Controls.InkCanvas>をフィルター処理するカスタムを示しています。  
  
 [!code-csharp[AdvancedInkTopicsSamples#4](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/Window1.xaml.cs#4)]  
  
 アプリケーションにを`FilterInkCanvas`追加して実行すると、ユーザーがストロークを完了するまで、インクが領域に限定されないことがわかります。 これは、 <xref:System.Windows.Controls.InkCanvas>に<xref:System.Windows.Input.StylusPlugIns.StylusPlugIn>という<xref:System.Windows.Controls.InkCanvas.DynamicRenderer%2A>プロパティがあり、既に<xref:System.Windows.UIElement.StylusPlugIns%2A>コレクションのメンバーであるためです。 コレクションに追加<xref:System.Windows.Input.StylusPlugIns.StylusPlugIn>したカスタムは、がデータを<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>受信した後にデータを<xref:System.Windows.Input.StylusPoint>受信します。 <xref:System.Windows.UIElement.StylusPlugIns%2A> その結果<xref:System.Windows.Input.StylusPoint> 、ユーザーがペンを離してストロークを終了するまで、データはフィルター処理されません。 ユーザーがインクを描画するときにフィルター処理するには、 `FilterPlugin`の<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>前にを挿入する必要があります。  
  
 次C#のコードは、描画<xref:System.Windows.Controls.InkCanvas>時にインクをフィルター処理するカスタムを示しています。  
  
 [!code-csharp[AdvancedInkTopicsSamples#5](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/Window1.xaml.cs#5)]  
  
<a name="Conclusion"></a>   
## <a name="conclusion"></a>まとめ  
 独自<xref:System.Windows.Input.StylusPlugIns.StylusPlugIn>のクラスを派生させてコレクション<xref:System.Windows.Input.StylusPlugIns.StylusPlugInCollection>に挿入することにより、デジタルインクの動作を大幅に向上させることができます。 生成された<xref:System.Windows.Input.StylusPoint>データにアクセスできるため、 <xref:System.Windows.Input.Stylus>入力をカスタマイズすることができます。 データへの<xref:System.Windows.Input.StylusPoint>低レベルのアクセス権があるため、アプリケーションに最適なパフォーマンスでインクの収集とレンダリングを実装できます。  
  
## <a name="see-also"></a>関連項目

- [高度なインク処理](advanced-ink-handling.md)
- [ペン入力にアクセスして操作する](https://go.microsoft.com/fwlink/?LinkId=50752&clcid=0x409)
