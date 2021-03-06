---
title: "マークアップ拡張機能と WPF XAML"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- brace character [WPF]
- Binding markup extensions [WPF]
- RelativeSource markup extensions [WPF]
- XAML [WPF], markup extensions
- markup extensions [WPF]
- nesting extension syntax [WPF]
- curly brace characters ({})
- TemplateBinding markup extensions [WPF]
- StaticResource markup extensions [WPF]
- literal curly brace characters ({})
- characters [WPF], curly brace
- DynamicResource markup extensions [WPF]
ms.assetid: 618dc745-8b14-4886-833f-486d2254bb78
caps.latest.revision: "26"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5e6dec42d40039f9cc23ba976ecf421f6471888e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="markup-extensions-and-wpf-xaml"></a>マークアップ拡張機能と WPF XAML
ここでは XAML のマークアップ拡張の概念について、構文規則、目的、その基になるクラス オブジェクト モデルなどを説明します。 マークアップ拡張は、XAML 言語、および XAML サービスの .NET 実装の一般的な機能です。 ここでは、WPF XAML で使用するマークアップ拡張について特に詳しく説明します。  
  
  
<a name="XAML_Processors_and_Markup_Extensions"></a>   
## <a name="xaml-processors-and-markup-extensions"></a>XAML プロセッサとマークアップ拡張  
 一般に、XAML パーサーは、属性値を、プリミティブに変換できるリテラル文字列として解釈するか、何らかの方法でオブジェクトに変換することができます。 そのような方法の 1 つは、型コンバーターを参照することです。この方法については、「[TypeConverters および XAML](../../../../docs/framework/wpf/advanced/typeconverters-and-xaml.md)」で説明されています。 しかし、シナリオによっては、別の動作が必要な場合もあります。 たとえば、XAML プロセッサに対して、ある属性値がオブジェクト グラフ内の新しいオブジェクトにならないように指示することがあります。 代わりに、その属性を、オブジェクト グラフの別の部分にある既に構築されたオブジェクトに対する参照を行うオブジェクト グラフ、または静的オブジェクトにする必要があります。 別のシナリオとして、XAML プロセッサに対して、オブジェクトのコンストラクターに既定以外の引数を渡す構文を使用するように指示する場合もあります。 このような種類のシナリオは、マークアップ拡張によって解決できます。  
  
<a name="Basic_Markup_Extension_Syntax"></a>   
## <a name="basic-markup-extension-syntax"></a>マークアップ拡張の基本構文  
 マークアップ拡張を実装すると、属性の使用でのプロパティ、プロパティ要素の使用でのプロパティ、またはその両方の値を提供できます。  
  
 属性値を提供するために使用する場合、XAML プロセッサでマークアップ拡張シーケンスを区別する構文は、左中かっこと右中かっこ ({ と }) です。 その後、マークアップ拡張の種類は、左中かっこの直後の文字列トークンによって識別されます。  
  
 プロパティ要素構文で使用する場合、マークアップ拡張は、プロパティ要素値の指定に使用するその他の要素と表示上は同じになります。つまり、山かっこ (<>) で囲まれた、マークアップ拡張クラスを要素として参照する XAML 要素宣言になります。  
  
<a name="XAML_Defined_Markup_Extensions"></a>   
## <a name="xaml-defined-markup-extensions"></a>XAML で定義されたマークアップ拡張機能  
 XAML の WPF 実装に固有ではなく、言語としての XAML の組み込みまたは機能の実装であるマークアップ拡張がいくつか存在します。 これらのマークアップ拡張は、一般的な .NET Framework XAML サービスの一部として System.Xaml アセンブリで実装され、XAML 言語の XAML 名前空間内にあります。 これらのマークアップ拡張は、一般的なマークアップの使用方法では、通常、`x:` プレフィックスで識別できます。 <xref:System.Windows.Markup.MarkupExtension> (また、System.Xaml で定義された) ベースのクラスには、すべてのマークアップ拡張機能が XAML リーダーと XAML ライター、WPF XAML でなどではサポートするために使用するパターンが用意されています。  
  
