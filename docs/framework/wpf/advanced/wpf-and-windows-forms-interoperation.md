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
ms.openlocfilehash: 2e3390c3e387e75168958f946472a5a24a4bd440
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62053120"
---
# <a name="wpf-and-windows-forms-interoperation"></a>WPF と Windows フォームの相互運用性
[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]アプリケーション インターフェイスを作成するための 2 つの異なるアーキテクチャを提供します。 <xref:System.Windows.Forms.Integration?displayProperty=nameWithType>名前空間は、一般的な相互運用シナリオを有効にするクラスを提供します。 相互運用機能を実装する 2 つのキー クラスは<xref:System.Windows.Forms.Integration.WindowsFormsHost>と<xref:System.Windows.Forms.Integration.ElementHost>します。 このトピックでは、相互運用シナリオがサポートされているし、するシナリオはサポートされていませんがについて説明します。  
  
> [!NOTE]
>  特別な考慮事項が指定された、*ハイブリッド コントロール*シナリオ。 ハイブリッド コントロールには、その他のテクノロジからのコントロールに入れ子になった 1 つのテクノロジからのコントロールがあります。 これもと呼ばれる、*入れ子になった相互運用*します。 A*複数レベルのハイブリッド コントロール*ハイブリッドの 1 つ以上のレベルは入れ子を制御します。 複数レベルの入れ子になった相互運用性の例は、[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]コントロールを含む、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]別に格納する[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]コントロール。 複数レベルのハイブリッド コントロールがサポートされていません。  

<a name="Windows_Presentation_Foundation_Application_Hosting"></a>   
## <a name="hosting-windows-forms-controls-in-wpf"></a>WPF でのフォーム コントロールの Windows のホスト  
 次の相互運用シナリオがサポートされているときに、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]コントロール Windows フォーム コントロールをホストします。  
  
- [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]コントロールは、1 つまたは複数をホストできます[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]XAML の使用を制御します。  
  
- 1 つまたは複数をホストできます[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]コードの使用を制御します。  
  
- ホストできます[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]他を含むコンテナー コントロール[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]コントロール。  
  
- マスター/詳細フォームをホストすること、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]マスターと[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]詳細。  
  
- マスター/詳細フォームをホストすること、[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]マスターと[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]詳細。  
  
- 1 つまたは複数をホストできます[!INCLUDE[TLA2#tla_actx](../../../../includes/tla2sharptla-actx-md.md)]コントロール。  
  
- 1 つまたは複数の複合コントロールをホストできます。  
  
- 使用してハイブリッド コントロールをホストできます[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]します。  
  
- コードを使用してハイブリッド コントロールをホストできます。  
  
### <a name="layout-support"></a>レイアウトのサポート  
 次の一覧が既知の制限事項について説明しますと、<xref:System.Windows.Forms.Integration.WindowsFormsHost>要素が、そのホスト型統合しようとしています。[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]にコントロールを、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]レイアウト システム。  
  
- 場合によっては、[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]コントロールのサイズを変更できない、または特定のディメンションにのみサイズを設定することができます。 たとえば、 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] <xref:System.Windows.Forms.ComboBox>コントロールにのみ、1 つの高さ、コントロールのフォント サイズで定義されているがサポートしています。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]動的のレイアウトは、要素のホスト型が垂直方向に拡張できますを前提としています。<xref:System.Windows.Forms.ComboBox>期待どおりに、コントロールは拡張されません。  
  
- [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] コントロールを回転または傾斜ことはできません。 たとえば、ユーザー インターフェイスを 90 度回転するときにホスト[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]コントロールの垂直位置が維持されます。  
  
- ほとんどの場合、[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]コントロールは比例してスケーリングをサポートしません。 コントロールの全体的なディメンションのスケーラビリティが子コントロールとコントロールのコンポーネント要素可能性がありますのサイズ変更されない期待どおりにします。 この制限はどの程度各依存[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]コントロールがスケーリングをサポートします。  
  
- [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]ユーザー インターフェイスの動作が重複する制御する要素の z オーダーを変更することができます。 ホストされた[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]の上に常に描画するために個別の HWND では、コントロールが描画される[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]要素。  
  
- [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] コントロールは、フォント サイズに基づいた自動スケールをサポートします。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]個々 の要素を動的に変更可能性がありますが、ユーザー インターフェイス、フォント サイズを変更するは全体のレイアウトのサイズを変更できません。  
  
