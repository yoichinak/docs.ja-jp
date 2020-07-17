---
title: '方法: TableLayoutPanel コントロールの行と列を拡大する'
ms.date: 03/30/2017
f1_keywords:
- net.ComponentModel.StyleCollectionEditor.TLP.SpanRowsColumns
helpviewer_keywords:
- columns [Windows Forms], spanning
- merging cells
- TableLayoutPanel control [Windows Forms], spanning rows and columns
- rows [Windows Forms], spanning
- cells [Windows Forms], merging
ms.assetid: a8a2fdd3-a848-48b0-a4cd-4e85ebded87e
ms.openlocfilehash: a215b2b4e05bab5c81d2779d4b67d5b9d57b6ba5
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69039695"
---
# <a name="how-to-span-rows-and-columns-in-a-tablelayoutpanel-control"></a>方法: TableLayoutPanel コントロールの行と列を拡大する
<xref:System.Windows.Forms.TableLayoutPanel>コントロール内のコントロールは、隣接する行と列にまたがることができます。

## <a name="to-span-columns-and-rows"></a>列と行をスパンするには

1. <xref:System.Windows.Forms.TableLayoutPanel> ツールボックス **から** コントロールをフォームにドラッグします。

2. [ <xref:System.Windows.Forms.Button> **ツールボックス**] からコントロールをドラッグして、 <xref:System.Windows.Forms.TableLayoutPanel>コントロールの左上のセルに移動します。

3. コントロールの**columnspan**プロパティを2に設定します。 <xref:System.Windows.Forms.Button> コントロールが<xref:System.Windows.Forms.Button> 1 番目と2番目の列にまたがっていることに注意してください。

4. コントロールの RowSpan プロパティを**2**に設定します。 <xref:System.Windows.Forms.Button> コントロールが<xref:System.Windows.Forms.Button> 1 行目と2番目の行にまたがっていることに注意してください。

5. コントロールの**columnspan**プロパティを1に設定します。 <xref:System.Windows.Forms.Button> コントロールが<xref:System.Windows.Forms.Button>最初の列に移動し、最初の行と2番目の行にまたがっていることに注意してください。

## <a name="see-also"></a>関連項目

- [TableLayoutPanel コントロール](tablelayoutpanel-control-windows-forms.md)
