---
title: WPF と Windows フォームの相互運用性
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms [WPF], interoperability with
- nester interoperation [WPF]
- Windows Forms [WPF], WPF interoperation
- interoperability [WPF], Windows Forms
- hybrid control [WPF interoperability]
ms.assetid: 9e8aa6b6-112c-4579-98d1-c974917df499
ms.openlocfilehash: 0326f283cb271d1578e94b648e423c6f88c579f0
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69917403"
---
# <a name="wpf-and-windows-forms-interoperation"></a>WPF と Windows フォームの相互運用性
[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]と[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]には、アプリケーションインターフェイスを作成するための2つの異なるアーキテクチャがあります。 名前<xref:System.Windows.Forms.Integration?displayProperty=nameWithType>空間には、一般的な相互運用シナリオを可能にするクラスが用意されています。 相互運用機能を実装する2つの<xref:System.Windows.Forms.Integration.WindowsFormsHost>主要<xref:System.Windows.Forms.Integration.ElementHost>なクラスは、とです。 このトピックでは、サポートされている相互運用シナリオとサポートされていないシナリオについて説明します。  
  
> [!NOTE]
> *ハイブリッド制御*のシナリオには、特別な考慮事項があります。 ハイブリッドコントロールには、他のテクノロジのコントロールで入れ子になった1つのテクノロジからのコントロールがあります。 これは、入れ子に*なった相互運用*とも呼ばれます。 複数レベルの*ハイブリッドコントロール*には、複数レベルのハイブリッドコントロールの入れ子があります。 入れ子になった複数レベルの相互運用[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]の例とし[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]て、別[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]のコントロールを含むコントロールを含むコントロールがあります。 複数レベルのハイブリッドコントロールはサポートされていません。  

<a name="Windows_Presentation_Foundation_Application_Hosting"></a>   
## <a name="hosting-windows-forms-controls-in-wpf"></a>WPF での Windows フォームコントロールのホスト  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]コントロールが Windows フォームコントロールをホストする場合、次の相互運用シナリオがサポートされます。  
  
- コントロール[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]は、XAML を使用し[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]て1つ以上のコントロールをホストできます。  
  
- コードを使用して 1 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]つ以上のコントロールをホストできます。  
  
- これは、 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]他の[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]コントロールを含むコンテナーコントロールをホストする場合があります。  
  
- マスター/詳細形式のフォーム[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]をホストし[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]ている場合があります。  
  
- マスター/詳細形式のフォーム[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]をホストし[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]ている場合があります。  
  
- 1つ以上の ActiveX コントロールをホストできます。  
  
- 1つ以上の複合コントロールをホストできます。  
  
- これは、を使用し[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]てハイブリッドコントロールをホストする場合があります。  
  
- コードを使用してハイブリッドコントロールをホストする場合があります。  
  
### <a name="layout-support"></a>レイアウトのサポート  
 次の一覧では、要素が<xref:System.Windows.Forms.Integration.WindowsFormsHost>ホスト[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]されるコントロールを[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]レイアウトシステムに統合しようとした場合の既知の制限事項について説明します。  
  
- 場合によって[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]は、コントロールのサイズを変更したり、特定の大きさに合わせてサイズを変更したりすることはできません。 たとえば、コントロールは[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] <xref:System.Windows.Forms.ComboBox> 、コントロールのフォントサイズによって定義される1つの高さのみをサポートします。 動的レイアウトでは、要素が垂直方向に引き伸ばすことができると<xref:System.Windows.Forms.ComboBox>想定しているため、ホストされているコントロールは期待どおりに拡大されません。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]  
  
- [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]コントロールを回転または傾斜させることはできません。 たとえば、ユーザーインターフェイスを90度回転させると、ホスト[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]されたコントロールの位置が維持されます。  
  
- ほとんどの場合、 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]コントロールは比例スケールをサポートしていません。 コントロールの全体の次元はスケーリングされますが、コントロールの子コントロールとコンポーネント要素は、予期したとおりにサイズ変更されない可能性があります。 この制限は、各[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]コントロールがどの程度スケーリングをサポートするかによって異なります。  
  
- [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]ユーザーインターフェイスでは、要素の z オーダーを変更して、重なり合う動作を制御できます。 ホスト[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]されるコントロールは別の HWND で描画されるので、常に要素[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]の上に描画されます。  
  
