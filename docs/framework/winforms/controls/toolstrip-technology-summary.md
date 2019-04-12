---
title: ToolStrip テクノロジの概要
ms.date: 03/30/2017
helpviewer_keywords:
- ToolStrip control [Windows Forms], technology summary
- status bars [Windows Forms], technology summary
- toolbars [Windows Forms], technology summary
- menus [Windows Forms], technology summary
ms.assetid: e8d61973-7af9-429f-9df5-05a899c15a7b
ms.openlocfilehash: b6537faa3be7ee28a934927fc95100a34a64e176
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59120961"
---
# <a name="toolstrip-technology-summary"></a>ToolStrip テクノロジの概要
ここでは、`ToolStrip` コントロールおよびその使用をサポートしているクラスの概要について説明します。  
  
 `ToolStrip` コントロールとその関連クラスは、ツール バー、ステータス バー、メニューを作成するための完全なソリューションを提供します。  
  
## <a name="namespaces"></a>名前空間  
 <xref:System.Windows.Forms?displayProperty=nameWithType>  
  
## <a name="background"></a>背景  
 `ToolStrip` コントロールと関連クラスを使用すると、外観と動作に一貫性がある、プロフェッショナル レベルの高度なツール バー機能を作成できます。 `ToolStrip` コントロールとクラスでは、以前のコントロールから次の点が改善されました。  
  
-   より一貫性のあるイベント モデル。  
  
-   タスク一覧と項目コレクション エディターを含む、より一貫性のあるデザイン時動作。  
  
-   `ToolStripManager` と `ToolStripRenderer` を使用したカスタム描画。  
  
-   `ToolStripContainer` と `ToolStripPanel` を使用したビルトイン ラフティング (ドッキング時にツール領域内の水平スペースと垂直スペースを共有すること)。  
  
-   <xref:System.Windows.Forms.ToolStrip.AllowItemReorder%2A> プロパティを使用した、デザイン時および実行時の項目の並べ替え。  
  
-   <xref:System.Windows.Forms.ToolStrip.CanOverflow%2A> プロパティを使用した、オーバーフロー メニューへの項目の再配置。  
  
-   `ToolStripContainer`、`ToolStripPanel`、`ToolStripContentPanel` を使用した、自由に構成可能なコントロール位置。  
  
-   `ToolStripControlHost` を使用した、`ToolStrip`、従来のコントロール、またはカスタム コントロールのホスト。  
  
-   `ToolStripPanel` を使用した `ToolStrip` コントロールのマージ。  
  
 `ToolStrip` 拡張の基本クラスは、 `MenuStrip`、 `ContextMenuStrip`、および`StatusStrip`します。 これらのコントロールは、共通の動作とイベント処理を継承する <xref:System.Windows.Forms.ToolStripItem> コンテナーで、それぞれの実装で適切な動作を処理できるように拡張されています。 <xref:System.Windows.Forms.ToolStripItem> から派生するコントロールについて、次の表に示します。 `ToolStrip` 基底クラスでは、コントロールの描画、ユーザー入力、ドラッグ アンド ドロップの各イベントを処理します。  
  
 `ToolStrip`、`MenuStrip`、`ContextMenuStrip`、`StatusStrip` の各コントロールは、以前のツール バー、メニュー、ショートカット メニュー、ステータス バーの各コントロールに置き換わるものです。ただし、これらのコントロールも下位互換性の目的で保持されています。  
  
## <a name="toolstrip-classes-at-a-glance"></a>ToolStrip のクラスの概要  
 テクノロジ分野でグループ化した ToolStrip クラスを次の表に示します。  
  
