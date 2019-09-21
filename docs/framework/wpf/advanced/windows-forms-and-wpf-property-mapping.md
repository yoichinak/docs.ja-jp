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
ms.openlocfilehash: ae4a97bc96a4f9e93942b4995f488c427fda3134
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69917508"
---
# <a name="windows-forms-and-wpf-property-mapping"></a>Windows フォームと WPF プロパティの割り当て
[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] および[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]テクノロジには、2つの類似したが異なるプロパティモデルがあります。 *プロパティマッピング*は、2つのアーキテクチャ間の相互運用をサポートし、次の機能を提供します。  
  
- を使用すると、ホスト環境での関連するプロパティの変更を、ホストされているコントロールまたは要素に簡単にマップできます。  
  
- 最も一般的に使用されるプロパティをマップするための既定の処理を提供します。  
  
- 既定のプロパティの削除、上書き、または拡張を簡単に行うことができます。  
  
- ホスト上のプロパティ値の変更が自動的に検出され、ホストされているコントロールまたは要素に変換されることを保証します。  
  
> [!NOTE]
> プロパティ変更イベントは、ホスティングコントロールまたは要素階層の上位に伝達されません。 プロパティのローカル値が、直接設定、スタイル、継承、データバインディング、またはプロパティの値を変更するその他のメカニズムによって変更されない場合、プロパティの変換は実行されません。  
  
 プロパティマッピングにアクセスする<xref:System.Windows.Forms.Integration.WindowsFormsHost>には、 <xref:System.Windows.Forms.Integration.ElementHost.PropertyMap%2A>要素の<xref:System.Windows.Forms.Integration.ElementHost>プロパティとコントロールのプロパティを使用します。 <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A>  
  
## <a name="property-mapping-with-the-windowsformshost-element"></a>WindowsFormsHost 要素を使用したプロパティのマッピング  
 要素<xref:System.Windows.Forms.Integration.WindowsFormsHost>は、次[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]の変換テーブル[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]を使用して、既定のプロパティを同等のものに変換します。  
  
