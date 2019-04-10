---
title: XAML リソース
ms.date: 03/30/2017
helpviewer_keywords:
- reusing resources [WPF]
- resources [WPF], reusing
- reusing commonly defined objects [WPF]
- XAML [WPF], reusing resources
ms.assetid: 91580b89-a0a8-4889-aecb-fddf8e63175f
ms.openlocfilehash: d736d80a05469dafecbdaf196701c14528ee7d26
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59230019"
---
# <a name="xaml-resources"></a>XAML リソース
リソースは、アプリケーション内の別の場所で再利用できるオブジェクトです。 リソースの例には、ブラシ、スタイルが含まれます。 この概要でのリソースを使用する方法を説明します[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]します。 作成し、コードを使用して、またはコードの間で同じ意味でリソースにアクセスすることができますもと[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]します。 詳細については、次を参照してください。[リソースとコード](resources-and-code.md)します。  
  
> [!NOTE]
>  このトピックで説明されているリソース ファイルは、リソース ファイルで説明されているものと異なる[WPF アプリケーションのリソース、コンテンツ、およびデータ ファイル](../app-development/wpf-application-resource-content-and-data-files.md)しで説明されている埋め込みまたはリンクされたリソースとは異なる[管理アプリケーション リソース (.NET)](/visualstudio/ide/managing-application-resources-dotnet)します。  

