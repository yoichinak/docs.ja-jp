---
title: '方法: ストーリーボードを開始後に制御する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Storyboards [WPF], controlling after start
ms.assetid: 040f13f0-69f9-4ab5-be2b-079f4f80c7c0
ms.openlocfilehash: de30cfdb49df721cb4d6845dc67464e8a5b61f93
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855864"
---
# <a name="how-to-control-a-storyboard-after-it-starts"></a>方法: ストーリーボードを開始後に制御する

この例では、コードを使用して<xref:System.Windows.Media.Animation.Storyboard>を開始した後に制御する方法を示します。 で[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]ストーリーボードを制御するに<xref:System.Windows.Trigger>は<xref:System.Windows.TriggerAction> 、オブジェクトとオブジェクトを使用します。例については、「[開始後にイベントトリガーを使用してストーリーボードを制御](how-to-use-event-triggers-to-control-a-storyboard-after-it-starts.md)する」を参照してください。

ストーリーボードを開始するには、 <xref:System.Windows.Media.Animation.Storyboard.Begin%2A>そのメソッドを使用します。これにより、ストーリーボードのアニメーションがアニメーション化され、ストーリーボードが開始されます。

ストーリーボードを制御できるようにするに<xref:System.Windows.Media.Animation.Storyboard.Begin%2A>は、メソッドを使用し、2番目のパラメーターとして**true**を指定します。 その後、ストーリーボードの対話型メソッドを使用して、ストーリーボードの一時停止、再開、シーク、停止、速度の低下、または速度の低下を行うことができます。 次に、ストーリーボードの対話型メソッドの一覧を示します。

- <xref:System.Windows.Media.Animation.Storyboard.Pause%2A>:ストーリーボードを一時停止します。

- <xref:System.Windows.Media.Animation.Storyboard.Resume%2A>:一時停止したストーリーボードを再開します。

- <xref:System.Windows.Media.Animation.Storyboard.SetSpeedRatio%2A>:ストーリーボードの対話速度を設定します。

- <xref:System.Windows.Media.Animation.Storyboard.Seek%2A>:指定された場所でストーリーボードをシークします。

- <xref:System.Windows.Media.Animation.Storyboard.SeekAlignedToLastTick%2A>:指定された位置までストーリーボードをシークします。 <xref:System.Windows.Media.Animation.Storyboard.Seek%2A>メソッドとは異なり、この操作は次のティックの前に処理されます。

- <xref:System.Windows.Media.Animation.Storyboard.SkipToFill%2A>:ストーリーボードがある場合は、そのストーリーボードをその塗りつぶし期間に進めます。

- <xref:System.Windows.Media.Animation.Storyboard.Stop%2A>:ストーリーボードを停止します。

次の例では、ストーリーボードを対話的に制御するために、いくつかのストーリーボードメソッドが使用されています。

> [!NOTE]
> で[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]トリガーを使用してストーリーボードを制御する例については、「[開始後にイベントトリガーを使用してストーリーボードを制御](how-to-use-event-triggers-to-control-a-storyboard-after-it-starts.md)する」を参照してください。

## <a name="example"></a>例

[!code-csharp[timingbehaviors_procedural_snip#ControlStoryboardExampleUsingWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_procedural_snip/CSharp/ControlStoryboardExample.cs#controlstoryboardexampleusingwholepage)]
[!code-vb[timingbehaviors_procedural_snip#ControlStoryboardExampleUsingWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_procedural_snip/visualbasic/controlstoryboardexample.vb#controlstoryboardexampleusingwholepage)]

## <a name="see-also"></a>関連項目

- [開始後のストーリーボードをイベント トリガーを使用して制御する](how-to-use-event-triggers-to-control-a-storyboard-after-it-starts.md)
