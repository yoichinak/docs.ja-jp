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
ms.openlocfilehash: 02db78b07930676235e55e535fb24f6ff618d823
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62012972"
---
# <a name="how-to-span-rows-and-columns-in-a-tablelayoutpanel-control"></a>方法: TableLayoutPanel コントロールの行と列を拡大する
コントロールで、<xref:System.Windows.Forms.TableLayoutPanel>コントロールが隣接する行と列にまたがることができます。  
  
> [!NOTE]
>  実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。 設定を変更するには、 **[ツール]** メニューの **[設定のインポートとエクスポート]** をクリックします。 詳細については、「[Visual Studio IDE のカスタマイズ](/visualstudio/ide/personalizing-the-visual-studio-ide)」を参照してください。  
  
### <a name="to-span-columns-and-rows"></a>列と行にまたがること  
  
1. <xref:System.Windows.Forms.TableLayoutPanel> ツールボックス **から** コントロールをフォームにドラッグします。  
  
2. ドラッグ、<xref:System.Windows.Forms.Button>コントロールから、**ツールボックス**の左上隅のセルに、<xref:System.Windows.Forms.TableLayoutPanel>コントロール。  
  
3. 設定、<xref:System.Windows.Forms.Button>コントロールの**ColumnSpan**プロパティを**2**します。 なお、<xref:System.Windows.Forms.Button>にまたがる最初と 2 番目の列を制御します。  
  
4. 設定、<xref:System.Windows.Forms.Button>コントロールの**RowSpan**プロパティを**2**します。 なお、<xref:System.Windows.Forms.Button>コントロールが最初と 2 番目の行にまたがっています。  
  
5. 設定、<xref:System.Windows.Forms.Button>コントロールの**ColumnSpan**プロパティを**1**します。 なお、<xref:System.Windows.Forms.Button>コントロールは、最初の列に移動し、最初と 2 番目の行にまたがます。  
  
## <a name="see-also"></a>関連項目

- [TableLayoutPanel コントロール](tablelayoutpanel-control-windows-forms.md)
