---
title: '方法: Windows フォーム上のコントロールをドッキングする'
ms.date: 03/30/2017
helpviewer_keywords:
- controls [Windows Forms], docking
- Explorer-style applications [Windows Forms], creating
- Windows Forms controls, filling client area
ms.assetid: bc11f2e4-e90a-4830-b0e2-f43b6e2b8bec
ms.openlocfilehash: d015dce7307bec092f6da1dc5ee31691a6baf1f0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61941500"
---
# <a name="how-to-dock-controls-on-windows-forms"></a>方法: Windows フォーム上のコントロールをドッキングする
コントロールをフォームの端にドッキングまたはコントロールのコンテナー (フォームまたはコンテナー コントロールのいずれか) を入力することがあることができます。 たとえば、Windows エクスプ ローラーをドッキングその<xref:System.Windows.Forms.TreeView>、ウィンドウの左側にあるコントロールとその<xref:System.Windows.Forms.ListView>ウィンドウの右側にあるコントロール。 使用して、<xref:System.Windows.Forms.Control.Dock%2A>ドッキングのモードを定義する表示されているすべての Windows フォーム コントロールのプロパティ。  
  
> [!NOTE]
>  逆の z オーダーでコントロールがドッキングされます。  
  
 <xref:System.Windows.Forms.Control.Dock%2A>プロパティの対話、<xref:System.Windows.Forms.Control.AutoSize%2A>プロパティ。 詳細については、次を参照してください。 [AutoSize プロパティの概要](autosize-property-overview.md)します。  
  
### <a name="to-dock-a-control"></a>コントロールをドッキングするには  
  
1. ドッキングするコントロールを選択します。  
  
2. [プロパティ] ウィンドウの右側にある矢印をクリックします。、<xref:System.Windows.Forms.Control.Dock%2A>プロパティ。  
  
     一連の端とフォームの中央を表すボックスを示しています。 エディターが表示されます。  
  
3. コントロールをドッキングするフォームの端を表すボタンをクリックします。 コントロールのフォームまたはコンテナー コントロールの内容を入力するには、中央のボックスをクリックします。 クリックして **(なし)** ドッキングを無効にします。  
  
     コントロールのドッキングのエッジの境界に合わせてサイズを自動的にします。  
  
    > [!NOTE]
    >  継承されたコントロールである必要があります`Protected`ドッキングできるようにします。 コントロールのアクセス レベルを変更するには、次のように設定します。 その**修飾子**プロパティ ウィンドウでプロパティ。  
  
## <a name="see-also"></a>関連項目

- [Windows フォーム コントロール](index.md)
- [Windows フォームでのコントロールの配置](arranging-controls-on-windows-forms.md)
- [各 Windows フォーム コントロールのラベル設定とショートカットの作成](labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
- [Windows フォームで使用するコントロール](controls-to-use-on-windows-forms.md)
- [Windows フォーム コントロールの機能別一覧](windows-forms-controls-by-function.md)
- [方法: 固定およびドッキング FlowLayoutPanel コントロールで子コントロール](how-to-anchor-and-dock-child-controls-in-a-flowlayoutpanel-control.md)
- [方法: 固定およびドッキング TableLayoutPanel コントロールで子コントロール](how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md)
- [AutoSize プロパティの概要](autosize-property-overview.md)
- [方法: Windows フォームにコントロールを固定](how-to-anchor-controls-on-windows-forms.md)
