---
title: WindowsFormsHost 要素のレイアウトに関する考慮事項
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms [WPF], interoperability with
- Windows Forms [WPF], WPF interoperation
- interoperability [WPF], Windows Forms
- WindowsFormsHost element layout considerations [WPF]
- dynamic layout [WPF interoperability]
- device-independent pixels
ms.assetid: 3c574597-bbde-440f-95cc-01371f1a5d9d
ms.openlocfilehash: 93aaa8e21ef483fc21297e29189d86f93fbe138a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62001313"
---
# <a name="layout-considerations-for-the-windowsformshost-element"></a>WindowsFormsHost 要素のレイアウトに関する考慮事項
このトピックで説明する方法、<xref:System.Windows.Forms.Integration.WindowsFormsHost>要素と対話、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]レイアウト システム。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]フォームまたはページ上の要素を配置してサイズ変更のロジックを異なる、ただしと同様をサポートします。 ハイブリッド ユーザー インターフェイス (UI) を作成するときにホストする[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]でコントロールを[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]、<xref:System.Windows.Forms.Integration.WindowsFormsHost>要素には、2 つのレイアウトのスキームが統合されています。  
  
## <a name="differences-in-layout-between-wpf-and-windows-forms"></a>WPF と Windows フォームのレイアウトでの違い  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 解像度に依存しないレイアウトを使用します。 すべて[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]レイアウト サイズを指定する*デバイス非依存ピクセル*します。 デバイスに依存しないピクセルは、72 dpi モニターや 19,200 dpi プリンターにレンダリングするかどうかに関係なく同じような結果を取得するための 1 つ 90 6 インチのサイズと解像度に依存せず、です。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] またに基づいて*動的レイアウト*します。 これは、UI 要素自体の整列をフォームまたはページのコンテンツ、親レイアウト コンテナー、および使用可能な画面サイズに従っていることを意味します。 動的レイアウトでは、含まれる文字列の長さを変更するときに自動的に UI 要素の位置とサイズを調整してローカライズが容易になります。  
  
 レイアウト[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]がデバイスに依存し、静的である可能性が高くなります。 通常、[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]ハードウェア ピクセル単位で指定されたディメンションを使用してフォームにコントロールを絶対的に配置されます。 ただし、[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]は次の表にまとめるとおりいくつかの動的なレイアウト機能をサポートします。  
  
|レイアウト機能|説明|  
|--------------------|-----------------|  
|自動サイズ調整|いくつか[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]自体の内容を正しく表示するコントロールのサイズを変更します。 詳細については、次を参照してください。 [AutoSize プロパティの概要](../../winforms/controls/autosize-property-overview.md)します。|  
|固定とドッキング|[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] コントロールは、位置と親コンテナーに基づくサイズ変更をサポートします。 詳細については、次のトピックを参照してください。 <xref:System.Windows.Forms.Control.Anchor%2A?displayProperty=nameWithType> および <xref:System.Windows.Forms.Control.Dock%2A?displayProperty=nameWithType>|  
|自動スケール|自身とその子の出力デバイスまたはコンテナーの既定のフォントのピクセル単位で、サイズ、解像度に基づくコンテナー コントロールのサイズを変更します。 詳細については、次を参照してください。 [Windows フォームで自動スケーリング](../../winforms/automatic-scaling-in-windows-forms.md)します。|  
|レイアウト コンテナー|<xref:System.Windows.Forms.FlowLayoutPanel>と<xref:System.Windows.Forms.TableLayoutPanel>コントロールの子コントロールを配置および自体の内容に従ってサイズします。|  
  
## <a name="layout-limitations"></a>レイアウトの制限事項  
 一般に、[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]コントロールを拡張しで可能な範囲に変換されることはできません[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]します。 次の一覧が既知の制限事項について説明しますと、<xref:System.Windows.Forms.Integration.WindowsFormsHost>要素が、そのホスト型統合しようとしています。[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]にコントロールを、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]レイアウト システム。  
  
- 場合によっては、[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]コントロールのサイズを変更できない、または特定のディメンションにのみサイズを設定することができます。 たとえば、 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] <xref:System.Windows.Forms.ComboBox>コントロールにのみ、1 つの高さ、コントロールのフォント サイズで定義されているがサポートしています。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]場所要素延長される可能性が垂直方向に、ホストされる動的レイアウト<xref:System.Windows.Forms.ComboBox>期待どおりに、コントロールは拡張されません。  
  
