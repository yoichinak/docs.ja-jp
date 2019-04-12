---
title: '方法: デザイナー (Windows フォーム) を使用してピクチャを読み込む.'
ms.date: 03/30/2017
helpviewer_keywords:
- picture formats
- images [Windows Forms], displaying on Windows Forms
- pictures [Windows Forms], displaying
- forms [Windows Forms], displaying images
- PictureBox control [Windows Forms], adding pictures
ms.assetid: 4dc7b973-afb1-4276-8322-20825af96655
ms.openlocfilehash: 6bdf7c3df0ffd97dd88a4c442a8a73593a0447ee
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/09/2019
ms.locfileid: "59336383"
---
# <a name="how-to-load-a-picture-using-the-designer-windows-forms"></a>方法: デザイナー (Windows フォーム) を使用してピクチャを読み込む.
Windows フォームで<xref:System.Windows.Forms.PictureBox>コントロール、読み込みし、設定して、デザイン時にフォームに画像を表示できます、<xref:System.Windows.Forms.PictureBox.Image%2A>に有効な画像のプロパティ。 次の表では、許容されるファイルの種類を示します。  
  
|型|ファイル名の拡張子|  
|----------|-------------------------|  
|ビットマップ|.bmp|  
|アイコン|.ico|  
|GIF|.gif|  
|メタファイル|.wmf|  
|JPEG|.jpg|  
  
> [!NOTE]
>  実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。 設定を変更するには、 **[ツール]** メニューの **[設定のインポートとエクスポート]** をクリックします。 詳細については、「[Visual Studio IDE のカスタマイズ](/visualstudio/ide/personalizing-the-visual-studio-ide)」を参照してください。  
  
### <a name="to-display-a-picture-at-design-time"></a>デザイン時に画像を表示するには  
  
1. 描画を<xref:System.Windows.Forms.PictureBox>フォーム上のコントロール。  
  
2. プロパティ ウィンドウで、選択、<xref:System.Windows.Forms.PictureBox.Image%2A>プロパティ、省略記号を表示するボタンをクリックし、**オープン** ダイアログ ボックス。  
  
3. 特定のファイルの種類 (たとえば、.gif ファイル) を探している場合にそれを選択します。、**ファイルの種類**ボックス。  
  
4. 表示するファイルを選択します。  
  
### <a name="to-clear-the-picture-at-design-time"></a>デザイン時に、画像を消去するには  
  
1. **プロパティ**ウィンドウで、<xref:System.Windows.Forms.PictureBox.Image%2A>プロパティと、イメージ オブジェクトの名前の左側に表示される小さなのサムネイル画像を右クリックします。 選択**リセット**します。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.PictureBox>
- [PictureBox コントロールの概要 (Windows フォーム)](picturebox-control-overview-windows-forms.md)
- [方法: 実行時にピクチャのサイズまたは配置を変更する](how-to-modify-the-size-or-placement-of-a-picture-at-run-time-windows-forms.md)
- [方法: 実行時にピクチャを設定する](how-to-set-pictures-at-run-time-windows-forms.md)
- [PictureBox コントロール](picturebox-control-windows-forms.md)
