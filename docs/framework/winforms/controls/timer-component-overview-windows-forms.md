---
title: Timer コンポーネントの概要 (Windows フォーム)
ms.date: 03/30/2017
f1_keywords:
- Timer
helpviewer_keywords:
- Timer component [Windows Forms], about Timer components
- timers [Windows Forms], about timers
ms.assetid: e672c05b-a8b6-4b26-9e4d-9223aa9e3873
ms.openlocfilehash: a13afba026f1f9eed095817c65637bb6a091c7f0
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/09/2019
ms.locfileid: "57725286"
---
# <a name="timer-component-overview-windows-forms"></a>Timer コンポーネントの概要 (Windows フォーム)
Windows フォーム <xref:System.Windows.Forms.Timer> は、一定の間隔でイベントを発生させるコンポーネントです。 このコンポーネントは、Windows フォームの環境用に設計されています。 サーバー環境に適したタイマーが必要な場合は、「[サーバー ベースのタイマーの概要](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/tb9yt5e6(v=vs.90))」を参照してください。  
  
## <a name="key-properties-methods-and-events"></a>キー プロパティ、メソッド、およびイベント  
 間隔の長さが定義されている、<xref:System.Windows.Forms.Timer.Interval%2A>プロパティ、値はミリ秒単位で。 コンポーネントが有効にすると、<xref:System.Windows.Forms.Timer.Tick>イベントの発生間隔。 これは、実行するコードを追加することです。 詳細については、「[方法 :Windows フォームの Timer コンポーネントを使用して一定間隔でプロシージャを実行](run-procedures-at-set-intervals-with-wf-timer-component.md)します。 主要なメソッド、<xref:System.Windows.Forms.Timer>コンポーネントは<xref:System.Windows.Forms.Timer.Start%2A>と<xref:System.Windows.Forms.Timer.Stop%2A>タイマーをオンまたはオフにします。 タイマーをオフにすると、ときにリセットされます。一時停止する方法はありません、<xref:System.Windows.Forms.Timer>コンポーネント。  
  
## <a name="see-also"></a>関連項目
- <xref:System.Windows.Forms.Timer>
- [Timer コンポーネント](timer-component-windows-forms.md)
- [Windows フォームの Timer コンポーネントの Interval プロパティの制限](limitations-of-the-timer-component-interval-property.md)
