---
title: プロパティ変更イベント
ms.date: 03/30/2017
helpviewer_keywords:
- dependency properties [WPF], change events
- property value changes [WPF]
- change events [WPF], property
- events [WPF], change in property values
- creating property triggers [WPF]
- property change events [WPF], types of
- property change events [WPF]
- property triggers [WPF]
- identifying changed property events [WPF]
- property triggers [WPF], definition of
ms.assetid: 0a7989df-9674-4cc1-bc50-5d8ef5d9c055
ms.openlocfilehash: b6f625f76e230b7d6bf0488bfa75c227de31a5d0
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59166206"
---
# <a name="property-change-events"></a>プロパティ変更イベント
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] では、プロパティ値の変更に応答して発生するさまざまなイベントが定義されています。 通常、プロパティは依存関係プロパティです。 イベント自体は、ルーティング イベントのこともあれば、標準の [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] イベントのこともあります。 要素ツリーを通じて適切にルーティングされるプロパティ変更もあれば、プロパティが変更されたオブジェクトにのみ関係するプロパティ変更もあるため、イベントの定義はシナリオによって異なります。  
  
## <a name="identifying-a-property-change-event"></a>プロパティ変更イベントの識別  
 シグネチャ パターンまたは名前付けパターンに基づいてプロパティ変更を報告するすべてのイベントが、プロパティ変更イベントとして明示的に識別されるわけではありません。 通常、[!INCLUDE[TLA#tla_sdk](../../../../includes/tlasharptla-sdk-md.md)] ドキュメント内のイベントの説明では、イベントがプロパティ値の変更に直接結び付くものであるかどうかが示されており、プロパティとイベントのクロス リファレンスが提供されます。  
  
### <a name="routedpropertychanged-events"></a>RoutedPropertyChanged イベント  
 特定のイベントでは、プロパティ変更イベントで明示的に使用されるイベント データ型とデリゲートを使用します。 イベントのデータ型は<xref:System.Windows.RoutedPropertyChangedEventArgs%601>、デリゲートと<xref:System.Windows.RoutedPropertyChangedEventHandler%601>します。 イベント データもデリゲートも、ジェネリック型パラメーターを使用します。これは、ハンドラーを定義するときに、変更するプロパティの実際の型を指定するために使用されるものです。 イベント データには、2 つのプロパティが含まれている<xref:System.Windows.RoutedPropertyChangedEventArgs%601.OldValue%2A>と<xref:System.Windows.RoutedPropertyChangedEventArgs%601.NewValue%2A>、これは、どちらも、型の引数として渡さイベント データ。  
  
 名前の "Routed" 部分は、プロパティ変更イベントがルーティング イベントして登録されていることを示しています。 プロパティ変更イベントのルーティングには、子要素 (コントロールの複合部分) のプロパティが値を変更した場合に、コントロールのトップ レベルがプロパティ変更イベントを受信できるというメリットがあります。 たとえばが組み込まれているコントロールを作成する場合があります、<xref:System.Windows.Controls.Primitives.RangeBase>などを制御、<xref:System.Windows.Controls.Slider>します。 場合の値、<xref:System.Windows.Controls.Primitives.RangeBase.Value%2A>スライダー部分では、プロパティの変更の一部ではなく、親コントロールでは、その変更を処理することです。  
  
 古い値と新しい値があるため、このイベント ハンドラーがプロパティ値の検証コントロールとして使用される可能性があります。 しかし、プロパティ変更イベントの多くは、このような目的で設計されているわけではありません。 通常、値の提供は、他のロジック領域のコードでその値を処理するために行われますが、イベント ハンドラー内から値を実際に変更することはお勧めできません。また、ハンドラーの実装方法によっては、意図しない再帰が生じることもあります。  
  
 プロパティがカスタム依存関係プロパティの場合、またはインスタンス化コードが定義されている派生クラスの場合に組み込まれているプロパティの変更を追跡する優れたメカニズムがある場合、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]プロパティ システム:プロパティ システム コールバック<xref:System.Windows.CoerceValueCallback>と<xref:System.Windows.PropertyChangedCallback>します。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] プロパティ システムを使用して検証および強制型変換を行う方法の詳細については、「[依存関係プロパティのコールバックと検証](dependency-property-callbacks-and-validation.md)」および「[カスタム依存関係プロパティ](custom-dependency-properties.md)」を参照してください。  
  
