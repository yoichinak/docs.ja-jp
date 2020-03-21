---
title: WPF と Windows フォームの相互運用機能
titleSuffix: ''
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms [WPF], interoperability with
- nester interoperation [WPF]
- Windows Forms [WPF], WPF interoperation
- interoperability [WPF], Windows Forms
- hybrid control [WPF interoperability]
ms.assetid: 9e8aa6b6-112c-4579-98d1-c974917df499
ms.openlocfilehash: 76d1e97c92946267aa1217f52c93594fb63d20de
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187150"
---
# <a name="wpf-and-windows-forms-interoperation"></a>WPF と Windows フォームの相互運用性
[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]Windows フォームでは、アプリケーション インターフェイスを作成するための 2 つの異なるアーキテクチャが提供されます。 名前空間<xref:System.Windows.Forms.Integration?displayProperty=nameWithType>には、共通の相互運用シナリオを有効にするクラスが用意されています。 相互運用機能を実装する 2 つの主要な<xref:System.Windows.Forms.Integration.WindowsFormsHost>クラス<xref:System.Windows.Forms.Integration.ElementHost>は、 と です。 このトピックでは、サポートされる相互運用シナリオとサポートされないシナリオについて説明します。  
  
> [!NOTE]
> *ハイブリッド制御*シナリオには、特別な考慮事項があります。 ハイブリッド コントロールには、あるテクノロジからコントロールがネストされ、他のテクノロジのコントロールが含まれる場合。 これは、*ネストされた相互運用*とも呼ばれます。 *マルチレベルハイブリッド コントロール*には、複数のレベルのハイブリッド コントロールの入れ子があります。 入れ子になった複数レベルの相互運用の例としては、別の Windows[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]フォーム コントロールを含むコントロールを含む Windows フォーム コントロールがあります。 マルチレベルハイブリッドコントロールはサポートされていません。  

<a name="Windows_Presentation_Foundation_Application_Hosting"></a>
## <a name="hosting-windows-forms-controls-in-wpf"></a>WPF での Windows フォーム コントロールのホスト  
 コントロールが Windows フォーム コントロールをホスト[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]する場合、次の相互運用シナリオがサポートされます。  
  
- コントロール[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]は、XAML を使用して 1 つ以上の Windows フォーム コントロールをホストできます。  
  
- コードを使用して 1 つ以上の Windows フォーム コントロールをホストできます。  
  
- 他の Windows フォーム コントロールを含む Windows フォーム コンテナー コントロールをホストする場合があります。  
  
- マスター/詳細フォームをホストし、マスターと[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]Windows フォームの詳細をホストできます。  
  
- Windows フォーム マスターと詳細を含むマスター/詳細フォーム[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]をホストする場合があります。  
  
- 1 つ以上の ActiveX コントロールをホストできます。  
  
- 1 つ以上の複合コントロールをホストできます。  
  
- を使用してハイブリッド コントロール[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]をホストする場合があります。  
  
- コードを使用してハイブリッド コントロールをホストする場合があります。  
  
### <a name="layout-support"></a>レイアウトのサポート  
 次の一覧では、要素がホストされた<xref:System.Windows.Forms.Integration.WindowsFormsHost>Windows フォーム コントロールをレイアウト システムに統合しようとする場合[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]の既知の制限事項について説明します。  
  
- Windows フォーム コントロールのサイズを変更できない場合や、特定のサイズにしかサイズを変更できない場合があります。 たとえば、Windows フォーム<xref:System.Windows.Forms.ComboBox>コントロールは、コントロールのフォント サイズで定義される高さ 1 つだけをサポートします。 動的レイアウト[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]では、要素が垂直方向に伸びることを前提とし、ホストされた<xref:System.Windows.Forms.ComboBox>コントロールは期待どおりに伸びない。  
  
- Windows フォーム コントロールは、回転または傾斜できません。 たとえば、ユーザー インターフェイスを 90 度回転すると、ホストされた Windows フォーム コントロールは、その直立した位置を維持します。  
  
- ほとんどの場合、Windows フォーム コントロールは比例スケーリングをサポートしていません。 コントロールの全体的なサイズは拡大または縮小されますが、コントロールの子コントロールとコンポーネント要素は、期待どおりにサイズ変更されないことがあります。 この制限は、各 Windows フォーム コントロールがスケーリングをどの程度サポートしているかによって異なります。  
  
- [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]ユーザ インタフェースでは、要素の Z オーダーを変更して、重複する動作を制御できます。 ホストされた Windows フォーム コントロールは、個別の HWND で描画されるため、常に[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]要素の上に描画されます。  
  
