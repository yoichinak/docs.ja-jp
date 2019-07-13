---
title: Windows フォーム DataGridView コントロールにおける新規レコード行の使用
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], adding rows for new records
- rows [Windows Forms], new records
- DataGridView control [Windows Forms], data entry
ms.assetid: 6110f1ea-9794-442c-a98a-f104a1feeaf4
ms.openlocfilehash: b28a8a8fc2d75f80a14447008c850de63e4e04b3
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/19/2019
ms.locfileid: "65882430"
---
# <a name="using-the-row-for-new-records-in-the-windows-forms-datagridview-control"></a>Windows フォーム DataGridView コントロールにおける新規レコード行の使用
使用すると、<xref:System.Windows.Forms.DataGridView>アプリケーションでデータを編集するには、多くの場合することをデータ ストアに新しいデータ行を追加する機能をユーザーに提供します。 <xref:System.Windows.Forms.DataGridView>コントロールは、最後の行として常に表示されている、新しいレコードの行を指定してこの機能をサポートしています。 これは、行のヘッダーにアスタリスク (*) 記号でマークされます。 次のセクションでは、新しいレコードの行でプログラムが有効にした場合の考慮事項について説明します。  
  
## <a name="displaying-the-row-for-new-records"></a>新しいレコードの行を表示します。  
 使用して、<xref:System.Windows.Forms.DataGridView.AllowUserToAddRows%2A>新しいレコードの行を表示するかどうかを示すプロパティです。 このプロパティの既定値は `true` です。  
  
 新しいレコードの行が表示されます、データの場合、バインドの場合、<xref:System.Windows.Forms.DataGridView.AllowUserToAddRows%2A>コントロールのプロパティと<xref:System.ComponentModel.IBindingList.AllowNew%2A?displayProperty=nameWithType>のデータ ソースのプロパティは、どちらも`true`します。 いずれかの場合`false`その行は表示されません。  
  
## <a name="populating-the-row-for-new-records-with-default-data"></a>既定のデータを新しいレコードの行を設定  
 ユーザーが現在の行と新しいレコードの行を選択するとき、<xref:System.Windows.Forms.DataGridView>制御発生させ、<xref:System.Windows.Forms.DataGridView.DefaultValuesNeeded>イベント。  
  
 このイベントは、新しいへのアクセスを提供します。<xref:System.Windows.Forms.DataGridViewRow>既定のデータを新しい行に設定することができます。 詳細については、「[方法 :Windows フォームの DataGridView コントロール内の新しい行の既定値を指定します。](specify-default-values-for-new-rows-in-the-datagrid.md)  
  
## <a name="the-rows-collection"></a>行のコレクション  
 新しいレコードの行が含まれている、<xref:System.Windows.Forms.DataGridView>コントロールの<xref:System.Windows.Forms.DataGridView.Rows%2A>コレクションが、2 つの点では動作が異なります。  
  
- 新しいレコードの行を削除できません、<xref:System.Windows.Forms.DataGridView.Rows%2A>コレクション プログラムを使用します。 <xref:System.InvalidOperationException>が、これを試行した場合にスローされます。 また、ユーザーは、新しいレコードの行を削除できません。 <xref:System.Windows.Forms.DataGridViewRowCollection.Clear%2A?displayProperty=nameWithType>メソッドでは、この行からは削除されません、<xref:System.Windows.Forms.DataGridView.Rows%2A>コレクション。  
  
- 新しいレコードの行の後に行を追加されません。 <xref:System.InvalidOperationException>が、これを試行した場合に発生します。 その結果、新しいレコードの行は常に最後の行で、<xref:System.Windows.Forms.DataGridView>コントロール。 メソッドを<xref:System.Windows.Forms.DataGridViewRowCollection>行を追加する-<xref:System.Windows.Forms.DataGridViewRowCollection.Add%2A>、 <xref:System.Windows.Forms.DataGridViewRowCollection.AddCopy%2A>、および<xref:System.Windows.Forms.DataGridViewRowCollection.AddCopies%2A>— すべてメソッドを呼び出す挿入内部的に新しいレコードの行が存在する場合。  
  
