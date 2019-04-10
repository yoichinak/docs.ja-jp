---
title: '方法: Windows フォームの ToolTip コンポーネントの遅延時間を変更する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- ToolTip component [Windows Forms], delay values
- tooltips [Windows Forms], delay values
- examples [Windows Forms], tooltips
ms.assetid: 08979ba7-dd84-477b-ab17-8d06e759be99
ms.openlocfilehash: 5b903f48035ac27cdd79f0ea38a7a68d558b3c1f
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59198661"
---
# <a name="how-to-change-the-delay-of-the-windows-forms-tooltip-component"></a>方法: Windows フォームの ToolTip コンポーネントの遅延時間を変更する
Windows フォームに設定できる複数の遅延時間の値がある<xref:System.Windows.Forms.ToolTip>コンポーネント。 これらすべてのプロパティの測定単位は、(ミリ秒) です。 <xref:System.Windows.Forms.ToolTip.InitialDelay%2A>プロパティは、ユーザーが、関連付けられたコントロールに表示されるツールヒントの文字列でポイントする必要があります期間を決定します。 <xref:System.Windows.Forms.ToolTip.ReshowDelay%2A>プロパティ後続のヒント文字列が表示されるツールヒントに関連付けられている 1 つのコントロール間マウスを移動するためにかかる時間をミリ秒単位の数を設定します。 <xref:System.Windows.Forms.ToolTip.AutoPopDelay%2A>プロパティがツール ヒントの文字列が表示される時間の長さを決定します。 これらの値を設定するには、個別またはの値を設定して、<xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A>プロパティです。 その他の遅延に割り当てられている値に基づいてプロパティが設定、<xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A>プロパティ。 たとえば、 <xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A> N の値に設定されている<xref:System.Windows.Forms.ToolTip.InitialDelay%2A>N に設定されている<xref:System.Windows.Forms.ToolTip.ReshowDelay%2A>の値に設定されている<xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A>5 で割った値 (または N/5) と<xref:System.Windows.Forms.ToolTip.AutoPopDelay%2A>5 倍の値を示す値に設定されている、<xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A>プロパティ (または 5 個以上)。  
  
### <a name="to-set-the-delay"></a>遅延を設定するには  
  
1.  この例で示すように、次のプロパティを設定します。  
  
    ```vb  
    ToolTip1.InitialDelay = 500  
    ToolTip1.ReshowDelay = 100  
    ToolTip1.AutoPopDelay = 5000  
    ```  
  
    ```csharp  
    ToolTip1.InitialDelay = 500;  
    ToolTip1.ReshowDelay = 100;  
    ToolTip1.AutoPopDelay = 5000;  
    ```  
  
    ```cpp  
    toolTip1->InitialDelay = 500;  
    toolTip1->ReshowDelay = 100;  
    toolTip1->AutoPopDelay = 5000;  
    ```  
  
## <a name="see-also"></a>関連項目

- [ToolTip コンポーネントの概要](tooltip-component-overview-windows-forms.md)
- [方法: デザイン時に Windows フォームのコントロールにツールヒントを設定する](how-to-set-tooltips-for-controls-on-a-windows-form-at-design-time.md)
- [ToolTip コンポーネント](tooltip-component-windows-forms.md)
