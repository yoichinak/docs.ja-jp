---
title: XAML リソース
ms.date: 03/30/2017
helpviewer_keywords:
- reusing resources [WPF]
- resources [WPF], reusing
- reusing commonly defined objects [WPF]
- XAML [WPF], reusing resources
ms.assetid: 91580b89-a0a8-4889-aecb-fddf8e63175f
ms.openlocfilehash: 738a4f397b1677b867126c7bb439b027f951baa0
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69958815"
---
# <a name="xaml-resources"></a>XAML リソース
リソースは、アプリケーションのさまざまな場所で再利用できるオブジェクトです。 リソースの例としては、ブラシやスタイルなどがあります。 この概要では、の[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]リソースを使用する方法について説明します。 また、コードを使用してリソースを作成してアクセスしたり、 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]コードとを区別したりすることもできます。 詳細については、「[リソースとコード](resources-and-code.md)」を参照してください。  
  
> [!NOTE]
> このトピックで説明するリソースファイルは、「 [WPF アプリケーションリソース、コンテンツ、およびデータファイル](../app-development/wpf-application-resource-content-and-data-files.md)」で説明されているリソースファイルとは異なり、「[アプリケーションリソースの管理 (.net)」で説明されている埋め込みリソースまたはリンクされたリソースとは異なります](/visualstudio/ide/managing-application-resources-dotnet)。  

