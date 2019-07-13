---
title: Windows フォーム DataGridView コントロールでのデータ表示モード
ms.date: 03/30/2017
helpviewer_keywords:
- data [Windows Forms], display modes
- data grids [Windows Forms], display modes
- DataGridView control [Windows Forms], display modes
ms.assetid: 9755a030-3f3f-4705-a661-ba5a48a81875
ms.openlocfilehash: 673780909f6d66168548893e99d79bbfec70a0e0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62011426"
---
# <a name="data-display-modes-in-the-windows-forms-datagridview-control"></a>Windows フォーム DataGridView コントロールでのデータ表示モード
<xref:System.Windows.Forms.DataGridView>コントロールは、次の 3 つの異なるモードでデータを表示することができます。 バインド、バインドされていない、および仮想です。 要件に基づいて最も適したモードを選択します。  
  
## <a name="unbound"></a>バインドされていません。  
 非バインド モードは、比較的少量のプログラムで管理するデータを表示するために適しています。 アタッチしない、<xref:System.Windows.Forms.DataGridView>バインド モードのようにデータ ソースへの直接制御します。 代わりに、必要があります設定するコントロールを自分で通常を使用して、<xref:System.Windows.Forms.DataGridViewRowCollection.Add%2A?displayProperty=nameWithType>メソッド。  
  
 非バインド モードは、静的な読み取り専用のデータ、または外部データ ストアと対話するコードを指定する場合に便利にできます。 外部データ ソースとの対話をユーザーにする場合は、ただしは通常モードを使用するバインド。  
  
 読み取り専用に使用する例については、バインドされていない<xref:System.Windows.Forms.DataGridView>を参照してください[方法。バインドされていない Windows フォーム DataGridView コントロールの作成](how-to-create-an-unbound-windows-forms-datagridview-control.md)です。  
  
## <a name="bound"></a>バインドされています。  
 バインド モードは、データ ストアと自動の操作を使用してデータを管理するために適しています。 アタッチすることができます、<xref:System.Windows.Forms.DataGridView>コントロールを設定してそのデータ ソースに直接、<xref:System.Windows.Forms.DataGridView.DataSource%2A>プロパティ。 コントロールがバインドされたデータの場合は、データ行はプッシュし、プル ユーザー側で明示的に管理する必要がありません。 ときに、<xref:System.Windows.Forms.DataGridView.AutoGenerateColumns%2A>プロパティは`true`、データ ソース内の各列は、コントロール内に作成する対応する列になります。 このプロパティを設定するには、独自の列を作成する場合は、`false`を使用して、<xref:System.Windows.Forms.DataGridViewColumn.DataPropertyName%2A>プロパティを構成するときに、各列をバインドします。 これは、既定で生成される型以外の列の型を使用する場合に便利です。 詳細については、次を参照してください。 [Windows フォームの DataGridView コントロールの列型](column-types-in-the-windows-forms-datagridview-control.md)します。  
  
 バインドされたを使用する例については<xref:System.Windows.Forms.DataGridView>コントロールを参照してください[チュートリアル。フォームの DataGridView コントロールを Windows のデータの検証](walkthrough-validating-data-in-the-windows-forms-datagridview-control.md)です。  
  
 バインドされていない列を追加することも、<xref:System.Windows.Forms.DataGridView>バインド モードで制御します。 これは、特定の行に対して操作を実行するユーザーを有効にするボタンやリンクの列を表示する場合に便利です。 バインドされた列から計算された値を持つ列を表示すると便利です。 ハンドラーで計算列のセル値を設定することができます、<xref:System.Windows.Forms.DataGridView.CellFormatting>イベント。 使用する場合、<xref:System.Data.DataSet>または<xref:System.Data.DataTable>データ ソースとしてただしが使用する、<xref:System.Data.DataColumn.Expression%2A?displayProperty=nameWithType>代わりに、計算列を作成するプロパティ。 ここで、<xref:System.Windows.Forms.DataGridView>コントロールは、データ ソースの他の任意の列と同じように計算列を扱います。  
  
 バインド モードでバインドされていない列による並べ替えはサポートされていません。 ユーザーが編集可能な値を含むバインド モードで非バインド列を作成する場合は、コントロールがバインドされた列で並べ替えられる場合は、これらの値を維持するために仮想モードを実装する必要があります。  
  
## <a name="virtual"></a>仮想  
 仮想モードでは、独自のデータ管理操作を実装できます。 これは、コントロールがバインドされた列で並べ替えられる場合は、バインド モードでバインドされていない列の値を維持するために必要です。 仮想モードの主な用途は、ただし、大量のデータを操作するときにパフォーマンスを最適化するためにです。  
  
 アタッチする、<xref:System.Windows.Forms.DataGridView>にキャッシュを管理するにコントロールとデータ行のプッシュし、プルの場合、コードを制御します。 メモリ フット プリントを小さく保つには、キャッシュが現在表示されている行の数ほぼ同じサイズにする必要があります。 ユーザーは、ビューに新しい行をスクロールするときに、コードはキャッシュから新しいデータを要求し、必要に応じて古いデータをメモリからフラッシュします。  
  
 仮想モードを実装するときは、新しい行が新しい行の追加をロールバックするときにデータ モデルを必要なときに追跡する必要があります。 この機能の正確な実装は、データ モデルの実装と、データ モデルのトランザクション セマンティクスに依存します。コミットのスコープがセルまたは行レベルでかどうか。  
  
 仮想モードの詳細については、次を参照してください。 [Windows フォームの DataGridView コントロールでの仮想モード](virtual-mode-in-the-windows-forms-datagridview-control.md)します。 仮想モードのイベントを使用する方法を示しますたとえば、次を参照してください。[チュートリアル。仮想モードの実装で、Windows フォーム DataGridView コントロール](implementing-virtual-mode-wf-datagridview-control.md)します。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.DataSource%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.VirtualMode%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.BindingSource>
- <xref:System.Windows.Forms.DataGridViewColumn.DataPropertyName%2A?displayProperty=nameWithType>
- [Windows フォーム DataGridView コントロールでのデータの表示](displaying-data-in-the-windows-forms-datagridview-control.md)
- [Windows フォーム DataGridView コントロールの列型](column-types-in-the-windows-forms-datagridview-control.md)
- [チュートリアル: 作成、バインドされていない Windows フォーム DataGridView コントロール](walkthrough-creating-an-unbound-windows-forms-datagridview-control.md)
- [方法: Windows フォームの DataGridView コントロールにデータをバインドします。](how-to-bind-data-to-the-windows-forms-datagridview-control.md)
- [Windows フォーム DataGridView コントロールでの仮想モード](virtual-mode-in-the-windows-forms-datagridview-control.md)
- [チュートリアル: Windows フォームの DataGridView コントロールで仮想モードの実装](implementing-virtual-mode-wf-datagridview-control.md)