- [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] コントロールを回転または傾斜ことはできません。 <xref:System.Windows.Forms.Integration.WindowsFormsHost>要素の生成、<xref:System.Windows.Forms.Integration.WindowsFormsHost.LayoutError>傾斜や回転変換を適用する場合のイベント。 処理しない場合、 <xref:System.Windows.Forms.Integration.WindowsFormsHost.LayoutError> 、イベント、<xref:System.InvalidOperationException>が発生します。  
  
- ほとんどの場合、[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]コントロールは比例してスケーリングをサポートしません。 コントロールの全体的なディメンションのスケーラビリティが子コントロールとコントロールのコンポーネント要素可能性がありますのサイズ変更されない期待どおりにします。 この制限はどの程度各依存[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]コントロールがスケーリングをサポートします。 さらに、スケールすることはできません[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]0 ピクセルのサイズまでコントロール。  
  
- [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] コントロールは、自動スケールのフォームはそれ自体とそのコントロールのフォント サイズに基づいて自動的に変更をサポートします。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]個々 の要素を動的に変更可能性がありますが、ユーザー インターフェイス、フォント サイズを変更するは全体のレイアウトのサイズを変更できません。  
  
### <a name="z-order"></a>Z オーダー  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]ユーザー インターフェイスの動作が重複する制御する要素の z オーダーを変更することができます。 ホストされた[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]の上に常に描画するために個別の HWND では、コントロールが描画される[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]要素。  
  
 ホストされた[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]コントロールのいずれかの上に描画も<xref:System.Windows.Documents.Adorner>要素。  
  
## <a name="layout-behavior"></a>レイアウトの動作  
 次のセクションをホストする場合にレイアウト動作の特定の側面を説明します[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]でコントロールを[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]します。  
  
### <a name="scaling-unit-conversion-and-device-independence"></a>スケーリング、単位換算、およびデバイス非依存  
 たびに、<xref:System.Windows.Forms.Integration.WindowsFormsHost>要素は、関連する操作を実行します。[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]と[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]次元、2 つの座標系が関係している: デバイスに依存しないピクセル[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]ハードウェア ピクセルの[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]します。 そのため、一貫性のあるレイアウトを実現するために適切な単体とスケーリング変換を適用する必要があります。  
  
 座標システムの間の変換は、現在のデバイスの解像度と任意のレイアウトによって異なります。 または、に適用される変換のレンダリング、<xref:System.Windows.Forms.Integration.WindowsFormsHost>要素またはその先祖にします。  
  
 出力デバイスが 96 dpi と、スケーリングに適用されていないかどうか、<xref:System.Windows.Forms.Integration.WindowsFormsHost>要素、1 つのデバイスに依存しないピクセルは 1 つのハードウェア ピクセルを等しくします。  
  
 それ以外の場合は、座標系のスケーリングが必要です。 ホストされるコントロールのサイズは変更されません。 代わりに、<xref:System.Windows.Forms.Integration.WindowsFormsHost>要素がホストされているコントロールとその子コントロールのすべてのスケールを試みます。 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]スケーリングをサポートしていません、<xref:System.Windows.Forms.Integration.WindowsFormsHost>要素が特定のコントロールでサポートされているレベルにスケーリングします。  
  
 上書き、<xref:System.Windows.Forms.Integration.WindowsFormsHost.ScaleChild%2A>ホストされた Windows フォーム コントロールのカスタム スケーリングの動作を提供するメソッド。  
  
 スケーリング、だけでなく、<xref:System.Windows.Forms.Integration.WindowsFormsHost>要素は、次の表に示すように丸め処理やオーバーフローの場合を処理します。  
  
|変換の問題|説明|  
|----------------------|-----------------|  
|丸め|[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] デバイス非依存のピクセル寸法、として指定`double`、および[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]としてハードウェア ピクセル サイズが指定されて`int`します。 場合、 `double`-に基づいてディメンションに変換されます`int`-ベースのディメンション、<xref:System.Windows.Forms.Integration.WindowsFormsHost>要素が 0.5 未満の小数部の値に切り上げられます 0 ように標準の丸めを使用します。|  
|オーバーフロー|ときに、<xref:System.Windows.Forms.Integration.WindowsFormsHost>から要素が変換`double`値を`int`値、オーバーフローが可能です。 も大きい値は<xref:System.Int32.MaxValue>に設定されている<xref:System.Int32.MaxValue>します。|  
  
