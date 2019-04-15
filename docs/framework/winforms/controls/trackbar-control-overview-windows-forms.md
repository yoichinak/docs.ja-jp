---
title: TrackBar コントロールの概要 (Windows フォーム)
ms.date: 03/30/2017
f1_keywords:
- TrackBar
helpviewer_keywords:
- sliders [Windows Forms], about sliders
- TrackBar control [Windows Forms], about TrackBar control
- slider controls [Windows Forms], about slider controls
ms.assetid: 95910ecb-8a4c-4776-89fa-206c89ed6973
ms.openlocfilehash: 1606db73485944f3dfa8b9c084bffda817520c7c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59200637"
---
# <a name="trackbar-control-overview-windows-forms"></a>TrackBar コントロールの概要 (Windows フォーム)
Windows フォーム<xref:System.Windows.Forms.TrackBar>コントロール ("slider"コントロールと呼ばれることもあります) が大量の情報をナビゲートするのか、数値の設定を視覚的に調整するために使用されます。 <xref:System.Windows.Forms.TrackBar>コントロールに 2 つの部分がある: 一般的に、スライダーとティックとも呼ばれます。 Thumb は、調整可能な部分です。 その位置に対応して、<xref:System.Windows.Forms.TrackBar.Value%2A>プロパティ。 目盛りは、一定の間隔で間隔が視覚インジケーターです。 単位を指定し、水平方向または垂直方向に配置することができますが、トラック バーが移動します。 たとえば、トラック バーを使用して、システムのカーソルの点滅速度やマウス速度を制御する可能性があります。  
  
## <a name="key-properties"></a>キー プロパティ  
 キー プロパティ、<xref:System.Windows.Forms.TrackBar>コントロールは<xref:System.Windows.Forms.TrackBar.Value%2A>、 <xref:System.Windows.Forms.TrackBar.TickFrequency%2A>、 <xref:System.Windows.Forms.TrackBar.Minimum%2A>、および<xref:System.Windows.Forms.TrackBar.Maximum%2A>します。 <xref:System.Windows.Forms.TrackBar.TickFrequency%2A> 目盛りの間隔です。 <xref:System.Windows.Forms.TrackBar.Minimum%2A> <xref:System.Windows.Forms.TrackBar.Maximum%2A>トラック バーを表すことができる最小値と最大値です。  
  
 その他の 2 つの重要なプロパティが<xref:System.Windows.Forms.TrackBar.SmallChange%2A>と<xref:System.Windows.Forms.TrackBar.LargeChange%2A>します。 値、<xref:System.Windows.Forms.TrackBar.SmallChange%2A>プロパティは、thumb が押された、左または右矢印キーを持つへの応答での位置の数。 値、<xref:System.Windows.Forms.TrackBar.LargeChange%2A>プロパティがつまみが移動すると、PAGE UP または PAGE DOWN キーを押すと、またはマウスへの応答では、トラック バーのつまみの両側でクリックしての位置の数。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.TrackBar>
- [TrackBar コントロール](trackbar-control-windows-forms.md)