|Windows Presentation Foundation ホスト|Windows フォーム|相互運用の動作|  
|---------------------------------------------|-------------------|-----------------------------|  
|<xref:System.Windows.Controls.Control.Background%2A><br /><br /> (<xref:System.Windows.Media.Brush?displayProperty=nameWithType>)|<xref:System.Windows.Forms.Control.BackColor%2A><br /><br /> (<xref:System.Drawing.Color?displayProperty=nameWithType>)|要素<xref:System.Windows.Forms.Integration.WindowsFormsHost>は、ホスト<xref:System.Windows.Forms.Control.BackColor%2A>されるコントロールのプロパティと<xref:System.Windows.Forms.Control.BackgroundImage%2A>ホストされるコントロールのプロパティを設定します。 マッピングは、次の規則を使用して実行されます。<br /><br /> -が<xref:System.Windows.Controls.Control.Background%2A>純色の場合は、変換され、ホストされ<xref:System.Windows.Forms.Control.BackColor%2A>ているコントロールのプロパティを設定するために使用されます。 ホストされるコントロールが<xref:System.Windows.Forms.Control.BackColor%2A>プロパティの値を継承できるため、プロパティはホストされるコントロールに設定されません。<xref:System.Windows.Forms.Control.BackColor%2A> **注:** ホストされているコントロールは、透明度をサポートしていません。 に<xref:System.Windows.Forms.Control.BackColor%2A>割り当てられたすべての色は、アルファ値が0xff である完全に不透明である必要があります。 <br /><br /> -が<xref:System.Windows.Controls.Control.Background%2A>純色でない場合、コントロール<xref:System.Windows.Forms.Integration.WindowsFormsHost>は<xref:System.Windows.Controls.Control.Background%2A>プロパティからビットマップを作成します。 コントロール<xref:System.Windows.Forms.Integration.WindowsFormsHost>は、このビットマップ<xref:System.Windows.Forms.Control.BackgroundImage%2A>をホストされるコントロールのプロパティに割り当てます。 これにより、透過性に似た効果が得られます。 **注:** この動作をオーバーライドすることも、 <xref:System.Windows.Controls.Control.Background%2A>プロパティマッピングを削除することもできます。|  
|<xref:System.Windows.FrameworkElement.Cursor%2A>|<xref:System.Windows.Forms.Control.Cursor%2A>|既定のマッピングが再割り当てされて<xref:System.Windows.Forms.Integration.WindowsFormsHost>いない場合は、 <xref:System.Windows.FrameworkElement.Cursor%2A>プロパティが設定されている先祖が見つかるまで、コントロールは先祖階層を走査します。 この値は、対応する[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]最も近いカーソルに変換されます。<br /><br /> <xref:System.Windows.FrameworkElement.ForceCursor%2A>プロパティの既定のマッピングが再割り当てされていない場合は、がに`true`設定さ<xref:System.Windows.FrameworkElement.ForceCursor%2A>れている最初の先祖でトラバーサルが停止します。|  
|<xref:System.Windows.FrameworkElement.FlowDirection%2A><br /><br /> (<xref:System.Windows.FlowDirection?displayProperty=nameWithType>)|<xref:System.Windows.Forms.Control.RightToLeft%2A><br /><br /> (<xref:System.Windows.Forms.RightToLeft?displayProperty=nameWithType>)|<xref:System.Windows.FlowDirection.LeftToRight>に<xref:System.Windows.Forms.RightToLeft.No>マップされます。<br /><br /> <xref:System.Windows.FlowDirection.RightToLeft>に<xref:System.Windows.Forms.RightToLeft.Yes>マップされます。<br /><br /> <xref:System.Windows.Forms.RightToLeft.Inherit>がマップされていません。<br /><br /> <xref:System.Windows.FlowDirection.RightToLeft?displayProperty=nameWithType>に<xref:System.Windows.Forms.RightToLeft.Yes?displayProperty=nameWithType>マップされます。|  
|<xref:System.Windows.Controls.Control.FontStyle%2A>|<xref:System.Drawing.Font.Style%2A>ホストされるコントロールの<xref:System.Drawing.Font?displayProperty=nameWithType>|一連[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]のプロパティは、対応<xref:System.Drawing.Font>するに変換されます。 これらのプロパティのいずれかが変更さ<xref:System.Drawing.Font>れると、新しいが作成されます。 の<xref:System.Windows.FontStyles.Normal%2A>場合<xref:System.Drawing.FontStyle.Italic> : は無効です。 また<xref:System.Windows.FontStyles.Italic%2A>は<xref:System.Windows.FontStyles.Oblique%2A>の<xref:System.Drawing.FontStyle.Italic>場合: が有効になります。|  
|<xref:System.Windows.Controls.Control.FontWeight%2A>|<xref:System.Drawing.Font.Style%2A>ホストされるコントロールの<xref:System.Drawing.Font?displayProperty=nameWithType>|一連[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]のプロパティは、対応<xref:System.Drawing.Font>するに変換されます。 これらのプロパティのいずれかが変更さ<xref:System.Drawing.Font>れると、新しいが作成されます。 <xref:System.Windows.FontWeights.Black%2A> 、<xref:System.Windows.FontWeights.ExtraBold%2A> <xref:System.Windows.FontWeights.UltraBold%2A>、、、、、 、また<xref:System.Drawing.FontStyle.Bold>は: が有効になっています。 <xref:System.Windows.FontWeights.SemiBold%2A> <xref:System.Windows.FontWeights.Bold%2A> <xref:System.Windows.FontWeights.DemiBold%2A> <xref:System.Windows.FontWeights.Heavy%2A> <xref:System.Windows.FontWeights.Medium%2A> <xref:System.Windows.FontWeights.ExtraLight%2A> 、<xref:System.Windows.FontWeights.Light%2A> 、、<xref:System.Windows.FontWeights.UltraLight%2A>、、またはの場合:<xref:System.Drawing.FontStyle.Bold>は無効です。 <xref:System.Windows.FontWeights.Thin%2A> <xref:System.Windows.FontWeights.Normal%2A> <xref:System.Windows.FontWeights.Regular%2A>|  
|<xref:System.Windows.Controls.Control.FontFamily%2A><br /><br /> <xref:System.Windows.Controls.Control.FontSize%2A><br /><br /> <xref:System.Windows.Controls.Control.FontStretch%2A><br /><br /> <xref:System.Windows.Controls.Control.FontStyle%2A><br /><br /> <xref:System.Windows.Controls.Control.FontWeight%2A>|<xref:System.Windows.Forms.Control.Font%2A><br /><br /> (<xref:System.Drawing.Font?displayProperty=nameWithType>)|一連[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]のプロパティは、対応<xref:System.Drawing.Font>するに変換されます。 これらのプロパティのいずれかが変更さ<xref:System.Drawing.Font>れると、新しいが作成されます。 ホスト[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]されるコントロールは、フォントサイズに基づいてサイズが変更されます。<br /><br /> の[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]フォントサイズは、1インチの 90 ~ 6 インチ[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]として表現され、1インチの seventy 秒として表現されます。 対応する変換は次のとおりです。<br /><br /> [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]フォントサイズ = [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]フォントサイズ * 72.0/96.0。|  
|<xref:System.Windows.Controls.Control.Foreground%2A><br /><br /> (<xref:System.Windows.Media.Brush?displayProperty=nameWithType>)|<xref:System.Windows.Forms.Control.ForeColor%2A><br /><br /> (<xref:System.Drawing.Color?displayProperty=nameWithType>)|<xref:System.Windows.Controls.Control.Foreground%2A>プロパティマッピングは、次の規則を使用して実行されます。<br /><br /> -が<xref:System.Windows.Controls.Control.Foreground%2A>の<xref:System.Windows.Media.SolidColorBrush>場合は、 <xref:System.Windows.Media.SolidColorBrush.Color%2A>に<xref:System.Windows.Forms.Control.ForeColor%2A>を使用します。<br />- <xref:System.Windows.Controls.Control.Foreground%2A> <xref:System.Windows.Media.GradientStop>がの場合は、のオフセット値<xref:System.Windows.Forms.Control.ForeColor%2A>が最も小さいの色を使用します。 <xref:System.Windows.Media.GradientBrush><br />-その他<xref:System.Windows.Media.Brush>の型の場合<xref:System.Windows.Forms.Control.ForeColor%2A>は、変更されません。 これは、既定値が使用されることを意味します。|  
|<xref:System.Windows.UIElement.IsEnabled%2A>|<xref:System.Windows.Forms.Control.Enabled%2A>|が<xref:System.Windows.UIElement.IsEnabled%2A>設定され<xref:System.Windows.Forms.Integration.WindowsFormsHost>ている場合<xref:System.Windows.Forms.Control.Enabled%2A> 、要素はホストされているコントロールのプロパティを設定します。|  
|<xref:System.Windows.Controls.Control.Padding%2A>|<xref:System.Windows.Forms.Control.Padding%2A>|ホスト<xref:System.Windows.Forms.Control.Padding%2A> <xref:System.Windows.Thickness>されるコントロールのプロパティの4つの値はすべて、同じ値に設定されます。 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]<br /><br /> -より<xref:System.Int32.MaxValue>大きい値はに<xref:System.Int32.MaxValue>設定されます。<br />-未満の値<xref:System.Int32.MinValue>はに<xref:System.Int32.MinValue>設定されます。|  
|<xref:System.Windows.UIElement.Visibility%2A>|<xref:System.Windows.Forms.Control.Visible%2A>|-   <xref:System.Windows.Visibility.Visible>に<xref:System.Windows.Forms.Control.Visible%2A>マップされ`true`ます。  =  ホスト[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]されるコントロールが表示されます。 ホストされる<xref:System.Windows.Forms.Control.Visible%2A>コントロールのプロパティを明示的`false`にに設定することはお勧めしません。<br />-   <xref:System.Windows.Visibility.Collapsed>または<xref:System.Windows.Forms.Control.Visible%2A>  =  `true`に割り当てられます。 `false` ホスト[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]されるコントロールは描画されず、その領域は折りたたまれます。<br />-   <xref:System.Windows.Visibility.Hidden>:ホスト[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]されるコントロールはレイアウトの領域を占有しますが、表示されません。 この場合、 <xref:System.Windows.Forms.Control.Visible%2A>プロパティはに`true`設定されます。 ホストされる<xref:System.Windows.Forms.Control.Visible%2A>コントロールのプロパティを明示的`false`にに設定することはお勧めしません。|  
  
 コンテナー要素の添付プロパティは、 <xref:System.Windows.Forms.Integration.WindowsFormsHost>要素によって完全にサポートされています。  
  
 詳細については、「[チュートリアル:WindowsFormsHost 要素](walkthrough-mapping-properties-using-the-windowsformshost-element.md)を使用したプロパティのマッピング。  
  