- Windows フォーム コントロールは、フォント サイズに基づく自動スケールをサポートします。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]ユーザー インターフェイスでは、フォント サイズを変更してもレイアウト全体のサイズは変更されませんが、個々の要素のサイズは動的に変更される場合があります。  
  
### <a name="ambient-properties"></a>アンビエント プロパティ  
 コントロールのアンビエント[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]プロパティの一部には、Windows フォームと同等のプロパティがあります。 これらのアンビエント プロパティは、ホストされる Windows フォーム コントロールに反映され、<xref:System.Windows.Forms.Integration.WindowsFormsHost>コントロールのパブリック プロパティとして公開されます。 コントロール<xref:System.Windows.Forms.Integration.WindowsFormsHost>は、各[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]アンビエント プロパティを対応する Windows フォームに変換します。  
  
 詳細については、「 [Windows フォームと WPF プロパティ マッピング](windows-forms-and-wpf-property-mapping.md)」を参照してください。  
  
### <a name="behavior"></a>動作  
 次の表は、相互運用の動作を示しています。  
  
|動作|サポートされています|サポートされていません|  
|--------------|---------------|-------------------|  
|透明性|Windows フォーム コントロールのレンダリングは、透過性をサポートします。 親[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]コントロールの背景は、ホストされた Windows フォーム コントロールの背景になる場合があります。|Windows フォーム コントロールの中には、透過性をサポートしていないものがあります。 たとえば、<xref:System.Windows.Forms.TextBox>および<xref:System.Windows.Forms.ComboBox>コントロールは、 によって[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]ホストされるときには透過的ではありません。|  
|タブ|ホストされた Windows フォーム コントロールのタブ オーダーは、Windows フォーム ベースのアプリケーションでコントロールがホストされている場合と同じです。<br /><br /> コントロールから[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]Windows フォーム コントロールに Tab キーを押すと、Tab キーと Shift キーを押しながら Tab キーを押すと、通常どおり動作します。<br /><br /> プロパティ値が "コントロール<xref:System.Windows.Forms.Control.TabStop%2A>" である`false`Windows フォーム コントロールは、ユーザーがコントロールをタブで移動してもフォーカスを受け取りません。<br /><br /> -<xref:System.Windows.Forms.Integration.WindowsFormsHost>各コントロールには<xref:System.Windows.Forms.Integration.WindowsFormsHost.TabIndex%2A>、コントロールがフォーカスを受<xref:System.Windows.Forms.Integration.WindowsFormsHost>け取るタイミングを決定する値があります。<br />- コンテナー内に<xref:System.Windows.Forms.Integration.WindowsFormsHost>含まれる Windows フォーム コントロールは、プロパティ<xref:System.Windows.Forms.Control.TabIndex%2A>で指定された順序に従います。 最後のタブインデックスからタブ移動すると、次[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]のコントロールが存在する場合は、そのコントロールにフォーカスが置かれます。 フォーカスを設定できる[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]コントロールが他に存在しない場合は、タブ オーダーの最初の Windows フォーム コントロールにタブ移動します。<br />-   <xref:System.Windows.Forms.Integration.WindowsFormsHost.TabIndex%2A>内のコントロールの値<xref:System.Windows.Forms.Integration.WindowsFormsHost>は、コントロールに含まれる兄弟 Windows フォーム<xref:System.Windows.Forms.Integration.WindowsFormsHost>コントロールに対する相対値です。<br />- タブは、コントロール固有の動作を優先します。 たとえば、プロパティ値が " "<xref:System.Windows.Forms.TextBox>の値を<xref:System.Windows.Forms.TextBoxBase.AcceptsTab%2A>持つコントロール`true`の Tab キーを押すと、フォーカスを移動する代わりに、テキスト ボックスにタブが表示されます。|適用不可。|  
|矢印キーによるナビゲーション|-<xref:System.Windows.Forms.Integration.WindowsFormsHost>コントロール内の方向キーを使用したナビゲーションは、通常の Windows フォーム コンテナー コントロールと同じです。<br />-<xref:System.Windows.Forms.Integration.WindowsFormsHost>コントロールに含まれる最初のコントロールの上方向キーと左方向キーは、Shift + Tab キーのキーボード ショートカットと同じ操作を実行します。 フォーカス可能な[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]コントロールがある場合、フォーカスはコントロールの外側<xref:System.Windows.Forms.Integration.WindowsFormsHost>に移動します。 この動作は、最後のコントロール<xref:System.Windows.Forms.ContainerControl>への折り返しが発生しないという点で、標準の動作とは異なります。 フォーカスを設定できる[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]コントロールが他に存在しない場合、タブ オーダーの最後の Windows フォーム コントロールにフォーカスが戻ります。<br />-<xref:System.Windows.Forms.Integration.WindowsFormsHost>コントロールに含まれる最後のコントロールの下方向キーと右方向キーは、Tab キーと同じ操作を実行します。 フォーカス可能な[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]コントロールがある場合、フォーカスはコントロールの外側<xref:System.Windows.Forms.Integration.WindowsFormsHost>に移動します。 この動作は、最初のコントロール<xref:System.Windows.Forms.ContainerControl>に折り返しが発生しないという点で、標準の動作とは異なります。 フォーカスを設定できる[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]コントロールが他に存在しない場合、タブ オーダーの最初の Windows フォーム コントロールにフォーカスが戻ります。|適用不可。|  
|アクセラレータ|アクセラレータは、「サポートされていない」の欄に記載されている場合を除き、通常どおりに動作します。|テクノロジ間で重複するアクセラレータは、通常の重複アクセラレータのようには機能しません。 アクセラレータがテクノロジ間で複製され、Windows フォーム コントロール上に少なくとも 1 つと[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]コントロール上に 1 つ以上のアクセラレータが存在する場合、Windows フォーム コントロールは常にアクセラレータを受け取ります。 重複するアクセラレータが押された場合、フォーカスはコントロール間で切り替えません。|  
|ショートカット キー|ショートカット キーは、"サポートされていません" 列に記載されている場合を除き、通常どおりに機能します。|- 前処理の段階で処理される Windows フォームのショートカット キーは[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]、常にショートカット キーよりも優先されます。 たとえば、Ctrl + S<xref:System.Windows.Forms.ToolStrip>のショートカット キーを持つコントロールが定義されている場合[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]、Ctrl + S に<xref:System.Windows.Forms.ToolStrip>バインドされたコマンドがある場合、コントロール ハンドラーはフォーカスに関係なく、常に最初に呼び出されます。<br />- イベントによって処理される Windows フォーム<xref:System.Windows.Forms.Control.KeyDown>のショートカット キーは[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]、 で最後に処理されます。 この現象を回避するには、Windows フォーム コントロールの<xref:System.Windows.Forms.Control.IsInputKey%2A>メソッドをオーバーライドするか、イベントを<xref:System.Windows.Forms.Control.PreviewKeyDown>処理します。 <xref:System.Windows.Forms.Control.IsInputKey%2A>メソッド`true`から戻るか、イベント ハンドラーでプロパティの<xref:System.Windows.Forms.PreviewKeyDownEventArgs.IsInputKey%2A?displayProperty=nameWithType>値を`true`に設定<xref:System.Windows.Forms.Control.PreviewKeyDown>します。|  
|リターン、受け入れタブ、およびその他のコントロール固有の動作を受け入れます。|既定のキーボード動作を変更するプロパティは、Windows フォーム コントロールが返す<xref:System.Windows.Forms.Control.IsInputKey%2A>`true`メソッドをオーバーライドすることを前提に、通常どおり動作します。|<xref:System.Windows.Forms.Control.KeyDown>イベントを処理することによって既定のキーボード動作を変更する Windows フォーム コントロールは、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]ホスト コントロール内で最後に処理されます。 これらのコントロールは最後に処理されるため、予期しない動作が発生する可能性があります。|  
|イベントの入力と終了|フォーカスがコントロール<xref:System.Windows.Forms.Integration.ElementHost>にフォーカスを合わせない場合、1 つの<xref:System.Windows.Forms.Integration.WindowsFormsHost>コントロールでフォーカスが変更されると、Enter イベントと Leave イベントが通常どおり発生します。|次のフォーカス変更が発生した場合、Enter イベントと Leave イベントは発生しません。<br /><br /> - コントロールの内側から<xref:System.Windows.Forms.Integration.WindowsFormsHost>外側へ<br />- コントロールの外側から<xref:System.Windows.Forms.Integration.WindowsFormsHost>内側へ。<br />- コントロール<xref:System.Windows.Forms.Integration.WindowsFormsHost>の外<br />-<xref:System.Windows.Forms.Integration.WindowsFormsHost>コントロールでホストされている Windows フォーム コントロールから<xref:System.Windows.Forms.Integration.ElementHost>、同じ<xref:System.Windows.Forms.Integration.WindowsFormsHost>コントロール内でホストされるコントロールまで 。|  
|マルチスレッド|マルチスレッドのすべての種類がサポートされています。|Windows フォームと[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]テクノロジは、どちらもシングル スレッド同時実行モデルを想定しています。 デバッグ中に、他のスレッドからフレームワーク オブジェクトを呼び出すと、この要件を適用する例外が発生します。|  
|Security|すべての相互運用シナリオには完全な信頼が必要です。|部分信頼では相互運用シナリオは許可されません。|  
|アクセシビリティ|すべてのユーザー補助シナリオがサポートされています。 Windows フォームと[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]コントロールの両方を含むハイブリッド アプリケーションで使用すると、支援技術製品は正しく機能します。|適用不可。|  
|クリップボード|クリップボード操作はすべて通常どおり動作します。 これには、Windows フォームとコントロールの間で[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]切り取りと貼り付けが含まれます。|適用不可。|  
|ドラッグアンドドロップ機能|すべてのドラッグ アンド ドロップ操作は通常どおり動作します。 これには、Windows フォームとコントロール[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]間の操作が含まれます。|適用不可。|  
  
