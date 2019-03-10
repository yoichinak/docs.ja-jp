---
title: Windows ストア アプリおよび Windows ランタイムのための .NET Framework サポート
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- Windows Store apps, .NET Framework support for
- Windows Runtime, .NET Framework support for
- .NET for Windows Store apps
- .NET Framework, and Windows Store apps
- .NET Framework, and Windows Runtime
ms.assetid: 6fa7d044-ae12-4c54-b8ee-50915607a565
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 750bddce508a72c6aaac659feac90b7c17e53137
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/09/2019
ms.locfileid: "57708406"
---
# <a name="net-framework-support-for-windows-store-apps-and-windows-runtime"></a>Windows ストア アプリおよび Windows ランタイムのための .NET Framework サポート

  [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] は [!INCLUDE[wrt](../../../includes/wrt-md.md)]のさまざまなソフトウェア開発シナリオをサポートします。 これらのシナリオは次の 3 つのカテゴリに分類されます。

-   開発[!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)]」の説明に従って、XAML コントロールを使用したアプリ[ロードマップの Windows ストア アプリを c# または Visual Basic を使用して](https://docs.microsoft.com/previous-versions/windows/apps/br229583(v=win.10))、[方法操作方法 (XAML)](https://docs.microsoft.com/previous-versions/windows/apps/br229566(v=win.10))、および[.NET Windows ストア アプリの概要](https://docs.microsoft.com/previous-versions/windows/apps/br230302(v=vs.140)).

-   .NET Framework で作成する [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] アプリで使用するクラス ライブラリを開発する。

-   .WinMD ファイルにパッケージ化され、[!INCLUDE[wrt](../../../includes/wrt-md.md)]をサポートするすべてのプログラミング言語で使用できる、[!INCLUDE[wrt](../../../includes/wrt-md.md)] コンポーネントを開発する。 たとえばを参照してください[c# および Visual Basic での Windows ランタイム コンポーネントの作成](/windows/uwp/winrt-components/creating-windows-runtime-components-in-csharp-and-visual-basic)です。

 このトピックでは、3 つのカテゴリすべてに対して .NET Framework が提供するサポートの概略と、[!INCLUDE[wrt](../../../includes/wrt-md.md)] コンポーネント用シナリオについて説明します。 最初のセクションでは、.NET Framework と [!INCLUDE[wrt](../../../includes/wrt-md.md)]の関係についての基本情報と、ヘルプ システムや IDE で見られる可能性がある特異な状況について説明します。 [2 番目のセクション](#WindowsRuntimeComponents)を開発するためのシナリオについて説明します[!INCLUDE[wrt](../../../includes/wrt-md.md)]コンポーネント。

## <a name="the-basics"></a>基本事項
 .NET Framework は、[!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)] を提供することと [!INCLUDE[wrt](../../../includes/wrt-md.md)]自体をサポートすることによって、前述の 3 つの開発シナリオをサポートします。

-   [.NET framework と Windows ランタイム名前空間](https://docs.microsoft.com/previous-versions/windows/apps/br230302(v=vs.140)#net-framework-and-windows-runtime-namespaces)、.NET Framework クラス ライブラリの簡素化されたビューを示し、型と作成に使用できるメンバーのみを含める[!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)]アプリと[!INCLUDE[wrt](../../../includes/wrt-md.md)]コンポーネント。

    -   Visual Studio (Visual Studio 2012 またはそれ以降) を使用して開発するときに、[!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)]アプリまたは[!INCLUDE[wrt](../../../includes/wrt-md.md)]コンポーネント、参照アセンブリのセットにより、関連する型とメンバーのみが表示されます。

    -   この簡素化された API セットは、.NET Framework 内で重複した機能、または [!INCLUDE[wrt](../../../includes/wrt-md.md)]の機能と重複した機能を削除すると、さらに単純化できます。 たとえば、簡素化された API セットにはコレクション型のジェネリック バージョンのみが含まれ、XML ドキュメント オブジェクト モデルは削除されて、代わりに [!INCLUDE[wrt](../../../includes/wrt-md.md)] XML API セットが使用されます。

    -   オペレーティング システムの API をラップするだけの機能も削除されます。これは、[!INCLUDE[wrt](../../../includes/wrt-md.md)] をマネージド コードから簡単に呼び出すことができるためです。

     詳細について、[!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)]を参照してください、 [.NET Windows ストア アプリの概要](https://docs.microsoft.com/previous-versions/windows/apps/br230302(v=vs.140))します。 API 選択プロセスについては、次を参照してください。、 [Metro スタイル アプリ用 .NET](https://devblogs.microsoft.com/dotnet/net-for-metro-style-apps/) .NET ブログのエントリ。

-   [Windows ランタイム](/uwp/api/)構築するためのユーザー インターフェイス要素を提供します[!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)]アプリ、およびオペレーティング システムの機能へのアクセスを提供します。 .NET Framework と同様、[!INCLUDE[wrt](../../../includes/wrt-md.md)]には、C# や Visual Basic のコンパイラが .NET Framework クラス ライブラリを使用するのと同じ方法で [!INCLUDE[wrt](../../../includes/wrt-md.md)]を使用するためのメタデータが含まれています。 .NET Framework では、一部の相違点を非表示にすることで [!INCLUDE[wrt](../../../includes/wrt-md.md)]が使いやすくなっています。

    -   .NET Framework と [!INCLUDE[wrt](../../../includes/wrt-md.md)]間のプログラミング パターン (イベント ハンドラーを追加および削除するパターンなど) の違いの一部が非表示になります。 ユーザーは .NET Framework のパターンを使用するとよいだけです。

    -   よく使用される型 (たとえばプリミティブ型やコレクション) の違いの一部が非表示になります。 説明したように単純に .NET Framework 型を使用する[の相違点で表示される IDE](#DifferencesVisibleInIDE)、この記事で後述します。

 ほとんどの場合、[!INCLUDE[wrt](../../../includes/wrt-md.md)]の .NET Framework サポートは透過的です。 次のセクションでは、マネージド コードと [!INCLUDE[wrt](../../../includes/wrt-md.md)]との明確な違いのいくつかについて説明します。

<a name="AboutReferenceDocumentation"></a>
### <a name="the-net-framework-and-the-includewrtincludeswrt-mdmd-reference-documentation"></a>.NET Framework と [!INCLUDE[wrt](../../../includes/wrt-md.md)]のリファレンス ドキュメント
 Windows ランタイムと .NET Framework ドキュメント セットは、分離です。 型またはメンバーに関するヘルプを表示するために F1 キーを押すと、該当するセットのリファレンス ドキュメントが表示されます。 ただしを参照する場合、 [Windows ランタイム リファレンス](/uwp/api/)不可解と思われる例が発生する可能性があります。

-   などのトピック、<xref:Windows.Foundation.Collections.IIterable%601>インターフェイスでは、Visual Basic または c# の宣言の構文がありません。 代わりに、メモをセクションの構文上が表示されます (この場合は、".NET:このインターフェイスは System.Collections.Generic.IEnumerable として表示されます\<T >")。 これは、.NET Framework と [!INCLUDE[wrt](../../../includes/wrt-md.md)]で、同様の機能が異なるインターフェイスにより用意されているためです。 さらに、`IIterable` では列挙子を返すのに `First` メソッドではなく <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> メソッドを使用するという、動作の違いもあります。 .NET Framework では、一般的なタスクを実行する別の方法をユーザーが学習する必要はなく、使い慣れた型を使用できるようマネージド コードを表示して [!INCLUDE[wrt](../../../includes/wrt-md.md)]をサポートします。 IDE では `IIterable` インターフェイスを使用しないため、[!INCLUDE[wrt](../../../includes/wrt-md.md)]のリファレンス ドキュメントでこのインターフェイスを目にするのは、ドキュメントを直接参照する場合のみです。

-   <xref:Windows.Web.Syndication.SyndicationFeed.%23ctor(System.String,System.String,Windows.Foundation.Uri)>ドキュメントは、密接に関連する問題を示しています。さまざまな言語別に、パラメーターの型が表示されます。 C# と Visual Basic の場合、パラメーターの型は <xref:System.String?displayProperty=nameWithType> と <xref:System.Uri?displayProperty=nameWithType> です。 これもやはり、.NET Framework で独自の `String` 型と `Uri` 型が使われるためであり、このようなよく使用される型について、.NET Framework ユーザーが処理を実行する別の方法を学習しても意味はありません。 IDE では、これに対応する [!INCLUDE[wrt](../../../includes/wrt-md.md)]の型が .NET Framework によって非表示にされます。

-   いくつかの場合など、<xref:Windows.UI.Xaml.GridLength>構造体には、.NET Framework には、同じ名前が、多くの機能を持つ型。 たとえば、一連のコンストラクターとプロパティのトピックは `GridLength` に関連付けられますが、メンバーがマネージド コードでのみ使用可能であるために、Visual Basic と C# に関してのみ構文ブロックの機能を備えています。 
  [!INCLUDE[wrt](../../../includes/wrt-md.md)]では、構造体にフィールドがあるだけです。 [!INCLUDE[wrt](../../../includes/wrt-md.md)]構造はヘルパー クラスを必要と<xref:Windows.UI.Xaml.GridLengthHelper>、同等の機能を提供します。 このヘルパー クラスは、マネージド コードを記述している間は IDE に表示されません。

-   IDE では、[!INCLUDE[wrt](../../../includes/wrt-md.md)]の型は <xref:System.Object?displayProperty=nameWithType> から派生するように表示されます。 この型のメンバーは、<xref:System.Object> などの <xref:System.Object.ToString%2A?displayProperty=nameWithType> から継承されるように表示されます。 これらのメンバーは、型が実際に <xref:System.Object> から継承され、[!INCLUDE[wrt](../../../includes/wrt-md.md)]の型が <xref:System.Object> にキャストできる場合と同様に動作します。 この機能は、.NET Framework が [!INCLUDE[wrt](../../../includes/wrt-md.md)]用に用意しているサポートの一部です。 ただし、[!INCLUDE[wrt](../../../includes/wrt-md.md)]のリファレンス ドキュメントで型を表示しても、このようなメンバーは表示されません。 これらの見かけ上の継承されたメンバーに関するドキュメントは、<xref:System.Object?displayProperty=nameWithType> のリファレンス ドキュメントに含まれています。

<a name="DifferencesVisibleInIDE"></a>
### <a name="differences-that-are-visible-in-the-ide"></a>IDE で表示される相違点
 より高度なプログラミング シナリオ (例: C# で記述された [!INCLUDE[wrt](../../../includes/wrt-md.md)] コンポーネントを使い、JavaScript を使用して Windows 用にビルドされた [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] アプリのアプリケーション ロジックを提供する) では、ドキュメントと同様 IDE でもこのような相違点が表示されます。 コンポーネントから JavaScript に `IDictionary<int, string>` が返され、それを JavaScript デバッガーで調べると、JavaScript が `IMap<int, string>`の型を使用するので、[!INCLUDE[wrt](../../../includes/wrt-md.md)] のメソッドが表示されます。 よく使用されるコレクション型のうち、この 2 言語で表示が異なる型の一部を次の表に示します。

|[!INCLUDE[wrt](../../../includes/wrt-md.md)] 型|対応する .NET Framework の型|
|--------------------------------------------------------------|---------------------------------------|
|`IIterable<T>`|`IEnumerable<T>`|
|`IIterator<T>`|`IEnumerator<T>`|
|`IVector<T>`|`IList<T>`|
|`IVectorView<T>`|`IReadOnlyList<T>`|
|`IMap<K, V>`|`IDictionary<TKey, TValue>`|
|`IMapView<K, V>`|`IReadOnlyDictionary<TKey, TValue>`|
|`IBindableIterable`|`IEnumerable`|
|`IBindableVector`|`IList`|
|`Windows.UI.Xaml.Data.INotifyPropertyChanged`|`System.ComponentModel.INotifyPropertyChanged`|
|`Windows.UI.Xaml.Data.PropertyChangedEventHandler`|`System.ComponentModel.PropertyChangedEventHandler`|
|`Windows.UI.Xaml.Data.PropertyChangedEventArgs`|`System.ComponentModel.PropertyChangedEventArgs`|

 
  [!INCLUDE[wrt](../../../includes/wrt-md.md)]では、`IMap<K, V>` と `IMapView<K, V>` は `IKeyValuePair` を使用して反復されます。 これらをマネージド コードに渡すと、`IDictionary<TKey, TValue>` および `IReadOnlyDictionary<TKey, TValue>` として表示されるため、これを列挙するには必然的に `System.Collections.Generic.KeyValuePair<TKey, TValue>` を使用します。

 インターフェイスがマネージド コード内に表示される方法によって、これらのインターフェイスを実装する型の表示方法が決まります。 たとえば、`PropertySet` クラスは `IMap<K, V>` を実装しますが、これはマネージド コードでは `IDictionary<TKey, TValue>` として表示されます。 `PropertySet` は、`IDictionary<TKey, TValue>` ではなく `IMap<K, V>` を実装したかのように表示されます。したがってマネージ コードでは、`Add` メソッド (その動作は .NET Framework ディクショナリの `Add` メソッドと同様) が含まれているように表示されます。 
  `Insert` メソッドがないように見えます。

 詳細については、.NET Framework を使用して作成する方法、[!INCLUDE[wrt](../../../includes/wrt-md.md)]コンポーネント、および JavaScript で、このようなコンポーネントを使用する方法を示すチュートリアルを参照してください。 [c# および Visual Basic での Windows ランタイム コンポーネントの作成](/windows/uwp/winrt-components/creating-windows-runtime-components-in-csharp-and-visual-basic)です。

### <a name="primitive-types"></a>プリミティブ型
 マネージド コードで [!INCLUDE[wrt](../../../includes/wrt-md.md)]のナチュラルな使用を有効にすると、[!INCLUDE[wrt](../../../includes/wrt-md.md)]のプリミティブ型ではなく .NET Framework のプリミティブ型がコードに表示されます。 .NET Framework では、`Int32` 構造体などのプリミティブ型には、`Int32.TryParse` メソッドなどの便利なプロパティとメソッドが多くあります。 一方、[!INCLUDE[wrt](../../../includes/wrt-md.md)]のプリミティブ型と構造体にはフィールドしかありません。 マネージド コードでプリミティブを使用すると、.NET Framework の型のように表示され、通常どおりに .NET Framework 型のプロパティとメソッドを使用できます。 要約すると、次のようになります。

-   
  [!INCLUDE[wrt](../../../includes/wrt-md.md)]のプリミティブ `Int32`、`Int64`、`Single`、`Double`、`Boolean`、`String` (Unicode 文字の変更できないコレクション)、`Enum`、`UInt32`、`UInt64`、および `Guid` では、`System` 名前空間内の同じ名前の型を使用します。

-   
  `UInt8` では、`System.Byte` を使用します。

-   
  `Char16` では、`System.Char` を使用します。

-   
  `IInspectable` インターフェイスでは、`System.Object` を使用します。

-   
  `HRESULT` では、`System.Int32` のメンバーを 1 つ含む構造体を使用します。

 インターフェイス型の場合と同様、この表示の証拠が表示されるのは、.NET Framework プロジェクトが、JavaScript を使用してビルドされた [!INCLUDE[wrt](../../../includes/wrt-md.md)] アプリで使用される [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] コンポーネントである場合に限られます。

 .NET Framework に相当するものとしてマネージド コードに表示される、よく使用されるその他の基本的な [!INCLUDE[wrt](../../../includes/wrt-md.md)]の型には、`Windows.Foundation.DateTime` 構造体および <xref:System.DateTimeOffset?displayProperty=nameWithType> 構造体が組み込まれています。前者はマネージド コードで `Windows.Foundation.TimeSpan` 構造体として表示され、後者は <xref:System.TimeSpan?displayProperty=nameWithType> 構造体として表示されます。

### <a name="other-differences"></a>その他の相違点
 コードで [!INCLUDE[wrt](../../../includes/wrt-md.md)]の型ではなく .NET Framework の型が表示されるために、ユーザー側のアクションが必要になる場合があります。 たとえば、<xref:Windows.Foundation.Uri?displayProperty=nameWithType>クラスとして表示されます<xref:System.Uri?displayProperty=nameWithType>.NET Framework コードでします。 <xref:System.Uri?displayProperty=nameWithType> により、相対 URI ですが<xref:Windows.Foundation.Uri?displayProperty=nameWithType>絶対 URI が必要です。 したがって、[!INCLUDE[wrt](../../../includes/wrt-md.md)] メソッドに URI を渡すときには、絶対 URI にする必要があります。 (を参照してください[Windows ランタイムへの URI の引き渡し](../../../docs/standard/cross-platform/passing-a-uri-to-the-windows-runtime.md))。

<a name="WindowsRuntimeComponents"></a>
## <a name="scenarios-for-developing-windows-runtime-components"></a>Windows ランタイム コンポーネントの開発シナリオ
 
  [!INCLUDE[wrt](../../../includes/wrt-md.md)]のマネージド コンポーネントでサポートされるシナリオは、次の原則に依存します。

-   .NET Framework を使用してビルドされる [!INCLUDE[wrt](../../../includes/wrt-md.md)] コンポーネントとその他の [!INCLUDE[wrt](../../../includes/wrt-md.md)] ライブラリの間に、明確な違いはありません。 たとえば、マネージド コードを使用して [!INCLUDE[wrt](../../../includes/wrt-md.md)]のネイティブ コンポーネントを再実装する場合、この 2 つのコンポーネントは外部から見て区別が付きません。 コンポーネントがマネージド コードで記述されているという事実は、そのコード自体がマネージド コードであったとしても、そのコンポーネントを使用するコードには表示されません。 ただし内部的には、そのコンポーネントは真のマネージド コードであり、共通言語ランタイム (CLR) 上で実行されます。

-   コンポーネントには、アプリケーション ロジック、[!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] UI コントロール、またはその両方を実装する型を含めることができます。

    > [!NOTE]
    >  アプリケーション ロジックから UI 要素を分離することをお勧めします。 また、JavaScript や HTML を使用して Windows 用にビルドされた [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] アプリでは、[!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] UI コントロールを使用できません。

-   コンポーネントは、[!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] アプリ用 Visual Studio ソリューション内のプロジェクトの場合もあれば、複数のソリューションに追加できる再利用可能なコンポーネントの場合もあります。

    > [!NOTE]
    >  コンポーネントが C# または Visual Basic でのみ使用される場合は、それを [!INCLUDE[wrt](../../../includes/wrt-md.md)] コンポーネントにする必要はありません。 代わりにそれを通常の .NET Framework クラス ライブラリにすると、そのパブリック API サーフェイスを [!INCLUDE[wrt](../../../includes/wrt-md.md)]の型に制限する必要はありません。

-   使用してバージョンの再利用可能なコンポーネントを解放することができます、 [!INCLUDE[wrt](../../../includes/wrt-md.md)] <xref:Windows.Foundation.Metadata.VersionAttribute>さまざまなバージョンでどの型 (および型のメンバー) を識別するために属性が追加されました。

-   コンポーネントの型は [!INCLUDE[wrt](../../../includes/wrt-md.md)]の型から派生できます。 コントロールが内のプリミティブ コントロール型から派生できます、<xref:Windows.UI.Xaml.Controls.Primitives>名前空間または終了コントロールなどの詳細はから<xref:Windows.UI.Xaml.Controls.Button>します。

    > [!IMPORTANT]
    >  
  [!INCLUDE[win8](../../../includes/win8-md.md)] および [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] 以降では、[!INCLUDE[wrt](../../../includes/wrt-md.md)] マネージド コンポーネントのすべてのパブリック型をシールする必要があります。 別の [!INCLUDE[wrt](../../../includes/wrt-md.md)] コンポーネント内の型はそこから派生できません。 コンポーネントでポリモーフィックな動作を提供するには、インターフェイスを作成し、そのインターフェイスをポリモーフィックな型に実装します。

-   コンポーネント内のパブリック型で指定されるすべてのパラメーターと戻り値の型は、[!INCLUDE[wrt](../../../includes/wrt-md.md)]の型 (コンポーネントで定義する [!INCLUDE[wrt](../../../includes/wrt-md.md)]の型を含む) である必要があります。

 次のセクションでは、一般的なシナリオの例を示します。

### <a name="application-logic-for-a-includewin8appnamelongincludeswin8-appname-long-mdmd-app-with-javascript"></a>JavaScript による [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] アプリ用アプリケーション ロジック
 JavaScript を使用して Windows の [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] アプリを開発する場合、アプリケーション ロジックの一部が、他の部分に比べてマネージド コードでより適切に機能したり、開発が容易であったりすることがあります。 JavaScript では .NET Framework クラス ライブラリを直接使用できませんが、クラス ライブラリを .WinMD ファイルにすることができます。 このシナリオでは、[!INCLUDE[wrt](../../../includes/wrt-md.md)] コンポーネントがアプリに不可欠な部分であるため、バージョン属性を提供する意味がありません。

### <a name="reusable-includewin8appnamelongincludeswin8-appname-long-mdmd-ui-controls"></a>再利用可能な [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] UI コントロール
 関連する UI コントロールのセットを再利用可能な [!INCLUDE[wrt](../../../includes/wrt-md.md)] コンポーネントにパッケージ化できます。 コンポーネントは、単独で商品化することも、作成するアプリの要素として使用することもできます。 このシナリオで理にかなってを使用して、 [!INCLUDE[wrt](../../../includes/wrt-md.md)] <xref:Windows.Foundation.Metadata.VersionAttribute>互換性を改善する属性。

### <a name="reusable-application-logic-from-existing-net-framework-apps"></a>既存の .NET Framework アプリからの再利用可能なアプリケーション ロジック
 既存のデスクトップ アプリからマネージド コードをスタンドアロンの [!INCLUDE[wrt](../../../includes/wrt-md.md)] コンポーネントとしてパッケージ化できます。 これによって、C# または Visual Basic を使用してビルドされる [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] アプリに加えて、C++ または JavaScript を使用してビルドされる [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] アプリでも、コンポーネントを使用できるようになります。 コードに再利用シナリオが複数ある場合、バージョン管理はオプションです。

## <a name="related-topics"></a>関連トピック

|タイトル|説明|
|-----------|-----------------|
|[Windows ストア アプリ用 .NET の概要](https://docs.microsoft.com/previous-versions/windows/apps/br230302(v=vs.140))|
  [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] アプリと [!INCLUDE[wrt](../../../includes/wrt-md.md)] コンポーネントの作成に使用できる .NET Framework の型およびメンバーについて説明します  (Windows デベロッパー センター内)。|
|[C# または Visual Basic を使った Windows ストア アプリのロードマップ](https://docs.microsoft.com/previous-versions/windows/apps/br229583(v=win.10))|C# または Visual Basic を使用して [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] アプリの開発を開始するときに役立つ主要リソース (各種のクイック スタート トピック、ガイドライン、ベスト プラクティスなど) が用意されています  (Windows デベロッパー センター内)。|
|[どのように操作方法 (XAML)](https://docs.microsoft.com/previous-versions/windows/apps/br229566(v=win.10))|C# または Visual Basic を使用して [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] アプリの開発を開始するときに役立つ主要リソース (各種のクイック スタート トピック、ガイドライン、ベスト プラクティスなど) が用意されています  (Windows デベロッパー センター内)。|
|[C# および Visual Basic での Windows ランタイム コンポーネントの作成](/windows/uwp/winrt-components/creating-windows-runtime-components-in-csharp-and-visual-basic)|.NET Framework を使用して [!INCLUDE[wrt](../../../includes/wrt-md.md)] コンポーネントを作成する方法、JavaScript を使用して Windows 用にビルドされた [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] アプリの一部としてそのコンポーネントを使用する方法、Visual Studio との組み合わせをデバッグする方法について説明します  (Windows デベロッパー センター内)。|
|[Windows ランタイム リファレンス](/uwp/api/)|
  [!INCLUDE[wrt](../../../includes/wrt-md.md)]のリファレンス ドキュメント  (Windows デベロッパー センター内)。|
|[Windows ランタイムへの URI の引き渡し](../../../docs/standard/cross-platform/passing-a-uri-to-the-windows-runtime.md)|マネージド コードから [!INCLUDE[wrt](../../../includes/wrt-md.md)]に URI を渡すときに発生する可能性がある問題と、その回避方法について説明します。|