-   `x:Type` は、名前を指定した型の <xref:System.Type> オブジェクトを提供します。 この機能は、スタイルとテンプレートで最もよく使用されます。 詳細については、「[x:Type マークアップ拡張機能](../../../../docs/framework/xaml-services/x-type-markup-extension.md)」を参照してください。  
  
-   `x:Static` は、静的な値を生成します。 この値は、直接的にはターゲット プロパティの値の型ではなくても、その型に評価することができる値型コード エンティティから生成されます。 詳細については、「[x:Static マークアップ拡張機能](../../../../docs/framework/xaml-services/x-static-markup-extension.md)」を参照してください。  
  
-   `x:Null` は、プロパティの値として `null` を指定し、属性またはプロパティ要素の値として使用できます。 詳細については、「[x:Null マークアップ拡張機能](../../../../docs/framework/xaml-services/x-null-markup-extension.md)」を参照してください。  
  
-   `x:Array` は、XAML 構文での一般的な配列の作成をサポートします。WPF 基本要素とコントロール モデルで提供されているコレクションのサポートをあえて使用しない場合に使用します。 詳細については、「[x:Array Markup Extension](../../../../docs/framework/xaml-services/x-array-markup-extension.md)」を参照してください。  
  
> [!NOTE]
>  `x:` プレフィックスは、XAML 言語の組み込みに対する標準的な XAML 名前空間マッピングのために、XAML ファイルまたは稼働環境のルート要素で使用します。 たとえば、WPF アプリケーション用の [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] テンプレートでは、XAML ファイルの先頭でこの `x:` マッピングを使用しています。 独自の XAML 名前空間マッピングに別のプレフィックス トークンを選ぶこともできますが、このドキュメントでは、WPF の既定の名前空間や、特定のフレームワークに関連のないその他の XAML 名前空間ではなく、XAML 言語の XAML 名前空間の一部として定義されているエンティティを識別する手段として、既定の `x:` マッピングを想定します。  
  
<a name="WPF_Specific_Markup_Extensions"></a>   
## <a name="wpf-specific-markup-extensions"></a>WPF 固有のマークアップ拡張  
 WPF プログラミングで使用される最も一般的なマークアップ拡張には、リソースの参照をサポートするもの (`StaticResource` と `DynamicResource`) と、データ バインディングをサポートするもの (`Binding`) があります。  
  
-   `StaticResource` は、既に定義されているリソースの値を代入することによって、プロパティの値を提供します。 `StaticResource` の評価は、最終的には XAML の読み込み時に行われます。実行時にオブジェクト グラフにアクセスすることはできません。 詳細については、「[StaticResource のマークアップ拡張機能](../../../../docs/framework/wpf/advanced/staticresource-markup-extension.md)」を参照してください。  
  
-   `DynamicResource` は、プロパティの値がリソースに対する実行時参照になるように延期することによって、プロパティの値を提供します。 動的リソース参照では、そのようなリソースがアクセスされるたびに、強制的に新しいルックアップが行われます。実行時にオブジェクト グラフにアクセスすることもできます。 このようなアクセスを実現するために、`DynamicResource` の概念が、WPF プロパティ システムの依存関係プロパティと、評価された式によってサポートされます。 したがって、`DynamicResource` は、依存関係プロパティ ターゲットにのみ使用できます。 詳細については、「[DynamicResource のマークアップ拡張機能](../../../../docs/framework/wpf/advanced/dynamicresource-markup-extension.md)」を参照してください。  
  
-   `Binding` は、実行時に親オブジェクトに適用されるデータ コンテキストを使用して、データ バインディングされた値をプロパティに提供します。 このマークアップ拡張は、データ バインディングを指定するためにかなりの量のインライン構文を使用できるため、比較的複雑です。 詳細については、「[バインディングのマークアップ拡張機能](../../../../docs/framework/wpf/advanced/binding-markup-extension.md)」を参照してください。  
  
