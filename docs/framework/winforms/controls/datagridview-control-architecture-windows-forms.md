---
title: DataGridView コントロールのアーキテクチャ (Windows フォーム)
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], architecture
ms.assetid: 1c6cabf0-02ee-4bbc-9574-b54bb7f5b19e
ms.openlocfilehash: d215eeaa367156c6228615a8f6e0a7f889efdf60
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/09/2019
ms.locfileid: "57713814"
---
# <a name="datagridview-control-architecture-windows-forms"></a>DataGridView コントロールのアーキテクチャ (Windows フォーム)
<xref:System.Windows.Forms.DataGridView>コントロールとその関連クラスが表示および表形式のデータを編集するための柔軟で拡張性の高いシステムで設計されています。 これらのクラスがすべてに含まれる、<xref:System.Windows.Forms?displayProperty=nameWithType>名前空間、およびそれらのすべてが"DataGridView"プレフィックスを持つという名前です。  
  
## <a name="architecture-elements"></a>アーキテクチャの要素  
 プライマリ<xref:System.Windows.Forms.DataGridView>コンパニオン クラスから派生<xref:System.Windows.Forms.DataGridViewElement>します。 次のオブジェクト モデルを示しています、<xref:System.Windows.Forms.DataGridViewElement>継承階層。  
  
 ![DataGridViewElement オブジェクト モデル](./media/datagridviewelement.gif "DataGridViewElement")  
DataGridViewElement オブジェクト モデル  
  
 <xref:System.Windows.Forms.DataGridViewElement>クラスは、親への参照を提供<xref:System.Windows.Forms.DataGridView>コントロールであり、<xref:System.Windows.Forms.DataGridViewElement.State%2A>プロパティの値の組み合わせを表す値を保持する、<xref:System.Windows.Forms.DataGridViewElementStates>列挙体。  
  
 次のセクションで説明します、<xref:System.Windows.Forms.DataGridView>コンパニオン クラスで詳しく説明します。  
  
### <a name="datagridviewelementstates"></a>DataGridViewElementStates  
 <xref:System.Windows.Forms.DataGridViewElementStates>列挙には、次の値が含まれています。  
  
-   <xref:System.Windows.Forms.DataGridViewElementStates.None>  
  
-   <xref:System.Windows.Forms.DataGridViewElementStates.Frozen>  
  
-   <xref:System.Windows.Forms.DataGridViewElementStates.ReadOnly>  
  
-   <xref:System.Windows.Forms.DataGridViewElementStates.Resizable>  
  
-   <xref:System.Windows.Forms.DataGridViewElementStates.ResizableSet>  
  
-   <xref:System.Windows.Forms.DataGridViewElementStates.Selected>  
  
-   <xref:System.Windows.Forms.DataGridViewElementStates.Visible>  
  
 この列挙体の値はビットごとの論理演算子と組み合わせることができますので、<xref:System.Windows.Forms.DataGridViewElement.State%2A>プロパティは、一度に 1 つ以上の状態を表すことができます。 たとえば、<xref:System.Windows.Forms.DataGridViewElement>同時に実行できる<xref:System.Windows.Forms.DataGridViewElementStates.Frozen>、<xref:System.Windows.Forms.DataGridViewElementStates.Selected>と<xref:System.Windows.Forms.DataGridViewElementStates.Visible>します。  
  
### <a name="cells-and-bands"></a>セルとバンド  
 <xref:System.Windows.Forms.DataGridView>コントロールには 2 つの基本的な種類のオブジェクトが構成されます。 セルとバンド。 すべてのセルから派生して、<xref:System.Windows.Forms.DataGridViewCell>基本クラス。 2 つの種類、バンドの<xref:System.Windows.Forms.DataGridViewColumn>と<xref:System.Windows.Forms.DataGridViewRow>から派生両方、<xref:System.Windows.Forms.DataGridViewBand>基本クラス。  
  
 <xref:System.Windows.Forms.DataGridView>コントロールがいくつかのクラスと相互運用が、最も一般的に見られるは<xref:System.Windows.Forms.DataGridViewCell>、 <xref:System.Windows.Forms.DataGridViewColumn>、および<xref:System.Windows.Forms.DataGridViewRow>します。  
  
