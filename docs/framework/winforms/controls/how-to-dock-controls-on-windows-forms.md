---
title: '方法: Windows フォーム上のコントロールをドッキングする'
ms.date: 03/30/2017
helpviewer_keywords:
- controls [Windows Forms], docking
- Explorer-style applications [Windows Forms], creating
- Windows Forms controls, filling client area
ms.assetid: bc11f2e4-e90a-4830-b0e2-f43b6e2b8bec
ms.openlocfilehash: dc514fd8b9b7a17bf07a878e42729db4187d2b82
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69963627"
---
# <a name="how-to-dock-controls-on-windows-forms"></a>方法: Windows フォーム上のコントロールをドッキングする
コントロールをフォームの端にドッキングしたり、コントロールのコンテナー (フォームまたはコンテナーコントロールのいずれか) に入力したりすることができます。 たとえば、Windows エクスプローラーでは、 <xref:System.Windows.Forms.TreeView>ウィンドウの左側<xref:System.Windows.Forms.ListView>にコントロールがドッキングされ、コントロールはウィンドウの右側に表示されます。 ドッキングモード<xref:System.Windows.Forms.Control.Dock%2A>を定義するには、表示されているすべての Windows フォームコントロールに対してプロパティを使用します。  
  
> [!NOTE]
> コントロールは、逆 z オーダーでドッキングされます。  
  
 プロパティ<xref:System.Windows.Forms.Control.Dock%2A>は、 <xref:System.Windows.Forms.Control.AutoSize%2A>プロパティと対話します。 詳細については、「 [AutoSize プロパティの概要](autosize-property-overview.md)」を参照してください。  
  
### <a name="to-dock-a-control"></a>コントロールをドッキングするには  
  
1. ドッキングするコントロールを選択します。  
  
2. プロパティウィンドウで、 <xref:System.Windows.Forms.Control.Dock%2A>プロパティの右側にある矢印をクリックします。  
  
     フォームの端と中央を表す一連のボックスを示すエディターが表示されます。  
  
3. コントロールをドッキングするフォームの端を表すボタンをクリックします。 コントロールのフォームまたはコンテナーコントロールの内容を塗りつぶすには、中央のボックスをクリックします。 **[(なし)]** をクリックして、ドッキングを無効にします。  
  
     ドッキングされた端の境界に合わせてコントロールのサイズが自動的に変更されます。  
  
    > [!NOTE]
    > 継承された`Protected`コントロールは、ドッキングできる必要があります。 コントロールのアクセスレベルを変更するには、プロパティウィンドウの **[修飾子]** プロパティを設定します。  
  
## <a name="see-also"></a>関連項目

- [Windows フォーム コントロール](index.md)
- [Windows フォームでのコントロールの配置](arranging-controls-on-windows-forms.md)
- [各 Windows フォーム コントロールのラベル設定とショートカットの作成](labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
- [Windows フォームで使用するコントロール](controls-to-use-on-windows-forms.md)
- [Windows フォーム コントロールの機能別一覧](windows-forms-controls-by-function.md)
- [方法: FlowLayoutPanel コントロールに子コントロールを固定およびドッキングする](how-to-anchor-and-dock-child-controls-in-a-flowlayoutpanel-control.md)
- [方法: TableLayoutPanel コントロールに子コントロールを固定およびドッキングする](how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md)
- [AutoSize プロパティの概要](autosize-property-overview.md)
- [方法: Windows フォームのアンカーコントロール](how-to-anchor-controls-on-windows-forms.md)
