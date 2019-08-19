---
title: データ バインディングの概要
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data conversion for binding [WPF]
- binding data [WPF], about data binding
- data binding [WPF], about data binding
- conversion for data binding [WPF]
ms.assetid: c707c95f-7811-401d-956e-2fffd019a211
ms.openlocfilehash: 44a35131273c6f191ab5da5bc1639d97bd961ff1
ms.sourcegitcommit: 29a9b29d8b7d07b9c59d46628da754a8bff57fa4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/17/2019
ms.locfileid: "69567522"
---
# <a name="data-binding-overview"></a>データ バインディングの概要
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] データ バインディングは、データを表示したり操作するための単純で一貫した方法をアプリケーションに提供します。 要素は、共通言語ランタイム (CLR) オブジェクトおよび[!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)]の形式で、さまざまなデータソースのデータにバインドできます。 <xref:System.Windows.Controls.ContentControl>などの <xref:System.Windows.Controls.Button>と<xref:System.Windows.Controls.ItemsControl>など <xref:System.Windows.Controls.ListBox>と<xref:System.Windows.Controls.ListView>を 1 つのデータ項目の柔軟なスタイルまたはデータ項目のコレクションを有効にする機能が組み込まれました。 並べ替えビュー、フィルター ビュー、およびグループ ビューは、データの上に生成できます。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] のデータ バインディング機能には、本質的にデータ バインディングをサポートする広範なプロパティ、データの柔軟な [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 表現、[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] からのビジネス ロジックの明確な分離など、従来のモデルより優れた長所がいくつかあります  
  
 このトピックでは、まず、 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]データバインディングの基本概念について説明し<xref:System.Windows.Data.Binding>た後、クラスの使用方法とデータバインディングのその他の機能について説明します。  

