---
title: '方法: 開始後に、ストーリー ボードを制御します。'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Storyboards [WPF], controlling after start
ms.assetid: 040f13f0-69f9-4ab5-be2b-079f4f80c7c0
ms.openlocfilehash: 98eba600f64c8b656e3597b429cc69766f398f7b
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2019
ms.locfileid: "57361058"
---
# <a name="how-to-control-a-storyboard-after-it-starts"></a>方法: 開始後に、ストーリー ボードを制御します。
この例では、コントロールにコードを使って、<xref:System.Windows.Media.Animation.Storyboard>開始後。 ストーリー ボードを制御する[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]を使用して、<xref:System.Windows.Trigger>と<xref:System.Windows.TriggerAction>オブジェクト。 例については、[、ストーリー ボード開始後の制御をイベント トリガーを使用して](how-to-use-event-triggers-to-control-a-storyboard-after-it-starts.md)を参照してください。  
  
 使用するストーリー ボードを開始するには、その<xref:System.Windows.Media.Animation.Storyboard.Begin%2A>メソッド、プロパティがアニメーション化して、ストーリー ボードを開始するストーリー ボードのアニメーションを分散します。  
  
 ストーリー ボードを制御するためには、使用する、<xref:System.Windows.Media.Animation.Storyboard.Begin%2A>メソッドを指定して**true** 2 番目のパラメーター。 一時停止、再開、シーク、停止、高速化する、またはストーリー ボード、速度が低下または塗りつぶし期間まで進める、ストーリー ボードの対話型のメソッドを使用できます。 次には、ストーリー ボードの対話型のメソッドの一覧を示します。  
  
-   <xref:System.Windows.Media.Animation.Storyboard.Pause%2A>:ストーリー ボードを一時停止します。  
  
-   <xref:System.Windows.Media.Animation.Storyboard.Resume%2A>:一時停止中のストーリー ボードを再開します。  
  
-   <xref:System.Windows.Media.Animation.Storyboard.SetSpeedRatio%2A>:ストーリー ボードの対話型速度を設定します。  
  
-   <xref:System.Windows.Media.Animation.Storyboard.Seek%2A>:指定した場所のストーリー ボードをシークします。  
  
-   <xref:System.Windows.Media.Animation.Storyboard.SeekAlignedToLastTick%2A>:指定した場所にストーリー ボードをシークします。 異なり、<xref:System.Windows.Media.Animation.Storyboard.Seek%2A>メソッドでは、この操作は、次の目盛りの前に処理されます。  
  
-   <xref:System.Windows.Media.Animation.Storyboard.SkipToFill%2A>:ある場合は、塗りつぶし期間、ストーリー ボードを進めます。  
  
-   <xref:System.Windows.Media.Animation.Storyboard.Stop%2A>:ストーリー ボードを停止します。  
  
 次の例では、いくつかのストーリー ボード メソッドは、ストーリー ボードを対話的に制御に使用されます。  
  
 **注:** トリガーを使用してストーリー ボードを制御するための例を参照する[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]を参照してください[イベント トリガーを使用して、ストーリー ボード開始後に制御する](how-to-use-event-triggers-to-control-a-storyboard-after-it-starts.md)します。  
  
## <a name="example"></a>例  
 [!code-csharp[timingbehaviors_procedural_snip#ControlStoryboardExampleUsingWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_procedural_snip/CSharp/ControlStoryboardExample.cs#controlstoryboardexampleusingwholepage)]
 [!code-vb[timingbehaviors_procedural_snip#ControlStoryboardExampleUsingWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_procedural_snip/visualbasic/controlstoryboardexample.vb#controlstoryboardexampleusingwholepage)]  
  
## <a name="see-also"></a>関連項目
- [開始後のストーリーボードをイベント トリガーを使用して制御する](how-to-use-event-triggers-to-control-a-storyboard-after-it-starts.md)
