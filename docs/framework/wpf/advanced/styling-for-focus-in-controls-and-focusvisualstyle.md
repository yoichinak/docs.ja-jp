---
title: コントロールのフォーカスのスタイルと FocusVisualStyle
ms.date: 03/30/2017
helpviewer_keywords:
- keyboard focus [WPF]
- focus [WPF], visual styling
- styles [WPF], focus visual style
ms.assetid: 786ac576-011b-4d72-913b-558deccb9b35
ms.openlocfilehash: fda7ed12d232af5a7cfb8eb43cbb09eb793da171
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79141200"
---
# <a name="styling-for-focus-in-controls-and-focusvisualstyle"></a>コントロールのフォーカスのスタイルと FocusVisualStyle
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]には、キーボード フォーカスを受け取ったときにコントロールの外観を変更するための 2 つの並列機構が用意されています。 1 つ目のメカニズムは、コントロールに適用されるスタイルや<xref:System.Windows.UIElement.IsKeyboardFocused%2A>テンプレート内などのプロパティにプロパティ セッターを使用する方法です。 2 番目のメカニズムは、プロパティの値として別のスタイル<xref:System.Windows.FrameworkElement.FocusVisualStyle%2A>を提供することです。"フォーカスの表示スタイル" は、コントロールの上に描画される装飾用の個別のビジュアル ツリーを作成します。 ここでは、これらの各メカニズムが適切なシナリオについて説明します。  

<a name="Purpose"></a>
## <a name="the-purpose-of-focus-visual-style"></a>フォーカス表示スタイルの目的  
 フォーカス表示スタイル機能は、UI 要素へのキーボード ナビゲーションに基づいてユーザーの視覚的なフィードバックを紹介するための一般的な "オブジェクト モデル" を提供します。 これは、コントロールに新しいテンプレートを適用したり、特定のテンプレート構成を知らなくても可能です。  
  
 ただし、フォーカス表示スタイル機能はコントロール テンプレートを知らなくても機能するため、フォーカス表示スタイルを使用してコントロールに表示できる視覚的フィードバックは必ずしも制限されます。 この機能が実際に行うことは、テンプレートを通じてコントロールのレンダリングによって作成されたビジュアル ツリーの上に別のビジュアル ツリー (装飾) をオーバーレイすることです。 この別のビジュアル ツリーは、プロパティを塗りつぶす<xref:System.Windows.FrameworkElement.FocusVisualStyle%2A>スタイルを使用して定義します。  
  
<a name="Default"></a>
## <a name="default-focus-visual-style-behavior"></a>既定のフォーカス表示スタイルの動作  
 フォーカス表示スタイルは、キーボードによってフォーカスアクションが開始された場合にのみ機能します。 マウス操作やプログラムによるフォーカスの変更は、フォーカス表示スタイルのモードを無効にします。 フォーカス モードの違いについては、「[フォーカスの概要](focus-overview.md)」を参照してください。  
  
 コントロールのテーマには、テーマ内のすべてのコントロールのフォーカス表示スタイルとなる既定のフォーカス表示スタイルの動作が含まれます。 このテーマ スタイルは、静的キー<xref:System.Windows.SystemParameters.FocusVisualStyleKey%2A>の値で識別されます。 アプリケーション レベルで独自のフォーカス表示スタイルを宣言すると、テーマからこの既定のスタイルの動作が置き換えられます。 または、テーマ全体を定義する場合は、同じキーを使用して、テーマ全体の既定の動作のスタイルを定義する必要があります。  
  
 テーマでは、既定のフォーカス表示スタイルは一般的に非常に単純です。 大まかな近似値を次に示します。  
  
```xaml  
<Style x:Key="{x:Static SystemParameters.FocusVisualStyleKey}">  
  <Setter Property="Control.Template">  
    <Setter.Value>  
      <ControlTemplate>  
        <Rectangle StrokeThickness="1"  
          Stroke="Black"  
          StrokeDashArray="1 2"  
          SnapsToDevicePixels="true"/>  
      </ControlTemplate>  
    </Setter.Value>  
  </Setter>  
</Style>  
```  
  
<a name="When"></a>
## <a name="when-to-use-focus-visual-styles"></a>フォーカス表示スタイルを使用する場合  
 概念的には、コントロールに適用されるフォーカス表示スタイルの外観は、コントロール間で一貫性のあるものにする必要があります。 一貫性を確保する 1 つの方法は、テーマ全体を構成する場合にのみフォーカス表示スタイルを変更することです。コントロール。 または、ページまたは UI 内のすべてのキーボード フォーカス可能な要素のスタイルを同じスタイル (または類似のスタイル) を使用することもできます。  
  
 テーマ<xref:System.Windows.FrameworkElement.FocusVisualStyle%2A>の一部ではない個々のコントロール スタイルに対して設定することは、フォーカス表示スタイルの使用目的ではありません。 これは、コントロール間の表示動作が一貫していないため、キーボード フォーカスに関するユーザー エクスペリエンスが混乱する可能性があります。 テーマ全体で意図的に一貫性のないキーボード フォーカスに対するコントロール固有の動作を意図している場合は、 や などの<xref:System.Windows.UIElement.IsFocused%2A>個々の入力状態プロパティに対して、トリガをスタイルで使用する<xref:System.Windows.UIElement.IsKeyboardFocused%2A>方がはるかに優れた方法です。  
  
 フォーカス表示スタイルは、キーボード フォーカス専用に機能します。 そのため、フォーカス表示スタイルはアクセシビリティ機能の一種です。 マウス、キーボード、プログラムのいずれを使用しても、フォーカスの種類に対する UI の変更が必要な場合は、フォーカス表示スタイルを使用<xref:System.Windows.UIElement.IsFocused%2A>しないでください。 <xref:System.Windows.UIElement.IsKeyboardFocusWithin%2A>  
  
