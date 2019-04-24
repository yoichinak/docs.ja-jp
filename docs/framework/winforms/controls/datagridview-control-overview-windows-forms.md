---
title: DataGridView コントロールの概要 (Windows フォーム)
ms.date: 03/30/2017
f1_keywords:
- DataGridView
helpviewer_keywords:
- DataGridView control [Windows Forms], about DataGridView control
- grid controls [Windows Forms]
- tables [Windows Forms], displaying in DataGridView control
- tables [Windows Forms], binding to DataGridView control
- columns [Windows Forms], DataGridView control
- bound controls [Windows Forms], dataGridView control
- datasets [Windows Forms], binding to DataGridView control
- data grids [Windows Forms], about data grids
- data [Windows Forms], resorting
- data [Windows Forms], navigating
- grids [Windows Forms]
- data binding [Windows Forms], DataGridView control
- data sources [Windows Forms], binding to DataGridView control
- DataGridView control [Windows Forms], data binding
ms.assetid: 0a45c661-89dc-4390-9cc6-c47eee501488
ms.openlocfilehash: 095c89fd305b1eeb73e2919760abe48e848c6aa0
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59112880"
---
# <a name="datagridview-control-overview-windows-forms"></a>DataGridView コントロールの概要 (Windows フォーム)
> [!NOTE]
>  <xref:System.Windows.Forms.DataGridView> コントロールは、<xref:System.Windows.Forms.DataGrid> コントロールに代わると共に追加の機能を提供します。ただし、<xref:System.Windows.Forms.DataGrid> コントロールは、下位互換性を保つ目的および将来使用する目的で保持されます。 詳細については、「[Windows フォームの DataGridView コントロールと DataGrid コントロールの違いについて](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md)」を参照してください。  
  
 <xref:System.Windows.Forms.DataGridView>コントロールを表示し、さまざまな種類のデータ ソースから表形式のデータを編集できます。  
  
 データ バインド、<xref:System.Windows.Forms.DataGridView>コントロールは簡単かつ直感的なおよび設定だけでは多くの場合、<xref:System.Windows.Forms.DataGridView.DataSource%2A>プロパティ。 複数のリストまたはテーブルを含むデータ ソースにバインドする場合は、設定、<xref:System.Windows.Forms.DataGridView.DataMember%2A>プロパティをリストまたはテーブルにバインドするを指定する文字列。  
  
 <xref:System.Windows.Forms.DataGridView>コントロールの次の一覧で説明されているクラスのインスタンスにバインドするための標準の Windows フォーム データ バインディング モデルをサポートしています。  
  
-   実装するクラス、 <xref:System.Collections.IList> 1 次元配列を含むインターフェイス。  
  
-   実装するクラス、<xref:System.ComponentModel.IListSource>インターフェイスなど、<xref:System.Data.DataTable>と<xref:System.Data.DataSet>クラス。  
  
-   実装するクラス、<xref:System.ComponentModel.IBindingList>インターフェイスなど、<xref:System.ComponentModel.BindingList%601>クラス。  
  
