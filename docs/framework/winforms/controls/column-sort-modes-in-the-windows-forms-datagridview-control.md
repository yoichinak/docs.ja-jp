---
title: Windows フォーム DataGridView コントロール内の列の並べ替えモード
ms.date: 03/30/2017
helpviewer_keywords:
- data grids [Windows Forms], sort modes
- DataGridView control [Windows Forms], sort mode
ms.assetid: 43715887-2df9-4da7-bcf1-b9c7c842b2bf
ms.openlocfilehash: b8f6048946d367dd79b1ce0d23d84446ffdb1115
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61956222"
---
# <a name="column-sort-modes-in-the-windows-forms-datagridview-control"></a>Windows フォーム DataGridView コントロール内の列の並べ替えモード
<xref:System.Windows.Forms.DataGridView> 列では、次の 3 つの並べ替えモードがあります。 使用して各列の並べ替えモードを指定、<xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A>プロパティは、次のいずれかに設定することができる列の<xref:System.Windows.Forms.DataGridViewColumnSortMode>列挙値。  
  
|`DataGridViewColumnSortMode` の値|説明|  
|----------------------------------------|-----------------|  
|<xref:System.Windows.Forms.DataGridViewColumnSortMode.Automatic>|テキスト ボックスの列の既定値します。 選択範囲の列ヘッダーは使用しないと、列ヘッダーをクリックすると、自動的に並べ替えます、<xref:System.Windows.Forms.DataGridView>この列で並べ替え順序を示すグリフを表示します。|  
|<xref:System.Windows.Forms.DataGridViewColumnSortMode.NotSortable>|非テキスト ボックスの列の既定値します。 プログラムでこの列を並べ替えることができます。ただし、ものではありません、並べ替えのため、並べ替えグリフの領域が予約されていません。|  
|<xref:System.Windows.Forms.DataGridViewColumnSortMode.Programmatic>|プログラムでは、この列を並べ替えることができ、並べ替えグリフの領域を予約します。|  
  
 既定値は列の並べ替えモードを変更する<xref:System.Windows.Forms.DataGridViewColumnSortMode.NotSortable>明確注文可能な値が含まれている場合。 項目の状態を表す数値を含むデータベースの列があれば、たとえば、image 列をデータベース列にバインドすることによってこれらの数値として対応するアイコンに表示できます。 ハンドラーでイメージの表示値に数値のセルの値を変更し、<xref:System.Windows.Forms.DataGridView.CellFormatting?displayProperty=nameWithType>イベント。 この場合、設定、<xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A>プロパティを<xref:System.Windows.Forms.DataGridViewColumnSortMode.Automatic>列の並べ替えにユーザーを有効になります。 自動並べ替えにより、ユーザーは、番号に対応する状態が自然な順序を持っていない場合でも同じ状態になっているアイテムをグループ化します。 列のチェック ボックスは、自動並べ替えが同じ状態で項目をグループ化するために役立ちます別の例です。  
  
 並べ替えることができます、<xref:System.Windows.Forms.DataGridView>プログラムの任意の列またはに関係なく、複数の列の値によって、<xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A>設定します。 プログラムによる並べ替えは、並べ替え、独自のユーザー インターフェイス (UI) を提供する場合、またはカスタムの並べ替え機能を実装する場合に便利です。 並べ替えの UI は役立ちますが、提供するなど、設定すると、<xref:System.Windows.Forms.DataGridView>列ヘッダーの選択を有効にするモードを選択します。 ここでは、並べ替え、列ヘッダーを使用することはできませんするため、設定は、適切な並べ替えグリフを表示するヘッダー、<xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A>プロパティを<xref:System.Windows.Forms.DataGridViewColumnSortMode.Programmatic>します。  
  
 プログラムによる並べ替えモードに設定された列は、自動的に並べ替えグリフを表示しません。 これらの列にする必要があります、グリフ自分で設定して表示する、<xref:System.Windows.Forms.DataGridViewColumnHeaderCell.SortGlyphDirection%2A?displayProperty=nameWithType>プロパティ。 これは、カスタムの並べ替えを柔軟にする場合に必要です。 たとえば、並べ替える場合、<xref:System.Windows.Forms.DataGridView>を複数の列で複数の並べ替えグリフまたはない並べ替えグリフを表示したい場合があります。  
  
 プログラムで並べ替えることができますが、<xref:System.Windows.Forms.DataGridView>列を指定してボタンの列などのいくつかの列では、可能性がありますが含まれていない明確注文可能な値には。 これらの列に対して、<xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A>プロパティの設定の<xref:System.Windows.Forms.DataGridViewColumnSortMode.NotSortable>並べ替えグリフ用のヘッダー領域を予約する必要がないことには使用されず、並べ替えを示します。  
  
 ときに、<xref:System.Windows.Forms.DataGridView>は、並べ替えを指定できます、並べ替え列と並べ替え順序の両方の値をチェックして、<xref:System.Windows.Forms.DataGridView.SortedColumn%2A>と<xref:System.Windows.Forms.DataGridView.SortOrder%2A>プロパティ。 カスタムの並べ替え操作の後にこれらの値を意味することができません。 カスタムの並べ替えの詳細については、このトピックの「カスタムの並べ替え」を参照してください。  
  
 ときに、<xref:System.Windows.Forms.DataGridView>バインドとバインドされていない列を含むコントロールが並べ替えられ、非バインド列の値を自動的に維持することはできません。 これらの値を維持するために設定して仮想モードを実装する必要があります、<xref:System.Windows.Forms.DataGridView.VirtualMode%2A>プロパティを`true`と処理、<xref:System.Windows.Forms.DataGridView.CellValueNeeded>と<xref:System.Windows.Forms.DataGridView.CellValuePushed>イベント。 詳細については、「[方法 :仮想モードを実装で、Windows フォーム DataGridView コントロール](how-to-implement-virtual-mode-in-the-windows-forms-datagridview-control.md)します。 バインド モードでバインドされていない列による並べ替えはサポートされていません。  
  
