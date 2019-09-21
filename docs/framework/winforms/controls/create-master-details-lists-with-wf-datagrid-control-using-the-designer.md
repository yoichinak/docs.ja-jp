---
title: '方法: デザイナーで Windows フォーム DataGrid コントロールを使用してマスター/詳細リストを作成する'
ms.date: 03/30/2017
helpviewer_keywords:
- master-details lists
- DataGrid control [Windows Forms], master-details lists
- related tables [Windows Forms], displaying in DataGrid control
ms.assetid: 19438ba2-f687-4417-a2fb-ab1cd69d4ded
ms.openlocfilehash: 3962b671176ad158b338889140181834e05bbeee
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69929720"
---
# <a name="how-to-create-master-details-lists-with-the-windows-forms-datagrid-control-using-the-designer"></a>方法: デザイナーで Windows フォーム DataGrid コントロールを使用してマスター/詳細リストを作成する

> [!NOTE]
> <xref:System.Windows.Forms.DataGridView> コントロールは、<xref:System.Windows.Forms.DataGrid> コントロールに代わると共に追加の機能を提供します。ただし、<xref:System.Windows.Forms.DataGrid> コントロールは、下位互換性を保つ目的および将来使用する目的で保持されます。 詳細については、「[Windows フォームの DataGridView コントロールと DataGrid コントロールの違いについて](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md)」を参照してください。

 に<xref:System.Data.DataSet>一連の関連テーブルが含まれている場合は、 <xref:System.Windows.Forms.DataGrid> 2 つのコントロールを使用して、マスター/詳細形式でデータを表示できます。 1 <xref:System.Windows.Forms.DataGrid>つはマスターグリッドとして指定され、2番目は詳細グリッドとして指定されます。 マスターリストでエントリを選択すると、関連するすべての子エントリが詳細一覧に表示されます。 たとえば、に<xref:System.Data.DataSet> customers テーブルと関連する orders テーブルが含まれている場合は、customers テーブルをマスターグリッドに指定し、orders テーブルを詳細グリッドとして指定します。 マスターグリッドから顧客を選択すると、Orders テーブル内のその顧客に関連付けられているすべての注文が詳細グリッドに表示されます。

 次の手順では、 **Windows アプリケーション**プロジェクトが必要です (**ファイル** >  **新しい** > **プロジェクト** >  **ビジュアルC#**  または  **Visual Basic**  >  **クラシックデスクトップ** > **Windows フォームアプリケーション**)。

## <a name="to-create-a-master-details-list-in-the-designer"></a>デザイナーでマスター/詳細リストを作成するには

1. フォームに<xref:System.Windows.Forms.DataGrid> 2 つのコントロールを追加します。 詳細については、「[方法 :Windows フォーム](how-to-add-controls-to-windows-forms.md)にコントロールを追加します。 Visual Studio 2005 <xref:System.Windows.Forms.DataGrid>では、コントロールは既定では**ツールボックス**に含まれていません。 詳細については、「[方法 :ツールボックス](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms165355(v=vs.100))に項目を追加します。

    > [!NOTE]
    > 次の手順は、デザイン時のデータバインディングに **[データソース]** ウィンドウを使用する Visual Studio 2005 には適用されません。 詳細については、「 [Visual Studio でのデータへのコントロールのバインド](/visualstudio/data-tools/bind-controls-to-data-in-visual-studio)」と[「方法:Windows フォームアプリケーション](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/57tx3hhe(v=vs.120))に関連データを表示します。

2. **サーバーエクスプローラー**からフォームに2つ以上のテーブルをドラッグします。

3. **[データ]** メニューの データ **[セットの生成]** を選択します。

4. XML デザイナーを使用して、テーブル間のリレーションシップを設定します。 詳細については、「方法:MSDN の XML スキーマとデータセットに、一対多のリレーションシップを作成します。

5. **[ファイル]** メニューの **[すべてを保存]** を選択して、リレーションシップを保存します。

6. 次のように、マスターグリッドを指定するコントロールを構成します。<xref:System.Windows.Forms.DataGrid>

    1. プロパティのドロップダウンリスト<xref:System.Data.DataSet>からを選択<xref:System.Windows.Forms.DataGrid.DataSource%2A>します。

    2. <xref:System.Windows.Forms.DataGrid.DataMember%2A>プロパティのドロップダウンリストからマスターテーブル (たとえば、"Customers") を選択します。

7. 詳細グリッドを指定するコントロールを次のように構成します。<xref:System.Windows.Forms.DataGrid>

    1. プロパティのドロップダウンリスト<xref:System.Data.DataSet>からを選択<xref:System.Windows.Forms.DataGrid.DataSource%2A>します。

    2. <xref:System.Windows.Forms.DataGrid.DataMember%2A>プロパティのドロップダウンリストから、マスターテーブルと詳細テーブルの間のリレーションシップ (例: "CustOrd") を選択します。 リレーションシップを表示するには、ドロップダウンリストでマスターテーブルの横に **+** あるプラス記号 () をクリックして、ノードを展開します。

## <a name="see-also"></a>関連項目

- [DataGrid コントロール](datagrid-control-windows-forms.md)
- [DataGrid コントロールの概要](datagrid-control-overview-windows-forms.md)
- [方法: データソースへの Windows フォーム DataGrid コントロールのバインド](how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md)
- [Visual Studio でのデータへのコントロールのバインド](/visualstudio/data-tools/bind-controls-to-data-in-visual-studio)
