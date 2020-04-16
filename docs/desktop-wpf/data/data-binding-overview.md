---
title: データ バインディングの概要
description: NET Core 用 Windows プレゼンテーション ファウンデーションでプロジェクトに追加できるさまざまなデータ ソースについて説明します。 データ ソースは XAML 要素にバインドして、動的なアプリを作成できます。
author: thraka
ms.date: 09/19/2019
ms.author: adegeo
dev_langs:
- csharp
- vb
ms.openlocfilehash: 7f17ff094a35c04ba880c87c6966d7d249817516
ms.sourcegitcommit: b75a45f0cfe012b71b45dd9bf723adf32369d40c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/24/2020
ms.locfileid: "81433254"
---
# <a name="data-binding-overview-in-wpf"></a>WPF でのデータ バインディングの概要

Windows プレゼンテーション ファンデーション (WPF) のデータ バインディングは、アプリがデータを表示および操作するためのシンプルで一貫した方法を提供します。 要素は、.NET オブジェクトと XML の形式でさまざまなデータ ソースのデータにバインドできます。 <xref:System.Windows.Controls.ContentControl>など<xref:System.Windows.Controls.Button>、および<xref:System.Windows.Controls.ItemsControl>など<xref:System.Windows.Controls.ListBox><xref:System.Windows.Controls.ListView>、1 つのデータ項目またはデータ項目のコレクションの柔軟なスタイル設定を可能にする組み込み機能があります。 並べ替えビュー、フィルター ビュー、およびグループ ビューは、データの上に生成できます。

WPF のデータ バインディング機能には、幅広いプロパティによるデータ バインディングの固有のサポート、柔軟なデータ UI 表現、ビジネス ロジックの UI からの明確な分離など、従来のモデルに対していくつかの利点があります。

この記事では、まず WPF データ バインディングの基本概念について説明<xref:System.Windows.Data.Binding>し、次にクラスの使用方法とデータ バインディングのその他の機能について説明します。

[!INCLUDE [desktop guide under construction](../../../includes/desktop-guide-preview-note.md)]

## <a name="what-is-data-binding"></a>データ バインディングとは何か。

データ バインディングは、アプリ UI と表示されるデータとの間の接続を確立するプロセスです。 バインドが適切に設定され、データから適切な通知が提供される場合、データの値が変更されると、そのデータにバインドされている要素に変更が自動的に反映されます。 データ バインディングには、要素内のデータの外部表現が変更された場合、基になるデータを自動的に更新して変更を反映できるという意味もあります。 たとえば、ユーザーが要素の値を編集すると`TextBox`、基になるデータ値が自動的に更新され、その変更が反映されます。

データ バインディングの一般的な用途は、サーバーまたはローカルの構成データをフォームまたは他の UI コントロールに配置することです。 WPF では、この概念は、さまざまなデータ ソースに対する幅広いプロパティのバインドを含むように拡張されています。 WPF では、要素の依存関係プロパティを .NET オブジェクト (ADO.NET オブジェクトまたは Web サービスおよび Web プロパティに関連付けられたオブジェクトを含む) および XML データにバインドできます。

データ バインディングの例については、オークション アイテムの一覧を表示する[データ バインド デモ][data-binding-demo]の次のアプリ UI を見てみましょう。

![データ バインディングのサンプル のスクリーンショット](./media/data-binding-overview/demo.png "DataBinding_DataBindingDemo")

アプリは、データ バインディングの次の機能を示しています。

- リスト ボックスの内容は、*オークション アイテム*オブジェクトのコレクションにバインドされます。 *AuctionItem*オブジェクトには、*説明*、*開始価格*、*開始日*、*カテゴリ*、*特殊機能*などのプロパティがあります。

