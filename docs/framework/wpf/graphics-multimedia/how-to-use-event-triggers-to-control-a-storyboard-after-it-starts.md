---
title: '方法: 開始後のストーリーボードをイベント トリガーを使用して制御する'
ms.date: 03/30/2017
helpviewer_keywords:
- triggers [WPF], controlling Storyboards
- event triggers [WPF], controlling Storyboards
- Storyboards [WPF], controlling after start
ms.assetid: 3b115594-6a93-4972-b24d-61aa16f1c15f
ms.openlocfilehash: d444349f8bc9236e1d15f484f35b1326c77e2425
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59170652"
---
# <a name="how-to-use-event-triggers-to-control-a-storyboard-after-it-starts"></a>方法: 開始後のストーリーボードをイベント トリガーを使用して制御する
この例では、制御、<xref:System.Windows.Media.Animation.Storyboard>開始後にします。 開始する、<xref:System.Windows.Media.Animation.Storyboard>を使用して[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]を使用して、<xref:System.Windows.Media.Animation.BeginStoryboard>オブジェクトとプロパティをアニメーション化して、ストーリー ボードを起動しにアニメーションを配布します。 付ける場合<xref:System.Windows.Media.Animation.BeginStoryboard>名前を指定してその<xref:System.Windows.Media.Animation.BeginStoryboard.Name%2A>プロパティをできるようにする制御可能なストーリー ボード。 ことができます対話的に制御、ストーリー ボードが開始されます。  
  
 と共に次のストーリー ボード アクションを使用して、<xref:System.Windows.EventTrigger>ストーリー ボードを制御するオブジェクト。  
  
-   <xref:System.Windows.Media.Animation.PauseStoryboard>:ストーリー ボードを一時停止します。  
  
-   <xref:System.Windows.Media.Animation.ResumeStoryboard>:一時停止中のストーリー ボードを再開します。  
  
-   <xref:System.Windows.Media.Animation.SetStoryboardSpeedRatio>:ストーリー ボードの速度を変更します。  
  
-   <xref:System.Windows.Media.Animation.SkipStoryboardToFill>:ある場合は、その保留期間の末尾にストーリー ボードを進めます。  
  
-   <xref:System.Windows.Media.Animation.StopStoryboard>:ストーリー ボードを停止します。  
  
-   <xref:System.Windows.Media.Animation.RemoveStoryboard>:リソースの解放、ストーリー ボードを削除します。  
  
## <a name="example"></a>例  
 次の例では、制御可能なストーリー ボード アクションを使用して、ストーリー ボードを対話的に制御します。  
  
 **注:** コードを使用してストーリー ボードを制御するための例を表示するには、次を参照してください。 [、ストーリー ボードの後に開始の対話型メソッドを使用して制御](how-to-control-a-storyboard-after-it-starts.md)します。  
  
 [!code-xaml[timingbehaviors_snip#ControlStoryboardExampleUsingWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/ControlStoryboardExample.xaml#controlstoryboardexampleusingwholepage)]  
  
 その他の例では、次を参照してください。、[アニメーション サンプル ギャラリー](https://go.microsoft.com/fwlink/?LinkID=159969)します。  
  
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
