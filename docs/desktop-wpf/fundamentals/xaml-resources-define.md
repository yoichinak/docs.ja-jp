---
title: XAML リソースの定義
description: WPF の XAML リソースについて説明します。 XAML リソースの種類を理解し、XAML リソースを定義する方法について説明します。
author: thraka
ms.author: adegeo
ms.date: 08/21/2019
ms.openlocfilehash: b278bb92afc308578d60e347871e0150b26a95db
ms.sourcegitcommit: f8c36054eab877de4d40a705aacafa2552ce70e9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/31/2019
ms.locfileid: "81432570"
---
# <a name="overview-of-xaml-resources"></a>XAML リソースの概要

リソースは、アプリ内のさまざまな場所で再利用できるオブジェクトです。 リソースの例としては、ブラシやスタイルなどがあります。 この概要では、拡張アプリケーション マークアップ言語 (XAML) でリソースを使用する方法について説明します。 コードを使用してリソースを作成してアクセスすることもできます。

> [!NOTE]
> この記事で説明する XAML リソースは、アプリ*リソース*とは異なり、通常はコンテンツ、データ、埋め込みファイルなど、アプリに追加されるファイルです。

<!-- TODO: File redirect from docs\framework\wpf\advanced\xaml-resources.md -->

[!INCLUDE [desktop guide under construction](../../../includes/desktop-guide-preview-note.md)]

## <a name="using-resources-in-xaml"></a>XAML でのリソースの使用

次の例では、<xref:System.Windows.Media.SolidColorBrush>をページのルート要素のリソースとして定義します。 次に、リソースを参照し、リソースを使用して、 <xref:System.Windows.Shapes.Ellipse> <xref:System.Windows.Controls.TextBlock>、および a を含む複数の<xref:System.Windows.Controls.Button>子要素のプロパティを設定します。