|テクノロジ分野|クラス|  
|---------------------|-----------|  
|ツール バー、ステータス、メニューのコンテナー|<xref:System.Windows.Forms.ToolStrip><br /><br /> <xref:System.Windows.Forms.MenuStrip><br /><br /> <xref:System.Windows.Forms.ContextMenuStrip><br /><br /> <xref:System.Windows.Forms.StatusStrip><br /><br /> <xref:System.Windows.Forms.ToolStripDropDownMenu>|  
|ToolStrip 項目|<xref:System.Windows.Forms.ToolStripLabel><br /><br /> <xref:System.Windows.Forms.ToolStripDropDownItem><br /><br /> <xref:System.Windows.Forms.ToolStripMenuItem><br /><br /> <xref:System.Windows.Forms.ToolStripButton><br /><br /> <xref:System.Windows.Forms.ToolStripStatusLabel><br /><br /> <xref:System.Windows.Forms.ToolStripSeparator><br /><br /> <xref:System.Windows.Forms.ToolStripControlHost><br /><br /> <xref:System.Windows.Forms.ToolStripComboBox><br /><br /> <xref:System.Windows.Forms.ToolStripTextBox><br /><br /> <xref:System.Windows.Forms.ToolStripProgressBar><br /><br /> <xref:System.Windows.Forms.ToolStripDropDownButton><br /><br /> <xref:System.Windows.Forms.ToolStripSplitButton>|  
|場所|<xref:System.Windows.Forms.ToolStripContainer><br /><br /> <xref:System.Windows.Forms.ToolStripContentPanel><br /><br /> <xref:System.Windows.Forms.ToolStripPanel>|  
|プレゼンテーションと描画|<xref:System.Windows.Forms.ToolStripManager><br /><br /> <xref:System.Windows.Forms.ToolStripRenderer><br /><br /> <xref:System.Windows.Forms.ToolStripProfessionalRenderer><br /><br /> <xref:System.Windows.Forms.ToolStripRenderMode><br /><br /> <xref:System.Windows.Forms.ToolStripManagerRenderMode>|  
  
## <a name="toolstrip-design-time-features"></a>ToolStrip のデザイン時機能  
 <xref:System.Windows.Forms.ToolStrip> ファミリのコントロールには、実用的なアプリケーションを短期間で作成できるように、埋め込み先での編集とユーザー インターフェイスの基盤の定義を行うための豊富なツールとテンプレートのセットが用意されています。  
  
### <a name="task-dialog-boxes"></a>タスク ダイアログ ボックス  
 Visual Studio のデザイナーでコントロールのスマート タグをクリックすると、タスク一覧が表示されます。タスク一覧からは、よく使用する多くのコマンドに簡単にアクセスできます。  
  
-   [[MenuStrip タスク] ダイアログ ボックス](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms233645(v=vs.100))  
  
-   [[ToolStrip タスク] ダイアログ ボックス](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms233648(v=vs.100))  
  
-   [[ContextMenuStrip タスク] ダイアログ ボックス](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms233646(v=vs.100))  
  
-   [[StatusStrip タスク] ダイアログ ボックス](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms233642(v=vs.100))  
  
-   [[ToolStripContainer タスク] ダイアログ ボックス](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms233647(v=vs.100))  
  
### <a name="items-collection-editors"></a>項目コレクション エディター  
 クリックすると、Visual Studio で**アイテムの編集**タスクの一覧またはクリックし、コントロールを右クリックして**アイテムの編集**ショートカット メニューで、コントロールのコレクション エディターが表示されます。 コレクション エディターを使用すると、コントロールに含まれる項目の追加、削除、並べ替えを行うことができます。 また、コントロールとコントロール項目のプロパティを表示および変更することもできます。  
  
-   [MenuStrip Items コレクション エディター](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms233625(v=vs.100))  
  
-   [StatusStrip Items コレクション エディター](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms233631(v=vs.100))  
  
-   [ContextMenuStrip Items コレクション エディター](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms233641(v=vs.100))  
  
-   [ToolStrip Items コレクション エディター](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms233643(v=vs.100))  
  
