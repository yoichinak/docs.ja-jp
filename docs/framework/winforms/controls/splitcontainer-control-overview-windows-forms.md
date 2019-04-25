---
title: SplitContainer コントロールの概要 (Windows フォーム)
ms.date: 03/30/2017
f1_keywords:
- SplitContainer
helpviewer_keywords:
- SplitContainer control [Windows Forms], about SplitContainer control
ms.assetid: 6de5a5f7-97a5-402d-be6d-7e2785483db5
ms.openlocfilehash: 4afdd764b2f6ef7f15e8bd26459f0fa4c7d345e1
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59219422"
---
# <a name="splitcontainer-control-overview-windows-forms"></a>SplitContainer コントロールの概要 (Windows フォーム)
Windows フォームの <xref:System.Windows.Forms.SplitContainer> コントロールは複合と考えることができ、移動可能なバーで区切られた 2 つのパネルです。 マウス ポインターがバーの上に移動すると、ポインターの形が変わり、バーが移動可能であることを示します。  
  
> [!IMPORTANT]
>  **ツールボックス**、<xref:System.Windows.Forms.SplitContainer>置換を制御、 <xref:System.Windows.Forms.Splitter> Visual Studio の以前のバージョンであるコントロール。 <xref:System.Windows.Forms.SplitContainer> コントロールは <xref:System.Windows.Forms.Splitter> コントロールより優先されます。 <xref:System.Windows.Forms.Splitter>クラスも含める、[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]既存のアプリケーションとの互換性のために使用するぜひが、<xref:System.Windows.Forms.SplitContainer>新しいプロジェクトのコントロール。  
  
 <xref:System.Windows.Forms.SplitContainer>コントロール、複雑なユーザー インターフェイスを作成することができます。 多くの場合、1 つのパネルで選択範囲を決定、その他のパネルに表示されるオブジェクト。 この配置は、情報の表示と参照に対して非常に効果的です。 2 つのパネルで地域では、情報を集計して、バー、または「分割」により、パネルのサイズを変更するユーザーに簡単です。  
  
 1 つ以上<xref:System.Windows.Forms.SplitContainer>コントロール ネストすることも、2 つ目<xref:System.Windows.Forms.SplitContainer>上部と下部のパネルを作成する、水平方向に制御します。  
  
 注意してくださいを<xref:System.Windows.Forms.SplitContainer>コントロールは既定では、キーボードからアクセスは、ユーザーは、分割線を移動する方向キーを押すことができます、<xref:System.Windows.Forms.SplitContainer.IsSplitterFixed%2A>プロパティに設定されて`false`します。  
  
 <xref:System.Windows.Forms.SplitContainer.Orientation%2A>のプロパティ、<xref:System.Windows.Forms.SplitContainer>コントロール、コントロール自体のない、スプリッターの方向を決定します。 そのため、このプロパティ設定されている場合<xref:System.Windows.Forms.Orientation.Vertical>、分割線を上から下、左および右のパネルを作成する実行します。  
  
 さらに、注意の値、<xref:System.Windows.Forms.SplitContainer.SplitterRectangle%2A>プロパティの値によって異なります、<xref:System.Windows.Forms.SplitContainer.Orientation%2A>プロパティ。 詳細については、次を参照してください。<xref:System.Windows.Forms.SplitContainer.SplitterRectangle%2A>プロパティ。  
  
 移動とサイズを制限することも、<xref:System.Windows.Forms.SplitContainer>コントロール。 <xref:System.Windows.Forms.SplitContainer.FixedPanel%2A>プロパティは、パネルは残ります後に同じサイズを決定します。、<xref:System.Windows.Forms.SplitContainer>コントロールがサイズ変更、および<xref:System.Windows.Forms.SplitContainer.IsSplitterFixed%2A>プロパティの場合、スプリッターは、キーボードまたはマウスを移動することが決定します。  
  
> [!NOTE]
>  場合でも、<xref:System.Windows.Forms.SplitContainer.IsSplitterFixed%2A>プロパティに設定されて`true`、分割ウィンドウも移動を許可するなど、プログラムでを使用して、<xref:System.Windows.Forms.SplitContainer.SplitterDistance%2A>プロパティ。  
  
 最後に、各パネル、<xref:System.Windows.Forms.SplitContainer>コントロールの個々 のサイズを決定するプロパティがあります。  
  
## <a name="commonly-used-properties-methods-and-events"></a>一般的に使用されるプロパティ、メソッド、およびイベント  
  
|名前|説明|  
|----------|-----------------|  
|<xref:System.Windows.Forms.SplitContainer.FixedPanel%2A> プロパティ|同じパネルを決定後サイズ、<xref:System.Windows.Forms.SplitContainer>コントロールのサイズを変更します。|  
|<xref:System.Windows.Forms.SplitContainer.IsSplitterFixed%2A> プロパティ|キーボードまたはマウスで分割線を移動できるかどうかを決定します。|  
|<xref:System.Windows.Forms.SplitContainer.Orientation%2A> プロパティ|垂直方向または水平方向に分割が配置されているかどうかを決定します。|  
|<xref:System.Windows.Forms.SplitContainer.SplitterDistance%2A> プロパティ|移動可能な分割バーを左端または上端からのピクセル単位で距離を決定します。|  
|<xref:System.Windows.Forms.SplitContainer.SplitterIncrement%2A> プロパティ|最小距離 (ピクセル単位)、スプリッターをユーザーが移動できることを決定します。|  
|<xref:System.Windows.Forms.SplitContainer.SplitterWidth%2A> プロパティ|分割線のピクセル単位での太さを決定します。|  
|<xref:System.Windows.Forms.SplitContainer.SplitterMoving> イベント|分割線を移動するときに発生します。|  
|<xref:System.Windows.Forms.SplitContainer.SplitterMoved> イベント|分割線が移動されたときに発生します。|  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.SplitContainer>
- [SplitContainer コントロール](splitcontainer-control-windows-forms.md)
- [SplitContainer コントロールのサンプル](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/0ffz7d1b(v=vs.90))
