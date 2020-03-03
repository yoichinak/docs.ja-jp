---
title: '方法: デザイン時にフォームの端に合わせてコントロールを配置する'
ms.date: 03/30/2017
helpviewer_keywords:
- custom controls [Windows Forms], docking using designer
- Dock property [Windows Forms], aligning controls (using designer)
ms.assetid: 51f08998-5e3b-4330-be58-a4edd0eb60f4
ms.openlocfilehash: b08e01eb9adb984a32a8fc435cf1f3b93b159a14
ms.sourcegitcommit: 0d0a6e96737dfe24d3257b7c94f25d9500f383ea
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/07/2019
ms.locfileid: "65210380"
---
# <a name="how-to-align-a-control-to-the-edges-of-forms-at-design-time"></a>方法: デザイン時にフォームの端に合わせてコントロールを配置する

コントロールの値を設定して、フォームの端に合わせて整列を行うことができます、<xref:System.Windows.Forms.Control.Dock%2A>プロパティ。 このプロパティは、フォーム内のコントロールの場所を指定します。 <xref:System.Windows.Forms.Control.Dock%2A> プロパティには次の値のいずれかを設定できます。

|設定|コントロールへの影響|
|-------------|----------------------------|
|<xref:System.Windows.Forms.DockStyle.Bottom>|フォームの下部にドッキングします。|
|<xref:System.Windows.Forms.DockStyle.Fill>|フォームの残りの全スペースを埋めます。|
|<xref:System.Windows.Forms.DockStyle.Left>|フォームの左側にドッキングします。|
|<xref:System.Windows.Forms.DockStyle.None>|によって指定された場所に表示されます、任意の場所と、ドッキングせずその<xref:System.Windows.Forms.Control.Location%2A>します。|
|<xref:System.Windows.Forms.DockStyle.Right>|フォームの右側にドッキングします。|
|<xref:System.Windows.Forms.DockStyle.Top>|フォームの上部にドッキングします。|

これらの値は、コードでも設定できます。 詳細については、「[方法 :コントロールをフォームの端を揃える](how-to-align-a-control-to-the-edges-of-forms.md)します。

## <a name="set-the-dock-property-for-your-control-at-design-time"></a>デザイン時に、コントロールの Dock プロパティを設定します。

1. Visual Studio で Windows フォーム デザイナーでコントロールを選択します。

2. **プロパティ**ウィンドウで、ドロップダウン リスト ボックスには、[次へ] をクリックして、<xref:System.Windows.Forms.Control.Dock%2A>プロパティ。

     6 つを表すグラフィカル インターフェイス<xref:System.Windows.Forms.Control.Dock%2A>設定が表示されます。

3. 適切な設定を選択します。

4. コントロールの設定で指定された方法でドッキングされます。

## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.Control.Dock%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.Control.Anchor%2A?displayProperty=nameWithType>
- [方法: コントロールをフォームの端を揃える](how-to-align-a-control-to-the-edges-of-forms.md)
- [チュートリアル: スナップ線を使用して Windows フォーム コントロールの配置](walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)
- [方法: Windows フォームにコントロールを固定](how-to-anchor-controls-on-windows-forms.md)
- [方法: 固定およびドッキング TableLayoutPanel コントロールで子コントロール](how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md)
- [方法: 固定およびドッキング FlowLayoutPanel コントロールで子コントロール](how-to-anchor-and-dock-child-controls-in-a-flowlayoutpanel-control.md)
- [チュートリアル: TableLayoutPanel を使用して Windows フォーム コントロールの配置](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)
- [チュートリアル: FlowLayoutPanel を使用して Windows フォーム コントロールの配置](walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)
- [デザイン時の Windows フォーム コントロールの開発](developing-windows-forms-controls-at-design-time.md)
