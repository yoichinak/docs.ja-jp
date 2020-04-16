---
title: スタイルとテンプレート
description: NET コアの Windows プレゼンテーション ファンデーション (WPF) の XAML リソースについて説明します。 スタイルとテーマに関連する XAML リソースの種類を理解する。
author: thraka
ms.author: adegeo
ms.date: 09/09/2019
dev_langs:
- csharp
- vb
ms.openlocfilehash: f845e739ec3cae502d1e4fd6631f987c5364a42e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "81433098"
---
# <a name="styles-and-templates-in-wpf"></a>WPF のスタイルとテンプレート

Windows プレゼンテーション ファンデーション (WPF) のスタイルとテンプレートは、開発者とデザイナーが視覚的に説得力のある効果と製品の一貫した外観を作成できるようにする一連の機能を指します。 アプリの外観をカスタマイズする場合は、アプリ内およびアプリ間で外観のメンテナンスと共有を可能にする強力なスタイルとテンプレート モデルが必要です。 WPF はそのモデルを提供します。

WPF スタイル モデルのもう 1 つの機能は、プレゼンテーションとロジックの分離です。 デザイナーは、開発者が C# または Visual Basic を使用してプログラミング ロジックを操作するのと同時に XAML のみを使用して、アプリの外観を操作できます。

この概要では、アプリのスタイル設定とテンプレートの側面に焦点を当て、データ バインディングの概念については説明しません。 データ バインディングの詳細については、「[データ バインディングの概要](../data/data-binding-overview.md)」を参照してください。

スタイルとテンプレートを再利用できるようにするリソースを理解することが重要です。 リソースの詳細については、「[XAML Resources](xaml-resources-define.md)」を参照してください。

[!INCLUDE [desktop guide under construction](../../../includes/desktop-guide-preview-note.md)]

## <a name="sample"></a>サンプル

この概要で提供されるサンプル コードは、次の図に示す[単純な写真参照アプリケーション](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating)に基づいています。

![スタイル設定された ListView](./media/styles-and-templates-overview/stylingintro-triggers.png "StylingIntro_triggers")

この単純な写真のサンプルは、スタイルとテンプレートを使用して、視覚的に説得力のあるユーザー エクスペリエンスを作成します。 サンプルには 2<xref:System.Windows.Controls.TextBlock>つの要素<xref:System.Windows.Controls.ListBox>と、イメージのリストにバインドされたコントロールがあります。

完全なサンプルについては、「[Introduction to Styling and Templating Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating)」を参照してください。

## <a name="styles"></a>スタイル

プロパティ<xref:System.Windows.Style>値のセットを複数の要素に適用する便利な方法と考えることができます。 <xref:System.Windows.FrameworkElement>スタイルは、 または<xref:System.Windows.FrameworkContentElement>など<xref:System.Windows.Window>から派生する任意の要素に対して<xref:System.Windows.Controls.Button>使用できます。

スタイルを宣言する最も一般的な方法は、XAML`Resources`ファイルのセクション内のリソースとして使用することです。 スタイルはリソースであるため、すべてのリソースに適用されるのと同じスコープルールに従います。 簡単に言うと、スタイルを宣言する場所は、スタイルを適用できる場所に影響します。 たとえば、アプリ定義 XAML ファイルのルート要素でスタイルを宣言すると、アプリ内の任意の場所でスタイルを使用できます。

たとえば、次の XAML コードでは、1 つの`TextBlock`スタイルが自動的`TextBlock`にすべての要素に適用され、もう 1 つは明示的に参照する必要があります。

