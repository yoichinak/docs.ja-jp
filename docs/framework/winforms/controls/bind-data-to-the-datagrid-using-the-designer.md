---
title: '方法: デザイナーを使用してデータを Windows フォーム DataGridView コントロールにバインドする'
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms controls, binding to a data source
- data sources [Windows Forms], binding to Windows Forms controls
- DataGridView control [Windows Forms], data binding
ms.assetid: f4f46009-cec2-441b-8668-6b5af057558b
ms.openlocfilehash: 609878416be26786ce865168c996c78e18b1897f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69917885"
---
# <a name="how-to-bind-data-to-the-windows-forms-datagridview-control-using-the-designer"></a>方法: デザイナーを使用してデータを Windows フォーム DataGridView コントロールにバインドする
デザイナーを使用すると、データベース、 <xref:System.Windows.Forms.DataGridView>ビジネスオブジェクト、Web サービスなど、さまざまな種類のデータソースにコントロールを接続できます。 デザイナーを使用してコントロールをデータソースにバインドすると、コントロールはデータソースを表す<xref:System.Windows.Forms.BindingSource>コンポーネントに自動的にバインドされます。 さらに、データ ソースによって提供されるスキーマ情報に対応するように、このコントロールの列が自動的に生成されます。

 列が生成された後に、ニーズに合わせて列を変更できます。 たとえば、表示に関係のない列を削除または非表示にしたり、列の順序を変更したり、列の型を変更したりすることができます。 列の変更の詳細については、「関連項目」セクションの各トピックを参照してください。

 また、関連テーブルに<xref:System.Windows.Forms.DataGridView>複数のコントロールをバインドして、マスター/詳細リレーションシップを作成することもできます。 この構成では、1 つのコントロールに親テーブルが表示され、別のコントロールには親テーブルの現在の行に関連する子テーブルの行のみが表示されます。 詳細については、「[方法 :Windows フォームアプリケーション](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/57tx3hhe(v=vs.120))に関連データを表示します。

 次の手順では、マスター/詳細リレーションシップのコントロールまたは<xref:System.Windows.Forms.DataGridView> 2 つのコントロールを含むフォームを含む**Windows アプリケーション**プロジェクトが必要です。 このようなプロジェクトを開始する方法の[詳細については、「方法:Windows フォームアプリケーションプロジェクト](/visualstudio/ide/step-1-create-a-windows-forms-application-project)を作成し[、次の操作を行います。Windows フォーム](how-to-add-controls-to-windows-forms.md)にコントロールを追加します。

## <a name="to-bind-the-control-to-a-data-source"></a>コントロールをデータ ソースにバインドするには

1. <xref:System.Windows.Forms.DataGridView>コントロールの右上隅にあるスマートタググリフ (![スマートタググリフ](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) をクリックします。

2. **[データ ソースの選択]** オプションのドロップダウン矢印をクリックします。

3. プロジェクトにまだデータ ソースがない場合は、 **[プロジェクト データ ソースの追加]** をクリックし、ウィザードに示される手順に従います。

     詳細については、「[データ ソース構成ウィザード](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/w4dd7z6t(v=vs.120))」を参照してください。 **[データ ソースの選択]** ドロップダウン ウィンドウに新しいデータ ソースが表示されます。 新しいデータ ソースに含まれるのが単一データベース テーブルなど、1 つのメンバーのみの場合、コントロールはそのメンバーに自動的にバインドされます。 それ以外の場合は、次の手順に進みます。

4. 展開されていない場合は **[他のデータ ソース]** ノードと **[プロジェクト データ ソース]** ノードを展開し、コントロールをバインドするデータ ソースを選択します。

5. 複数のテーブルを含むを<xref:System.Data.DataSet?displayProperty=nameWithType>作成した場合など、データソースに複数のメンバーが含まれている場合は、データソースを展開し、バインド先の特定のメンバーを選択します。

6. マスター/詳細リレーションシップを作成するには、 **[データソースの選択]** ドロップダウンウィンドウ<xref:System.Windows.Forms.DataGridView>で、親テーブル用に<xref:System.Windows.Forms.BindingSource>作成したを展開し、表示されている一覧から関連する子テーブルを選択します。

    > [!NOTE]
    > プロジェクトにデータ ソースが既にある場合は、 **[データソース]** ウィンドウを使用してデータ フォームを作成することもできます。 詳細については、「[[データ ソース] ウィンドウ](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/6ckyxa83(v=vs.120))」を参照してください。

## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.BindingSource>
- <xref:System.Windows.Forms.DataGridView.DataMember%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.DataSource%2A?displayProperty=nameWithType>
- [方法: データベース内のデータへの接続](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/fxk9yw1t(v=vs.120))
- [方法: デザイナーを使用した Windows フォーム DataGridView コントロールでの列の追加と削除](add-and-remove-columns-in-the-datagrid-using-the-designer.md)
- [方法: デザイナーを使用して Windows フォーム DataGridView コントロールの列の順序を変更する](change-the-order-of-columns-in-the-datagrid-using-the-designer.md)
- [方法: デザイナーを使用して Windows フォーム DataGridView 列の型を変更する](change-the-type-of-a-wf-datagridview-column-using-the-designer.md)
- [方法: デザイナーを使用して Windows フォーム DataGridView コントロールの列を固定する](freeze-columns-in-the-datagrid-using-the-designer.md)
- [方法: デザイナーを使用して Windows フォーム DataGridView コントロールの列を非表示にする](hide-columns-in-the-datagrid-using-the-designer.md)
- [方法: デザイナーを使用して Windows フォーム DataGridView コントロールで列を読み取り専用にする](make-columns-read-only-in-the-datagrid-using-the-designer.md)
- [方法: Windows フォーム アプリケーション プロジェクトの作成](/visualstudio/ide/step-1-create-a-windows-forms-application-project)
- [方法: コントロールを Windows フォームに追加する](how-to-add-controls-to-windows-forms.md)
- [データソースウィンドウ](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/6ckyxa83(v=vs.120))
- [方法: Windows フォームアプリケーションに関連データを表示する](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/57tx3hhe(v=vs.120))
