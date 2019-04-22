---
title: Windows フォーム DataGridView コントロールでの仮想モード
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], virtual mode
ms.assetid: feae5d43-2848-4b1a-8ea7-77085dc415b5
ms.openlocfilehash: f284835578221ad1fe859f260e37bb829cd64b2d
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59124723"
---
# <a name="virtual-mode-in-the-windows-forms-datagridview-control"></a>Windows フォーム DataGridView コントロールでの仮想モード
仮想モードの間の相互作用を管理することができます、<xref:System.Windows.Forms.DataGridView>コントロールとカスタム データ キャッシュします。 仮想モードを実装するには、設定、<xref:System.Windows.Forms.DataGridView.VirtualMode%2A>プロパティを`true`し、このトピックで説明されているイベントの 1 つ以上を処理します。 通常は、少なくとも`CellValueNeeded`イベントで、データ キャッシュ内の値をコントロールの外観を有効します。  
  
## <a name="bound-mode-and-virtual-mode"></a>バインド モードと仮想モード  
 仮想モードは、バインド モードを補完したりする必要がある場合にのみ必要があります。 バインドのモードでは設定、<xref:System.Windows.Forms.DataGridView.DataSource%2A>プロパティ、およびコントロールを自動的に、指定したソースからデータを読み込み、返送にユーザーが変更を送信します。 データ ソース自体が通常の並べ替えなどの操作を処理し、バインドされた列の表示を制御できます。  
  
## <a name="supplementing-bound-mode"></a>バインド モードの補完  
 バインド モードは、バインドされた列とバインドされていない列を表示することで補うことができます。 これ「混合モード」とも呼ばれますが、計算値またはユーザー インターフェイス (UI) の制御などを表示するために便利です。  
  
 バインドされていない列では、データ ソースの外部であるために、データ ソースの並べ替え操作では無視されます。 そのため、混在モードでの並べ替えを有効にするとローカル キャッシュ内でバインドされていないデータを管理してさせる仮想モードを実装、<xref:System.Windows.Forms.DataGridView>コントロールを操作します。  
  
 仮想モードを使用して、非バインド列の値を維持する方法の詳細については、例を参照してください、<xref:System.Windows.Forms.DataGridViewCheckBoxColumn.ThreeState%2A?displayProperty=nameWithType>プロパティと<xref:System.Windows.Forms.DataGridViewComboBoxColumn?displayProperty=nameWithType>クラスのリファレンス トピック。  
  
## <a name="replacing-bound-mode"></a>バインド モードの置換  
 バインド モードが、パフォーマンスのニーズを満たしていない場合は、仮想モードのイベント ハンドラーを使用して、カスタム キャッシュ内のすべてのデータを管理できます。 ジャストイン タイム データのみを取得するメカニズムの読み込みを実装するために仮想モードを使用するなど、ネットワーク上のデータベースからデータが最適なパフォーマンスが必要です。 このシナリオは、低速ネットワーク接続経由でデータ量が多いと RAM または記憶域スペースの制限があるクライアント コンピューターを操作する場合に特に役立ちます。  
  
 ジャストイン タイムのシナリオで仮想モードの使用に関する詳細については、次を参照してください。 [Windows フォームの DataGridView コントロールで Just-In-Time データ読み込みで仮想モードの実装](implementing-virtual-mode-jit-data-loading-in-the-datagrid.md)します。  
  
## <a name="virtual-mode-events"></a>仮想モードのイベント  
 データが読み取り専用である場合、`CellValueNeeded`イベントが唯一のイベントを処理する必要があります。 仮想モードの追加のイベントでは、ユーザーを編集する、行の追加と削除、および行レベルのトランザクションなど特定の機能を有効にできます。  
  
 標準的な<xref:System.Windows.Forms.DataGridView>イベント (など、ユーザー追加の行を削除またはセルの値が場合に発生するイベントは、編集、解析、検証、または書式設定されます) の指定は、仮想モードに役立ちます。 通常はセルのツールヒント テキスト、セルと行のエラー テキスト、セルと行のショートカット メニューのデータ、および行の高さデータなど、バインドされたデータ ソースに格納された値を保持できるようにするイベントを処理することもできます。  
  
 行レベルのコミットのスコープを持つ読み取り/書き込みデータを管理する仮想モードの実装の詳細については、次を参照してください。[チュートリアル。仮想モードの実装で、Windows フォーム DataGridView コントロール](implementing-virtual-mode-wf-datagridview-control.md)します。  
  
 セル レベルのコミットのスコープを使用して仮想モードを実装する例を参照してください、<xref:System.Windows.Forms.DataGridView.VirtualMode%2A>プロパティの参照トピック。  
  
 次のイベントにのみ発生するときに、<xref:System.Windows.Forms.DataGridView.VirtualMode%2A>プロパティに設定されて`true`します。  
  
|event|説明|  
|-----------|-----------------|  
|<xref:System.Windows.Forms.DataGridView.CellValueNeeded>|表示用のデータ キャッシュからのセル値を取得するコントロールで使用します。 このイベントは、バインドされていない列のセルに対してのみ発生します。|  
|<xref:System.Windows.Forms.DataGridView.CellValuePushed>|セルのユーザー入力をデータ キャッシュにコミットするためのコントロールで使用します。 このイベントは、バインドされていない列のセルに対してのみ発生します。<br /><br /> 呼び出す、<xref:System.Windows.Forms.DataGridView.UpdateCellValue%2A>メソッド以外のキャッシュされた値を変更するときに、<xref:System.Windows.Forms.DataGridView.CellValuePushed>イベント ハンドラーの現在の値をコントロールに表示されるようにして、現時点で有効には、すべての自動サイズ変更モードを適用します。|  
|<xref:System.Windows.Forms.DataGridView.NewRowNeeded>|データ キャッシュ内の新しい行の必要性を示すために、コントロールで使用します。|  
|<xref:System.Windows.Forms.DataGridView.RowDirtyStateNeeded>|行にコミットされていない変更があるかどうかを決定するコントロールで使用します。|  
|<xref:System.Windows.Forms.DataGridView.CancelRowEdit>|コントロールで使用を示す行が、キャッシュされた値に戻る必要があります。|  
  
 次のイベントは仮想モードでは役立ちますに関係なく使用できます、<xref:System.Windows.Forms.DataGridView.VirtualMode%2A>プロパティの設定。  
  
