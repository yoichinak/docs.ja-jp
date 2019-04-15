---
title: '方法: デザイナーを使用して Windows フォーム DataGridView コントロールに交互の行のスタイルを設定する'
ms.date: 03/30/2017
helpviewer_keywords:
- ledger-like formats
- DataGridView control [Windows Forms], row style alternation
- Windows Forms, rows
- rows [Windows Forms], alternating
- data [Windows Forms], displaying
ms.assetid: 02373442-bf94-4470-9f8a-e44c4a9d5b88
ms.openlocfilehash: fb338a3616bc20542ec940db5977c4ffdab9654c
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/09/2019
ms.locfileid: "59335629"
---
# <a name="how-to-set-alternating-row-styles-for-the-windows-forms-datagridview-control-using-the-designer"></a>方法: デザイナーを使用して Windows フォーム DataGridView コントロールに交互の行のスタイルを設定する
表形式のデータは多くの場合、別の背景色の交互の行のある帳簿のような形式で表示されます。 この形式を使用すると、多数の列がある幅の広いテーブルで、ユーザーが各行にあるセルを簡単に識別できるようになります。  
  
 <xref:System.Windows.Forms.DataGridView> コントロールを使用すると、1 行おきの完全なスタイル情報を指定できます。 交互の行を区別するために、前景色と背景の色に加えて、フォントなどのスタイル特性を使用できます。 詳細については、次を参照してください。 [Windows フォームの DataGridView コントロールのセル スタイル](cell-styles-in-the-windows-forms-datagridview-control.md)します。  
  
 次の手順が必要です、 **Windows アプリケーション**プロジェクトが含まれているフォームを<xref:System.Windows.Forms.DataGridView>コントロール。 このようなプロジェクトの設定の詳細については、次を参照してください。[方法。Windows フォーム アプリケーション プロジェクトを作成](/visualstudio/ide/step-1-create-a-windows-forms-application-project)と[方法。Windows フォームにコントロールを追加](how-to-add-controls-to-windows-forms.md)します。  
  
> [!NOTE]
>  実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。 設定を変更するには、 **[ツール]** メニューの **[設定のインポートとエクスポート]** をクリックします。 詳細については、「[Visual Studio IDE のカスタマイズ](/visualstudio/ide/personalizing-the-visual-studio-ide)」を参照してください。  
  
### <a name="define-styles-for-alternating-rows"></a>交互の行のスタイルを定義します。  
  
1. 選択、<xref:System.Windows.Forms.DataGridView>デザイナーでコントロールできます。  
  
2. **プロパティ**ウィンドウで、省略記号ボタンをクリックします (![VisualStudioEllipsesButton スクリーン ショット](../media/vbellipsesbutton.png "vbEllipsesButton")) 横に、<xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A>プロパティ。  
  
3. **CellStyle ビルダー**ダイアログ ボックスで、プロパティを設定してスタイルを定義して、**プレビュー**ウィンドウで選択内容を確認します。 以降、2 つ目では、コントロールに表示されるその他のすべての行では、指定したスタイルが使用されます。  
  
4. 残りの行のスタイルを定義するには、手順 2 および 3 を使用して、<xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A>プロパティ。  
  
    > [!NOTE]
    >  セルは、複数のプロパティから継承されたスタイルを使用して表示されます。 スタイルの継承の詳細については、次を参照してください。 [Windows フォームの DataGridView コントロールのセル スタイル](cell-styles-in-the-windows-forms-datagridview-control.md)します。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.DataGridView>
- [Windows フォーム DataGridView コントロールでのセルのスタイル](cell-styles-in-the-windows-forms-datagridview-control.md)
- [Windows フォームの DataGridView コントロールの基本的な書式設定およびスタイル設定](basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)
- [Windows フォーム DataGridView コントロールでのデザイナーの使用](using-the-designer-with-the-windows-forms-datagridview-control.md)
- [方法: Windows フォーム アプリケーション プロジェクトを作成します。](/visualstudio/ide/step-1-create-a-windows-forms-application-project)
- [方法: Windows フォームにコントロールを追加する](how-to-add-controls-to-windows-forms.md)
