---
title: Visual Basic と WPF のイベント処理
ms.date: 03/30/2017
helpviewer_keywords:
- Visual Basic [WPF], event handlers
- event handlers [WPF], Visual Basic
ms.assetid: ad4eb9aa-3afc-4a71-8cf6-add3fbea54a1
ms.openlocfilehash: 8407958ec76be7e402025ece57371e67581e5291
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69942127"
---
# <a name="visual-basic-and-wpf-event-handling"></a>Visual Basic と WPF のイベント処理
Microsoft Visual Basic .net 言語では、言語固有`Handles`のキーワードを使用して、イベントハンドラーを属性にアタッチしたり、 <xref:System.Windows.UIElement.AddHandler%2A>メソッドを使用したりする代わりに、イベントハンドラーをインスタンスに関連付けることができます。 ただし、インスタンスにハンドラーをアタッチする`Handles` [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 方法にはいくつかの制限があります。この構文では、イベントシステムの特定のルーティングイベント機能の一部がサポートされ`Handles`ないためです。  
  
## <a name="using-handles-in-a-wpf-application"></a>WPF アプリケーションでの "ハンドル" の使用  
 で`Handles`インスタンスおよびイベントに接続されているイベントハンドラーはすべて、インスタンスの部分クラス宣言内で定義されている必要があります。これは、要素の属性値を通じて割り当てられたイベントハンドラーにも必要です。 を指定`Handles`できるのは、 <xref:System.Windows.FrameworkContentElement.Name%2A>プロパティ値 (または[x:Name ディレクティブ](../../xaml-services/x-name-directive.md)が宣言されている) を持つページ上の要素だけです。 これは、の<xref:System.Windows.FrameworkContentElement.Name%2A>に[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]よって、*インスタンス*をサポートするために必要なインスタンス参照が作成されるため`Handles`です。この構文では、イベント参照形式が必要です。 参照<xref:System.Windows.FrameworkContentElement.Name%2A>がない場合に使用できる唯一`Handles`の要素は、部分クラスを定義するルート要素のインスタンスです。  
  
 インスタンスを分離することによって、複数の要素に同じハンドラーを`Handles`割り当てることができます *。イベント*は、コンマで区切って参照します。  
  
 を使用`Handles`して、同じインスタンスに複数のハンドラーを割り当てることができ*ます。イベント*の参照。 `Handles`参照でハンドラーが指定されている順序には重要度を割り当てないでください。同じイベントを処理するハンドラーを任意の順序で呼び出すことができます。  
  
 宣言`Handles`にで追加されたハンドラーを削除するには、を<xref:System.Windows.UIElement.RemoveHandler%2A>呼び出すことができます。  
  
 を使用`Handles`すると、メンバーテーブルで処理されるイベントを定義するインスタンスにハンドラーをアタッチできる限り、ルーティングイベントのハンドラーをアタッチできます。 ルーティングイベントの場合、に`Handles`アタッチされているハンドラーは、属性として、または共通の<xref:System.Windows.UIElement.AddHandler%2A>シグネチャを使用して、属性として[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]アタッチされるハンドラーと同じルーティング規則に従います。 これは、イベントが既に処理済みとして<xref:System.Windows.RoutedEventArgs.Handled%2A>マークされている場合`True`(イベントデータのプロパティが`Handles`の場合)、そのイベントインスタンスへの応答としてにアタッチされたハンドラーが呼び出されないことを意味します。 イベントは、ルート内の別の要素のインスタンスハンドラーによって処理されるようにマークすることも、現在の要素またはルートの前の要素に対するクラス処理によって処理することもできます。 ペアのトンネル/バブルイベントをサポートする入力イベントの場合、トンネリングルートでは、イベントペアが処理済みとマークされている可能性があります。 ルーティング イベントの詳細については、「[ルーティング イベントの概要](routed-events-overview.md)」を参照してください。  
  
## <a name="limitations-of-handles-for-adding-handlers"></a>ハンドラーを追加するための "処理" の制限事項  
 `Handles`添付イベントのハンドラーを参照できません。 この添付イベントの`add`アクセサーメソッド、またはの[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] *typename*イベント属性を使用する必要があります。 詳細については、「[ルーティングイベントの概要](routed-events-overview.md)」を参照してください。  
  
 ルーティングイベントの場合は、インスタンスメンバー `Handles`テーブルにそのイベントが存在するインスタンスに対してのみ、を使用してハンドラーを割り当てることができます。 ただし、一般的なルーティングイベントでは、親要素がメンバーテーブルにそのイベントを持たない場合でも、子要素からのイベントのリスナーになります。 属性構文では、 *typename. membername*属性フォームを使用して指定できます。これは、処理するイベントを実際に定義する型を修飾します。 たとえば、イベントが定義`Page`されて`Click`いない親は、フォーム`Button.Click`で属性ハンドラーを割り当てることによって、ボタンクリックイベントをリッスンできます。 ただし`Handles` 、では、競合している*インスタンス*をサポートする必要があるため、 *typename. membername*フォームはサポートしていません。 詳細については、「[ルーティングイベントの概要](routed-events-overview.md)」を参照してください。  
  
 `Handles`既に処理済みとしてマークされているイベントに対して呼び出されるハンドラーをアタッチすることはできません。 代わりに、コードを使用し、の`handledEventsToo` <xref:System.Windows.UIElement.AddHandler%28System.Windows.RoutedEvent%2CSystem.Delegate%2CSystem.Boolean%29>オーバーロードを呼び出す必要があります。  
  
> [!NOTE]
> XAML で同じイベント`Handles`に対してイベントハンドラーを指定する場合は、Visual Basic コードで構文を使用しないでください。 この場合、イベントハンドラーは2回呼び出されます。  
  
## <a name="how-wpf-implements-handles-functionality"></a>WPF が "ハンドル" 機能を実装する方法  
 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] ページがコンパイルされると、中間ファイルは、<xref:System.Windows.FrameworkContentElement.Name%2A> プロパティが設定されている (または [x:Name Directive](../../xaml-services/x-name-directive.md) が宣言されている) ページ上のすべての要素への `Friend` `WithEvents` 参照を宣言します。 各名前付きインスタンスは、によって`Handles`ハンドラーに割り当てることができる要素である可能性があります。  
  
> [!NOTE]
> で[!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)]は、IntelliSense で、ページ内の`Handles`参照に使用できる要素の完了を確認できます。 ただし、この場合、中間ファイルがすべての`Friends`参照を設定できるように、1つのコンパイルパスが必要になることがあります。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.UIElement.AddHandler%2A>
- [ルーティング イベントの処理済みとしてのマーキング、およびクラス処理](marking-routed-events-as-handled-and-class-handling.md)
- [ルーティング イベントの概要](routed-events-overview.md)
- [XAML の概要 (WPF)](xaml-overview-wpf.md)