-   `RelativeSource`ソース情報を提供する<xref:System.Windows.Data.Binding>実行時のオブジェクト ツリーで、いくつかの可能なリレーションシップを移動することができます。 これにより、周囲のオブジェクト ツリーに関する完全な知識がなくても、多目的のテンプレートで作成されるバインド、またはコードで作成されるバインドに対して、特殊なソースを指定することができます。 詳細については、「[RelativeSource のマークアップ拡張機能](../../../../docs/framework/wpf/advanced/relativesource-markupextension.md)」を参照してください。  
  
-   `TemplateBinding` により、コントロール テンプレートがテンプレート プロパティの値を使用できるようになります。それらの値は、テンプレートを使用するクラスのオブジェクト モデルで定義されたプロパティから取られます。 つまり、テンプレート定義内のプロパティが、テンプレートを適用する場合にのみ存在するコンテキストにアクセスできます。 詳細については、「[TemplateBinding のマークアップ拡張機能](../../../../docs/framework/wpf/advanced/templatebinding-markup-extension.md)」を参照してください。 `TemplateBinding` の実際の使用方法の詳細については、「[ControlTemplate を使用したスタイル設定のサンプル](http://go.microsoft.com/fwlink/?LinkID=160041)」を参照してください。  
  
-   `ColorConvertedBitmap` は、比較的高度なイメージング シナリオをサポートします。 詳細については、「[ColorConvertedBitmap のマークアップ拡張機能](../../../../docs/framework/wpf/advanced/colorconvertedbitmap-markup-extension.md)」を参照してください。  
  
-   `ComponentResourceKey` と `ThemeDictionary` は、リソースのルックアップをサポートします。特に、カスタム コントロールでパッケージ化されるリソースとテーマを対象としています。 詳細については、「[ComponentResourceKey マークアップ拡張機能](../../../../docs/framework/wpf/advanced/componentresourcekey-markup-extension.md)」、「[ThemeDictionary のマークアップ拡張機能](../../../../docs/framework/wpf/advanced/themedictionary-markup-extension.md)」、「[コントロールの作成の概要](../../../../docs/framework/wpf/controls/control-authoring-overview.md)」を参照してください。  
  
<a name="StarExtension"></a>   
## <a name="extension-classes"></a>*Extension クラス  
 一般的な XAML の言語と WPF 固有のマークアップ拡張機能の両方で各マークアップ拡張機能の動作は識別を介して XAML プロセッサに対して、`*Extension`から派生したクラス<xref:System.Windows.Markup.MarkupExtension>の実装を提供し、 <xref:System.Windows.Markup.StaticExtension.ProvideValue%2A>メソッド。 各拡張にあるこのメソッドは、マークアップ拡張の評価時に返されるオブジェクトを提供します。 返されるオブジェクトは、通常、マークアップ拡張に渡されたさまざまな文字列トークンに基づいて評価されます。  
  
 たとえば、<xref:System.Windows.StaticResourceExtension>クラスの実際のリソースの参照の表面の実装を提供できるようにその<xref:System.Windows.Markup.MarkupExtension.ProvideValue%2A>実装するために使用される文字列の中に実装する特定の入力を要求したオブジェクトが返されますリソースを検索、`x:Key`です。 既存のマークアップ拡張を使用している場合は、この実装の詳細の大部分は重要ではありません。  
  
 一部のマークアップ拡張では、文字列トークン引数は使用されません。 これは、それらのマークアップ拡張では静的な値や一貫した値が返されるため、または返されるべき値のコンテキストが `serviceProvider` パラメーターを介して渡されるサービスの 1 つから得られるためです。  
  
 `*Extension` 名前付けパターンは、便宜上のものであり、一貫性を確保するためのものです。 XAML プロセッサがマークアップ拡張のサポートとしてそのクラスを識別するためには必要ではありません。 コードベースは System.Xaml が含まれていて、.NET Framework XAML サービス実装を使用する限り、すべて必要がある認識されるために XAML マークアップ拡張機能はから派生するという<xref:System.Windows.Markup.MarkupExtension>構築構文をサポートするとします。 WPF のマークアップ拡張機能を有効にするクラスが定義に従っていない、`*Extension`など、パターンの名前を付け<xref:System.Windows.Data.Binding>です。 通常、純粋なマークアップ拡張のサポートを超えたシナリオをそのクラスがサポートすることが原因です。 場合、<xref:System.Windows.Data.Binding>クラスは、XAML を行うには何が含まれる場合のオブジェクトのメソッドとプロパティへの実行時アクセスをサポートします。  
  
### <a name="extension-class-interpretation-of-initialization-text"></a>初期化テキストの拡張クラスの解釈  
 マークアップ拡張名の後に続き、中かっこの内側にある文字列トークンは、次の方法のいずれかで XAML プロセッサに解釈されます。  
  
-   コンマは常に個別のトークンの区切りまたは区切り記号を表します。  
  
-   個別の区切られたトークンに等号が含まれない場合、各トークンはコンストラクター引数として扱われます。 各コンストラクター パラメーターは、そのシグネチャで想定される型として、そのシグネチャで想定される適切な順序で指定する必要があります。  
  
    > [!NOTE]
    >  XAML プロセッサは、ペアの数の引数の数に一致するコンストラクターを呼び出す必要があります。 このため、カスタム マークアップ拡張を実装する場合は、複数のパラメーターに同じ引数の数を指定しないでください。 パラメーターの数が同じマークアップ拡張コンストラクター パスが複数存在する場合の XAML プロセッサの動作は、定義されていません。ただし、マークアップ拡張の型定義がこのような状態になっていると、使用方法に関する例外が XAML プロセッサからスローされる可能性があることを想定しておく必要があります。  
  
-   個別の区切られたトークンに等号が含まれている場合、XAML プロセッサは最初にマークアップ拡張の既定のコンストラクターを呼び出します。 その後、各 "名前=値" のペアは、マークアップ拡張に存在するプロパティ名、およびそのプロパティに割り当てる値として解釈されます。  
  
-   マークアップ拡張でコンストラクターの動作とプロパティの設定の動作の結果が類似している場合は、どちらの動作を使用しても問題はありません。 複数の設定可能なプロパティを持つマークアップ拡張では、"*プロパティ*`=`*値*" のペアの方がよく使用されます。単に、その方がマークアップの意図が明確になり、コンストラクター パラメーターを間違って入れ替える可能性も低いためです。 ("プロパティ=値" のペアを指定すると、それらのプロパティは任意の順序になります。)また、設定可能なプロパティのすべてを設定するコンストラクター パラメーターがマークアップ拡張によって提供されるという保証はありません。 たとえば、<xref:System.Windows.Data.Binding>マークアップ拡張機能、設定の拡張機能を使用できる多くのプロパティでは、*プロパティ*`=`*値*フォームが<xref:System.Windows.Data.Binding>のみ 2 をサポートコンス トラクター: 既定のコンス トラクターと最初のパスを設定する 1 つです。  
  
-   リテラルのコンマは、エスケープせずにマークアップ拡張に渡すことはできません。  
  
<a name="EscapeSequences"></a>   
## <a name="escape-sequences-and-markup-extensions"></a>エスケープ シーケンスとマークアップ拡張  
 XAML プロセッサによる属性の処理では、マークアップ拡張シーケンスのインジケーターとして中かっこを使用します。 必要に応じて、空の中かっこペアの後にリテラル中かっこを使用したエスケープ シーケンスを入力することによって、リテラル中かっこ文字の属性値を生成することもできます。 参照してください[{} エスケープ シーケンスのマークアップ拡張機能](../../xaml-services/escape-sequence-markup-extension.md)します。  
  
<a name="Nesting"></a>   
## <a name="nesting-markup-extensions-in-xaml-usage"></a>XAML の使用におけるマークアップ拡張の入れ子  
 複数のマークアップ拡張を入れ子にすることができます。各マークアップ拡張は、最も深いものが最初に評価されます。 たとえば、次のような使用方法があります。  
  
```  
<Setter Property="Background"  
  Value="{DynamicResource {x:Static SystemColors.ControlBrushKey}}" />  
```  
  
 この使用方法では、`x:Static` ステートメントが最初に評価され、文字列を返します。 この文字列が、`DynamicResource` の引数として使用されます。  
  
## <a name="markup-extensions-and-property-element-syntax"></a>マークアップ拡張とプロパティ要素構文  
 マークアップ拡張クラスは、プロパティ要素値を設定するオブジェクト要素として使用した場合、XAML で使用可能な通常の型に基づくオブジェクト要素と見た目上は区別できません。 通常のオブジェクト要素とマークアップ拡張の実用上の違いは、マークアップ拡張は、型指定された値に評価されるか、式として処理が遅延されるかのどちらかであることです。 したがって、マークアップ拡張のプロパティ値について発生する可能性のある型エラーのメカニズムは異なります。これは、他のプログラミング モデルにおける遅延バインディング プロパティの処理方法と似ています。 通常のオブジェクト要素では、XAML が解析される時点で、そのオブジェクト要素が設定しているターゲット プロパティに対して型の一致が評価されます。  
  
 ほとんどのマークアップ拡張は、プロパティ要素を指定するオブジェクト要素構文で使用される場合、内側にコンテンツや他のプロパティ要素構文を含みません。 このため、オブジェクト要素タグを閉じ、子要素は指定しません。 オブジェクト要素が XAML プロセッサで検出されるたびに、そのクラスのコンストラクターが呼び出され、解析した要素から作成されたオブジェクトがインスタンス化されます。 マークアップ拡張クラスも同じです。マークアップ拡張をオブジェクト要素構文で使用できるようにする場合は、既定のコンストラクターを用意する必要があります。 既存のマークアップ拡張の中には、有効な初期化のために指定する必要のある必須プロパティ値を少なくとも 1 つ持っているものがあります。 その場合、通常、そのプロパティ値はオブジェクト要素のプロパティ属性として指定します。 「[XAML 名前空間 (x:) 言語機能](../../../../docs/framework/xaml-services/xaml-namespace-x-language-features.md)」および「[WPF XAML 拡張機能](../../../../docs/framework/wpf/advanced/wpf-xaml-extensions.md)」の各リファレンス ページで、必須プロパティを持つマークアップ拡張 (および必須プロパティの名前) について説明します。 これらのリファレンス ページでは、特定のマークアップ拡張でオブジェクト要素構文と属性構文のどちらかが使用できないケースについても説明します。 特に注意する必要があるケースは、[x:Array マークアップ拡張](../../../../docs/framework/xaml-services/x-array-markup-extension.md)です。このマークアップ拡張では、配列の内容をタグ設定の内側にコンテンツとして指定する必要があるため、属性構文をサポートできません。 配列の内容は一般的なオブジェクトとして扱われるため、属性に対する既定の型コンバーターは使用できません。 また、[x:Array マークアップ拡張](../../../../docs/framework/xaml-services/x-array-markup-extension.md)には `type` パラメーターが必要です。  
  
## <a name="see-also"></a>参照  
 [XAML の概要 (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)  
 [XAML 名前空間 (x:) 言語機能](../../../../docs/framework/xaml-services/xaml-namespace-x-language-features.md)  
 [WPF XAML 拡張機能](../../../../docs/framework/wpf/advanced/wpf-xaml-extensions.md)  
 [StaticResource のマークアップ拡張機能](../../../../docs/framework/wpf/advanced/staticresource-markup-extension.md)  
 [バインドのマークアップ拡張機能](../../../../docs/framework/wpf/advanced/binding-markup-extension.md)  
 [DynamicResource マークアップ拡張](../../../../docs/framework/wpf/advanced/dynamicresource-markup-extension.md)  
 [x:Type マークアップ拡張機能](../../../../docs/framework/xaml-services/x-type-markup-extension.md)
