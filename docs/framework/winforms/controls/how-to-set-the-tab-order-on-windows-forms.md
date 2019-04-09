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
ms.openlocfilehash: cd86757d43d7d57dc7777422086a7b7a96b6611e
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59162125"
---
# <a name="how-to-set-the-tab-order-on-windows-forms"></a>方法: Windows フォーム上のタブ オーダーを設定する
タブ オーダーは、ユーザーが TAB キーを押して 1 つのコントロールからでフォーカスを移動する順序です。 各フォームには、独自のタブ オーダーがあります。 既定では、タブ オーダーは、コントロールを作成した順序と同じです。 タブ オーダーの番号は 0 から始まります。  
  
> [!NOTE]
>  実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。 設定を変更するには、 **[ツール]** メニューの **[設定のインポートとエクスポート]** をクリックします。 詳細については、「[Visual Studio IDE のカスタマイズ](/visualstudio/ide/personalizing-the-visual-studio-ide)」を参照してください。  
  
### <a name="to-set-the-tab-order-of-a-control"></a>コントロールのタブ オーダーを設定するには  
  
1.  **ビュー**  メニューのをクリックして**タブ オーダー**します。  
  
     これには、フォームのタブ オーダー選択モードがアクティブにします。 数値 (を表す、<xref:System.Windows.Forms.Control.TabIndex%2A>プロパティ) の各コントロールの左上隅に表示されます。  
  
2.  タブの順序を確立するために順番にコントロールをクリックします。  
  
    > [!NOTE]
    >  タブ オーダーのコントロールの位置は 0 以上、任意の値に設定できます。 重複が発生して、2 つのコントロールの z オーダーが評価され、上位のコントロールが最初にタブ付き。 (Z オーダーは、フォームの z 軸 [奥行] に沿ってフォーム上のコントロールのビジュアル レイヤー。 Z オーダーを決定するコントロールは、他のコントロールの前にします。)Z オーダーの詳細については、次を参照してください。 [Windows フォーム上のオブジェクトの階層構造](how-to-layer-objects-on-windows-forms.md)します。  
  
3.  完了したら、クリックして**タブ オーダー**上、**ビュー**タブ オーダー モードを終了するには、もう一度メニュー。  
  
    > [!NOTE]
    >  無効になっており、非表示のコントロールと、フォーカスを取得できませんコントロールがない、<xref:System.Windows.Forms.Control.TabIndex%2A>プロパティとは、タブ オーダーに含まれません。 ユーザーは、TAB キーを押すと、これらのコントロールはスキップされます。  
  
 プロパティ ウィンドウを使用してタブ オーダーを設定する代わりに、<xref:System.Windows.Forms.Control.TabIndex%2A>プロパティ。 <xref:System.Windows.Forms.Control.TabIndex%2A>タブ オーダーの位置は、コントロールのプロパティを決定します。 既定では、最初のコントロールが描画されるが、<xref:System.Windows.Forms.Control.TabIndex%2A>値 0、2 番目に、 <xref:System.Windows.Forms.Control.TabIndex%2A> 1 の。  
  
 さらに、既定を<xref:System.Windows.Forms.GroupBox>コントロールがある独自<xref:System.Windows.Forms.Control.TabIndex%2A>整数の値。 A<xref:System.Windows.Forms.GroupBox>コントロール自体は実行時にフォーカスを持つことはできません。 内の各コントロール、そのため、<xref:System.Windows.Forms.GroupBox>が独自の 10 進数<xref:System.Windows.Forms.Control.TabIndex%2A>.0 から始まる値。 当然ながら、として、<xref:System.Windows.Forms.Control.TabIndex%2A>の<xref:System.Windows.Forms.GroupBox>コントロールがインクリメントされます、内のコントロールが適宜インクリメントされます。 変更した場合、 <xref:System.Windows.Forms.Control.TabIndex%2A> 5 から 6 までの値、 <xref:System.Windows.Forms.Control.TabIndex%2A> 6.0 では、という具合に、グループ内の最初のコントロールの値が自動的に変更します。  
  
 最後に、フォーム上の多数の任意のコントロールは、タブ オーダー内でスキップできます。 通常は、TAB キーを押して連続して実行時の選択タブ オーダー内の各コントロール。 無効にして、<xref:System.Windows.Forms.Control.TabStop%2A>プロパティ、経由で、フォームのタブ オーダー内で渡されるコントロールを行うことができます。  
  
#### <a name="to-remove-a-control-from-the-tab-order"></a>タブ オーダーのコントロールを削除するには  
  
1.  コントロールの設定<xref:System.Windows.Forms.Control.TabStop%2A>プロパティを`false`プロパティ ウィンドウでします。  
  
     いる A コントロール<xref:System.Windows.Forms.Control.TabStop%2A>プロパティに設定された`false`コントロールをスキップして、TAB キーでコントロールを循環する場合でも、タブ オーダー内の位置を維持します。  
  
    > [!NOTE]
    >  ラジオ ボタン グループには、実行時に停止する 1 つのタブがあります。 選択したボタン (ボタンは、その<xref:System.Windows.Forms.RadioButton.Checked%2A>プロパティに設定`true`) がその<xref:System.Windows.Forms.Control.TabStop%2A>プロパティが自動的に設定`true`他のボタンがありますが、その<xref:System.Windows.Forms.Control.TabStop%2A>プロパティに設定`false`します。 グループ化の詳細については<xref:System.Windows.Forms.RadioButton>コントロールを参照してください[セットとして機能する Windows フォーム RadioButton コントロールをグループ化](how-to-group-windows-forms-radiobutton-controls-to-function-as-a-set.md)します。  
  
## <a name="see-also"></a>関連項目

- [Windows フォーム コントロール](index.md)
- [Windows フォームでのコントロールの配置](arranging-controls-on-windows-forms.md)
- [Windows フォームで使用するコントロール](controls-to-use-on-windows-forms.md)
- [Windows フォーム コントロールの機能別一覧](windows-forms-controls-by-function.md)