<a name="Windows_Forms_Application_Hosting_Windows"></a>
## <a name="hosting-wpf-controls-in-windows-forms"></a>Windows フォームでの WPF コントロールのホスティング  
 Windows フォーム コントロールがコントロールをホストする場合、次の相互運用[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]シナリオがサポートされます。  
  
- コードを使用して[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]1 つ以上のコントロールをホストする。  
  
- プロパティ シートと 1 つ以上のホストされたコントロールを[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]関連付ける。  
  
- フォーム内の[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]1 つ以上のページをホストする。  
  
- ウィンドウを[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]開始します。  
  
- Windows フォーム マスターと詳細を含むマスター/[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]詳細フォームのホスト。  
  
- マスターと Windows フォームの詳細[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]を含むマスター/詳細フォームをホストする。  
  
- カスタム[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]コントロールをホストしています。  
  
- ハイブリッド コントロールをホストする。  
  
### <a name="ambient-properties"></a>アンビエント プロパティ  
 Windows フォーム コントロールのアンビエント[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]プロパティの一部は、同等のものを持っています。 これらのアンビエント プロパティは、ホストされた[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]コントロールに反映され、<xref:System.Windows.Forms.Integration.ElementHost>コントロールのパブリック プロパティとして公開されます。 コントロール<xref:System.Windows.Forms.Integration.ElementHost>は、各 Windows フォームアンビエント[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]プロパティを同等のプロパティに変換します。  
  
 詳細については、「 [Windows フォームと WPF プロパティ マッピング](windows-forms-and-wpf-property-mapping.md)」を参照してください。  
  
