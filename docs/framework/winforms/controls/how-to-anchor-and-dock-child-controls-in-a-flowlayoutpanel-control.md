---
title: '方法: FlowLayoutPanel コントロールで子コントロールを固定およびドッキングする'
ms.date: 03/30/2017
helpviewer_keywords:
- layout [Windows Forms], child controls
- FlowLayoutPanel control [Windows Forms], child controls
- controls [Windows Forms], child
- child controls [Windows Forms], anchoring and docking
ms.assetid: a2bcdfca-9b63-45e6-9c0e-3411015cba98
ms.openlocfilehash: 255ac50ae79d6931c9b82b50677c450c0834fdea
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62011183"
---
# <a name="how-to-anchor-and-dock-child-controls-in-a-flowlayoutpanel-control"></a>方法: FlowLayoutPanel コントロールで子コントロールを固定およびドッキングする
<xref:System.Windows.Forms.FlowLayoutPanel> コントロールは、子コントロールの <xref:System.Windows.Forms.Control.Anchor%2A> プロパティと <xref:System.Windows.Forms.Control.Dock%2A> プロパティをサポートします。  
  
### <a name="to-anchor-and-dock-child-controls-in-a-flowlayoutpanel-control"></a>FlowLayoutPanel コントロールで子コントロールを固定およびドッキングするには  
  
1. フォームで <xref:System.Windows.Forms.FlowLayoutPanel> コントロールを作成します。  
  
2. 設定、<xref:System.Windows.Forms.Control.Width%2A>の<xref:System.Windows.Forms.FlowLayoutPanel>に制御を**300**、設定とその<xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A>に<xref:System.Windows.Forms.FlowDirection.TopDown>します。  
  
3. 2 つの <xref:System.Windows.Forms.Button> コントロールを作成し、<xref:System.Windows.Forms.FlowLayoutPanel> コントロールに配置します。  
  
4. 設定、<xref:System.Windows.Forms.Control.Width%2A>に最初のボタンの**200**します。  
  
5. 2 番目のボタンの <xref:System.Windows.Forms.Control.Dock%2A> プロパティを <xref:System.Windows.Forms.DockStyle.Fill> に設定します。  
  
    > [!NOTE]
    >  2 番目のボタンは、最初のボタンと同じ幅を前提としています。 <xref:System.Windows.Forms.FlowLayoutPanel> コントロールの幅にまたがって伸縮しません。  
  
6. 2 番目のボタンの <xref:System.Windows.Forms.Control.Dock%2A> プロパティを `None` に設定します。 これにより、元の幅のボタンを前提とします。  
  
7. 2 番目のボタンの <xref:System.Windows.Forms.Control.Anchor%2A> プロパティを `Left, Right` に設定します。  
  
    > [!IMPORTANT]
    >  2 番目のボタンは、最初のボタンと同じ幅を前提としています。 <xref:System.Windows.Forms.FlowLayoutPanel> コントロールの幅にまたがって伸縮しません。 これは、<xref:System.Windows.Forms.FlowLayoutPanel> コントロールの固定とドッキングの一般的な規則です。垂直方向のフローについては、<xref:System.Windows.Forms.FlowLayoutPanel> コントロールが、幅の最大の列の子コントロールから暗黙の列の幅を計算します。 <xref:System.Windows.Forms.Control.Anchor%2A> プロパティまたは <xref:System.Windows.Forms.Control.Dock%2A> プロパティを持つこの列のその他のすべてのコントロールが、この暗黙の列に合わせて配置または拡大されます。 この動作は、水平のフロー方向と同様の方法で機能します。 <xref:System.Windows.Forms.FlowLayoutPanel> コントロールは、行で最も高い子コントロールから、暗黙の行の高さを計算して、この行のすべてのドッキングまたは固定の子コントロールは、暗黙の行に合わせて配置またはサイズが変更されます。  
  
## <a name="example"></a>例  
 次の図は、<xref:System.Windows.Forms.FlowLayoutPanel> 内の青のボタンを基準とする相対位置に固定されてドッキングされる 4 つのボタンを示しています。 <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> が <xref:System.Windows.Forms.FlowDirection.LeftToRight> です。  
  
 ![FlowLayoutPanel アンカー](./media/net-flpanchorexp.gif "NET_FLPanchorExp")  
  
 次の図は、<xref:System.Windows.Forms.FlowLayoutPanel> 内の青のボタンを基準とする相対位置に固定されてドッキングされる 4 つのボタンを示しています。 <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> が <xref:System.Windows.Forms.FlowDirection.TopDown> です。  
  
 ![FlowLayoutPanel アンカー](./media/vs-flpanchor2.gif "VS_FLPanchor2")  
  
 次のコード例は、<xref:System.Windows.Forms.FlowLayoutPanel> コントロールの <xref:System.Windows.Forms.Button> コントロールにおける様々な <xref:System.Windows.Forms.Control.Anchor%2A> プロパティの値を示します。  
  
 [!code-csharp[System.Windows.Forms.FlowLayoutPanel.AnchorExampleForm#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlowLayoutPanel.AnchorExampleForm/CS/FlpAnchorExampleForm.cs#1)]
 [!code-vb[System.Windows.Forms.FlowLayoutPanel.AnchorExampleForm#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlowLayoutPanel.AnchorExampleForm/VB/FlpAnchorExampleForm.vb#1)]  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 この例で必要な要素は次のとおりです。  
  
- System、System.Data、System.Drawing、および System.Windows.Forms の各アセンブリへの参照。  
  
 Visual Basic または Visual C# からこの例をビルドする方法については、[コマンド ラインからのビルド](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md)、または[csc.exe を使用したコマンド ラインからのビルド](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md) を参照してください。 新しいプロジェクトにコードを貼り付けることによって、この例では、Visual Studio を構築することもできます。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.FlowLayoutPanel>
- [FlowLayoutPanel コントロールの概要](flowlayoutpanel-control-overview.md)