## <a name="updates-to-parent-properties"></a>親プロパティの更新  
 ほとんどの親プロパティに対する変更によって、ホストされている子コントロールへの通知が発生します。 次の一覧では、値が変更された場合に通知が発生しないプロパティについて説明します。  
  
- <xref:System.Windows.Controls.Control.Background%2A>  
  
- <xref:System.Windows.FrameworkElement.Cursor%2A>  
  
- <xref:System.Windows.FrameworkElement.ForceCursor%2A>  
  
- <xref:System.Windows.UIElement.Visibility%2A>  
  
 たとえば、 <xref:System.Windows.Controls.Control.Background%2A> <xref:System.Windows.Forms.Integration.WindowsFormsHost>要素のプロパティの値を変更しても、ホストされているコントロールのプロパティは変更されません。<xref:System.Windows.Forms.Control.BackColor%2A>  
  
## <a name="property-mapping-with-the-elementhost-control"></a>コントロールを使用したプロパティのマッピング  
 次のプロパティは、組み込みの変更通知を提供します。 これらのプロパティを<xref:System.Windows.FrameworkElement.OnPropertyChanged%2A>マッピングする場合は、メソッドを呼び出さないでください。  
  
- AutoSize  
  
- 色  
  
- BackgroundImage  
  
- BackgroundImageLayout  
  