## <a name="programmatic-sorting"></a>プログラムによる並べ替え  
 並べ替えることができます、<xref:System.Windows.Forms.DataGridView>プログラムで呼び出してその<xref:System.Windows.Forms.DataGridView.Sort%2A>メソッド。  
  
 `Sort(DataGridViewColumn,ListSortDirection)`のオーバー ロード、<xref:System.Windows.Forms.DataGridView.Sort%2A>メソッドは、<xref:System.Windows.Forms.DataGridViewColumn>と<xref:System.ComponentModel.ListSortDirection>パラメーターとしての列挙値。 このオーバー ロードは、値を明確注文することができますが、自動並べ替えを構成するたくないを列で並べ替える場合に便利です。 このオーバー ロードを呼び出すし、列に渡す、<xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A>プロパティ値の<xref:System.Windows.Forms.DataGridViewColumnSortMode.Automatic?displayProperty=nameWithType>、<xref:System.Windows.Forms.DataGridView.SortedColumn%2A>と<xref:System.Windows.Forms.DataGridView.SortOrder%2A>プロパティが自動的に設定して、列ヘッダーに適切な並べ替えグリフが表示されます。  
  
> [!NOTE]
>  ときに、<xref:System.Windows.Forms.DataGridView>コントロールが設定して、外部データ ソースにバインドされて、<xref:System.Windows.Forms.DataGridView.DataSource%2A>プロパティ、`Sort(DataGridViewColumn,ListSortDirection)`非バインド列のメソッドのオーバー ロードは機能しません。 さらに、ときに、<xref:System.Windows.Forms.DataGridView.VirtualMode%2A>プロパティは`true`、バインドされた列に対してのみ、このオーバー ロードを呼び出すことができます。 列のデータ バインドがあるかどうかを確認するには<xref:System.Windows.Forms.DataGridViewColumn.IsDataBound%2A>プロパティの値。 バインド モードでバインドされていない列の並べ替えはサポートされていません。  
  
