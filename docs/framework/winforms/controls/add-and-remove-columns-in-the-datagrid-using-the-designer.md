---
title: '方法: デザイナーを使用して Windows フォーム DataGridView コントロールの列を追加および削除する'
ms.date: 03/30/2017
f1_keywords:
- vs.DataGridViewAddColumnDialog
helpviewer_keywords:
- DataGridView control [Windows Forms], adding columns
- DataGridView control [Windows Forms], removing columns
ms.assetid: 9e709f35-0a8c-4e7e-b4c4-bacb7a834077
ms.openlocfilehash: 80ede9b7bc5bf667e03dc0a745fbc0b5f6c2663a
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/09/2019
ms.locfileid: "59343286"
---
# <a name="how-to-add-and-remove-columns-in-the-windows-forms-datagridview-control-using-the-designer"></a>方法: デザイナーを使用して Windows フォーム DataGridView コントロールの列を追加および削除する
Windows フォーム<xref:System.Windows.Forms.DataGridView>コントロールがデータを表示するために列を含める必要があります。 コントロールを手動で設定する場合は、する必要があります列を追加する、自分でします。 または、コントロールを生成し、列に自動的に設定するデータ ソースにバインドできます。 データ ソースに表示するより多くの列が含まれている場合は、不要な列を削除できます。  
  
 次の手順が必要です、 **Windows アプリケーション**プロジェクトが含まれているフォームを<xref:System.Windows.Forms.DataGridView>コントロール。 このようなプロジェクトの設定の詳細については、次を参照してください。[方法。Windows フォーム アプリケーション プロジェクトを作成](/visualstudio/ide/step-1-create-a-windows-forms-application-project)と[方法。Windows フォームにコントロールを追加](how-to-add-controls-to-windows-forms.md)します。  
  
> [!NOTE]
>  実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。 設定を変更するには、 **[ツール]** メニューの **[設定のインポートとエクスポート]** をクリックします。 詳細については、「[Visual Studio IDE のカスタマイズ](/visualstudio/ide/personalizing-the-visual-studio-ide)」を参照してください。  
  
### <a name="to-add-a-column-using-the-designer"></a>デザイナーを使用して列を追加するには  
  
1. スマート タグ グリフをクリックします (![スマート タグ グリフ](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) の右上隅で、 <xref:System.Windows.Forms.DataGridView> 、制御し、**列の追加**します。  
  
2. **列の追加** ダイアログ ボックスで、選択、**データ バインド列**オプションし、データ ソースから列を選択するか選択、**非バインド列**オプションを選択し、列の定義該当するフィールドを使用します。  
  
3. をクリックして、**追加**に既存の列が既にいっぱいになるコントロールの表示領域がある場合に、デザイナーに表示される原因となる列を追加するボタンをクリックします。  
  
    > [!NOTE]
    >  列のプロパティを変更することができます、**列の編集** ダイアログ ボックスで、コントロールのスマート タグからアクセスできます。  
  
### <a name="to-remove-a-column-using-the-designer"></a>デザイナーを使用して列を削除するには  
  
1. 選択**列の編集**コントロールのスマート タグから。  
  
2. 列を選択、**選択した列**一覧。  
  
3. をクリックして、**削除**デザイナーから非表示にされ、列を削除するボタンをクリックします。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.DataGridView>
- [方法: Windows フォーム アプリケーション プロジェクトを作成します。](/visualstudio/ide/step-1-create-a-windows-forms-application-project)
- [方法: Windows フォームにコントロールを追加する](how-to-add-controls-to-windows-forms.md)