<a name="usingresources"></a>   
## <a name="using-resources-in-xaml"></a>XAML でリソースの使用  
 次の例では、定義、<xref:System.Windows.Media.SolidColorBrush>リソース ページのルート要素として。 例では、リソースを参照しなどのいくつかの子要素のプロパティを設定するため、 <xref:System.Windows.Shapes.Ellipse>、 <xref:System.Windows.Controls.TextBlock>、および<xref:System.Windows.Controls.Button>します。  
  
 [!code-xaml[FEResourceSH_snip#XAML](~/samples/snippets/csharp/VS_Snippets_Wpf/FEResourceSH_snip/CS/page1.xaml#xaml)]  
  
 フレームワーク レベルのすべての要素 (<xref:System.Windows.FrameworkElement>または<xref:System.Windows.FrameworkContentElement>) が、<xref:System.Windows.FrameworkElement.Resources%2A>リソースを含むプロパティであるプロパティ (として、 <xref:System.Windows.ResourceDictionary>) リソースを定義します。 任意の要素には、リソースを定義できます。 ただし、リソースが、これはルート要素で定義された最も多くの場合、<xref:System.Windows.Controls.Page>の例です。  
  
 リソース ディクショナリ内の各リソースは、一意キーを持つ必要があります。 使って一意のキーを割り当てるマークアップでリソースを定義するときに、 [X:key ディレクティブ](../../xaml-services/x-key-directive.md)します。 通常、キーは、文字列。ただし、設定することできますも、その他のオブジェクトの種類に適切なマークアップ拡張機能を使用しています。 リソースの文字列以外のキーで特定の機能領域で使用されます[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]、特にのスタイル、コンポーネントのリソース、およびデータのスタイル設定します。  
  
 リソースを定義した後は、キーの名前を示すリソース マークアップ拡張構文を使用してプロパティ値を使用するリソースを参照できます。  
  
 [!code-xaml[FEResourceSH_snip#KeyNameUsage](~/samples/snippets/csharp/VS_Snippets_Wpf/FEResourceSH_snip/CS/page2.xaml#keynameusage)]  
  
 前の例では、ときに、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]ローダーは、値を処理`{StaticResource MyBrush}`の<xref:System.Windows.Controls.Control.Background%2A>プロパティ<xref:System.Windows.Controls.Button>、リソースの検索ロジックは最初のリソース ディクショナリにチェック、<xref:System.Windows.Controls.Button>要素。 場合<xref:System.Windows.Controls.Button>のリソース キーの定義がない`MyBrush`(そうでない、そのリソースのコレクションが空)、参照は、次の親要素をチェック<xref:System.Windows.Controls.Button>、これは<xref:System.Windows.Controls.Page>します。 したがってでリソースを定義する場合、<xref:System.Windows.Controls.Page>ルート要素では、論理ツリー内のすべての要素、<xref:System.Windows.Controls.Page>がアクセスできるし、任意のプロパティの値の設定の同じリソースを再利用することができます、<xref:System.Type>をリソース表します。 前の例で、同じ`MyBrush`リソースは、2 つの異なるプロパティを設定:<xref:System.Windows.Controls.Control.Background%2A>の<xref:System.Windows.Controls.Button>、および<xref:System.Windows.Shapes.Shape.Fill%2A>の<xref:System.Windows.Shapes.Rectangle>します。  
  
<a name="staticdynamic"></a>   
## <a name="static-and-dynamic-resources"></a>静的および動的なリソース  
 リソースは、静的リソースまたは動的リソースのいずれかとして参照できます。 いずれかを使用して、これは、 [StaticResource マークアップ拡張機能](staticresource-markup-extension.md)または[DynamicResource マークアップ拡張機能](dynamicresource-markup-extension.md)します。 マークアップ拡張機能の機能である[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]オブジェクト参照を指定するには、マークアップ拡張機能属性文字列を処理し、オブジェクトを返すことによって起こります、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]ローダー。 マークアップ拡張機能の動作の詳細については、次を参照してください。[マークアップ拡張機能と WPF XAML](markup-extensions-and-wpf-xaml.md)します。  
  
 マークアップ拡張機能を使用する場合は、その特定のマークアップ拡張機能によって処理される文字列形式の 1 つまたは複数のパラメーターではなく設定されるプロパティのコンテキストで評価される通常提供します。 [StaticResource マークアップ拡張機能](staticresource-markup-extension.md)すべての利用可能なリソース ディクショナリ内でそのキーの値を参照して、キーを処理します。 これは、読み込みプロセスを静的リソース参照を受け取るプロパティの値を割り当てる必要がある場合に、ポイントの読み込み中に発生します。 [DynamicResource マークアップ拡張機能](dynamicresource-markup-extension.md)代わりにプロセス式、およびその式を作成して、キー残り評価されていないアプリケーションが実際に実行されるまで、どの時点で、式が評価され、値を指定します。  
  
 リソースを参照すると次の考慮事項は静的リソース参照または動的リソース参照を使用するかどうかを与えることができます。  
  
-   アプリケーションのリソースを作成する方法の全体的なデザイン (アプリケーションでは、ページごとに疎[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]リソースの唯一のアセンブリで)。  
  
-   アプリケーションの機能: アプリケーションの要件の一部をリアルタイムでリソースを更新していますか?  
  
-   リソース参照の種類のそれぞれの検索動作します。  
  
-   特定のプロパティまたはリソースの種類、およびそれらの型のネイティブの動作。  
  
### <a name="static-resources"></a>静的なリソース  
 静的リソースは、次の状況に最適な作業を参照します。  
  
-   アプリケーションの設計は集中ディクショナリでは、リソースのページへのアプリケーション レベルのリソースのすべての最もします。 静的リソース参照は、ページの再読み込みなどの実行時の動作に基づいて再評価されないと、したがってするは、リソースごとに必要なときに、多数の動的リソース参照を使用しないようにするパフォーマンスが向上し、アプリケーションの設計。  
  
-   含まれていないプロパティの値を設定する、<xref:System.Windows.DependencyObject>または<xref:System.Windows.Freezable>します。  
  
-   DLL にコンパイルし、アプリケーションの一部としてパッケージ化またはアプリケーション間で共有されるリソース ディクショナリを作成します。  
  
-   カスタム コントロールのテーマを作成し、テーマ内で使用されているリソースを定義します。 この場合は、通常たくない動的リソース参照の検索動作は、検索結果は予測可能で自己完結型のテーマにように代わりに静的リソース参照の動作をしますか。 動的リソース参照で、テーマでの参照のままもが、実行時まで評価し、テーマが適用されている、ローカルのいくつかの要素を参照しようとして、テーマ キーを再定義し、ローカルの要素を前に分類されます可能性があります。検索で自体テーマ。 その場合は、テーマは予期したとおりに動作しません。  
  
-   多数の依存関係プロパティを設定するのには、リソースを使用しています。 依存関係プロパティでは、有効な値がプロパティ システムによって有効になっているため、読み込み時に評価される依存関係プロパティの値を指定する場合、依存関係プロパティ reevaluated 式を確認する必要はありませんおよび返すことができますをキャッシュします最後の有効な値。 この方法は、パフォーマンスが向上します。  
  
-   すべてのコンシューマーの基になるリソースを変更するかを使用して、各コンシューマーの書き込み可能な個別のインスタンスを保持したい、 [x: 共有属性](../../xaml-services/x-shared-attribute.md)します。  
  
#### <a name="static-resource-lookup-behavior"></a>静的リソース参照動作  
  
1.  プロパティを設定する要素によって定義されたリソース ディクショナリ内で要求されたキーの参照プロセスを確認します。  
  
2.  参照プロセスは、親要素とそのリソース ディクショナリにし、論理ツリーを上を走査します。 これは、ルート要素に達するまで続きます。  
  
3.  次に、アプリケーションのリソースがチェックされます。 アプリケーション リソースで定義されているリソース ディクショナリ内では、<xref:System.Windows.Application>オブジェクト、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]アプリケーション。  
  
 リソース ディクショナリ内の静的リソース参照では、既に定義されている構文的リソース参照の前にリソースを参照する必要があります。 静的リソース参照では、前方参照を解決できません。 このため、静的リソース参照を使用する場合する必要があります構造を設計する、リソース ディクショナリで、または各リソース ディクショナリの先頭付近に、リソースで使用するためのリソースが定義されているようにします。  
  
 静的リソース参照は、テーマまたはシステム リソースを拡張できますが、だけであるためこれはサポートされて、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]ローダーによって要求が遅延します。 ページの読み込み時にランタイムのテーマは、アプリケーションに正しく適用できるように、遅延する必要があります。 ただし、テーマまたはシステム リソースは推奨されませんとしてのみ存在することが知られているキーに静的リソースを参照します。 これは、テーマがリアルタイムでユーザーが変更された場合、このような参照が再評価されないためにです。 テーマまたはシステム リソースを要求すると、動的リソース参照はより信頼性の高いです。 テーマ要素自体が別のリソースを要求したときに例外です。 これらの参照の前に説明した理由から、静的リソース参照があります。  
  
 静的リソース参照が見つからない場合は、例外動作によって異なります。 リソースが延期された場合は、実行時に例外が発生します。 リソースを遅延しませんが、読み込み時に、例外が発生します。  
  
