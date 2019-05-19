---
title: '方法: デザイナーを使って Windows フォーム DataGrid コントロールにテーブルと列を追加する'
ms.date: 03/30/2017
helpviewer_keywords:
- columns [Windows Forms], adding to DataGrid control
- tables [Windows Forms], adding to DataGrid control
- DataGrid control [Windows Forms], adding tables and columns
ms.assetid: 4a6d1b34-b696-476b-bf8a-57c6230aa9e1
ms.openlocfilehash: b248e9b250ce18f05a2bf57b80af8fbcebb4f811
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/19/2019
ms.locfileid: "65880601"
---
# <a name="how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control-using-the-designer"></a>方法: デザイナーを使って Windows フォーム DataGrid コントロールにテーブルと列を追加する

> [!NOTE]
>  
  <xref:System.Windows.Forms.DataGridView> コントロールは、<xref:System.Windows.Forms.DataGrid> コントロールに代わると共に追加の機能を提供します。ただし、<xref:System.Windows.Forms.DataGrid> コントロールは、下位互換性を保つ目的および将来使用する目的で保持されます。 詳細については、「[Windows フォームの DataGridView コントロールと DataGrid コントロールの違いについて](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md)」を参照してください。  
  
 データを表示するには、Windows フォームで<xref:System.Windows.Forms.DataGrid>テーブルと列を作成してコントロール<xref:System.Windows.Forms.DataGridTableStyle>オブジェクトと追加すること、<xref:System.Windows.Forms.GridTableStylesCollection>オブジェクトを通じてアクセスされる、<xref:System.Windows.Forms.DataGrid>コントロールの<xref:System.Windows.Forms.DataGrid.TableStyles%2A>プロパティ。 各テーブルのスタイルがで指定されたは、どのようなデータ テーブルの内容を表示、<xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A>のプロパティ、<xref:System.Windows.Forms.DataGridTableStyle>します。 既定では、指定された列スタイルなしのテーブルのスタイルはそのデータ テーブル内のすべての列に表示されます。 追加することで表示するテーブルから列を制限する<xref:System.Windows.Forms.DataGridColumnStyle>オブジェクトを<xref:System.Windows.Forms.GridColumnStylesCollection>、経由でアクセスする、<xref:System.Windows.Forms.DataGridTableStyle.GridColumnStyles%2A>の各プロパティ<xref:System.Windows.Forms.DataGridTableStyle>します。  
  
 次の手順が必要です、 **Windows アプリケーション**を含むフォームを使用してプロジェクトを<xref:System.Windows.Forms.DataGrid>コントロール。 このようなプロジェクトを設定する方法については、次を参照してください。[方法。Windows フォーム アプリケーション プロジェクトを作成](/visualstudio/ide/step-1-create-a-windows-forms-application-project)と[方法。Windows フォームにコントロールを追加](how-to-add-controls-to-windows-forms.md)します。 既定では、Visual Studio 2005 で、<xref:System.Windows.Forms.DataGrid>制御されていない、**ツールボックス**します。 追加の詳細については、次を参照してください。[方法。項目をツールボックスに追加](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms165355(v=vs.100))します。  
  
> [!NOTE]
>  実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。 設定を変更するには、 **[ツール]** メニューの **[設定のインポートとエクスポート]** をクリックします。 詳細については、「[Visual Studio IDE のカスタマイズ](/visualstudio/ide/personalizing-the-visual-studio-ide)」を参照してください。  
  
### <a name="to-add-a-table-to-the-datagrid-control-in-the-designer"></a>デザイナーの DataGrid コントロールにテーブルを追加するには  
  
1. テーブルにデータを表示するにはまず、<xref:System.Windows.Forms.DataGrid>データセットへのコントロール。 詳細については、「[方法 :デザイナーを使用してデータ ソースに Windows フォーム DataGrid コントロールをバインド](bind-wf-datagrid-control-to-a-data-source-using-the-designer.md)します。  
  
2.  選択、<xref:System.Windows.Forms.DataGrid>コントロールの<xref:System.Windows.Forms.DataGrid.TableStyles%2A>[プロパティ] ウィンドウで、省略記号ボタンをクリックし、(![. Visual Studio の [プロパティ] ウィンドウで、省略記号ボタン (…)](./media/visual-studio-ellipsis-button.png)) を表示するプロパティの横に、**DataGridTableStyle コレクション エディター**します。  
  
3. コレクション エディターで **追加**テーブル スタイルを挿入します。  
  
4. クリックして**OK**コレクション エディターを終了し、横にある省略記号ボタンをクリックして再度、<xref:System.Windows.Forms.DataGrid.TableStyles%2A>プロパティ。  
  
     コレクション エディターを開くと、コントロールにバインドされているすべてのデータ テーブルは、のドロップダウン リストに表示されます、<xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A>テーブル スタイルのプロパティ。  
  
5. **メンバー**ボックス、コレクション エディターのテーブルのスタイルをクリックします。  
  
6. **プロパティ**のコレクション エディターでは、選択ボックス、<xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A>を表示するテーブルの値。  
  
### <a name="to-add-a-column-to-the-datagrid-control-in-the-designer"></a>デザイナーの DataGrid コントロールに列を追加するには  
  
1.  **メンバー**のボックス、 **DataGridTableStyle コレクション エディター**、適切なテーブルのスタイルを選択します。 **プロパティ**のコレクション エディターでは、選択ボックス、<xref:System.Windows.Forms.DataGridTableStyle.GridColumnStyles%2A>コレクション、省略記号ボタンをクリックし、(![. Visual Studio の [プロパティ] ウィンドウで、省略記号ボタン (…)](./media/visual-studio-ellipsis-button.png)) 横にこのプロパティを表示、 **DataGridColumnStyle コレクション エディター**します。  
  
2. コレクション エディターで **追加**列スタイルの挿入または下向きの矢印をクリックして**追加**列の型を指定します。  
  
     ドロップダウン ボックスで、いずれかを選択できます、<xref:System.Windows.Forms.DataGridTextBoxColumn>または<xref:System.Windows.Forms.DataGridBoolColumn>型。  
  
3. 閉じるには、[ok] をクリックして、 **DataGridColumnStyle コレクション エディター**、横にある省略記号ボタンをクリックして再度開くと、<xref:System.Windows.Forms.DataGridTableStyle.GridColumnStyles%2A>プロパティ。  
  
     ドロップダウン リストにバインドされたデータ テーブル内のデータ列が表示されます、コレクション エディターを再度開くと、<xref:System.Windows.Forms.DataGridColumnStyle.MappingName%2A>列スタイルのプロパティ。  
  
4. **メンバー**ボックス、コレクション エディターの列のスタイルをクリックします。  
  
5. **プロパティ**のコレクション エディターでは、選択ボックス、<xref:System.Windows.Forms.DataGridColumnStyle.MappingName%2A>を表示する列の値。  
  
## <a name="see-also"></a>関連項目

- [DataGrid コントロール](datagrid-control-windows-forms.md)
- [方法: 削除、または Windows フォームの DataGrid コントロール内の列を非表示にします。](how-to-delete-or-hide-columns-in-the-windows-forms-datagrid-control.md)