- [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]コントロールは、フォントサイズに基づいて自動スケールをサポートします。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]ユーザーインターフェイスでは、フォントサイズを変更してもレイアウト全体のサイズは変更されませんが、個々の要素のサイズは動的に変更される可能性があります。  
  
### <a name="ambient-properties"></a>アンビエントプロパティ  
 コントロールの[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]アンビエントプロパティには、同等[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]のものがあります。 これらのアンビエントプロパティは、ホスト[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]されるコントロールに反映され、 <xref:System.Windows.Forms.Integration.WindowsFormsHost>コントロールのパブリックプロパティとして公開されます。 コントロール<xref:System.Windows.Forms.Integration.WindowsFormsHost>は、各[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]アンビエントプロパティを等価[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]のに変換します。  
  
 詳細については、「 [Windows フォームと WPF プロパティのマッピング](windows-forms-and-wpf-property-mapping.md)」を参照してください。  
  
### <a name="behavior"></a>動作  
 次の表では、相互運用の動作について説明します。  
  
|動作|サポート状況|サポートなし|  
|--------------|---------------|-------------------|  
|[透明度]|[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]コントロールのレンダリングは透明度をサポートします。 親[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]コントロールの背景が、ホスト[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]されているコントロールの背景になる場合があります。|一部[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]のコントロールは、透明度をサポートしていません。 たとえば<xref:System.Windows.Forms.TextBox> 、コントロールと<xref:System.Windows.Forms.ComboBox>コントロールは、でホストされて[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]いる場合は透過的になりません。|  
|インデント|ホスト[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]されたコントロールのタブオーダーは、これらのコントロールがベースの[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]アプリケーションでホストされている場合と同じです。<br /><br /> Tab キーおよび[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] SHIFT + TAB [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]キーを使用してコントロールからコントロールに tab キーを押すと、通常どおりに動作します。<br /><br /> [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]<xref:System.Windows.Forms.Control.TabStop%2A> の`false`プロパティ値を持つコントロールは、ユーザーがコントロールを使用してタブを表示してもフォーカスを受け取りません。<br /><br /> -各<xref:System.Windows.Forms.Integration.WindowsFormsHost>コントロール<xref:System.Windows.Forms.Integration.WindowsFormsHost.TabIndex%2A>には、その<xref:System.Windows.Forms.Integration.WindowsFormsHost>コントロールがフォーカスを受け取るタイミングを決定する値があります。<br />-   [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]<xref:System.Windows.Forms.Integration.WindowsFormsHost>コンテナー内に含まれるコントロールは、 <xref:System.Windows.Forms.Control.TabIndex%2A>プロパティで指定された順序に従います。 最後のタブインデックスから tab キーを置くと、 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]次のコントロール (存在する場合) にフォーカスが移動します。 フォーカス[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]がある他のコントロールが存在しない場合は[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 、タブオーダーの最初のコントロールに戻ります。<br />-   <xref:System.Windows.Forms.Integration.WindowsFormsHost.TabIndex%2A>内<xref:System.Windows.Forms.Integration.WindowsFormsHost>のコントロールの値は、 <xref:System.Windows.Forms.Integration.WindowsFormsHost>コントロールに[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]含まれる兄弟コントロールに対して相対的です。<br />-Tab キーを指定すると、コントロール固有の動作が受け入れます。 たとえば、 <xref:System.Windows.Forms.TextBox> <xref:System.Windows.Forms.TextBoxBase.AcceptsTab%2A>プロパティ値`true`がであるコントロールで tab キーを押すと、フォーカスを移動するのではなく、テキストボックスにタブが表示されます。|該当なし。|  
|方向キーを使用したナビゲーション|- <xref:System.Windows.Forms.Integration.WindowsFormsHost>コントロールの方向キーを使用したナビゲーションは、通常[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]のコンテナーコントロールの場合と同じです。上方向キーと左方向キーは、前のコントロールを選択し、下方向キーと右方向キーは次のコントロールを選択します。<br />- <xref:System.Windows.Forms.Integration.WindowsFormsHost>コントロールに含まれている最初のコントロールの上方向キーと左方向キーは、SHIFT + TAB キーショートカットと同じ操作を実行します。 フォーカスがある[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]コントロールがある場合、フォーカスはコントロール<xref:System.Windows.Forms.Integration.WindowsFormsHost>の外に移動します。 この動作は、最後の<xref:System.Windows.Forms.ContainerControl>コントロールがラップされていないという点で、標準の動作とは異なります。 フォーカスがある他[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]のコントロールが存在しない場合は[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 、タブオーダーの最後のコントロールにフォーカスが戻ります。<br />- <xref:System.Windows.Forms.Integration.WindowsFormsHost>コントロールに含まれている最後のコントロールの下方向キーと右方向キーは、TAB キーと同じ操作を実行します。 フォーカスがある[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]コントロールがある場合、フォーカスはコントロール<xref:System.Windows.Forms.Integration.WindowsFormsHost>の外に移動します。 この動作は、最初の<xref:System.Windows.Forms.ContainerControl>コントロールのラップが行われないという点で、標準の動作とは異なります。 フォーカスがある他[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]のコントロールが存在しない場合は[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 、タブオーダーの最初のコントロールにフォーカスが戻ります。|該当なし。|  
|アクセラレータ|アクセラレータは、"サポートされていません" 列に記載されている場合を除き、通常どおりに動作します。|テクノロジ間の重複するアクセラレータは、通常の重複アクセラレータと同じようには機能しません。 複数のテクノロジにわたってアクセラレータが複製され、コントロール上[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]に少なくと[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]も1つのコントロールが[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]ある場合、コントロールは常にアクセラレータを受け取ります。 重複するアクセラレータが押されている場合、フォーカスは切り替えられません。|  
|ショートカットキー|ショートカットキーは、"サポートされていません" 列に記載されている場合を除き、通常どおりに動作します。|-   [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]前処理段階で処理されるショートカットキーは、常に[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]ショートカットキーよりも優先されます。 たとえば、ctrl + s ショートカット<xref:System.Windows.Forms.ToolStrip>キーが定義されているコントロールがあり、 <xref:System.Windows.Forms.ToolStrip> ctrl + [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] s にバインドされたコマンドがある場合、フォーカスに関係なく、常にコントロールハンドラーが最初に呼び出されます。<br />-   [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]<xref:System.Windows.Forms.Control.KeyDown>イベントによって処理されるショートカットキーは、 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]で最後に処理されます。 この動作を回避するには、 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]コントロールの<xref:System.Windows.Forms.Control.IsInputKey%2A>メソッドをオーバーライドする<xref:System.Windows.Forms.Control.PreviewKeyDown>か、イベントを処理します。 `true` <xref:System.Windows.Forms.PreviewKeyDownEventArgs.IsInputKey%2A?displayProperty=nameWithType> `true`メソッドからを返すか、 <xref:System.Windows.Forms.Control.PreviewKeyDown>イベントハンドラーでプロパティの値をに設定します。 <xref:System.Windows.Forms.Control.IsInputKey%2A>|  
|AcceptsReturn、AcceptsTab、およびその他のコントロール固有の動作|既定のキーボード動作を変更するプロパティは、コントロールが[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]メソッドを<xref:System.Windows.Forms.Control.IsInputKey%2A>オーバーライドしてを返す`true`ことを想定して、通常どおりに動作します。|[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]イベントを<xref:System.Windows.Forms.Control.KeyDown>処理することによって既定のキーボード動作を変更するコントロール[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]は、ホストコントロールで最後に処理されます。 これらのコントロールは最後に処理されるため、予期しない動作が発生する可能性があります。|  
|イベントの開始と終了|フォーカスが格納<xref:System.Windows.Forms.Integration.ElementHost>しているコントロールに移動しない場合、1つ<xref:System.Windows.Forms.Integration.WindowsFormsHost>のコントロールでフォーカスが変更されると、Enter イベントと Leave イベントが通常どおりに発生します。|次のような変更が発生すると、Enter イベントと Leave イベントは発生しません。<br /><br /> -内部からコントロールの<xref:System.Windows.Forms.Integration.WindowsFormsHost>外部へ。<br />-外側から<xref:System.Windows.Forms.Integration.WindowsFormsHost>コントロール内へ。<br />-コントロールの<xref:System.Windows.Forms.Integration.WindowsFormsHost>外側。<br />- [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] コントロール<xref:System.Windows.Forms.Integration.WindowsFormsHost>でホストされているコントロールから<xref:System.Windows.Forms.Integration.ElementHost> 、同じ<xref:System.Windows.Forms.Integration.WindowsFormsHost>内でホストされているコントロールへの。|  
|マルチスレッド|すべての種類のマルチスレッドがサポートされています。|[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] と[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]テクノロジはどちらも、シングルスレッドの同時実行モデルを想定しています。 デバッグ中に、他のスレッドからフレームワークオブジェクトを呼び出すと、例外が発生し、この要件が適用されます。|  
|セキュリティ|すべての相互運用シナリオには、完全な信頼が必要です。|部分信頼では、相互運用シナリオは許可されません。|  
|ユーザー補助|すべてのユーザー補助シナリオがサポートされています。 との両方[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]のコントロールを含むハイブリッドアプリケーションでは、 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]支援技術製品が正しく機能します。|該当なし。|  
|クリップボードのトピック|すべてのクリップボード操作は通常どおりに動作します。 これには、コントロールと[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]コントロールの間の切り取りと貼り付けが含まれます。|該当なし。|  
|ドラッグアンドドロップ機能|すべてのドラッグアンドドロップ操作は通常どおりに動作します。 これには、 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]コントロール[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]とコントロールの間の操作が含まれます。|該当なし。|  
  