### <a name="dynamic-resources"></a>動的リソース  
 次の状況に最適な動的リソース。  
  
-   リソースの値は、実行時までわからない条件によって異なります。 これには、システム リソース、または他のユーザー設定可能なリソースが含まれます。 によって公開されていると、システムのプロパティを参照する set アクセス操作子の値を作成するなど<xref:System.Windows.SystemColors>、 <xref:System.Windows.SystemFonts>、または<xref:System.Windows.SystemParameters>します。 これらの値は、ユーザーとオペレーティング システムのランタイム環境から最終的になるため、完全に動的です。 ページ レベル リソースへのアクセス、変更のキャプチャをする必要がありますも、変更できるアプリケーション レベルのテーマもあります。  
  
-   作成するカスタム コントロールのテーマのスタイルを参照します。  
  
-   内容を調整する、<xref:System.Windows.ResourceDictionary>アプリケーションの有効期間中にします。  
  
-   前方参照が必要に、依存関係を持つ構造の複雑なリソースがあります。 静的リソース参照は、前方参照をサポートしていませんが、動的リソース参照をサポートしてそれらのリソースが、実行時まで評価する必要がないため、前方参照でないため、関連する概念。  
  
-   コンパイルまたはワーキング セットの観点から、特に大規模なリソースを参照しているし、ページが読み込まれるときにすぐに、リソースを使用しない場合があります。 静的リソース参照を常に読み込む[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]ページの読み込み。 ただし、動的リソース参照まで読み込まれませんが、実際に使用します。  
  
-   Set アクセス操作子の値がテーマやその他のユーザー設定の影響を受けるその他の値を元のスタイルを作成します。  
  
-   要素が親を再指定論理ツリーでアプリケーションの有効期間中にリソースを適用します。 リソース ルックアップ スコープを変更して、親を変更することもありますので、する場合は、リソースに再評価をこの要素の新しい範囲に基づく、常に使用して、動的リソース参照。  
  
#### <a name="dynamic-resource-lookup-behavior"></a>動的リソース参照動作  
 呼び出す場合、動的リソース参照のリソースの検索の動作は、コード内の検索の動作に対応して<xref:System.Windows.FrameworkElement.FindResource%2A>または<xref:System.Windows.FrameworkElement.SetResourceReference%2A>します。  
  
1.  プロパティを設定する要素によって定義されたリソース ディクショナリ内で要求されたキーの参照プロセスを確認します。  
  
    -   要素が定義されている場合、<xref:System.Windows.FrameworkElement.Style%2A>プロパティ、<xref:System.Windows.Style.Resources%2A>ディクショナリ内で、<xref:System.Windows.Style>がチェックされます。  
  
    -   要素が定義されている場合、<xref:System.Windows.Controls.Control.Template%2A>プロパティ、<xref:System.Windows.FrameworkTemplate.Resources%2A>ディクショナリ内で、<xref:System.Windows.FrameworkTemplate>がチェックされます。  
  
