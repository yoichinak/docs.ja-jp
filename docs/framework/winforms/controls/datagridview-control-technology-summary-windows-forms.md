---
title: DataGridView コントロール テクノロジの概要 (Windows フォーム)
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], about DataGridView control
- data grids [Windows Forms], about data grids
ms.assetid: 094498c3-a126-4a3f-83fe-f69e96c7717b
ms.openlocfilehash: ca8268137f2a154c782388d0f13cdd02504cbb64
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59217420"
---
# <a name="datagridview-control-technology-summary-windows-forms"></a>DataGridView コントロール テクノロジの概要 (Windows フォーム)
ここでは、`DataGridView` コントロールおよびその使用をサポートしているクラスの概要について説明します。  
  
 表形式でデータの表示は、頻繁に実行する可能性がありますで行います。 `DataGridView`コントロールは完全なソリューションをグリッドにデータを表示するために設計されています。  
  
## <a name="keywords"></a>キーワード  
 DataGridView、BindingSource、テーブル、セル、データ バインド、仮想モード  
  
## <a name="namespaces"></a>名前空間  
 <xref:System.Windows.Forms?displayProperty=nameWithType>  
  
 <xref:System.Data?displayProperty=nameWithType>  
  
## <a name="related-technologies"></a>関連技術  
 `BindingSource`  
  
## <a name="background"></a>背景  
 ユーザー インターフェイス (UI) デザイナー頻繁が必要なユーザーに表形式のデータを表示します。 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]テーブルまたはグリッドにデータを表示するいくつかの方法を提供します。 `DataGridView`コントロールは、Windows フォーム アプリケーションには、このテクノロジの最新の進化を表します。  
  
 `DataGridView`コントロールがデータ ストアからのデータの行を表示できます。 多くの種類のデータ ストアがサポートされています。 1 次元の配列などの単純な型指定されていないデータを保持できるデータ ストアまたは型指定されたデータを保持できるよう、<xref:System.Data.DataSet>します。 詳細については、「[方法 :バインド データを Windows フォーム DataGridView コントロール](how-to-bind-data-to-the-windows-forms-datagridview-control.md)します。  
  
 `DataGridView` コントロールには、データを表形式で表示するための強力で柔軟な機能が用意されています。 コントロールを使用すると、非常に大規模な小さなデータ セットの読み取り専用または編集可能なビューを表示します。  
  
 拡張することができます、`DataGridView`をアプリケーションにカスタム動作を構築するためにいくつかの方法で制御します。 たとえば、プログラムで独自の並べ替えアルゴリズムを指定したり、独自の種類のセルを作成したりできます。 `DataGridView` コントロールの外観は、いくつかのプロパティを選択することで簡単にカスタマイズできます。 多くの種類のデータ ストアをデータ ソースとして使用できますか、`DataGridView`にバインドされたデータ ソースなしコントロールで動作できます。  
  
## <a name="implementing-datagridview-classes"></a>DataGridView のクラスを実装します。  
 いくつかの方法を活用するための`DataGridView`コントロールの拡張機能。 イベントのプロパティを使用してコントロールの多くの側面をカスタマイズすることができますが、一部のカスタマイズでは、既存のものから派生した新しいクラスを作成する必要があります`DataGridView`クラス。  
  
 一般的に使用される基本クラスは`DataGridViewCell`と`DataGridViewColumn`します。 独自のセル クラスを派生する`DataGridViewCell`またはその子クラスのいずれか。 任意のセルの種類を追加するには任意の列は通常も派生する列のコンパニオン クラスから`DataGridViewColumn`既定では、カスタムのセルの種類のセルをホストします。  
  
 実装することができます、`IDataGridViewEditingCell`編集機能が編集モードでコントロールをホストしていないセルの種類を作成するには、派生セル クラスのインターフェイス。 編集モードのセルでホストできるコントロールを作成するには、実装することができます、`IDataGridViewEditingControl`から派生したクラスでインターフェイス<xref:System.Windows.Forms.Control>します。  
  
 詳細については、「[方法 :セルのカスタマイズし、列で、Windows フォーム DataGridView コントロールのそれぞれの動作と外観を拡張することによって](customize-cells-and-columns-in-the-datagrid-by-extending-behavior.md)と[方法。Windows フォーム DataGridView Cells コントロールをホスト](how-to-host-controls-in-windows-forms-datagridview-cells.md)します。  
  
## <a name="datagridview-classes-at-a-glance"></a>DataGridView のクラスの概要  
 <xref:System.Windows.Forms>  
  
|テクノロジ領域|クラス/インターフェイス/構成要素|  
|---------------------|-------------------------------------------------|  
|データ バインディング|<xref:System.Windows.Forms.BindingSource>|  
|データの表示|<xref:System.Windows.Forms.DataGridView><br /><br /> <xref:System.Windows.Forms.DataGridViewCell> クラスと派生クラス<br /><br /> <xref:System.Windows.Forms.DataGridViewRow> クラスと派生クラス<br /><br /> <xref:System.Windows.Forms.DataGridViewColumn> クラスと派生クラス<br /><br /> <xref:System.Windows.Forms.DataGridViewCellStyle>|  
|<xref:System.Windows.Forms.DataGridView> 機能拡張|<xref:System.Windows.Forms.DataGridViewCell> クラスと派生クラス<br /><br /> <xref:System.Windows.Forms.DataGridViewColumn> クラスと派生クラス<br /><br /> <xref:System.Windows.Forms.IDataGridViewEditingCell><br /><br /> <xref:System.Windows.Forms.IDataGridViewEditingControl>|  
  
## <a name="whats-new"></a>新機能  
 <xref:System.Windows.Forms.DataGridView>コントロールは表形式データを Windows フォームを表示するための完全なソリューションとして設計されています。 使用を検討する必要があります、<xref:System.Windows.Forms.DataGridView>など、他のソリューションの前に制御<xref:System.Windows.Forms.DataGrid>、新しいアプリケーションを作成する場合。 詳細については、「[Windows フォームの DataGridView コントロールと DataGrid コントロールの違いについて](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md)」を参照してください。  
  
 <xref:System.Windows.Forms.DataGridView>コントロールが閉じると組み合わせて動作できます、<xref:System.Windows.Forms.BindingSource>コンポーネント。 このコンポーネントは、フォームのプライマリ データ ソースとして設計されています。 間の相互作用を管理できる、<xref:System.Windows.Forms.DataGridView>コントロールとデータに関係なく、データ ソースのソースの種類。  
  
## <a name="see-also"></a>関連項目

- [DataGridView コントロールの概要 (Windows フォーム)](datagridview-control-overview-windows-forms.md)
- [DataGridView コントロールのアーキテクチャ](datagridview-control-architecture-windows-forms.md)
- [接続情報の保護](../../data/adonet/protecting-connection-information.md)