<a name="Windows_Forms_Application_Hosting_Windows"></a>   
## <a name="hosting-wpf-controls-in-windows-forms"></a>Windows フォームでの WPF コントロールのホスト  
 Windows フォームコントロールがコントロールを[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]ホストする場合、次の相互運用シナリオがサポートされます。  
  
- コードを使用し[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]て1つ以上のコントロールをホストする。  
  
- プロパティシートと1つ以上のホスト[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]されるコントロールとの関連付け。  
  
- 1つ[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]以上のページをフォームでホストする。  
  
- ウィンドウを[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]起動しています。  
  
- マスター/詳細を含む[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]フォームをホストする。  
  
- マスター/詳細を含む[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]フォームをホストする。  
  
- カスタム[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]コントロールをホストしています。  
  
- ハイブリッドコントロールをホストする。  
  
### <a name="ambient-properties"></a>アンビエントプロパティ  
 コントロールの[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]アンビエントプロパティには、同等[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]のものがあります。 これらのアンビエントプロパティは、ホスト[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]されるコントロールに反映され、 <xref:System.Windows.Forms.Integration.ElementHost>コントロールのパブリックプロパティとして公開されます。 コントロール<xref:System.Windows.Forms.Integration.ElementHost>は、各[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]アンビエントプロパティを等価[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]のに変換します。  
  
 詳細については、「 [Windows フォームと WPF プロパティのマッピング](windows-forms-and-wpf-property-mapping.md)」を参照してください。  
  