<a name="what_is_data_binding"></a>   
## <a name="what-is-data-binding"></a>データ バインディングとは  
 データ バインディングとは、アプリケーション [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] とビジネス ロジックの間の接続を確立する処理です。 バインドが適切に設定され、データから適切な通知が提供される場合、データの値が変更されると、そのデータにバインドされている要素に変更が自動的に反映されます。 データ バインディングには、要素内のデータの外部表現が変更された場合、基になるデータを自動的に更新して変更を反映できるという意味もあります。 たとえば、ユーザーが<xref:System.Windows.Controls.TextBox>要素内の値を編集した場合、基になるデータ値が自動的に更新され、その変更が反映されます。  
  
 データ バインディングの一般的な使用は、サーバーまたはローカルの構成データをフォームまたはその他の [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] コントロールに配置することです。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] では、この概念は幅広いプロパティのバインドからさまざまなデータ ソースまで拡張されます。 で[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]は、要素の依存関係プロパティを CLR オブジェクト (ADO.NET オブジェクトや、web サービスや web プロパティに関連付けられた[!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)]オブジェクトなど) およびデータにバインドできます。  
  
 データ バインディングの例については、[データ バインディング デモ](https://go.microsoft.com/fwlink/?LinkID=163703)の次のアプリケーション [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] を参照してください。  
  
 ![データバインディングのサンプルのスクリーンショット](./media/databinding-databindingdemo.png "DataBinding_DataBindingDemo")  
  
 上記は、オークション品目の一覧を表示するアプリケーションの [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] です。 このアプリケーションは、データ バインディングの次の機能を示しています。  
  
- の<xref:System.Windows.Controls.ListBox>コンテンツは、 *AuctionItem*オブジェクトのコレクションにバインドされます。 *AuctionItem* オブジェクトには、*Description*、*StartPrice*、*StartDate*、*Category*、*SpecialFeatures* などのプロパティがあります。  
  
- に<xref:System.Windows.Controls.ListBox>表示されるデータ (*AuctionItem*オブジェクト) は、項目ごとに説明と現在の価格が表示されるように、テンプレート化されています。 これは、を<xref:System.Windows.DataTemplate>使用して行います。 さらに、各項目の外観は、表示されている *AuctionItem* の *SpecialFeatures* の値に依存します。 *AuctionItem* の *SpecialFeatures* の値が *Color* の場合、その項目には青の枠線が付きます。 値が *Highlight* の場合、その項目にはオレンジの枠線と星が付きます。 「[データ テンプレート](#data_templating)」セクションでは、データ テンプレートに関する情報を提供します。  
  
- ユーザーは、 <xref:System.Windows.Controls.CheckBox>提供されたを使用して、データのグループ化、フィルター処理、または並べ替えを行うことができます。 上の図では、[カテゴリでグループ化] と [カテゴリと日付<xref:System.Windows.Controls.CheckBox>で並べ替え] が選択されています。 データが製品のカテゴリに基づいてグループ化され、カテゴリ名がアルファベット順になっていることが分かります。 図では分かりにくいですが、項目は各カテゴリ内での開始日でも並べ替えられています。 これは*コレクション ビュー*を使用して行えます。 コレクション ビューについては、「[コレクションにバインドする](#binding_to_collections)」セクションで説明します。  
  
- ユーザーが項目<xref:System.Windows.Controls.ContentControl>を選択すると、選択した項目の詳細が表示されます。 これは*マスター詳細シナリオ*と呼ばれます。 この種類のバインドのシナリオに関する情報は、「[マスター詳細シナリオ](#master_detail_scenario)」セクションにあります。  
  
- *StartDate*プロパティの型はです。 <xref:System.DateTime>これは、ミリ秒の時刻を含む日付を返します。 このアプリケーションでは、より短い日付文字列を表示するため、カスタムのコンバーターが使用されています。 コンバーターに関する情報は、「[データ変換](#data_conversion)」セクションにあります。  
  
 ユーザーが [*Add Product (製品の追加)* ] ボタンをクリックすると、次のフォームが表示されます。  
  
 ![製品の追加一覧のページ](./media/databinding-demo-addproductlisting.png "DataBinding_Demo_AddProductListing")  
  
 ユーザーは、フォーム内のフィールドを編集して、簡単なプレビューとより詳細なプレビュー ペインを使用して製品の一覧をプレビューしてから [*送信*] をクリックして新しい製品の一覧を追加することができます。 既存のグループ化、フィルター処理および並べ替えの機能は、新しいエントリに適用されます。 この特定のケースでは、上のイメージで入力した項目が *Computer* カテゴリ内の 2 番目の項目として表示されます。  
  
 このイメージには、*開始日* <xref:System.Windows.Controls.TextBox>に指定された検証ロジックが示されていません。 ユーザーが無効な日付 (無効な書式設定または過去の日付) を入力した場合、ユーザー <xref:System.Windows.Controls.ToolTip>には、との<xref:System.Windows.Controls.TextBox>横に赤い感嘆符が表示されます。 検証ロジックの作成方法については、「[データの検証](#data_validation)」セクションで説明します。  
  
 上記で説明したデータ バインディングのさまざまな機能の説明に入る前に、最初に [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] データ バインディングの理解に欠かせない基本概念について次のセクションで説明します。  
  
## <a name="basic-data-binding-concepts"></a>基本的なデータ バインディングの概念  
  
 バインドする要素およびデータ ソースの性質に関係なく、各バインドは常に次の図で示したモデルに従います。  
  
 ![基本的なデータバインディングモデルを示す図。](./media/data-binding-overview/basic-data-binding-diagram.png)  
  
 上の図に示したように、データ バインディングは本質的に、バインディング ターゲットとバインディング ソース間の橋渡しです。 図には、次の基本的な [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] データ バインディングの概念が示されています。  
  
- 通常、各バインディングには、バインディング ターゲット オブジェクト、ターゲット プロパティ、バインディング ソース、および使用するバインディング ソース内の値へのパスの 4 つのコンポーネントがあります。 たとえば<xref:System.Windows.Controls.TextBox> 、のコンテンツを*Employee*オブジェクトの<xref:System.Windows.Controls.TextBox> *Name*プロパティにバインドする場合、ターゲットオブジェクトはで、ターゲットプロパティは<xref:System.Windows.Controls.TextBox.Text%2A>プロパティ、使用する値は*Name*、およびのようになります。ソースオブジェクトは*Employee*オブジェクトです。  
  
- ターゲット プロパティは、依存関係プロパティである必要があります。 ほとんど<xref:System.Windows.UIElement>のプロパティは依存関係プロパティであり、ほとんどの依存関係プロパティ (読み取り専用のプロパティを除く) は、既定でデータバインディングをサポートします。 (型<xref:System.Windows.DependencyObject>だけが依存関係プロパティを定義<xref:System.Windows.UIElement>でき、すべて<xref:System.Windows.DependencyObject>のはから派生します)。  
  
- 図には指定されていませんが、バインディングソースオブジェクトはカスタム CLR オブジェクトに限定されないことに注意してください。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]データバインディングは、CLR オブジェクトと[!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)]の形式のデータをサポートします。 いくつかの例を示す<xref:System.Windows.UIElement>ために、バインディングソースは、、すべてのリストオブジェクト、ADO.NET data または Web サービスに関連付けられている CLR オブジェクト、または[!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)]データを含む XmlNode にすることができます。 詳しくは、「[バインディング ソースの概要](binding-sources-overview.md)」をご覧ください。  
  
 他の SDK のトピックを参照するときは、バインドを確立するときにバインディングターゲットをバインディングソース*に*バインドすることを忘れないように注意する必要があります。 たとえば[!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] 、データバインディングを<xref:System.Windows.Controls.ListBox>使用しての基になるデータをいくつか表示する場合は<xref:System.Windows.Controls.ListBox> 、を[!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)]データにバインドします。  
  
 バインディングを確立するには、 <xref:System.Windows.Data.Binding>オブジェクトを使用します。 このトピックの残りの部分では、に関連するさまざまな概念と、 <xref:System.Windows.Data.Binding>オブジェクトのプロパティと使用方法について説明します。  
  
<a name="direction_of_data_flow"></a>   
### <a name="direction-of-the-data-flow"></a>データ フローの方向  
 前述のように、上の図の矢印で示されているように、バインディングのデータフローは、バインディングターゲットからバインディングソースに移動できます (たとえば、ユーザーがの<xref:System.Windows.Controls.TextBox>値を編集したときにソース値が変更された場合など)。バインディングソースが適切な通知を提供する<xref:System.Windows.Controls.TextBox>場合、バインディングターゲットに (たとえば、コンテンツがバインディングソースの変更で更新されます)。  
  
 アプリケーションでユーザーがデータを変更してそれをソース オブジェクトに反映できるようにすることができます。 または、ユーザーがソース データを更新できないようにすることもできます。 これを制御するには、 <xref:System.Windows.Data.Binding.Mode%2A> <xref:System.Windows.Data.Binding>オブジェクトのプロパティを設定します。 次の図は、さまざまなデータ フローの種類を示しています。  
  
 ![データ バインディングのデータ フロー](./media/databinding-dataflow.png "DataBinding_DataFlow")  
  
- <xref:System.Windows.Data.BindingMode.OneWay>バインドによって source プロパティが変更され、ターゲットプロパティが自動的に更新されますが、ターゲットプロパティへの変更はソースプロパティに反映されません。 この型のバインディングは、バインドされているコントロールが暗黙的な読み取り専用の場合に適しています。 たとえば、株価情報などのソースにバインドしたり、またはターゲット プロパティに、データ バインドされたテーブルの背景色などのように、変更用コントロール インターフェイスがない可能性もあります。 ターゲット プロパティの変更を監視する必要がない場合は、<xref:System.Windows.Data.BindingMode.OneWay> バインディング モードを使うことにより、<xref:System.Windows.Data.BindingMode.TwoWay> バインディング モードのオーバーヘッドを回避できます。  
  
- <xref:System.Windows.Data.BindingMode.TwoWay>バインドによって、ソースプロパティまたはターゲットプロパティのいずれかが変更され、もう一方が自動的に更新されます。 この型のバインディングは、編集可能なフォームや完全対話型の [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] シナリオに適しています。 ほとんどのプロパティは<xref:System.Windows.Data.BindingMode.OneWay>バインドに既定で設定されていますが、一部の依存関係プロパティ<xref:System.Windows.Controls.TextBox.Text%2A> (通常<xref:System.Windows.Controls.TextBox>はのプロパティや<xref:System.Windows.Controls.CheckBox>のプロパティなど、ユーザーが編集可能なコントロールのプロパティ) が既定値に<xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> 設定されます。<xref:System.Windows.Data.BindingMode.TwoWay>バインド。 依存関係プロパティが既定で一方向と双方向のどちらでバインドされるかをプログラムで判断する 1 つの方法として、<xref:System.Windows.DependencyProperty.GetMetadata%2A> を使用してそのプロパティのプロパティ メタデータを取得してから、<xref:System.Windows.FrameworkPropertyMetadata.BindsTwoWayByDefault%2A> プロパティのブール値を確認することがきます。  
  
- <xref:System.Windows.Data.BindingMode.OneWayToSource>はバインドの<xref:System.Windows.Data.BindingMode.OneWay>逆です。ターゲットプロパティが変更されたときに、source プロパティを更新します。 1 つのサンプル シナリオは、[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] からのソース値のみを再評価する必要があるかどうかです。  
  
- 図に示されてい<xref:System.Windows.Data.BindingMode.OneTime>ないのはバインドです。これにより、source プロパティによってターゲットプロパティが初期化されますが、その後の変更は反映されません。 これは、データ コンテキストが変更されるか、データ コンテキスト内のオブジェクトが変更された場合に、その変更がターゲット プロパティに反映されないことを意味します。 この型のバインディングは、現在の状態のスナップショットが用途に合っている場合や、データが完全に静的である場合に適しています。 また、ソース プロパティの値を使用してターゲット プロパティを初期化するときにデータ コンテキストが事前にわからない場合にも、この型のバインディングは便利です。 基本的に、この型のバインディングは、ソース値が変わらない場合にパフォーマンスを向上させる <xref:System.Windows.Data.BindingMode.OneWay> バインディングを簡易化したものです。  
  
 ソースの変更 (および<xref:System.Windows.Data.BindingMode.OneWay> <xref:System.Windows.Data.BindingMode.TwoWay>バインドに適用可能) を検出するには、ソースがなど<xref:System.ComponentModel.INotifyPropertyChanged>の適切なプロパティ変更通知機構を実装する必要があります。 <xref:System.ComponentModel.INotifyPropertyChanged>実装の例については、「[プロパティ変更通知の実装](how-to-implement-property-change-notification.md)」を参照してください。  
  
 プロパティ<xref:System.Windows.Data.Binding.Mode%2A>ページには、バインドモードに関する詳細情報と、バインディングの方向を指定する方法の例が表示されます。  
  
<a name="what_triggers_source_updates"></a>   
### <a name="what-triggers-source-updates"></a>ソース更新のトリガー  
 ターゲットプロパティの<xref:System.Windows.Data.BindingMode.TwoWay>変更<xref:System.Windows.Data.BindingMode.OneWayToSource>をリッスンし、ソースに反映させるバインディング。 これは、ソースの更新と呼ばれます。 たとえば、TextBox のテキストを編集して、基になるソース値を変更できます。 最後のセクションで説明したように、データフローの方向はバインディングの<xref:System.Windows.Data.Binding.Mode%2A>プロパティの値によって決まります。  
  
 ただし、ソース値が更新されるのは、テキストの編集中またはテキストの編集後にマウス ポインターを TextBox から離した後でしょうか。 バインディング<xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A>のプロパティは、ソースの更新をトリガーする対象を決定します。 次の図の右矢印の点は、 <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A>プロパティの役割を示しています。  
  
 ![アップデート Ourcetrigger プロパティのロールを示す図。](./media/data-binding-overview/data-binding-updatesource-trigger.png)  
  
 <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A>の値が<xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>の場合、指す値の右矢印<xref:System.Windows.Data.BindingMode.TwoWay>または<xref:System.Windows.Data.BindingMode.OneWayToSource>バインドはターゲット プロパティの変更と、すぐに更新を取得します。 ただし、 <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A>値が<xref:System.Windows.Data.UpdateSourceTrigger.LostFocus>の場合は、ターゲットプロパティがフォーカスを失ったときに、その値のみが新しい値で更新されます。  
  
 <xref:System.Windows.Data.Binding.Mode%2A>プロパティと同様に、別の依存関係プロパティが別の既定値を持つ<xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A>値。 ほとんどの依存関係プロパティの既定値は <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged> です。ただし、<xref:System.Windows.Controls.TextBox.Text%2A> プロパティの既定値は <xref:System.Windows.Data.UpdateSourceTrigger.LostFocus> です。 これは、ターゲットプロパティが変更されるたびにソースの更新が発生する<xref:System.Windows.Controls.CheckBox>ことを意味します。これは、es や他の簡単なコントロールには適しています。 しかし、テキスト フィールドについては、キーストロークのたびに更新すると、パフォーマンスが低下する可能性があり、また、ユーザーが新しい値をコミットする前にいつものようにバックスペースでタイプ ミスを消す機会がなくなります。 このため、 <xref:System.Windows.Controls.TextBox.Text%2A>プロパティの既定<xref:System.Windows.Data.UpdateSourceTrigger.LostFocus>値はではなく<xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>になります。  
  
 依存関係プロパティの既定の<xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A>値を検索する方法に関する情報については、<xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A>プロパティページ参照してください。  
  
 次の表に、 <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> <xref:System.Windows.Controls.TextBox>を例として使用した各値のシナリオ例を示します。  
  
|UpdateSourceTrigger の値|ソース値が更新されるとき|TextBox のサンプル シナリオ|  
|-------------------------------|----------------------------------------|----------------------------------|  
|LostFocus (の<xref:System.Windows.Controls.TextBox.Text%2A?displayProperty=nameWithType>既定値)|TextBox コントロールがフォーカスを失ったとき|検証ロジックに関連付けられている。「データ検証」を参照してください。<xref:System.Windows.Controls.TextBox>|  
|PropertyChanged|を入力すると、<xref:System.Windows.Controls.TextBox>|<xref:System.Windows.Controls.TextBox>チャットルームウィンドウ内のコントロール|  
|Explicit|アプリケーションがを呼び出すとき<xref:System.Windows.Data.BindingExpression.UpdateSource%2A>|<xref:System.Windows.Controls.TextBox>編集可能なフォーム内のコントロール (ユーザーが [送信] ボタンをクリックしたときにのみソース値が更新されます)|  
  
 例については、「[TextBox テキストでソースを更新するタイミングを制御する](how-to-control-when-the-textbox-text-updates-the-source.md)」を参照してください。  
  
<a name="creating_a_binding"></a>   
## <a name="creating-a-binding"></a>バインディングの作成  
  
 前のセクションで説明したいくつかの概念を要約するには、 <xref:System.Windows.Data.Binding>オブジェクトを使用してバインディングを確立します。各バインディングには、通常、バインディングターゲット、ターゲットプロパティ、バインディングソース、および使用するソース値へのパスの4つのコンポーネントがあります。 このセクションでは、バインドの設定方法について説明します。  
  
 次の例について考えます。この例では、バインディング ソース オブジェクトは、*SDKSample* 名前空間で定義されている *MyData* という名前のクラスです。 デモンストレーション目的のため、*MyData* クラスには、値が "Red" に設定された *ColorName* という名前の文字列プロパティがあります。 したがって、この例では、背景が赤のボタンが生成されます。  
  
 [!code-xaml[BindNonTextProperty#1](~/samples/snippets/csharp/VS_Snippets_Wpf/BindNonTextProperty/CS/Page1.xaml#1)]  
  
 バインディング宣言の構文の詳細およびコード内でバインディングを設定する方法の例については、「[バインディング宣言の概要](binding-declarations-overview.md)」を参照してください。  
  
 この例を基本的な図に適用すると、結果として得られる図は、次のようになります。 これは、 <xref:System.Windows.Data.BindingMode.OneWay> Background プロパティが既定でバインド<xref:System.Windows.Data.BindingMode.OneWay>をサポートしているためです。  
  
 ![データバインディングの背景プロパティを示す図。](./media/data-binding-overview/data-binding-button-background-example.png)  
  
 *Colorname*プロパティが string 型であるのに<xref:System.Windows.Controls.Control.Background%2A> 、プロパティの型<xref:System.Windows.Media.Brush>がである場合でも、これが機能するのはなぜでしょうか。 これは作業中の既定の型変換であり、「[データ変換](#data_conversion)」セクションで説明されています。  
  
<a name="specifying_the_binding_source"></a>   
### <a name="specifying-the-binding-source"></a>バインディング ソースの指定  
 前の例では、 <xref:System.Windows.FrameworkElement.DataContext%2A> <xref:System.Windows.Controls.DockPanel>要素のプロパティを設定することによって、バインディングソースが指定されていることに注意してください。 次<xref:System.Windows.Controls.Button>に、は<xref:System.Windows.FrameworkElement.DataContext%2A> 、その親<xref:System.Windows.Controls.DockPanel>要素であるから値を継承します。 繰り返しますが、バインディング ソース オブジェクトは、バインディングの 4 つの必須コンポーネントの 1 つです。 したがって、バインディング ソース オブジェクトが指定されていないと、バインディングは機能しません。  
  
 バインディング ソース オブジェクトを指定するには複数の方法があります。 親要素でプロパティを使用すると、複数のプロパティを同じソースにバインドする場合に便利です。 <xref:System.Windows.FrameworkElement.DataContext%2A> ただし、個々のバインディング宣言でバインディング ソースを指定する方が適切な場合もあります。 前の例では、 <xref:System.Windows.FrameworkElement.DataContext%2A>プロパティを使用する代わりに、次の例に示すように、ボタンのバインディング宣言で<xref:System.Windows.Data.Binding.Source%2A>プロパティを直接設定することによって、バインディングソースを指定することができます。  
  
 [!code-xaml[BindNonTextProperty#BackgroundBindingCompact](~/samples/snippets/csharp/VS_Snippets_Wpf/BindNonTextProperty/CS/Page2.xaml#backgroundbindingcompact)]  
  
 要素のプロパティを<xref:System.Windows.FrameworkElement.DataContext%2A>直接設定し、先祖 (最初の<xref:System.Windows.FrameworkElement.DataContext%2A>例のボタンなど) の値を継承し、次の<xref:System.Windows.Data.Binding.Source%2A>プロパティを設定してバインディングソースを明示的に指定する以外に、<xref:System.Windows.Data.Binding>(最後の例のボタンなど) で<xref:System.Windows.Data.Binding.ElementName%2A> <xref:System.Windows.Data.Binding.RelativeSource%2A>は、プロパティまたはプロパティを使用してバインディングソースを指定することもできます。 <xref:System.Windows.Data.Binding.ElementName%2A>プロパティは、スライダーを使用してボタンの幅を調整する場合など、アプリケーションの他の要素にバインドする場合に便利です。 プロパティは、 <xref:System.Windows.Controls.ControlTemplate> また<xref:System.Windows.Style>はでバインディングが指定されている場合に便利です。 <xref:System.Windows.Data.Binding.RelativeSource%2A> 詳しくは、「[バインディング ソースを指定する](how-to-specify-the-binding-source.md)」をご覧ください。  
  
<a name="specifying_the_path_to_the_value"></a>   
### <a name="specifying-the-path-to-the-value"></a>値にパスを指定する  
 バインディングソースがオブジェクトの場合は、 <xref:System.Windows.Data.Binding.Path%2A>プロパティを使用して、バインドに使用する値を指定します。 データに[!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)]バインドする場合は、 <xref:System.Windows.Data.Binding.XPath%2A>プロパティを使用して値を指定します。 場合によっては、データがの<xref:System.Windows.Data.Binding.Path%2A> [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)]場合でも、プロパティを使用することができます。 たとえば、(XPath クエリ) の結果として返される XmlNode の Name プロパティにアクセスする場合は、<xref:System.Windows.Data.Binding.XPath%2A>プロパティのほか<xref:System.Windows.Data.Binding.Path%2A>プロパティを使用する必要があります。  
  
 構文の詳細と例について<xref:System.Windows.Data.Binding.Path%2A>は<xref:System.Windows.Data.Binding.XPath%2A> 、「」および「プロパティページ」を参照してください。  
  
 使用する値は、 <xref:System.Windows.Data.Binding.Path%2A>バインドに必要な4つのコンポーネントの1つであるという点に注目しましたが、オブジェクト全体にバインドするシナリオでは、使用する値はバインディングソースオブジェクトと同じになります。 そのような<xref:System.Windows.Data.Binding.Path%2A>場合は、を指定しないようにすることができます。 次に例を示します。  
  
 [!code-xaml[MasterDetail#EmptyBinding](~/samples/snippets/csharp/VS_Snippets_Wpf/MasterDetail/CSharp/Page1.xaml#emptybinding)]  
  
 上記の例では、空のバインド構文 {Binding} を使用しています。 この場合、は<xref:System.Windows.Controls.ListBox>親の system.windows.controls.dockpanel> 要素から DataContext を継承します (この例では示されていません)。 パスが指定されていない場合、既定では、オブジェクト全体にバインドします。 つまり、この例では、オブジェクト全体に<xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>プロパティをバインドしているため、パスは残されています。 (詳しい説明については、「[コレクションにバインドする](#binding_to_collections)」セクションを参照してください)。  
  
 コレクションにバインドする以外に、オブジェクトの 1 つのプロパティだけではなくオブジェクト全体にバインドするときにもこのシナリオは役立ちます。 たとえば、ソース オブジェクトが文字列型で、文字列そのものにバインドしたい場合などです。 もう 1 つの一般的なシナリオは、要素をいくつかのプロパティを持つオブジェクトにバインドする場合です。  
  
 データがバインドされているターゲット プロパティにとって意味のあるものになるように、カスタム ロジックの適用が必要になる場合があることに注意してください。 (既定の型変換が存在しない場合) カスタム ロジックはカスタムのコンバーターの形式になる場合があります。 コンバーターの詳細については、「[データ変換](#data_conversion)」を参照してください。  
  
<a name="binding_bindingexpression"></a>   
### <a name="binding-and-bindingexpression"></a>Binding と BindingExpression  
 データバインディングの他の機能や使用方法に入る前に、 <xref:System.Windows.Data.BindingExpression>クラスを導入すると便利です。 前のセクション<xref:System.Windows.Data.Binding>で説明したように、クラスはバインドの宣言の最上位クラスです。クラスに<xref:System.Windows.Data.Binding>は、バインディングの特性を指定するためのプロパティが多数用意されています。 関連するクラス<xref:System.Windows.Data.BindingExpression>は、ソースとターゲットの間の接続を維持する、基になるオブジェクトです。 バインドには、複数のバインド式の間で共有できるすべての情報が含まれています。 は、共有できず、 <xref:System.Windows.Data.Binding>のすべてのインスタンス情報を含むインスタンス式です。 <xref:System.Windows.Data.BindingExpression>  
  
 たとえば、次のようにします。ここで、 *mydataobject*は、 *mydata*クラスのインスタンス、 <xref:System.Windows.Data.Binding> *myBinding*はソースオブジェクト、 *MyData*クラスは、という*文字列プロパティを含む定義済みのクラスです。MyDataProperty*。 この例では、の<xref:System.Windows.Controls.TextBlock>インスタンスである*mytext*のテキストコンテンツを*MyDataProperty*にバインドします。  
  
 [!code-csharp[CodeOnlyBinding#1](~/samples/snippets/csharp/VS_Snippets_Wpf/CodeOnlyBinding/CSharp/binding.cs#1)]
 [!code-vb[CodeOnlyBinding#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CodeOnlyBinding/VisualBasic/App.vb#1)]  
  
 同じ *myBinding* オブジェクトを使用して、他のバインディングを作成できます。 たとえば、*myBinding* オブジェクトを使用して、チェック ボックスのテキストの内容を *MyDataProperty* にバインドすることができます。 このシナリオでは、 <xref:System.Windows.Data.BindingExpression> *myBinding*オブジェクトを共有するインスタンスが2つあります。  
  
 オブジェクト<xref:System.Windows.Data.BindingExpression>を取得するには、データバインドオブジェクトで<xref:System.Windows.Data.BindingOperations.GetBindingExpression%2A>を呼び出すの戻り値を使用します。 次のトピックでは、 <xref:System.Windows.Data.BindingExpression>クラスの使用方法について説明します。  
  
- [バインドされているターゲット プロパティからのバインディング オブジェクトの取得](how-to-get-the-binding-object-from-a-bound-target-property.md)  
  
- [TextBox テキストでソースを更新するタイミングを制御する](how-to-control-when-the-textbox-text-updates-the-source.md)  
  
<a name="data_conversion"></a>   
## <a name="data-conversion"></a>データ変換  
 前の例では、 <xref:System.Windows.Controls.Control.Background%2A>プロパティが "red" という値を持つ文字列プロパティにバインドされているため、ボタンは赤になります。 これは、文字列値<xref:System.Windows.Media.Brush> <xref:System.Windows.Media.Brush>をに変換する型が型に存在するために機能します。  
  
 この情報を「[バインディングの作成](#creating_a_binding)」セクションの図に追加すると、図は次のようになります。  
  
 ![データバインディングの既定のプロパティを示す図。](./media/data-binding-overview/data-binding-button-default-conversion.png)  
  
 ただし、文字列型のプロパティを使用せずに、バインドソースオブジェクトの*Color*プロパティが型<xref:System.Windows.Media.Color>である場合はどうでしょうか。 この場合、バインドを機能させるには、まず*Color*プロパティの値を<xref:System.Windows.Controls.Control.Background%2A>プロパティが受け入れるものに変換する必要があります。 次の例に示すように、 <xref:System.Windows.Data.IValueConverter>インターフェイスを実装してカスタムコンバーターを作成する必要があります。  
  
 [!code-csharp[ColorPicker_snip#16](~/samples/snippets/csharp/VS_Snippets_Wpf/ColorPicker_snip/CSharp/ColorPickerLib/ColorPicker.cs#16)]
 [!code-vb[ColorPicker_snip#16](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ColorPicker_snip/visualbasic/colorpickerlib/colorpicker.vb#16)]  
  
 詳細<xref:System.Windows.Data.IValueConverter>については、リファレンスページを参照してください。  
  
 これで既定の変換の代わりにカスタムのコンバーターが使用されるようになったので、図はこのようになります。  
  
 ![データバインディングカスタムコンバーターを示す図。](./media/data-binding-overview/data-binding-converter-color-example.png)  
  
 繰り返しますが、バインドされている型に存在する型コンバーターにより、既定の変換が使用できます。 この動作は、ターゲットで利用可能な型コンバーターによって異なります。 独自のコンバーターを作成して、確認してみてください。  
  
 データ コンバーターを実装するのが合理的な典型的なシナリオをいくつか次に示します。  
  
- カルチャに応じてデータを異なる方法で表示する必要がある場合。 たとえば、特定のカルチャで使用されている値または標準に基づいて、通貨コンバーターまたはカレンダー日付/時刻のコンバーターを実装することができます。  
  
- 使用されているデータが必ずしもプロパティのテキスト値を変更することを意図しているわけではく、イメージのソースや表示テキストの色やスタイルなど、他のいくつかの値を変更することを意図している場合。 この場合、コンバーターを使用して、適切と思われないプロパティのバインディング (テキスト フィールドをテーブルのセルの Background プロパティにバインドするなど) を変換することができます。  
  
- 複数のコントロールまたはコントロールの複数のプロパティが同じデータにバインドされている場合。 この場合、プライマリ バインドがテキストだけを表示する可能性があるのに対し、他のバインドは特定の表示に関する問題を処理しますが、同じバインドをソース情報として使用します。  
  
- ここまでは説明<xref:System.Windows.Data.MultiBinding>しませんでした。ターゲットプロパティにバインドのコレクションが含まれています。 の<xref:System.Windows.Data.MultiBinding>場合は、カスタム<xref:System.Windows.Data.IMultiValueConverter>を使用して、バインディングの値から最終的な値を生成します。 たとえば、色は赤、青、および緑の値から計算できますが、これらは同じまたは異なるバインディング ソース オブジェクトからの値にすることができます。 例と<xref:System.Windows.Data.MultiBinding>情報については、クラスのページを参照してください。  
  
<a name="binding_to_collections"></a>   
## <a name="binding-to-collections"></a>コレクションにバインドする  
  
 バインド ソース オブジェクトは、プロパティにデータが含まれている 1 つのオブジェクト、または多くの場合、グループ化されるポリモーフィック型オブジェクト (データベースへのクエリの結果など) のデータ コレクションとして扱うことができます。 ここまでは、1 つのオブジェクトへのバインドだけを説明してきましたが、データ コレクションへのバインドは一般的なシナリオです。 たとえば、一般的なシナリオでは、、、 <xref:System.Windows.Controls.ItemsControl>などのを<xref:System.Windows.Controls.ListBox>使用<xref:System.Windows.Controls.ListView> <xref:System.Windows.Controls.TreeView>してデータコレクションを表示します。たとえば、「[データバインディングとは](#what_is_data_binding)」セクションで示したアプリケーションのようにします。  
  
 幸い、基本的な図を引き続き使用できます。 をコレクション<xref:System.Windows.Controls.ItemsControl>にバインドしている場合、図は次のようになります。  
  
 ![データバインディングの ItemsControl オブジェクトを示す図。](./media/data-binding-overview/data-binding-itemscontrol.png)  
  
 この図に示すように、をコレクション<xref:System.Windows.Controls.ItemsControl> <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>オブジェクトにバインドするには、プロパティを使用します。 <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>プロパティは、 <xref:System.Windows.Controls.ItemsControl>のコンテンツと考えることができます。 バインディングは<xref:System.Windows.Data.BindingMode.OneWay> 、プロパティが<xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>既定でバインディングを<xref:System.Windows.Data.BindingMode.OneWay>サポートしているためであることに注意してください。  
  
<a name="how_to_implement_collections"></a>   
### <a name="how-to-implement-collections"></a>コレクションを実装する方法  
 <xref:System.Collections.IEnumerable>インターフェイスを実装する任意のコレクションを列挙できます。 ただし、コレクションの挿入または削除によってが[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]自動的に更新されるように動的バインドを設定するには、コレクションで<xref:System.Collections.Specialized.INotifyCollectionChanged>インターフェイスを実装する必要があります。 このインターフェイスは、基になるコレクションが変更されたときに発生させるイベントを公開します。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]クラスを提供します。これは、インターフェイスを<xref:System.Collections.Specialized.INotifyCollectionChanged>公開するデータコレクションの組み込みの実装です。 <xref:System.Collections.ObjectModel.ObservableCollection%601> ソースオブジェクトからターゲットへのデータ値の転送を完全にサポートするには、バインド可能なプロパティをサポートするコレクション内<xref:System.ComponentModel.INotifyPropertyChanged>の各オブジェクトもインターフェイスを実装する必要があることに注意してください。 詳しくは、「[バインディング ソースの概要](binding-sources-overview.md)」をご覧ください。  
  
 独自のコレクションを実装する前に<xref:System.Collections.ObjectModel.ObservableCollection%601> 、または既存のコレクションクラス (、、 <xref:System.Collections.Generic.List%601>など<xref:System.Collections.ObjectModel.Collection%601>) <xref:System.ComponentModel.BindingList%601>のいずれかを使用することを検討してください。 高度なシナリオがあり、独自のコレクションを実装する場合は、を<xref:System.Collections.IList>使用することを検討してください。これにより、インデックスによって個別にアクセスできるオブジェクトの非ジェネリックコレクションが提供されるため、最適なパフォーマンスが得られます。  
  
<a name="collection_views"></a>   
### <a name="collection-views"></a>コレクション ビュー  
 <xref:System.Windows.Controls.ItemsControl>をデータコレクションにバインドしたら、データの並べ替え、フィルター処理、またはグループ化を行うことができます。 これを行うには、 <xref:System.ComponentModel.ICollectionView>インターフェイスを実装するクラスであるコレクションビューを使用します。  

#### <a name="what-are-collection-views"></a>コレクション ビューとは  
 コレクション ビューは、基になるソース コレクション自体を変更することなく、並べ替え、フィルター、およびグループのクエリに基づくソース コレクションを移動および表示を可能にするバインディング ソース コレクションの上にある層です。 コレクション ビューには、コレクション内の現在の項目へのポインターも保持されます。 ソースコレクションが<xref:System.Collections.Specialized.INotifyCollectionChanged>インターフェイスを実装し<xref:System.Collections.Specialized.INotifyCollectionChanged.CollectionChanged>ている場合は、イベントによって発生した変更がビューに反映されます。  
  
 ビューは基になるソース コレクションを変更しないため、各ソース コレクションは関連付けられた複数のビューを持つことができます。 たとえば、*Task* オブジェクトのコレクションを持つことができます。 ビューを使用すると、同じデータをさまざまな方法で表示できます。 たとえば、ページの左側に優先度で並べ替えられたタスクを表示し、右側に区分でグループ化されたタスクを表示できます。  
  
<a name="how_to_create_a_view"></a>   
#### <a name="how-to-create-a-view"></a>ビューの作成方法  
 ビューを作成して使用する方法の 1 つは、ビュー オブジェクトを直接インスタンス化して、それをバインディング ソースとして使用することです。 たとえば、「[データ バインディングとは](#what_is_data_binding)」のセクションで示されている[データ バインディング デモ](https://go.microsoft.com/fwlink/?LinkID=163703)を考えてみましょう。 アプリケーションは、がデータコレクションで<xref:System.Windows.Controls.ListBox>はなくデータコレクションに対してビューにバインドするように実装されます。 次の例は、[データ バインディング デモ](https://go.microsoft.com/fwlink/?LinkID=163703)のアプリケーションから抽出されたものです。 クラスは、から[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] <xref:System.Windows.Data.CollectionView>継承されるクラスのプロキシです。 <xref:System.Windows.Data.CollectionViewSource> この特定の例では<xref:System.Windows.Data.CollectionViewSource.Source%2A> 、ビューのが、現在のアプリケーションオブジェクトの*AuctionItems* collection <xref:System.Collections.ObjectModel.ObservableCollection%601>(型) にバインドされています。  
  
 [!code-xaml[DataBindingLab#WindowResources1](~/samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/MainWindow.xaml#windowresources1)]  
[!code-xaml[DataBindingLab#CollectionViewSource](~/samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/MainWindow.xaml#collectionviewsource)]  
[!code-xaml[DataBindingLab#WindowResources2](~/samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/MainWindow.xaml#windowresources2)]  
  
 リソース*listingDataView*は、次の<xref:System.Windows.Controls.ListBox>ように、アプリケーションの要素のバインディングソースとして機能します。  
  
 [!code-xaml[DataBindingLab#Master1](~/samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/MainWindow.xaml#master1)]  
[!code-xaml[DataBindingLab#Master2](~/samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/MainWindow.xaml#master2)]  
  
 同じコレクションに対して別のビューを作成するには<xref:System.Windows.Data.CollectionViewSource> 、別のインスタンスを作成`x:Key`して別の名前を指定します。  
  
 次の表に、既定のコレクションビューとして作成されるビューデータ<xref:System.Windows.Data.CollectionViewSource>型、またはソースコレクション型に基づいて作成されるビューデータ型を示します。  
  
|ソース コレクションの型|コレクション ビューの型|メモ|  
|----------------------------|--------------------------|-----------|  
|<xref:System.Collections.IEnumerable>|に基づく内部型<xref:System.Windows.Data.CollectionView>|項目のグループ化は不可|  
|<xref:System.Collections.IList>|<xref:System.Windows.Data.ListCollectionView>|最も高速|  
|<xref:System.ComponentModel.IBindingList>|<xref:System.Windows.Data.BindingListCollectionView>||  
  
##### <a name="using-a-default-view"></a>既定のビューの使用  
 コレクション ビューを作成して使用する 1 つの方法は、バインディング ソースとしてコレクション ビューを指定することです。 WPF では、バインディング ソースとして使用されるすべてのコレクションに対して既定のコレクション ビューも作成されます。 コレクションに直接バインドすると、WPF はその既定のビューにバインドします。 この既定のビューは、同じコレクションにバインドされているすべてのバインディングで共有されるため、1 つのバインド コントロールまたはコードによる既定のビューへの変更 (後述する並べ替えや現在の項目ポインターへの変更など) は、同じコレクションにバインドされている他のすべてのバインディングに反映されます。  
  
 既定のビューを取得するには、 <xref:System.Windows.Data.CollectionViewSource.GetDefaultView%2A>メソッドを使用します。 例については、「[データ コレクションの既定のビューを取得する](how-to-get-the-default-view-of-a-data-collection.md)」を参照してください。  
  
##### <a name="collection-views-with-adonet-datatables"></a>コレクション ビューと ADO.NET DataTable  
 パフォーマンスを向上させるために、 <xref:System.Data.DataTable> ADO.NET <xref:System.Data.DataView>またはオブジェクトのコレクションビューは<xref:System.Data.DataView>、の並べ替えとフィルター処理を委任します。 これにより、並べ替えとフィルター処理がデータ ソースのすべてのコレクション ビューで共有されます。 各コレクションビューで個別に並べ替えとフィルター処理を有効にするには、各<xref:System.Data.DataView>コレクションビューを独自のオブジェクトで初期化します。  
  
#### <a name="sorting"></a>並べ替え  
 前述したように、ビューでは並べ替え順序をコレクションに適用できます。 これは基になるコレクション内に存在するため、データに関連性がない場合や、本来の順序ではない場合もあります。 コレクションのビューでは、指定する比較の基準に基づいて、順序を強制したり、既定の順序を変更することができます。 これはデータのクライアント ベースのビューであるため、一般的なシナリオは、ユーザーが列に対応する値ごとに表形式のデータの列を並べ替える場合です。 ビューを使用することで、このようなユーザー主導の並べ替えを適用することができます。この場合も、基になるコレクションを変更したり、コレクションのコンテンツにクエリを再実行する必要はありません。 例については、「[ヘッダーがクリックされたときに GridView 列を並べ替える](../controls/how-to-sort-a-gridview-column-when-a-header-is-clicked.md)」を参照してください。  
  
 次の例は、「[データバインディングとは](#what_is_data_binding)」セクションのアプリケーション[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]の " <xref:System.Windows.Controls.CheckBox>カテゴリと日付で並べ替え" の並べ替えロジックを示しています。  
  
 [!code-csharp[DataBindingLab#8](~/samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/MainWindow.xaml.cs#8)]
 [!code-vb[DataBindingLab#8](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataBindingLab/VisualBasic/MainWindow.xaml.vb#8)]  
  
#### <a name="filtering"></a>フィルター処理  
 ビューでは、コレクションにフィルターを適用することもできます。 つまり、項目がコレクションに存在していても、この特定のビューは、コレクション全体の特定のサブセットのみを表示することを意図しています。 データ内の条件をフィルターすることができます。 たとえば、アプリケーションによる[データバインドの定義](#what_is_data_binding)に関するセクションでは、"Show only bargains" <xref:System.Windows.Controls.CheckBox>には、$25 以上のコストの項目を除外するためのロジックが含まれています。 次のコードを実行すると、 *ShowOnlyBargainsFilter*が<xref:System.Windows.Data.CollectionViewSource.Filter>選択された<xref:System.Windows.Controls.CheckBox>ときにイベントハンドラーとして設定されます。  
  
 [!code-csharp[DataBindingLab#10](~/samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/MainWindow.xaml.cs#10)]
 [!code-vb[DataBindingLab#10](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataBindingLab/VisualBasic/MainWindow.xaml.vb#10)]  
  
 *ShowOnlyBargainsFilter* イベント ハンドラーには、次の実装があります。  
  
 [!code-csharp[DataBindingLab#5](~/samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/MainWindow.xaml.cs#5)]
 [!code-vb[DataBindingLab#5](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataBindingLab/VisualBasic/MainWindow.xaml.vb#5)]  
  
 では<xref:System.Windows.Data.CollectionView> <xref:System.Windows.Data.CollectionViewSource>なく、クラスのいずれかを直接使用している場合は、 <xref:System.Windows.Data.CollectionView.Filter%2A>プロパティを使用してコールバックを指定します。 例については、「[ビュー内のデータをフィルター処理する](how-to-filter-data-in-a-view.md)」を参照してください。  
  
#### <a name="grouping"></a>グループ化  
 コレクションを表示<xref:System.Collections.IEnumerable>する内部クラスを除き、すべてのコレクションビューはグループ化の機能をサポートしているので、ユーザーはコレクションビュー内のコレクションを論理グループに分割できます。 グループは、明示的 (ユーザーがグループの一覧を提供する) または暗黙的 (グループがデータに応じて動的に生成される) にすることができます。  
  
 次の例は、"Group by category" <xref:System.Windows.Controls.CheckBox>のロジックを示しています。  
  
 [!code-csharp[DataBindingLab#6](~/samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/MainWindow.xaml.cs#6)]
 [!code-vb[DataBindingLab#6](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataBindingLab/VisualBasic/MainWindow.xaml.vb#6)]  
  
 別のグループ化の例については、「[GridView を実装する ListView の項目をグループ化する](../controls/how-to-group-items-in-a-listview-that-implements-a-gridview.md)」を参照してください。  
  
#### <a name="current-item-pointers"></a>現在の項目ポインター  
 ビューでは、現在の項目の概念もサポートされています。 コレクション ビュー内のオブジェクト間を移動することができます。 移動するときに、項目のポインターを動かすことで、コレクション内の特定の場所に存在するオブジェクトを取得できます。 例については、「[データ CollectionView のオブジェクト間を移動する](how-to-navigate-through-the-objects-in-a-data-collectionview.md)」を参照してください。  
  
 WPF はビュー (指定したビュー、またはコレクションの既定のビュー) を使用してコレクションのみにバインドするため、コレクションへのすべてのバインディングには現在の項目のポインターがあります。 ビューにバインドする際に、`Path` 値内のスラッシュ ("/") 文字は、ビューの現在の項目を指定します。 次の例では、データ コンテキストはコレクション ビューです。 最初の行は、コレクションにバインドします。 2 番目の行は、コレクション内の現在の項目にバインドします。 3 番目の行は、コレクション内の現在の項目の `Description` プロパティにバインドします。  
  
```xaml  
<Button Content="{Binding }" />  
<Button Content="{Binding Path=/}" />  
<Button Content="{Binding Path=/Description}" />   
```  
  
 スラッシュとプロパティの構文をスタックして、コレクションの階層をトラバースすることもできます。 次の例では、ソース コレクションの現在の項目のプロパティでである、`Offices` という名前のコレクションの現在の項目にバインドします。  
  
```xaml  
<Button Content="{Binding /Offices/}" />  
```  
  
 現在の項目のポインターは、コレクションに適用されている任意の並べ替えまたはフィルター処理の影響を受ける場合があります。 並べ替えは、現在の項目のポインターを最後に選択した項目に保持しますが、コレクション ビューはそれを中心に再構築されています (以前はリストの先頭にあった選択した項目が、現在はリストの中ほどにある場合があります)。フィルター処理後に選択した項目がビューに残っている場合、フィルター処理はその項目を保持します。 それ以外の場合は、現在の項目のポインターが、フィルター処理されたコレクション ビューの最初の項目に設定されます。  
  
<a name="master_detail_scenario"></a>   
#### <a name="master-detail-binding-scenario"></a>マスターと詳細のバインディング シナリオ  
 現在の項目の概念は、コレクション内の項目間の移動に役立つだけでなく、マスターと詳細のバインディング シナリオにも役立ちます。 もう一度、「[データ バインディングとは](#what_is_data_binding)」セクションのアプリケーション [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] を考えてみましょう。 そのアプリケーションでは、内<xref:System.Windows.Controls.ListBox>の選択によって<xref:System.Windows.Controls.ContentControl>に表示されるコンテンツが決まります。 別の方法で配置するには、 <xref:System.Windows.Controls.ListBox>項目を選択<xref:System.Windows.Controls.ContentControl>すると、選択した項目の詳細がに表示されます。  
  
 同じビューにバインドされた 2 つ以上のコントロールがあるだけで、マスターと詳細のシナリオを実装できます。 [データバインディングデモ](https://go.microsoft.com/fwlink/?LinkID=163703)の次の例では、のマークアップ<xref:System.Windows.Controls.ListBox>と<xref:System.Windows.Controls.ContentControl> 、アプリケーション[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]に表示されるの[データバインディングの概要](#what_is_data_binding)について説明します。  
  
 [!code-xaml[DataBindingLab#Master1](~/samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/MainWindow.xaml#master1)]  
[!code-xaml[DataBindingLab#Master2](~/samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/MainWindow.xaml#master2)]  
[!code-xaml[DataBindingLab#Detail](~/samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/MainWindow.xaml#detail)]  
  
 両方のコントロールが同じソース *listingDataView* 静的リソース (このリソースの定義は「[ビューの作成方法](#how_to_create_a_view)」セクションを参照してください) にバインドされていることに注目してください。 これは、シングルトンオブジェクト (この場合は<xref:System.Windows.Controls.ContentControl> ) がコレクションビューにバインドされると、ビュー <xref:System.Windows.Data.CollectionView.CurrentItem%2A>のに自動的にバインドされるためです。 オブジェクトが<xref:System.Windows.Data.CollectionViewSource>通貨と選択を自動的に同期することに注意してください。 この例のように、リストコントロールが<xref:System.Windows.Data.CollectionViewSource>オブジェクトにバインドされていない場合は、その<xref:System.Windows.Controls.Primitives.Selector.IsSynchronizedWithCurrentItem%2A>プロパティをに`true`設定して、これが機能するようにする必要があります。  
  
 その他の例については、「[コレクションにバインドして選択に基づく情報を表示する](how-to-bind-to-a-collection-and-display-information-based-on-selection.md)」と「[階層データでマスター詳細パターンを使用する](how-to-use-the-master-detail-pattern-with-hierarchical-data.md)」を参照してください。  
  
 上記の例では、テンプレートが使用されています。 実際、データは、 <xref:System.Windows.Controls.ContentControl>テンプレート (で明示的に使用されているものと、に<xref:System.Windows.Controls.ListBox>よって暗黙的に使用されるもの) を使用せずに、希望の方法で表示されることはありません。 次のセクションで、データ テンプレートについて説明します。  
  
<a name="data_templating"></a>   
## <a name="data-templating"></a>データ テンプレート  
 データ テンプレートを使用しないと、「[データ バインディングとは](#what_is_data_binding)」セクションのアプリケーション [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] は、次のようになります。  
  
 ![データ テンプレートのないデータ バインディング デモ](./media/data-binding-overview/data-binding-demo-templates.png)  
  
 前のセクションの例に示されているように<xref:System.Windows.Controls.ListBox> 、コントロールと<xref:System.Windows.Controls.ContentControl>は両方とも、 *AuctionItem*s のコレクションオブジェクト全体 (具体的には、コレクションオブジェクトに対するビュー) にバインドされています。 データコレクション<xref:System.Windows.Controls.ListBox>を表示する具体的な指示がないと、は、基になるコレクション内の各オブジェクトの文字列表現を<xref:System.Windows.Controls.ContentControl>表示し、は、バインドされているオブジェクトの文字列表現を表示します。  
  
 この問題を解決するには、 <xref:System.Windows.DataTemplate>アプリケーションでを定義します。 前のセクションの例に示されている<xref:System.Windows.Controls.ContentControl>ように、では*detailsProductListingTemplate*<xref:System.Windows.DataTemplate>が明示的に使用されます。 コントロール<xref:System.Windows.Controls.ListBox>は、コレクション内の<xref:System.Windows.DataTemplate> *AuctionItem*オブジェクトを表示するときに、次のものを暗黙的に使用します。  
  
 [!code-xaml[DataBindingLab#AuctionItemDataTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/DataBindingLabApp.xaml#auctionitemdatatemplate)]  
  
 これら2つ<xref:System.Windows.DataTemplate>のを使用すると、結果として得られる UI は、「[データバインディングとは](#what_is_data_binding)」セクションで示されているものになります。 このスクリーンショットからわかるように、コントロールにデータを配置するだけでなく、を<xref:System.Windows.DataTemplate>使用すると、データに説得力のあるビジュアルを定義することができます。 たとえば、上<xref:System.Windows.DataTrigger> <xref:System.Windows.DataTemplate>ので s が使用されているため、 *AuctionItem*s と特別*特徴*の値が*強調*表示されると、オレンジ色の枠線と星が表示されます。  
  
 データ テンプレートの詳細については、「[データ テンプレートの概要](data-templating-overview.md)」を参照してください。  
  
<a name="data_validation"></a>   
## <a name="data-validation"></a>データの検証  
  
 ユーザー入力を受け取るほとんどのアプリケーションには、ユーザーが必要な情報を入力していることを確認する検証ロジックが必要です。 検証チェックは、型、範囲、形式、またはその他のアプリケーションに固有の要件に基づいて作成できます。 このセクションでは、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] でデータ検証がどのように機能するかについて説明します。  
  
### <a name="associating-validation-rules-with-a-binding"></a>検証ルールをバインドに関連付ける  
 データバインディングモデルを使用すると、 <xref:System.Windows.Data.Binding.ValidationRules%2A> <xref:System.Windows.Data.Binding>オブジェクトに関連付けることができます。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] たとえば、次の例では、 <xref:System.Windows.Controls.TextBox>をという名前`StartPrice`のプロパティに<xref:System.Windows.Controls.ExceptionValidationRule>バインドし、 <xref:System.Windows.Data.Binding.ValidationRules%2A?displayProperty=nameWithType>オブジェクトをプロパティに追加します。  
  
 [!code-xaml[DataBindingLab#DefaultValidation](~/samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/AddProductWindow.xaml#defaultvalidation)]  
  
 <xref:System.Windows.Controls.ValidationRule>オブジェクトは、プロパティの値が有効かどうかを確認します。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]には、次の2種類の組み込み<xref:System.Windows.Controls.ValidationRule>オブジェクトがあります。  
  
- は<xref:System.Windows.Controls.ExceptionValidationRule> 、バインディングソースプロパティの更新中にスローされた例外を確認します。 前述の例では、`StartPrice` は整数型です。 ユーザーが整数に変換できない値を入力すると、例外がスローされ、バインディングが無効としてマークされます。 を明示的に設定する<xref:System.Windows.Controls.ExceptionValidationRule>別の構文は、 <xref:System.Windows.Data.Binding.ValidatesOnExceptions%2A> <xref:System.Windows.Data.Binding>または`true` <xref:System.Windows.Data.MultiBinding>オブジェクトのプロパティをに設定することです。  
  
- オブジェクト<xref:System.Windows.Controls.DataErrorValidationRule>は、 <xref:System.ComponentModel.IDataErrorInfo>インターフェイスを実装するオブジェクトによって発生したエラーを確認します。 この検証規則の使用例については<xref:System.Windows.Controls.DataErrorValidationRule>、「」を参照してください。 を明示的に設定する<xref:System.Windows.Controls.DataErrorValidationRule>別の構文は、 <xref:System.Windows.Data.Binding.ValidatesOnDataErrors%2A> <xref:System.Windows.Data.Binding>または`true` <xref:System.Windows.Data.MultiBinding>オブジェクトのプロパティをに設定することです。  
  
 <xref:System.Windows.Controls.ValidationRule>クラスから派生し、 <xref:System.Windows.Controls.ValidationRule.Validate%2A>メソッドを実装することによって、独自の検証規則を作成することもできます。 次の例では、[[データバインディングとは](#what_is_data_binding)] セクションの [製品<xref:System.Windows.Controls.TextBox>の追加]*一覧*の [開始日] で使用されるルールを示します。  
  
 [!code-csharp[DataBindingLab#2](~/samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/FutureDateRule.cs#2)]
 [!code-vb[DataBindingLab#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataBindingLab/VisualBasic/FutureDateRule.vb#2)]  
  
 *Startdateentryform* <xref:System.Windows.Controls.TextBox>は、次の例に示すように、この*FutureDateRule*を使用します。  
  
 [!code-xaml[DataBindingLab#CustomValidation](~/samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/AddProductWindow.xaml#customvalidation)]  
  
 <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A>値がのため、バインド<xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>エンジンによって、すべてのキーストロークのソース値が更新されることに注意して<xref:System.Windows.Data.Binding.ValidationRules%2A>ください。これは、すべてのキーストロークでコレクション内のすべての規則をチェックすることを意味します。 これについては、「検証プロセス」セクションで詳しく説明します。  
  
<a name="invalidation_feedback"></a>   
### <a name="providing-visual-feedback"></a>視覚的なフィードバックを提供する  
 ユーザーが無効な値を入力した場合に、エラーに関する何らかのフィードバックをアプリケーション [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] に提供することができます。 このようなフィードバックを提供する方法の 1 <xref:System.Windows.Controls.Validation.ErrorTemplate%2A?displayProperty=nameWithType>つは、添付プロパティ<xref:System.Windows.Controls.ControlTemplate>をカスタムに設定することです。 前のサブセクションで示したように、 *startdateentryform* <xref:System.Windows.Controls.TextBox>は、 <xref:System.Windows.Controls.Validation.ErrorTemplate%2A>呼び出された*validationtemplate*を使用します。 次の例は、*validationTemplate* の定義を示します。  
  
 [!code-xaml[DataBindingLab#1](~/samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/AddProductWindow.xaml#1)]  
  
 要素<xref:System.Windows.Controls.AdornedElementPlaceholder>は、装飾されるコントロールを配置する場所を指定します。  
  
 さらに、を<xref:System.Windows.Controls.ToolTip>使用してエラーメッセージを表示することもできます。 *Startdateentryform*と*StartPriceEntryForm*<xref:System.Windows.Controls.TextBox>es は両方とも<xref:System.Windows.Controls.ToolTip> style *textStyleTextBox*を使用します。これにより、エラーメッセージを表示するが作成されます。 次の例は、*textStyleTextBox* の定義を示します。 添付プロパティ<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> `true`は、バインドされた要素のプロパティで1つ以上のバインドがエラーになった場合に発生します。  
  
 [!code-xaml[DataBindingLab#14](~/samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/DataBindingLabApp.xaml#14)]  
  
 カスタム<xref:System.Windows.Controls.Validation.ErrorTemplate%2A> <xref:System.Windows.Controls.TextBox>の<xref:System.Windows.Controls.ToolTip>とを使用すると、検証エラーが発生したときに、 *startdateentryform*は次のようになります。  
  
 ![データ バインディングの検証エラー](./media/databindingdemo-validation.PNG "DataBindingDemo_Validation")  
  
 に<xref:System.Windows.Data.Binding>検証規則が関連付けられているが、バインド<xref:System.Windows.Controls.Validation.ErrorTemplate%2A>されたコントロールにを指定<xref:System.Windows.Controls.Validation.ErrorTemplate%2A>していない場合は、検証エラーが発生したときにユーザーに通知するための既定値が使用されます。 既定値<xref:System.Windows.Controls.Validation.ErrorTemplate%2A>は、装飾レイヤーの赤い枠線を定義するコントロールテンプレートです。 <xref:System.Windows.Controls.Validation.ErrorTemplate%2A>既定の<xref:System.Windows.Controls.TextBox> [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]およびでは、検証エラーが発生すると、StartPriceEntryForm のは次のようになります。 <xref:System.Windows.Controls.ToolTip>  
  
 ![データ バインディングの検証エラー](./media/databindingdemo-validationdefault.PNG "DataBindingDemo_ValidationDefault")  
  
 ダイアログ ボックス内のすべてのコントロールを検証するためのロジックを提供する方法の例については、「[ダイアログ ボックスの概要](../app-development/dialog-boxes-overview.md)」の「カスタム ダイアログ ボックス」セクションを参照してください。  
  
### <a name="validation-process"></a>検証プロセス  
 検証は通常、ターゲットの値がバインディング ソースのプロパティに転送されるときに発生します。 これは、 <xref:System.Windows.Data.BindingMode.TwoWay>バインディング<xref:System.Windows.Data.BindingMode.OneWayToSource>とバインドで発生します。 繰り返しますが、ソースの更新が発生する原因は、 <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A>プロパティの値によって異なります。詳細については、「ソースの[更新トリガー](#what_triggers_source_updates) 」を参照してください。  
  
 次に*検証*プロセスを説明します。 このプロセス中の任意の時点で検証エラーまたはその他の種類のエラーが発生すると、プロセスが停止されることに注意してください。  
  
1. バインディングエンジンは、 <xref:System.Windows.Controls.ValidationRule> <xref:System.Windows.Controls.ValidationStep.RawProposedValue> <xref:System.Windows.Controls.ValidationRule.Validate%2A> がに<xref:System.Windows.Controls.ValidationRule>設定されているカスタムオブジェクトが定義されているかどうかを確認します。この場合、そのオブジェクトのいずれかがエラーになるまで、それぞれのに対してメソッドを呼び出します。<xref:System.Windows.Data.Binding> <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A>または、すべての処理が成功するまで続きます。  
  
2. その後、バインディング エンジンがコンバーターを呼び出します (ある場合)。  
  
3. コンバーターが正常に終了した場合、バインディングエンジン<xref:System.Windows.Controls.ValidationRule>は、 <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A>がに<xref:System.Windows.Controls.ValidationStep.ConvertedProposedValue>設定されているカスタムオブジェクトがあるかどうかを確認<xref:System.Windows.Controls.ValidationRule.Validate%2A>します。 <xref:System.Windows.Controls.ValidationRule>その<xref:System.Windows.Data.Binding>場合は、のいずれ<xref:System.Windows.Controls.ValidationStep.ConvertedProposedValue>かがエラーになるか、またはすべてのが成功するまで、をに設定します。 <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A>  
  
4. バインディング エンジンは、ソース プロパティを設定します。  
  
5. <xref:System.Windows.Controls.ValidationRule>バインディングエンジンは、 <xref:System.Windows.Controls.ValidationStep.UpdatedValue> <xref:System.Windows.Controls.ValidationRule> <xref:System.Windows.Controls.ValidationRule.Validate%2A> がに設定<xref:System.Windows.Controls.ValidationRule.ValidationStep%2A>されているカスタムオブジェクトが定義されているかどうかを確認します。この場合、がに設定されている各に対してメソッドを呼び出します。<xref:System.Windows.Data.Binding> <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A><xref:System.Windows.Controls.ValidationStep.UpdatedValue>そのうちの1つがエラーになるまで、またはすべての処理が成功するまで実行されます。 がバインディングに関連付けられてい<xref:System.Windows.Controls.ValidationRule.ValidationStep%2A>て、そのが既定値<xref:System.Windows.Controls.ValidationStep.UpdatedValue> <xref:System.Windows.Controls.DataErrorValidationRule>に設定されている場合、はこの時点でチェックされます。 <xref:System.Windows.Controls.DataErrorValidationRule> これは、 <xref:System.Windows.Data.Binding.ValidatesOnDataErrors%2A>がに`true`設定されているバインディングがチェックされる場合も指します。  
  
6. <xref:System.Windows.Controls.ValidationRule>バインディングエンジンは、 <xref:System.Windows.Controls.ValidationStep.CommittedValue> <xref:System.Windows.Controls.ValidationRule> <xref:System.Windows.Controls.ValidationRule.Validate%2A> がに設定<xref:System.Windows.Controls.ValidationRule.ValidationStep%2A>されているカスタムオブジェクトが定義されているかどうかを確認します。この場合、がに設定されている各に対してメソッドを呼び出します。<xref:System.Windows.Data.Binding> <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A><xref:System.Windows.Controls.ValidationStep.CommittedValue>そのうちの1つがエラーになるまで、またはすべての処理が成功するまで実行されます。  
  
 がこのプロセス全体を通じていつでも通過しない場合、バインディングエンジン<xref:System.Windows.Controls.ValidationError>はオブジェクトを作成<xref:System.Windows.Controls.Validation.Errors%2A?displayProperty=nameWithType>し、バインドされた要素のコレクションに追加します。 <xref:System.Windows.Controls.ValidationRule> バインドエンジンは、特定の<xref:System.Windows.Controls.ValidationRule>手順でオブジェクトを実行する前に、 <xref:System.Windows.Controls.ValidationError>バインドされた要素<xref:System.Windows.Controls.Validation.Errors%2A?displayProperty=nameWithType>の添付プロパティに追加されたを削除します。 たとえば場合、<xref:System.Windows.Controls.ValidationRule>が<xref:System.Windows.Controls.ValidationRule.ValidationStep%2A>に設定されている<xref:System.Windows.Controls.ValidationStep.UpdatedValue>に失敗しました次回の検証プロセスが発生すると、バインディング エンジンが削除される<xref:System.Windows.Controls.ValidationError>前にいずれかの呼び出しの直前に<xref:System.Windows.Controls.ValidationRule>を持つ<xref:System.Windows.Controls.ValidationRule.ValidationStep%2A>に設定<xref:System.Windows.Controls.ValidationStep.UpdatedValue>。  
  
 が<xref:System.Windows.Controls.Validation.Errors%2A?displayProperty=nameWithType>空でない`true`場合、要素の添付プロパティはに設定されます。<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> また、 <xref:System.Windows.Data.Binding.NotifyOnValidationError%2A> `true`のプロパティ<xref:System.Windows.Controls.Validation.Error?displayProperty=nameWithType>がに設定されている場合、バインディングエンジンは要素の添付イベントを発生させます。 <xref:System.Windows.Data.Binding>  
  
 また、いずれかの方向 (ターゲットからソースまたはソースからターゲット) への有効な値<xref:System.Windows.Controls.Validation.Errors%2A?displayProperty=nameWithType>転送は、添付プロパティをクリアすることにも注意してください。  
  
 バインディング<xref:System.Windows.Controls.ExceptionValidationRule>に関連付けられているがある場合、また<xref:System.Windows.Data.Binding.ValidatesOnExceptions%2A>はプロパティがに`true`設定されていて、バインドエンジンがソースを設定したときに例外がスローされた<xref:System.Windows.Data.Binding.UpdateSourceExceptionFilter%2A>場合、バインディングエンジンはがあるかどうかを確認します。 <xref:System.Windows.Data.Binding.UpdateSourceExceptionFilter%2A>コールバックを使用して、例外を処理するためのカスタムハンドラーを提供するオプションがあります。 がに指定されていない<xref:System.Windows.Controls.Validation.Errors%2A?displayProperty=nameWithType>場合<xref:System.Windows.Controls.ValidationError> 、バインディングエンジンは例外を使用してを作成し、バインドされた要素のコレクションに<xref:System.Windows.Data.Binding>追加 <xref:System.Windows.Data.Binding.UpdateSourceExceptionFilter%2A>します。  
  
## <a name="debugging-mechanism"></a>デバッグのメカニズム  
 バインディング関連のオブジェクトの添付<xref:System.Diagnostics.PresentationTraceSources.TraceLevel%2A?displayProperty=nameWithType>プロパティを設定して、特定のバインディングの状態に関する情報を受け取ることができます。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Controls.DataErrorValidationRule>
- [WPF Version 4.5 の新機能](../getting-started/whats-new.md)
- [LINQ クエリの結果にバインドする](how-to-bind-to-the-results-of-a-linq-query.md)
- [データ バインディング](../advanced/optimizing-performance-data-binding.md)
- [データバインディングのデモ](https://go.microsoft.com/fwlink/?LinkID=163703)
- [方法トピック](data-binding-how-to-topics.md)
- [ADO.NET データ ソースにバインドする](how-to-bind-to-an-ado-net-data-source.md)
