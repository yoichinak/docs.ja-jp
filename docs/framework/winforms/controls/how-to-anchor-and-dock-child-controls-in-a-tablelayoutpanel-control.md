---
title: '方法: TableLayoutPanel コントロールで子コントロールを固定およびドッキングする'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
f1_keywords:
- net.ComponentModel.StyleCollectionEditor.TLP.AnchorDock
helpviewer_keywords:
- layout [Windows Forms], child controls
- controls [Windows Forms], child
- child controls [Windows Forms], anchoring and docking
- TableLayoutPanel control [Windows Forms], child controls
ms.assetid: 0d267c35-25f1-49b8-8976-c64e8f0ddc0b
ms.openlocfilehash: 7adbf9a98b25b237ee49d2689154e903d8fc0b5a
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/14/2019
ms.locfileid: "65586175"
---
# <a name="how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control"></a>方法: TableLayoutPanel コントロールで子コントロールを固定およびドッキングする
<xref:System.Windows.Forms.TableLayoutPanel> コントロールは、子コントロールの <xref:System.Windows.Forms.Control.Anchor%2A> プロパティと <xref:System.Windows.Forms.Control.Dock%2A> プロパティをサポートします。  
  
### <a name="to-align-a-child-control-in-a-tablelayoutpanel-cell"></a>TableLayoutPanel のセル内の子コントロールを揃えるには  
  
1. フォームで <xref:System.Windows.Forms.TableLayoutPanel> コントロールを作成します。  
  
2. 値を設定、<xref:System.Windows.Forms.TableLayoutPanel>コントロールの<xref:System.Windows.Forms.TableLayoutPanel.ColumnCount%2A>と<xref:System.Windows.Forms.TableLayoutPanel.RowCount%2A>プロパティ**1**します。  
  
3. 
  <xref:System.Windows.Forms.TableLayoutPanel> コントロールで <xref:System.Windows.Forms.Button> コントロールを作成します。 
  <xref:System.Windows.Forms.Button> がセルの左上隅を占有します。  
  
4. <xref:System.Windows.Forms.Button> コントロールの <xref:System.Windows.Forms.Control.Anchor%2A> プロパティの値を `Left`に変更します。 
  <xref:System.Windows.Forms.Button> コントロールが、セルの左罫線に合うように移動します。  
  
    > [!NOTE]
    >  この動作は、他のコンテナー コントロールの動作と異なります。 他のコンテナー コントロールでは、<xref:System.Windows.Forms.Control.Anchor%2A> プロパティが設定されてと子コントロールは移動せず、固定されたコントロールと親コンテナーの境界間の距離は、<xref:System.Windows.Forms.Control.Anchor%2A> プロパティが設定されたときに固定されます。  
  
5. <xref:System.Windows.Forms.Button> コントロールの <xref:System.Windows.Forms.Control.Anchor%2A> プロパティの値を `Top, Left`に変更します。 
  <xref:System.Windows.Forms.Button> コントロールがセルの左上隅を占有するよう移動します。  
  
6. 手順 5. を繰り返し、値の`Top, Right`を移動する、<xref:System.Windows.Forms.Button>セルの右上隅にあるコントロール。 `Bottom, Left` と `Bottom, Right` の値を指定して繰り返します。  
  
### <a name="to-stretch-a-child-control-in-a-tablelayoutpanel-cell"></a>TableLayoutPanel セル内の子コントロールを拡大するには  
  
1. <xref:System.Windows.Forms.Button> コントロールの <xref:System.Windows.Forms.Control.Anchor%2A> プロパティの値を `Left, Right`に変更します。 
  <xref:System.Windows.Forms.Button> コントロールがサイズ変更され、セルいっぱいに拡大されます。  
  
    > [!NOTE]
    >  この動作は、他のコンテナー コントロールの動作と異なります。 その他のコンテナー コントロールで子コントロールでないときにサイズ変更、<xref:System.Windows.Forms.Control.Anchor%2A>プロパティに設定されて`Left, Right`または`Top, Bottom`します。  
  
2. <xref:System.Windows.Forms.Button> コントロールの <xref:System.Windows.Forms.Control.Anchor%2A> プロパティの値を `Top, Bottom`に変更します。 
  <xref:System.Windows.Forms.Button> コントロールがサイズ変更され、セルの上から下まで拡大されます。  
  
3. <xref:System.Windows.Forms.Button> コントロールの <xref:System.Windows.Forms.Control.Anchor%2A> プロパティの値を `Top, Bottom, Left, Right`に変更します。 
  <xref:System.Windows.Forms.Button> コントロールがセルを満たすようサイズ変更されます。  
  
4. <xref:System.Windows.Forms.Button> コントロールの <xref:System.Windows.Forms.Control.Anchor%2A> プロパティの値を `None`に変更します。 
  <xref:System.Windows.Forms.Button> コントロールがサイズ変更され、セルの中央に配置されます。  
  
5. <xref:System.Windows.Forms.Button> コントロールの <xref:System.Windows.Forms.Control.Dock%2A> プロパティの値を <xref:System.Windows.Forms.DockStyle.Left> に変更します。 <xref:System.Windows.Forms.Button> コントロールが、セルの左罫線に合うように移動します。 <xref:System.Windows.Forms.Button> コントロールの幅は保持されますが、高さはセルを垂直方向に満たすようサイズ変更されます。  
  
    > [!NOTE]
    >  これは、他のコンテナー コントロール内で発生するのと同じ動作です。  
  
6. <xref:System.Windows.Forms.Button> コントロールの <xref:System.Windows.Forms.Control.Dock%2A> プロパティの値を <xref:System.Windows.Forms.DockStyle.Fill> に変更します。 
  <xref:System.Windows.Forms.Button> コントロールがセルを満たすようサイズ変更されます。  
  
## <a name="example"></a>例  
 次の図は、5 つの個別の <xref:System.Windows.Forms.TableLayoutPanel> のセルに固定されている 5 つのボタンを示しています。  
  
 ![TableLayoutPanel アンカー](./media/vs-tlpanchor.gif "VS_TLPanchor")  
  
 次の図は、4 つの個別の <xref:System.Windows.Forms.TableLayoutPanel> のセルの隅に固定されている 4 つのボタンを示しています。  
  
 ![TableLayoutPanel アンカー](./media/vs-tlpanchor2.gif "VS_TLPanchor2")  
  
 次の図は、3 つの個別の <xref:System.Windows.Forms.TableLayoutPanel> のセルに固定することで拡大された 3 つのボタンを示しています。  
  
 ![TableLayoutPanel アンカー](./media/vs-tlpanchor3.gif "VS_TLPAnchor3")  
  
 次のコード例は、<xref:System.Windows.Forms.TableLayoutPanel> コントロールの <xref:System.Windows.Forms.Button> コントロールにおけるすべての組み合わせの <xref:System.Windows.Forms.Control.Anchor%2A> プロパティの値を示します。  
  
 [!code-csharp[System.Windows.Forms.TableLayoutPanel.AnchorExampleForm#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.TableLayoutPanel.AnchorExampleForm/CS/TlpAnchorExampleForm.cs#1)]
 [!code-vb[System.Windows.Forms.TableLayoutPanel.AnchorExampleForm#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.TableLayoutPanel.AnchorExampleForm/VB/TlpAnchorExampleForm.vb#1)]  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 この例で必要な要素は次のとおりです。  
  
- System、System.Data、System.Drawing、および System.Windows.Forms の各アセンブリへの参照。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.TableLayoutPanel>
- [TableLayoutPanel コントロール](tablelayoutpanel-control-windows-forms.md)