### <a name="behavior"></a>動作  
 次の表では、相互運用の動作について説明します。  
  
|動作|サポート状況|サポートなし|  
|--------------|---------------|-------------------|  
|[透明度]|[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]コントロールのレンダリングは透明度をサポートします。 親[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]コントロールの背景が、ホスト[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]されているコントロールの背景になる場合があります。|該当なし。|  
|マルチスレッド|すべての種類のマルチスレッドがサポートされています。|[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] と[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]テクノロジはどちらも、シングルスレッドの同時実行モデルを想定しています。 デバッグ中に、他のスレッドからフレームワークオブジェクトを呼び出すと、例外が発生し、この要件が適用されます。|  
|セキュリティ|すべての相互運用シナリオには、完全な信頼が必要です。|部分信頼では、相互運用シナリオは許可されません。|  
|ユーザー補助|すべてのユーザー補助シナリオがサポートされています。 との両方[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]のコントロールを含むハイブリッドアプリケーションでは、 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]支援技術製品が正しく機能します。|該当なし。|  
|クリップボードのトピック|すべてのクリップボード操作は通常どおりに動作します。 これには、コントロールと[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]コントロールの間の切り取りと貼り付けが含まれます。|該当なし。|  
|ドラッグアンドドロップ機能|すべてのドラッグアンドドロップ操作は通常どおりに動作します。 これには、 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]コントロール[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]とコントロールの間の操作が含まれます。|該当なし。|  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [チュートリアル: WPF での Windows フォームコントロールのホスト](walkthrough-hosting-a-windows-forms-control-in-wpf.md)
- [チュートリアル: WPF での Windows フォーム複合コントロールのホスト](walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)
- [チュートリアル: Windows フォームでの WPF 複合コントロールのホスト](walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
- [Windows フォームと WPF プロパティの割り当て](windows-forms-and-wpf-property-mapping.md)
