---
title: Windows フォームと WPF プロパティの割り当て
ms.date: 03/30/2017
helpviewer_keywords:
- property mapping [WPF interoperability]
- Windows Forms [WPF], interoperability with
- Windows Forms [WPF], WPF interoperation
- interoperability [WPF], Windows Forms
- WindowsFormsHost element property mapping [WPF]
ms.assetid: 999d8298-9c04-467d-a453-86e41002057d
ms.openlocfilehash: a7d78837a141ed322da42629501cee6dcc9143e1
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59088822"
---
# <a name="windows-forms-and-wpf-property-mapping"></a>Windows フォームと WPF プロパティの割り当て
[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]と[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]テクノロジに 2 つのプロパティが似ていますが、異なるモデルがあります。 *プロパティ マッピング*2 つのアーキテクチャ間の相互運用をサポートし、次の機能を提供します。  
  
-   ホスト環境で関連するプロパティの変更をホストされるコントロールまたは要素にマップする簡単にします。  
  
-   既定の処理のほとんどを一般的にマッピングするために使用されるプロパティを提供します。  
  
-   簡単に削除すると、オーバーライド、または既定のプロパティの拡張を許可します。  
  
-   ホストのプロパティ値の変更が自動的に検出され、ホストされるコントロールまたは要素に変換するようにします。  
  
> [!NOTE]
>  プロパティ変更イベントは、ホストしているコントロールまたは要素の階層は反映されません。 ローカル プロパティの値が直接設定、スタイル、継承、データ バインディング、またはプロパティの値を変更するその他のメカニズムのために変更されない場合は、プロパティの変換は実行されません。  
  
 使用して、<xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A>プロパティを<xref:System.Windows.Forms.Integration.WindowsFormsHost>要素と<xref:System.Windows.Forms.Integration.ElementHost.PropertyMap%2A>プロパティを<xref:System.Windows.Forms.Integration.ElementHost>プロパティ マッピングにアクセスするコントロール。  
  
## <a name="property-mapping-with-the-windowsformshost-element"></a>WindowsFormsHost 要素のプロパティ マッピング  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>要素は、既定値を変換[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]プロパティを[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]対応する次の変換テーブルを使用します。  
  