### <a name="datagridviewcell"></a>DataGridViewCell  
 セルがの相互作用の基本的な単位、<xref:System.Windows.Forms.DataGridView>します。 表示が、セルの中央に配置し、多くの場合、データ エントリはセルを実行します。 使用してセルにアクセスすることができます、<xref:System.Windows.Forms.DataGridViewRow.Cells%2A>のコレクション、<xref:System.Windows.Forms.DataGridViewRow>を使用して、選択したセルにアクセスできるクラスとする、<xref:System.Windows.Forms.DataGridView.SelectedCells%2A>のコレクション、<xref:System.Windows.Forms.DataGridView>コントロール。 この使用方法とを示しています、次のオブジェクト モデル、<xref:System.Windows.Forms.DataGridViewCell>継承階層。  
  
 ![DataGridViewCell オブジェクト モデル](./media/datagridviewcell.gif "DataGridViewCell")  
DataGridViewCell オブジェクト モデル  
  
 <xref:System.Windows.Forms.DataGridViewCell>型はすべてのセルの型の派生元となる抽象基本クラス。 <xref:System.Windows.Forms.DataGridViewCell> その派生型は、Windows フォーム コントロールが一部のホスト Windows フォーム コントロール。 セルの数式でサポートされている編集機能は通常、ホストされるコントロールによって処理されます。  
  
 <xref:System.Windows.Forms.DataGridViewCell> オブジェクトは制御されません、独自の外観と描画機能と同じ方法で Windows フォーム コントロールとして。 代わりに、<xref:System.Windows.Forms.DataGridView>の外観は、その<xref:System.Windows.Forms.DataGridViewCell>オブジェクト。 操作することで大幅にセルの動作と外観に影響することができます、<xref:System.Windows.Forms.DataGridView>コントロールのプロパティおよびイベント。 機能を超えているカスタマイズ用の特別な要件がある場合、<xref:System.Windows.Forms.DataGridView>コントロールから派生した独自のクラスを実装する<xref:System.Windows.Forms.DataGridViewCell>またはその子クラスの 1 つ。  
  
 次の一覧から派生したクラスを示しています<xref:System.Windows.Forms.DataGridViewCell>:。  
  
-   <xref:System.Windows.Forms.DataGridViewTextBoxCell>  
  
-   <xref:System.Windows.Forms.DataGridViewButtonCell>  
  
-   <xref:System.Windows.Forms.DataGridViewLinkCell>  
  
-   <xref:System.Windows.Forms.DataGridViewCheckBoxCell>  
  
-   <xref:System.Windows.Forms.DataGridViewComboBoxCell>  
  
-   <xref:System.Windows.Forms.DataGridViewImageCell>  
  
-   <xref:System.Windows.Forms.DataGridViewHeaderCell>  
  
-   <xref:System.Windows.Forms.DataGridViewRowHeaderCell>  
  
-   <xref:System.Windows.Forms.DataGridViewColumnHeaderCell>  
  
-   <xref:System.Windows.Forms.DataGridViewTopLeftHeaderCell>  
  
-   カスタムのセルの種類を  
  
### <a name="datagridviewcolumn"></a>DataGridViewColumn  
 スキーマ、<xref:System.Windows.Forms.DataGridView>でコントロールの接続されたデータ ストアが表される、<xref:System.Windows.Forms.DataGridView>コントロールの列。 アクセスできる、<xref:System.Windows.Forms.DataGridView>コントロールの列を使用して、<xref:System.Windows.Forms.DataGridView.Columns%2A>コレクション。 選択した列を使用してアクセスすることができます、<xref:System.Windows.Forms.DataGridView.SelectedColumns%2A>コレクション。 この使用方法とを示しています、次のオブジェクト モデル、<xref:System.Windows.Forms.DataGridViewColumn>継承階層。  
  
 ![DataGridViewColumn オブジェクト モデル](./media/datagridviewcolumn.gif "DataGridViewColumn")  
DataGridViewColumn オブジェクト モデル  
  
 一部のキーのセルの種類はある対応する列の種類です。 これらから派生、<xref:System.Windows.Forms.DataGridViewColumn>基本クラス。  
  
 次の一覧から派生したクラスを示しています<xref:System.Windows.Forms.DataGridViewColumn>:。  
  
-   <xref:System.Windows.Forms.DataGridViewButtonColumn>  
  
-   <xref:System.Windows.Forms.DataGridViewCheckBoxColumn>  
  
-   <xref:System.Windows.Forms.DataGridViewComboBoxColumn>  
  
-   <xref:System.Windows.Forms.DataGridViewImageColumn>  
  
-   <xref:System.Windows.Forms.DataGridViewTextBoxColumn>  
  
-   <xref:System.Windows.Forms.DataGridViewLinkColumn>  
  
-   カスタム列の型  
  