### <a name="ambient-properties"></a>アンビエント プロパティ  
 一部のアンビエント プロパティの[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]コントロールが[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]対応します。 これらのアンビエント プロパティを反映する、ホストされている[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]を制御し、上のパブリック プロパティとして公開、<xref:System.Windows.Forms.Integration.WindowsFormsHost>コントロール。 <xref:System.Windows.Forms.Integration.WindowsFormsHost>コントロールにそれぞれ変換[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]アンビエント プロパティにその[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]と同じです。  
  
 詳細については、次を参照してください。 [Windows フォームと WPF プロパティのマッピング](windows-forms-and-wpf-property-mapping.md)します。  
  
### <a name="behavior"></a>動作  
 次の表では、相互運用の動作について説明します。  
  
|動作|サポート状況|サポートなし|  
|--------------|---------------|-------------------|  
|[透明度]|[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] コントロールのレンダリングでは、透明性をサポートします。 親の背景[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]コントロールの背景になれるホステッド[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]コントロール。|いくつか[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]コントロールは透明度をサポートしません。 たとえば、<xref:System.Windows.Forms.TextBox>と<xref:System.Windows.Forms.ComboBox>コントロールをによってホストされているときに透明にすることはできません[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]します。|  
|Tab キーによる移動|タブ オーダーがホストされている[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]コントロールは、それらのコントロールがでホストされている場合と同じ、 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]-ベースのアプリケーション。<br /><br /> Tab、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]への制御、[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]通常どおりに動作を TAB キーと shift キーを押しながら TAB キーを制御します。<br /><br /> [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] コントロールを持つ、<xref:System.Windows.Forms.Control.TabStop%2A>プロパティの値`false`ときに、ユーザーがタブ コントロール内にフォーカスを受け取るされません。<br /><br /> -各<xref:System.Windows.Forms.Integration.WindowsFormsHost>コントロールが、<xref:System.Windows.Forms.Integration.WindowsFormsHost.TabIndex%2A>値で、タイミングを決定する<xref:System.Windows.Forms.Integration.WindowsFormsHost>コントロールがフォーカスを受け取る。<br />-   [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] コントロール内に含まれる、<xref:System.Windows.Forms.Integration.WindowsFormsHost>コンテナーで指定された順序に従う、<xref:System.Windows.Forms.Control.TabIndex%2A>プロパティ。 フォーカスを次に設定する最後のタブ インデックスから tab キーによる移動[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]が存在する場合は、制御します。 その他のフォーカス[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]を返します。 最初のタブ コントロールが存在する[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]タブ オーダーでコントロールできます。<br />-   <xref:System.Windows.Forms.Integration.WindowsFormsHost.TabIndex%2A> コントロール内の値、<xref:System.Windows.Forms.Integration.WindowsFormsHost>は兄弟を基準と[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]コントロールに含まれている、<xref:System.Windows.Forms.Integration.WindowsFormsHost>コントロール。<br />-コントロール固有の動作は、のタブ移動されます。 TAB キーを押すなど、<xref:System.Windows.Forms.TextBox>を持つコントロールを<xref:System.Windows.Forms.TextBoxBase.AcceptsTab%2A>プロパティ値の`true`フォーカスを移動する代わりにテキスト ボックスにタブを入力します。|該当なし。|  
|方向キーを使用したナビゲーション|矢印の付いたナビゲーション キー、<xref:System.Windows.Forms.Integration.WindowsFormsHost>コントロールは、通常と同じ[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]コンテナー コントロール。上向き矢印と左方向キーは、前のコントロールを選択し、下向き矢印と右矢印キーが次のコントロールを選択します。<br />-最初のコントロールに含まれているからと左方向キーを<xref:System.Windows.Forms.Integration.WindowsFormsHost>コントロールは、SHIFT キーを押しながら TAB キーのキーボード ショートカットと同じアクションを実行します。 フォーカスを設定できる場合[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]外部コントロール、フォーカスの移動、<xref:System.Windows.Forms.Integration.WindowsFormsHost>コントロール。 この動作は、標準<xref:System.Windows.Forms.ContainerControl>その動作は行われません、最後にコントロールをラップします。 その他のフォーカス[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]コントロールが存在すると、フォーカスが戻ります最後[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]タブ オーダーでコントロール。<br />-最後のコントロールに含まれている矢印および右矢印キーを<xref:System.Windows.Forms.Integration.WindowsFormsHost>コントロールは、TAB キーと同じアクションを実行します。 フォーカスを設定できる場合[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]外部コントロール、フォーカスの移動、<xref:System.Windows.Forms.Integration.WindowsFormsHost>コントロール。 この動作は、標準<xref:System.Windows.Forms.ContainerControl>動作を最初のコントロールに折り返しは行われません。 その他のフォーカス[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]にフォーカスが戻りますコントロールが存在する最初の[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]タブ オーダーでコントロール。|該当なし。|  
|アクセラレータ|アクセラレータは、「サポートされていません」の列に示されている場合を除き、通常どおりに動作します。|通常のアクセラレータが重複しないようなテクノロジの間で重複するアクセラレータは機能しません。 アクセラレータに少なくとも 1 つのテクノロジで複製されるときに、[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]コントロールと上、その他の[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]コントロール、[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]コントロールが常に、アクセラレータを受け取ります。 重複するアクセラレータが押されたときに、コントロール間でフォーカスが切り替わりません。|  
|ショートカット キー|ショートカット キーは、「サポートされていません」の列に示されている場合を除き、通常どおりに動作します。|-   [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ショートカット キーは、前処理段階で常に処理するよりも優先[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]ショートカット キー。 ある場合など、<xref:System.Windows.Forms.ToolStrip>で定義されている場合、CTRL + S ショートカット キーの制御し、は、 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] CTRL + S にバインドされているコマンド、<xref:System.Windows.Forms.ToolStrip>フォーカスに関係なくコントロール ハンドラーが最初に、常に呼び出されます。<br />-   [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ショートカット キーによって処理される、<xref:System.Windows.Forms.Control.KeyDown>イベントが最後に処理されて[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]します。 この動作をオーバーライドすることで防ぐことができます、[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]コントロールの<xref:System.Windows.Forms.Control.IsInputKey%2A>メソッドまたは処理、<xref:System.Windows.Forms.Control.PreviewKeyDown>イベント。 返す`true`から、<xref:System.Windows.Forms.Control.IsInputKey%2A>メソッド、またはの値を設定、<xref:System.Windows.Forms.PreviewKeyDownEventArgs.IsInputKey%2A?displayProperty=nameWithType>プロパティを`true`で、<xref:System.Windows.Forms.Control.PreviewKeyDown>イベント ハンドラー。|  
|AcceptsReturn、AcceptsTab、およびその他のコントロールに固有の動作|既定のキーボード動作を変更するプロパティの動作を通常どおり、あると仮定して、[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]上書きを制御、<xref:System.Windows.Forms.Control.IsInputKey%2A>メソッドを返す`true`します。|[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 既定値を変更するコントロールが処理することによって動作をキーボード、<xref:System.Windows.Forms.Control.KeyDown>イベントは、ホストで最後に処理[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]コントロール。 これらのコントロールは最後に処理されるため、予期しない動作する可能性があります。|  
|Enter および Leave イベント|ときにフォーカスを格納しているに送られない<xref:System.Windows.Forms.Integration.ElementHost>を制御する、」と入力しのままにイベントが通常どおり 1 つのフォーカスが変更されたときに発生<xref:System.Windows.Forms.Integration.WindowsFormsHost>コントロール。|入力し、次のフォーカスの変更が発生すると終了イベントは発生しません。<br /><br /> 元の外部の内側に、<xref:System.Windows.Forms.Integration.WindowsFormsHost>コントロール。<br />外部の内、<xref:System.Windows.Forms.Integration.WindowsFormsHost>コントロール。<br />-外部、<xref:System.Windows.Forms.Integration.WindowsFormsHost>コントロール。<br />[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]でホストされているコントロールを<xref:System.Windows.Forms.Integration.WindowsFormsHost>への制御、<xref:System.Windows.Forms.Integration.ElementHost>同じ内でホストされるコントロール<xref:System.Windows.Forms.Integration.WindowsFormsHost>。|  
|マルチスレッド|さまざまなマルチ スレッドがサポートされています。|両方の[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]と[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]テクノロジは、シングル スレッドの同時実行モデルを想定しています。 デバッグ中に、他のスレッドから framework のオブジェクトへの呼び出しでこの要件を強制する例外が発生します。|  
|セキュリティ|すべての相互運用シナリオでは、完全な信頼が必要です。|部分信頼では、相互運用シナリオは許可されません。|  
|ユーザー補助|すべてのユーザー補助のシナリオがサポートされています。 両方を含むハイブリッド アプリケーションを使用している場合に、支援技術製品が正常に機能[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]と[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]コントロール。|該当なし。|  
|クリップボードのトピック|すべてのクリップボード操作は通常どおりに動作します。 これは、カット アンド ペーストとの間に含まれます[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]と[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]コントロール。|該当なし。|  
|ドラッグ アンド ドロップ機能|すべてのドラッグ アンド ドロップ操作が通常どおりに動作します。 間での操作が含まれます[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]と[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]コントロール。|該当なし。|  
  
<a name="Windows_Forms_Application_Hosting_Windows"></a>   
## <a name="hosting-wpf-controls-in-windows-forms"></a>Windows フォームでの WPF コントロールのホスト  
 Windows フォーム コントロールのホスト時に、次の相互運用シナリオがサポートされて、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]コントロール。  
  
- 1 つまたは複数のホスト[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]コードの使用を制御します。  
  
- 1 つのシートまたはよりホストのプロパティを関連付ける[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]コントロール。  
  
- 1 つまたは複数のホスト[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]フォーム内のページ。  
  
- 以降、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]ウィンドウ。  
  
