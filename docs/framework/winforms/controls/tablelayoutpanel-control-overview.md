---
title: TableLayoutPanel コントロールの概要
ms.date: 03/30/2017
f1_keywords:
- TableLayoutPanel
helpviewer_keywords:
- controls [Windows Forms], resizing
- resizable controls [Windows Forms]
- Windows Forms controls, proportional resizing
- Windows Forms, proportional resizing of controls
- layout [Windows Forms], TableLayoutPanel control
- TableLayoutPanel control [Windows Forms], about TableLayoutPanel control
ms.assetid: 337661c8-61cb-44ee-93e0-3662bddec327
ms.openlocfilehash: 65daba0ce1a6f1c37fb257c1029396577821aad9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62009631"
---
# <a name="tablelayoutpanel-control-overview"></a>TableLayoutPanel コントロールの概要
<xref:System.Windows.Forms.TableLayoutPanel> コントロールは、その内容をグリッド内に配置します。 レイアウトはデザイン時と実行時の両方で行われるため、アプリケーション環境の変更に合わせて動的に変更できます。 これにより、パネル内のコントロールを適切にサイズ変更することができるため、親コントロールのサイズ変更や、ローカライズによるテキスト長の変更などの変更に対応できます。  
  
 Windows フォーム コントロールは、<xref:System.Windows.Forms.TableLayoutPanel> の他のインスタンスを含めて、<xref:System.Windows.Forms.TableLayoutPanel> コントロールの子にすることができます。 これにより、実行時の変化に適応する高度なレイアウトを構築することができます。  
  
 <xref:System.Windows.Forms.TableLayoutPanel.RowCount%2A>、<xref:System.Windows.Forms.TableLayoutPanel.ColumnCount%2A>、および <xref:System.Windows.Forms.TableLayoutPanel.GrowStyle%2A> プロパティの値に応じて、<xref:System.Windows.Forms.TableLayoutPanel> コントロールを追加するときに新しいコントロールに合わせて拡張できます。 <xref:System.Windows.Forms.TableLayoutPanel.RowCount%2A> プロパティまたは <xref:System.Windows.Forms.TableLayoutPanel.ColumnCount%2A> プロパティのいずれかを 0 の値に設定すると、<xref:System.Windows.Forms.TableLayoutPanel> が対応する方向にバインド解除されます。  
  
 <xref:System.Windows.Forms.TableLayoutPanel> コントロールが完全に子コントロールになった後で、(水平または垂直の) 展開の方向を制御することもできます。 既定では、<xref:System.Windows.Forms.TableLayoutPanel> コントロールは行を追加することで下方向に拡張します。  
  
 既定の動作とは異なる方法で行と列を動作させる場合は、<xref:System.Windows.Forms.TableLayoutPanel.RowStyles%2A> プロパティと <xref:System.Windows.Forms.TableLayoutPanel.ColumnStyles%2A> プロパティを使用して、行と列のプロパティを制御できます。 行または列のプロパティを個別に設定することができます。  
  
 <xref:System.Windows.Forms.TableLayoutPanel> コントロールは、その子コントロールに `Cell`、`Column`、`Row`、`ColumnSpan`、および `RowSpan` の各プロパティを追加します。  
  
 子コントロールで `ColumnSpan` プロパティまたは `RowSpan` プロパティを設定することで、<xref:System.Windows.Forms.TableLayoutPanel> コントロールのセルをマージできます。  
  
1. [方法: 配置して、コントロールを TableLayoutPanel コントロールで伸縮](how-to-align-and-stretch-a-control-in-a-tablelayoutpanel-control.md)  
  
2. [方法: TableLayoutPanel コントロールの行と列にまたがる](how-to-span-rows-and-columns-in-a-tablelayoutpanel-control.md)  
  
3. [方法: TableLayoutPanel コントロールの列と行を編集します。](how-to-edit-columns-and-rows-in-a-tablelayoutpanel-control.md)  
  
4. [チュートリアル: TableLayoutPanel を使用して Windows フォーム コントロールの配置](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.FlowLayoutPanel>
- <xref:System.Windows.Forms.TableLayoutSettings>
- [方法: ローカリゼーションに対応する Windows フォーム レイアウトをデザインします。](how-to-design-a-windows-forms-layout-that-responds-well-to-localization.md)
- [方法: データ入力用のサイズ変更可能な Windows フォームを作成します。](how-to-create-a-resizable-windows-form-for-data-entry.md)
- [TableLayoutPanel コントロールの推奨される手順](best-practices-for-the-tablelayoutpanel-control.md)
