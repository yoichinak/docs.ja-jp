---
title: Panel コントロールの概要 (Windows フォーム)
ms.date: 03/30/2017
f1_keywords:
- Panel
helpviewer_keywords:
- grouping controls [Windows Forms], Panel control
- Panel control [Windows Forms], about Panel control
ms.assetid: b6b83636-2c39-4dad-89d6-f0fa41049a74
ms.openlocfilehash: 2b70996f7944f3f5ef8ef8bc80015836956a9b00
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/09/2019
ms.locfileid: "57715504"
---
# <a name="panel-control-overview-windows-forms"></a>Panel コントロールの概要 (Windows フォーム)
Windows フォーム<xref:System.Windows.Forms.Panel>コントロールを使用すると、他のコントロールの特定のグループ化を提供します。 通常、関数によってフォームを分割するのにパネルを使用します。 たとえば、どの宅配業者を使用するなどの絞り込みメール配信オプションを指定する注文書があります。 パネル内のすべてのオプションをグループ化と、ユーザーが論理視覚的に。 デザイン時にすべてのコントロールを簡単に移動できます-移動すると、<xref:System.Windows.Forms.Panel>もその格納されているコントロールが移動してすべての制御します。 パネルにグループ化コントロールを介してアクセスできるその<xref:System.Windows.Forms.Control.Controls%2A>プロパティ。 このプロパティのコレクションを返します<xref:System.Windows.Forms.Control>コントロールをキャストする必要があります通常のインスタンスがその特定の型には、この方法を取得します。  
  
## <a name="panel-versus-groupbox"></a>GroupBox とパネル  
 <xref:System.Windows.Forms.Panel>コントロールに似ていますが、<xref:System.Windows.Forms.GroupBox>制御。 ただし、のみ、<xref:System.Windows.Forms.Panel>コントロールがスクロール バーを持つことができますのみと、<xref:System.Windows.Forms.GroupBox>コントロールにキャプションが表示されます。  
  
## <a name="key-properties"></a>キー プロパティ  
 スクロール バーを表示するには、設定、<xref:System.Windows.Forms.ScrollableControl.AutoScroll%2A>プロパティを`true`します。 設定して、パネルの外観をカスタマイズすることも、 <xref:System.Windows.Forms.Control.BackColor%2A>、 <xref:System.Windows.Forms.Control.BackgroundImage%2A>、および<xref:System.Windows.Forms.Panel.BorderStyle%2A>プロパティ。 詳細については、<xref:System.Windows.Forms.Control.BackColor%2A>と<xref:System.Windows.Forms.Control.BackgroundImage%2A>プロパティを参照してください[方法。パネルの背景を設定](how-to-set-the-background-of-a-windows-forms-panel.md)します。 <xref:System.Windows.Forms.Panel.BorderStyle%2A>プロパティが表示されている境界のない、パネルが記載されているかどうかを決定します (<xref:System.Windows.Forms.BorderStyle.None>)、プレーンな行 (<xref:System.Windows.Forms.BorderStyle.FixedSingle>)、またはシャドウされた行 (<xref:System.Windows.Forms.BorderStyle.Fixed3D>)。  
  
## <a name="see-also"></a>関連項目
- <xref:System.Windows.Forms.Panel>
- [GroupBox コントロール](groupbox-control-windows-forms.md)
- [方法: コントロール デザイナーを使用して Windows フォーム Panel コントロールをグループ](group-controls-with-wf-panel-control-using-the-designer.md)
- [方法: デザイナーを使用して Windows フォーム パネルの背景を設定します。](how-to-set-the-background-of-a-windows-forms-panel-using-the-designer.md)
