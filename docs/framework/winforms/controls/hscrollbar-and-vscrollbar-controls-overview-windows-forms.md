---
title: HScrollBar コントロールと VScrollBar コントロールの概要 (Windows フォーム)
ms.date: 03/30/2017
f1_keywords:
- HScrollBar
- VScrollBar
helpviewer_keywords:
- ScrollBar control [Windows Forms]
- HScrollBar control [Windows Forms], about HScrollBar
- VScrollBar control [Windows Forms], about VScrollBar control
- ScrollBar control [Windows Forms], about ScrollBar control
- scroll bars [Windows Forms], about scroll bars
ms.assetid: 8b307679-1cae-41d8-99aa-3d1efd207cd6
ms.openlocfilehash: d4a7912a5781fc583357affa728f7d81059b5cf9
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59097318"
---
# <a name="hscrollbar-and-vscrollbar-controls-overview-windows-forms"></a>HScrollBar コントロールと VScrollBar コントロールの概要 (Windows フォーム)
Windows フォーム<xref:System.Windows.Forms.ScrollBar>または垂直方向に水平方向にスクロールすることにより、アプリケーションまたはコントロール内の項目または大量の情報の長いリストを簡単にナビゲートを提供するコントロールを使用します。 スクロール バー、Windows インターフェイスの一般的な要素は、そのため、<xref:System.Windows.Forms.ScrollBar>から派生していないコントロールのコントロールが使用される多くの場合、<xref:System.Windows.Forms.ScrollableControl>クラス。 同様に、多くの開発者が組み込む選択、<xref:System.Windows.Forms.ScrollBar>独自のユーザー コントロールを作成するときを制御します。  
  
 <xref:System.Windows.Forms.HScrollBar> (水平) と<xref:System.Windows.Forms.VScrollBar>(垂直) コントロールは、他のコントロールから独立して動作し、イベント、プロパティ、およびメソッドの独自セットがあります。 <xref:System.Windows.Forms.ScrollBar> コントロールは、テキスト ボックス、リスト ボックス、コンボ ボックス、または MDI フォームにアタッチされている組み込みのスクロール バーと同じではありません (、<xref:System.Windows.Forms.TextBox>コントロールが、<xref:System.Windows.Forms.TextBox.ScrollBars%2A>コントロールに関連付けられているスクロール バーを非表示プロパティ)。  
  
 <xref:System.Windows.Forms.ScrollBar>使用を制御、<xref:System.Windows.Forms.ScrollBar.Scroll>に沿ってスクロール バーのスクロール ボックス (つまみとも呼ばれます) の動きを監視するイベントです。 使用して、<xref:System.Windows.Forms.ScrollBar.Scroll>イベントがドラッグされているようにスクロール バーの値へのアクセスを提供します。  
  
## <a name="value-property"></a>Value プロパティ  
 <xref:System.Windows.Forms.ScrollBar.Value%2A>プロパティ (つまり、既定では、0) は、`integer`スクロール バーのスクロール ボックスの位置に対応する値。 スクロール ボックスの位置は、最小値では、(水平スクロール バー) の左端の位置または (垂直スクロール バーの上端の位置に移動します。 スクロール ボックスが最大値、一番右にスクロール ボックスの移動、または下部にある位置にある場合です。 同様に、範囲の上端と下端の中間値は、スクロール バーの途中でのスクロール ボックスのリーディング エッジを配置します。  
  
 マウスのクリックを使用して、スクロール バーの値を変更する、だけでなく、ユーザーがバーに沿って任意の時点のスクロール ボックスをドラッグすることもできます。 結果の値は、スクロール ボックスの位置によって異なりますが、範囲の中では常に、<xref:System.Windows.Forms.ScrollBar.Minimum%2A>に<xref:System.Windows.Forms.ScrollBar.Maximum%2A>ユーザーによって設定されるプロパティ。  
  
## <a name="largechange-and-smallchange-properties"></a>LargeChange と SmallChange プロパティ  
 PAGE UP または PAGE DOWN キーを押すか、スクロール バーのトラック、スクロール ボックスのいずれかの側をクリックしたときに、<xref:System.Windows.Forms.ScrollBar.Value%2A>プロパティの変更で設定された値に従って、<xref:System.Windows.Forms.ScrollBar.LargeChange%2A>プロパティ。  
  
 キーまたはスクロール バーのボタンのクリックしたとき、ユーザーが矢印の 1 つ、<xref:System.Windows.Forms.ScrollBar.Value%2A>プロパティの変更で設定された値に従って、<xref:System.Windows.Forms.ScrollBar.SmallChange%2A>プロパティ。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.HScrollBar>
- <xref:System.Windows.Forms.VScrollBar>
- [Windows フォームで使用するコントロール](controls-to-use-on-windows-forms.md)
