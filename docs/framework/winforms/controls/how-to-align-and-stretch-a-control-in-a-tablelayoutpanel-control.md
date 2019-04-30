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
ms.openlocfilehash: 6f36914387519b027fcf4cb6bf1e7654e551b3eb
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62010996"
---
# <a name="how-to-align-and-stretch-a-control-in-a-tablelayoutpanel-control"></a>方法: TableLayoutPanel コントロール内でコントロールを配置して伸縮する
内のコントロールを拡張して整列することができます、<xref:System.Windows.Forms.TableLayoutPanel>で、<xref:System.Windows.Forms.Control.Anchor%2A>と<xref:System.Windows.Forms.Control.Dock%2A>プロパティ。  
  
> [!NOTE]
>  実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。 設定を変更するには、 **[ツール]** メニューの **[設定のインポートとエクスポート]** をクリックします。 詳細については、「[Visual Studio IDE のカスタマイズ](/visualstudio/ide/personalizing-the-visual-studio-ide)」を参照してください。  
  
### <a name="to-align-and-stretch-a-control"></a>配置して伸縮を制御する  
  
1. <xref:System.Windows.Forms.TableLayoutPanel> ツールボックス **から** コントロールをフォームにドラッグします。  
  
2. ドラッグ、<xref:System.Windows.Forms.Button>コントロールから、**ツールボックス**の左上隅のセルに、<xref:System.Windows.Forms.TableLayoutPanel>コントロール。 <xref:System.Windows.Forms.Button>コントロールがセルの中央に配置します。  
  
3. 値を設定、<xref:System.Windows.Forms.Button>コントロールの<xref:System.Windows.Forms.Control.Anchor%2A>プロパティを`Left,Right`します。 <xref:System.Windows.Forms.Button>端まで拡大に合わせてセルの幅を制御します。  
  
4. 値を設定、<xref:System.Windows.Forms.Button>コントロールの<xref:System.Windows.Forms.Control.Anchor%2A>プロパティを`Top,Bottom`します。 <xref:System.Windows.Forms.Button>端まで拡大に合わせてセルの高さを制御します。  
  
5. 値を設定、<xref:System.Windows.Forms.Button>コントロールの<xref:System.Windows.Forms.Control.Dock%2A>プロパティを<xref:System.Windows.Forms.DockStyle.Fill>します。 <xref:System.Windows.Forms.Button>セル コントロールを拡張します。  
  
6. 値を設定、<xref:System.Windows.Forms.Button>コントロールの<xref:System.Windows.Forms.Control.Dock%2A>プロパティを<xref:System.Windows.Forms.DockStyle.None>します。 <xref:System.Windows.Forms.Button>コントロールは、元のサイズを返し、セルの左上隅に移動します。 **Windows フォーム デザイナー**設定が、<xref:System.Windows.Forms.Control.Anchor%2A>プロパティを`Top, Left`します。  
  
7. 値を設定、<xref:System.Windows.Forms.Button>コントロールの<xref:System.Windows.Forms.Control.Anchor%2A>プロパティを`Bottom,Right`します。 <xref:System.Windows.Forms.Button>コントロールがセルの右下隅に移動します。  
  
8. 値を設定、<xref:System.Windows.Forms.Button>コントロールの<xref:System.Windows.Forms.Control.Anchor%2A>プロパティを<xref:System.Windows.Forms.AnchorStyles.None>します。 <xref:System.Windows.Forms.Button>コントロールがセルの中央に移動します。  
  
## <a name="see-also"></a>関連項目

- [TableLayoutPanel コントロール](tablelayoutpanel-control-windows-forms.md)