## <a name="custom-sorting"></a>カスタムの並べ替え  
 カスタマイズできる<xref:System.Windows.Forms.DataGridView>を使用して、`Sort(IComparer)`のオーバー ロード、<xref:System.Windows.Forms.DataGridView.Sort%2A>メソッドまたは処理することによって、<xref:System.Windows.Forms.DataGridView.SortCompare>イベント。  
  
 `Sort(IComparer)`メソッドのオーバー ロードが実装するクラスのインスタンスを受け取り、<xref:System.Collections.IComparer>インターフェイスをパラメーターとして。 このオーバー ロードは、カスタムの並べ替え; を提供する場合に役立ちますたとえば、列の値を持っていない場合、自然な並べ替え順序またはと自然に並べ替え順序が適切です。 ここで、自動並べ替えを使用することはできませんが、ユーザーが列見出しをクリックして並べ替えする可能性があります。 ハンドラーでこのオーバー ロードを呼び出すことができます、<xref:System.Windows.Forms.DataGridView.ColumnHeaderMouseClick>イベントの選択範囲の列ヘッダーを使用しない場合。  
  
> [!NOTE]
>  `Sort(IComparer)`メソッドのオーバー ロードの動作の場合にのみ、<xref:System.Windows.Forms.DataGridView>コントロールは、外部データ ソースにバインドされていないと、<xref:System.Windows.Forms.DataGridView.VirtualMode%2A>プロパティの値が`false`します。 外部データ ソースにバインドされている列の並べ替えをカスタマイズするには、データ ソースによって提供される並べ替え操作を使用する必要があります。 仮想モードでは、バインドされていない列に対して独自の並べ替え操作を提供する必要があります。  
  
 使用する、`Sort(IComparer)`メソッド オーバー ロードで実装するクラスを作成する必要があります、<xref:System.Collections.IComparer>インターフェイス。 このインターフェイスを実装するクラスが必要です、<xref:System.Collections.IComparer.Compare%2A?displayProperty=nameWithType>先のメソッド、<xref:System.Windows.Forms.DataGridView>渡します<xref:System.Windows.Forms.DataGridViewRow>オブジェクトとして入力ときに、`Sort(IComparer)`メソッドのオーバー ロードが呼び出されます。 これにより、任意の列の値に基づいて適切な行の順序を計算できます。  
  
 `Sort(IComparer)`メソッドのオーバー ロードが設定されていない、<xref:System.Windows.Forms.DataGridView.SortedColumn%2A>と<xref:System.Windows.Forms.DataGridView.SortOrder%2A>プロパティ、常に設定する必要がありますので、<xref:System.Windows.Forms.DataGridViewColumnHeaderCell.SortGlyphDirection%2A?displayProperty=nameWithType>並べ替えグリフを表示するプロパティ。  
  
 代替方法として、`Sort(IComparer)`メソッド オーバー ロードで行うことができますのハンドラーを実装することによってカスタムの並べ替え、<xref:System.Windows.Forms.DataGridView.SortCompare>イベント。 このイベントは、ユーザーは、自動並べ替えに対してを呼び出したときに構成された列のヘッダーをクリックしたときに発生します。、`Sort(DataGridViewColumn,ListSortDirection)`のオーバー ロード、<xref:System.Windows.Forms.DataGridView.Sort%2A>メソッド。 正しい順序を計算できるように、コントロール内の行のペアごとに、イベントが発生します。  
  
> [!NOTE]
>  <xref:System.Windows.Forms.DataGridView.SortCompare>イベントは発生しないときに、<xref:System.Windows.Forms.DataGridView.DataSource%2A>プロパティを設定またはときに、<xref:System.Windows.Forms.DataGridView.VirtualMode%2A>プロパティの値が`true`します。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.Sort%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.SortedColumn%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.SortOrder%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewColumnHeaderCell.SortGlyphDirection%2A?displayProperty=nameWithType>
- [Windows フォームの DataGridView コントロールでのデータの並べ替え](sorting-data-in-the-windows-forms-datagridview-control.md)
- [方法: Windows フォームの DataGridView コントロール内の列の並べ替えモードを設定します。](set-the-sort-modes-for-columns-wf-datagridview-control.md)
- [方法: Windows フォームの DataGridView コントロールでの並べ替えをカスタマイズします。](how-to-customize-sorting-in-the-windows-forms-datagridview-control.md)
