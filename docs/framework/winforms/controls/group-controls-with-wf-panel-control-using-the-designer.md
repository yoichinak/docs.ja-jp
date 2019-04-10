---
title: '方法: デザイナーを使用して Windows フォーム Panel コントロールでコントロールをグループ化する'
ms.date: 03/30/2017
helpviewer_keywords:
- Panel control [Windows Forms], grouping controls
- controls [Windows Forms], grouping
- Windows Forms controls, grouping
ms.assetid: 7e1cd708-fdb1-49d8-9ca2-5640b276bf2e
ms.openlocfilehash: 662343af42f72816a5a673d2cd6d839a5dca9190
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/09/2019
ms.locfileid: "59341401"
---
# <a name="how-to-group-controls-with-the-windows-forms-panel-control-using-the-designer"></a>方法: デザイナーを使用して Windows フォーム Panel コントロールでコントロールをグループ化する
Windows フォーム<xref:System.Windows.Forms.Panel>コントロールを使用すると、その他のコントロールをグループ化します。 コントロールをグループ化の 3 つの理由があります。 視覚的にわかりやすいユーザー インターフェイスです。 関連するフォーム要素のグループ化もう 1 つは、プログラムによるグループ化、ラジオ ボタンの例です。最後には、単位としてデザイン時にコントロールを移動するためです。  
  
> [!NOTE]
>  実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。 設定を変更するには、 **[ツール]** メニューの **[設定のインポートとエクスポート]** をクリックします。 詳細については、「[Visual Studio IDE のカスタマイズ](/visualstudio/ide/personalizing-the-visual-studio-ide)」を参照してください。  
  
### <a name="to-create-a-group-of-controls"></a>コントロールのグループを作成するには  
  
1. ドラッグ、<xref:System.Windows.Forms.Panel>コントロールから、 **Windows フォーム**フォームには、ツールボックスのタブ。  
  
2. その他のコントロール、パネル、パネル内の各描画を追加します。  
  
     既存のコントロール パネルにする場合は、すべてのコントロールを選択する、選択、クリップボードに切り取ります、<xref:System.Windows.Forms.Panel>を制御して、パネルに貼り付けます。 パネルにもドラッグできます。  
  
3. (省略可能)パネルに罫線を追加する場合は、設定、<xref:System.Windows.Forms.BorderStyle>プロパティ。 次の 3 つの選択肢があります: <xref:System.Windows.Forms.BorderStyle.Fixed3D>、 <xref:System.Windows.Forms.BorderStyle.FixedSingle>、および<xref:System.Windows.Forms.BorderStyle.None>します。  
  
## <a name="see-also"></a>関連項目

- [Panel コントロール](panel-control-windows-forms.md)
- [Panel コントロールの概要](panel-control-overview-windows-forms.md)
- [方法: パネルの背景を設定する](how-to-set-the-background-of-a-windows-forms-panel.md)
