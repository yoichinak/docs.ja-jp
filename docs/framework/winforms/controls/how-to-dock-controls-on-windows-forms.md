---
title: '方法: Windows フォーム上のコントロールをドッキングする'
ms.date: 03/30/2017
helpviewer_keywords:
- controls [Windows Forms], docking
- Explorer-style applications [Windows Forms], creating
- Windows Forms controls, filling client area
ms.assetid: bc11f2e4-e90a-4830-b0e2-f43b6e2b8bec
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 58b61af306385a245bedf16e370e6830c370a622
ms.sourcegitcommit: 37616676fde89153f563a485fc6159fc57326fc2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/23/2019
ms.locfileid: "69987478"
---
# <a name="how-to-dock-controls-on-windows-forms"></a>方法: Windows フォームにコントロールをドッキングする

コントロールをフォームの端にドッキングしたり、コントロールのコンテナー (フォームまたはコンテナーコントロールのいずれか) に入力したりすることができます。 たとえば、Windows エクスプローラーでは、 <xref:System.Windows.Forms.TreeView>ウィンドウの左側<xref:System.Windows.Forms.ListView>にコントロールがドッキングされ、コントロールはウィンドウの右側に表示されます。 ドッキングモード<xref:System.Windows.Forms.Control.Dock%2A>を定義するには、表示されているすべての Windows フォームコントロールに対してプロパティを使用します。

> [!NOTE]
> コントロールは、逆 z オーダーでドッキングされます。

プロパティ<xref:System.Windows.Forms.Control.Dock%2A>は、 <xref:System.Windows.Forms.Control.AutoSize%2A>プロパティと対話します。 詳細については、「 [AutoSize プロパティの概要](autosize-property-overview.md)」を参照してください。

## <a name="to-dock-a-control"></a>コントロールをドッキングするには

1. Visual Studio で、ドッキングするコントロールを選択します。

2. **[プロパティ]** ウィンドウで、 <xref:System.Windows.Forms.Control.Dock%2A>プロパティの右側にある矢印をクリックします。

   フォームの端と中央を表す一連のボックスを示すエディターが表示されます。

3. コントロールをドッキングするフォームの端を表すボタンをクリックします。 コントロールのフォームまたはコンテナーコントロールの内容を塗りつぶすには、中央のボックスをクリックします。 **[(なし)]** をクリックして、ドッキングを無効にします。

   ドッキングされた端の境界に合わせてコントロールのサイズが自動的に変更されます。

   > [!NOTE]
   > 継承された`Protected`コントロールは、ドッキングできる必要があります。 コントロールのアクセスレベルを変更するには、 **[プロパティ]** ウィンドウでその **[修飾子]** プロパティを設定します。

## <a name="see-also"></a>関連項目

- [Windows フォーム コントロール](index.md)
- [各 Windows フォーム コントロールのラベル設定とショートカットの作成](labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
- [Windows フォームで使用するコントロール](controls-to-use-on-windows-forms.md)
- [Windows フォーム コントロールの機能別一覧](windows-forms-controls-by-function.md)
- [方法: FlowLayoutPanel コントロールに子コントロールを固定およびドッキングする](how-to-anchor-and-dock-child-controls-in-a-flowlayoutpanel-control.md)
- [方法: TableLayoutPanel コントロールに子コントロールを固定およびドッキングする](how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md)
- [AutoSize プロパティの概要](autosize-property-overview.md)
- [方法: Windows フォームのアンカーコントロール](how-to-anchor-controls-on-windows-forms.md)