## <a name="hosting-controls"></a>コントロールのホスト  
 <xref:System.Windows.Forms.ToolStripControlHost> クラスは、<xref:System.Windows.Forms.ToolStripComboBox> コントロール、<xref:System.Windows.Forms.ToolStripTextBox> コントロール、<xref:System.Windows.Forms.ToolStripProgressBar> コントロールのためのビルトイン ラッパーを提供します。 その他の既存のコントロールまたは COM コントロールを <xref:System.Windows.Forms.ToolStripControlHost> でホストすることもできます。  
  
 コントロールのホストの例は、次を参照してください。[方法。Windows フォーム コントロールをラップする ToolStripControlHost](how-to-wrap-a-windows-forms-control-with-toolstripcontrolhost.md)します。  
  
## <a name="rendering"></a>[レンダリング]  
 <xref:System.Windows.Forms.ToolStrip> クラスは、他の Windows フォーム コントロールから大幅に異なる描画スキームを実装します。 このスキームを使用すると、スタイルとテーマを簡単に適用できます。  
  
 <xref:System.Windows.Forms.ToolStrip> とそこに含まれるすべての <xref:System.Windows.Forms.ToolStripItem> オブジェクトにスタイルを適用する場合、<xref:System.Windows.Forms.ToolStripItem.Paint> イベントを項目ごとに処理する必要はありません。 代わりに、<xref:System.Windows.Forms.ToolStrip.RenderMode%2A> プロパティを <xref:System.Windows.Forms.ToolStripRenderMode> 値のいずれかに設定できます (<xref:System.Windows.Forms.ToolStripRenderMode.Custom> を除きます)。 さらに別の方法として、<xref:System.Windows.Forms.ToolStripRenderer> クラスを継承する任意のクラスに <xref:System.Windows.Forms.ToolStrip.Renderer%2A> を直接設定することもできます。 このプロパティを設定すると、<xref:System.Windows.Forms.ToolStrip.RenderMode%2A> が自動的に設定されます。  
  
 <xref:System.Windows.Forms.ToolStrip.RenderMode%2A> を <xref:System.Windows.Forms.ToolStripRenderMode.ManagerRenderMode> に設定し、<xref:System.Windows.Forms.ToolStripManager.RenderMode%2A> または <xref:System.Windows.Forms.ToolStripManager.Renderer%2A> プロパティをそれぞれ任意の <xref:System.Windows.Forms.ToolStripManagerRenderMode> または <xref:System.Windows.Forms.ToolStripRenderer> 値に設定すると、同じアプリケーション内の複数の <xref:System.Windows.Forms.ToolStrip> オブジェクトに同じスタイルを適用できます。  
  
 レンダリングの例については、次を参照してください。[方法。作成し、Windows 内の ToolStrip コントロールをフォームにカスタム レンダラーを設定](create-and-set-a-custom-renderer-for-the-toolstrip-control-in-wf.md)します。  
  
## <a name="styles-and-themes"></a>スタイルとテーマ  
 <xref:System.Windows.Forms.ToolStrip> 関連クラスは、視覚スタイルとカスタムの外観のオーバーライドを必要としないをサポートする簡単な方法と、<xref:System.Windows.Forms.ToolStripItem.OnPaint%2A>各項目のメソッド。 <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> と、<xref:System.Windows.Forms.ToolStrip.RenderMode%2A> プロパティおよび <xref:System.Windows.Forms.ToolStrip.Renderer%2A> プロパティを使用します。  
  
