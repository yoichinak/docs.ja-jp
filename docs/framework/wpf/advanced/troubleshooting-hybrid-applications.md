---
title: ハイブリッド アプリケーションのトラブルシューティング
ms.date: 03/30/2017
helpviewer_keywords:
- overlapping controls [WPF]
- Windows Forms [WPF], interoperability with
- Windows Forms [WPF], WPF interoperation
- interoperability [WPF], Windows Forms
- hybrid applications [WPF interoperability]
- message loops [WPF]
ms.assetid: f440c23f-fa5d-4d5a-852f-ba61150e6405
ms.openlocfilehash: b85a607d2e44d6253359a81118f90e6ee05d2d3f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187323"
---
# <a name="troubleshooting-hybrid-applications"></a>ハイブリッド アプリケーションのトラブルシューティング
<a name="introduction"></a>このトピックでは、ハイブリッド アプリケーションを作成するときに発生する可能性のあるいくつかの一般的な[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]問題を示します。  

<a name="overlapping_controls"></a>
## <a name="overlapping-controls"></a>コントロールの重複  
 コントロールは、期待どおりに重ならない場合があります。 Windows フォームでは、コントロールごとに個別の HWND が使用されます。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]では、ページ上のすべてのコンテンツに対して 1 つの HWND を使用します。 この実装の違いにより、予期しない重複する動作が発生します。  
  
 で[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]ホストされている Windows フォーム コントロールは、常に[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]コンテンツの上部に表示されます。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]コントロールでホストされているコンテンツ<xref:System.Windows.Forms.Integration.ElementHost>は、コントロールの Z オーダーで<xref:System.Windows.Forms.Integration.ElementHost>表示されます。 コントロールを重ねて表示<xref:System.Windows.Forms.Integration.ElementHost>することはできますが、ホストされた[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]コンテンツは結合または相互作用しません。  
  
<a name="child_property"></a>
## <a name="child-property"></a>子プロパティ  
 および<xref:System.Windows.Forms.Integration.WindowsFormsHost><xref:System.Windows.Forms.Integration.ElementHost>クラスは、1 つの子コントロールまたは要素のみをホストできます。 複数のコントロールまたは要素をホストするには、コンテナを子コンテンツとして使用する必要があります。 たとえば、Windows フォーム ボタンとチェック ボックス コントロールを<xref:System.Windows.Forms.Panel?displayProperty=nameWithType>コントロールに追加し、そのパネルを<xref:System.Windows.Forms.Integration.WindowsFormsHost>コントロールの<xref:System.Windows.Forms.Integration.WindowsFormsHost.Child%2A>プロパティに割り当てることができます。 ただし、ボタンとチェック ボックスのコントロールを別々に同じ<xref:System.Windows.Forms.Integration.WindowsFormsHost>コントロールに追加することはできません。  
  
<a name="scaling"></a>
## <a name="scaling"></a>Scaling  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]Windows フォームには、さまざまなスケーリング モデルがあります。 スケーリング[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]変換は Windows フォーム コントロールにとって意味のあるものもあれば、意味がないものもあります。 たとえば、Windows フォーム コントロールを 0 にスケーリングすると機能しますが、同じコントロールを 0 以外の値にスケールバックしようとすると、コントロールのサイズは 0 のままです。 詳細については、「 [Windows フォーム ホスト要素のレイアウトに関する考慮事項](layout-considerations-for-the-windowsformshost-element.md)」を参照してください。  
  
<a name="adapter"></a>
## <a name="adapter"></a>アダプター  
 クラスと<xref:System.Windows.Forms.Integration.WindowsFormsHost><xref:System.Windows.Forms.Integration.ElementHost>を操作するときに混乱が生じる可能性があります。 <xref:System.Windows.Forms.Integration.WindowsFormsHost>クラスと<xref:System.Windows.Forms.Integration.ElementHost>クラスには、コンテンツのホストに使用する*アダプター*と呼ばれる非表示のコンテナーがあります。 要素の<xref:System.Windows.Forms.Integration.WindowsFormsHost>場合、アダプターは<xref:System.Windows.Forms.ContainerControl?displayProperty=nameWithType>クラスから派生します。 コントロールの<xref:System.Windows.Forms.Integration.ElementHost>場合、アダプターは<xref:System.Windows.Controls.DockPanel>要素から派生します。 他の相互運用のトピックでアダプターへの参照を参照する場合、このコンテナーは、説明されています。  
  
<a name="nesting"></a>
## <a name="nesting"></a>入れ子  
 コントロール内の<xref:System.Windows.Forms.Integration.WindowsFormsHost>要素の<xref:System.Windows.Forms.Integration.ElementHost>入れ子はサポートされていません。 要素内の<xref:System.Windows.Forms.Integration.ElementHost>コントロールの<xref:System.Windows.Forms.Integration.WindowsFormsHost>入れ子もサポートされていません。  
  
