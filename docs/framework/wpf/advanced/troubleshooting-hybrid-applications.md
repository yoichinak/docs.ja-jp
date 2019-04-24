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
ms.openlocfilehash: 707e77ac69878c1c7fb8e975c1f90ad657228d1a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59079676"
---
# <a name="troubleshooting-hybrid-applications"></a>ハイブリッド アプリケーションのトラブルシューティング
<a name="introduction"></a> このトピックでは、両方を使用するハイブリッド アプリケーションを作成するときに発生する可能性がある一般的な問題を示します[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]と[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]テクノロジ。  

<a name="overlapping_controls"></a>   
## <a name="overlapping-controls"></a>コントロールの重複  
 想像どおり、コントロールが重複しない可能性があります。 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 各コントロールの個別の HWND を使用します。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ページ上のすべてのコンテンツには、1 つの HWND を使用します。 この実装の違いにより、予期しない重複する動作。  
  
 A[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]でホストされているコントロール[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]の上に常に表示されます、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]コンテンツ。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ホストされているコンテンツ、<xref:System.Windows.Forms.Integration.ElementHost>の z オーダーでコントロールが表示されます、<xref:System.Windows.Forms.Integration.ElementHost>コントロール。 重複することは<xref:System.Windows.Forms.Integration.ElementHost>、コントロールではなく、ホストされている[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]コンテンツが結合または対話していません。  
  
<a name="child_property"></a>   
## <a name="child-property"></a>子プロパティ  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>と<xref:System.Windows.Forms.Integration.ElementHost>クラスは、1 つの子コントロールまたは要素のみをホストできます。 1 つ以上のコントロールまたは要素をホストするには、子コンテンツとしてコンテナーを使用する必要があります。 たとえば、追加する[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]ボタンとチェック ボックス コントロールを<xref:System.Windows.Forms.Panel?displayProperty=nameWithType>、制御しするパネルを割り当てる、<xref:System.Windows.Forms.Integration.WindowsFormsHost>コントロールの<xref:System.Windows.Forms.Integration.WindowsFormsHost.Child%2A>プロパティ。 ただしに追加できません、ボタンおよびチェック ボックス コントロールとは別に、同じ<xref:System.Windows.Forms.Integration.WindowsFormsHost>コントロール。  
  
<a name="scaling"></a>   
## <a name="scaling"></a>スケーリング  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]異なるスケーリング モデルがあります。 いくつか[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]にとって意味のある拡大縮小の変換[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]コントロールが、他のユーザーはいません。 たとえば、スケーリング、[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]コントロールを 0 に機能しますが、0 以外の値に同じコントロールのスケール設定しようとする場合、コントロールのサイズは 0 のままです。 詳細については、次を参照してください。 [WindowsFormsHost 要素のレイアウトに関する考慮事項](layout-considerations-for-the-windowsformshost-element.md)します。  
  
<a name="adapter"></a>   
## <a name="adapter"></a>アダプター  
 使用する場合、混乱にすることがあります、<xref:System.Windows.Forms.Integration.WindowsFormsHost>と<xref:System.Windows.Forms.Integration.ElementHost>クラスを非表示コンテナーが含まれているためです。 両方の<xref:System.Windows.Forms.Integration.WindowsFormsHost>と<xref:System.Windows.Forms.Integration.ElementHost>クラスがある、という名前の非表示コンテナー、*アダプター*コンテンツをホストするために使用します。 <xref:System.Windows.Forms.Integration.WindowsFormsHost>から派生した要素のアダプター、<xref:System.Windows.Forms.ContainerControl?displayProperty=nameWithType>クラス。 <xref:System.Windows.Forms.Integration.ElementHost>コントロール、アダプターがから派生、<xref:System.Windows.Controls.DockPanel>要素。 アダプターは、他の相互運用のトピックへの参照が表示されたら、このコンテナーは、説明する内容です。  
  
<a name="nesting"></a>   
## <a name="nesting"></a>入れ子  
 入れ子、<xref:System.Windows.Forms.Integration.WindowsFormsHost>内の要素、<xref:System.Windows.Forms.Integration.ElementHost>コントロールはサポートされていません。 入れ子、<xref:System.Windows.Forms.Integration.ElementHost>内の制御、<xref:System.Windows.Forms.Integration.WindowsFormsHost>要素もサポートされていません。  
  
