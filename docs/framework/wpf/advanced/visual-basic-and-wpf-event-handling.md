---
title: Visual Basic と WPF のイベント処理
ms.date: 03/30/2017
helpviewer_keywords:
- Visual Basic [WPF], event handlers
- event handlers [WPF], Visual Basic
ms.assetid: ad4eb9aa-3afc-4a71-8cf6-add3fbea54a1
ms.openlocfilehash: 736542a4d12f96c40e836f84066dbeb8e66b9436
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2019
ms.locfileid: "57358952"
---
# <a name="visual-basic-and-wpf-event-handling"></a>Visual Basic と WPF のイベント処理
Microsoft Visual Basic .NET 言語の具体的を使えば、言語固有`Handles`属性を持つイベント ハンドラーをアタッチまたはを使用してではなく、インスタンスにイベント ハンドラーを関連付けるキーワード、<xref:System.Windows.UIElement.AddHandler%2A>メソッド。 ただし、`Handles`ために、ハンドラーのインスタンスにアタッチするための手法はいくつかの制限には、`Handles`構文は、の特定のルーティング イベント機能の一部をサポートできない、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]イベント システム。  
  
## <a name="using-handles-in-a-wpf-application"></a>WPF アプリケーションで「ハンドル」の使用  
 インスタンスとのイベントに接続されているイベント ハンドラー`Handles`すべてこれは、要素の属性値を割り当てられているイベント ハンドラーの要件でも、インスタンスの部分クラス宣言内で定義する必要があります。 だけを指定することができます`Handles`がページ上の要素の<xref:System.Windows.FrameworkContentElement.Name%2A>プロパティの値 (または[X:name ディレクティブ](../../xaml-services/x-name-directive.md)宣言)。 これは、ため、<xref:System.Windows.FrameworkContentElement.Name%2A>で[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]をサポートするために必要なインスタンスの参照を作成します、 *Instance.Event*で必要な参照形式、`Handles`構文。 使用できる唯一の要素`Handles`せず、<xref:System.Windows.FrameworkContentElement.Name%2A>参照が部分クラスを定義するルート要素のインスタンス。  
  
 分離することで、複数の要素に同じハンドラーを割り当てることができます*Instance.Event*後参照`Handles`コンマで区切ります。  
  
 使用することができます`Handles`を同じ 1 つ以上のハンドラーを割り当てる*Instance.Event*参照。 ハンドラーがでは指定された順序に任意の重要度を割り当てないでください、 `Handles` ; を参照する任意の順序で、同じイベントを処理するハンドラーを起動できることを想定してください。  
  
 追加されたハンドラーを削除する`Handles`の宣言で呼び出すことができます<xref:System.Windows.UIElement.RemoveHandler%2A>します。  
  
 使用することができます`Handles`メンバー テーブルで処理されるイベントを定義するインスタンスにハンドラーをアタッチする限り、ルーティング イベントのハンドラーをアタッチします。 ルーティング イベントに結び付けられているハンドラーの`Handles`としてアタッチされているハンドラーと同じルーティング規則に従う[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]属性、またはの一般的なシグネチャを持つ<xref:System.Windows.UIElement.AddHandler%2A>します。 つまり、イベントが処理されて既に場合 (、<xref:System.Windows.RoutedEventArgs.Handled%2A>プロパティ、イベント データが、 `True`) とハンドラーをアタッチし、`Handles`そのイベントのインスタンスへの応答は呼び出されません。 またはクラスには、現在の要素または経路の直前の要素を処理して、ルート上で別の要素のインスタンス ハンドラーによって処理されたイベントをマークする可能性があります。 トンネル/バブルのペアになっているイベントをサポートする入力イベントでトンネリングのルートを処理イベントのペア マークがあることがあります。 ルーティング イベントの詳細については、「[ルーティング イベントの概要](routed-events-overview.md)」を参照してください。  
  
## <a name="limitations-of-handles-for-adding-handlers"></a>「ハンドル」のハンドラーを追加するための制限事項  
 `Handles` 添付イベントのハンドラーを参照することはできません。 使用する必要があります、 `add` 、その添付イベントのアクセサー メソッドまたは*typename.eventname*イベント属性[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]します。 詳細については、[ルーティング イベントの概要](routed-events-overview.md)を参照してください。  
  
 ルーティング イベントの場合のみ使用できます`Handles`ハンドラーを割り当てるインスタンスのメンバー テーブルでそのイベントが存在するインスタンス。 ただし、ルーティング イベントで一般に、親要素できます、子要素からのイベントのリスナーを場合でも、親要素では、そのメンバー テーブルでは、そのイベントはありません。 属性構文でこれを指定できます、 *typename.membername*属性の種類が実際に処理するイベントを定義しますを修飾するフォーム。 たとえば、親`Page`(なしで`Click`イベントが定義されている) 形式で、属性のハンドラーを割り当てることでボタン クリック イベントをリッスンできます`Button.Click`します。 `Handles`はサポートしていません、 *typename.membername*フォームの 競合しているをサポートする必要がありますので*Instance.Event*フォーム。 詳細については、[ルーティング イベントの概要](routed-events-overview.md)を参照してください。  
  
 `Handles` 既に処理済みとしてマークするイベントに対して呼び出されるハンドラーをアタッチすることはできません。 代わりに、コードと呼び出しを使用する必要があります、`handledEventsToo`のオーバー ロード<xref:System.Windows.UIElement.AddHandler%28System.Windows.RoutedEvent%2CSystem.Delegate%2CSystem.Boolean%29>します。  
  
> [!NOTE]
>  使用しないでください、 `Handles` XAML で、同じイベントに対してイベント ハンドラーを指定すると、Visual Basic コードの構文。 この場合、イベント ハンドラーが 2 回呼び出されます。  
  
## <a name="how-wpf-implements-handles-functionality"></a>WPF 実装「の処理方法」機能  
 ときに、[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]ページがコンパイルされると、中間ファイルは、宣言`Friend``WithEvents`がページ上のすべての要素への参照を<xref:System.Windows.FrameworkContentElement.Name%2A>プロパティ セット (または[X:name ディレクティブ](../../xaml-services/x-name-directive.md)宣言)。 各名前付きインスタンスは、潜在的要素を使用してハンドラーを割り当てることができる`Handles`します。  
  
> [!NOTE]
>  内で[!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)]、[!INCLUDE[TLA2#tla_intellisense](../../../../includes/tla2sharptla-intellisense-md.md)]要素が使用できる入力候補を表示できます、`Handles`ページ内の参照。 ただし、このかかる 1 回のコンパイル パス中間ファイルが設定できるように、`Friends`参照。  
  
## <a name="see-also"></a>関連項目
- <xref:System.Windows.UIElement.AddHandler%2A>
- [ルーティング イベントの処理済みとしてのマーキング、およびクラス処理](marking-routed-events-as-handled-and-class-handling.md)
- [ルーティング イベントの概要](routed-events-overview.md)
- [XAML の概要 (WPF)](xaml-overview-wpf.md)