### <a name="datagridview-editing-controls"></a>DataGridView 編集コントロール  
 通常は高度な編集機能をサポートしているセルは、Windows フォーム コントロールから派生したホストされるコントロールを使用します。 これらのコントロールの実装も、<xref:System.Windows.Forms.IDataGridViewEditingControl>インターフェイス。 次のオブジェクト モデルでは、これらのコントロールの使用方法を示します。  
  
 ![DataGridView コントロールのオブジェクト モデルを編集](./media/datagridviewediting.gif "DataGridViewEditing")  
DataGridView 編集コントロール オブジェクト モデル  
  
 次の編集コントロールが付属、<xref:System.Windows.Forms.DataGridView>コントロール。  
  
-   <xref:System.Windows.Forms.DataGridViewComboBoxEditingControl>  
  
-   <xref:System.Windows.Forms.DataGridViewTextBoxEditingControl>  
  
 独自の編集コントロールを作成する方法の詳細については、次を参照してください。[方法。Windows フォーム DataGridView Cells コントロールをホスト](how-to-host-controls-in-windows-forms-datagridview-cells.md)します。  
  
 次の表は、セルの種類を列の種類、および編集コントロール間の関係を示しています。  
  
|セルの種類|ホストされるコントロール|列の型|  
|---------------|--------------------|-----------------|  
|<xref:System.Windows.Forms.DataGridViewButtonCell>|N/A|<xref:System.Windows.Forms.DataGridViewButtonColumn>|  
|<xref:System.Windows.Forms.DataGridViewCheckBoxCell>|該当なし|<xref:System.Windows.Forms.DataGridViewCheckBoxColumn>|  
|<xref:System.Windows.Forms.DataGridViewComboBoxCell>|<xref:System.Windows.Forms.DataGridViewComboBoxEditingControl>|<xref:System.Windows.Forms.DataGridViewComboBoxColumn>|  
|<xref:System.Windows.Forms.DataGridViewImageCell>|該当なし|<xref:System.Windows.Forms.DataGridViewImageColumn>|  
|<xref:System.Windows.Forms.DataGridViewLinkCell>|N/A|<xref:System.Windows.Forms.DataGridViewLinkColumn>|  
|<xref:System.Windows.Forms.DataGridViewTextBoxCell>|<xref:System.Windows.Forms.DataGridViewTextBoxEditingControl>|<xref:System.Windows.Forms.DataGridViewTextBoxColumn>|  
  
### <a name="datagridviewrow"></a>DataGridViewRow  
 <xref:System.Windows.Forms.DataGridViewRow>をクラスの表示、レコードのデータ フィールドのデータを格納、<xref:System.Windows.Forms.DataGridView>コントロールをアタッチします。 アクセスできる、<xref:System.Windows.Forms.DataGridView>コントロールの行を使用して、<xref:System.Windows.Forms.DataGridView.Rows%2A>コレクション。 選択した行を使用してアクセスすることができます、<xref:System.Windows.Forms.DataGridView.SelectedRows%2A>コレクション。 この使用方法とを示しています、次のオブジェクト モデル、<xref:System.Windows.Forms.DataGridViewRow>継承階層。  
  
 ![DataGridViewRow オブジェクト モデル](./media/datagridviewrow.gif "DataGridViewRow")  
DataGridViewRow オブジェクト モデル  
  
 独自の型を派生させることができます、<xref:System.Windows.Forms.DataGridViewRow>クラスが、これは通常不要になります。 <xref:System.Windows.Forms.DataGridView>コントロールがいくつかの行に関連するイベントおよびプロパティの動作をカスタマイズするため、<xref:System.Windows.Forms.DataGridViewRow>オブジェクト。  
  
 有効にした場合、<xref:System.Windows.Forms.DataGridView>コントロールの<xref:System.Windows.Forms.DataGridView.AllowUserToAddRows%2A>プロパティ、新しい行を追加するための特別な行は、最後の行として表示されます。 この行の一部である、<xref:System.Windows.Forms.DataGridView.Rows%2A>が、コレクションが特別な機能に対処することがあります。 詳細については、次を参照してください。 [Windows フォームの DataGridView コントロールにおける新規レコードの行を使用して](using-the-row-for-new-records-in-the-windows-forms-datagridview-control.md)します。  
  
## <a name="see-also"></a>関連項目
- [DataGridView コントロールの概要](datagridview-control-overview-windows-forms.md)
- [Windows フォーム DataGridView コントロールのカスタマイズ](customizing-the-windows-forms-datagridview-control.md)
- [Windows フォーム DataGridView コントロールにおける新規レコード行の使用](using-the-row-for-new-records-in-the-windows-forms-datagridview-control.md)
