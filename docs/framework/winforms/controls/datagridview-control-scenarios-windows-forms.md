---
title: DataGridView コントロールのシナリオ (Windows フォーム)
ms.date: 03/30/2017
helpviewer_keywords:
- data [Windows Forms], displaying in tabular format
- data grids [Windows Forms], about data grids
- DataGridView control [Windows Forms], scenarios
ms.assetid: 09a5fd05-3447-47ec-a4ec-6082a2b7f0dd
ms.openlocfilehash: 52c448f21be056e6166334785943356039baf3ad
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59175293"
---
# <a name="datagridview-control-scenarios-windows-forms"></a>DataGridView コントロールのシナリオ (Windows フォーム)
<xref:System.Windows.Forms.DataGridView>コントロール、さまざまなデータ ソースから表形式のデータを表示することができます。 単純な用途は、手動で設定できる、<xref:System.Windows.Forms.DataGridView>コントロールから直接データを操作します。 通常、ただし、外部データ ソースにデータを格納してコントロールにバインドして、<xref:System.Windows.Forms.BindingSource>コンポーネント。  
  
 このトピックでは、一部を実行する一般的なシナリオについて説明します、<xref:System.Windows.Forms.DataGridView>コントロール。  
  
## <a name="scenario-1-displaying-small-amounts-of-data"></a>シナリオ 1:少量のデータを表示します。  
 表示する外部データ ソースにデータを格納する必要はありません、<xref:System.Windows.Forms.DataGridView>コントロール。 少量のデータを使用する場合は、自分でコントロールを設定し、コントロールを通じてデータを操作できます。 これは呼び出されます*非バインド モード*します。 詳細については、「[方法 :バインドされていない Windows フォーム DataGridView コントロールの作成](how-to-create-an-unbound-windows-forms-datagridview-control.md)です。  
  
### <a name="scenario-key-points"></a>シナリオの要点  
  
-   非バインド モード設定コントロールを手動でします。  
  
-   非バインド モードは、読み取り専用データが少ない場合に特に適しています。  
  
-   非バインド モードはスプレッドシート形式または値の数がテーブルにも適しています。  
  
## <a name="scenario-2-viewing-and-updating-data-stored-in-an-external-data-source"></a>シナリオ 2:表示し、外部データ ソースに格納されたデータの更新  
 使用することができます、<xref:System.Windows.Forms.DataGridView>ユーザーを通じて、データベース テーブルまたはビジネス オブジェクトのコレクションなどのデータ ソースに保持されるデータにアクセスできるユーザー インターフェイス (UI) コントロールです。 詳細については、「[方法 :バインド データを Windows フォーム DataGridView コントロール](how-to-bind-data-to-the-windows-forms-datagridview-control.md)します。  
  
### <a name="scenario-key-points"></a>シナリオの要点  
  
-   バインド モードでは、データ ソースへの接続、データ ソースのプロパティまたはデータベースの列に基づく列を自動的に生成およびコントロールを自動的に設定できます。  
  
-   バインド モードは、負荷の高いユーザー データとやり取りに適しています。 表示、データを書式設定することができ、ユーザー指定のデータをデータ ソースによって予期される形式に解析できます。 ユーザーに警告およびエラーのあるセルを修正できるように、エラーおよびデータベースの制約のエラーの書式設定データ エントリを検出できます。  
  
-   列の並べ替えなどの追加機能は、フリーズ、および並べ替えは、ワークフローに最も便利な方法でデータを表示するユーザーに有効にします。  
  
-   クリップボードのサポートでは、他のアプリケーションへのアプリケーションからデータをコピーすることができます。  
  
## <a name="scenario-3-advanced-data"></a>シナリオ 3:高度なデータ  
 実装することで、コントロールとデータ間の相互作用を管理するには、標準的なデータ バインディング モデルが解決されない特別なニーズがあれば、*仮想モード*します。 仮想モード手段の情報とセルのコントロール要求について使用できる 1 つまたは複数のイベント ハンドラーの実装の実装が必要です。  
  
 たとえば、大量のデータを使用する場合、最適な効率性を確保する仮想モードを実装します。 仮想モードも別のデータ ソースから取得した列と共に表示する非バインド列の値を維持するために役立ちます。  
  
 仮想モードの詳細については、次を参照してください。[チュートリアル。仮想モードの実装で、Windows フォーム DataGridView コントロール](implementing-virtual-mode-wf-datagridview-control.md)します。  
  