|Windows Presentation Foundation のホスティング|Windows フォーム|相互運用の動作|  
|---------------------------------------------|-------------------|-----------------------------|  
|<xref:System.Windows.Controls.Control.Background%2A><br /><br /> (<xref:System.Windows.Media.Brush?displayProperty=nameWithType>)|<xref:System.Windows.Forms.Control.BackColor%2A><br /><br /> (<xref:System.Drawing.Color?displayProperty=nameWithType>)|<xref:System.Windows.Forms.Integration.WindowsFormsHost>要素セット、<xref:System.Windows.Forms.Control.BackColor%2A>ホストされるコントロールのプロパティと<xref:System.Windows.Forms.Control.BackgroundImage%2A>ホストされるコントロールのプロパティ。 マッピングは、次の規則を使用して実行されます。<br /><br /> If<xref:System.Windows.Controls.Control.Background%2A>が純色を変換して設定するため、<xref:System.Windows.Forms.Control.BackColor%2A>ホストされるコントロールのプロパティ。 <xref:System.Windows.Forms.Control.BackColor%2A>プロパティが設定されていないホスト型のコントロールでは、ホストされるコントロールの値を継承できるため、<xref:System.Windows.Forms.Control.BackColor%2A>プロパティ。 **注:** ホストされるコントロールは、透明度をサポートしていません。 割り当てられている任意の色<xref:System.Windows.Forms.Control.BackColor%2A>0 xff のアルファ値を持つ、完全に不透明である必要があります。 <br /><br /> If<xref:System.Windows.Controls.Control.Background%2A>純色ではありません、<xref:System.Windows.Forms.Integration.WindowsFormsHost>コントロールからビットマップを作成する、<xref:System.Windows.Controls.Control.Background%2A>プロパティ。 <xref:System.Windows.Forms.Integration.WindowsFormsHost>コントロールは、このビットマップを割り当てます、<xref:System.Windows.Forms.Control.BackgroundImage%2A>ホストされるコントロールのプロパティ。 これは、透過性のような効果を提供します。 **注:** この動作をオーバーライドすることができますか、削除することができます、<xref:System.Windows.Controls.Control.Background%2A>プロパティ マッピングします。|  
|<xref:System.Windows.FrameworkElement.Cursor%2A>|<xref:System.Windows.Forms.Control.Cursor%2A>|既定のマッピングが割り当てされていない場合<xref:System.Windows.Forms.Integration.WindowsFormsHost>の先祖が見つかるまで、コントロールがその先祖の階層を走査その<xref:System.Windows.FrameworkElement.Cursor%2A>プロパティ セット。 この値は、最も近い対応する翻訳[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]カーソル。<br /><br /> 場合の既定のマッピング、<xref:System.Windows.FrameworkElement.ForceCursor%2A>プロパティが再割り当てされていない、トラバーサルの停止を持つ最初の先祖に対して<xref:System.Windows.FrameworkElement.ForceCursor%2A>に設定`true`します。|  
|<xref:System.Windows.FrameworkElement.FlowDirection%2A><br /><br /> (<xref:System.Windows.FlowDirection?displayProperty=nameWithType>)|<xref:System.Windows.Forms.Control.RightToLeft%2A><br /><br /> (<xref:System.Windows.Forms.RightToLeft?displayProperty=nameWithType>)|<xref:System.Windows.FlowDirection.LeftToRight> マップ<xref:System.Windows.Forms.RightToLeft.No>します。<br /><br /> <xref:System.Windows.FlowDirection.RightToLeft> マップ<xref:System.Windows.Forms.RightToLeft.Yes>します。<br /><br /> <xref:System.Windows.Forms.RightToLeft.Inherit> マップされていません。<br /><br /> <xref:System.Windows.FlowDirection.RightToLeft?displayProperty=nameWithType> マップ<xref:System.Windows.Forms.RightToLeft.Yes?displayProperty=nameWithType>します。|  
|<xref:System.Windows.Controls.Control.FontStyle%2A>|<xref:System.Drawing.Font.Style%2A> ホストされるコントロールの上 <xref:System.Drawing.Font?displayProperty=nameWithType>|一連の[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]プロパティに変換される、対応する<xref:System.Drawing.Font>します。 これらのプロパティのいずれかが変更されると、新しい<xref:System.Drawing.Font>が作成されます。 <xref:System.Windows.FontStyles.Normal%2A>:<xref:System.Drawing.FontStyle.Italic>は無効です。 <xref:System.Windows.FontStyles.Italic%2A>または<xref:System.Windows.FontStyles.Oblique%2A>:<xref:System.Drawing.FontStyle.Italic>を有効にします。|  
|<xref:System.Windows.Controls.Control.FontWeight%2A>|<xref:System.Drawing.Font.Style%2A> ホストされるコントロールの上 <xref:System.Drawing.Font?displayProperty=nameWithType>|一連の[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]プロパティに変換される、対応する<xref:System.Drawing.Font>します。 これらのプロパティのいずれかが変更されると、新しい<xref:System.Drawing.Font>が作成されます。 <xref:System.Windows.FontWeights.Black%2A>、 <xref:System.Windows.FontWeights.Bold%2A>、 <xref:System.Windows.FontWeights.DemiBold%2A>、 <xref:System.Windows.FontWeights.ExtraBold%2A>、 <xref:System.Windows.FontWeights.Heavy%2A>、 <xref:System.Windows.FontWeights.Medium%2A>、 <xref:System.Windows.FontWeights.SemiBold%2A>、または<xref:System.Windows.FontWeights.UltraBold%2A>:<xref:System.Drawing.FontStyle.Bold>を有効にします。 <xref:System.Windows.FontWeights.ExtraLight%2A>、 <xref:System.Windows.FontWeights.Light%2A>、 <xref:System.Windows.FontWeights.Normal%2A>、 <xref:System.Windows.FontWeights.Regular%2A>、 <xref:System.Windows.FontWeights.Thin%2A>、または<xref:System.Windows.FontWeights.UltraLight%2A>:<xref:System.Drawing.FontStyle.Bold>は無効です。|  
|<xref:System.Windows.Controls.Control.FontFamily%2A><br /><br /> <xref:System.Windows.Controls.Control.FontSize%2A><br /><br /> <xref:System.Windows.Controls.Control.FontStretch%2A><br /><br /> <xref:System.Windows.Controls.Control.FontStyle%2A><br /><br /> <xref:System.Windows.Controls.Control.FontWeight%2A>|<xref:System.Windows.Forms.Control.Font%2A><br /><br /> (<xref:System.Drawing.Font?displayProperty=nameWithType>)|一連の[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]プロパティに変換される、対応する<xref:System.Drawing.Font>します。 これらのプロパティのいずれかが変更されると、新しい<xref:System.Drawing.Font>が作成されます。 ホストされた[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]フォント サイズに基づくサイズ変更を制御します。<br /><br /> フォント サイズで[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]は 1 つ 90 6 インチを単位ととして表現[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]インチの 70-2 番目の 1 つとして。 対応する変換では。<br /><br /> [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] フォント サイズ =[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]フォント サイズ * 72.0 96.0/。|  
|<xref:System.Windows.Controls.Control.Foreground%2A><br /><br /> (<xref:System.Windows.Media.Brush?displayProperty=nameWithType>)|<xref:System.Windows.Forms.Control.ForeColor%2A><br /><br /> (<xref:System.Drawing.Color?displayProperty=nameWithType>)|<xref:System.Windows.Controls.Control.Foreground%2A>プロパティ マッピングが、次の規則を使用して実行します。<br /><br /> If<xref:System.Windows.Controls.Control.Foreground%2A>は、<xref:System.Windows.Media.SolidColorBrush>を使用して、<xref:System.Windows.Media.SolidColorBrush.Color%2A>の<xref:System.Windows.Forms.Control.ForeColor%2A>します。<br />If<xref:System.Windows.Controls.Control.Foreground%2A>は、<xref:System.Windows.Media.GradientBrush>の色を使用して、<xref:System.Windows.Media.GradientStop>のオフセット値が最小で<xref:System.Windows.Forms.Control.ForeColor%2A>します。<br />-その他の<xref:System.Windows.Media.Brush>ままにして、入力<xref:System.Windows.Forms.Control.ForeColor%2A>変更されません。 つまり、既定値を使用します。|  
|<xref:System.Windows.UIElement.IsEnabled%2A>|<xref:System.Windows.Forms.Control.Enabled%2A>|ときに<xref:System.Windows.UIElement.IsEnabled%2A>が設定されている<xref:System.Windows.Forms.Integration.WindowsFormsHost>要素セット、<xref:System.Windows.Forms.Control.Enabled%2A>ホストされるコントロールのプロパティ。|  
|<xref:System.Windows.Controls.Control.Padding%2A>|<xref:System.Windows.Forms.Control.Padding%2A>|4 つの値がすべて、<xref:System.Windows.Forms.Control.Padding%2A>プロパティをホストされている[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]コントロールが同じに設定されて<xref:System.Windows.Thickness>値。<br /><br /> 値より大きい<xref:System.Int32.MaxValue>に設定されている<xref:System.Int32.MaxValue>します。<br />値より小さい<xref:System.Int32.MinValue>に設定されている<xref:System.Int32.MinValue>します。|  
|<xref:System.Windows.UIElement.Visibility%2A>|<xref:System.Windows.Forms.Control.Visible%2A>|-   <xref:System.Windows.Visibility.Visible> マップ<xref:System.Windows.Forms.Control.Visible%2A>  = `true`します。 ホストされている[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]コントロールを表示します。 明示的に設定、<xref:System.Windows.Forms.Control.Visible%2A>プロパティにホストされているコントロールを`false`はお勧めしません。<br />-   <xref:System.Windows.Visibility.Collapsed> マップ<xref:System.Windows.Forms.Control.Visible%2A>  =  `true`または`false`します。 ホストされている[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]コントロールは描画しないと、その領域が折りたたまれています。<br />-   <xref:System.Windows.Visibility.Hidden> :ホストされている[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]コントロールがレイアウトでは、領域を占有しませんは表示されません。 ここで、<xref:System.Windows.Forms.Control.Visible%2A>プロパティに設定されて`true`します。 明示的に設定、<xref:System.Windows.Forms.Control.Visible%2A>プロパティにホストされているコントロールを`false`はお勧めしません。|  
  
 コンテナー要素で添付プロパティは完全にサポートによって、<xref:System.Windows.Forms.Integration.WindowsFormsHost>要素。  
  
 詳細については、「[チュートリアル:WindowsFormsHost 要素を使用してプロパティをマッピング](walkthrough-mapping-properties-using-the-windowsformshost-element.md)します。  
  
