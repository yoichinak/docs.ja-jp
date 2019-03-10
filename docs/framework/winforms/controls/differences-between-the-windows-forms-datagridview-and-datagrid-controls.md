---
title: Windows フォームの DataGridView コントロールと DataGrid コントロールの違いについて
ms.date: 03/30/2017
helpviewer_keywords:
- data grids [Windows Forms
- DataGrid control [Windows Forms], DataGridView control compared
- DataGridView control [Windows Forms], DataGrid control compared
ms.assetid: d412c786-140e-4210-8a56-a68467530a55
ms.openlocfilehash: b7d97431bfdbdafd5e87bfbfb9c5badd9ba273ea
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/09/2019
ms.locfileid: "57720489"
---
# <a name="differences-between-the-windows-forms-datagridview-and-datagrid-controls"></a>Windows フォームの DataGridView コントロールと DataGrid コントロールの違いについて
<xref:System.Windows.Forms.DataGridView>コントロールは、新しいコントロールを置き換える、<xref:System.Windows.Forms.DataGrid>コントロール。 <xref:System.Windows.Forms.DataGridView>コントロールで不足している多数の基本と高度な機能を提供する、<xref:System.Windows.Forms.DataGrid>コントロール。 アーキテクチャではさらに、<xref:System.Windows.Forms.DataGridView>コントロールにより、簡単に拡張およびカスタマイズよりも、<xref:System.Windows.Forms.DataGrid>コントロール。  
  
 次の表に、いくつかの主な機能で使用できる、<xref:System.Windows.Forms.DataGridView>の不足しているコントロール、<xref:System.Windows.Forms.DataGrid>コントロール。  
  
|DataGridView コントロールの機能|説明|  
|----------------------------------|-----------------|  
|複数の列の型|<xref:System.Windows.Forms.DataGridView>コントロールよりも多くの組み込みの列の型を提供する、<xref:System.Windows.Forms.DataGrid>コントロール。 これらの列型は、最も一般的なシナリオのニーズを満たすが、簡単に拡張または置換列型よりも、<xref:System.Windows.Forms.DataGrid>コントロール。 詳細については、次を参照してください。 [Windows フォームの DataGridView コントロールの列型](column-types-in-the-windows-forms-datagridview-control.md)します。|  
|複数のデータを表示する方法|<xref:System.Windows.Forms.DataGrid>外部データ ソースからデータを表示するときに、コントロールは制限されています。 <xref:System.Windows.Forms.DataGridView>コントロールは、コントロールや、バインドされたデータ ソースからデータ バインドとバインドされていないデータにまとめて格納されているバインドされていないデータを表示できます。 仮想モードを実装することも、<xref:System.Windows.Forms.DataGridView>カスタム データの管理を提供するコントロール。 詳細については、次を参照してください。 [Windows フォームの DataGridView コントロールでのデータ表示モード](data-display-modes-in-the-windows-forms-datagridview-control.md)します。|  
|複数のデータの表示をカスタマイズする方法|<xref:System.Windows.Forms.DataGridView>コントロールには、多くのプロパティおよびデータの書式設定し、表示方法を指定するためのイベントが用意されています。 たとえば、セル、行、および含まれるデータに依存する列の外観を変更するまたは別の型の同等のデータを 1 つのデータ型のデータを置き換えることができます。 詳細については、次を参照してください。 [Windows フォーム DataGridView コントロールでデータの書式設定](data-formatting-in-the-windows-forms-datagridview-control.md)します。|  
|セル、行、列、およびヘッダーの外観と動作を変更するための複数のオプション|<xref:System.Windows.Forms.DataGridView>コントロールでは、さまざまな方法でグリッドの個々 のコンポーネントを操作することができます。 たとえば、行と列をスクロールすることを防ぐことを固定できます。行、列、およびヘッダーを非表示にします。行、列、およびヘッダーのサイズが調整されている方法を変更します。項目を選択するようにする方法を変更します。個々 のセル、行、および列のツールヒントとショートカット メニューを提供します。|  
  
 <xref:System.Windows.Forms.DataGrid>と、旧バージョンとの互換性のための特別なニーズに合わせて、コントロールは保持されます。 ほぼすべての目的で使用する必要があります、<xref:System.Windows.Forms.DataGridView>コントロール。 使用できる唯一の機能、<xref:System.Windows.Forms.DataGrid>コントロールでは使用できませんが、<xref:System.Windows.Forms.DataGridView>コントロールが 1 つのコントロールで 2 つの関連テーブルからの情報の階層表示します。 2 つを使用する必要があります<xref:System.Windows.Forms.DataGridView>マスター/詳細リレーションシップに含まれる 2 つのテーブルから情報を表示するコントロール。  
  
## <a name="upgrading-to-the-datagridview-control"></a>DataGridView コントロールへのアップグレード  
 使用する既存のアプリケーションがある場合、<xref:System.Windows.Forms.DataGrid>コントロール カスタマイズなしの単純なデータ バインド シナリオで置き換えることができます単純に古いコントロール、新しいコントロール。 両方のコントロールを使用して、標準の Windows フォーム データ バインディング アーキテクチャ、<xref:System.Windows.Forms.DataGridView>コントロールは必要な追加構成なしで、バインドされたデータを表示します。 ただし、データ バインディングの向上、データをバインドすることによって利用を検討することもできます、<xref:System.Windows.Forms.BindingSource>にバインドすることができますし、コンポーネント、<xref:System.Windows.Forms.DataGridView>コントロール。 詳細については、次を参照してください。 [BindingSource コンポーネント](bindingsource-component.md)します。  
  
 <xref:System.Windows.Forms.DataGridView>コントロールが、まったく新しいアーキテクチャは、使用できる簡単な変換パスはありません<xref:System.Windows.Forms.DataGrid>とカスタマイズ、<xref:System.Windows.Forms.DataGridView>コントロール。 多く<xref:System.Windows.Forms.DataGrid>カスタマイズは必要では、<xref:System.Windows.Forms.DataGridView>制御、ただし、新しいコントロールで使用できる組み込みの機能が原因です。 カスタム列の型を作成した場合、<xref:System.Windows.Forms.DataGrid>で使用するコントロール、<xref:System.Windows.Forms.DataGridView>コントロール、もう一度新しいアーキテクチャを使用してそれらを実装する必要があります。 詳細については、次を参照してください。 [Windows フォーム DataGridView コントロールのカスタマイズ](customizing-the-windows-forms-datagridview-control.md)します。  
  
## <a name="see-also"></a>関連項目
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGrid>
- <xref:System.Windows.Forms.BindingSource>
- [DataGridView コントロール](datagridview-control-windows-forms.md)
- [DataGrid コントロール](datagrid-control-windows-forms.md)
- [BindingSource コンポーネント](bindingsource-component.md)
- [Windows フォーム DataGridView コントロールの列型](column-types-in-the-windows-forms-datagridview-control.md)
- [Windows フォーム DataGridView コントロールでのセルのスタイル](cell-styles-in-the-windows-forms-datagridview-control.md)
- [Windows フォーム DataGridView コントロールでのデータ表示モード](data-display-modes-in-the-windows-forms-datagridview-control.md)
- [Windows フォーム DataGridView コントロールでのデータの書式設定](data-formatting-in-the-windows-forms-datagridview-control.md)
- [Windows フォーム DataGridView コントロールのサイズ変更オプション](sizing-options-in-the-windows-forms-datagridview-control.md)
- [Windows フォーム DataGridView コントロール内の列の並べ替えモード](column-sort-modes-in-the-windows-forms-datagridview-control.md)
- [Windows フォーム DataGridView コントロールの選択モード](selection-modes-in-the-windows-forms-datagridview-control.md)
- [Windows フォーム DataGridView コントロールのカスタマイズ](customizing-the-windows-forms-datagridview-control.md)