<a name="focus"></a>
## <a name="focus"></a>Focus  
 Windows フォームでは[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]フォーカスの動作が異なり、ハイブリッド アプリケーションでフォーカスの問題が発生する可能性があります。 たとえば、要素内に<xref:System.Windows.Forms.Integration.WindowsFormsHost>フォーカスがある場合、ページを最小化して復元するか、モーダル ダイアログ ボックスを表示すると、要素内の<xref:System.Windows.Forms.Integration.WindowsFormsHost>フォーカスが失われる可能性があります。 要素<xref:System.Windows.Forms.Integration.WindowsFormsHost>にはまだフォーカスがありますが、その中のコントロールはフォーカスを持っていない可能性があります。  
  
 データの入力規則もフォーカスの影響を受けます。 検証は<xref:System.Windows.Forms.Integration.WindowsFormsHost>要素で機能しますが、要素の外にタブを移動したり、2 つの異なる<xref:System.Windows.Forms.Integration.WindowsFormsHost><xref:System.Windows.Forms.Integration.WindowsFormsHost>要素間でタブを移動したりしても機能しません。  
  
<a name="property_mapping"></a>
## <a name="property-mapping"></a>プロパティの対応  
 一部のプロパティ マッピングでは、Windows フォーム テクノロジと Windows[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]フォーム テクノロジ間の異なる実装をブリッジするために、広範な解釈が必要になります。 プロパティ マッピングを使用すると、フォント、色、およびその他のプロパティの変更にコードで対応できます。 一般に、プロパティ の割り当ては、*プロパティ*変更イベント*またはプロパティ変更*時の呼び出しをリッスンし、子コントロールまたはそのアダプターに適切なプロパティを設定することによって機能します。 詳細については、「 [Windows フォームと WPF プロパティ マッピング](windows-forms-and-wpf-property-mapping.md)」を参照してください。  
  
<a name="layoutrelated_properties_on_hosted_content"></a>
## <a name="layout-related-properties-on-hosted-content"></a>ホストされたコンテンツのレイアウト関連のプロパティ  
 または<xref:System.Windows.Forms.Integration.ElementHost.Child%2A?displayProperty=nameWithType><xref:System.Windows.Forms.Integration.WindowsFormsHost.Child%2A?displayProperty=nameWithType>プロパティが割り当てられると、ホストされたコンテンツのレイアウト関連のプロパティが自動的に設定されます。 これらのコンテンツ プロパティを変更すると、予期しないレイアウト動作が発生する可能性があります。  
  
 ホストされたコンテンツは、<xref:System.Windows.Forms.Integration.WindowsFormsHost>および<xref:System.Windows.Forms.Integration.ElementHost>親を埋めるためにドッキングされます。 この塗りつぶし動作を有効にするには、子プロパティを設定するときにいくつかのプロパティが設定されます。 次の表に、 クラスと<xref:System.Windows.Forms.Integration.ElementHost><xref:System.Windows.Forms.Integration.WindowsFormsHost>クラスによって設定されるコンテンツ プロパティを示します。  
  
|ホスト クラス|コンテンツプロパティ|  
|----------------|------------------------|  
|<xref:System.Windows.Forms.Integration.ElementHost>|<xref:System.Windows.FrameworkElement.Height%2A><br /><br /> <xref:System.Windows.FrameworkElement.Width%2A><br /><br /> <xref:System.Windows.FrameworkElement.Margin%2A><br /><br /> <xref:System.Windows.FrameworkElement.VerticalAlignment%2A><br /><br /> <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>|  
|<xref:System.Windows.Forms.Integration.WindowsFormsHost>|<xref:System.Windows.Forms.Control.Margin%2A><br /><br /> <xref:System.Windows.Forms.Control.Dock%2A><br /><br /> <xref:System.Windows.Forms.Control.AutoSize%2A><br /><br /> <xref:System.Windows.Forms.Control.Location%2A><br /><br /> <xref:System.Windows.Forms.Control.MaximumSize%2A>|  
  
 ホストされたコンテンツにこれらのプロパティを直接設定しないでください。 詳細については、「 [Windows フォーム ホスト要素のレイアウトに関する考慮事項](layout-considerations-for-the-windowsformshost-element.md)」を参照してください。  
  