### <a name="scenario-key-points"></a>シナリオの要点  
  
-   仮想モードは、パフォーマンスを微調整する必要がある場合は、非常に大量のデータを表示するために適しています。  
  
## <a name="scenario-4-automatically-resizing-rows-and-columns"></a>シナリオ 4:行と列を自動的にサイズ変更  
 定期的に更新するデータを表示するときにすべてのコンテンツが表示されていることを確認する行と列を自動的に変更できます。 <xref:System.Windows.Forms.DataGridView>コントロールは、有効または無効にする手動のサイズ変更、特定の時点でサイズをプログラムで変更できるようにするいくつかのオプションを提供します。 または、自動的にサイズ変更されるたびに、変更をコンテンツ。 詳細については、次を参照してください。 [Windows フォームの DataGridView コントロールのサイズ変更オプション](sizing-options-in-the-windows-forms-datagridview-control.md)します。  
  
### <a name="scenario-key-points"></a>シナリオの要点  
  
-   手動のサイズを変更すると、セルの高さと幅を調整するユーザーができます。  
  
-   自動サイズ変更するには、セルの内容がクリップされないように、セルのサイズを維持することができます。  
  
-   プログラムによるサイズ変更するには、継続的な自動サイズ変更のパフォーマンスの低下を回避するために特定の時点でのセルのサイズを変更することができます。  
  
## <a name="scenario-5-simple-customization"></a>シナリオ 5:単純なカスタマイズ  
 <xref:System.Windows.Forms.DataGridView>コントロールには、その基本的な外観と動作を変更するためのさまざまな方法が用意されています。 詳細については、次を参照してください。 [Windows フォームの DataGridView コントロールのセル スタイル](cell-styles-in-the-windows-forms-datagridview-control.md)します。  
  
### <a name="scenario-key-points"></a>シナリオの要点  
  
-   <xref:System.Windows.Forms.DataGridViewCellStyle> オブジェクトを使用して、色、フォント、書式設定、および複数のレベルと、コントロールの個々 の要素の位置情報を提供できます。  
  
-   セル スタイルを階層化し、コードを再利用することができます、複数の要素によって共有されることができます。  
  
## <a name="scenario-6-advanced-customization"></a>シナリオ 6:高度なカスタマイズ  
 <xref:System.Windows.Forms.DataGridView>コントロールの外観と動作をカスタマイズするためのさまざまな方法を提供します。  
  
### <a name="scenario-key-points"></a>シナリオの要点  
  
-   セルの描画コードを行うことができます。 詳細については、「[方法 :Windows フォームの DataGridView コントロール内のセルの外観をカスタマイズ](customize-the-appearance-of-cells-in-the-datagrid.md)します。  
  
-   独自の行の描画を行うことができます。 たとえば、複数の列にまたがるコンテンツを含む行を作成するこれは、役立ちます。 詳細については、「[方法 :Windows フォームの DataGridView コントロール内の行の外観をカスタマイズ](customize-the-appearance-of-rows-in-the-datagrid.md)します。  
  
-   セルの外観をカスタマイズする、独自のセルと列のクラスを実装することができます。 詳細については、「[方法 :セルのカスタマイズし、列で、Windows フォーム DataGridView コントロールのそれぞれの動作と外観を拡張することによって](customize-cells-and-columns-in-the-datagrid-by-extending-behavior.md)します。  
  
-   組み込みの列の型によって提供されるもの以外のホスト コントロールに、独自のセルと列のクラスを実装することができます。 詳細については、「[方法 :Windows フォーム DataGridView Cells コントロールをホスト](how-to-host-controls-in-windows-forms-datagridview-cells.md)します。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.DataGridView>
- [DataGridView コントロールの概要](datagridview-control-overview-windows-forms.md)