<a name="usingresources"></a>   
## <a name="using-resources-in-xaml"></a>XAML でのリソースの使用  
 次の例では<xref:System.Windows.Media.SolidColorBrush> 、ページのルート要素のリソースとしてを定義します。 次に、リソースを参照し、このリソースを使用して<xref:System.Windows.Shapes.Ellipse> <xref:System.Windows.Controls.TextBlock>、、 <xref:System.Windows.Controls.Button>、などのいくつかの子要素のプロパティを設定します。  
  
 [!code-xaml[FEResourceSH_snip#XAML](~/samples/snippets/csharp/VS_Snippets_Wpf/FEResourceSH_snip/CS/page1.xaml#xaml)]  
  
 すべてのフレームワークレベル要素 (<xref:System.Windows.FrameworkElement>また<xref:System.Windows.FrameworkContentElement>は) に<xref:System.Windows.FrameworkElement.Resources%2A>は、リソースを定義するリソース (として<xref:System.Windows.ResourceDictionary>) を含むプロパティであるプロパティがあります。 任意の要素にリソースを定義できます。 ただし、多くの場合、リソースはルート要素 (例では<xref:System.Windows.Controls.Page> ) で定義されています。  
  
 リソースディクショナリ内の各リソースには、一意のキーが必要です。 マークアップでリソースを定義する場合は、 [X:Key ディレクティブ](../../xaml-services/x-key-directive.md)を使用して一意のキーを割り当てます。 通常、キーは文字列です。ただし、適切なマークアップ拡張機能を使用して、他のオブジェクトの種類に設定することもできます。 リソースの文字列以外のキーは[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]、の特定の機能領域 (特に、スタイル、コンポーネントリソース、データスタイル) で使用されます。  
  
 リソースを定義した後、キー名を指定するリソースマークアップ拡張構文を使用して、プロパティ値に使用するリソースを参照できます。次に例を示します。  
  
 [!code-xaml[FEResourceSH_snip#KeyNameUsage](~/samples/snippets/csharp/VS_Snippets_Wpf/FEResourceSH_snip/CS/page2.xaml#keynameusage)]  
  
 前の例では、ローダー [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]がの<xref:System.Windows.Controls.Button> `{StaticResource MyBrush}` <xref:System.Windows.Controls.Control.Background%2A>プロパティの値を処理するときに、リソース検索ロジック<xref:System.Windows.Controls.Button>はまず、要素のリソースディクショナリをチェックします。 に<xref:System.Windows.Controls.Button>リソースキー `MyBrush`の定義がない (そのリソースコレクションが空である) 場合、参照は次にの<xref:System.Windows.Controls.Button>親要素を確認します (つまり<xref:System.Windows.Controls.Page>、)。 したがって、 <xref:System.Windows.Controls.Page>ルート要素でリソースを定義すると、 <xref:System.Windows.Controls.Page>の論理ツリー内のすべての要素がそのリソースにアクセスできるようになります。また、同じリソースを再利用して、リソース<xref:System.Type>に対するを受け入れるプロパティの値を設定することもできます。を. 前の例では、同じ`MyBrush`リソースによって、 <xref:System.Windows.Shapes.Shape.Fill%2A> <xref:System.Windows.Controls.Control.Background%2A>の<xref:System.Windows.Controls.Button> <xref:System.Windows.Shapes.Rectangle>とのの2つの異なるプロパティが設定されています。  
  
<a name="staticdynamic"></a>   
## <a name="static-and-dynamic-resources"></a>静的および動的なリソース  
 リソースは、静的リソースと動的リソースのどちらかとして参照できます。 これは、 [StaticResource マークアップ拡張](staticresource-markup-extension.md)機能または[Dynamicresource マークアップ拡張機能](dynamicresource-markup-extension.md)のいずれかを使用して行います。 マークアップ拡張機能は、マーク[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]アップ拡張機能によって属性文字列を処理し、オブジェクトを[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]ローダーに返すことで、オブジェクト参照を指定できるようにする機能です。 マークアップ拡張機能の動作の詳細については、「[マークアップ拡張機能と WPF XAML](markup-extensions-and-wpf-xaml.md)」を参照してください。  
  
 マークアップ拡張機能を使用する場合、通常は、設定されるプロパティのコンテキストで評価されるのではなく、特定のマークアップ拡張機能によって処理される1つ以上のパラメーターを文字列形式で指定します。 [StaticResource マークアップ拡張機能](staticresource-markup-extension.md)は、使用可能なすべてのリソースディクショナリでそのキーの値を検索することによって、キーを処理します。 読み込み中に発生します。これは、読み込みプロセスが静的リソース参照を受け取るプロパティ値を割り当てる必要がある時点です。 代わりに、 [Dynamicresource マークアップ拡張機能](dynamicresource-markup-extension.md)は、式を作成することによってキーを処理します。この式は、アプリケーションが実際に実行されるまで未評価のままです。その時点で、式が評価され、値が提供されます。  
  
 リソースを参照する場合、次の考慮事項は、静的リソース参照と動的リソース参照のどちらを使用するかに影響する可能性があります。  
  
- アプリケーションのリソースを作成する方法の全体的な設計 (リソースのみのアセンブリでは、アプリケーション内で[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]は、アプリケーション内では疎ではありません)。  
  
- アプリケーションの機能: アプリケーションの要件のリアルタイムの部分でリソースを更新していますか。  
  
- そのリソース参照型のそれぞれの参照動作。  
  
- 特定のプロパティまたはリソースの種類、およびそれらの型のネイティブな動作。  
  
### <a name="static-resources"></a>静的リソース  
 静的リソース参照は、次のような状況に最も適しています。  
  
- アプリケーションの設計では、すべてのリソースのほとんどがページまたはアプリケーションレベルのリソースディクショナリに集中しています。 静的リソース参照は、ページの再読み込みなどの実行時の動作に基づいて再評価されることはないため、リソースごとに不要な動的リソース参照を大量に回避すると、パフォーマンス上の利点があります。アプリケーションの設計。  
  
- <xref:System.Windows.DependencyObject>またはにないプロパティの値を設定しようとしています。<xref:System.Windows.Freezable>  
  
- DLL にコンパイルされるリソースディクショナリを作成し、アプリケーションの一部としてパッケージ化するか、アプリケーション間で共有します。  
  
- カスタムコントロールのテーマを作成し、テーマ内で使用されるリソースを定義します。 この場合、動的リソース参照の参照動作は通常は必要ありません。代わりに、静的なリソース参照の動作を使用して、参照が予測可能であり、テーマに自己完結している必要があります。 動的リソース参照を使用すると、テーマ内の参照が実行可能になるまでは評価されません。また、テーマが適用されると、テーマが参照しようとしているキーが一部のローカル要素によって再定義され、ローカル要素が前になります。検索でテーマ自体に。 そのような場合は、テーマが期待どおりに動作しません。  
  
- リソースを使用して、多数の依存関係プロパティを設定しています。 依存関係プロパティの有効な値のキャッシュは、プロパティシステムによって有効になります。したがって、読み込み時に評価できる依存関係プロパティの値を指定する場合、依存関係プロパティは再評価式を確認する必要がなく、最後の有効な値。 この手法は、パフォーマンス上の利点があります。  
  
- すべてのコンシューマーの基になるリソースを変更する必要がある場合、または[X:Shared 属性](../../xaml-services/x-shared-attribute.md)を使用してコンシューマーごとに個別の書き込み可能インスタンスを保持する場合。  
  
#### <a name="static-resource-lookup-behavior"></a>静的リソース参照の動作  
  
1. 参照プロセスは、プロパティを設定する要素によって定義されたリソースディクショナリ内で、要求されたキーを確認します。  
  
2. 次に、参照プロセスによって論理ツリーが上位に、親要素とそのリソースディクショナリに向かって走査されます。 これは、ルート要素に到達するまで続行されます。  
  
3. 次に、アプリケーションリソースが確認されます。 アプリケーションリソースは、 <xref:System.Windows.Application> [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]アプリケーションのオブジェクトによって定義されたリソースディクショナリ内のリソースです。  
  
 リソースディクショナリ内からの静的リソース参照は、リソース参照の前に既に定義されているリソースを参照する必要があります。 前方参照は、静的リソース参照によって解決できません。 このため、静的なリソース参照を使用する場合は、リソースディクショナリの構造を設計する必要があります。これは、リソースを使用することを目的としたリソースが、それぞれのリソースディクショナリの先頭に定義されているか、その近くに定義されているかを示します。  
  
 静的リソース参照は、テーマまたはシステムリソースに拡張できますが、これはローダーが[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]要求を延期することによってのみサポートされます。 遅延は、ページが読み込まれるときのランタイムテーマがアプリケーションに適切に適用されるようにするために必要です。 ただし、にのみ存在することがわかっているキーへの静的リソース参照は、テーマまたはシステムリソースとしてのみ存在することをお勧めします。 これは、ユーザーがリアルタイムでテーマを変更した場合に、このような参照が再評価されないためです。 動的リソース参照は、テーマまたはシステムリソースを要求するときに信頼性が高くなります。 例外は、テーマ要素自体が別のリソースを要求する場合です。 これらの参照は、前述の理由により、静的なリソース参照である必要があります。  
  
 静的リソース参照が見つからない場合の例外動作は異なります。 リソースが遅延された場合は、実行時に例外が発生します。 リソースが遅延されていない場合は、読み込み時に例外が発生します。  
  
### <a name="dynamic-resources"></a>動的リソース  
 動的リソースは、次のような状況で最適に機能します。  
  
- リソースの値は、ランタイムまで不明な条件に依存します。 これには、システムリソース、またはユーザーが設定できるリソースが含まれます。 たとえば、、 <xref:System.Windows.SystemColors> <xref:System.Windows.SystemFonts>、または<xref:System.Windows.SystemParameters>によって公開されているシステムプロパティを参照する setter 値を作成できます。 これらの値は、最終的にユーザーおよびオペレーティングシステムのランタイム環境から取得されるため、真に動的です。 また、変更できるアプリケーションレベルのテーマがある場合もあります。この場合、ページレベルのリソースへのアクセスでも変更をキャプチャする必要があります。  
  
- カスタムコントロールのテーマスタイルを作成または参照している。  
  
- アプリケーションの有効期間<xref:System.Windows.ResourceDictionary>中にの内容を調整する場合。  
  
- 相互依存関係を持つ複雑なリソース構造があり、前方参照が必要になる場合があります。 静的リソース参照では前方参照はサポートされていませんが、動的リソース参照では、リソースをランタイムに評価する必要がなく、前方参照が関連する概念ではないため、動的リソース参照はこれらをサポートします。  
  
- コンパイルまたはワーキングセットの観点から特に大きいリソースを参照しているため、ページの読み込み時にリソースがすぐには使用されない可能性があります。 静的リソース参照は、ページ[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]が読み込まれるときに常に読み込まれます。ただし、動的リソース参照は、実際に使用されるまで読み込まれません。  
  
- テーマまたはその他のユーザー設定の影響を受ける他の値からセッター値が取得される可能性があるスタイルを作成しています。  
  
- アプリケーションの有効期間中に論理ツリー内で親される可能性のある要素にリソースを適用しています。 親を変更すると、リソースルックアップスコープも変更される可能性があるため、新しいスコープに基づいて親要素のリソースを再評価するには、常に動的リソース参照を使用します。  
  
#### <a name="dynamic-resource-lookup-behavior"></a>動的リソース参照の動作  
 動的リソース参照のリソース参照動作は、または<xref:System.Windows.FrameworkElement.FindResource%2A> <xref:System.Windows.FrameworkElement.SetResourceReference%2A>を呼び出すと、コードの参照動作と同じです。  
  
1. 参照プロセスは、プロパティを設定する要素によって定義されたリソースディクショナリ内で、要求されたキーを確認します。  
  
    - 要素がプロパティ<xref:System.Windows.FrameworkElement.Style%2A> <xref:System.Windows.Style.Resources%2A>を定義している場合は、 <xref:System.Windows.Style>内のディクショナリがチェックされます。  
  
    - 要素がプロパティ<xref:System.Windows.Controls.Control.Template%2A> <xref:System.Windows.FrameworkTemplate.Resources%2A>を定義している場合は、 <xref:System.Windows.FrameworkTemplate>内のディクショナリがチェックされます。  
  
2. 次に、参照プロセスによって論理ツリーが上位に、親要素とそのリソースディクショナリに向かって走査されます。 これは、ルート要素に到達するまで続行されます。  
  
3. 次に、アプリケーションリソースが確認されます。 アプリケーションリソースは、 <xref:System.Windows.Application> [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]アプリケーションのオブジェクトによって定義されたリソースディクショナリ内のリソースです。  
  
4. 現在アクティブなテーマのテーマリソースディクショナリがチェックされます。 実行時にテーマが変更された場合、値は再評価されます。  
  
5. システムリソースがチェックされます。  
  
 例外の動作 (存在する場合) は、次のように異なります。  
  
- リソースが<xref:System.Windows.FrameworkElement.FindResource%2A>呼び出しによって要求され、が見つからなかった場合は、例外が発生します。  
  
- リソースが<xref:System.Windows.FrameworkElement.TryFindResource%2A>呼び出しによって要求され、が見つからなかった場合は、例外は発生しませんが`null`、戻り値はになります。 設定するプロパティがを受け入れ`null`ない場合でも、より深い例外が発生する可能性があります (これは、設定されている個々のプロパティによって異なります)。  
  
- リソースがの[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]動的リソース参照によって要求され、見つからなかった場合、動作は一般的なプロパティシステムによって異なりますが、一般的な動作は、リソースが存在するレベルでプロパティ設定操作が行われなかった場合と同じです。 たとえば、評価できないリソースを使用して個々の button 要素の背景を設定しようとした場合、値は設定されませんが、プロパティシステムと値の優先順位の他の参加者から有効な値を取得できます。 たとえば、背景値は、ローカルに定義されたボタンスタイルまたはテーマスタイルから取得される場合があります。 テーマスタイルで定義されていないプロパティの場合、リソースの評価に失敗した後の有効値は、プロパティメタデータの既定値から取得される可能性があります。  
  
#### <a name="restrictions"></a>制約  
 動的リソース参照には、いくつかの注目すべき制限があります。 少なくとも次のいずれかが true である必要があります。  
  
- 設定するプロパティは、 <xref:System.Windows.FrameworkElement>または<xref:System.Windows.FrameworkContentElement>のプロパティである必要があります。 このプロパティは、 <xref:System.Windows.DependencyProperty>でサポートされている必要があります。  
  
- 参照は、 <xref:System.Windows.Style> <xref:System.Windows.Setter>内の値を対象としています。  
  
- 設定する<xref:System.Windows.Freezable>プロパティは、プロパティ<xref:System.Windows.FrameworkElement> <xref:System.Windows.FrameworkContentElement>またはプロパティの値または値として指定されたのプロパティである必要があります。<xref:System.Windows.Setter>  
  
 設定するプロパティはプロパティ<xref:System.Windows.DependencyProperty>または<xref:System.Windows.Freezable>プロパティである必要があるため、プロパティの変更 (動的リソース値の変更) がプロパティシステムによって確認されるため、ほとんどのプロパティ変更が UI に反映される可能性があります。 ほとんどのコントロールには、 <xref:System.Windows.DependencyProperty>変更やそのプロパティがレイアウトに影響を与える可能性がある場合に、コントロールの別のレイアウトを強制的に適用するロジックが含まれます。 ただし、 [Dynamicresource マークアップ拡張機能](dynamicresource-markup-extension.md)が値として使用されているすべてのプロパティでは、UI でリアルタイムに更新されるように値を提供することが保証されています。 この機能は、プロパティによって異なりますが、プロパティを所有する型やアプリケーションの論理構造によっても異なる場合があります。  
  
<a name="stylesimplicitkeys"></a>   
## <a name="styles-datatemplates-and-implicit-keys"></a>スタイル、DataTemplates、および暗黙のキー  
 前に、内の<xref:System.Windows.ResourceDictionary>すべての項目にキーが必要であることが示されていました。 ただし、これは、すべてのリソースに明示的`x:Key`なが必要であるという意味ではありません。 オブジェクトの種類によっては、リソースとして定義されている場合、キー値が別のプロパティの値に関連付けられている場合に、暗黙的なキーをサポートします。 これは暗黙のキー `x:Key`として知られていますが、属性は明示的なキーです。 明示的なキーを指定することで、暗黙のキーを上書きできます。  
  
 リソースの非常に重要なシナリオの1つは<xref:System.Windows.Style>、を定義する場合です。 実際、は、 <xref:System.Windows.Style>スタイルが本質的に再利用されることを意図しているため、ほとんどの場合、リソースディクショナリ内のエントリとして定義されます。 スタイルの詳細については、「スタイル[とテンプレート](../controls/styling-and-templating.md)」を参照してください。  
  
 コントロールのスタイルは、を使用して作成することも、暗黙的なキーを使用して参照することもできます。 コントロールの既定の外観を定義するテーマスタイルは、この暗黙のキーに依存します。 要求の観点から見た暗黙のキーは、 <xref:System.Type>コントロール自体のです。 リソースの定義の観点からの暗黙のキーは<xref:System.Windows.Style.TargetType%2A> 、スタイルのです。 したがって、カスタムコントロールのテーマを作成していて、既存のテーマスタイルと対話するスタイルを作成している場合は、その<xref:System.Windows.Style>に対して[x:Key ディレクティブ](../../xaml-services/x-key-directive.md)を指定する必要はありません。 また、テーマ付きスタイルを使用する場合は、スタイルを指定する必要はありません。 たとえば、次のスタイル定義は、 <xref:System.Windows.Style>リソースがキーを持っていないように見える場合でも動作します。  
  
 [!code-xaml[FEResourceSH_snip#ImplicitStyle](~/samples/snippets/csharp/VS_Snippets_Wpf/FEResourceSH_snip/CS/page2.xaml#implicitstyle)]  
  
 このスタイルには、暗黙のキー `typeof(` <xref:System.Windows.Controls.Button> `)`というキーが実際に含まれています。 マークアップでは、を型<xref:System.Windows.Style.TargetType%2A>名として直接指定できます (または、必要に応じて[{x:Type...}](../../xaml-services/x-type-markup-extension.md)を使用することもできます)。 を返す場合<xref:System.Type>は。  
  
 によっ[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]て使用される既定のテーマスタイル機構を使用して、そのスタイルは<xref:System.Windows.Controls.Button> 、その<xref:System.Windows.FrameworkElement.Style%2A>プロパティまたは特定の<xref:System.Windows.Controls.Button>リソースを指定しようとしない場合でも、ページ上ののランタイムスタイルとして適用されます。スタイルへの参照。 ページで定義されているスタイルは、テーマ辞書のスタイルと同じキーを使用して、参照シーケンスの前にテーマディクショナリのスタイルよりも前にあります。 ページ内の任意`<Button>Hello</Button>`の`Button`場所を指定するだけで、で<xref:System.Windows.Style.TargetType%2A>定義したスタイルがそのボタンに適用されます。 必要に応じて、マークアップでわかりやすくするために、と<xref:System.Windows.Style.TargetType%2A>同じ型の値を持つスタイルを明示的にキー指定することもできますが、これは省略可能です。  
  
 がの場合<xref:System.Windows.FrameworkElement.OverridesDefaultStyle%2A> 、スタイルの暗黙のキーはコントロールに適用されませ<xref:System.Windows.FrameworkElement.OverridesDefaultStyle%2A>ん (これは`true` 、コントロールのインスタンスで明示的にではなく、コントロールクラスのネイティブ動作の一部として設定されることもあります)。 また、派生クラスのシナリオで暗黙のキーをサポートするには、コントロール<xref:System.Windows.FrameworkElement.DefaultStyleKey%2A>をオーバーライドする必要があります ( [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]の一部として提供されるすべての既存のコントロール)。 スタイル、テーマ、およびコントロールのデザインの詳細については、「[スタイルコントロールを設計するためのガイドライン](../controls/guidelines-for-designing-stylable-controls.md)」を参照してください。  
  
 <xref:System.Windows.DataTemplate>には、暗黙のキーもあります。 の<xref:System.Windows.DataTemplate>暗黙のキー <xref:System.Windows.DataTemplate.DataType%2A>は、プロパティ値です。 <xref:System.Windows.DataTemplate.DataType%2A>は、 [{x:Type...}](../../xaml-services/x-type-markup-extension.md)を明示的に使用するのではなく、型の名前として指定することもできます。 詳細については、「[データテンプレートの概要](../data/data-templating-overview.md)」を参照してください。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.ResourceDictionary>
- [アプリケーション リソース](optimizing-performance-application-resources.md)
- [リソースとコード](resources-and-code.md)
- [リソースを定義および参照する](how-to-define-and-reference-a-resource.md)
- [アプリケーション管理の概要](../app-development/application-management-overview.md)
- [x:Type マークアップ拡張機能](../../xaml-services/x-type-markup-extension.md)
- [StaticResource のマークアップ拡張機能](staticresource-markup-extension.md)
- [DynamicResource マークアップ拡張](dynamicresource-markup-extension.md)
