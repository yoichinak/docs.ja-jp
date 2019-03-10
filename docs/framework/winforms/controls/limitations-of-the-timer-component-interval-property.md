---
title: Windows フォームの Timer コンポーネントの Interval プロパティの制限
ms.date: 03/30/2017
helpviewer_keywords:
- timers [Windows Forms], event intervals
- Interval property [Windows Forms], limitations
- timers [Windows Forms], Windows-based
- Timer component [Windows Forms], limitations of Interval property
ms.assetid: 7e5fb513-77e7-4046-a8e8-aab94e61ca0f
ms.openlocfilehash: f564a4ce7fa2d9b8ea5446f2cf6bd016db054dd9
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/09/2019
ms.locfileid: "57724389"
---
# <a name="limitations-of-the-windows-forms-timer-components-interval-property"></a>Windows フォームの Timer コンポーネントの Interval プロパティの制限
Windows フォーム<xref:System.Windows.Forms.Timer>コンポーネントには、<xref:System.Windows.Forms.Timer.Interval%2A>と次の 1 つのタイマー イベントの間の経過時間をミリ秒数を指定するプロパティ。 タイマーは引き続き受信コンポーネントが無効にしない限り、<xref:System.Windows.Forms.Timer.Tick>ほぼ一定の時間間隔でイベント。  
  
 このコンポーネントは、Windows フォームの環境用に設計されています。 サーバー環境に適したタイマーが必要な場合は、「[サーバー ベースのタイマーの概要](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/tb9yt5e6(v=vs.90))」を参照してください。  
  
## <a name="the-interval-property"></a>間隔のプロパティ  
 <xref:System.Windows.Forms.Timer.Interval%2A>プロパティがプログラミングしているときに考慮すべきいくつかの制限、<xref:System.Windows.Forms.Timer>コンポーネント。  
  
-   アプリケーションまたは別のアプリケーションで、システムで重い負荷が早い場合、長いループや複雑な計算、またはドライブ、ネットワーク、またはポートへのアクセスなど-アプリケーションとしてのタイマー イベントを頻繁に利用できない、<xref:System.Windows.Forms.Timer.Interval%2A>プロパティを指定します。  
  
-   間隔は、正確に時間の経過時間は保証されません。 精度を保証するには、タイマーする必要があります、必要に応じて、システム クロックのチェックではなく保持の累積時間を内部的にしようとしています。  
  
-   有効桁数、<xref:System.Windows.Forms.Timer.Interval%2A>プロパティの単位はミリ秒です。 一部のコンピューターでは、ミリ秒よりも高い解像度が高分解能カウンターを提供します。 このようなカウンターの可用性は、コンピューターのプロセッサ ハードウェアに依存します。
  
## <a name="see-also"></a>関連項目
- <xref:System.Windows.Forms.Timer>
- [Timer コンポーネント](timer-component-windows-forms.md)
- [Timer コンポーネントの概要](timer-component-overview-windows-forms.md)