<a name="How"></a>
## <a name="how-to-create-a-focus-visual-style"></a>フォーカス表示スタイルを作成する方法  
 フォーカス表示スタイルに対して作成するスタイルは、 の<xref:System.Windows.Style.TargetType%2A><xref:System.Windows.Controls.Control>スタイルを持つ必要があります。 スタイルは主に<xref:System.Windows.Controls.ControlTemplate>. フォーカス表示スタイルが に割り当てられる型としてターゲット型を指定しないでください<xref:System.Windows.FrameworkElement.FocusVisualStyle%2A>。  
  
 ターゲットの型は常に<xref:System.Windows.Controls.Control>ので、すべてのコントロールに共通するプロパティを使用してスタイルを設定する必要<xref:System.Windows.Controls.Control>があります (クラスとその基本クラスのプロパティを使用)。 UI 要素のオーバーレイとして適切に機能し、コントロールの機能領域を隠さないテンプレートを作成する必要があります。 これは通常、視覚的なフィードバックがコントロールの余白の外側に表示されるか、フォーカス表示スタイルが適用されるコントロールのヒット テストをブロックしない一時的または控えめな効果として表示されることを意味します。 オーバーレイ テンプレートのサイズと位置を決定するのに役立つ、テンプレート バインドで使用できるプロパティには、 <xref:System.Windows.FrameworkElement.ActualHeight%2A> <xref:System.Windows.FrameworkElement.ActualWidth%2A>、 <xref:System.Windows.FrameworkElement.Margin%2A>、<xref:System.Windows.Controls.Control.Padding%2A>および が含まれます。  
  
<a name="Alternatives"></a>
## <a name="alternatives-to-using-a-focus-visual-style"></a>フォーカス表示スタイルを使用する代わりに  
 フォーカス表示スタイルを使用することが適切でない状況では、単一のコントロールのスタイルを設定するだけか、コントロール テンプレートをより詳細に制御する必要があるため、ビジュアルを作成できる他の多くのアクセス可能なプロパティとテクニックがあります。フォーカスの変更に応じて動作します。  
  
 トリガー、セッター、およびイベントセッターについては、[すべて「スタイル設定とテンプレート](../../../desktop-wpf/fundamentals/styles-templates-overview.md)」で詳しく説明しています。 ルーティング イベントの処理については、「[ルーティング イベントの概要](routed-events-overview.md)」を参照してください。  
  
### <a name="iskeyboardfocused"></a>フォーカスを絞った  
 特にキーボード フォーカスに関心がある場合は<xref:System.Windows.UIElement.IsKeyboardFocused%2A>、依存関係プロパティをプロパティ<xref:System.Windows.Trigger>に使用できます。 スタイルまたはテンプレートのプロパティ トリガーは、単一のコントロールに対して非常に特別なキーボード フォーカス動作を定義する場合に、他のコントロールのキーボード フォーカスの動作と視覚的に一致しない場合に、より適切な手法です。  
  
 もう 1 つの<xref:System.Windows.UIElement.IsKeyboardFocusWithin%2A>同様の依存関係プロパティは、 を使用して、キーボード フォーカスがコンポジティング内またはコントロールの機能領域内にある場合に使用するのが適切な場合があります。 例えば、複数のコントロールを<xref:System.Windows.UIElement.IsKeyboardFocusWithin%2A>グループ化するパネルが、そのパネル内の個々の要素に対してより正確にフォーカスされている場合でも、異なる表示方法で表示されるようにトリガーを配置できます。  
  
 イベント<xref:System.Windows.UIElement.GotKeyboardFocus>と<xref:System.Windows.UIElement.LostKeyboardFocus>(プレビューと同等のイベント) を使用することもできます。 これらのイベントは、の基礎として使用することも、<xref:System.Windows.EventSetter>分離コード内のイベントのハンドラーを記述することもできます。  
  
### <a name="other-focus-properties"></a>その他のフォーカス プロパティ  
 フォーカスを変更する考えられる原因をすべて視覚的な動作にする場合は<xref:System.Windows.UIElement.IsFocused%2A>、依存関係プロパティに基づいてセッターまたはトリガを作成するか、または に使用<xref:System.Windows.UIElement.GotFocus>される<xref:System.Windows.UIElement.LostFocus>or イベント<xref:System.Windows.EventSetter>を使用する必要があります。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.FrameworkElement.FocusVisualStyle%2A>
- [スタイルとテンプレート](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [フォーカスの概要](focus-overview.md)
- [入力の概要](input-overview.md)