## <a name="visual-customization-of-the-row-for-new-records"></a>新しいレコードの行のビジュアルのカスタマイズ  
 指定した行に基づいて新しいレコードの行が作成されたときに、<xref:System.Windows.Forms.DataGridView.RowTemplate%2A>プロパティ。 この行に指定されていないセルのスタイルは、その他のプロパティから継承されます。 セル スタイルの継承の詳細については、次を参照してください。 [Windows フォームの DataGridView コントロールのセル スタイル](cell-styles-in-the-windows-forms-datagridview-control.md)します。  
  
 各セルから新しいレコードを取得、行内のセルで表示される初期値<xref:System.Windows.Forms.DataGridViewCell.DefaultNewRowValue%2A>プロパティ。 型のセルの<xref:System.Windows.Forms.DataGridViewImageCell>、このプロパティは、プレース ホルダー イメージを返します。 このプロパティを返しますそれ以外の場合、`null`します。 カスタム値を返すには、このプロパティをオーバーライドすることができます。 ただし、によってこれらの初期値を置き換えることができます、<xref:System.Windows.Forms.DataGridView.DefaultValuesNeeded>新しいレコードの行にフォーカスが移ったときにイベント ハンドラー。  
  
 矢印またはアスタリスクは、この行のヘッダーの標準アイコンは、パブリックに公開されません。 アイコンをカスタマイズするには、カスタムを作成する必要があります<xref:System.Windows.Forms.DataGridViewRowHeaderCell>クラス。  
  
 標準のアイコンを使用して、<xref:System.Windows.Forms.DataGridViewCellStyle.ForeColor%2A>のプロパティ、<xref:System.Windows.Forms.DataGridViewCellStyle>行ヘッダー セルで使用します。 標準のアイコンは、それらを完全に表示するには、十分な領域がない場合はレンダリングされません。  
  
 行ヘッダー セルに設定すると、文字列値が設定されている場合、およびテキストとアイコンの両方に対して十分な空きがない場合は、アイコンを先に削除します。  
  
## <a name="sorting"></a>並べ替え  
 バインドされていないモードでは、新しいレコードがの末尾に追加する常に、<xref:System.Windows.Forms.DataGridView>場合でも、ユーザーには、内容が並べ替えられて、<xref:System.Windows.Forms.DataGridView>します。 ユーザーは、正しい位置に行を並べ替えるために再度並べ替えを適用する必要があります。この動作は、に似ていますが、<xref:System.Windows.Forms.ListView>コントロール。  
  
 データ バインドされた仮想のモードでは、並べ替えが適用されるときに、カーソル動作はデータ モデルの実装に依存することができます。 Ado.net の場合は、正しい位置に行がすぐに並べ替えられます。  
  
## <a name="other-notes-on-the-row-for-new-records"></a>新しいレコードの行でその他の注意事項  
 設定することはできません、<xref:System.Windows.Forms.DataGridViewRow.Visible%2A>プロパティには、この行の`false`します。 <xref:System.InvalidOperationException>が、これを試行した場合に発生します。  
  
 新しいレコードの行が選択されていない状態で常に作成されます。  
  
## <a name="virtual-mode"></a>仮想モード  
 仮想モードを実装する場合は、新しいレコードの行がデータ モデルと、行の追加をロールバックするために必要な場合に追跡する必要があります。 この機能の正確な実装に依存データ モデルとそのトランザクションのセマンティクスの実装など、コミットのスコープがセルまたは行レベルであるかどうか。 詳細については、次を参照してください。 [Windows フォームの DataGridView コントロールでの仮想モード](virtual-mode-in-the-windows-forms-datagridview-control.md)します。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.DefaultValuesNeeded?displayProperty=nameWithType>
- [Windows フォーム DataGridView コントロールでのデータ入力](data-entry-in-the-windows-forms-datagridview-control.md)
- [方法: Windows フォームの DataGridView コントロール内の新しい行の既定値を指定します。](specify-default-values-for-new-rows-in-the-datagrid.md)