<a name="focus"></a>   
## <a name="focus"></a>フォーカス  
 フォーカスの動作が異なる方法で[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]と[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]問題に焦点を当てていることを意味するハイブリッド アプリケーションで発生します。 内でフォーカスがある場合など、<xref:System.Windows.Forms.Integration.WindowsFormsHost>を最小限に抑えると、ページを復元またはモーダル ダイアログ ボックスを表示、内でフォーカスいずれかを<xref:System.Windows.Forms.Integration.WindowsFormsHost>要素が失われる可能性があります。 <xref:System.Windows.Forms.Integration.WindowsFormsHost>要素がまだ、フォーカスがその内部のコントロールがない場合があります。  
  
 データの検証は、フォーカスの影響を受けます。 検証の動作、<xref:System.Windows.Forms.Integration.WindowsFormsHost>要素が、これは機能しません帯 タブ、<xref:System.Windows.Forms.Integration.WindowsFormsHost>要素、または 2 つの異なる間<xref:System.Windows.Forms.Integration.WindowsFormsHost>要素。  
  
<a name="property_mapping"></a>   
## <a name="property-mapping"></a>プロパティのマッピング  
 いくつかのプロパティ マッピングが複数の異なる実装間をブリッジする広範な解釈が必要です、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]と[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]テクノロジ。 プロパティ マッピングには、フォント、色、およびその他のプロパティの変更に対応するため、コードが有効にします。 一般に、プロパティ マッピングがリッスンするかによって機能*プロパティ*変更イベントまたは*プロパティ*呼び出し、および子コントロールまたはそのアダプターのいずれかの適切なプロパティの設定を変更します。 詳細については、次を参照してください。 [Windows フォームと WPF プロパティのマッピング](windows-forms-and-wpf-property-mapping.md)します。  
  
<a name="layoutrelated_properties_on_hosted_content"></a>   
## <a name="layout-related-properties-on-hosted-content"></a>ホストされるコンテンツにレイアウト関連のプロパティ  
 ときに、<xref:System.Windows.Forms.Integration.WindowsFormsHost.Child%2A?displayProperty=nameWithType>または<xref:System.Windows.Forms.Integration.ElementHost.Child%2A?displayProperty=nameWithType>プロパティが割り当てられる、ホストされたコンテンツにいくつかのレイアウトに関連するプロパティが自動的に設定されます。 これらのコンテンツ プロパティを変更すると、レイアウトの予期しない動作が発生することができます。  
  
 ホストされているコンテンツが全体にドッキングされて、<xref:System.Windows.Forms.Integration.WindowsFormsHost>と<xref:System.Windows.Forms.Integration.ElementHost>親。 この動作を有効にするには、いくつかのプロパティは、子プロパティを設定するときに設定されます。 次の表にリストによりコンテンツのプロパティが設定される、<xref:System.Windows.Forms.Integration.ElementHost>と<xref:System.Windows.Forms.Integration.WindowsFormsHost>クラス。  
  
|ホスト クラス|コンテンツのプロパティ|  
|----------------|------------------------|  
|<xref:System.Windows.Forms.Integration.ElementHost>|<xref:System.Windows.FrameworkElement.Height%2A><br /><br /> <xref:System.Windows.FrameworkElement.Width%2A><br /><br /> <xref:System.Windows.FrameworkElement.Margin%2A><br /><br /> <xref:System.Windows.FrameworkElement.VerticalAlignment%2A><br /><br /> <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>|  
|<xref:System.Windows.Forms.Integration.WindowsFormsHost>|<xref:System.Windows.Forms.Control.Margin%2A><br /><br /> <xref:System.Windows.Forms.Control.Dock%2A><br /><br /> <xref:System.Windows.Forms.Control.AutoSize%2A><br /><br /> <xref:System.Windows.Forms.Control.Location%2A><br /><br /> <xref:System.Windows.Forms.Control.MaximumSize%2A>|  
  
 ホストされたコンテンツに直接これらのプロパティを設定しないでください。 詳細については、次を参照してください。 [WindowsFormsHost 要素のレイアウトに関する考慮事項](layout-considerations-for-the-windowsformshost-element.md)します。  
  
<a name="navigation_applications"></a>   
## <a name="navigation-applications"></a>ナビゲーション アプリケーション  
 ナビゲーション アプリケーションは、ユーザー状態を保持しない場合があります。 <xref:System.Windows.Forms.Integration.WindowsFormsHost>要素は、ナビゲーション アプリケーションを使用すると、そのコントロールを再作成されます。 ユーザーがページのホストから移動するときに子コントロールを再作成が発生した、<xref:System.Windows.Forms.Integration.WindowsFormsHost>要素とそれを返します。 ユーザーが型指定されたコンテンツはすべて失われます。  
  
