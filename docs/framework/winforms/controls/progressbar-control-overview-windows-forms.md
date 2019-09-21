---
title: ProgressBar コントロールの概要 (Windows フォーム)
ms.date: 03/30/2017
f1_keywords:
- ProgressBar
helpviewer_keywords:
- ProgressBar control [Windows Forms], about ProgressBar control
- progress controls [Windows Forms], about progress controls
ms.assetid: a05d9cba-3a6a-4f8f-94b8-8ec12799fb80
ms.openlocfilehash: 7dd434492cd688527ddbce5aaffa442a0b40a9e4
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69968318"
---
# <a name="progressbar-control-overview-windows-forms"></a>ProgressBar コントロールの概要 (Windows フォーム)
> [!IMPORTANT]
> <xref:System.Windows.Forms.ToolStripProgressBar> コントロールは、<xref:System.Windows.Forms.ProgressBar> コントロールに代わると共に追加の機能を提供します。ただし、<xref:System.Windows.Forms.ProgressBar> コントロールは、下位互換性を保つ目的および将来使用する目的で保持されます。  
  
 Windows フォーム<xref:System.Windows.Forms.ProgressBar>コントロールは、水平バーに配置された適切な数の四角形を表示することによって、プロセスの進行状況を示します。 プロセスが完了すると、バーは塗りつぶされます。 一般的に、進行状況バーは、プロセスが完了するまでの待機時間をユーザーに示すために使用されます。たとえば、大きなファイルが読み込まれている場合です。  
  
> [!NOTE]
> コントロール<xref:System.Windows.Forms.ProgressBar>は、フォーム上で水平方向にのみ配置できます。  
  
## <a name="key-properties-and-methods"></a>キーのプロパティとメソッド  
 <xref:System.Windows.Forms.ProgressBar>コントロールの主要なプロパティは<xref:System.Windows.Forms.ProgressBar.Value%2A>、 <xref:System.Windows.Forms.ProgressBar.Minimum%2A>、、および<xref:System.Windows.Forms.ProgressBar.Maximum%2A>です。 プロパティ<xref:System.Windows.Forms.ProgressBar.Minimum%2A> と<xref:System.Windows.Forms.ProgressBar.Maximum%2A>プロパティは、進行状況バーに表示できる最大値と最小値を設定します。 プロパティ<xref:System.Windows.Forms.ProgressBar.Value%2A>は、操作の完了に向けた進行状況を表します。 コントロールに表示されるバーはブロックで構成されているため、 <xref:System.Windows.Forms.ProgressBar>コントロールによって表示される値は、 <xref:System.Windows.Forms.ProgressBar.Value%2A>プロパティの現在の値のみを概算します。 プロパティは<xref:System.Windows.Forms.ProgressBar> <xref:System.Windows.Forms.ProgressBar.Value%2A> 、コントロールのサイズに基づいて、次のブロックを表示するタイミングを決定します。  
  
 現在の進行状況の値を更新する最も一般的な方法は、 <xref:System.Windows.Forms.ProgressBar.Value%2A>プロパティを設定するコードを記述することです。 大きなファイルを読み込む例では、ファイルの最大サイズをキロバイト単位で設定できます。 たとえば、 <xref:System.Windows.Forms.ProgressBar.Maximum%2A>プロパティが 100 <xref:System.Windows.Forms.ProgressBar.Minimum%2A>に設定されている場合、プロパティは 10 <xref:System.Windows.Forms.ProgressBar.Value%2A>に設定され、プロパティは50に設定され、5つの四角形が表示されます。 これは、表示できる数の半分です。  
  
 ただし、 <xref:System.Windows.Forms.ProgressBar> <xref:System.Windows.Forms.ProgressBar.Value%2A>プロパティを直接設定する以外に、コントロールによって表示される値を変更する方法は他にもあります。 プロパティを使用して、 <xref:System.Windows.Forms.ProgressBar.Value%2A>プロパティをインクリメントする値を指定できます。 <xref:System.Windows.Forms.ProgressBar.Step%2A> 次に、 <xref:System.Windows.Forms.ProgressBar.PerformStep%2A>メソッドを呼び出すと、値がインクリメントされます。 インクリメント値を変更するには、 <xref:System.Windows.Forms.ProgressBar.Increment%2A>メソッドを使用して、 <xref:System.Windows.Forms.ProgressBar.Value%2A>プロパティをインクリメントする値を指定します。  
  
 現在のアクションについてグラフィカルにユーザーに通知する別<xref:System.Windows.Forms.StatusBar>のコントロールがコントロールです。  
  
> [!IMPORTANT]
> <xref:System.Windows.Forms.StatusBar> <xref:System.Windows.Forms.StatusBarPanel> <xref:System.Windows.Forms.StatusBar>コントロール<xref:System.Windows.Forms.StatusStrip>と<xref:System.Windows.Forms.ToolStripStatusLabel>コントロールは、および<xref:System.Windows.Forms.StatusBarPanel>コントロールに対して、機能の置き換えと追加を行います。ただし、コントロールとコントロールは、下位互換性と将来の使用の両方のために保持されます。し.  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.ProgressBar>
- [ProgressBar コントロール](progressbar-control-windows-forms.md)
