---
title: '方法: MenuStrip にオプションボタンを表示する (Windows フォーム)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- MenuStrip [Windows Forms], displaying option buttons
- displaying option buttons [Windows Forms], MenuStrip [Windows Forms]
- option buttons [Windows Forms], displaying in MenuStrip
ms.assetid: 8b596af2-9ff8-4f7b-93d7-cba830e167f4
ms.openlocfilehash: 94d683369edd6583ad8b01c2ce3f393567a5ed75
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/13/2019
ms.locfileid: "68971933"
---
# <a name="how-to-display-option-buttons-in-a-menustrip-windows-forms"></a>方法: MenuStrip にオプションボタンを表示する (Windows フォーム)

オプションボタンは、オプションボタンとも呼ばれ、ユーザーが一度に1つだけ選択できる点を除いて、チェックボックスに似ています。 既定では、 <xref:System.Windows.Forms.ToolStripMenuItem>クラスにはオプションボタンの動作が用意されていませんが、クラスには、 <xref:System.Windows.Forms.MenuStrip>コントロールのメニュー項目に対してオプションボタンの動作を実装するようにカスタマイズできるチェックボックスの動作が用意されています。

メニュー項目の`true`プロパティがの場合、ユーザーは項目をクリックしてチェックマークの表示を切り替えることができます。 <xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A> プロパティ<xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A>は、項目の現在の状態を示します。 基本的なオプションボタンの動作を実装するには、項目が選択されているときに<xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A> 、前に選択した項目`false`のプロパティをに設定する必要があります。

次の手順では、 <xref:System.Windows.Forms.ToolStripMenuItem>クラスを継承するクラスにこの機能と追加の機能を実装する方法について説明します。 クラス`ToolStripRadioButtonMenuItem`は、 <xref:System.Windows.Forms.ToolStripMenuItem.OnCheckedChanged%2A> や<xref:System.Windows.Forms.ToolStripMenuItem.OnPaint%2A>などのメンバーをオーバーライドして、オプションボタンの選択動作と外観を提供します。 また、このクラスは、 <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A>親項目が選択されていない場合にサブメニューのオプションが無効になるように、プロパティをオーバーライドします。

## <a name="to-implement-option-button-selection-behavior"></a>オプションボタンの選択動作を実装するには

1. 項目の<xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A>選択を`true`有効にするには、プロパティをに初期化します。

     [!code-csharp[ToolStripRadioButtonMenuItem#110](~/samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#110)]
     [!code-vb[ToolStripRadioButtonMenuItem#110](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#110)]

2. 新しい項目<xref:System.Windows.Forms.ToolStripMenuItem.OnCheckedChanged%2A>を選択したときに、前に選択した項目の選択を解除するには、メソッドをオーバーライドします。

     [!code-csharp[ToolStripRadioButtonMenuItem#120](~/samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#120)]
     [!code-vb[ToolStripRadioButtonMenuItem#120](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#120)]

3. <xref:System.Windows.Forms.ToolStripMenuItem.OnClick%2A>メソッドをオーバーライドして、既に選択されている項目をクリックしても選択内容がクリアされないようにします。

     [!code-csharp[ToolStripRadioButtonMenuItem#130](~/samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#130)]
     [!code-vb[ToolStripRadioButtonMenuItem#130](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#130)]

## <a name="to-modify-the-appearance-of-the-option-button-items"></a>オプションボタンの項目の外観を変更するには

1. クラスを使用して、既定のチェックマークをオプションボタンに置き換えるには、メソッドを<xref:System.Windows.Forms.ToolStripMenuItem.OnPaint%2A>オーバーライドします。 <xref:System.Windows.Forms.RadioButtonRenderer>

     [!code-csharp[ToolStripRadioButtonMenuItem#140](~/samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#140)]
     [!code-vb[ToolStripRadioButtonMenuItem#140](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#140)]

2. <xref:System.Windows.Forms.ToolStripMenuItem.OnMouseEnter%2A> <xref:System.Windows.Forms.ToolStripMenuItem.OnPaint%2A> 、、、および<xref:System.Windows.Forms.ToolStripMenuItem.OnMouseUp%2A>の各メソッドをオーバーライドしてマウスの状態を追跡し、メソッドが適切なオプションボタンの状態を描画するようにします。 <xref:System.Windows.Forms.ToolStripMenuItem.OnMouseDown%2A> <xref:System.Windows.Forms.ToolStripMenuItem.OnMouseLeave%2A>

     [!code-csharp[ToolStripRadioButtonMenuItem#150](~/samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#150)]
     [!code-vb[ToolStripRadioButtonMenuItem#150](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#150)]

## <a name="to-disable-options-on-a-submenu-when-the-parent-item-is-not-selected"></a>親項目が選択されていないときにサブメニューのオプションを無効にするには

1. <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A> <xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A> の<xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A>値と値の両方を持つ親項目がある場合に、項目が無効になるように、プロパティをオーバーライドします。`false` `true`

     [!code-csharp[ToolStripRadioButtonMenuItem#160](~/samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#160)]
     [!code-vb[ToolStripRadioButtonMenuItem#160](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#160)]

2. 親アイテム<xref:System.Windows.Forms.ToolStripMenuItem.OnOwnerChanged%2A>の<xref:System.Windows.Forms.ToolStripMenuItem.CheckedChanged>イベントをサブスクライブするには、メソッドをオーバーライドします。

     [!code-csharp[ToolStripRadioButtonMenuItem#170](~/samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#170)]
     [!code-vb[ToolStripRadioButtonMenuItem#170](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#170)]

3. 親項目<xref:System.Windows.Forms.ToolStripMenuItem.CheckedChanged>のイベントのハンドラーで、項目を無効にして、新しい有効な状態で表示を更新します。

     [!code-csharp[ToolStripRadioButtonMenuItem#180](~/samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#180)]
     [!code-vb[ToolStripRadioButtonMenuItem#180](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#180)]

## <a name="example"></a>例

次のコード例では、 `ToolStripRadioButtonMenuItem`完全なクラス<xref:System.Windows.Forms.Form>と、オプション`Program`ボタンの動作を示すクラスとクラスを提供しています。

[!code-csharp[ToolStripRadioButtonMenuItem#000](~/samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#000)]
[!code-vb[ToolStripRadioButtonMenuItem#000](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#000)]

## <a name="compiling-the-code"></a>コードのコンパイル

この例で必要な要素は次のとおりです。

- System、System.Drawing、および System.Windows.Forms の各アセンブリへの参照。

## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStripMenuItem>
- <xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ToolStripMenuItem.OnCheckedChanged%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ToolStripMenuItem.OnPaint%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.RadioButtonRenderer>
- [MenuStrip コントロール](menustrip-control-windows-forms.md)
- [方法: カスタム ToolStripRenderer を実装する](how-to-implement-a-custom-toolstriprenderer.md)