- に表示されるデータ (*AuctionItem* `ListBox`オブジェクト ) は、各明細に対して説明と現在の価格が表示されるようにテンプレート化されています。 テンプレートは を使用して作成<xref:System.Windows.DataTemplate>されます。 さらに、各項目の外観は、表示されている *AuctionItem* の *SpecialFeatures* の値に依存します。 *AuctionItem* の *SpecialFeatures* の値が *Color* の場合、その項目には青の枠線が付きます。 値が *Highlight* の場合、その項目にはオレンジの枠線と星が付きます。 「[データ テンプレート](#data-templating)」セクションでは、データ テンプレートに関する情報を提供します。

- ユーザーは、`CheckBoxes`提供された を使用して、データをグループ化、フィルター処理、または並べ替えることができます。 上の画像では、[**カテゴリでグループ化**] と [`CheckBoxes`**カテゴリと日付で並べ替え]** が選択されています。 データが製品のカテゴリに基づいてグループ化され、カテゴリ名がアルファベット順になっていることが分かります。 図では分かりにくいですが、項目は各カテゴリ内での開始日でも並べ替えられています。 並べ替えは *、コレクション ビュー*を使用して行います。 コレクション ビュー[のバインディングセクションでは、](#binding-to-collections)コレクション ビューについて説明します。

- ユーザーが項目を選択すると、 に<xref:System.Windows.Controls.ContentControl>選択した項目の詳細が表示されます。 このエクスペリエンスを*マスター詳細シナリオ と呼ばれます*。 [マスター詳細シナリオ](#master-detail-binding-scenario)セクションでは、このタイプのバインディングに関する情報を提供します。

- *プロパティ*の型は<xref:System.DateTime>、ミリ秒までの時間を含む日付を返します。 このアプリでは、短い日付文字列が表示されるようにカスタム コンバータが使用されています。 [データ変換](#data-conversion)セクションでは、コンバータに関する情報を提供します。

ユーザーが *[製品の追加]* ボタンを選択すると、次のフォームが表示されます。

![[Add Product Listing] ページ](./media/data-binding-overview/demo-addproductlisting.png "DataBinding_Demo_AddProductListing")

ユーザーは、フォームのフィールドを編集し、短いプレビュー ウィンドウまたは詳細なプレビュー ウィンドウを使用して製品`Submit`一覧をプレビューし、新しい製品一覧を追加することを選択できます。 既存のグループ化、フィルタ、並べ替えの設定は、新しいエントリに適用されます。 この特定のケースでは、上のイメージで入力した項目が *Computer* カテゴリ内の 2 番目の項目として表示されます。

このイメージには表示されないのは、*開始日*<xref:System.Windows.Controls.TextBox>に示されている検証ロジックです。 ユーザーが無効な日付 (無効な書式または過去の日付) を入力すると、ユーザーに通知<xref:System.Windows.Controls.ToolTip>され、 の横に赤い感嘆<xref:System.Windows.Controls.TextBox>符が表示されます。 検証ロジックの作成方法については、「[データの検証](#data-validation)」セクションで説明します。

上記のデータ バインディングのさまざまな機能に入る前に、WPF データ バインディングを理解するために重要な基本的な概念について説明します。

## <a name="basic-data-binding-concepts"></a>データ バインディングの基本概念

バインドする要素やデータ ソースの性質に関係なく、各バインディングは常に次の図に示すモデルに従います。

![基本的なデータ バインディング モデルを示す図。](./media/data-binding-overview/basic-data-binding-diagram.png)

図に示すように、データ バインディングは基本的にバインディング ターゲットとバインディング ソースの間のブリッジです。 次の図は、WPF データ バインディングの基本的な概念を示しています。

- 通常、各バインディングには 4 つのコンポーネントがあります。

  - バインディング ターゲット オブジェクト。
  - ターゲット プロパティ。
  - バインディング ソース。
  - 使用するバインディング ソースの値へのパス。
  
  > `TextBox`たとえば、 のコンテンツを`Employee.Name`プロパティにバインドする場合、ターゲット オブジェクトは`TextBox`、 ターゲット プロパティは<xref:System.Windows.Controls.TextBox.Text%2A>プロパティ、使用する値は*Name、* ソース オブジェクトは*Employee*オブジェクトです。

- ターゲット プロパティは、依存関係プロパティである必要があります。 ほとんどの<xref:System.Windows.UIElement>プロパティは依存関係プロパティであり、ほとんどの依存関係プロパティは読み取り専用プロパティを除き、既定でデータ バインディングをサポートします。 (依存関係プロパティを定義<xref:System.Windows.DependencyObject>できるのは派生型のみで、すべての<xref:System.Windows.UIElement>型は`DependencyObject`から派生します)。

- 図に示されていませんが、バインディング ソース オブジェクトがカスタム .NET オブジェクトに限定されないことに注意してください。 WPF データ バインディングは、.NET オブジェクトと XML 形式のデータをサポートします。 いくつかの例を示すために、バインディング ソースは、<xref:System.Windows.UIElement>任意のリスト オブジェクト、ADO.NETまたは Web サービス オブジェクト、または XML データを含む XmlNode です。 詳しくは、[バインディング・ソースの概要を](../../framework/wpf/data/binding-sources-overview.md)参照してください。

バインディングを確立する場合は、バインディング ターゲットをバインディング ソース*に*バインドすることに注意してください。 たとえば、使用データ バインディングで基になる XML データを<xref:System.Windows.Controls.ListBox>表示する場合、XML データに`ListBox`バインドします。

バインディングを確立するには、オブジェクトを<xref:System.Windows.Data.Binding>使用します。 この資料の残りの部分では、オブジェクトに関連する概念の多く、およびオブジェクトの`Binding`プロパティと使用方法について説明します。

### <a name="direction-of-the-data-flow"></a>データ フローの方向

前の図の矢印に示すように、バインディングのデータ フローは、バインディング のターゲットからバインディング ソースに向かう可能性があります (たとえば、ユーザーが の値を`TextBox`編集するとソース値が変更される、バインディング ソースからバインディング ターゲットに (たとえば、`TextBox`コンテンツがソースの変更で更新されます) 場合、バインディング ソースが適切な通知を提供します。

ユーザーがデータを変更し、ソース オブジェクトに反映できるようにアプリを使用できます。 または、ユーザーがソース データを更新できないようにすることもできます。 データの流れを制御する場合は、<xref:System.Windows.Data.Binding.Mode?displayProperty=nameWithType>を設定します。

次の図は、さまざまな種類のデータ フローを示しています。

![データ バインディング データ フロー](./media/data-binding-overview/databinding-dataflow.png "DataBinding_DataFlow")

- <xref:System.Windows.Data.BindingMode.OneWay>バインドを行うと、ソース プロパティに対する変更が自動的に更新されますが、ターゲット プロパティへの変更はソース プロパティに反映されません。 この型のバインディングは、バインドされているコントロールが暗黙的な読み取り専用の場合に適しています。 たとえば、ストック ティッカーなどのソースにバインドしたり、テーブルのデータ バインド背景色などの変更を行うためのコントロール インターフェイスがターゲット プロパティに備わっていない場合があります。 ターゲット プロパティの変更を監視する必要がない場合は、<xref:System.Windows.Data.BindingMode.OneWay> バインディング モードを使うことにより、<xref:System.Windows.Data.BindingMode.TwoWay> バインディング モードのオーバーヘッドを回避できます。

- <xref:System.Windows.Data.BindingMode.TwoWay>バインドすると、ソース プロパティまたはターゲット プロパティが変更され、他方が自動的に更新されます。 この種類のバインディングは、編集可能なフォームやその他の完全に対話型の UI シナリオに適しています。 ほとんどのプロパティは既定<xref:System.Windows.Data.BindingMode.OneWay>でバインディングに設定されていますが、一部の依存関係プロパティ (通常は、ユーザー<xref:System.Windows.Controls.TextBox.Text?displayProperty=nameWithType>が編集可能なコントロールのプロパティ ( <xref:System.Windows.Data.BindingMode.TwoWay> [および CheckBox.IsChecked](xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked)などの既定のバインディング ) 。 依存関係プロパティが既定で一方向または双方向のどちらにバインドされるかをプログラムで判断するには、プロパティ メタデータを取得<xref:System.Windows.DependencyProperty.GetMetadata%2A?displayProperty=nameWithType>してから<xref:System.Windows.FrameworkPropertyMetadata.BindsTwoWayByDefault%2A?displayProperty=nameWithType>、プロパティのブール値を確認します。

- <xref:System.Windows.Data.BindingMode.OneWayToSource>バインディングの逆です<xref:System.Windows.Data.BindingMode.OneWay>。ターゲット プロパティが変更されると、ソース プロパティが更新されます。 シナリオの例としては、UI からソース値を再評価するだけで済みます。

- 図に示されていないバインディングは<xref:System.Windows.Data.BindingMode.OneTime>、ソース プロパティがターゲット プロパティを初期化するが、後続の変更を反映しません。 データ コンテキストが変更された場合、またはデータ コンテキスト内のオブジェクトが変更*された*場合、その変更はターゲット プロパティに反映されません。 この種類のバインディングは、現在の状態のスナップショットが適切であるか、データが本当に静的である場合に適しています。 また、ソース プロパティの値を使用してターゲット プロパティを初期化するときにデータ コンテキストが事前にわからない場合にも、この型のバインディングは便利です。 このモードは基本的に単純な<xref:System.Windows.Data.BindingMode.OneWay>バインディング形式で、ソース値が変更されない場合にパフォーマンスが向上します。

ソースの変更 (および<xref:System.Windows.Data.BindingMode.OneWay><xref:System.Windows.Data.BindingMode.TwoWay>バインディングに適用可能) を検出するには、ソースが、 などの<xref:System.ComponentModel.INotifyPropertyChanged>適切なプロパティ変更通知メカニズムを実装する必要があります。 実装[の例については、「方法: プロパティ変更通知を実装](../../framework/wpf/data/how-to-implement-property-change-notification.md)する」を参照してください。 <xref:System.ComponentModel.INotifyPropertyChanged>

この<xref:System.Windows.Data.Binding.Mode?displayProperty=nameWithType>プロパティは、バインディング モードの詳細と、バインディングの方向を指定する方法の例を提供します。

### <a name="what-triggers-source-updates"></a>ソース更新のトリガー

ターゲット プロパティの<xref:System.Windows.Data.BindingMode.TwoWay>変更<xref:System.Windows.Data.BindingMode.OneWayToSource>をリッスンしてソースに反映するバインディング (ソースの更新と呼ばれます)。 たとえば、TextBox のテキストを編集して、基になるソース値を変更できます。

ただし、テキストの編集中またはテキストの編集が終了してコントロールがフォーカスを失った後に、ソース値が更新されますか。 プロパティ<xref:System.Windows.Data.Binding.UpdateSourceTrigger?displayProperty=nameWithType>は、ソースの更新をトリガーする内容を決定します。 次の図の右矢印のドットは、プロパティの役割を<xref:System.Windows.Data.Binding.UpdateSourceTrigger?displayProperty=nameWithType>示しています。

![プロパティのロールを示す図。](./media/data-binding-overview/data-binding-updatesource-trigger.png)

値が`UpdateSourceTrigger`の<xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged?displayProperty=nameWithType>場合、右矢印<xref:System.Windows.Data.BindingMode.TwoWay>または<xref:System.Windows.Data.BindingMode.OneWayToSource>バインドによって示される値は、ターゲット プロパティが変更されるとすぐに更新されます。 ただし、値が`UpdateSourceTrigger`の<xref:System.Windows.Data.UpdateSourceTrigger.LostFocus>場合、ターゲット プロパティがフォーカスを失ったときに、その値は新しい値で更新されます。

プロパティと同様<xref:System.Windows.Data.Binding.Mode%2A>に、依存関係プロパティの既定値は異<xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A>なります。 ほとんどの依存関係プロパティの既定値は <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged> です。ただし、`TextBox.Text` プロパティの既定値は <xref:System.Windows.Data.UpdateSourceTrigger.LostFocus> です。 `PropertyChanged`ソースの更新は通常、ターゲット プロパティが変更されるたびに行われます。 瞬時の変更は、チェック ボックスやその他の簡単なコントロールに問題ありません。 ただし、テキストフィールドの場合、キーストロークのたびに更新するとパフォーマンスが低下し、新しい値にコミットする前にユーザーが入力エラーをバックスペースして修正する通常の機会を拒否します。

依存関係プロパティ<xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A>の既定値を検索する方法については、プロパティ ページを参照してください。

次の表は、 を例に<xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A>示<xref:System.Windows.Controls.TextBox>した各値のシナリオ例を示しています。

| UpdateSourceTrigger の値 | ソース値が更新された場合 | テキスト ボックスのシナリオ例 |
| ------------------------- | ---------------------------------- | ---------------------------- |
| `LostFocus`(デフォルトの<xref:System.Windows.Controls.TextBox.Text%2A?displayProperty=nameWithType>) | TextBox コントロールがフォーカスを失ったとき。 | 検証ロジックに関連付けられているテキスト ボックス (以下[のデータの検証を](#data-validation)参照)。 |
| `PropertyChanged` | に入力すると、 <xref:System.Windows.Controls.TextBox>. | チャット ルーム ウィンドウのテキスト ボックス コントロール。 |
| `Explicit` | アプリが呼び<xref:System.Windows.Data.BindingExpression.UpdateSource%2A>出すとき. | 編集可能なフォームの TextBox コントロール (ユーザーが送信ボタンをクリックした場合にのみソース値が更新されます)。 |

例については、「[方法 : TextBox テキストがソースを更新するタイミングを制御する」を](../../framework/wpf/data/how-to-control-when-the-textbox-text-updates-the-source.md)参照してください。

## <a name="creating-a-binding"></a>バインディングの作成

前のセクションで説明した概念の一部を再表示するには、オブジェクトを使用して<xref:System.Windows.Data.Binding>バインディングを確立し、各バインディングには、バインディング ターゲット、ターゲット プロパティ、バインディング ソース、および使用するソース値へのパスの 4 つのコンポーネントがあります。 このセクションでは、バインドの設定方法について説明します。

次の例について考えます。この例では、バインディング ソース オブジェクトは、*SDKSample* 名前空間で定義されている *MyData* という名前のクラスです。 MyData には、*MyData*デモンストレーション用に*ColorName*という名前の文字列プロパティがあり、その値は "赤" に設定されています。 したがって、この例では、背景が赤のボタンが生成されます。

[!code-xaml[BindNonTextProperty](~/samples/snippets/desktop-guide/wpf/data-binding-overview/csharp/AutoConvertPropertyToColor.xaml#BindAutoConvertColor)]

バインディング宣言の構文と、コードでバインディングを設定する方法の例の詳細については、「[バインディング宣言の概要](../../framework/wpf/data/binding-declarations-overview.md)」を参照してください。

この例を基本的な図に適用すると、結果として得られる図は、次のようになります。 この図は、Background<xref:System.Windows.Data.BindingMode.OneWay>プロパティが既定でバインディング<xref:System.Windows.Data.BindingMode.OneWay>をサポートしているため、バインディングについて説明しています。

![データ バインディングの背景プロパティを示す図。](./media/data-binding-overview/data-binding-button-background-example.png)

*ColorName*プロパティが文字列型であるのに、プロパティが型<xref:System.Windows.Controls.Control.Background%2A><xref:System.Windows.Media.Brush>である場合でも、なぜこのバインディングが機能するのか疑問に思うかもしれません。 このバインディングでは、データ変換のセクションで説明されている既定の型[変換](#data-conversion)を使用します。

### <a name="specifying-the-binding-source"></a>バインディング ソースの指定

前の例では、バインド ソースは[、DockPanel.DataContext](xref:System.Windows.FrameworkElement.DataContext)プロパティを設定して指定されていることに注意してください。 その<xref:System.Windows.Controls.Button>後、親要素<xref:System.Windows.FrameworkElement.DataContext%2A>である<xref:System.Windows.Controls.DockPanel>の値を継承します。 繰り返しますが、バインディング ソース オブジェクトは、バインディングの 4 つの必須コンポーネントの 1 つです。 したがって、バインディング ソース オブジェクトが指定されていないと、バインディングは機能しません。

バインディング ソース オブジェクトを指定するには複数の方法があります。 親要素<xref:System.Windows.FrameworkElement.DataContext%2A>でプロパティを使用すると、複数のプロパティを同じソースにバインドする場合に便利です。 ただし、個々のバインディング宣言でバインディング ソースを指定する方が適切な場合もあります。 前の例では、次の例のように<xref:System.Windows.FrameworkElement.DataContext%2A>、プロパティを使用する代わりに、ボタンのバインディング<xref:System.Windows.Data.Binding.Source%2A?displayProperty=nameWithType>宣言にプロパティを直接設定することでバインディング ソースを指定できます。

[!code-xaml[BindNonTextPropertyCompactBinding](~/samples/snippets/desktop-guide/wpf/data-binding-overview/csharp/AutoConvertPropertyToColor.xaml#BindAutoConvertColorCompactBinding)]

要素にプロパティを<xref:System.Windows.FrameworkElement.DataContext%2A>直接設定する以外に、先祖 (<xref:System.Windows.FrameworkElement.DataContext%2A>最初の例のボタンなど) から値を継承し、バインディングの<xref:System.Windows.Data.Binding.Source%2A?displayProperty=nameWithType>プロパティ (最後の例のボタンなど) を設定してバインディング ソースを明示的に指定する以外に、<xref:System.Windows.Data.Binding.ElementName?displayProperty=nameWithType>プロパティまたはプロパティを<xref:System.Windows.Data.Binding.RelativeSource?displayProperty=nameWithType>使用してバインディング ソースを指定することもできます。 この<xref:System.Windows.Data.Binding.ElementName%2A>プロパティは、スライダーを使用してボタンの幅を調整する場合など、アプリ内の他の要素にバインドする場合に便利です。 この<xref:System.Windows.Data.Binding.RelativeSource%2A>プロパティは、<xref:System.Windows.Controls.ControlTemplate>または でバインドが指定されている場合<xref:System.Windows.Style>に便利です。 詳細については、「[方法 : バインド ソースを指定する](../../framework/wpf/data/how-to-specify-the-binding-source.md)」を参照してください。

### <a name="specifying-the-path-to-the-value"></a>値へのパスの指定

バインディング ソースがオブジェクトの場合は、プロパティを<xref:System.Windows.Data.Binding.Path?displayProperty=nameWithType>使用して、バインディングに使用する値を指定します。 XML データにバインドする場合は、プロパティを<xref:System.Windows.Data.Binding.XPath?displayProperty=nameWithType>使用して値を指定します。 場合によっては、データが XML の場合でも<xref:System.Windows.Data.Binding.Path%2A>、このプロパティを使用できます。 たとえば、返された XmlNode の Name プロパティにアクセスする場合 (XPath クエリの結果として)、プロパティに<xref:System.Windows.Data.Binding.Path%2A>加えてプロパティを使用<xref:System.Windows.Data.Binding.XPath%2A>する必要があります。

詳細については、 および<xref:System.Windows.Data.Binding.Path%2A><xref:System.Windows.Data.Binding.XPath%2A>プロパティを参照してください。

使用<xref:System.Windows.Data.Binding.Path%2A>する値はバインディングの 4 つの必須コンポーネントの 1 つであることを強調しましたが、オブジェクト全体にバインドするシナリオでは、使用する値はバインディング ソース オブジェクトと同じになります。 そのような場合は、 を指定しない場合に適用<xref:System.Windows.Data.Binding.Path%2A>されます。 各データ メンバー フィールドが JSON オブジェクトにマップされ、フィールド名がオブジェクトの "key" 部分にマップされ、"value" 部分がオブジェクトの値の部分に再帰的にマップされます。

[!code-xaml[EmptyBinding](~/samples/snippets/desktop-guide/wpf/data-binding-overview/csharp/EmptyBinding.xaml#EmptyBinding)]

上記の例では、空のバインド構文 {Binding} を使用しています。 この場合、親の<xref:System.Windows.Controls.ListBox>DockPanel 要素から DataContext を継承します (この例では示されていません)。 パスが指定されていない場合、既定では、オブジェクト全体にバインドします。 つまり、この例では、<xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>プロパティをオブジェクト全体にバインドしているため、パスは取り残されています。 (詳細な説明については[、「コレクションへのバインド](#binding-to-collections)」セクションを参照してください。

コレクションにバインドする以外に、オブジェクトの 1 つのプロパティだけではなくオブジェクト全体にバインドするときにもこのシナリオは役立ちます。 たとえば、ソース オブジェクトが<xref:System.String>型の場合、文字列自体にバインドするだけの場合があります。 もう 1 つの一般的なシナリオは、要素をいくつかのプロパティを持つオブジェクトにバインドする場合です。

データがバインドされたターゲット プロパティに意味を持たるように、カスタム ロジックを適用する必要がある場合があります。 既定の型変換が存在しない場合、カスタム ロジックはカスタム コンバーターの形式になることがあります。 コンバーターについては、[データ変換](#data-conversion)を参照してください。

### <a name="binding-and-bindingexpression"></a>Binding と BindingExpression

データ バインディングの他の機能や使用方法に入る前に、<xref:System.Windows.Data.BindingExpression>クラスを導入しておくと便利です。 前のセクションで説明したように、<xref:System.Windows.Data.Binding>クラスはバインディングの宣言の上位クラスです。バインドの特性を指定できる多くのプロパティを提供します。 関連クラス 、<xref:System.Windows.Data.BindingExpression>は、ソースとターゲットの間の接続を維持する基になるオブジェクトです。 バインドには、複数のバインド式の間で共有できるすべての情報が含まれています。 A<xref:System.Windows.Data.BindingExpression>は、共有できないインスタンス式で、 のインスタンス情報をすべて含んでいます<xref:System.Windows.Data.Binding>。

次の例`myDataObject`では、`MyData`クラス`myBinding`のインスタンスがソース<xref:System.Windows.Data.Binding>オブジェクトであり`MyData`、という名前`MyDataProperty`の文字列プロパティを含む定義済みクラスであるとします。 この例では、 のインスタンス`myText`<xref:System.Windows.Controls.TextBlock>のテキスト コンテンツを`MyDataProperty`にバインドします。

[!code-csharp[CodeOnlyBinding](~/samples/snippets/desktop-guide/wpf/data-binding-overview/csharp/ManualBinding.cs#CodeOnlyBinding)]
[!code-vb[CodeOnlyBinding](~/samples/snippets/desktop-guide/wpf/data-binding-overview/vb/ManualBinding.vb#CodeOnlyBinding)]

同じ *myBinding* オブジェクトを使用して、他のバインディングを作成できます。 たとえば *、myBinding*オブジェクトを使用して、チェック ボックスのテキスト コンテンツを*MyDataProperty*にバインドできます。 このシナリオでは *、myBinding*オブジェクトを共有する<xref:System.Windows.Data.BindingExpression>2 つのインスタンスがあります。

オブジェクト<xref:System.Windows.Data.BindingExpression>は、データ バインド<xref:System.Windows.Data.BindingOperations.GetBindingExpression%2A>オブジェクトを呼び出すことによって返されます。 次の記事では、クラスの使用方法の一部<xref:System.Windows.Data.BindingExpression>を示します。

- [バインドされているターゲット プロパティからのバインディング オブジェクトの取得](../../framework/wpf/data/how-to-get-the-binding-object-from-a-bound-target-property.md)

- [コントロール テキスト ボックス テキストがソースを更新するとき](../../framework/wpf/data/how-to-control-when-the-textbox-text-updates-the-source.md)

## <a name="data-conversion"></a>データ変換

[[バインディングの作成](#creating-a-binding)] セクションでは、<xref:System.Windows.Controls.Control.Background%2A>プロパティが値 "Red" の文字列プロパティにバインドされているため、ボタンは赤になります。 この文字列値は、型コンバーターが文字列値を<xref:System.Windows.Media.Brush><xref:System.Windows.Media.Brush>に変換する型に存在するため、機能します。

この情報を図に追加[する バインディングの作成](#creating-a-binding)セクションは次のようになります。

![データ バインディング Default プロパティを示す図。](./media/data-binding-overview/data-binding-button-default-conversion.png)

ただし、文字列型のプロパティを持つ代わりに、バインド ソース オブジェクトに Color*型の*プロパティがある場合はどうでしょうか<xref:System.Windows.Media.Color>。 その場合、バインドを機能させるには、まず*Color*プロパティ値を<xref:System.Windows.Controls.Control.Background%2A>プロパティが受け入れるものに変換する必要があります。 次の例のように、<xref:System.Windows.Data.IValueConverter>インターフェイスを実装してカスタム コンバーターを作成する必要があります。

[!code-csharp[CodeOnlyBinding](~/samples/snippets/desktop-guide/wpf/data-binding-overview/csharp/ColorBrushConverter.cs#ColorBrushConverter)]
[!code-vb[CodeOnlyBinding](~/samples/snippets/desktop-guide/wpf/data-binding-overview/vb/ColorBrushConverter.vb#ColorBrushConverter)]

詳細については、「 <xref:System.Windows.Data.IValueConverter> 」を参照してください。

これで、既定の変換の代わりにカスタム コンバーターが使用され、図は次のようになります。

![データ バインディングのカスタム コンバーターを示す図。](./media/data-binding-overview/data-binding-converter-color-example.png)

繰り返しますが、バインドされている型に存在する型コンバーターにより、既定の変換が使用できます。 この動作は、ターゲットで利用可能な型コンバーターによって異なります。 独自のコンバーターを作成して、確認してみてください。

データ コンバーターを実装する場合の一般的なシナリオを次に示します。

- カルチャに応じてデータを異なる方法で表示する必要がある場合。 たとえば、特定のカルチャで使用される規則に基づいて、通貨コンバーターまたはカレンダーの日付/時刻コンバーターを実装する場合があります。

- 使用されているデータが必ずしもプロパティのテキスト値を変更することを意図しているわけではく、イメージのソースや表示テキストの色やスタイルなど、他のいくつかの値を変更することを意図している場合。 この場合、コンバーターを使用して、適切と思われないプロパティのバインディング (テキスト フィールドをテーブルのセルの Background プロパティにバインドするなど) を変換することができます。

- 複数のコントロールまたはコントロールの複数のプロパティが同じデータにバインドされています。 この場合、プライマリ バインドがテキストだけを表示する可能性があるのに対し、他のバインドは特定の表示に関する問題を処理しますが、同じバインドをソース情報として使用します。

- ターゲット プロパティには、バインディングのコレクションがあります<xref:System.Windows.Data.MultiBinding>。 の<xref:System.Windows.Data.MultiBinding>場合は、カスタム<xref:System.Windows.Data.IMultiValueConverter>を使用してバインディングの値から最終的な値を生成します。 たとえば、色は赤、青、および緑の値から計算できますが、これらは同じまたは異なるバインディング ソース オブジェクトからの値にすることができます。 例<xref:System.Windows.Data.MultiBinding>と情報については、「」を参照してください。

## <a name="binding-to-collections"></a>コレクションへのバインド

バインディング ソース オブジェクトは、プロパティにデータが含まれる単一のオブジェクトとして扱うか、多くの場合グループ化されるポリモーフィック オブジェクトのデータ コレクションとして扱うことができます (データベースへのクエリの結果など)。 ここまでは、単一のオブジェクトへのバインドについてのみ説明してきました。 ただし、データ コレクションへのバインドは一般的なシナリオです。 たとえば、一般的なシナリオとしては、、<xref:System.Windows.Controls.ItemsControl>データ の<xref:System.Windows.Controls.ListBox>バインド<xref:System.Windows.Controls.ListView>の内容<xref:System.Windows.Controls.TreeView>セクションに示されているアプリなど、データ コレクションを表示するために、 、、または などの[データ](#what-is-data-binding)コレクションを表示します。

幸い、基本的な図を引き続き使用できます。 をコレクション<xref:System.Windows.Controls.ItemsControl>にバインドする場合、図は次のようになります。

![データ バインディング ItemsControl オブジェクトを示す図。](./media/data-binding-overview/data-binding-itemscontrol.png)

この図に示すように、 を<xref:System.Windows.Controls.ItemsControl>コレクション オブジェクトにバインドするには<xref:System.Windows.Controls.ItemsControl.ItemsSource%2A?displayProperty=nameWithType>、プロパティを使用するプロパティです。 の内容`ItemsSource`と考えることができます<xref:System.Windows.Controls.ItemsControl>。 バインディングは、<xref:System.Windows.Data.BindingMode.OneWay>プロパティが`ItemsSource`既定で`OneWay`バインドをサポートしているためです。

### <a name="how-to-implement-collections"></a>コレクションの実装方法

インターフェイスを実装する任意のコレクションを<xref:System.Collections.IEnumerable>列挙できます。 ただし、コレクション内の挿入または削除によって UI が自動的に更新されるように動的バインディングを設定するには、コレクションにインターフェイスを実装<xref:System.Collections.Specialized.INotifyCollectionChanged>する必要があります。 このインターフェイスは、基になるコレクションが変更されたときに発生させるイベントを公開します。

WPF は<xref:System.Collections.ObjectModel.ObservableCollection%601>、インターフェイスを公開するデータ コレクションの組み込みの実装であるクラスを<xref:System.Collections.Specialized.INotifyCollectionChanged>提供します。 ソース オブジェクトからターゲットへのデータ値の転送を完全にサポートするには、バインド可能なプロパティをサポートするコレクション内の各<xref:System.ComponentModel.INotifyPropertyChanged>オブジェクトもインターフェイスを実装する必要があります。 詳しくは、[バインディング・ソースの概要を](../../framework/wpf/data/binding-sources-overview.md)参照してください。

独自のコレクションを実装する前に<xref:System.Collections.ObjectModel.ObservableCollection%601>、<xref:System.Collections.ObjectModel.Collection%601>などの<xref:System.ComponentModel.BindingList%601>既存のコレクション クラスの<xref:System.Collections.Generic.List%601>1 つを使用するか、その他の多くのコレクション クラスを使用することを検討してください。 高度なシナリオがあり、独自のコレクションを実装する場合は、インデックスによって<xref:System.Collections.IList>個別にアクセスできるオブジェクトの非ジェネリック コレクションを提供し、最適なパフォーマンスを提供する を使用することを検討してください。

### <a name="collection-views"></a>コレクション ビュー

データ<xref:System.Windows.Controls.ItemsControl>コレクションにバインドしたら、データの並べ替え、フィルタ処理、またはグループ化を行います。 そのためには、インターフェイスを実装するクラスであるコレクション ビューを<xref:System.ComponentModel.ICollectionView>使用します。

#### <a name="what-are-collection-views"></a>コレクション ビューとは

コレクション ビューは、基になるソース コレクション自体を変更することなく、並べ替え、フィルター、およびグループのクエリに基づくソース コレクションを移動および表示を可能にするバインディング ソース コレクションの上にある層です。 コレクション ビューには、コレクション内の現在の項目へのポインターも保持されます。 ソース コレクションがインターフェイスを実装<xref:System.Collections.Specialized.INotifyCollectionChanged>している場合、イベントによって発生した<xref:System.Collections.Specialized.INotifyCollectionChanged.CollectionChanged>変更はビューに反映されます。

ビューは基になるソース コレクションを変更しないため、各ソース コレクションは関連付けられた複数のビューを持つことができます。 たとえば、*Task* オブジェクトのコレクションを持つことができます。 ビューを使用すると、同じデータをさまざまな方法で表示できます。 たとえば、ページの左側に優先度で並べ替えられたタスクを表示し、右側に区分でグループ化されたタスクを表示できます。

#### <a name="how-to-create-a-view"></a>ビューの作成方法

ビューを作成して使用する方法の 1 つは、ビュー オブジェクトを直接インスタンス化して、それをバインディング ソースとして使用することです。 たとえば、「[データ バインディング][data-binding-demo]の説明」セクションに示されている[データ バインディング](#what-is-data-binding)デモ アプリを考えてみましょう。 アプリは、データ コレクションのビュー<xref:System.Windows.Controls.ListBox>に直接バインドするのではなく、データ コレクションにバインドするように実装されます。 次の例は、[データ バインディングデモ][data-binding-demo]アプリから抽出されます。 クラス<xref:System.Windows.Data.CollectionViewSource>は、 から<xref:System.Windows.Data.CollectionView>継承するクラスの XAML プロキシです。 この特定の例では、<xref:System.Windows.Data.CollectionViewSource.Source%2A>ビューのが現在のアプリ オブジェクトの (種類<xref:System.Collections.ObjectModel.ObservableCollection%601>の )*の AuctionItems*コレクションにバインドされています。

[!code-xaml[CollectionView](~/samples/snippets/desktop-guide/wpf/data-binding-overview/csharp/CollectionView.xaml#CollectionView)]

リソース*listingDataView*は、アプリ内の要素のバインディング ソースとして機能します<xref:System.Windows.Controls.ListBox>。

[!code-xaml[ListBoxCollectionView](~/samples/snippets/desktop-guide/wpf/data-binding-overview/csharp/CollectionView.xaml#ListBoxCollectionView)]

同じコレクションに別のビューを作成するには、別<xref:System.Windows.Data.CollectionViewSource>のインスタンスを作成して別`x:Key`の名前を付けます。

次の表は、既定のコレクション ビューとして、またはソース コレクション型<xref:System.Windows.Data.CollectionViewSource>に基づいて作成されるビュー データ型を示しています。

| ソース コレクションの型                    | コレクション ビューの型 | Notes |
| ----------------------------------------- | -------------------- | ----- |
| <xref:System.Collections.IEnumerable>     | ベースの内部型<xref:System.Windows.Data.CollectionView> | 項目のグループ化は不可 |
| <xref:System.Collections.IList>           | <xref:System.Windows.Data.ListCollectionView> | 最も高速 |
| <xref:System.ComponentModel.IBindingList> | <xref:System.Windows.Data.BindingListCollectionView> | |

#### <a name="using-a-default-view"></a>既定のビューを使用する

コレクション ビューを作成して使用する 1 つの方法は、バインディング ソースとしてコレクション ビューを指定することです。 WPF では、バインディング ソースとして使用されるすべてのコレクションに対して既定のコレクション ビューも作成されます。 コレクションに直接バインドすると、WPF はその既定のビューにバインドします。 この既定のビューは、同じコレクションに対するすべてのバインドで共有されるため、1 つのバインド されたコントロールまたはコードによって既定のビューに加えられた変更 (並べ替えや、後で説明する現在の項目ポインターへの変更など) は、同じコレクションに対する他のすべてのバインドに反映されます。

既定のビューを取得するには、 メソッド<xref:System.Windows.Data.CollectionViewSource.GetDefaultView%2A>を使用します。 例については、「データ[コレクションの既定のビューを取得する」を](../../framework/wpf/data/how-to-get-the-default-view-of-a-data-collection.md)参照してください。

#### <a name="collection-views-with-adonet-datatables"></a>ADO.NETデータテーブルを持つコレクション ビュー

パフォーマンスを向上させるために、ADO.NET<xref:System.Data.DataTable>または<xref:System.Data.DataView>オブジェクトのコレクション ビューは<xref:System.Data.DataView>、 に対して並べ替えとフィルター処理を委任します。 各コレクション ビューを個別に並べ替えおよびフィルター処理できるようにするには、各コレクション<xref:System.Data.DataView>ビューを独自のオブジェクトで初期化します。

#### <a name="sorting"></a>並べ替え

前述したように、ビューでは並べ替え順序をコレクションに適用できます。 これは基になるコレクション内に存在するため、データに関連性がない場合や、本来の順序ではない場合もあります。 コレクションのビューでは、指定する比較の基準に基づいて、順序を強制したり、既定の順序を変更することができます。 これはデータのクライアント ベースのビューであるため、一般的なシナリオは、ユーザーが列に対応する値ごとに表形式のデータの列を並べ替える場合です。 ビューを使用することで、このようなユーザー主導の並べ替えを適用することができます。この場合も、基になるコレクションを変更したり、コレクションのコンテンツにクエリを再実行する必要はありません。 例については、「[ヘッダーがクリックされたときに GridView 列を並べ替える](../../framework/wpf/controls/how-to-sort-a-gridview-column-when-a-header-is-clicked.md)」を参照してください。

次の例は、[[データ バインドの内容](#what-is-data-binding)] セクションで、アプリ<xref:System.Windows.Controls.CheckBox>UI の "カテゴリと日付で並べ替え" の並べ替えロジックを示しています。

[!code-csharp[AddSortChecked](~/samples/snippets/desktop-guide/wpf/data-binding-overview/csharp/CollectionView.xaml.cs#AddSortChecked)]
[!code-vb[AddSortChecked](~/samples/snippets/desktop-guide/wpf/data-binding-overview/vb/CollectionView.xaml.vb#AddSortChecked)]

#### <a name="filtering"></a>Filtering

ビューは、コレクションにフィルターを適用して、ビューにコレクション全体の特定のサブセットのみを表示するようにすることもできます。 データ内の条件をフィルターすることができます。 たとえば、[データ バインドの内容](#what-is-data-binding)セクションのアプリで行われるように、「バーゲンのみを表示」には<xref:System.Windows.Controls.CheckBox>、25 ドル以上のアイテムを除外するロジックが含まれています。 次のコードが実行され、イベント ハンドラーとして選択されている場合<xref:System.Windows.Data.CollectionViewSource.Filter><xref:System.Windows.Controls.CheckBox>に *、その*フィルターが設定されます。

[!code-csharp[ListingViewFilter](~/samples/snippets/desktop-guide/wpf/data-binding-overview/csharp/CollectionView.xaml.cs#ListingViewFilter)]
[!code-vb[ListingViewFilter](~/samples/snippets/desktop-guide/wpf/data-binding-overview/vb/CollectionView.xaml.vb#ListingViewFilter)]

*イベント*ハンドラには、次の実装があります。

[!code-csharp[FilterEvent](~/samples/snippets/desktop-guide/wpf/data-binding-overview/csharp/CollectionView.xaml.cs#FilterEvent)]
[!code-vb[FilterEvent](~/samples/snippets/desktop-guide/wpf/data-binding-overview/vb/CollectionView.xaml.vb#FilterEvent)]

クラスの 1 つを直接<xref:System.Windows.Data.CollectionView><xref:System.Windows.Data.CollectionViewSource>使用する場合は、 プロパティを<xref:System.Windows.Data.CollectionView.Filter%2A>使用してコールバックを指定します。 例については、「[ビュー内のデータをフィルター処理する](../../framework/wpf/data/how-to-filter-data-in-a-view.md)」を参照してください。

#### <a name="grouping"></a>グループ化

<xref:System.Collections.IEnumerable>コレクションを表示する内部クラスを除き、すべてのコレクション ビューでは*グループ化*がサポートされており、ユーザーはコレクション ビュー内のコレクションを論理グループに分割できます。 グループは、明示的 (ユーザーがグループの一覧を提供する) または暗黙的 (グループがデータに応じて動的に生成される) にすることができます。

次の例は、"カテゴリごとにグループ化"<xref:System.Windows.Controls.CheckBox>のロジックを示しています。

[!code-csharp[ListingGroupCheck](~/samples/snippets/desktop-guide/wpf/data-binding-overview/csharp/CollectionView.xaml.cs#ListingGroupCheck)]
[!code-vb[ListingGroupCheck](~/samples/snippets/desktop-guide/wpf/data-binding-overview/vb/CollectionView.xaml.vb#ListingGroupCheck)]

別のグループ化の例については、「[GridView を実装する ListView の項目をグループ化する](../../framework/wpf/controls/how-to-group-items-in-a-listview-that-implements-a-gridview.md)」を参照してください。

#### <a name="current-item-pointers"></a>現在のアイテム のポインター

ビューでは、現在の項目の概念もサポートされています。 コレクション ビュー内のオブジェクト間を移動することができます。 移動するときに、項目のポインターを動かすことで、コレクション内の特定の場所に存在するオブジェクトを取得できます。 例については、「[データのコレクションビュー内のオブジェクト間を移動する](../../framework/wpf/data/how-to-navigate-through-the-objects-in-a-data-collectionview.md)」を参照してください。

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

現在の項目のポインターは、コレクションに適用されている任意の並べ替えまたはフィルター処理の影響を受ける場合があります。 並べ替えは、現在の項目のポインターを最後に選択した項目に保持しますが、コレクション ビューはそれを中心に再構築されています  (選択した項目は以前はリストの先頭にあったかもしれませんが、選択した項目が途中にある可能性があります)。フィルター処理では、選択したアイテムがフィルター処理後もビューに残っている場合、そのアイテムは保持されます。 それ以外の場合は、現在の項目のポインターが、フィルター処理されたコレクション ビューの最初の項目に設定されます。

#### <a name="master-detail-binding-scenario"></a>マスター/詳細バインドシナリオ

現在の項目の概念は、コレクション内の項目間の移動に役立つだけでなく、マスターと詳細のバインディング シナリオにも役立ちます。 もう一度、「データ[バインディングの内容](#what-is-data-binding)」セクションでアプリの UI を検討してください。 そのアプリでは、 内<xref:System.Windows.Controls.ListBox>の選択によって、 に表示される<xref:System.Windows.Controls.ContentControl>コンテンツが決定されます。 別の方法で言うと、項目が<xref:System.Windows.Controls.ListBox>選択されている場合、選択<xref:System.Windows.Controls.ContentControl>した項目の詳細が 表示されます。

同じビューにバインドされた 2 つ以上のコントロールがあるだけで、マスターと詳細のシナリオを実装できます。 次の例では[、データ バインドのデモ][data-binding-demo]では、アプリ<xref:System.Windows.Controls.ListBox>UI<xref:System.Windows.Controls.ContentControl>の の マークアップと、 [[データ バインドの内容](#what-is-data-binding)] セクションに表示されます。

[!code-xaml[ListBoxContentControl](~/samples/snippets/desktop-guide/wpf/data-binding-overview/csharp/CollectionView.xaml#ListBoxContentControl)]

両方のコントロールが同じソース *、listingDataView*静的リソースにバインドされていることに注意してください (「[ビューを作成する方法」セクション](#how-to-create-a-view)でこのリソースの定義を参照してください)。 このバインディングは、シングルトン オブジェクト (<xref:System.Windows.Controls.ContentControl>この場合は) がコレクション ビューにバインドされると、ビューの に<xref:System.Windows.Data.CollectionView.CurrentItem%2A>自動的にバインドされるために機能します。 オブジェクト<xref:System.Windows.Data.CollectionViewSource>は、通貨と選択を自動的に同期します。 この例のようにリスト コントロールが<xref:System.Windows.Data.CollectionViewSource>オブジェクトにバインドされていない場合は、この機能を実現するために、その<xref:System.Windows.Controls.Primitives.Selector.IsSynchronizedWithCurrentItem%2A>プロパティを`true`に設定する必要があります。

その他の例については、「[コレクションにバインドして選択に基づいて情報を表示](../../framework/wpf/data/how-to-bind-to-a-collection-and-display-information-based-on-selection.md)する」および「[階層データでマスター/詳細パターンを使用](../../framework/wpf/data/how-to-use-the-master-detail-pattern-with-hierarchical-data.md)する」を参照してください。

上記の例では、テンプレートが使用されています。 実際、テンプレート (によって明示的に使用されたもの、および で暗黙的に使用される テンプレート) を<xref:System.Windows.Controls.ContentControl>使用しないと、データは<xref:System.Windows.Controls.ListBox>望むように表示されません。 次のセクションで、データ テンプレートについて説明します。

## <a name="data-templating"></a>データ テンプレート

データ テンプレートを使用しない場合は、「[データ バインドの説明](#what-is-data-binding)」セクションのアプリ UI は次のようになります。

![データ テンプレートのないデータ バインディング デモ](./media/data-binding-overview/demo-no-template.png)

前のセクションの例に示すように、<xref:System.Windows.Controls.ListBox>コントロールと の<xref:System.Windows.Controls.ContentControl>両方が *、AuctionItem*s のコレクション オブジェクト全体 (つまり、コレクション オブジェクトのビュー) にバインドされています。 データ コレクションの表示方法に関する具体的な指示<xref:System.Windows.Controls.ListBox>がない場合は、基になるコレクション内の各オブジェクトの文字列表現<xref:System.Windows.Controls.ContentControl>が表示され、バインドされているオブジェクトの文字列表現が 表示されます。

この問題を解決するために、アプリは<xref:System.Windows.DataTemplate?text=DataTemplates>を定義します。 前のセクションの例に示すように、明示的<xref:System.Windows.Controls.ContentControl>に*詳細製品リストテンプレート テンプレートを*使用します。 コントロール<xref:System.Windows.Controls.ListBox>は、コレクション内の*AuctionItem*オブジェクトを表示するときに、次のデータ テンプレートを暗黙的に使用します。

[!code-xaml[AuctionItemDataTemplate](~/samples/snippets/desktop-guide/wpf/data-binding-overview/csharp/CollectionView.xaml#AuctionItemDataTemplate)]

これら 2 つの DataTemplates を使用すると、結果の UI は[「データ バインディングの意味](#what-is-data-binding)」セクションに示す UI です。 このスクリーンショットからわかるように、DataTemplates を使用すると、データをコントロールに配置できるだけでなく、データの魅力的なビジュアルを定義できます。 たとえば、上<xref:System.Windows.DataTrigger>の例<xref:System.Windows.DataTemplate>では、*特殊*機能値が*HighLight*の*オークションアイテム*がオレンジ色の境界線と星で表示されるように、s を使用します。

データ テンプレートの詳細については、「[データ テンプレートの概要](../../framework/wpf/data/data-templating-overview.md)」を参照してください。

## <a name="data-validation"></a>データ検証

ユーザー入力を受け取るほとんどのアプリは、ユーザーが予期した情報を入力したことを確認するための検証ロジックを持っている必要があります。 検証チェックは、種類、範囲、形式、またはその他のアプリ固有の要件に基づいて行うことができます。 このセクションでは、WPF でのデータの検証のしくみについて説明します。

### <a name="associating-validation-rules-with-a-binding"></a>検証規則とバインディングの関連付け

WPF データ バインド モデルを使用<xref:System.Windows.Data.Binding.ValidationRules%2A>すると、<xref:System.Windows.Data.Binding>オブジェクトに関連付けることができます。 たとえば、次の例では、 を<xref:System.Windows.Controls.TextBox>という名前`StartPrice`のプロパティにバインドし<xref:System.Windows.Controls.ExceptionValidationRule>、プロパティに<xref:System.Windows.Data.Binding.ValidationRules%2A?displayProperty=nameWithType>オブジェクトを追加します。

[!code-xaml[TextboxStartPrice](~/samples/snippets/desktop-guide/wpf/data-binding-overview/csharp/DataValidation.xaml#TextboxStartPrice)]

オブジェクト<xref:System.Windows.Controls.ValidationRule>は、プロパティの値が有効かどうかをチェックします。 WPF には、次の 2<xref:System.Windows.Controls.ValidationRule>種類の組み込みオブジェクトがあります。

- バインディング<xref:System.Windows.Controls.ExceptionValidationRule>ソース プロパティの更新中にスローされた例外をチェックします。 前述の例では、`StartPrice` は整数型です。 ユーザーが整数に変換できない値を入力すると、例外がスローされ、バインディングが無効としてマークされます。 明示的に設定する別の<xref:System.Windows.Controls.ExceptionValidationRule><xref:System.Windows.Data.Binding.ValidatesOnExceptions%2A>構文は、`true`プロパティ<xref:System.Windows.Data.Binding><xref:System.Windows.Data.MultiBinding>をまたはオブジェクトに設定することです。

- オブジェクト<xref:System.Windows.Controls.DataErrorValidationRule>は、インターフェイスを実装するオブジェクトによって発生するエラーを<xref:System.ComponentModel.IDataErrorInfo>チェックします。 この検証規則の使用例については、を参照してください<xref:System.Windows.Controls.DataErrorValidationRule>。 明示的に設定する別の<xref:System.Windows.Controls.DataErrorValidationRule><xref:System.Windows.Data.Binding.ValidatesOnDataErrors%2A>構文は、`true`プロパティ<xref:System.Windows.Data.Binding><xref:System.Windows.Data.MultiBinding>をまたはオブジェクトに設定することです。

クラスから派生してメソッドを実装することで、独自の<xref:System.Windows.Controls.ValidationRule>検証規則を<xref:System.Windows.Controls.ValidationRule.Validate%2A>作成することもできます。 次の例は、[[データ バインディング](#what-is-data-binding)とは] セクションの *[製品リストの追加*] "開始日" で<xref:System.Windows.Controls.TextBox>使用されるルールを示しています。

[!code-csharp[FutureDateRule](~/samples/snippets/desktop-guide/wpf/data-binding-overview/csharp/FutureDateRule.cs#FutureDateRule)]
[!code-vb[FutureDateRule](~/samples/snippets/desktop-guide/wpf/data-binding-overview/vb/FutureDateRule.vb#FutureDateRule)]

次の例に示すように、*この*<xref:System.Windows.Controls.TextBox> *FutureDateRule*を使用します。

[!code-xaml[TextboxStartDate](~/samples/snippets/desktop-guide/wpf/data-binding-overview/csharp/DataValidation.xaml#TextboxStartDate)]

<xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A>値は であるため<xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>、バインディング エンジンは、キーストロークごとにソース値を更新します<xref:System.Windows.Data.Binding.ValidationRules%2A>。 これについては、「検証プロセス」セクションで詳しく説明します。

### <a name="providing-visual-feedback"></a>視覚的なフィードバックを提供する

ユーザーが無効な値を入力した場合は、アプリの UI でエラーに関するフィードバックを提供する必要があります。 このようなフィードバックを提供する 1 つの方法<xref:System.Windows.Controls.Validation.ErrorTemplate%2A?displayProperty=nameWithType>は、添付プロパティを<xref:System.Windows.Controls.ControlTemplate>カスタム に設定することです。 前のサブセクションに示したように *、StartDateEntryForm は*<xref:System.Windows.Controls.TextBox>呼<xref:System.Windows.Controls.Validation.ErrorTemplate%2A>び出された*検証テンプレート*を使用します。 次の例は、*検証*テンプレートの定義を示しています。

[!code-xaml[ControlTemplate](~/samples/snippets/desktop-guide/wpf/data-binding-overview/csharp/DataValidation.xaml#ControlTemplate)]

要素<xref:System.Windows.Controls.AdornedElementPlaceholder>は、装飾されるコントロールを配置する場所を指定します。

また、 を<xref:System.Windows.Controls.ToolTip>使用してエラー メッセージを表示することもできます。 *エラー*<xref:System.Windows.Controls.TextBox>メッセージを表示するスタイルテキスト*StartPriceEntryForm**スタイルテキスト ボックス*を<xref:System.Windows.Controls.ToolTip>使用します。 次の例は、*textStyleTextBox* の定義を示します。 添付プロパティ<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>は、`true`バインドされた要素のプロパティの 1 つ以上のバインドがエラーの場合です。

[!code-xaml[TextBoxStyle](~/samples/snippets/desktop-guide/wpf/data-binding-overview/csharp/DataValidation.xaml#TextBoxStyle)]

カスタム<xref:System.Windows.Controls.Validation.ErrorTemplate%2A>と、<xref:System.Windows.Controls.ToolTip>では、検証エラーが発生すると *、StartDateEntryForm*<xref:System.Windows.Controls.TextBox>は次のようになります。

![データ バインディング検証エラー](./media/data-binding-overview/demo-validation-date.png "DataBindingDemo_Validation")

関連付<xref:System.Windows.Data.Binding>けられた検証規則があるが、バインド されたコントロール<xref:System.Windows.Controls.Validation.ErrorTemplate%2A>で を指定しない場合は<xref:System.Windows.Controls.Validation.ErrorTemplate%2A>、検証エラーが発生したときにユーザーに通知する既定値が使用されます。 既定値<xref:System.Windows.Controls.Validation.ErrorTemplate%2A>は、装飾レイヤの赤い枠線を定義するコントロール テンプレートです。 既定<xref:System.Windows.Controls.Validation.ErrorTemplate%2A>と、<xref:System.Windows.Controls.ToolTip>では、検証エラーが発生すると *、StartPriceEntryForm*<xref:System.Windows.Controls.TextBox>の UI は次のようになります。

![データ バインディング検証エラー](./media/data-binding-overview/demo-validation-price.png "DataBindingDemo_ValidationDefault")

ダイアログ ボックスのすべてのコントロールを検証するロジックを提供する方法の例については、[ダイアログ ボックスの概要](../../framework/wpf/app-development/dialog-boxes-overview.md)の「カスタム ダイアログ ボックス」セクションを参照してください。

### <a name="validation-process"></a>検証プロセス

検証は通常、ターゲットの値がバインディング ソースのプロパティに転送されるときに発生します。 この転送は、バインディング<xref:System.Windows.Data.BindingMode.TwoWay>と<xref:System.Windows.Data.BindingMode.OneWayToSource>で行われます。 繰り返しになりますが、ソースの更新の原因は、「ソース<xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A>の更新を[トリガーするもの](#what-triggers-source-updates)」セクションで説明されているように、プロパティの値によって異なります。

次の項目は *、検証*プロセスについて説明します。 このプロセスの間に検証エラーまたはその他の種類のエラーが発生した場合、プロセスは停止します。

1. バインディング エンジンは、そのオブジェクトに設定<xref:System.Windows.Controls.ValidationRule><xref:System.Windows.Controls.ValidationRule.ValidationStep%2A><xref:System.Windows.Controls.ValidationStep.RawProposedValue><xref:System.Windows.Data.Binding>されているカスタム オブジェクトが定義されているかどうかをチェックします<xref:System.Windows.Controls.ValidationRule.Validate%2A><xref:System.Windows.Controls.ValidationRule>。

2. その後、バインディング エンジンがコンバーターを呼び出します (ある場合)。

3. コンバーター<xref:System.Windows.Controls.ValidationRule>が成功すると、バインディング エンジンは、そのオブジェクトに設定<xref:System.Windows.Controls.ValidationRule.ValidationStep%2A><xref:System.Windows.Controls.ValidationStep.ConvertedProposedValue><xref:System.Windows.Data.Binding>されているカスタム オブジェクトが定義されているかどうかをチェックします。 <xref:System.Windows.Controls.ValidationRule.Validate%2A> <xref:System.Windows.Controls.ValidationRule> <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> <xref:System.Windows.Controls.ValidationStep.ConvertedProposedValue>

4. バインディング エンジンは、ソース プロパティを設定します。

5. バインディング エンジンは、そのオブジェクトに設定<xref:System.Windows.Controls.ValidationRule><xref:System.Windows.Controls.ValidationRule.ValidationStep%2A><xref:System.Windows.Controls.ValidationStep.UpdatedValue><xref:System.Windows.Data.Binding>されているカスタム オブジェクトが定義されているかどうかをチェックします<xref:System.Windows.Controls.ValidationRule.Validate%2A><xref:System.Windows.Controls.ValidationRule><xref:System.Windows.Controls.ValidationRule.ValidationStep%2A><xref:System.Windows.Controls.ValidationStep.UpdatedValue>。 が<xref:System.Windows.Controls.DataErrorValidationRule>バインドに関連付けられており、その<xref:System.Windows.Controls.ValidationRule.ValidationStep%2A>バインドがデフォルトに設定されている<xref:System.Windows.Controls.ValidationStep.UpdatedValue>場合は<xref:System.Windows.Controls.DataErrorValidationRule>、 がこの時点でチェックされます。 この時点で、セットを持つ<xref:System.Windows.Data.Binding.ValidatesOnDataErrors%2A>すべてのバインディング`true`がチェックされます。

6. バインディング エンジンは、そのオブジェクトに設定<xref:System.Windows.Controls.ValidationRule><xref:System.Windows.Controls.ValidationRule.ValidationStep%2A><xref:System.Windows.Controls.ValidationStep.CommittedValue><xref:System.Windows.Data.Binding>されているカスタム オブジェクトが定義されているかどうかをチェックします<xref:System.Windows.Controls.ValidationRule.Validate%2A><xref:System.Windows.Controls.ValidationRule><xref:System.Windows.Controls.ValidationRule.ValidationStep%2A><xref:System.Windows.Controls.ValidationStep.CommittedValue>。

このプロセス<xref:System.Windows.Controls.ValidationRule>を通じて a が渡されない場合、バインディング エンジンは<xref:System.Windows.Controls.ValidationError>オブジェクトを作成し、バインド<xref:System.Windows.Controls.Validation.Errors%2A?displayProperty=nameWithType>された要素のコレクションに追加します。 バインディング エンジンは、特定<xref:System.Windows.Controls.ValidationRule>のステップでオブジェクトを実行する前に、<xref:System.Windows.Controls.ValidationError>そのステップの間に<xref:System.Windows.Controls.Validation.Errors%2A?displayProperty=nameWithType>バインドされた要素の添付プロパティに追加されたオブジェクトを削除します。 たとえば、失敗に設定<xref:System.Windows.Controls.ValidationRule>されている<xref:System.Windows.Controls.ValidationRule.ValidationStep%2A>a<xref:System.Windows.Controls.ValidationStep.UpdatedValue>が次に検証プロセスが発生したときに、バインド<xref:System.Windows.Controls.ValidationError>エンジンは<xref:System.Windows.Controls.ValidationRule><xref:System.Windows.Controls.ValidationRule.ValidationStep%2A>、 に設定されているを呼び出す直前にそのを<xref:System.Windows.Controls.ValidationStep.UpdatedValue>削除します。

空<xref:System.Windows.Controls.Validation.Errors%2A?displayProperty=nameWithType>でない場合、要素の<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>添付プロパティは`true`に設定されます。 また、 の<xref:System.Windows.Data.Binding.NotifyOnValidationError%2A>プロパティ<xref:System.Windows.Data.Binding>が に`true`設定されている場合、バインディング エンジンは、要素<xref:System.Windows.Controls.Validation.Error?displayProperty=nameWithType>に添付イベントを発生させます。

また、有効な値の転送方向 (ソースからソースへのターゲット) は、添付プロパティを<xref:System.Windows.Controls.Validation.Errors%2A?displayProperty=nameWithType>クリアすることに注意してください。

バインディングに<xref:System.Windows.Controls.ExceptionValidationRule>関連付けられているか、<xref:System.Windows.Data.Binding.ValidatesOnExceptions%2A>プロパティが設定され、バインディング エンジンがソース`true`を設定したときに例外がスローされた場合、バインディング エンジンは<xref:System.Windows.Data.Binding.UpdateSourceExceptionFilter%2A>. コールバックを使用して、例外を<xref:System.Windows.Data.Binding.UpdateSourceExceptionFilter%2A>処理するためのカスタム ハンドラーを提供するオプションがあります。 で<xref:System.Windows.Data.Binding.UpdateSourceExceptionFilter%2A><xref:System.Windows.Data.Binding>を指定しない場合、バインド エンジンは例外を<xref:System.Windows.Controls.ValidationError>持つ を作成し、バインド<xref:System.Windows.Controls.Validation.Errors%2A?displayProperty=nameWithType>された要素のコレクションに追加します。

## <a name="debugging-mechanism"></a>デバッグメカニズム

バインド関連オブジェクトの添付プロパティ<xref:System.Diagnostics.PresentationTraceSources.TraceLevel%2A?displayProperty=nameWithType>を設定して、特定のバインディングの状態に関する情報を受け取ることができます。

## <a name="see-also"></a>関連項目

- <xref:System.Windows.Controls.DataErrorValidationRule>
- [LINQ クエリの結果にバインドする](../../framework/wpf/data/how-to-bind-to-the-results-of-a-linq-query.md)
- [データ バインディング](../../framework/wpf/advanced/optimizing-performance-data-binding.md)
- [データ バインディングのデモ][data-binding-demo]
- [ハウツー記事](../../framework/wpf/data/data-binding-how-to-topics.md)
- [ADO.NET データ ソースにバインドする](../../framework/wpf/data/how-to-bind-to-an-ado-net-data-source.md)

[data-binding-demo]: https://github.com/microsoft/WPF-Samples/tree/master/Sample%20Applications/DataBindingDemo "データ バインド デモ アプリ"
