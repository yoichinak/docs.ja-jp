---
title: TableLayoutPanel コントロールにおける AutoSize 動作
ms.date: 03/30/2017
helpviewer_keywords:
- AutoSize property [Windows Forms], tableLayoutPanel control
- controls [Windows Forms], sizing
- localizing forms
- layout [Windows Forms], AutoSize
- sizing [Windows Forms], automatic
- TableLayoutPanel control [Windows Forms], AutoSize behavior
- automatic sizing
- AutoSizeMode property
ms.assetid: 9233e0c3-2fa6-405e-8701-959479b1250e
ms.openlocfilehash: 466edeee5f45ec72ef265ef4855049c7852641b0
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59164971"
---
# <a name="autosize-behavior-in-the-tablelayoutpanel-control"></a>TableLayoutPanel コントロールにおける AutoSize 動作
## <a name="distinct-autosize-behaviors"></a>個別の AutoSize 動作  
 <xref:System.Windows.Forms.TableLayoutPanel>コントロールは、次の方法での自動サイズ変更動作をサポートしています。  
  
-   を通じて、<xref:System.Windows.Forms.Control.AutoSize%2A>プロパティです。  
  
-   を通じて、<xref:System.Windows.Forms.TableLayoutStyle.SizeType%2A>プロパティを<xref:System.Windows.Forms.TableLayoutPanel>コントロールの列と行のスタイル。  
  
### <a name="the-autosize-property-with-row-and-column-styles"></a>行および列のスタイルと AutoSize プロパティ  
 次の表に、間の相互作用、<xref:System.Windows.Forms.Control.AutoSize%2A>プロパティおよび<xref:System.Windows.Forms.TableLayoutPanel>コントロールの列と行のスタイル。  
  
|自動サイズ調整の設定|スタイルの相互作用|  
|----------------------|-----------------------|  
|`false`|<xref:System.Windows.Forms.TableLayoutPanel>コントロールは左から右に開始され、または次の順序で列または行の領域を割り当てます。<br /><br /> 1.場合、<xref:System.Windows.Forms.TableLayoutStyle.SizeType%2A>プロパティに設定されて<xref:System.Windows.Forms.SizeType.Absolute>で指定されたピクセル数<xref:System.Windows.Forms.ColumnStyle.Width%2A>または<xref:System.Windows.Forms.RowStyle.Height%2A>が割り当てられます。<br />2.場合、<xref:System.Windows.Forms.TableLayoutStyle.SizeType%2A>プロパティに設定されて<xref:System.Windows.Forms.SizeType.AutoSize>、子コントロールのによって返されるピクセル数<xref:System.Windows.Forms.Control.GetPreferredSize%2A>メソッドが割り当てられます。<br />3.すべてのスペース後<xref:System.Windows.Forms.SizeType.Absolute>と<xref:System.Windows.Forms.SizeType.AutoSize>列または行は、割り当て済みの行または列<xref:System.Windows.Forms.TableLayoutStyle.SizeType%2A>設定<xref:System.Windows.Forms.SizeType.Percent>比例して残りの空き領域を割り当てに使用されます|  
|`true`|例外と、前の対話のようなを<xref:System.Windows.Forms.SizeType.Percent>列または行の自動サイズ変更アスペクトを取得します。<br /><br /> <xref:System.Windows.Forms.TableLayoutPanel>コントロールは、十分な空き領域を作成する行または列を拡張できるようにない列または行を<xref:System.Windows.Forms.SizeType.Percent>スタイルは、その内容をクリップします。 <xref:System.Windows.Forms.TableLayoutPanel>コントロールが比例的による新しい領域を割り当て、<xref:System.Windows.Forms.ColumnStyle.Width%2A>または<xref:System.Windows.Forms.RowStyle.Height%2A>プロパティ。|  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.TableLayoutPanel>
- [TableLayoutPanel コントロールの概要](tablelayoutpanel-control-overview.md)