|イベント|説明|  
|------------|-----------------|  
|<xref:System.Windows.Forms.DataGridView.UserDeletingRow><br /><br /> <xref:System.Windows.Forms.DataGridView.UserDeletedRow><br /><br /> <xref:System.Windows.Forms.DataGridView.RowsRemoved><br /><br /> <xref:System.Windows.Forms.DataGridView.RowsAdded>|ときに行が削除されるか、データ キャッシュを適宜更新する、追加のことを示す、コントロールで使用します。|  
|<xref:System.Windows.Forms.DataGridView.CellFormatting><br /><br /> <xref:System.Windows.Forms.DataGridView.CellParsing><br /><br /> <xref:System.Windows.Forms.DataGridView.CellValidating><br /><br /> <xref:System.Windows.Forms.DataGridView.CellValidated><br /><br /> <xref:System.Windows.Forms.DataGridView.RowValidating><br /><br /> <xref:System.Windows.Forms.DataGridView.RowValidated>|表示とを解析し、ユーザー入力を検証するには、セルの値を書式設定するコントロールによって使用されます。|  
|<xref:System.Windows.Forms.DataGridView.CellToolTipTextNeeded>|セルのツールヒント テキストを取得する、コントロールによって使用されるときに、<xref:System.Windows.Forms.DataGridView.DataSource%2A>プロパティを設定または<xref:System.Windows.Forms.DataGridView.VirtualMode%2A>プロパティは`true`します。<br /><br /> セルのツールヒントが表示される場合にのみ、<xref:System.Windows.Forms.DataGridView.ShowCellToolTips%2A>プロパティの値が`true`します。|  
|<xref:System.Windows.Forms.DataGridView.CellErrorTextNeeded><br /><br /> <xref:System.Windows.Forms.DataGridView.RowErrorTextNeeded>|セルまたは行のエラー テキストを取得する、コントロールによって使用されるときに、<xref:System.Windows.Forms.DataGridView.DataSource%2A>プロパティを設定または<xref:System.Windows.Forms.DataGridView.VirtualMode%2A>プロパティは`true`します。<br /><br /> 呼び出す、<xref:System.Windows.Forms.DataGridView.UpdateCellErrorText%2A>メソッドまたは<xref:System.Windows.Forms.DataGridView.UpdateRowErrorText%2A>メソッド、現在の値をコントロールに表示されるようにするセルまたは行のエラー テキストを変更するとします。<br /><br /> セルと行のエラー グリフが表示されるときに、<xref:System.Windows.Forms.DataGridView.ShowCellErrors%2A>と<xref:System.Windows.Forms.DataGridView.ShowRowErrors%2A>プロパティの値は`true`します。|  
|<xref:System.Windows.Forms.DataGridView.CellContextMenuStripNeeded><br /><br /> <xref:System.Windows.Forms.DataGridView.RowContextMenuStripNeeded>|セルまたは行を取得する、コントロールによって使用される<xref:System.Windows.Forms.ContextMenuStrip>ときにコントロール<xref:System.Windows.Forms.DataGridView.DataSource%2A>プロパティを設定または<xref:System.Windows.Forms.DataGridView.VirtualMode%2A>プロパティは`true`します。|  
|<xref:System.Windows.Forms.DataGridView.RowHeightInfoNeeded><br /><br /> <xref:System.Windows.Forms.DataGridView.RowHeightInfoPushed>|データ キャッシュ内の行の高さ情報を格納または取得するコントロールで使用します。 呼び出す、<xref:System.Windows.Forms.DataGridView.UpdateRowHeightInfo%2A>メソッド以外のキャッシュされた行の高さ情報を変更するときに、<xref:System.Windows.Forms.DataGridView.RowHeightInfoPushed>イベント ハンドラーを現在の値がコントロールの表示で使用されるようにします。|  
  
## <a name="best-practices-in-virtual-mode"></a>仮想モードでのベスト プラクティス  
 大量のデータを効率的に使用するには仮想モードを実装する場合、使用効率的にしていることを確認するはも、<xref:System.Windows.Forms.DataGridView>コントロール自体。 セルのスタイル、自動サイズ変更、選択内容、および行の共有の効率的な使用の詳細については、次を参照してください。 [Windows フォーム DataGridView コントロールを拡張するためのベスト プラクティス](best-practices-for-scaling-the-windows-forms-datagridview-control.md)します。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.VirtualMode%2A>
- [Windows フォーム DataGridView コントロールでのパフォーマンス チューニング](performance-tuning-in-the-windows-forms-datagridview-control.md)
- [Windows フォーム DataGridView コントロールを拡張するための推奨される手順](best-practices-for-scaling-the-windows-forms-datagridview-control.md)
- [チュートリアル: Windows フォームの DataGridView コントロールで仮想モードの実装](implementing-virtual-mode-wf-datagridview-control.md)
- [Windows フォーム DataGridView コントロールでの Just-In-Time データ読み込みによる仮想モードの実装](implementing-virtual-mode-jit-data-loading-in-the-datagrid.md)