## <a name="updates-to-parent-properties"></a>親のプロパティの更新  
 ほとんどの親プロパティへの変更は、ホストされた子コントロールへの通知が。 次の一覧には、その値を変更するときに通知を発生させないプロパティについて説明します。  
  
-   <xref:System.Windows.Controls.Control.Background%2A>  
  
-   <xref:System.Windows.FrameworkElement.Cursor%2A>  
  
-   <xref:System.Windows.FrameworkElement.ForceCursor%2A>  
  
-   <xref:System.Windows.UIElement.Visibility%2A>  
  
 値を変更する場合など、<xref:System.Windows.Controls.Control.Background%2A>のプロパティ、<xref:System.Windows.Forms.Integration.WindowsFormsHost>要素、<xref:System.Windows.Forms.Control.BackColor%2A>ホストされるコントロールのプロパティは変更されません。  
  
## <a name="property-mapping-with-the-elementhost-control"></a>ElementHost コントロールのプロパティ マッピング  
 次のプロパティは、組み込みの変更通知を提供します。 呼び出すのではない、<xref:System.Windows.FrameworkElement.OnPropertyChanged%2A>メソッドがこれらのプロパティをマップしているとき。  
  
-   AutoSize  
  
-   背景色  
  
-   BackgroundImage  
  