[!code-xaml[SnippetDefaultTextBlockStyleBasedOn](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/csharp/Window2.xaml#SnippetDefaultTextBlockStyleBasedOn)]

上で宣言したスタイルの例を次に示します。

[!code-xaml[SnippetTextBlocksExplicit](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/csharp/Window2.xaml#SnippetTextBlocksExplicit)]

![スタイル付きのテキストブロック](./media/styles-and-templates-overview/stylingintro-textblocks.png)

詳細については、「[コントロールのスタイルを作成する」を](styles-templates-create-apply-style.md)参照してください。

## <a name="controltemplates"></a>ControlTemplate

WPF では、<xref:System.Windows.Controls.ControlTemplate>コントロールの コントロールの外観が定義されます。 新しい<xref:System.Windows.Controls.ControlTemplate>コントロールを定義してコントロールに割り当てることで、コントロールの構造と外観を変更できます。 多くの場合、テンプレートは十分な柔軟性を提供するため、独自のカスタム コントロールを作成する必要はありません。

各コントロールには[、Control.Template](xref:System.Windows.Controls.Control.Template)プロパティに割り当てられた既定のテンプレートがあります。 テンプレートは、コントロールのビジュアル プレゼンテーションとコントロールの機能を結び付けます。 XAML でテンプレートを定義するため、コードを記述せずにコントロールの外観を変更できます。 各テンプレートは、 など、特定のコントロール用に<xref:System.Windows.Controls.Button>設計されています。

通常、テンプレートは XAML ファイルのセクション`Resources`でリソースとして宣言します。 すべてのリソースと同様に、スコープルールが適用されます。

コントロール テンプレートは、スタイルよりも多くの関係があります。 これは、コントロール テンプレートがコントロール全体の外観を書き換える一方で、スタイルは単に既存のコントロールにプロパティの変更を適用するためです。 ただし[、Control.Template](xref:System.Windows.Controls.Control.Template)プロパティを設定してコントロールのテンプレートを適用するため、スタイルを使用してテンプレートを定義または設定できます。

通常、デザイナーでは既存のテンプレートのコピーを作成して変更できます。 たとえば、Visual Studio WPF デザイナーでコントロールを`CheckBox`選択し、右クリックして [**テンプレート** > の編集] を**選択します。** このコマンドは、*テンプレートを定義するスタイルを*生成します。

```xaml
<Style x:Key="CheckBoxStyle1" TargetType="{x:Type CheckBox}">
    <Setter Property="FocusVisualStyle" Value="{StaticResource FocusVisual1}"/>
    <Setter Property="Background" Value="{StaticResource OptionMark.Static.Background1}"/>
    <Setter Property="BorderBrush" Value="{StaticResource OptionMark.Static.Border1}"/>
    <Setter Property="Foreground" Value="{DynamicResource {x:Static SystemColors.ControlTextBrushKey}}"/>
    <Setter Property="BorderThickness" Value="1"/>
    <Setter Property="Template">
        <Setter.Value>
            <ControlTemplate TargetType="{x:Type CheckBox}">
                <Grid x:Name="templateRoot" Background="Transparent" SnapsToDevicePixels="True">
                    <Grid.ColumnDefinitions>
                        <ColumnDefinition Width="Auto"/>
                        <ColumnDefinition Width="*"/>
                    </Grid.ColumnDefinitions>
                    <Border x:Name="checkBoxBorder" Background="{TemplateBinding Background}" BorderThickness="{TemplateBinding BorderThickness}" BorderBrush="{TemplateBinding BorderBrush}" HorizontalAlignment="{TemplateBinding HorizontalContentAlignment}" Margin="1" VerticalAlignment="{TemplateBinding VerticalContentAlignment}">
                        <Grid x:Name="markGrid">
                            <Path x:Name="optionMark" Data="F1 M 9.97498,1.22334L 4.6983,9.09834L 4.52164,9.09834L 0,5.19331L 1.27664,3.52165L 4.255,6.08833L 8.33331,1.52588e-005L 9.97498,1.22334 Z " Fill="{StaticResource OptionMark.Static.Glyph1}" Margin="1" Opacity="0" Stretch="None"/>
                            <Rectangle x:Name="indeterminateMark" Fill="{StaticResource OptionMark.Static.Glyph1}" Margin="2" Opacity="0"/>
                        </Grid>
                    </Border>
                    <ContentPresenter x:Name="contentPresenter" Grid.Column="1" Focusable="False" HorizontalAlignment="{TemplateBinding HorizontalContentAlignment}" Margin="{TemplateBinding Padding}" RecognizesAccessKey="True" SnapsToDevicePixels="{TemplateBinding SnapsToDevicePixels}" VerticalAlignment="{TemplateBinding VerticalContentAlignment}"/>
                </Grid>
                <ControlTemplate.Triggers>
                    <Trigger Property="HasContent" Value="true">
                        <Setter Property="FocusVisualStyle" Value="{StaticResource OptionMarkFocusVisual1}"/>
                        <Setter Property="Padding" Value="4,-1,0,0"/>

... content removed to save space ...
```

テンプレートのコピーを編集すると、テンプレートの動作を理解できます。 新しい空のテンプレートを作成する代わりに、コピーを編集し、ビジュアル プレゼンテーションのいくつかの側面を変更する方が簡単です。

例については、「[コントロールのテンプレートを作成する](../themes/how-to-create-apply-template.md)」を参照してください。

### <a name="templatebinding"></a>TemplateBinding

前のセクションで定義したテンプレート リソースで[TemplateBinding マークアップ拡張機能](../../framework/wpf/advanced/templatebinding-markup-extension.md)が使用されていることがわかります。 A`TemplateBinding`は、テンプレート シナリオ用のバインディングの最適化された形式で、 で`{Binding RelativeSource={RelativeSource TemplatedParent}}`作成されたバインディングに似ています。 `TemplateBinding`は、テンプレートの一部をコントロールのプロパティにバインドする場合に便利です。 たとえば、各コントロールにはプロパティがあります<xref:System.Windows.Controls.Control.BorderThickness>。 テンプレート内`TemplateBinding`のどの要素がこのコントロール設定の影響を受けるかを管理するには、 を使用します。

### <a name="contentcontrol-and-itemscontrol"></a>コンテンツ コントロールとアイテム コントロール

の<xref:System.Windows.Controls.ContentPresenter>で<xref:System.Windows.Controls.ControlTemplate><xref:System.Windows.Controls.ContentControl>a が宣言されている場合<xref:System.Windows.Controls.ContentPresenter>、 は、<xref:System.Windows.Controls.ContentControl.ContentTemplate%2A>プロパティ<xref:System.Windows.Controls.ContentControl.Content%2A>と プロパティに自動的にバインドされます。 同様に、<xref:System.Windows.Controls.ItemsPresenter>のに含まれる<xref:System.Windows.Controls.ControlTemplate>の<xref:System.Windows.Controls.ItemsControl>は、 プロパティと<xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A><xref:System.Windows.Controls.ItemsControl.Items%2A>プロパティに自動的にバインドされます。

## <a name="datatemplates"></a>データテンプレート

このサンプル アプリでは、写真の<xref:System.Windows.Controls.ListBox>一覧にバインドされたコントロールがあります。

[!code-xaml[ListBox](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/csharp/Window3.xaml#SnippetListBox)]

これは<xref:System.Windows.Controls.ListBox>現在、次のようになります。

![テンプレート適用前の ListBox](./media/styles-and-templates-overview/stylingintro-listboxbefore.png "StylingIntro_ListBoxBefore")

ほとんどのコントロールはいくつかの型のコンテンツを持ち、そのコンテンツは多くの場合バインディング先のデータから取得されます。 このサンプルでは、データは写真のリストです。 WPF では、 を<xref:System.Windows.DataTemplate>使用してデータの視覚的表現を定義します。 基本的に、レンダリングされたアプリで<xref:System.Windows.DataTemplate>データがどのようなものに表示されるかは決まります。

サンプル アプリでは、各カスタム`Photo`オブジェクトには`Source`、イメージのファイル パスを指定する string 型のプロパティがあります。 現在のところ、写真オブジェクトは、ファイルのパスとして表示されます。

[!code-csharp[PhotoClass](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/csharp/Photo.cs#PhotoClass)]
[!code-vb[PhotoClass](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/vb/Photo.vb#PhotoClass)]

写真を画像として表示するには、リソースとして を<xref:System.Windows.DataTemplate>作成します。

[!code-xaml[DataTemplate](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/csharp/Window4.xaml#SnippetDataTemplate)]

プロパティは、 <xref:System.Windows.DataTemplate.DataType%2A> <xref:System.Windows.Style.TargetType%2A><xref:System.Windows.Style>のプロパティと似ています。 がリソース<xref:System.Windows.DataTemplate>セクションにある場合、型にプロパティを<xref:System.Windows.DataTemplate.DataType%2A>指定し、 を`x:Key`省略すると、その型<xref:System.Windows.DataTemplate>が表示されるたびに が適用されます。 を<xref:System.Windows.DataTemplate>使用して を割り当て`x:Key`、プロパティやプロパティなどの型を`StaticResource`取得<xref:System.Windows.DataTemplate>するプロパティとして設定する<xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A>オプションは常にあります。 <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A>

基本的に、上<xref:System.Windows.DataTemplate>の例では、`Photo`オブジェクトがある場合は常に、 内に. <xref:System.Windows.Controls.Image> <xref:System.Windows.Controls.Border> これで<xref:System.Windows.DataTemplate>、私たちのアプリは今このように見えます。

![フォト イメージ](./media/styles-and-templates-overview/stylingintro-photosasimages.png "StylingIntro_PhotosAsImages")

データ テンプレートのモデルでは、その他の機能を提供します。 たとえば<xref:System.Windows.Controls.HeaderedItemsControl>、<xref:System.Windows.Controls.Menu>や などの型を使用して、他のコレクションを含むコレクション データを<xref:System.Windows.Controls.TreeView>表示する場合は、<xref:System.Windows.HierarchicalDataTemplate>が表示されます。 もう 1 つのデータ テンプレート<xref:System.Windows.Controls.DataTemplateSelector>機能は、 で、カスタム<xref:System.Windows.DataTemplate>ロジックに基づいて を使用する を選択できます。 詳細については、「[Data Templating Overview](../../framework/wpf/data/data-templating-overview.md)」を参照してください。ここでは、さまざまなデータ テンプレート機能を詳しく説明します。

## <a name="triggers"></a>トリガー

トリガーは、プロパティ値が変更されたときまたはイベントが発生したときに、プロパティを設定するかまたはアニメーションなどのアクションを開始します。 <xref:System.Windows.Style>、、<xref:System.Windows.Controls.ControlTemplate>および<xref:System.Windows.DataTemplate>すべてのプロパティには`Triggers`、一連のトリガを含めることができます。 トリガーには、いくつかの種類があります。

### <a name="propertytriggers"></a>プロパティトリガー

プロパティ<xref:System.Windows.Trigger>値を設定する、またはプロパティの値に基づいてアクションを開始する場合は、プロパティ トリガーと呼ばれます。

プロパティ トリガーの使用方法を示すために、選択されていない場合<xref:System.Windows.Controls.ListBoxItem>は、各部分を透明にすることができます。 次のスタイルは、<xref:System.Windows.UIElement.Opacity%2A>の<xref:System.Windows.Controls.ListBoxItem>値を`0.5`に設定します。 ただし、<xref:System.Windows.Controls.ListBoxItem.IsSelected%2A>プロパティが`true`の場合は<xref:System.Windows.UIElement.Opacity%2A>、 が`1.0`に設定されます。

[!code-xaml[PropertyTrigger](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/csharp/Window5.xaml#SnippetPropertyTrigger)]

この例では、<xref:System.Windows.Trigger>を使用してプロパティ値を設定しますが<xref:System.Windows.Trigger>、トリガーがアクション<xref:System.Windows.TriggerBase.EnterActions%2A>を<xref:System.Windows.TriggerBase.ExitActions%2A>実行できるようにする プロパティと プロパティもクラスに含まれています。

の<xref:System.Windows.FrameworkElement.MaxHeight%2A>プロパティ<xref:System.Windows.Controls.ListBoxItem>が に設定されていることに`75`注意してください。 次の図では、3 番目の項目が選択された項目です。

![スタイル設定された ListView](./media/styles-and-templates-overview/stylingintro-triggers.png "StylingIntro_triggers")

### <a name="eventtriggers-and-storyboards"></a>Eventtrigger とストーリー ボード

別の種類のトリガは<xref:System.Windows.EventTrigger>、イベントの発生に基づいて一連のアクションを開始する です。 たとえば、次<xref:System.Windows.EventTrigger>のオブジェクトは、マウス ポインターが<xref:System.Windows.Controls.ListBoxItem>を入力したときに、<xref:System.Windows.FrameworkElement.MaxHeight%2A>プロパティが`90``0.2`2 番目の期間の値にアニメーション化することを指定します。 この項目からマウスを遠ざけると、`1` 秒間、元の値に戻ります。 <xref:System.Windows.ContentElement.MouseLeave>アニメーションの<xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>値を指定する必要はありません。 これは、アニメーションが元の値を追跡できるからです。

[!code-xaml[StyleEventTriggers](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/csharp/Window6.xaml#SnippetStyleEventTriggers)]

詳細については、「[ストーリーボードの概要](../../framework/wpf/graphics-multimedia/storyboards-overview.md)」を参照してください。

次の図では、マウスが 3 番目の項目を指しています。

![スタイリングサンプルスクリーンショット](./media/styles-and-templates-overview/stylingintro-eventtriggers.png "StylingIntro_EventTriggers")

### <a name="multitriggers-datatriggers-and-multidatatriggers"></a>MultiTriggers、DataTriggers、および MultiDataTriggers

および<xref:System.Windows.EventTrigger>のほか<xref:System.Windows.Trigger>に、他の種類のトリガーもあります。 <xref:System.Windows.MultiTrigger>では、複数の条件に基づいてプロパティ値を設定できます。 条件の<xref:System.Windows.DataTrigger>プロパティ<xref:System.Windows.MultiDataTrigger>がデータバインドである場合に使用します。

## <a name="visual-states"></a>ビジュアル状態

コントロールは常に特定の**状態**です。 たとえば、コントロールの表面上をマウスが移動すると、コントロールは一般的な状態であると見なされます`MouseOver`。 特定の状態のないコントロールは、共通`Normal`の状態であると見なされます。 状態はグループに分割され、前述の状態は状態グループ`CommonStates`の一部です。 ほとんどのコントロールには、 と`CommonStates`の`FocusStates`2 つの状態グループがあります。 コントロールに適用される各状態グループのうち、コントロールは常に各グループの 1 つの状態`CommonStates.MouseOver`(`FocusStates.Unfocused`および など) です。 ただし、コントロールを同じグループ内の 2 つの異なる状態に`CommonStates.Normal`することはできません。 `CommonStates.Disabled` ほとんどのコントロールが認識して使用する状態のテーブルを次に示します。

| VisualState 名 | VisualStateGroup 名 | 説明 |
| ---------------- | --------------------- | ----------- |
| Normal           | CommonStates          | 既定の状態です。 |
| MouseOver        | CommonStates          | マウス ポインターがコントロール上に配置されます。 |
| 押されている          | CommonStates          | コントロールが押されています。 |
| 無効         | CommonStates          | コントロールが無効になっています。 |
| フォーカスされている          | FocusStates           | コントロールにフォーカスがあります。 |
| フォーカスされていない        | FocusStates           | コントロールにフォーカスがありません。 |

コントロール テンプレートの<xref:System.Windows.VisualStateManager?displayProperty=fullName>ルート要素で を定義すると、コントロールが特定の状態になったときにアニメーションをトリガーできます。 は`VisualStateManager`、どの組み合わせ<xref:System.Windows.VisualStateGroup>と<xref:System.Windows.VisualState>を見るかを宣言します。 コントロールが監視状態になると、 で定義されたアニメーション`VisaulStateManager`が開始されます。

たとえば、次の XAML コードは`CommonStates.MouseOver`、という名前`backgroundElement`の要素の塗りつぶしの色をアニメーション化する状態を監視します。 コントロールが`CommonStates.Normal`状態に戻ると、名前の付いた`backgroundElement`要素の塗りつぶしの色が復元されます。

```xaml
<ControlTemplate x:Key="roundbutton" TargetType="Button">
    <Grid>
        <VisualStateManager.VisualStateGroups>
            <VisualStateGroup Name="CommonStates">
                <VisualState Name="Normal">
                    <ColorAnimation Storyboard.TargetName="backgroundElement"
                                    Storyboard.TargetProperty="(Shape.Fill).(SolidColorBrush.Color)"
                                    To="{TemplateBinding Background}"
                                    Duration="0:0:0.3"/>
                </VisualState>
                <VisualState Name="MouseOver">
                    <ColorAnimation Storyboard.TargetName="backgroundElement"
                                    Storyboard.TargetProperty="(Shape.Fill).(SolidColorBrush.Color)"
                                    To="Yellow"
                                    Duration="0:0:0.3"/>
                </VisualState>
            </VisualStateGroup>
        </VisualStateManager.VisualStateGroups>

        ...
```

ストーリーボードの詳細については、「ストーリーボードの[概要](../../framework/wpf/graphics-multimedia/storyboards-overview.md)」を参照してください。

## <a name="shared-resources-and-themes"></a>共有リソースとテーマ

一般的な WPF アプリには、アプリ全体に適用される複数の UI リソースが含まれている場合があります。 このリソースのセットをまとめて、アプリのテーマと見なすことができます。 WPFWPF では、クラスとしてカプセル化されたリソース ディクショナリを使用して、UI リソースをテーマ<xref:System.Windows.ResourceDictionary>としてパッケージ化できます。

WPF テーマは、WPF が任意の要素のビジュアルをカスタマイズするために公開するスタイルとテンプレートのメカニズムを使用して定義されます。

WPF テーマ リソースは、埋め込みリソース ディクショナリに格納されます。 これらのリソース ディクショナリは署名されたアセンブリ内に埋め込む必要があり、コード自体と同じアセンブリまたはサイド バイ サイド アセンブリで埋め込むことができます。 WPF コントロールを含むアセンブリである PresentationFramework.dll の場合、テーマ リソースは一連のサイド バイ サイド アセンブリに含まれます。

テーマは、要素のスタイルを検索するときに最後に検索する場所になります。 通常、検索は要素ツリーを参照して適切なリソースを検索してから、アプリ リソース コレクションを調べ、最後にシステムにクエリを実行します。 これにより、アプリ開発者は、テーマに到達する前に、ツリーまたはアプリ レベルで任意のオブジェクトのスタイルを再定義できます。

リソース ディクショナリは、複数のアプリでテーマを再利用できる個別のファイルとして定義できます。 また、同じ種類のリソースだが値が異なる複数のリソース ディクショナリを定義して、交換できるテーマを作成することもできます。 アプリ レベルでこれらのスタイルやその他のリソースを再定義することは、アプリをスキニングするための推奨される方法です。

スタイルやテンプレートなどのリソースをアプリ間で共有するには、XAML ファイルを作成し、<xref:System.Windows.ResourceDictionary>`shared.xaml`ファイルへの参照を含む を定義します。

```xaml
<ResourceDictionary.MergedDictionaries>
  <ResourceDictionary Source="Shared.xaml" />
</ResourceDictionary.MergedDictionaries>
```

の共有は、スタイル`shared.xaml`リソースとブラシ リソース<xref:System.Windows.ResourceDictionary>のセットを含む を定義する自体が定義されており、アプリ内のコントロールの外観を一貫させることができます。

詳細については、「[マージされたリソース ディクショナリ](../../framework/wpf/advanced/merged-resource-dictionaries.md)」を参照してください。

カスタム コントロールのテーマを作成する場合は、「[コントロールオーサリングの概要](../../framework/wpf/controls/control-authoring-overview.md#defining-resources-at-the-theme-level)」の **「テーマ レベルでのリソースの定義**」セクションを参照してください。

## <a name="see-also"></a>関連項目

- [WPF におけるパッケージの URI](../../framework/wpf/app-development/pack-uris-in-wpf.md)
- [方法: ControlTemplate によって生成された要素を検索する](../../framework/wpf/controls/how-to-find-controltemplate-generated-elements.md)
- [データテンプレート生成要素の検索](../../framework/wpf/data/how-to-find-datatemplate-generated-elements.md)