2.  参照プロセスは、親要素とそのリソース ディクショナリにし、論理ツリーを上を走査します。 これは、ルート要素に達するまで続きます。  
  
3.  次に、アプリケーションのリソースがチェックされます。 アプリケーション リソースで定義されているリソース ディクショナリ内では、<xref:System.Windows.Application>オブジェクト、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]アプリケーション。  
  
4.  現在アクティブなテーマのテーマのリソース ディクショナリがチェックされます。 実行時にテーマが変更された場合、値が再評価されます。  
  
5.  システム リソースがチェックされます。  
  
 (あれば) 例外の動作が異なります。  
  
-   リソースが要求した場合、<xref:System.Windows.FrameworkElement.FindResource%2A>を呼び出すし、見つからなかった、例外が発生します。  
  
-   リソースが要求した場合、<xref:System.Windows.FrameworkElement.TryFindResource%2A>を呼び出すし、見つからなかった、例外は発生しませんが、返される値は`null`します。 設定されるプロパティを受け入れない場合`null`、詳細な例外が発生することも可能にし、(これは設定されている個々 のプロパティに依存)。  
  
-   動的リソース参照によってリソースが要求されたかどうか[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]が見つかりませんでしたとし、動作は、[全般] プロパティ システムによって異なりますが、全般的な動作は、リソースが存在するレベルのプロパティ設定操作が発生しなかったかのようです。 たとえばの背景を設定しようとした場合、評価できないリソースを使用して、個々 のボタン要素値の設定はありません、結果がプロパティ システムと値の優先順位の他の参加者から有効な値が決まることができます。 たとえば、バック グラウンド値がローカルに定義されたボタンのスタイル、またはテーマ スタイルから決まる場合があります。 テーマ スタイルによって定義されていないプロパティの場合は、失敗したリソースの評価後に有効な値は、プロパティ メタデータの既定値から取得可能性があります。  
  
#### <a name="restrictions"></a>制約  
 動的リソース参照では、いくつか注目すべき制限があります。 次の少なくとも 1 つは true である必要があります。  
  
-   設定されているプロパティのプロパティである必要があります、<xref:System.Windows.FrameworkElement>または<xref:System.Windows.FrameworkContentElement>します。 プロパティをバックアップする必要がある、<xref:System.Windows.DependencyProperty>します。  
  
-   内の値が参照されて、<xref:System.Windows.Style><xref:System.Windows.Setter>します。  
  
-   設定されているプロパティのプロパティである必要があります、<xref:System.Windows.Freezable>いずれかの値として提供されている、<xref:System.Windows.FrameworkElement>または<xref:System.Windows.FrameworkContentElement>プロパティ、または<xref:System.Windows.Setter>値。  
  
 プロパティが設定されている必要があるので、<xref:System.Windows.DependencyProperty>または<xref:System.Windows.Freezable>プロパティ、プロパティ変更のほとんどに伝達できます UI プロパティの変更 (動的なリソースが変更された値) の受信がプロパティ システムによって確認するためです。 ほとんどのコントロールが場合は、コントロールの別のレイアウトを強制的にロジックを含む、<xref:System.Windows.DependencyProperty>変更とプロパティがレイアウトに影響を与えます。 ただし、すべてのプロパティがある、 [DynamicResource マークアップ拡張機能](dynamicresource-markup-extension.md)それらの値として、UI にリアルタイムで更新するように値を提供する保証されます。 その機能は、によって、プロパティと、プロパティ、またはアプリケーションの論理構造を所有する型によって使用異なる場合がありますもします。  
  