- マスター/詳細フォームをホストしている、[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]マスターと[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]詳細。  
  
- マスター/詳細フォームをホストしている、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]マスターと[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]詳細。  
  
- カスタム ホスト[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]コントロール。  
  
- ハイブリッド コントロールをホストします。  
  
### <a name="ambient-properties"></a>アンビエント プロパティ  
 一部のアンビエント プロパティの[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]コントロールが[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]対応します。 これらのアンビエント プロパティを反映する、ホストされている[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]を制御し、上のパブリック プロパティとして公開、<xref:System.Windows.Forms.Integration.ElementHost>コントロール。 <xref:System.Windows.Forms.Integration.ElementHost>コントロールにそれぞれ変換[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]アンビエント プロパティをその[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]と同じです。  
  
 詳細については、次を参照してください。 [Windows フォームと WPF プロパティのマッピング](windows-forms-and-wpf-property-mapping.md)します。  
  
### <a name="behavior"></a>動作  
 次の表では、相互運用の動作について説明します。  
  
|動作|サポート状況|サポートなし|  
|--------------|---------------|-------------------|  
|[透明度]|[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] コントロールのレンダリングでは、透明性をサポートします。 親の背景[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]コントロールの背景になれるホステッド[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]コントロール。|該当なし。|  
|マルチスレッド|さまざまなマルチ スレッドがサポートされています。|両方の[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]と[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]テクノロジは、シングル スレッドの同時実行モデルを想定しています。 デバッグ中に、他のスレッドから framework のオブジェクトへの呼び出しでこの要件を強制する例外が発生します。|  
|セキュリティ|すべての相互運用シナリオでは、完全な信頼が必要です。|部分信頼では、相互運用シナリオは許可されません。|  
|ユーザー補助|すべてのユーザー補助のシナリオがサポートされています。 両方を含むハイブリッド アプリケーションを使用している場合に、支援技術製品が正常に機能[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]と[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]コントロール。|該当なし。|  
|クリップボードのトピック|すべてのクリップボード操作は通常どおりに動作します。 これは、カット アンド ペーストとの間に含まれます[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]と[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]コントロール。|該当なし。|  
|ドラッグ アンド ドロップ機能|すべてのドラッグ アンド ドロップ操作が通常どおりに動作します。 間での操作が含まれます[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]と[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]コントロール。|該当なし。|  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [チュートリアル: WPF での Windows フォーム コントロールのホスト](walkthrough-hosting-a-windows-forms-control-in-wpf.md)
- [チュートリアル: WPF で Windows フォーム複合コントロールのホスト](walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)
- [チュートリアル: Windows フォームでの WPF 複合コントロールをホストしています。](walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
- [Windows フォームと WPF プロパティの割り当て](windows-forms-and-wpf-property-mapping.md)
