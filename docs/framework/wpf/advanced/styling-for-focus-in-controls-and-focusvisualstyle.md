---
title: コントロールのフォーカスのスタイルと FocusVisualStyle
ms.date: 03/30/2017
helpviewer_keywords:
- keyboard focus [WPF]
- focus [WPF], visual styling
- styles [WPF], focus visual style
ms.assetid: 786ac576-011b-4d72-913b-558deccb9b35
ms.openlocfilehash: 745c2174c54ed072f91a6d5eb3b43d5385e96b90
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62053375"
---
# <a name="styling-for-focus-in-controls-and-focusvisualstyle"></a>コントロールのフォーカスのスタイルと FocusVisualStyle
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] キーボード フォーカスを受け取るときに、コントロールの外観を変更するための 2 つの並列メカニズムを提供します。 最初のメカニズムは、プロパティなどのプロパティ set アクセス操作子を使用する<xref:System.Windows.UIElement.IsKeyboardFocused%2A>スタイルまたはコントロールに適用されているテンプレート内で。 2 つ目のメカニズムの値として別のスタイルを提供する、<xref:System.Windows.FrameworkElement.FocusVisualStyle%2A>プロパティまたはその他の UI コントロールのビジュアル ツリーを変更するのではなく、コントロールの上に描画される装飾の個別のビジュアル ツリーを作成する「フォーカスのビジュアル スタイル」置換することで要素。 このトピックでは、これらのメカニズムが適切なシナリオについて説明します。  

<a name="Purpose"></a>   
## <a name="the-purpose-of-focus-visual-style"></a>フォーカスのビジュアル スタイルの目的は、  
 フォーカス表示スタイルの機能は、UI 要素にキーボード ナビゲーションに基づく visual ユーザーからのフィードバックを導入するための一般的な「オブジェクト モデル」を提供します。 特定のテンプレート構成を知る必要も、コントロールに新しいテンプレートを適用することがなく可能です。  
  
 ただし、フォーカスの視覚スタイルの機能は、コントロール テンプレートを知ることがなく機能するために正確にフォーカスのビジュアル スタイルを使用してコントロールの表示可能な視覚的フィードバックは必ずしも制限されます。 機能が実際には、テンプレートを通じて、コントロールの描画によって作成されたビジュアル ツリーの上に別のビジュアル ツリー (装飾) をオーバーレイすることです。 表示されるスタイルを使用してこの個別のビジュアル ツリーを定義する、<xref:System.Windows.FrameworkElement.FocusVisualStyle%2A>プロパティ。  
  
<a name="Default"></a>   
## <a name="default-focus-visual-style-behavior"></a>フォーカスの Visual スタイルの既定の動作  
 フォーカス表示スタイルは、キーボードでフォーカスのアクションが開始された場合にのみ機能します。 任意のマウス操作またはプログラムによるフォーカスの変更は、visual スタイルのフォーカス モードを無効にします。 フォーカス モードの違いの詳細については、次を参照してください。[フォーカスの概要](focus-overview.md)します。  
  
 コントロールのテーマには、テーマのすべてのコントロールのフォーカスの視覚スタイルになる既定フォーカス visual スタイルの動作が含まれます。 このテーマ スタイルは、静的なキーの値によって識別される<xref:System.Windows.SystemParameters.FocusVisualStyleKey%2A>します。 アプリケーション レベルで、独自のフォーカス表示スタイルを宣言するときに、このテーマから既定のスタイル動作を置き換えます。 また、全体のテーマを定義する場合に、全体のテーマの既定の動作のスタイルを定義するこれと同じキーを使用する必要があります。  
  
 テーマ、既定のフォーカスの視覚スタイルは一般に、非常に単純です。 おおよその近似値を次に示します。  
  
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
## <a name="when-to-use-focus-visual-styles"></a>フォーカスの視覚スタイルを使用する場合  
 概念的には、コントロールに適用されるフォーカスの視覚スタイルの外観は、コントロール間で一貫している必要があります。 一貫性を実現する方法の 1 つがコントロールから続きに visual スタイルで、テーマで定義されている各コントロールを取得フォーカス表示スタイルをまったく同じまたはスタイルのいくつかのバリエーションのいずれかを全体のテーマを作成する場合にのみが関連する視覚的にフォーカスを変更するにはrol します。 ページまたは UI にキーボード フォーカスのすべての要素のスタイルを設定する同じスタイル (または同様のスタイル) を使用する場合があります。  
  
 設定<xref:System.Windows.FrameworkElement.FocusVisualStyle%2A>テーマの一部ではない個々 のコントロールのスタイルはフォーカスの使用目的ではない視覚スタイル。 これは、コントロール間の一貫性のない visual 動作がキーボード フォーカスに関するユーザー エクスペリエンスは混乱を招く可能性があるためにです。 キーボード フォーカスは、テーマ間で一貫性のあるは意図的にコントロール固有の動作をコントロールするはるかに優れた方法は、スタイルのトリガーをなど、個々 の入力の状態のプロパティを使用します<xref:System.Windows.UIElement.IsFocused%2A>または<xref:System.Windows.UIElement.IsKeyboardFocused%2A>します。  
  
 フォーカスの視覚スタイルがキーボード フォーカスの専用の機能です。 そのため、フォーカスの視覚スタイルは、ユーザー補助機能の種類です。 マウスを使用しているかどうか、フォーカスの任意の型の UI の変更をする場合キーボード、またはプログラムによって、しするが、フォーカスの視覚スタイルを使用しないでくださいし、set アクセス操作子とスタイルまたはテンプレートの全般的な焦点プロパティの値から作業をでトリガーを使用する必要があります。など<xref:System.Windows.UIElement.IsFocused%2A>または<xref:System.Windows.UIElement.IsKeyboardFocusWithin%2A>します。  
  
