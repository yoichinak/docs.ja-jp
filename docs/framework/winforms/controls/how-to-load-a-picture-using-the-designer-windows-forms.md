---
title: '方法: デザイナーを使用して画像を読み込む (Windows フォーム)'
ms.date: 03/30/2017
helpviewer_keywords:
- picture formats
- images [Windows Forms], displaying on Windows Forms
- pictures [Windows Forms], displaying
- forms [Windows Forms], displaying images
- PictureBox control [Windows Forms], adding pictures
ms.assetid: 4dc7b973-afb1-4276-8322-20825af96655
ms.openlocfilehash: 1d95d5baafa42c7dea40933ba837b684d90b7b2b
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/13/2019
ms.locfileid: "68972372"
---
# <a name="how-to-load-a-picture-using-the-designer-windows-forms"></a>方法: デザイナーを使用して画像を読み込む (Windows フォーム)

Windows フォーム<xref:System.Windows.Forms.PictureBox>コントロールを使用すると、プロパティを<xref:System.Windows.Forms.PictureBox.Image%2A>有効な画像に設定することによって、デザイン時にフォームの画像を読み込んで表示することができます。 次の表に、許容されるファイルの種類を示します。

|種類|ファイル名の拡張子|
|----------|-------------------------|
|ビットマップ|.bmp|
|アイコン|.ico|
|GIF|.gif|
|ピクチャ|.wmf|
|JPEG|.jpg|

> [!NOTE]
>  実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。 設定を変更するには、 **[ツール]** メニューの **[設定のインポートとエクスポート]** をクリックします。 詳細については、「[Visual Studio IDE のカスタマイズ](/visualstudio/ide/personalizing-the-visual-studio-ide)」を参照してください。

## <a name="to-display-a-picture-at-design-time"></a>デザイン時に画像を表示するには

1. フォーム上<xref:System.Windows.Forms.PictureBox>にコントロールを描画します。

2. プロパティウィンドウで、 <xref:System.Windows.Forms.PictureBox.Image%2A>プロパティを選択し、省略記号ボタンをクリックして **開く** ダイアログボックスを表示します。

3. 特定のファイルの種類 (.gif ファイルなど) を探している場合は、 **[ファイルの種類]** ボックスでそれを選択します。

4. 表示するファイルを選択します。

## <a name="to-clear-the-picture-at-design-time"></a>デザイン時に画像をクリアするには

1. **[プロパティ]** ウィンドウで、 <xref:System.Windows.Forms.PictureBox.Image%2A>プロパティを選択し、イメージオブジェクトの名前の左側に表示される小さいサムネイル画像を右クリックします。 **[リセット]** を選択します。

## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.PictureBox>
- [PictureBox コントロールの概要](picturebox-control-overview-windows-forms.md)
- [方法: 実行時に画像のサイズまたは配置を変更する](how-to-modify-the-size-or-placement-of-a-picture-at-run-time-windows-forms.md)
- [方法: 実行時に画像を設定する](how-to-set-pictures-at-run-time-windows-forms.md)
- [PictureBox コントロール](picturebox-control-windows-forms.md)
