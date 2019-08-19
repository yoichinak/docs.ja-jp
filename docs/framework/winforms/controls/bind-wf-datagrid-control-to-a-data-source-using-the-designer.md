---
title: '方法: デザイナーを使ってデータ ソースに Windows フォーム DataGrid コントロールをバインドする'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- datasets [Windows Forms], binding to DataGrid control
- data binding [Windows Forms], DataGrid control
- DataGrid control [Windows Forms], data binding
- Windows Forms controls, data binding
- bound controls [Windows Forms]
ms.assetid: 4e96e3d0-b1cc-4de1-8774-bc9970ec4554
ms.openlocfilehash: de8b8d16f45221fbafe9f61ca634f144d8f6f6ae
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69040012"
---
# <a name="how-to-bind-the-windows-forms-datagrid-control-to-a-data-source-using-the-designer"></a>方法: デザイナーを使ってデータ ソースに Windows フォーム DataGrid コントロールをバインドする

> [!NOTE]
>  <xref:System.Windows.Forms.DataGridView> コントロールは、<xref:System.Windows.Forms.DataGrid> コントロールに代わると共に追加の機能を提供します。ただし、<xref:System.Windows.Forms.DataGrid> コントロールは、下位互換性を保つ目的および将来使用する目的で保持されます。 詳細については、「[Windows フォームの DataGridView コントロールと DataGrid コントロールの違いについて](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md)」を参照してください。

 Windows フォーム<xref:System.Windows.Forms.DataGrid>コントロールは、特にデータソースからの情報を表示するように設計されています。 デザイン時にコントロールをバインドするには、 <xref:System.Windows.Forms.DataGrid.DataSource%2A>プロパティ<xref:System.Windows.Forms.DataGrid.DataMember%2A>とプロパティを設定するか、 <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A>メソッドを呼び出して実行時にコントロールをバインドします。 さまざまなデータソースのデータを表示できますが、最も一般的なソースはデータセットとデータビューです。

 データソースがデザイン時に使用可能な場合 (たとえば、フォームにデータセットまたはデータビューのインスタンスが含まれている場合)、デザイン時にグリッドをデータソースにバインドできます。 これにより、データがグリッド内でどのように表示されるかをプレビューできます。

 また、実行時にプログラムによってグリッドをバインドすることもできます。 これは、実行時に取得した情報に基づいてデータソースを設定する場合に便利です。 たとえば、アプリケーションでは、表示するテーブルの名前をユーザーが指定できます。 また、デザイン時にデータソースが存在しない場合にも必要になります。 これには、配列、コレクション、型指定されていないデータセット、データリーダーなどのデータソースが含まれます。

 次の手順では、 <xref:System.Windows.Forms.DataGrid>コントロールを含むフォームを含む**Windows アプリケーション**プロジェクトが必要です。 このようなプロジェクトの設定の詳細につい[ては、「方法:Windows フォームアプリケーションプロジェクト](/visualstudio/ide/step-1-create-a-windows-forms-application-project)を作成し[、次の操作を行います。Windows フォーム](how-to-add-controls-to-windows-forms.md)にコントロールを追加します。 Visual Studio 2005 <xref:System.Windows.Forms.DataGrid>では、コントロールは既定では**ツールボックス**に含まれていません。 追加の詳細については[、「方法:ツールボックス](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms165355(v=vs.100))に項目を追加します。 さらに、Visual Studio 2005 では、デザイン時のデータバインディングに **[データソース]** ウィンドウを使用できます。 詳細については、「 [Visual Studio でのデータへのコントロールのバインド](/visualstudio/data-tools/bind-controls-to-data-in-visual-studio)」を参照してください。

## <a name="to-data-bind-the-datagrid-control-to-a-single-table-in-the-designer"></a>デザイナーで DataGrid コントロールを1つのテーブルにデータバインドするには

1. コントロールの<xref:System.Windows.Forms.DataGrid.DataSource%2A>プロパティに、バインド先のデータ項目を含むオブジェクトを設定します。

2. データソースがデータセットである場合は、 <xref:System.Windows.Forms.DataGrid.DataMember%2A>バインド先のテーブルの名前にプロパティを設定します。

3. データソースがデータセットまたはデータセットテーブルに基づくデータビューの場合は、データセットを埋めるためのコードをフォームに追加します。

     実際に使用するコードは、データセットがデータを取得している場所によって異なります。 データセットがデータベースから直接作成されている場合は、通常`Fill` 、次のコード例に示すようにデータアダプターのメソッドを呼び出します。この`DsCategories1`コード例は、というデータセットを設定します。

    ```vb
    sqlDataAdapter1.Fill(DsCategories1)
    ```

    ```csharp
    sqlDataAdapter1.Fill(DsCategories1);
    ```

    ```cpp
    sqlDataAdapter1->Fill(dsCategories1);
    ```

4. Optional適切なテーブルスタイルと列スタイルをグリッドに追加します。

     テーブルスタイルが存在しない場合は、テーブルが表示されますが、すべての列が表示されます。

## <a name="to-data-bind-the-datagrid-control-to-multiple-tables-in-a-dataset-in-the-designer"></a>デザイナーで DataGrid コントロールをデータセット内の複数のテーブルにデータバインドするには

1. コントロールの<xref:System.Windows.Forms.DataGrid.DataSource%2A>プロパティに、バインド先のデータ項目を含むオブジェクトを設定します。

2. データセットに関連テーブルが含まれている場合 (つまり、リレーションシップオブジェクトが含まれて<xref:System.Windows.Forms.DataGrid.DataMember%2A>いる場合)、プロパティを親テーブルの名前に設定します。

3. データセットを埋めるコードを記述します。

## <a name="see-also"></a>関連項目

- [DataGrid コントロールの概要](datagrid-control-overview-windows-forms.md)
- [方法: Windows フォーム DataGrid コントロールにテーブルと列を追加する](how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control.md)
- [DataGrid コントロール](datagrid-control-windows-forms.md)
- [Windows フォームでのデータ バインディング](../windows-forms-data-binding.md)
- [Visual Studio でのデータへのアクセス](/visualstudio/data-tools/accessing-data-in-visual-studio)