<a name="message_loop_interoperation"></a>   
## <a name="message-loop-interoperation"></a>メッセージ ループの相互運用  
 使用する場合[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]期待どおりにメッセージ ループでは、メッセージは処理されません。 <xref:System.Windows.Forms.Integration.WindowsFormsHost.EnableWindowsFormsInterop%2A>メソッドを呼び出して、<xref:System.Windows.Forms.Integration.WindowsFormsHost>コンス トラクター。 このメソッドにメッセージ フィルターを追加、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]メッセージ ループします。 このフィルターを呼び出す、<xref:System.Windows.Forms.Control.PreProcessMessage%2A?displayProperty=nameWithType>メソッド場合、<xref:System.Windows.Forms.Control?displayProperty=nameWithType>メッセージの対象となったとメッセージの変換/ディスパッチします。  
  
 表示する場合、<xref:System.Windows.Window>で、[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]とメッセージ ループ<xref:System.Windows.Forms.Application.Run%2A?displayProperty=nameWithType>を呼び出さない限り、何も入力することはできません、<xref:System.Windows.Forms.Integration.ElementHost.EnableModelessKeyboardInterop%2A>メソッド。 <xref:System.Windows.Forms.Integration.ElementHost.EnableModelessKeyboardInterop%2A>メソッドは、<xref:System.Windows.Window>を追加し、 <xref:System.Windows.Forms.IMessageFilter?displayProperty=nameWithType>、キーに関連するメッセージの経路を変更する、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]メッセージ ループします。 詳細については、次を参照してください。 [Windows フォームと WPF の相互運用性入力アーキテクチャ](windows-forms-and-wpf-interoperability-input-architecture.md)します。  
  
<a name="opacity_and_layering"></a>   
## <a name="opacity-and-layering"></a>不透明度と階層化  
 <xref:System.Windows.Interop.HwndHost>クラスは、階層化をサポートしていません。 つまり、その設定、<xref:System.Windows.UIElement.Opacity%2A>プロパティを<xref:System.Windows.Forms.Integration.WindowsFormsHost>要素に効果がないと、他のブレンドは発生しません[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]が windows<xref:System.Windows.Window.AllowsTransparency%2A>設定`true`します。  
  
<a name="dispose"></a>   
## <a name="dispose"></a>Dispose  
 クラスを正しく破棄しないと、リソースがリークすることができます。 ハイブリッド アプリケーションで、<xref:System.Windows.Forms.Integration.WindowsFormsHost>と<xref:System.Windows.Forms.Integration.ElementHost>クラスが破棄されると、またはリソースがリークする可能性があります。 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 破棄します<xref:System.Windows.Forms.Integration.ElementHost>タイミングを制御、非モーダル<xref:System.Windows.Forms.Form>親を閉じます。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 破棄<xref:System.Windows.Forms.Integration.WindowsFormsHost>要素、アプリケーションがシャット ダウンします。 表示することができます、<xref:System.Windows.Forms.Integration.WindowsFormsHost>内の要素を<xref:System.Windows.Window>で、[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]メッセージ ループします。 この場合、コードは、アプリケーションのシャット ダウンの通知を受け取れない可能性があります。  
  