<a name="How"></a>   
## <a name="how-to-create-a-focus-visual-style"></a>フォーカス表示スタイルを作成する方法  
 フォーカスのビジュアル スタイルを指定することは常に作成する、スタイル、<xref:System.Windows.Style.TargetType%2A>の<xref:System.Windows.Controls.Control>します。 主にスタイルが加え、<xref:System.Windows.Controls.ControlTemplate>します。 型であることに、フォーカスの視覚スタイルが割り当てられている対象の型を指定しない、<xref:System.Windows.FrameworkElement.FocusVisualStyle%2A>します。  
  
 対象の型は常にため<xref:System.Windows.Controls.Control>、すべてのコントロールに共通するプロパティを使用してスタイルを設定する必要があります (のプロパティを使用して、<xref:System.Windows.Controls.Control>クラスとその基本クラス)。 UI 要素にオーバーレイとして正しく機能して、コントロールの機能領域を隠さないテンプレートを作成する必要があります。 つまり、通常、視覚的なフィードバックが表示されること、コントロールのマージンの外部またはコントロールのヒット テストがブロックされていない一時的または控えめな効果と、フォーカスのビジュアル スタイルを適用します。 サイズ変更と、オーバーレイのテンプレートの配置を決定するために利用できるテンプレートのバインドで使用できるプロパティが含まれます<xref:System.Windows.FrameworkElement.ActualHeight%2A>、 <xref:System.Windows.FrameworkElement.ActualWidth%2A>、 <xref:System.Windows.FrameworkElement.Margin%2A>、および<xref:System.Windows.Controls.Control.Padding%2A>します。  
  
<a name="Alternatives"></a>   
## <a name="alternatives-to-using-a-focus-visual-style"></a>フォーカスのビジュアル スタイルの使用に代わる方法  
 状況でフォーカスのビジュアル スタイルを使用して、適切でない 1 つのコントロールをスタイル設定はのみか、またはコントロール テンプレートをより細かく制御するためがあるその他の多くのアクセス可能なプロパティやビジュアルを作成できる手法フォーカスの変更に応答で動作します。  
  
 トリガー、setter、およびイベント setter がすべてで詳しく説明されている[スタイルとテンプレート](../controls/styling-and-templating.md)します。 ルーティング イベントの処理は、後ほど[ルーティング イベントの概要](routed-events-overview.md)します。  
  
### <a name="iskeyboardfocused"></a>IsKeyboardFocused  
 キーボード フォーカスを具体的には関心がある場合、<xref:System.Windows.UIElement.IsKeyboardFocused%2A>プロパティの依存関係プロパティを使用できる<xref:System.Windows.Trigger>します。 スタイルまたはテンプレートのいずれかのプロパティ トリガーは、非常に具体的には、1 つのコントロールについては、他のコントロールのキーボード フォーカスの動作に一致する可能性がありますいない視覚的には、キーボード フォーカスの動作を定義するためのより適切な手法です。  
  
 別のような依存関係プロパティが<xref:System.Windows.UIElement.IsKeyboardFocusWithin%2A>、合成内またはコントロールの機能領域内ではどこかに、視覚的に、そのキーボード フォーカスを呼び出そうとする場合に使用する適切なされる可能性があります。 たとえば、配置する場合があります、<xref:System.Windows.UIElement.IsKeyboardFocusWithin%2A>トリガー場合でも、キーボード フォーカスがより正確に可能性があります、いくつかのコントロールをグループ化するパネルが異なる方法に表示されるようにそのパネル内の各要素にします。  
  
 イベントを使用することもできます。<xref:System.Windows.UIElement.GotKeyboardFocus>と<xref:System.Windows.UIElement.LostKeyboardFocus>(と同様に、プレビューの同等)。 基礎として、これらのイベントを使用することができます、 <xref:System.Windows.EventSetter>、または分離コードでイベントのハンドラーを記述することができます。  
  
### <a name="other-focus-properties"></a>その他のフォーカス プロパティ  
 Setter の基本やをトリガーする必要がありますのフォーカスを変更するすべての考えられる原因を視覚的な動作を生成する場合は、<xref:System.Windows.UIElement.IsFocused%2A>依存関係プロパティでは、別の方法で、<xref:System.Windows.UIElement.GotFocus>または<xref:System.Windows.UIElement.LostFocus>に使用されるイベント、<xref:System.Windows.EventSetter>します。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.FrameworkElement.FocusVisualStyle%2A>
- [スタイルとテンプレート](../controls/styling-and-templating.md)
- [フォーカスの概要](focus-overview.md)
- [入力の概要](input-overview.md)