### <a name="behavior"></a>動作  
 次の表は、相互運用の動作を示しています。  
  
|動作|サポートされています|サポートされていません|  
|--------------|---------------|-------------------|  
|透明性|[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]コントロール レンダリングは、透過性をサポートします。 親の Windows フォーム コントロールの背景は、ホストされた[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]コントロールの背景になる場合があります。|適用不可。|  
|マルチスレッド|マルチスレッドのすべての種類がサポートされています。|Windows フォームと[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]テクノロジは、どちらもシングル スレッド同時実行モデルを想定しています。 デバッグ中に、他のスレッドからフレームワーク オブジェクトを呼び出すと、この要件を適用する例外が発生します。|  
|Security|すべての相互運用シナリオには完全な信頼が必要です。|部分信頼では相互運用シナリオは許可されません。|  
|アクセシビリティ|すべてのユーザー補助シナリオがサポートされています。 Windows フォームと[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]コントロールの両方を含むハイブリッド アプリケーションで使用すると、支援技術製品は正しく機能します。|適用不可。|  
|クリップボード|クリップボード操作はすべて通常どおり動作します。 これには、Windows フォームとコントロールの間で[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]切り取りと貼り付けが含まれます。|適用不可。|  
|ドラッグアンドドロップ機能|すべてのドラッグ アンド ドロップ操作は通常どおり動作します。 これには、Windows フォームとコントロール[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]間の操作が含まれます。|適用不可。|  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [チュートリアル: WPF での Windows フォーム コントロールのホスト](walkthrough-hosting-a-windows-forms-control-in-wpf.md)
- [チュートリアル: WPF での Windows フォーム複合コントロールのホスト](walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)
- [チュートリアル: Windows フォームでの WPF 複合コントロールのホスト](walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
- [Windows フォームと WPF プロパティの割り当て](windows-forms-and-wpf-property-mapping.md)
