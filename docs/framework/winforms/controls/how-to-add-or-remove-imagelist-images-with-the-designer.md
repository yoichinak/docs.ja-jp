---
title: '方法: デザイナーを使って ImageList イメージを追加または削除する'
ms.date: 03/30/2017
helpviewer_keywords:
- ImageList component [Windows Forms], adding images
- ImageList component [Windows Forms], removing images
- images [Windows Forms], adding to ImageList component
ms.assetid: 5699b244-e37c-4d20-bc35-7441e55c1e3a
ms.openlocfilehash: 63692a797ad49f0adc3a0c5b0bfff1aebbc65257
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69038269"
---
# <a name="how-to-add-or-remove-imagelist-images-with-the-designer"></a>方法: デザイナーを使って ImageList イメージを追加または削除する

<xref:System.Windows.Forms.ImageList>コンポーネントにイメージを追加するには、さまざまな方法があります。 に関連付けられ<xref:System.Windows.Forms.ImageList>たスマートタグを使用すると、イメージをすばやく追加できます。また、 <xref:System.Windows.Forms.ImageList>で他のプロパティをいくつか設定する場合は、プロパティウィンドウで画像を追加する方が便利な場合があります。 コードを使用してイメージを追加することもできます。 コードを使用してイメージを追加する方法の詳細[については、「」を参照してください。Windows フォーム ImageList コンポーネント](how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md)を使用してイメージを追加または削除します。 通常は、コントロール<xref:System.Windows.Forms.ImageList>に関連付けられる前にコンポーネントにイメージを設定しますが、これは必須ではありません。


### <a name="to-add-or-remove-images-by-using-the-properties-window"></a>プロパティウィンドウを使用してイメージを追加または削除するには

1. <xref:System.Windows.Forms.ImageList>コンポーネントを選択するか、フォームに追加します。

2. プロパティウィンドウで、プロパティの![ <xref:System.Windows.Forms.ImageList.Images%2A>横にある省略記号ボタン (Visual](./media/visual-studio-ellipsis-button.png)Studio のプロパティウィンドウの省略記号ボタン (...)) をクリックします。

3. **イメージコレクションエディター**で、 **[追加]** または **[削除]** をクリックして、一覧からイメージを追加または削除します。

### <a name="to-add-or-remove-images-using-the-smart-tag"></a>スマートタグを使用してイメージを追加または削除するには

1. <xref:System.Windows.Forms.ImageList>コンポーネントを選択するか、フォームに追加します。

2. スマートタググリフ (![スマートタググリフ](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) をクリックします。

3. **[ImageList Tasks]** ダイアログボックスで、 **[Images の選択]** を選択します。

4. **イメージコレクションエディター**で、 **[追加]** または **[削除]** をクリックして、一覧からイメージを追加または削除します。

## <a name="see-also"></a>関連項目

- [イメージ、ビットマップ、メタファイル](../advanced/images-bitmaps-and-metafiles.md)
- [チュートリアル: Windows フォームコントロールでのスマートタグを使用した一般的なタスクの実行](performing-common-tasks-using-smart-tags-on-wf-controls.md)
- [ImageList コンポーネント](imagelist-component-windows-forms.md)
