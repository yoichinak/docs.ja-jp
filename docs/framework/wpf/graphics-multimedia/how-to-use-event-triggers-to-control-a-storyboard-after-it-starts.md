---
title: '方法: 開始後のストーリーボードをイベント トリガーを使用して制御する'
ms.date: 03/30/2017
helpviewer_keywords:
- triggers [WPF], controlling Storyboards
- event triggers [WPF], controlling Storyboards
- Storyboards [WPF], controlling after start
ms.assetid: 3b115594-6a93-4972-b24d-61aa16f1c15f
ms.openlocfilehash: 32591edd065a8122b84ff14102f672ccf6001d67
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855847"
---
# <a name="how-to-use-event-triggers-to-control-a-storyboard-after-it-starts"></a>方法: 開始後のストーリーボードをイベント トリガーを使用して制御する

この例では、の開始<xref:System.Windows.Media.Animation.Storyboard>後にを制御する方法を示します。 を使用<xref:System.Windows.Media.Animation.Storyboard> [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]してを開始する<xref:System.Windows.Media.Animation.BeginStoryboard>には、を使用します。これにより、アニメーションがアニメーション化されてオブジェクトとプロパティに配分され、ストーリーボードが開始されます。 プロパティ<xref:System.Windows.Media.Animation.BeginStoryboard.Name%2A>を指定<xref:System.Windows.Media.Animation.BeginStoryboard>して名前を指定すると、制御可能なストーリーボードになります。 その後、ストーリーボードを開始後に対話的に制御できます。

次のストーリーボードアクションをオブジェクト<xref:System.Windows.EventTrigger>と共に使用して、ストーリーボードを制御します。

- <xref:System.Windows.Media.Animation.PauseStoryboard>:ストーリーボードを一時停止します。

- <xref:System.Windows.Media.Animation.ResumeStoryboard>:一時停止したストーリーボードを再開します。

- <xref:System.Windows.Media.Animation.SetStoryboardSpeedRatio>:ストーリーボードの速度を変更します。

- <xref:System.Windows.Media.Animation.SkipStoryboardToFill>:ストーリーボードがある場合は、そのストーリーボードをその塗りつぶし期間の末尾に進めます。

- <xref:System.Windows.Media.Animation.StopStoryboard>:ストーリーボードを停止します。

- <xref:System.Windows.Media.Animation.RemoveStoryboard>:ストーリーボードを削除し、リソースを解放します。

## <a name="example"></a>例

次の例では、制御可能なストーリーボードアクションを使用して、ストーリーボードを対話的に制御します。

> [!NOTE]
> コードを使用してストーリーボードを制御する例については、「[対話的なメソッドを使用してストーリーボードを開始した後にコントロールを制御](how-to-control-a-storyboard-after-it-starts.md)する」を参照してください。

[!code-xaml[timingbehaviors_snip#ControlStoryboardExampleUsingWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/ControlStoryboardExample.xaml#controlstoryboardexampleusingwholepage)]

その他の例については、「[アニメーションの例ギャラリー](https://go.microsoft.com/fwlink/?LinkID=159969)」を参照してください。

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