<a name="navigation_applications"></a>
## <a name="navigation-applications"></a>ナビゲーションアプリケーション  
 ナビゲーション アプリケーションでは、ユーザー状態を維持できません。 要素<xref:System.Windows.Forms.Integration.WindowsFormsHost>は、ナビゲーション アプリケーションで使用されるときにコントロールを再作成します。 子コントロールの再作成は、ユーザーが<xref:System.Windows.Forms.Integration.WindowsFormsHost>要素をホストしているページから移動し、その後、その子コントロールに戻ったときに発生します。 ユーザーが入力したコンテンツはすべて失われます。  
  
<a name="message_loop_interoperation"></a>
## <a name="message-loop-interoperation"></a>メッセージ ループの相互運用  
 Windows フォーム メッセージ ループを操作する場合、メッセージが期待どおりに処理されないことがあります。 メソッド<xref:System.Windows.Forms.Integration.WindowsFormsHost.EnableWindowsFormsInterop%2A>は、コンストラクターによって呼<xref:System.Windows.Forms.Integration.WindowsFormsHost>び出されます。 このメソッドは、メッセージ ループに[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]メッセージ フィルターを追加します。 このフィルタ<xref:System.Windows.Forms.Control?displayProperty=nameWithType>は、<xref:System.Windows.Forms.Control.PreProcessMessage%2A?displayProperty=nameWithType>メッセージのターゲットである場合にメソッドを呼び出し、メッセージを変換/ディスパッチします。  
  
 を使用<xref:System.Windows.Window><xref:System.Windows.Forms.Application.Run%2A?displayProperty=nameWithType>して Windows フォーム のメッセージ ループを表示する場合、<xref:System.Windows.Forms.Integration.ElementHost.EnableModelessKeyboardInterop%2A>メソッドを呼び出す場合を除いて何も入力できません。 この<xref:System.Windows.Forms.Integration.ElementHost.EnableModelessKeyboardInterop%2A>メソッドは、 <xref:System.Windows.Window> <xref:System.Windows.Forms.IMessageFilter?displayProperty=nameWithType>を受け取り、キー関連のメッセージをメッセージ[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]ループに再ルーティングする を追加します。 詳細については、「 [Windows フォームと WPF 相互運用性の入力アーキテクチャ](windows-forms-and-wpf-interoperability-input-architecture.md)」を参照してください。  
  
<a name="opacity_and_layering"></a>
## <a name="opacity-and-layering"></a>不透明度とレイヤー  
 この<xref:System.Windows.Interop.HwndHost>クラスは、階層化をサポートしていません。 <xref:System.Windows.UIElement.Opacity%2A>つまり、要素のプロパティを<xref:System.Windows.Forms.Integration.WindowsFormsHost>設定しても効果がなく、 に[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<xref:System.Windows.Window.AllowsTransparency%2A>`true`設定されている他のウィンドウではブレンドは行われません。  
  
<a name="dispose"></a>
## <a name="dispose"></a>Dispose  
 クラスを適切に破棄しないと、リソースがリークする可能性があります。 ハイブリッド アプリケーションで、<xref:System.Windows.Forms.Integration.WindowsFormsHost>と<xref:System.Windows.Forms.Integration.ElementHost>クラスが破棄されていることを確認するか、リソースをリークする可能性があります。 Windows フォームは<xref:System.Windows.Forms.Integration.ElementHost>、非モーダル<xref:System.Windows.Forms.Form>親が閉じるときにコントロールを破棄します。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]アプリケーションが<xref:System.Windows.Forms.Integration.WindowsFormsHost>シャットダウンしたときに要素を破棄します。 Windows フォーム メッセージ<xref:System.Windows.Forms.Integration.WindowsFormsHost>ループ<xref:System.Windows.Window>内の要素を表示できます。 この場合、アプリケーションがシャットダウンしているという通知をコードが受け取らない可能性があります。  
  
<a name="enabling_visual_styles"></a>
## <a name="enabling-visual-styles"></a>視覚スタイルを有効にする  
 Windows フォーム コントロールの Visual スタイルが有効になっていない可能性があります。 この<xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType>メソッドは、Windows フォーム アプリケーションのテンプレートで呼び出されます。 このメソッドは既定では呼び出されませんが、Visual Studio を使用してプロジェクトを作成すると、Comctl32.dll のバージョン 6.0 が利用可能な場合は、コントロールの Microsoft Windows XP ビジュアル スタイルが使用されます。 スレッドでハンドルを<xref:System.Windows.Forms.Application.EnableVisualStyles%2A>作成する前に、このメソッドを呼び出す必要があります。 詳細については、「[方法 : ハイブリッド アプリケーションで Visual Styles を有効にする](how-to-enable-visual-styles-in-a-hybrid-application.md)」を参照してください。  
  