### <a name="dependencypropertychanged-events"></a>DependencyPropertyChanged イベント  
 プロパティ変更イベントのシナリオの一部である型の別のペアが<xref:System.Windows.DependencyPropertyChangedEventArgs>と<xref:System.Windows.DependencyPropertyChangedEventHandler>します。 これらのプロパティ変更のイベントはルーティングされません。これらは、標準の [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] イベントです。 <xref:System.Windows.DependencyPropertyChangedEventArgs> レポートの種類から派生しないため、特殊なイベント データは、 <xref:System.EventArgs>;<xref:System.Windows.DependencyPropertyChangedEventArgs>は構造体、クラスではなくです。  
  
 使用するイベント<xref:System.Windows.DependencyPropertyChangedEventArgs>と<xref:System.Windows.DependencyPropertyChangedEventHandler>より多少一般的`RoutedPropertyChanged`イベント。 これらの型を使用するイベントの例は、<xref:System.Windows.UIElement.IsMouseCapturedChanged>します。  
  
 ような<xref:System.Windows.RoutedPropertyChangedEventArgs%601>、<xref:System.Windows.DependencyPropertyChangedEventArgs>もプロパティ、新旧の値を報告します。 そのため、値を適用して行う操作に関して同じ注意が当てはまります。イベントに応答して送信元で値を再度変更することは、一般的にはお勧めできません。  
  
## <a name="property-triggers"></a>プロパティ トリガー  
 プロパティ変更イベントに密接に関係する概念がプロパティ トリガーです。 プロパティ トリガーはスタイルまたはテンプレート内に作成され、プロパティ トリガーが割り当てられるプロパティの値に基づく条件付きの動作を作成できます。  
  
 プロパティ トリガーのプロパティは、依存関係プロパティでなければなりません。 これは、読み取り専用の依存関係プロパティにすることができます (多くの場合そのようになっています)。 コントロールによって公開される依存関係プロパティが、プロパティ トリガーになるように部分的に設計されている場合、プロパティ名が "Is" で始まっていることで見分けられます。 この名前付けがされたプロパティは、多くの場合、読み取り専用のブール型の依存関係プロパティです。このプロパティの主要なシナリオは、リアルタイム UI に影響を及ぼす可能性があるためにプロパティ トリガーの候補である、レポート コントロール ステートです。  
  
 これらのプロパティの一部は、専用のプロパティ変更イベントも持ちます。 たとえば、プロパティ<xref:System.Windows.UIElement.IsMouseCaptured%2A>プロパティ変更イベントが<xref:System.Windows.UIElement.IsMouseCapturedChanged>します。 プロパティ自体がその値が入力のシステムによって調整された読み取り専用、および入力システムが発生<xref:System.Windows.UIElement.IsMouseCapturedChanged>リアルタイムの変更のたびにします。  
  
 プロパティ トリガーを使用してプロパティの変更に対処する場合は、本当のプロパティ変更イベントに比べ、いくつかの制限があります。  
  
 プロパティ トリガーは、完全一致ロジックを通じて動作します。 プロパティと、トリガーが処理する特定の値を示す値を指定します。次に例を示します: `<Setter Property="IsMouseCaptured" Value="true"> ... </Setter>`。 この制限のため、ほとんどのプロパティ トリガーの使用は、ブール型のプロパティか、専用の列挙値を使用するプロパティが対象です。この場合、有効な値の範囲は、各ケースに対応するトリガーを定義するために十分な程度管理することができます。 または、プロパティ トリガーは、項目のカウントがゼロに達した場合など、特別な値に対してのみ存在する可能性があります。プロパティ値がゼロから再び変更するケースに対処するトリガーはありません (すべてのケースに対応するトリガーではなく、コード イベント ハンドラー、または、値がゼロ以外のときにトリガー状態を再び元に戻す既定の動作が必要です)。  
  
 プロパティ トリガーの構文は、プログラミングの "if" ステートメントに似ています。 トリガー条件が true の場合、プロパティ トリガーの "本体" が "実行" されます。 プロパティ トリガーの "本体" はコードではなく、マークアップです。 そのマークアップは、1 つまたは複数の使用に限定<xref:System.Windows.Setter>スタイルまたはテンプレートが適用されているオブジェクトの他のプロパティを設定する要素。  
  
 さまざまな使用可能な値を持つプロパティ トリガーの"if"条件をオフセットするには一般に、既定値を使用してその同じプロパティ値を設定することをお勧め、<xref:System.Windows.Setter>します。 これにより、<xref:System.Windows.Trigger>が含む setter が優先トリガー条件が true の場合、および<xref:System.Windows.Setter>です内、<xref:System.Windows.Trigger>トリガー条件が false のときに、優先順位になります。  
  
 プロパティ トリガーは、通常、1 つ以上の外観プロパティが、同じ要素の別のプロパティの状態に基づいて変更されるシナリオに適しています。  
  
 プロパティ トリガーの詳細については、「[スタイルとテンプレート](../controls/styling-and-templating.md)」を参照してください。  
  
## <a name="see-also"></a>関連項目

- [ルーティング イベントの概要](routed-events-overview.md)
- [依存関係プロパティの概要](dependency-properties-overview.md)
