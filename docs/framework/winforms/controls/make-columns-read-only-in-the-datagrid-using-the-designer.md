---
title: '方法: 読み取り専用デザイナーを使用して Windows フォーム DataGridView コントロールで列を作成します。'
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, columns
- DataGridView control [Windows Forms], read-only columns
- data [Windows Forms], displaying
- columns [Windows Forms], read-only
ms.assetid: b4ef7a75-ab33-4ee3-b2cf-201530e454e9
ms.openlocfilehash: 0219f0cf50d9cce630dc44a37dd3c16d26874012
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/09/2019
ms.locfileid: "57718559"
---
# <a name="how-to-make-columns-read-only-in-the-windows-forms-datagridview-control-using-the-designer"></a>方法: 読み取り専用デザイナーを使用して Windows フォーム DataGridView コントロールで列を作成します。
ユーザーが既定では、テキストと Windows フォームに表示される数値のデータ変更できる<xref:System.Windows.Forms.DataGridView>コントロール。 変更できないデータを表示する場合は、読み取り専用データを含む列を行う必要があります。 完全に読み取り専用コントロールを作成する方法については、次を参照してください。[方法。行の追加を回避し、削除を Windows フォーム DataGridView コントロールのデザイナーを使用して](prevent-row-addition-and-deletion-in-the-datagrid-using-the-designer.md)します。  
  
 次の手順が必要です、 **Windows アプリケーション**プロジェクトが含まれているフォームを<xref:System.Windows.Forms.DataGridView>コントロール。 このようなプロジェクトの設定の詳細については、次を参照してください。[方法。Windows フォーム アプリケーション プロジェクトを作成](/visualstudio/ide/step-1-create-a-windows-forms-application-project)と[方法。Windows フォームにコントロールを追加](how-to-add-controls-to-windows-forms.md)します。  
  
> [!NOTE]
>  実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。 設定を変更するには、 **[ツール]** メニューの **[設定のインポートとエクスポート]** をクリックします。 詳細については、「[Visual Studio IDE のカスタマイズ](/visualstudio/ide/personalizing-the-visual-studio-ide)」を参照してください。  
  
### <a name="to-make-a-column-read-only-by-using-the-designer"></a>デザイナーを使用して、列を読み取り専用にする  
  
1.  スマート タグ グリフをクリックします (![スマート タグ グリフ](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) の右上隅で、 <xref:System.Windows.Forms.DataGridView> 、制御し、**列の編集**します。  
  
2.  列を選択、**選択した列**一覧。  
  
3.  **列プロパティ**グリッドで、設定、<xref:System.Windows.Forms.DataGridViewColumn.ReadOnly%2A>プロパティを`true`します。  
  
    > [!NOTE]
    >  行うことができますも列を読み取り専用を選択して追加すると、**読み取り専用** チェック ボックス、**列の追加** ダイアログ ボックス。  
  
## <a name="see-also"></a>関連項目
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewColumn.ReadOnly%2A?displayProperty=nameWithType>
- [方法: 追加して、デザイナーを使用して Windows フォーム DataGridView コントロールで列を削除](add-and-remove-columns-in-the-datagrid-using-the-designer.md)
- [方法: デザイナーを使用して Windows フォーム DataGridView コントロールで行の追加および削除を防ぐ](prevent-row-addition-and-deletion-in-the-datagrid-using-the-designer.md)
- [方法: Windows フォーム アプリケーション プロジェクトの作成](/visualstudio/ide/step-1-create-a-windows-forms-application-project)
- [方法: Windows フォームにコントロールを追加します。](how-to-add-controls-to-windows-forms.md)
