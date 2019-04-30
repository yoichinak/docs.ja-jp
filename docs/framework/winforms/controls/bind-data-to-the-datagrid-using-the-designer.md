---
title: '方法: デザイナーを使用してデータを Windows フォーム DataGridView コントロールにバインドする'
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms controls, binding to a data source
- data sources [Windows Forms], binding to Windows Forms controls
- DataGridView control [Windows Forms], data binding
ms.assetid: f4f46009-cec2-441b-8668-6b5af057558b
ms.openlocfilehash: 59a025535e850cf3c773a2a078511d41058bb24c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62011720"
---
# <a name="how-to-bind-data-to-the-windows-forms-datagridview-control-using-the-designer"></a>方法: デザイナーを使用してデータを Windows フォーム DataGridView コントロールにバインドする
デザイナーを使用して、接続、<xref:System.Windows.Forms.DataGridView>データベース、ビジネス オブジェクト、Web サービスなど、いくつかの異なる種類のデータ ソースへのコントロール。 デザイナーを使用してデータ ソースにコントロールをバインドすると、コントロールに自動的にバインドを<xref:System.Windows.Forms.BindingSource>コンポーネントをデータ ソースを表します。 さらに、データ ソースによって提供されるスキーマ情報に対応するように、このコントロールの列が自動的に生成されます。  
  
 列が生成された後に、ニーズに合わせて列を変更できます。 たとえば、表示に関係のない列を削除または非表示にしたり、列の順序を変更したり、列の型を変更したりすることができます。 列の変更の詳細については、「関連項目」セクションの各トピックを参照してください。  
  
 複数をバインドすることもできます。<xref:System.Windows.Forms.DataGridView>関連テーブルのマスター/詳細リレーションシップを作成するコントロール。 この構成では、1 つのコントロールに親テーブルが表示され、別のコントロールには親テーブルの現在の行に関連する子テーブルの行のみが表示されます。 詳細については、「[方法 :表示では、データ フォーム アプリケーションを Windows に関連する](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/57tx3hhe(v=vs.120))します。  
  
 次の手順が必要です、 **Windows アプリケーション**を含むフォームを使用してプロジェクトを<xref:System.Windows.Forms.DataGridView>コントロールまたはマスター/詳細リレーションシップの 2 つのコントロール。 このようなプロジェクトの開始方法の詳細については、次を参照してください。[方法。Windows フォーム アプリケーション プロジェクトを作成](/visualstudio/ide/step-1-create-a-windows-forms-application-project)と[方法。Windows フォームにコントロールを追加](how-to-add-controls-to-windows-forms.md)します。  
  
> [!NOTE]
>  実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。 設定を変更するには、 **[ツール]** メニューの **[設定のインポートとエクスポート]** をクリックします。 詳細については、「[Visual Studio IDE のカスタマイズ](/visualstudio/ide/personalizing-the-visual-studio-ide)」を参照してください。  
  
### <a name="to-bind-the-control-to-a-data-source"></a>コントロールをデータ ソースにバインドするには  
  
1. スマート タグ グリフをクリックします (![スマート タグ グリフ](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) の右上隅で、<xref:System.Windows.Forms.DataGridView>コントロール。  
  
2. **[データ ソースの選択]** オプションのドロップダウン矢印をクリックします。  
  
3. プロジェクトにまだデータ ソースがない場合は、**[プロジェクト データ ソースの追加]** をクリックし、ウィザードに示される手順に従います。  
  
     詳細については、「[データ ソース構成ウィザード](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/w4dd7z6t(v=vs.120))」を参照してください。 **[データ ソースの選択]** ドロップダウン ウィンドウに新しいデータ ソースが表示されます。 新しいデータ ソースに含まれるのが単一データベース テーブルなど、1 つのメンバーのみの場合、コントロールはそのメンバーに自動的にバインドされます。 それ以外の場合は、次の手順に進みます。  
  
4. 展開されていない場合は **[他のデータ ソース]** ノードと **[プロジェクト データ ソース]** ノードを展開し、コントロールをバインドするデータ ソースを選択します。  
  
5. データ ソースには、複数のメンバーが含まれている場合などを作成した場合、<xref:System.Data.DataSet?displayProperty=nameWithType>複数のテーブルを格納している、データ ソースを展開し、特定のメンバーにバインドします。  
  
6. マスター/詳細リレーションシップを作成する、**データ ソースの選択**を 2 番目のドロップダウン ウィンドウ<xref:System.Windows.Forms.DataGridView>コントロールを展開し、<xref:System.Windows.Forms.BindingSource>親テーブルの作成し、一覧から関連する子テーブルを選択表示されます。  
  
    > [!NOTE]
    >  プロジェクトにデータ ソースが既にある場合は、**[データソース]** ウィンドウを使用してデータ フォームを作成することもできます。 詳細については、「[[データ ソース] ウィンドウ](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/6ckyxa83(v=vs.120))」を参照してください。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.BindingSource>
- <xref:System.Windows.Forms.DataGridView.DataMember%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.DataSource%2A?displayProperty=nameWithType>
- [方法: データをデータベースに接続するには](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/fxk9yw1t(v=vs.120))
- [方法: 追加して、デザイナーを使用して Windows フォーム DataGridView コントロールで列を削除](add-and-remove-columns-in-the-datagrid-using-the-designer.md)
- [方法: デザイナーを使用して Windows フォーム DataGridView コントロール内の列の順序を変更します。](change-the-order-of-columns-in-the-datagrid-using-the-designer.md)
- [方法: デザイナーを使用して Windows フォーム DataGridView 列の型を変更します。](change-the-type-of-a-wf-datagridview-column-using-the-designer.md)
- [方法: デザイナーを使用して Windows フォーム DataGridView コントロールで列を固定します。](freeze-columns-in-the-datagrid-using-the-designer.md)
- [方法: デザイナーを使用して Windows フォーム DataGridView コントロール内の列を非表示にします。](hide-columns-in-the-datagrid-using-the-designer.md)
- [方法: 読み取り専用デザイナーを使用して Windows フォーム DataGridView コントロールで列を作成します。](make-columns-read-only-in-the-datagrid-using-the-designer.md)
- [方法: Windows フォーム アプリケーション プロジェクトの作成](/visualstudio/ide/step-1-create-a-windows-forms-application-project)
- [方法: Windows フォームにコントロールを追加します。](how-to-add-controls-to-windows-forms.md)
- [データ ソース ウィンドウ](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/6ckyxa83(v=vs.120))
- [方法: Windows フォーム アプリケーションで関連データを表示します。](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/57tx3hhe(v=vs.120))