### <a name="layout-related-properties"></a>レイアウト関連のプロパティ  
 レイアウト動作を制御するプロパティ[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]コントロールと[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]要素が、適切にマップされている、<xref:System.Windows.Forms.Integration.WindowsFormsHost>要素。 詳細については、次を参照してください。 [Windows フォームと WPF プロパティのマッピング](windows-forms-and-wpf-property-mapping.md)します。  
  
### <a name="layout-changes-in-the-hosted-control"></a>ホストされるコントロールのレイアウトの変更  
 ホストのレイアウトの変更[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]にコントロールを反映[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]レイアウトの更新をトリガーします。 <xref:System.Windows.UIElement.InvalidateMeasure%2A>メソッド<xref:System.Windows.Forms.Integration.WindowsFormsHost>ホストされるコントロールのレイアウトの変更が発生することにより、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]レイアウト エンジンを実行します。  
  
### <a name="continuously-sized-windows-forms-controls"></a>継続的に Windows フォーム コントロールのサイズ  
 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 継続的なスケーリングを完全にサポートするコントロールとの対話、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]レイアウト システム。 <xref:System.Windows.Forms.Integration.WindowsFormsHost>要素を使用して、<xref:System.Windows.FrameworkElement.MeasureOverride%2A>と<xref:System.Windows.FrameworkElement.ArrangeOverride%2A>メソッドのサイズし、配置ホストを通常どおり[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]コントロール。  
  
### <a name="sizing-algorithm"></a>サイズ調整アルゴリズム  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>要素は、次の手順を使用してホストされるコントロールのサイズを変更します。  
  
1. <xref:System.Windows.Forms.Integration.WindowsFormsHost>要素をオーバーライド、<xref:System.Windows.FrameworkElement.MeasureOverride%2A>と<xref:System.Windows.FrameworkElement.ArrangeOverride%2A>メソッド。  
  
2. ホストされるコントロールのサイズを決定する、<xref:System.Windows.FrameworkElement.MeasureOverride%2A>メソッドは、ホストされるコントロールの<xref:System.Windows.Forms.Control.GetPreferredSize%2A>制約を持つメソッドの変換に渡される制約から、<xref:System.Windows.FrameworkElement.MeasureOverride%2A>メソッド。  
  
3. <xref:System.Windows.FrameworkElement.ArrangeOverride%2A>メソッドは、指定されたサイズの制約にホストされるコントロールを設定しようとしています。  
  
4. 場合、ホストされるコントロールの<xref:System.Windows.Forms.Control.Size%2A>プロパティが指定した制約と一致する、ホストされるコントロールのサイズは、制約にします。  
  
 場合、<xref:System.Windows.Forms.Control.Size%2A>プロパティが指定した制約と一致しません、ホストされるコントロールは継続的なサイズ変更をサポートしていません。 たとえば、<xref:System.Windows.Forms.MonthCalendar>コントロールは、不連続のサイズだけを使用できます。 このコントロールの使用可能なサイズは、高さと幅の両方の整数 (月の数を表す) で構成されます。 、このような状況で、<xref:System.Windows.Forms.Integration.WindowsFormsHost>要素の次のように動作します。  
  
- 場合、<xref:System.Windows.Forms.Control.Size%2A>プロパティが指定した制約より大きいサイズを返します、<xref:System.Windows.Forms.Integration.WindowsFormsHost>要素がホストされるコントロールをクリップします。 高さと幅は、いずれかの方向でホストされるコントロールをクリップすることがありますので、個別に処理されます。  
  
- 場合、<xref:System.Windows.Forms.Control.Size%2A>プロパティが指定した制約よりも小さいサイズを返します<xref:System.Windows.Forms.Integration.WindowsFormsHost>このサイズの値を受け取り、値を返します、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]レイアウト システム。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [チュートリアル: WPF でのフォーム コントロールの Windows の配置](walkthrough-arranging-windows-forms-controls-in-wpf.md)
- [WPF のサンプルでのフォーム コントロールの Windows の配置](https://go.microsoft.com/fwlink/?LinkID=159971)
- [Windows フォームと WPF プロパティの割り当て](windows-forms-and-wpf-property-mapping.md)
- [移行と相互運用性](migration-and-interoperability.md)
