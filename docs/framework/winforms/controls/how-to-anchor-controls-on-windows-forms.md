---
title: '方法: Windows フォームにコントロールを固定する'
ms.date: 03/30/2017
helpviewer_keywords:
- Anchor property [Windows Forms], enabling resizable forms
- Windows Forms controls, screen resolutions
- resizing forms [Windows Forms]
- Windows Forms controls, size
- screen resolution and control display
- controls [Windows Forms], anchoring
- forms [Windows Forms], resizing
- Windows Forms, resizing
- controls [Windows Forms], positioning
ms.assetid: 59ea914f-fbd3-427a-80fe-decd02f7ae6d
ms.openlocfilehash: b5550aef220ece09d5486421275b19a37bfe9011
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59329779"
---
# <a name="how-to-anchor-controls-on-windows-forms"></a>方法: Windows フォームにコントロールを固定する
ユーザーが実行時にフォームをデザインする場合、フォーム上のコントロールをサイズを変更し、正しくの位置を変更します。 動的フォームにコントロールのサイズを変更するには、使用することができます、 <xref:System.Windows.Forms.Control.Anchor%2A> Windows フォーム コントロールのプロパティ。 <xref:System.Windows.Forms.Control.Anchor%2A>プロパティ、コントロールのアンカーの位置を定義します。 フォームにコントロールを固定すると、フォームのサイズが、コントロールは、コントロールとアンカー位置の間の距離を保持します。 ある場合など、<xref:System.Windows.Forms.TextBox>ようにフォームのサイズが、左、右、およびフォームの下端に固定されているコントロール、<xref:System.Windows.Forms.TextBox>フォームの右辺と左辺からの距離が維持されるため、水平方向にサイズ変更を制御します。 さらに、コントロール配置自体垂直方向にその場所は、フォームの下端から同じ距離では常にできるようにします。 コントロールが固定されていないと、フォームのサイズが、フォームの端を基準としたコントロールの位置が変更されました。  
  
 <xref:System.Windows.Forms.Control.Anchor%2A>プロパティの対話、<xref:System.Windows.Forms.Control.AutoSize%2A>プロパティ。 詳細については、次を参照してください。 [AutoSize プロパティの概要](autosize-property-overview.md)します。  
  
> [!NOTE]
>  実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。 設定を変更するには、 **[ツール]** メニューの **[設定のインポートとエクスポート]** をクリックします。 詳細については、「[Visual Studio IDE のカスタマイズ](/visualstudio/ide/personalizing-the-visual-studio-ide)」を参照してください。  
  
### <a name="to-anchor-a-control-on-a-form"></a>フォームのコントロールを固定するには  
  
1. 固定するコントロールを選択します。  
  
    > [!NOTE]
    >  CTRL キーを押しを選択し、各コントロールをクリックし、この手順の残りの部分で同時に複数のコントロールを固定できます。  
  
2. **プロパティ** ウィンドウの右矢印をクリックして、<xref:System.Windows.Forms.Control.Anchor%2A>プロパティ。  
  
     クロス エディターが表示されます。  
  
3. アンカーを設定するには、上、左、右、またはクロスの下部のセクションをクリックします。  
  
     コントロールでは、上部に固定し、既定のまま。  
  
4. 固定されているコントロールの辺をクリアするには、その arm クロスをクリックします。  
  
5. 閉じるには、<xref:System.Windows.Forms.Control.Anchor%2A>プロパティ エディターでは、クリックして、<xref:System.Windows.Forms.Control.Anchor%2A>プロパティ名をもう一度です。  
  
 実行時にフォームが表示されたら、フォームの端からの距離を保持するコントロールのサイズを変更します。 アンカーの端からの距離の距離では、Windows フォーム デザイナーでコントロールを配置するときに定義されているように同じが常にです。  
  
> [!NOTE]
>  などの特定のコントロール、<xref:System.Windows.Forms.ComboBox>コントロールを高さが制限があります。 フォームまたはコンテナーの下にコントロールを固定すると、その高さの制限を超えるコントロールが強制はできません。  
  
 継承されたコントロールである必要があります`Protected`固定できるようにします。 コントロールのアクセス レベルを変更するには、次のように設定します。 その`Modifiers`プロパティ、**プロパティ**ウィンドウ。  
  
## <a name="see-also"></a>関連項目

- [Windows フォーム コントロール](index.md)
- [Windows フォームでのコントロールの配置](arranging-controls-on-windows-forms.md)
- [AutoSize プロパティの概要](autosize-property-overview.md)
- [方法: Windows フォーム上のコントロールをドッキングします。](how-to-dock-controls-on-windows-forms.md)
- [チュートリアル: FlowLayoutPanel を使用して Windows フォーム コントロールの配置](walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)
- [チュートリアル: TableLayoutPanel を使用して Windows フォーム コントロールの配置](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)
- [チュートリアル: Windows フォーム コントロール Padding、Margin、および AutoSize プロパティをレイアウト](windows-forms-controls-padding-autosize.md)