<a name="stylesimplicitkeys"></a>   
## <a name="styles-datatemplates-and-implicit-keys"></a>スタイル、Datatemplate、および暗黙的なキー  
 以前では、示されていました内の項目をすべて、<xref:System.Windows.ResourceDictionary>キーを持っている必要があります。 ただし、いないわけでは、明示的なすべてのリソースである必要があります`x:Key`します。 いくつかのオブジェクト型では、別のプロパティの値に関連付けられた、キー値をリソースとして定義されている場合に暗黙のキーをサポートします。 一方、暗黙のキーと呼ばれます、`x:Key`属性は、明示的なキー。 明示的なキーを指定することによって、暗黙のキーを上書きできます。  
  
 リソースの 1 つの非常に重要なシナリオは、定義する場合、<xref:System.Windows.Style>します。 実際を<xref:System.Windows.Style>スタイルは本質的に再利用するためのものであるため、リソース ディクショナリのエントリとしてはほぼ常に定義します。 スタイルの詳細については、次を参照してください。[スタイルとテンプレート](../controls/styling-and-templating.md)します。  
  
 コントロールのスタイルで作成およびできる暗黙のキーを参照します。 コントロールの既定の外観を定義するテーマ スタイルは、この暗黙のキーに依存します。 要求の観点からは、暗黙のキーは、<xref:System.Type>コントロール自体の。 リソースの定義の観点からは、暗黙のキーは、<xref:System.Windows.Style.TargetType%2A>のスタイル。 そのため、カスタム コントロールのテーマを作成する場合、既存のテーマ スタイルを使用して対話するスタイルを作成する必要はありませんを指定する、 [X:key ディレクティブ](../../xaml-services/x-key-directive.md)を<xref:System.Windows.Style>します。 テーマ スタイルを使用する場合はまったく任意のスタイルを指定する必要はありません。 たとえば、次のスタイル定義の動作、場合でも、<xref:System.Windows.Style>キーにするリソースは表示されません。  
  
 [!code-xaml[FEResourceSH_snip#ImplicitStyle](~/samples/snippets/csharp/VS_Snippets_Wpf/FEResourceSH_snip/CS/page2.xaml#implicitstyle)]  
  
 あるスタイル実際には、キーが: 暗黙のキー`typeof(`<xref:System.Windows.Controls.Button>`)`します。 マークアップでは、指定することができます、<xref:System.Windows.Style.TargetType%2A>型として直接指定して (または、必要に応じて使用することができます[{X:type...}](../../xaml-services/x-type-markup-extension.md) 返す、<xref:System.Type>します。  
  
 使用される既定のテーマ スタイルのメカニズムを通じて[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]のランタイム スタイルとしてスタイルが適用されることを<xref:System.Windows.Controls.Button> ページで、場合でも、<xref:System.Windows.Controls.Button>自体を指定しません、<xref:System.Windows.FrameworkElement.Style%2A>プロパティまたは特定のリソーススタイルへの参照します。 ページで定義されているスタイルはテーマ ディクショナリのスタイルと同じキーを使用して、テーマ ディクショナリ スタイルより参照シーケンスの前にあります。 指定することだけでした`<Button>Hello</Button>` ページで、およびスタイルで定義されている任意の場所で<xref:System.Windows.Style.TargetType%2A>の`Button`そのボタンに適用されます。 同じ型の値を持つスタイルを明示的に引き続きキーことができる場合は、 <xref:System.Windows.Style.TargetType%2A>、わかりやすくするため、マークアップでは省略可能です。  
  
 場合、スタイルの暗黙的なキーは、コントロールに適用されません<xref:System.Windows.FrameworkElement.OverridesDefaultStyle%2A>は`true`(またを注意<xref:System.Windows.FrameworkElement.OverridesDefaultStyle%2A>ネイティブの動作、コントロール クラスではなく明示的に、コントロールのインスタンスの一部として設定することがあります)。 また、暗黙的なキーの派生クラスのシナリオをサポートするために、制御する必要がありますオーバーライド<xref:System.Windows.FrameworkElement.DefaultStyleKey%2A>(の一部として提供されるすべての既存コントロール[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]これを行う)。 スタイル、テーマ、およびコントロールのデザインの詳細については、次を参照してください。[スタイルのコントロールを設計するためのガイドライン](../controls/guidelines-for-designing-stylable-controls.md)します。  
  
 <xref:System.Windows.DataTemplate> 暗黙のキーがあります。 暗黙のキーを<xref:System.Windows.DataTemplate>は、<xref:System.Windows.DataTemplate.DataType%2A>プロパティの値。 <xref:System.Windows.DataTemplate.DataType%2A> 明示的に使用するのではなく、型の名前として指定することも[{X:type...}](../../xaml-services/x-type-markup-extension.md). 詳細については、次を参照してください。[データ テンプレートの概要](../data/data-templating-overview.md)します。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.ResourceDictionary>
- [アプリケーション リソース](optimizing-performance-application-resources.md)
- [リソースとコード](resources-and-code.md)
- [リソースを定義および参照する](how-to-define-and-reference-a-resource.md)
- [アプリケーション管理の概要](../app-development/application-management-overview.md)
- [x:Type マークアップ拡張機能](../../xaml-services/x-type-markup-extension.md)
- [StaticResource のマークアップ拡張機能](staticresource-markup-extension.md)
- [DynamicResource のマークアップ拡張機能](dynamicresource-markup-extension.md)
