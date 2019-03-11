---
title: ProgressBar コントロールの概要 (Windows フォーム)
ms.date: 03/30/2017
f1_keywords:
- ProgressBar
helpviewer_keywords:
- ProgressBar control [Windows Forms], about ProgressBar control
- progress controls [Windows Forms], about progress controls
ms.assetid: a05d9cba-3a6a-4f8f-94b8-8ec12799fb80
ms.openlocfilehash: db0a43534080d630323d8c1c95759fd2dcc04a85
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/09/2019
ms.locfileid: "57707945"
---
# <a name="progressbar-control-overview-windows-forms"></a>ProgressBar コントロールの概要 (Windows フォーム)
> [!IMPORTANT]
>  
  <xref:System.Windows.Forms.ToolStripProgressBar> コントロールは、<xref:System.Windows.Forms.ProgressBar> コントロールに代わると共に追加の機能を提供します。ただし、<xref:System.Windows.Forms.ProgressBar> コントロールは、下位互換性を保つ目的および将来使用する目的で保持されます。  
  
 Windows フォーム<xref:System.Windows.Forms.ProgressBar>コントロールを適切な数の水平のバーに配置された四角形を表示することによって、プロセスの進行状況を示します。 プロセスが完了すると、バーが入力されます。 進行状況バーが方法を理解するために使用される一般的なプロセスが完了するまで待機します。たとえば、大きなファイルがされる読み込まれるときにします。  
  
> [!NOTE]
>  <xref:System.Windows.Forms.ProgressBar>コントロールがフォームの水平方向がのみできます。  
  
## <a name="key-properties-and-methods"></a>キー プロパティとメソッド  
 キー プロパティ、<xref:System.Windows.Forms.ProgressBar>コントロールは<xref:System.Windows.Forms.ProgressBar.Value%2A>、 <xref:System.Windows.Forms.ProgressBar.Minimum%2A>、および<xref:System.Windows.Forms.ProgressBar.Maximum%2A>します。 <xref:System.Windows.Forms.ProgressBar.Minimum%2A>と<xref:System.Windows.Forms.ProgressBar.Maximum%2A>プロパティは、進行状況バーが表示できる最大値と最小値を設定します。 <xref:System.Windows.Forms.ProgressBar.Value%2A>プロパティは、操作の完了に向けたになっている進行状況を表します。 によって、コントロールに表示されるバーはブロックで構成されているため、値が表示されます、<xref:System.Windows.Forms.ProgressBar>コントロールのみに近い、<xref:System.Windows.Forms.ProgressBar.Value%2A>プロパティの現在の値。 サイズに基づいて、<xref:System.Windows.Forms.ProgressBar>コントロール、<xref:System.Windows.Forms.ProgressBar.Value%2A>プロパティは、次のブロックを表示するタイミングを決定します。  
  
 現在の進行状況の値を更新する最も一般的な方法を設定するコードを記述する、<xref:System.Windows.Forms.ProgressBar.Value%2A>プロパティ。 大きなファイルの読み込みの例では、キロバイト単位でファイルのサイズを最大値を設定できます。 たとえば場合、<xref:System.Windows.Forms.ProgressBar.Maximum%2A>プロパティが 100 に設定、 <xref:System.Windows.Forms.ProgressBar.Minimum%2A> 10 に設定されて、<xref:System.Windows.Forms.ProgressBar.Value%2A>プロパティが設定されてを 50 に、5 つの四角形が表示されます。 これは、表示可能な数の半分です。  
  
 ただしに表示される値を変更するには、その他の方法がある、<xref:System.Windows.Forms.ProgressBar>設定とは別のコントロール、<xref:System.Windows.Forms.ProgressBar.Value%2A>プロパティを直接します。 <xref:System.Windows.Forms.ProgressBar.Step%2A>をインクリメントする値を指定するプロパティを使用できます、<xref:System.Windows.Forms.ProgressBar.Value%2A>プロパティ。 次に、呼び出し、<xref:System.Windows.Forms.ProgressBar.PerformStep%2A>メソッドには、値が 1 ずつ増分されます。 増分値を変更するには、使用することができます、<xref:System.Windows.Forms.ProgressBar.Increment%2A>メソッドでインクリメントする値を指定し、<xref:System.Windows.Forms.ProgressBar.Value%2A>プロパティ。  
  
 視覚的に現在の動作についてユーザーに通知する別のコントロールが、<xref:System.Windows.Forms.StatusBar>コントロール。  
  
> [!IMPORTANT]
>  <xref:System.Windows.Forms.StatusStrip>と<xref:System.Windows.Forms.ToolStripStatusLabel>コントロールの置換し、する機能を追加、<xref:System.Windows.Forms.StatusBar>と<xref:System.Windows.Forms.StatusBarPanel>を制御しますただし、、<xref:System.Windows.Forms.StatusBar>と<xref:System.Windows.Forms.StatusBarPanel>場合、下位互換性と将来の使用の両方のコントロールが保持されますします。選択します。  
  
## <a name="see-also"></a>関連項目
- <xref:System.Windows.Forms.ProgressBar>
- [ProgressBar コントロール](progressbar-control-windows-forms.md)
