---
title: '方法 : 開始後のストーリーボードをイベント トリガーを使用して制御する'
ms.date: 03/30/2017
helpviewer_keywords:
- triggers [WPF], controlling Storyboards
- event triggers [WPF], controlling Storyboards
- Storyboards [WPF], controlling after start
ms.assetid: 3b115594-6a93-4972-b24d-61aa16f1c15f
ms.openlocfilehash: 518f5d7ea0b5dc00677489f1383814563c565145
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186703"
---
# <a name="how-to-use-event-triggers-to-control-a-storyboard-after-it-starts"></a>方法 : 開始後のストーリーボードをイベント トリガーを使用して制御する

この例では、開始後に<xref:System.Windows.Media.Animation.Storyboard>a を制御する方法を示します。 を使用<xref:System.Windows.Media.Animation.Storyboard>[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]して を開始するには<xref:System.Windows.Media.Animation.BeginStoryboard>、 を使用してアニメーションをアニメーション化したオブジェクトとプロパティにアニメーションを配信し、ストーリーボードを開始します。 プロパティを指定<xref:System.Windows.Media.Animation.BeginStoryboard>して名前を指定する場合は、そのプロパティを制御可能なストーリーボードにします。 <xref:System.Windows.Media.Animation.BeginStoryboard.Name%2A> ストーリーボードの開始後に、ストーリーボードを対話的に制御できます。

次のストーリーボード アクションをオブジェクト<xref:System.Windows.EventTrigger>と共に使用して、ストーリーボードを制御します。

- <xref:System.Windows.Media.Animation.PauseStoryboard>: ストーリーボードを一時停止します。

- <xref:System.Windows.Media.Animation.ResumeStoryboard>: 一時停止したストーリーボードを再開します。

- <xref:System.Windows.Media.Animation.SetStoryboardSpeedRatio>: ストーリーボードの速度を変更します。

- <xref:System.Windows.Media.Animation.SkipStoryboardToFill>: ストーリーボードの塗りつぶし期間が終了する場合は、その塗りつぶし期間の終了まで進めます。

- <xref:System.Windows.Media.Animation.StopStoryboard>: ストーリーボードを停止します。

- <xref:System.Windows.Media.Animation.RemoveStoryboard>: ストーリーボードを削除し、リソースを解放します。

## <a name="example"></a>例

次の例では、制御可能なストーリーボード アクションを使用して、ストーリーボードを対話的に制御します。

> [!NOTE]
> コードを使用してストーリーボードを制御する例については、「[対話型メソッドを使用してストーリーボードを開始した後でストーリーボードを制御する](how-to-control-a-storyboard-after-it-starts.md)」を参照してください。

[!code-xaml[timingbehaviors_snip#ControlStoryboardExampleUsingWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/ControlStoryboardExample.xaml#controlstoryboardexampleusingwholepage)]

その他の例については、「[アニメーションの例ギャラリー](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/AnimationExamples)」を参照してください。

## <a name="see-also"></a>関連項目

- <xref:System.Windows.Media.Animation.ResumeStoryboard>
- <xref:System.Windows.Media.Animation.SetStoryboardSpeedRatio>
- <xref:System.Windows.Media.Animation.SkipStoryboardToFill>
- <xref:System.Windows.Media.Animation.PauseStoryboard>
- <xref:System.Windows.Media.Animation.StopStoryboard>
- <xref:System.Windows.Media.Animation.SeekStoryboard>
- [対話型メソッドを使用してストーリーボードを開始後に制御する](how-to-control-a-storyboard-after-it-starts.md)
- [アニメーションの概要](animation-overview.md)
- [ストーリーボードの概要](storyboards-overview.md)