<a name="enabling_visual_styles"></a>   
## <a name="enabling-visual-styles"></a>視覚スタイルを有効にする  
 [!INCLUDE[TLA#tla_winxp](../../../../includes/tlasharptla-winxp-md.md)] 上の visual スタイルを[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]制御を有効にしない場合があります。 <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType>用のテンプレートでメソッドが呼び出された、[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]アプリケーション。 使用する場合、既定では、このメソッドが呼び出されませんが[!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)]取得するは、プロジェクトを作成する[!INCLUDE[TLA#tla_winxp](../../../../includes/tlasharptla-winxp-md.md)]Comctl32.dll のバージョン 6.0 が使用可能な場合は、コントロールのビジュアルをスタイル設定します。 呼び出す必要があります、<xref:System.Windows.Forms.Application.EnableVisualStyles%2A>メソッド ハンドルは、スレッドで作成する前にします。 詳細については、「[方法 :ハイブリッド アプリケーションで視覚スタイルを有効にする](how-to-enable-visual-styles-in-a-hybrid-application.md)します。  
  
<a name="licensed_controls"></a>   
## <a name="licensed-controls"></a>ライセンスされたコントロール  
 ライセンス[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]をユーザーにメッセージ ボックスにライセンス情報を表示するコントロールをハイブリッド アプリケーションで予期しない動作が発生する可能性があります。 一部のライセンスされたコントロールは、作成を処理する応答 ダイアログ ボックスを表示します。 たとえば、ライセンスが必要なまたはユーザーにある 3 つのコントロールの残りの試用、ライセンスされたコントロールはユーザーに通知可能性があります。  
  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>から派生した要素、<xref:System.Windows.Interop.HwndHost>クラス、および子コントロールのハンドル内に作成、<xref:System.Windows.Forms.Integration.WindowsFormsHost.BuildWindowCore%2A>メソッド。 <xref:System.Windows.Interop.HwndHost>クラスで処理されるメッセージを許可しません、<xref:System.Windows.Forms.Integration.WindowsFormsHost.BuildWindowCore%2A>メソッドが、ダイアログ ボックスの表示とメッセージが送信されます。 このライセンスのシナリオを有効にする、<xref:System.Windows.Forms.Control.CreateControl%2A?displayProperty=nameWithType>として割り当てる前にコントロールのメソッド、<xref:System.Windows.Forms.Integration.WindowsFormsHost>要素の子。  
  
<a name="wpf_designer"></a>   
## <a name="wpf-designer"></a>WPF デザイナー  
 使用して、WPF のコンテンツをデザインすることができます、[!INCLUDE[wpfdesigner_current_long](../../../../includes/wpfdesigner-current-long-md.md)]します。 次のセクションでは、使用してハイブリッド アプリケーションを作成するときに発生する可能性がある一般的な問題を一覧表示、[!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)]します。  
  
### <a name="backcolortransparent-is-ignored-at-design-time"></a>BackColorTransparent はデザイン時に無視されます。  
 <xref:System.Windows.Forms.Integration.ElementHost.BackColorTransparent%2A>プロパティがデザイン時に期待どおりに動作しない可能性があります。  
  
 WPF コントロールが表示される親にない場合は、WPF ランタイムが無視されます、<xref:System.Windows.Forms.Integration.ElementHost.BackColorTransparent%2A>値。 理由を<xref:System.Windows.Forms.Integration.ElementHost.BackColorTransparent%2A>が無視される場合は<xref:System.Windows.Forms.Integration.ElementHost>個別のオブジェクトが作成される<xref:System.AppDomain>。 ただし、アプリケーションを実行する<xref:System.Windows.Forms.Integration.ElementHost.BackColorTransparent%2A>が想定どおりに機能します。  
  
### <a name="design-time-error-list-appears-when-the-obj-folder-is-deleted"></a>Obj フォルダーが削除されたときに、デザイン時のエラーの一覧が表示されます。  
 Obj フォルダーが削除された場合は、デザイン時エラーの一覧が表示されます。  
  
 使用してデザインするときに<xref:System.Windows.Forms.Integration.ElementHost>、Windows フォーム デザイナーは、プロジェクトの obj フォルダー内のデバッグまたはリリース フォルダーに生成されたファイルを使用します。 これらのファイルを削除すると、デザイン時のエラーの一覧が表示されます。 この問題を解決するには、プロジェクトをリビルドします。 詳細については、次を参照してください。 [、Windows フォーム デザイナーでデザイン時エラー](../../winforms/controls/design-time-errors-in-the-windows-forms-designer.md)します。  
  
<a name="elementhost_and_ime"></a>   
## <a name="elementhost-and-ime"></a>ElementHost と IME  
 ホストされている WPF コントロール、<xref:System.Windows.Forms.Integration.ElementHost>はサポートされていません、<xref:System.Windows.Forms.Control.ImeMode%2A>プロパティ。 変更<xref:System.Windows.Forms.Control.ImeMode%2A>によってホストされるコントロールは無視されます。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [WPF デザイナーでの相互運用性](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/bb628658(v=vs.100))
- [Windows フォームと WPF の相互運用性入力アーキテクチャ](windows-forms-and-wpf-interoperability-input-architecture.md)
- [方法: ハイブリッド アプリケーションで視覚スタイルを有効にします。](how-to-enable-visual-styles-in-a-hybrid-application.md)
- [WindowsFormsHost 要素のレイアウトに関する考慮事項](layout-considerations-for-the-windowsformshost-element.md)
- [Windows フォームと WPF プロパティの割り当て](windows-forms-and-wpf-property-mapping.md)
- [Windows フォーム デザイナーでのデザイン時エラー](../../winforms/controls/design-time-errors-in-the-windows-forms-designer.md)
- [移行と相互運用性](migration-and-interoperability.md)