- BindingContext  
  
- CausesValidation  
  
- ContextMenu  
  
- ContextMenuStrip  
  
- カーソル  
  
- ドッキング  
  
- 有効  
  
- フォント  
  
- ForeColor  
  
- Location  
  
- 余白  
  
- [間隔]  
  
- Parent  
  
- リージョン  
  
- RightToLeft  
  
- サイズ  
  
- TabIndex  
  
- "  
  
- テキスト  
  
- Visible  
  
 コントロール<xref:System.Windows.Forms.Integration.ElementHost>は、次[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]の変換テーブル[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]を使用して、既定のプロパティを同等のものに変換します。  
  
 詳細については、「[チュートリアル:コントロール](walkthrough-mapping-properties-using-the-elementhost-control.md)を使用してプロパティをマッピングしています。  
  
|Windows フォームホスト|Windows Presentation Foundation|相互運用の動作|  
|---------------------------|-------------------------------------|-----------------------------|  
|<xref:System.Windows.Forms.Control.BackColor%2A><br /><br /> (<xref:System.Drawing.Color?displayProperty=nameWithType>)|<xref:System.Windows.Controls.Control.Background%2A><br /><br /> ホスト<xref:System.Windows.Media.Brush?displayProperty=nameWithType>されている要素の ()|このプロパティを設定すると、 <xref:System.Windows.Media.ImageBrush>が強制的に再描画されます。 <xref:System.Windows.Forms.Control.BackColor%2A> <xref:System.Windows.Forms.Control.BackgroundImage%2A> <xref:System.Windows.Forms.Control.BackgroundImageLayout%2A> <xref:System.Windows.Forms.Integration.ElementHost> `false`プロパティが (既定値) に設定されている場合<xref:System.Windows.Media.ImageBrush> 、これはコントロールの外観 (、、、プロパティ、添付されている描画を含む) に基づいています。 <xref:System.Windows.Forms.Integration.ElementHost.BackColorTransparent%2A>ハンドラー.<br /><br /> <xref:System.Windows.Forms.Integration.ElementHost> <xref:System.Windows.Forms.Control.BackgroundImage%2A> <xref:System.Windows.Forms.Control.BackgroundImageLayout%2A> <xref:System.Windows.Media.ImageBrush> <xref:System.Windows.Forms.Control.BackColor%2A>プロパティがに`true`設定されている場合、は、親の、、、の各プロパティ、および添付された描画を含む、コントロールの親の外観に基づきます。 <xref:System.Windows.Forms.Integration.ElementHost.BackColorTransparent%2A>ハンドラー.|  
|<xref:System.Windows.Forms.Control.BackgroundImage%2A><br /><br /> (<xref:System.Drawing.Image?displayProperty=nameWithType>)|<xref:System.Windows.Controls.Control.Background%2A><br /><br /> ホスト<xref:System.Windows.Media.Brush?displayProperty=nameWithType>されている要素の ()|このプロパティを設定すると、 <xref:System.Windows.Forms.Control.BackColor%2A>マッピングについて説明されているのと同じ動作が発生します。|  
|<xref:System.Windows.Forms.Control.BackgroundImageLayout%2A>|<xref:System.Windows.Controls.Control.Background%2A><br /><br /> ホスト<xref:System.Windows.Media.Brush?displayProperty=nameWithType>されている要素の ()|このプロパティを設定すると、 <xref:System.Windows.Forms.Control.BackColor%2A>マッピングについて説明されているのと同じ動作が発生します。|  
|<xref:System.Windows.Forms.Control.Cursor%2A><br /><br /> (<xref:System.Windows.Forms.Cursor?displayProperty=nameWithType>)|<xref:System.Windows.FrameworkElement.Cursor%2A><br /><br /> (<xref:System.Windows.Input.Cursor?displayProperty=nameWithType>)|標準カーソルは、対応する[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]標準カーソルに変換されます。 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]が標準カーソルでない場合は、既定値が割り当てられます。|  
|<xref:System.Windows.Forms.Control.Enabled%2A>|<xref:System.Windows.UIElement.IsEnabled%2A>|が<xref:System.Windows.Forms.Control.Enabled%2A>設定されて<xref:System.Windows.Forms.Integration.ElementHost>いる場合、 <xref:System.Windows.UIElement.IsEnabled%2A>コントロールはホストされている要素のプロパティを設定します。|  
|<xref:System.Windows.Forms.Control.Font%2A><br /><br /> (<xref:System.Drawing.Font?displayProperty=nameWithType>)|<xref:System.Windows.Controls.Control.FontFamily%2A><br /><br /> <xref:System.Windows.Controls.Control.FontSize%2A><br /><br /> <xref:System.Windows.Controls.Control.FontStretch%2A><br /><br /> <xref:System.Windows.Controls.Control.FontStyle%2A><br /><br /> <xref:System.Windows.Controls.Control.FontWeight%2A>|値<xref:System.Windows.Forms.Control.Font%2A>は、対応する一連の[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]フォントプロパティに変換されます。|  
|<xref:System.Drawing.Font.Bold%2A>|<xref:System.Windows.Controls.Control.FontWeight%2A>ホストされた要素の|<xref:System.Drawing.Font.Bold%2A> が `true` の場合、<xref:System.Windows.Controls.Control.FontWeight%2A> が <xref:System.Windows.FontWeights.Bold%2A> に設定されます。<br /><br /> <xref:System.Drawing.Font.Bold%2A> が `false` の場合、<xref:System.Windows.Controls.Control.FontWeight%2A> が <xref:System.Windows.FontWeights.Normal%2A> に設定されます。|  
|<xref:System.Drawing.Font.Italic%2A>|<xref:System.Windows.Controls.Control.FontStyle%2A>ホストされた要素の|<xref:System.Drawing.Font.Italic%2A> が `true` の場合、<xref:System.Windows.Controls.Control.FontStyle%2A> が <xref:System.Windows.FontStyles.Italic%2A> に設定されます。<br /><br /> <xref:System.Drawing.Font.Italic%2A> が `false` の場合、<xref:System.Windows.Controls.Control.FontStyle%2A> が <xref:System.Windows.FontStyles.Normal%2A> に設定されます。|  
|<xref:System.Drawing.Font.Strikeout%2A>|<xref:System.Windows.TextDecorations>ホストされた要素の|コントロールを<xref:System.Windows.Controls.TextBlock>ホストする場合にのみ適用されます。|  
|<xref:System.Drawing.Font.Underline%2A>|<xref:System.Windows.TextDecorations>ホストされた要素の|コントロールを<xref:System.Windows.Controls.TextBlock>ホストする場合にのみ適用されます。|  
|<xref:System.Windows.Forms.Control.RightToLeft%2A><br /><br /> (<xref:System.Windows.Forms.RightToLeft?displayProperty=nameWithType>)|<xref:System.Windows.FrameworkElement.FlowDirection%2A><br /><br /> (<xref:System.Windows.FlowDirection>)|<xref:System.Windows.Forms.RightToLeft.No>に<xref:System.Windows.FlowDirection.LeftToRight>マップされます。<br /><br /> <xref:System.Windows.Forms.RightToLeft.Yes>に<xref:System.Windows.FlowDirection.RightToLeft>マップされます。|  
|<xref:System.Windows.Forms.Control.Visible%2A>|<xref:System.Windows.UIElement.Visibility%2A>|コントロール<xref:System.Windows.Forms.Integration.ElementHost>は、次<xref:System.Windows.UIElement.Visibility%2A>の規則を使用して、ホストされる要素のプロパティを設定します。<br /><br /> -   <xref:System.Windows.Forms.Control.Visible%2A> = `true`に<xref:System.Windows.Visibility.Visible>マップされます。<br />-   <xref:System.Windows.Forms.Control.Visible%2A> = `false`に<xref:System.Windows.Visibility.Hidden>マップされます。|  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [WPF と Win32 の相互運用性](wpf-and-win32-interoperation.md)
- [WPF と Windows フォームの相互運用性](wpf-and-windows-forms-interoperation.md)
- [チュートリアル: WindowsFormsHost 要素を使用したプロパティのマッピング](walkthrough-mapping-properties-using-the-windowsformshost-element.md)
- [チュートリアル: コントロールを使用したプロパティのマッピング](walkthrough-mapping-properties-using-the-elementhost-control.md)
