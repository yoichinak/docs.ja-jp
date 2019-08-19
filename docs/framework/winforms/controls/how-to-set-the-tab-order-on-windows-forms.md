---
title: '方法: Windows フォーム上のタブ オーダーを設定する'
ms.date: 03/30/2017
f1_keywords:
- TabStop
- TabIndex
helpviewer_keywords:
- tab order [Windows Forms], controls on Windows forms
- Windows Forms controls, setting tab order
- controls [Windows Forms], setting tab order
- Windows Forms, setting tab order
ms.assetid: 71fa8e76-0472-414b-ad3c-0f90166e0ad7
ms.openlocfilehash: 5559a3a3e4e62ce9e620de23feef3cbfa0ab8f60
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69039851"
---
# <a name="how-to-set-the-tab-order-on-windows-forms"></a>方法: Windows フォーム上のタブ オーダーを設定する
タブオーダーは、TAB キーを押すことによって、ユーザーがあるコントロールから別のコントロールにフォーカスを移動する順序です。 各フォームには、独自のタブオーダーがあります。 既定では、タブオーダーは、コントロールを作成した順序と同じです。 タブオーダー番号は0から始まります。

## <a name="to-set-the-tab-order-of-a-control"></a>コントロールのタブオーダーを設定するには

1. **[表示]** メニューの **[タブオーダー]** をクリックします。

     これにより、フォームのタブオーダー選択モードがアクティブになります。 各コントロールの左上隅<xref:System.Windows.Forms.Control.TabIndex%2A>に、(プロパティを表す) 数値が表示されます。

2. コントロールを順番にクリックして、目的のタブオーダーを設定します。

    > [!NOTE]
    >  タブオーダー内のコントロールの位置は、0以上の任意の値に設定できます。 重複が発生すると、2つのコントロールの z オーダーが評価され、上のコントロールが最初にタブになります。 (Z オーダーは、フォームの z 軸の [奥行] に沿ったフォーム上のコントロールの視覚的なレイヤーです。 Z オーダーは、他のコントロールの前にあるコントロールを決定します。)Z オーダーの詳細については、「 [Windows フォームのオブジェクトのレイヤー](how-to-layer-objects-on-windows-forms.md)化」を参照してください。

3. 終了したら、 **[表示]** メニューの **[タブオーダー]** をもう一度クリックして、タブオーダーモードを終了します。

    > [!NOTE]
    >  フォーカスを取得できず、無効になったコントロールや非表示のコントロールでも、 <xref:System.Windows.Forms.Control.TabIndex%2A>プロパティはなく、タブオーダーには含まれません。 ユーザーが TAB キーを押すと、これらのコントロールはスキップされます。

 また、 <xref:System.Windows.Forms.Control.TabIndex%2A>プロパティを使用して、プロパティウィンドウでタブオーダーを設定することもできます。 コントロール<xref:System.Windows.Forms.Control.TabIndex%2A>のプロパティは、タブオーダー内での位置を決定します。 既定では、描画<xref:System.Windows.Forms.Control.TabIndex%2A>された最初のコントロールの値は0、2番目のコントロールのは<xref:System.Windows.Forms.Control.TabIndex%2A> 1、などです。

 また、既定<xref:System.Windows.Forms.GroupBox>では、コントロールには、 <xref:System.Windows.Forms.Control.TabIndex%2A>整数である独自の値があります。 コントロール<xref:System.Windows.Forms.GroupBox>自体には、実行時にフォーカスを設定することはできません。 したがって、内<xref:System.Windows.Forms.GroupBox>の各コントロールには、0から始まる独自の10進<xref:System.Windows.Forms.Control.TabIndex%2A>値があります。 当然ながら、 <xref:System.Windows.Forms.GroupBox>コントロール<xref:System.Windows.Forms.Control.TabIndex%2A>のがインクリメントされると、その中のコントロールがそれに応じてインクリメントされます。 値を<xref:System.Windows.Forms.Control.TabIndex%2A> 5 から6に変更した場合、 <xref:System.Windows.Forms.Control.TabIndex%2A>そのグループの最初のコントロールの値は自動的に6.0 に変更されます。

 最後に、フォーム上の多くのコントロールは、タブオーダーではスキップできます。 通常、実行時に TAB キーを連続して押すと、各コントロールがタブオーダーで選択されます。 <xref:System.Windows.Forms.Control.TabStop%2A>プロパティをオフにすると、フォームのタブオーダーでコントロールを渡すことができます。

## <a name="to-remove-a-control-from-the-tab-order"></a>タブオーダーからコントロールを削除するには

1. プロパティウィンドウで、コントロール<xref:System.Windows.Forms.Control.TabStop%2A>のプロパティ`false`をに設定します。

     Tab キーを<xref:System.Windows.Forms.Control.TabStop%2A>使用してコントロールを`false`巡回するときにコントロールがスキップされる場合でも、プロパティがに設定されているコントロールは、タブオーダーの位置を維持します。

    > [!NOTE]
    >  ラジオボタングループには、実行時に1つのタブストップがあります。 選択した<xref:System.Windows.Forms.RadioButton.Checked%2A>ボタン (プロパティがに`true`設定されているボタン) <xref:System.Windows.Forms.Control.TabStop%2A>では、プロパティが自動的`true`に<xref:System.Windows.Forms.Control.TabStop%2A>に設定され、他のボタンの`false`プロパティはに設定されます。 コントロールのグループ化<xref:System.Windows.Forms.RadioButton>の詳細については、「 [Set Windows フォーム RadioButton コントロールをセットとして機能させる](how-to-group-windows-forms-radiobutton-controls-to-function-as-a-set.md)」を参照してください。

## <a name="see-also"></a>関連項目

- [Windows フォーム コントロール](index.md)
- [Windows フォームでのコントロールの配置](arranging-controls-on-windows-forms.md)
- [Windows フォームで使用するコントロール](controls-to-use-on-windows-forms.md)
- [Windows フォーム コントロールの機能別一覧](windows-forms-controls-by-function.md)