## <a name="rafting-and-docking"></a>ラフティングとドッキング  
 <xref:System.Windows.Forms.ToolStrip> コントロールは、ラフティング、ドッキング、または絶対位置を指定して配置できます。 <xref:System.Windows.Forms.ToolStrip> 項目がによってレイアウト、<xref:System.Windows.Forms.ToolStrip.LayoutEngine%2A>のコンテナー。  
  
 *ラフティング*ツールバーの水平方向または垂直方向の領域を共有できることです。 Windows フォームでは、<xref:System.Windows.Forms.ToolStrip>、<xref:System.Windows.Forms.MenuStrip>、<xref:System.Windows.Forms.StatusStrip> の各コントロールの配置とラフティングを行うときに、フォームの左側、右側、上側、下側にパネルを持つ <xref:System.Windows.Forms.ToolStripContainer> を使用できます。 複数の <xref:System.Windows.Forms.ToolStrip> コントロールを左右の <xref:System.Windows.Forms.ToolStripContainer> に配置すると、コントロールは垂直方向に積み重ねられます。 上または下の <xref:System.Windows.Forms.ToolStripContainer> に配置すると、コントロールは水平方向に積み重ねられます。 <xref:System.Windows.Forms.ToolStripContainer> の中央の <xref:System.Windows.Forms.ToolStripContentPanel> を使用すると、従来のコントロールをフォーム上に配置できます。  
  
 一部または全部の <xref:System.Windows.Forms.ToolStripContainer> コントロールを、デザイン時に直接選択して削除できます。 <xref:System.Windows.Forms.ToolStripContainer> は展開および折りたたみが可能で、内部のコントロールに合わせてサイズ調整されます。  
  
 *ドッキング*コントロールのフォームの左、右、上、または下の辺の位置を単純に指定することができます。  
  
 ドッキングよりもラフティングの方が有利な点は、<xref:System.Windows.Forms.ToolStrip>、<xref:System.Windows.Forms.MenuStrip>、<xref:System.Windows.Forms.StatusStrip> の各コントロールが他のコントロールと水平スペースまたは垂直スペースを共有できることです。  
  
 ほとんどの <xref:System.Windows.Forms.ToolStrip> コントロールは、他のコントロールと同様、ラフティングを使用せずにフォームにドッキングできます。 また、<xref:System.Windows.Forms.ToolStrip> コントロールを <xref:System.Windows.Forms.ToolStripContainer> 外に移動し、`Dock` プロパティを `None` に設定することによって、コントロールをフォーム上の任意の配置することもできます。また、それぞれの <xref:System.Windows.Forms.Control.Location%2A> プロパティを設定して、コントロールの絶対位置を指定することもできます。 「[方法:ToolStrip を toolstripcontainer からフォームに移動](how-to-move-a-toolstrip-out-of-a-toolstripcontainer-onto-a-form.md)します。  
  
 1 つ以上の <xref:System.Windows.Forms.ToolStripPanel> コントロールを使用すると、柔軟性が高まります。特に、マルチ ドキュメント インターフェイス (MDI: Multiple Document Interface) アプリケーションの場合、または <xref:System.Windows.Forms.ToolStripContainer> が不要な場合には、これが当てはまります。 <xref:System.Windows.Forms.ToolStripPanel> には、<xref:System.Windows.Forms.ToolStrip> コントロールの配置とラフティングのためにドッキングできる領域が用意されていますが、従来のコントロールには用意されていません。 既定では、<xref:System.Windows.Forms.ToolStripPanel>デザイナーでない**ツールボックス**を右クリックし、そこを配置することができますが、**ツールボックス**、順にクリックします**アイテムの選択**します。 また、他のクラスと同様に、<xref:System.Windows.Forms.ToolStripPanel> にプログラムからアクセスすることもできます。  
  
 <xref:System.Windows.Forms.ToolStrip>、<xref:System.Windows.Forms.MenuStrip>、および <xref:System.Windows.Forms.StatusStrip> を使用すると、項目はオーバーフローします。 これは、Microsoft Office ツール バーの項目の動作と似ています。  
  
## <a name="see-also"></a>関連項目

- [ToolStrip コントロールの概要 (Windows フォーム)](toolstrip-control-overview-windows-forms.md)
- [ToolStrip コントロールのアーキテクチャ](toolstrip-control-architecture.md)