<a name="licensed_controls"></a>
## <a name="licensed-controls"></a>ライセンスコントロール  
 ユーザーに対してメッセージ ボックスにライセンス情報を表示するライセンスを受けた Windows フォーム コントロールは、ハイブリッド アプリケーションで予期しない動作を引き起こす可能性があります。 一部のライセンス コントロールは、ハンドルの作成に応じてダイアログ ボックスを表示します。 たとえば、ライセンスを持つコントロールは、ライセンスが必要であることをユーザーに通知したり、ユーザーがコントロールの 3 つの試用版を使用していることをユーザーに通知する場合があります。  
  
 要素<xref:System.Windows.Forms.Integration.WindowsFormsHost>は<xref:System.Windows.Interop.HwndHost>クラスから派生し、子コントロールのハンドルはメソッド内に作成されます<xref:System.Windows.Forms.Integration.WindowsFormsHost.BuildWindowCore%2A>。 この<xref:System.Windows.Interop.HwndHost>クラスでは、メソッドでメッセージを<xref:System.Windows.Forms.Integration.WindowsFormsHost.BuildWindowCore%2A>処理することはできませんが、ダイアログ ボックスを表示するとメッセージが送信されます。 このライセンスシナリオを有効にするには、要素の<xref:System.Windows.Forms.Control.CreateControl%2A?displayProperty=nameWithType>子として割り当てる前に、コントロール<xref:System.Windows.Forms.Integration.WindowsFormsHost>のメソッドを呼び出します。  
  
<a name="wpf_designer"></a>
## <a name="wpf-designer"></a>WPF デザイナー  
 WPF コンテンツをデザインするには、Visual Studio の WPF デザイナーを使用します。 次のセクションでは、WPF デザイナーを使用してハイブリッド アプリケーションを作成するときに発生する可能性のある一般的な問題を示します。  
  
### <a name="backcolortransparent-is-ignored-at-design-time"></a>デザイン時に透明な色は無視されます  
 デザイン<xref:System.Windows.Forms.Integration.ElementHost.BackColorTransparent%2A>時にプロパティが期待どおりに機能しない可能性があります。  
  
 WPF コントロールが表示可能な親コントロールにない場合、WPF ランタイムはその値<xref:System.Windows.Forms.Integration.ElementHost.BackColorTransparent%2A>を無視します。 無視される<xref:System.Windows.Forms.Integration.ElementHost.BackColorTransparent%2A>可能性があるのは、<xref:System.Windows.Forms.Integration.ElementHost>オブジェクトが別<xref:System.AppDomain>の . ただし、アプリケーションを実行すると、<xref:System.Windows.Forms.Integration.ElementHost.BackColorTransparent%2A>期待どおりに動作します。  
  
### <a name="design-time-error-list-appears-when-the-obj-folder-is-deleted"></a>obj フォルダが削除されると、デザイン時エラー一覧が表示される  
 obj フォルダが削除されると、デザイン時のエラー一覧が表示されます。  
  
 を使用して<xref:System.Windows.Forms.Integration.ElementHost>デザインする場合、Windows フォーム デザイナーは、プロジェクトの obj フォルダー内のデバッグ フォルダーまたはリリース フォルダーで生成されたファイルを使用します。 これらのファイルを削除すると、デザイン時エラーリストが表示されます。 この問題を解決するには、プロジェクトを再構築します。 詳細については、「 [Windows フォーム デザイナーのデザイン時エラー](../../winforms/controls/design-time-errors-in-the-windows-forms-designer.md)」を参照してください。  
  
<a name="elementhost_and_ime"></a>
## <a name="elementhost-and-ime"></a>要素ホストと IME  
 現在でホストされている WPF<xref:System.Windows.Forms.Integration.ElementHost>コントロールは、プロパティ<xref:System.Windows.Forms.Control.ImeMode%2A>をサポートしていません。 に対<xref:System.Windows.Forms.Control.ImeMode%2A>する変更は、ホストされたコントロールによって無視されます。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [WPF デザイナーでの相互運用性](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/bb628658(v=vs.100))
- [Windows フォームと WPF の相互運用性入力アーキテクチャ](windows-forms-and-wpf-interoperability-input-architecture.md)
- [方法 : ハイブリッド アプリケーションで視覚スタイルを有効にする](how-to-enable-visual-styles-in-a-hybrid-application.md)
- [WindowsFormsHost 要素のレイアウトに関する考慮事項](layout-considerations-for-the-windowsformshost-element.md)
- [Windows フォームと WPF プロパティの割り当て](windows-forms-and-wpf-property-mapping.md)
- [Windows フォーム デザイナーでのデザイン時エラー](../../winforms/controls/design-time-errors-in-the-windows-forms-designer.md)
- [移行と相互運用性](migration-and-interoperability.md)