[!code-xaml[FEResourceSH_snip#XAML](~/samples/snippets/csharp/VS_Snippets_Wpf/FEResourceSH_snip/CS/page1.xaml#xaml)]

フレームワーク レベルの要素<xref:System.Windows.FrameworkElement>(<xref:System.Windows.FrameworkContentElement>または<xref:System.Windows.FrameworkElement.Resources%2A>) には、定義<xref:System.Windows.ResourceDictionary>されたリソースを含む型であるプロパティがあります。 リソースは、 など、任意の要素に定義<xref:System.Windows.Controls.Button>できます。 ただし、リソースは、ほとんどの場合、ルート要素で定義されます<xref:System.Windows.Controls.Page>。

リソース ディクショナリ内の各リソースには、一意のキーが必要です。 マークアップでリソースを定義する場合は、 [x:Key ディレクティブ](../xaml-services/xkey-directive.md)を使用して一意のキーを割り当てます。 通常、キーは文字列です。ただし、適切なマークアップ拡張機能を使用して、他のオブジェクト型に設定することもできます。 リソースの文字列以外のキーは、特にスタイル、コンポーネント リソース、データ スタイル設定に使用される WPF の特定の機能領域で使用されます。

リソースのキー名を指定するリソース マークアップ拡張機能構文で、定義済みのリソースを使用できます。 たとえば、リソースを別の要素のプロパティの値として使用します。

[!code-xaml[FEResourceSH_snip#KeyNameUsage](~/samples/snippets/csharp/VS_Snippets_Wpf/FEResourceSH_snip/CS/page2.xaml#keynameusage)]

前の例では、XAML`{StaticResource MyBrush}`ローダーが<xref:System.Windows.Controls.Control.Background%2A>プロパティの値<xref:System.Windows.Controls.Button>を処理するときに、リソース検索ロジックは、まず、要素のリソース ディクショナリを<xref:System.Windows.Controls.Button>チェックします。 リソース<xref:System.Windows.Controls.Button>キー`MyBrush`の定義がない場合 (この例ではリソース コレクションが空である場合)、次に検索は<xref:System.Windows.Controls.Button><xref:System.Windows.Controls.Page>の親要素をチェックします。 ルート要素にリソースを<xref:System.Windows.Controls.Page>定義すると、 の論理ツリー内のすべての要素が<xref:System.Windows.Controls.Page>アクセスできます。 また、同じリソースを再利用して、リソースが表すのと同じ型を受け入れる任意のプロパティの値を設定できます。 前の例では、同じ`MyBrush`リソースが 2 つの異<xref:System.Windows.Controls.Control.Background%2A>なるプロパティ<xref:System.Windows.Controls.Button>を<xref:System.Windows.Shapes.Shape.Fill%2A>設定<xref:System.Windows.Shapes.Rectangle>します。

## <a name="static-and-dynamic-resources"></a>静的および動的リソース

リソースは、静的または動的のいずれかとして参照できます。 参照は[、StaticResource マークアップ拡張機能](../../framework/wpf/advanced/staticresource-markup-extension.md)または[DynamicResource マークアップ拡張機能](../../framework/wpf/advanced/dynamicresource-markup-extension.md)を使用して作成されます。 マークアップ拡張機能は、マークアップ拡張機能で属性文字列を処理し、オブジェクトを XAML ローダーに返すことによってオブジェクト参照を指定できる XAML 機能です。 マークアップ拡張機能の動作の詳細については、「[マークアップ拡張機能と WPF XAML](../../framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)」を参照してください。

マークアップ拡張機能を使用する場合、通常は、その特定のマークアップ拡張機能によって処理される文字列形式の 1 つ以上のパラメーターを指定します。 [StaticResource マークアップ拡張機能](../../framework/wpf/advanced/staticresource-markup-extension.md)は、すべての利用可能なリソース ディクショナリでそのキーの値を検索してキーを処理します。 ロード中に処理が行われるのは、読み込みプロセスがプロパティ値を割り当てる必要がある場合です。 [DynamicResource マークアップ拡張機能](../../framework/wpf/advanced/dynamicresource-markup-extension.md)は、式を作成することによってキーを処理し、その式は、アプリケーションが実行されるまで、式が評価され、値を提供するまで、未評価のままになります。

リソースを参照する場合、静的リソース参照または動的リソース参照のどちらを使用するかに、次の考慮事項が影響を与える可能性があります。

- アプリのリソースの作成方法 (ページごと、アプリ単位、loose XAML、またはリソースのみのアセンブリ) の全体的なデザインを決定する場合は、次の点を考慮してください。

- アプリの機能。 リアルタイムでのリソースの更新は、アプリの要件の一部ですか。
- そのリソース参照タイプのそれぞれのルックアップ動作。
- 特定のプロパティまたはリソースの種類、およびそれらの型のネイティブ動作。

## <a name="static-resources"></a>静的リソース

静的リソース参照は、次の状況で最適に機能します。

- アプリの設計では、ほとんどのリソースがページまたはアプリケーション レベルのリソース ディクショナリに集中します。 静的リソース参照は、ページの再読み込みなどの実行時の動作に基づいて再評価されません。 そのため、リソースとアプリの設計に基づいて必要のない動的リソース参照を大量に避けるには、パフォーマンス上の利点があります。

- または に含まれるプロパティの<xref:System.Windows.DependencyObject>値を設定している。 <xref:System.Windows.Freezable>

- DLL にコンパイルされ、アプリの一部としてパッケージ化されるか、アプリ間で共有されるリソース ディクショナリを作成しています。

- カスタム コントロールのテーマを作成し、テーマ内で使用されるリソースを定義しています。 この場合、通常は動的リソース参照のルックアップ動作は必要ありません。代わりに、静的リソース参照の動作を使用して、検索が予測可能で、テーマに対して自己完結するようにします。 動的リソース参照では、テーマ内の参照も実行時まで評価されません。 テーマが適用されると、いくつかのローカル要素がテーマが参照しようとしているキーを再定義し、ローカル要素がルックアップでテーマ自体の前に落ちる可能性があります。 その場合、テーマは期待どおりに動作しません。

- リソースを使用して多数の依存関係プロパティを設定しています。 依存関係プロパティには、プロパティ システムによって有効にされた有効な値のキャッシュがあるため、読み込み時に評価できる依存関係プロパティの値を指定する場合、依存関係プロパティは再評価された式をチェックする必要がなく、最後の有効値を返すことができます。 この手法は、パフォーマンス上の利点になります。

- すべてのコンシューマの基になるリソースを変更する場合、または[x:Shared 属性](../xaml-services/xshared-attribute.md)を使用して、各コンシューマに対して個別の書き込み可能なインスタンスを維持する必要があります。

### <a name="static-resource-lookup-behavior"></a>静的リソース検索動作

次に、静的リソースがプロパティまたは要素によって参照されるときに自動的に実行される参照プロセスについて説明します。

01. ルックアップ プロセスは、プロパティを設定する要素によって定義されたリソース ディクショナリ内の要求されたキーをチェックします。

01. 次に、参照プロセスは、論理ツリーを上位の親要素とそのリソース ディクショナリに移動します。 このプロセスは、ルート要素に到達するまで続きます。

01. アプリリソースがチェックされます。 アプリ リソースは、WPF アプリのオブジェクトによって定義されるリソース<xref:System.Windows.Application>ディクショナリ内のリソースです。

リソース ディクショナリ内からの静的リソース参照は、リソース参照の前に既に構文的に定義されているリソースを参照する必要があります。 前方参照は、静的リソース参照では解決できません。 このため、リソースがそれぞれのリソース ディクショナリの先頭または近くに定義されるように、リソース ディクショナリ構造を設計します。

静的リソースの参照はテーマまたはシステム リソースに拡張できますが、この検索は XAML ローダーが要求を延期するためだけにサポートされます。 ページの読み込み時にランタイム テーマがアプリに適切に適用されるようにするには、遅延が必要です。 ただし、テーマがユーザーによってリアルタイムに変更された場合、このような参照は再評価されないため、テーマまたはシステム リソースとしてしか存在しないキーへの静的リソース参照は推奨されません。 動的リソース参照は、テーマまたはシステム リソースを要求する場合に信頼性が高くなります。 例外は、テーマ要素自体が別のリソースを要求する場合です。 これらの参照は、前述の理由から静的リソース参照である必要があります。

静的リソース参照が見つからない場合の例外動作は、さまざまな変更を行います。 リソースが遅延された場合、例外は実行時に発生します。 リソースが遅延されていない場合、例外は読み込み時に発生します。

## <a name="dynamic-resources"></a>動的リソース

動的リソースは、次の場合に最適に機能します。

- システム リソースや、それ以外の場合はユーザーが設定可能なリソースを含むリソースの値は、ランタイムまでわからない条件によって異なります。 たとえば、<xref:System.Windows.SystemColors>によって<xref:System.Windows.SystemFonts>公開されるシステム プロパティを参照する設定値を<xref:System.Windows.SystemParameters>作成できます。 これらの値は、最終的にはユーザーとオペレーティング システムの実行時環境から取得されるため、本当に動的です。 また、変更可能なアプリケーション レベルのテーマがあり、ページ レベルのリソース アクセスも変更をキャプチャする必要があります。

- カスタム コントロールのテーマ スタイルを作成または参照しています。

- アプリの有効期間中にの<xref:System.Windows.ResourceDictionary>コンテンツを調整する場合。

- 前方参照が必要な場合は、相互依存性を持つ複雑なリソース構造があります。 静的リソース参照は前方参照をサポートしませんが、動的リソース参照は、ランタイムまでリソースを評価する必要がないため、参照が関連する概念ではないため、参照がサポートされます。

- コンパイルまたはワーキング セットの観点から大きいリソースを参照しており、ページの読み込み時にリソースがすぐには使用されない場合があります。 静的リソース参照は、ページの読み込み時に常に XAML から読み込まれます。 ただし、動的リソース参照は、使用されるまで読み込まれません。

- テーマやその他のユーザー設定の影響を受ける他の値から setter 値が取得される可能性があるスタイルを作成しています。

- アプリの有効期間中に論理ツリーで親を変更する可能性のある要素にリソースを適用しています。 親を変更するとリソース参照スコープも変更される可能性があるため、新しいスコープに基づいてリペアレント化された要素のリソースを再評価する場合は、常に動的リソース参照を使用します。

### <a name="dynamic-resource-lookup-behavior"></a>動的リソース検索動作

動的リソース参照のリソース検索動作は、 または を呼び出<xref:System.Windows.FrameworkElement.FindResource%2A>した場合、コード<xref:System.Windows.FrameworkElement.SetResourceReference%2A>内のルックアップ動作と並行して行われます。

01. lookup は、プロパティを設定する要素によって定義されたリソース ディクショナリ内の要求されたキーをチェックします。

    - 要素がプロパティを定義<xref:System.Windows.FrameworkElement.Style%2A>する場合、<xref:System.Windows.FrameworkElement.Style?displayProperty=fullName>要素ののディクショナリが<xref:System.Windows.Style.Resources>チェックされます。

    - 要素がプロパティを定義<xref:System.Windows.Controls.Control.Template%2A>する場合、<xref:System.Windows.FrameworkTemplate.Resources?displayProperty=fullName>要素のディクショナリがチェックされます。

01. 検索では、親要素とそのリソース ディクショナリに向けて論理ツリーを走査します。 このプロセスは、ルート要素に到達するまで続きます。

01. アプリリソースがチェックされます。 アプリ リソースは、WPF アプリのオブジェクトによって定義されるリソース<xref:System.Windows.Application>ディクショナリ内のリソースです。

01. 現在アクティブなテーマのテーマ リソース ディクショナリがチェックされます。 実行時にテーマが変更された場合、値が再評価されます。

01. システム リソースがチェックされます。

例外の動作 (存在する場合) は次のとおりです。

- <xref:System.Windows.FrameworkElement.FindResource%2A>呼び出しによってリソースが要求されたが見つからなかった場合は、例外がスローされます。

- <xref:System.Windows.FrameworkElement.TryFindResource%2A>リソースが呼び出しによって要求されたが見つからなかった場合、例外はスローされず、戻り値は`null`です。 設定されているプロパティが受け入れ`null`られない場合、設定されている個々のプロパティに応じて、より詳細な例外がスローされる可能性があります。

- XAML の動的リソース参照によってリソースが要求されたが見つからなかった場合、動作は一般的なプロパティ システムによって異なります。 一般的な動作は、リソースが存在するレベルでプロパティ設定操作が発生していない場合と同じ動作です。 たとえば、評価できなかったリソースを使用して個々のボタン要素に背景を設定しようとしても、値セットの結果は得られませんが、有効な値はプロパティ システムの他の参加者と値の優先順位から取得できます。 たとえば、背景の値は、ローカルで定義されたボタン スタイルまたはテーマ スタイルから取得できます。 テーマ スタイルで定義されていないプロパティの場合、リソース評価が失敗した後の有効値は、プロパティ メタデータの既定値から取得される場合があります。

### <a name="restrictions"></a>制限

動的リソース参照には、いくつかの注目すべき制限があります。 次の条件のうち少なくとも 1 つが真である必要があります。

- 設定されるプロパティは、<xref:System.Windows.FrameworkElement>または<xref:System.Windows.FrameworkContentElement>のプロパティである必要があります。 このプロパティは、 によってバックアップ<xref:System.Windows.DependencyProperty>される必要があります。

- 参照は、 内の値に`StyleSetter`対する参照です。

- 設定されるプロパティは、 または プロパティの<xref:System.Windows.Freezable><xref:System.Windows.FrameworkElement>値または値として提供される の<xref:System.Windows.FrameworkContentElement>プロパティである<xref:System.Windows.Setter>必要があります。

設定されるプロパティは a<xref:System.Windows.DependencyProperty>または<xref:System.Windows.Freezable>プロパティである必要があるため、プロパティの変更 (動的リソースの変更) がプロパティ システムによって確認されるため、ほとんどのプロパティの変更は UI に反映されます。 ほとんどのコントロールには、変更時にコントロールの別のレイアウトを<xref:System.Windows.DependencyProperty>強制するロジックが含まれています。 ただし、値として[DynamicResource マークアップ拡張機能](../../framework/wpf/advanced/dynamicresource-markup-extension.md)を持つすべてのプロパティは、UI でリアルタイムの更新を提供することが保証されていません。 この機能は、プロパティ、プロパティを所有する型、またはアプリの論理構造によっても変わる場合があります。

## <a name="styles-datatemplates-and-implicit-keys"></a>スタイル、データ テンプレート、および暗黙的なキー

内のすべての項目にはキー<xref:System.Windows.ResourceDictionary>が必要ですが、すべてのリソースに明示的`x:Key`な が必要であるとは言えません。 いくつかのオブジェクト型は、リソースとして定義されている場合に暗黙のキーをサポートし、キー値は別のプロパティの値に関連付けられます。 このタイプのキーは暗黙のキーと呼ばれますが、`x:Key`属性は明示的なキーです。 明示的なキーを指定することで、任意の暗黙的なキーを上書きできます。

リソースの重要なシナリオの 1 つは<xref:System.Windows.Style>、 を定義する場合です。 実際には、スタイル<xref:System.Windows.Style>は本質的に再利用を目的としているため、a はリソース ディクショナリのエントリとして定義されます。 スタイルの詳細については、「[スタイルとテンプレート](styles-templates-overview.md)」を参照してください。

コントロールのスタイルは、暗黙的なキーを使用して作成および参照できます。 コントロールの既定の外観を定義するテーマ スタイルは、この暗黙のキーに依存します。 要求の観点からは、暗黙のキーはコントロール自体<xref:System.Type>のです。 リソースを定義する観点から、暗黙のキーはスタイル<xref:System.Windows.Style.TargetType%2A>のです。 したがって、カスタム コントロールのテーマを作成したり、既存のテーマ スタイルと対話するスタイルを作成したりする場合は、そのテーマ[に対して x:Key ディレクティブ](../xaml-services/xkey-directive.md)を指定する<xref:System.Windows.Style>必要はありません。 テーマスタイルを使用する場合は、スタイルを指定する必要はありません。 たとえば、リソースにキーが含まれていないように見えても<xref:System.Windows.Style>、次のスタイル定義が機能します。

[!code-xaml[FEResourceSH_snip#ImplicitStyle](~/samples/snippets/csharp/VS_Snippets_Wpf/FEResourceSH_snip/CS/page2.xaml#implicitstyle)]

そのスタイルには、暗黙のキーというキーがあります`typeof(System.Windows.Controls.Button)`。 マークアップでは、型名として直接<xref:System.Windows.Style.TargetType%2A>を指定できます (またはオプションで[{x:Type.}}](../xaml-services/xtype-markup-extension.md) をクリックして<xref:System.Type>を返します。

WPF で使用される既定のテーマ スタイルのメカニズムを使用すると、<xref:System.Windows.Controls.Button><xref:System.Windows.Controls.Button>そのスタイルは、その<xref:System.Windows.FrameworkElement.Style%2A>プロパティまたはスタイルへの特定のリソース参照を指定しようとしない場合でも、ページ上ののランタイム スタイルとして適用されます。 ページで定義されているスタイルは、テーマ ディクショナリ スタイルと同じキーを使用して、検索順序の前にテーマ ディクショナリ スタイルを使用して検索されます。 ページ内の任意`<Button>Hello</Button>`の場所を指定するだけで、定義<xref:System.Windows.Style.TargetType%2A>したスタイルがそのボタンに`Button`適用されます。 必要に応じて、マークアップでわかりやすく<xref:System.Windows.Style.TargetType%2A>するために、同じ型の値を持つスタイルに明示的にキーを設定することもできますが、これはオプションです。

スタイルの暗黙のキー<xref:System.Windows.FrameworkElement.OverridesDefaultStyle%2A>は`true`、コントロールに適用されません。 (コントロールの<xref:System.Windows.FrameworkElement.OverridesDefaultStyle%2A>インスタンスで明示的にではなく、コントロール クラスのネイティブ動作の一部として設定することもできます)。また、派生クラスのシナリオで暗黙のキーをサポートするためには、コントロールをオーバーライド<xref:System.Windows.FrameworkElement.DefaultStyleKey%2A>する必要があります (WPF の一部として提供されるすべての既存のコントロールには、このオーバーライドが含まれています)。 スタイル、テーマ、およびコントロールデザインの詳細については、「[スタイル可能なコントロールを設計するためのガイドライン](../../framework/wpf/controls/guidelines-for-designing-stylable-controls.md)」を参照してください。

<xref:System.Windows.DataTemplate>また、暗黙のキーもあります。 の<xref:System.Windows.DataTemplate>暗黙のキーは<xref:System.Windows.DataTemplate.DataType%2A>、プロパティ値です。 <xref:System.Windows.DataTemplate.DataType%2A>また、[型](../xaml-services/xtype-markup-extension.md)の名前として指定することもできます。 詳細については、「[データ テンプレートの概要」を](../../framework/wpf/data/data-templating-overview.md)参照してください。

## <a name="see-also"></a>関連項目

- <xref:System.Windows.ResourceDictionary>
- [アプリケーション リソース](../../framework/wpf/advanced/optimizing-performance-application-resources.md)
- [リソースとコード](../../framework/wpf/advanced/resources-and-code.md)
- [リソースの定義と参照](../../framework/wpf/advanced/how-to-define-and-reference-a-resource.md)
- [アプリケーション管理の概要](../../framework/wpf/app-development/application-management-overview.md)
- [x:タイプマークアップ拡張機能](../xaml-services/xtype-markup-extension.md)
- [静的リソース マークアップ拡張機能](../../framework/wpf/advanced/staticresource-markup-extension.md)
- [動的リソース マークアップ拡張機能](../../framework/wpf/advanced/dynamicresource-markup-extension.md)
