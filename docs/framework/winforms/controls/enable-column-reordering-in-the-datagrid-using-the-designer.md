---
title: '方法: デザイナーを使用して Windows フォーム DataGridView コントロールの列の並べ替えを有効にする'
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], column order
- Windows Forms, columns
- columns [Windows Forms], reordering
- data [Windows Forms], displaying
ms.assetid: d82bd69c-6799-4439-a32c-91139c5901d1
ms.openlocfilehash: 4ccd9d0be702289386b6b817da781e255787fffe
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2019
ms.locfileid: "64614770"
---
# <a name="how-to-enable-column-reordering-in-the-windows-forms-datagridview-control-using-the-designer"></a>方法: デザイナーを使用して Windows フォーム DataGridView コントロールの列の並べ替えを有効にする
Windows フォームに表示されるデータを表示するときに<xref:System.Windows.Forms.DataGridView>コントロール、ユーザーことがありますする特定の列の値を比較します。 これは、できますしない列は、コントロールでは、広く区切られている場合に便利な特にで関心のあるすべての列を表示するには、ユーザーが前後へ水平方向にスクロールする必要があります。 列の順序を変更できるので、列の値を容易に比較を行うことができます。 列の並べ替えを有効にすると、ユーザーは、マウスで列ヘッダーをドラッグして列を新しい位置に移動できます。  
  
 次の手順が必要です、 **Windows アプリケーション**プロジェクトが含まれているフォームを<xref:System.Windows.Forms.DataGridView>コントロール。 このようなプロジェクトの設定の詳細については、次を参照してください。[方法。Windows フォーム アプリケーション プロジェクトを作成](/visualstudio/ide/step-1-create-a-windows-forms-application-project)と[方法。Windows フォームにコントロールを追加](how-to-add-controls-to-windows-forms.md)します。  
  
> [!NOTE]
>  実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。 設定を変更するには、 **[ツール]** メニューの **[設定のインポートとエクスポート]** をクリックします。 詳細については、「[Visual Studio IDE のカスタマイズ](/visualstudio/ide/personalizing-the-visual-studio-ide)」を参照してください。  
  
### <a name="to-enable-column-reordering"></a>列の並べ替えを有効にするには  
  
- スマート タグ グリフをクリックします (![スマート タグ グリフ](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) の右上隅で、 <xref:System.Windows.Forms.DataGridView> 、制御し、**列の並べ替えを有効にする**.  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.AllowUserToOrderColumns%2A?displayProperty=nameWithType>
- [方法: デザイナーを使用して Windows フォーム DataGridView コントロールで列を固定します。](freeze-columns-in-the-datagrid-using-the-designer.md)
- [方法: Windows フォーム アプリケーション プロジェクトの作成](/visualstudio/ide/step-1-create-a-windows-forms-application-project)
- [方法: Windows フォームにコントロールを追加します。](how-to-add-controls-to-windows-forms.md)