-   実装するクラス、<xref:System.ComponentModel.IBindingListView>インターフェイスなど、<xref:System.Windows.Forms.BindingSource>クラス。  
  
 <xref:System.Windows.Forms.DataGridView>コントロールは、これらのインターフェイスによって返されるオブジェクトのパブリック プロパティまたはによって返されるプロパティのコレクションにデータ バインディングをサポートしている、<xref:System.ComponentModel.ICustomTypeDescriptor>インターフェイスを実装して、返されたオブジェクトの場合。  
  
 通常、バインド、<xref:System.Windows.Forms.BindingSource>コンポーネントおよび bind、<xref:System.Windows.Forms.BindingSource>コンポーネントを別にデータ ソースまたはビジネス オブジェクトを設定します。 <xref:System.Windows.Forms.BindingSource>コンポーネントが優先されるデータ ソースでさまざまなデータ ソースにバインドでき、自動的に多くのデータ バインドの問題を解決することができます。 詳細については、次を参照してください。 [BindingSource コンポーネント](bindingsource-component.md)します。  
  
 <xref:System.Windows.Forms.DataGridView>コントロールはでも使用できます*バインドされていない*ない基になるデータ ストアとのモード。 非結合を使用するコード例については<xref:System.Windows.Forms.DataGridView>コントロールを参照してください[チュートリアル。作成、バインドされていない Windows フォーム DataGridView コントロール](walkthrough-creating-an-unbound-windows-forms-datagridview-control.md)します。  
  
 <xref:System.Windows.Forms.DataGridView>コントロール、構成可能かつ拡張可能なおよび多くのプロパティ、メソッド、およびその外観と動作をカスタマイズするイベントを提供します。 表形式のデータを表示するには、Windows フォーム アプリケーションを設定する場合は、使用を検討して、<xref:System.Windows.Forms.DataGridView>前に他のユーザー コントロール (たとえば、 <xref:System.Windows.Forms.DataGrid>)。 読み取り専用の値を小さなグリッドを表示する場合、または数百万件のレコードのテーブルを編集するユーザーを有効にする場合、<xref:System.Windows.Forms.DataGridView>コントロールで、簡単にプログラミング可能なメモリ効率の高いソリューションを提供します。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [DataGridView コントロール テクノロジの概要](datagridview-control-technology-summary-windows-forms.md)  
 要約<xref:System.Windows.Forms.DataGridView>概念と、関連するクラスの使用を制御します。  
  
 [DataGridView コントロールのアーキテクチャ](datagridview-control-architecture-windows-forms.md)  
 アーキテクチャについて説明します、<xref:System.Windows.Forms.DataGridView>コントロール、その型の階層と継承構造を説明します。  
  
 [DataGridView コントロールのシナリオ](datagridview-control-scenarios-windows-forms.md)  
 最も一般的なシナリオについて説明します<xref:System.Windows.Forms.DataGridView>コントロールを使用します。  
  
 [DataGridView コントロールのコード ディレクトリ](datagridview-control-code-directory-windows-forms.md)  
 さまざまなドキュメントのコード例へのリンクを提供します。<xref:System.Windows.Forms.DataGridView>タスク。 コード例はタスクの種類ごとに分類されています。  
  
## <a name="related-sections"></a>関連項目  
 [Windows フォーム DataGridView コントロールの列型](column-types-in-the-windows-forms-datagridview-control.md)  
 Windows フォームで列の型について説明します<xref:System.Windows.Forms.DataGridView>コントロール情報を表示したり変更したり、情報を追加できるようにするために使用します。  
  
 [Windows フォーム DataGridView コントロールでのデータの表示](displaying-data-in-the-windows-forms-datagridview-control.md)  
 コントロールに手動でデータを組み込む方法と、外部データ ソースからデータを取得する方法について説明するトピックを示します。  
  
 [Windows フォーム DataGridView コントロールのカスタマイズ](customizing-the-windows-forms-datagridview-control.md)  
 <xref:System.Windows.Forms.DataGridView> のセルおよび行のカスタム描画と、セル、列、および行の派生型の作成について説明するトピックを示します。  
  
 [Windows フォーム DataGridView コントロールでのパフォーマンス チューニング](performance-tuning-in-the-windows-forms-datagridview-control.md)  
 大量のデータを扱うときのパフォーマンスの問題を避けるために、このコントロールを効率的に使用する方法について説明するトピックを示します。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.BindingSource>
- [DataGridView コントロール](datagridview-control-windows-forms.md)
- [Windows フォーム DataGridView コントロールの既定の機能](default-functionality-in-the-windows-forms-datagridview-control.md)
- [Windows フォーム DataGridView コントロールの既定のキーボード処理とマウス処理](default-keyboard-and-mouse-handling-in-the-windows-forms-datagridview-control.md)
