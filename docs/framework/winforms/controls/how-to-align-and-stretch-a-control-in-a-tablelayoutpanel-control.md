---
title: '方法: TableLayoutPanel コントロール内でコントロールを配置して伸縮する'
ms.date: 03/30/2017
f1_keywords:
- net.ComponentModel.StyleCollectionEditor.TLP.AlignStretchCtrl
helpviewer_keywords:
- TableLayoutPanel control [Windows Forms], stretching controls
- controls [Windows Forms], stretching
- controls [Windows Forms], aligning
ms.assetid: 7dc1a157-6fee-4995-8ebc-b65bdc0909a8
ms.openlocfilehash: fd32593bcad9e3f3ef93edee8aa2659d423f9feb
ms.sourcegitcommit: 0d0a6e96737dfe24d3257b7c94f25d9500f383ea
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/07/2019
ms.locfileid: "65210363"
---
# <a name="how-to-align-and-stretch-a-control-in-a-tablelayoutpanel-control"></a>方法: TableLayoutPanel コントロール内でコントロールを配置して伸縮する

内のコントロールを拡張して整列することができます、<xref:System.Windows.Forms.TableLayoutPanel>で、<xref:System.Windows.Forms.Control.Anchor%2A>と<xref:System.Windows.Forms.Control.Dock%2A>プロパティ。

## <a name="align-and-stretch-a-control"></a>配置して伸縮コントロール

1. Visual Studio で、ドラッグ、<xref:System.Windows.Forms.TableLayoutPanel>コントロールから、**ツールボックス**フォームにします。

2. ドラッグ、<xref:System.Windows.Forms.Button>コントロールから、**ツールボックス**の左上隅のセルに、<xref:System.Windows.Forms.TableLayoutPanel>コントロール。 <xref:System.Windows.Forms.Button>コントロールがセルの中央に配置します。

3. 値を設定、<xref:System.Windows.Forms.Button>コントロールの<xref:System.Windows.Forms.Control.Anchor%2A>プロパティを`Left,Right`します。 <xref:System.Windows.Forms.Button>端まで拡大に合わせてセルの幅を制御します。

4. 値を設定、<xref:System.Windows.Forms.Button>コントロールの<xref:System.Windows.Forms.Control.Anchor%2A>プロパティを`Top,Bottom`します。 <xref:System.Windows.Forms.Button>端まで拡大に合わせてセルの高さを制御します。

5. 値を設定、<xref:System.Windows.Forms.Button>コントロールの<xref:System.Windows.Forms.Control.Dock%2A>プロパティを<xref:System.Windows.Forms.DockStyle.Fill>します。 <xref:System.Windows.Forms.Button>セル コントロールを拡張します。

6. 値を設定、<xref:System.Windows.Forms.Button>コントロールの<xref:System.Windows.Forms.Control.Dock%2A>プロパティを<xref:System.Windows.Forms.DockStyle.None>します。 <xref:System.Windows.Forms.Button>コントロールは、元のサイズを返し、セルの左上隅に移動します。 **Windows フォーム デザイナー**設定が、<xref:System.Windows.Forms.Control.Anchor%2A>プロパティを`Top, Left`します。

7. 値を設定、<xref:System.Windows.Forms.Button>コントロールの<xref:System.Windows.Forms.Control.Anchor%2A>プロパティを`Bottom,Right`します。 <xref:System.Windows.Forms.Button>コントロールがセルの右下隅に移動します。

8. 値を設定、<xref:System.Windows.Forms.Button>コントロールの<xref:System.Windows.Forms.Control.Anchor%2A>プロパティを<xref:System.Windows.Forms.AnchorStyles.None>します。 <xref:System.Windows.Forms.Button>コントロールがセルの中央に移動します。

## <a name="see-also"></a>関連項目

- [TableLayoutPanel コントロール](tablelayoutpanel-control-windows-forms.md)