-   BackgroundImageLayout  
  
-   BindingContext  
  
-   実行  
  
-   ContextMenu  
  
-   ContextMenuStrip  
  
-   カーソル  
  
-   ドッキング  
  
-   有効  
  
-   フォント  
  
-   ForeColor  
  
-   場所  
  
-   Margin  
  
-   [間隔]  
  
-   親  
  
-   Region  
  
-   RightToLeft  
  
-   サイズ  
  
-   TabIndex  
  
-   TabStop  
  
-   テキスト  
  
-   Visible  
  
 <xref:System.Windows.Forms.Integration.ElementHost>コントロールが既定値を変換します[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]プロパティを[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]次の変換テーブルを使用して対応します。  
  
 詳細については、「[チュートリアル:ElementHost コントロールを使用してプロパティをマッピング](walkthrough-mapping-properties-using-the-elementhost-control.md)します。  
  
|Windows フォームのホスト|Windows Presentation Foundation|相互運用の動作|  
|---------------------------|-------------------------------------|-----------------------------|  
|<xref:System.Windows.Forms.Control.BackColor%2A><br /><br /> (<xref:System.Drawing.Color?displayProperty=nameWithType>)|<xref:System.Windows.Controls.Control.Background%2A><br /><br /> (<xref:System.Windows.Media.Brush?displayProperty=nameWithType>) でホストされている要素|強制的に再描画でこのプロパティの設定、<xref:System.Windows.Media.ImageBrush>します。 場合、<xref:System.Windows.Forms.Integration.ElementHost.BackColorTransparent%2A>プロパティに設定されて`false`(既定値) の場合は、この<xref:System.Windows.Media.ImageBrush>の外観に基づいて、<xref:System.Windows.Forms.Integration.ElementHost>コントロールを含むその<xref:System.Windows.Forms.Control.BackColor%2A>、 <xref:System.Windows.Forms.Control.BackgroundImage%2A>、<xref:System.Windows.Forms.Control.BackgroundImageLayout%2A>プロパティ、および接続されている任意の描画ハンドラー。<br /><br /> 場合、<xref:System.Windows.Forms.Integration.ElementHost.BackColorTransparent%2A>プロパティに設定されて`true`、<xref:System.Windows.Media.ImageBrush>の外観に基づいて、<xref:System.Windows.Forms.Integration.ElementHost>コントロールの親、親を含む<xref:System.Windows.Forms.Control.BackColor%2A>、 <xref:System.Windows.Forms.Control.BackgroundImage%2A>、<xref:System.Windows.Forms.Control.BackgroundImageLayout%2A>プロパティ、および接続されている任意の描画ハンドラー。|  
|<xref:System.Windows.Forms.Control.BackgroundImage%2A><br /><br /> (<xref:System.Drawing.Image?displayProperty=nameWithType>)|<xref:System.Windows.Controls.Control.Background%2A><br /><br /> (<xref:System.Windows.Media.Brush?displayProperty=nameWithType>) でホストされている要素|このプロパティを設定すると、同じ動作が説明されている、<xref:System.Windows.Forms.Control.BackColor%2A>マッピングします。|  
|<xref:System.Windows.Forms.Control.BackgroundImageLayout%2A>|<xref:System.Windows.Controls.Control.Background%2A><br /><br /> (<xref:System.Windows.Media.Brush?displayProperty=nameWithType>) でホストされている要素|このプロパティを設定すると、同じ動作が説明されている、<xref:System.Windows.Forms.Control.BackColor%2A>マッピングします。|  
|<xref:System.Windows.Forms.Control.Cursor%2A><br /><br /> (<xref:System.Windows.Forms.Cursor?displayProperty=nameWithType>)|<xref:System.Windows.FrameworkElement.Cursor%2A><br /><br /> (<xref:System.Windows.Input.Cursor?displayProperty=nameWithType>)|[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]標準カーソルは、対応する翻訳[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]標準カーソル。 場合、[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]が標準的なカーソルの場合は、既定値が割り当てられます。|  
|<xref:System.Windows.Forms.Control.Enabled%2A>|<xref:System.Windows.UIElement.IsEnabled%2A>|ときに<xref:System.Windows.Forms.Control.Enabled%2A>が設定されている、<xref:System.Windows.Forms.Integration.ElementHost>コントロール セット、<xref:System.Windows.UIElement.IsEnabled%2A>ホスト型の要素のプロパティ。|  
|<xref:System.Windows.Forms.Control.Font%2A><br /><br /> (<xref:System.Drawing.Font?displayProperty=nameWithType>)|<xref:System.Windows.Controls.Control.FontFamily%2A><br /><br /> <xref:System.Windows.Controls.Control.FontSize%2A><br /><br /> <xref:System.Windows.Controls.Control.FontStretch%2A><br /><br /> <xref:System.Windows.Controls.Control.FontStyle%2A><br /><br /> <xref:System.Windows.Controls.Control.FontWeight%2A>|<xref:System.Windows.Forms.Control.Font%2A>対応する一連の値に変換される[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]フォントのプロパティ。|  
|<xref:System.Drawing.Font.Bold%2A>|<xref:System.Windows.Controls.Control.FontWeight%2A> ホストされている要素|<xref:System.Drawing.Font.Bold%2A> が `true` の場合、<xref:System.Windows.Controls.Control.FontWeight%2A> が <xref:System.Windows.FontWeights.Bold%2A> に設定されます。<br /><br /> <xref:System.Drawing.Font.Bold%2A> が `false` の場合、<xref:System.Windows.Controls.Control.FontWeight%2A> が <xref:System.Windows.FontWeights.Normal%2A> に設定されます。|  
|<xref:System.Drawing.Font.Italic%2A>|<xref:System.Windows.Controls.Control.FontStyle%2A> ホストされている要素|<xref:System.Drawing.Font.Italic%2A> が `true` の場合、<xref:System.Windows.Controls.Control.FontStyle%2A> が <xref:System.Windows.FontStyles.Italic%2A> に設定されます。<br /><br /> <xref:System.Drawing.Font.Italic%2A> が `false` の場合、<xref:System.Windows.Controls.Control.FontStyle%2A> が <xref:System.Windows.FontStyles.Normal%2A> に設定されます。|  
|<xref:System.Drawing.Font.Strikeout%2A>|<xref:System.Windows.TextDecorations> ホストされている要素|ホストしている場合にのみ適用されます、<xref:System.Windows.Controls.TextBlock>コントロール。|  
|<xref:System.Drawing.Font.Underline%2A>|<xref:System.Windows.TextDecorations> ホストされている要素|ホストしている場合にのみ適用されます、<xref:System.Windows.Controls.TextBlock>コントロール。|  
|<xref:System.Windows.Forms.Control.RightToLeft%2A><br /><br /> (<xref:System.Windows.Forms.RightToLeft?displayProperty=nameWithType>)|<xref:System.Windows.FrameworkElement.FlowDirection%2A><br /><br /> (<xref:System.Windows.FlowDirection>)|<xref:System.Windows.Forms.RightToLeft.No> マップ<xref:System.Windows.FlowDirection.LeftToRight>します。<br /><br /> <xref:System.Windows.Forms.RightToLeft.Yes> マップ<xref:System.Windows.FlowDirection.RightToLeft>します。|  
|<xref:System.Windows.Forms.Control.Visible%2A>|<xref:System.Windows.UIElement.Visibility%2A>|<xref:System.Windows.Forms.Integration.ElementHost>コントロール セット、<xref:System.Windows.UIElement.Visibility%2A>次の規則を使用してホストされている要素のプロパティ。<br /><br /> -   <xref:System.Windows.Forms.Control.Visible%2A> = `true` マップ<xref:System.Windows.Visibility.Visible>します。<br />-   <xref:System.Windows.Forms.Control.Visible%2A> = `false` マップ<xref:System.Windows.Visibility.Hidden>します。|  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [WPF と Win32 の相互運用性](wpf-and-win32-interoperation.md)
- [WPF と Windows フォームの相互運用性](wpf-and-windows-forms-interoperation.md)
- [チュートリアル: WindowsFormsHost 要素を使用したプロパティの割り当て](walkthrough-mapping-properties-using-the-windowsformshost-element.md)
- [チュートリアル: ElementHost コントロールを使用したプロパティの割り当て](walkthrough-mapping-properties-using-the-elementhost-control.md)
