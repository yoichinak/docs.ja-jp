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
ms.openlocfilehash: c49e9a5c4b8785704f8c4cbd1c9b7af10dc0c689
ms.sourcegitcommit: d6e27023aeaffc4b5a3cb4b88685018d6284ada4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/09/2019
ms.locfileid: "67661781"
---
# <a name="net-framework-support-for-windows-store-apps-and-windows-runtime"></a>Windows ストア アプリおよび Windows ランタイムのための .NET Framework サポート

.NET Framework 4.5 では、さまざまな Windows ランタイムでのソフトウェア開発シナ リオをサポートします。 これらのシナリオは次の 3 つのカテゴリに分類されます。

- 開発[!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)]」の説明に従って、XAML コントロールを使用したアプリ[ロードマップの Windows ストア アプリを c# または Visual Basic を使用して](https://docs.microsoft.com/previous-versions/windows/apps/br229583(v=win.10))、[方法操作方法 (XAML)](https://docs.microsoft.com/previous-versions/windows/apps/br229566(v=win.10))、および[.NET Windows ストア アプリの概要](https://docs.microsoft.com/previous-versions/windows/apps/br230302(v=vs.140)).

- .NET Framework で作成する [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] アプリで使用するクラス ライブラリを開発する。

- パッケージ化、Windows ランタイム コンポーネントを開発します。WinMD ファイルは、Windows ランタイムをサポートする任意のプログラミング言語で使用できます。 たとえばを参照してください[c# および Visual Basic での Windows ランタイム コンポーネントの作成](/windows/uwp/winrt-components/creating-windows-runtime-components-in-csharp-and-visual-basic)です。

このトピックでは、サポート、.NET Framework が 3 つのカテゴリのすべての提供し、Windows ランタイム コンポーネント用シナリオについて説明しますがについて説明します。 最初のセクションでは、.NET Framework と、Windows ランタイム間のリレーションシップに関する基本情報が含まれていて、ヘルプ システムや、IDE で発生する可能性が奇妙な動作を説明します。 [2 番目のセクション](#WindowsRuntimeComponents)Windows ランタイム コンポーネントを開発するためのシナリオについて説明します。

## <a name="the-basics"></a>基本事項

.NET Framework が提供することによって、前述の 3 つの開発シナ リオをサポートしている[!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)]、および Windows ランタイム自体をサポートすることで。

- [.NET framework と Windows ランタイム名前空間](https://docs.microsoft.com/previous-versions/windows/apps/br230302(v=vs.140)#net-framework-and-windows-runtime-namespaces)、.NET Framework クラス ライブラリの簡素化されたビューを示し、型と作成に使用できるメンバーのみを含める[!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)]アプリと Windows ランタイム コンポーネントです。

  - Visual Studio (Visual Studio 2012 またはそれ以降) を使用して開発するときに、[!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)]参照アセンブリのセットにより、関連する型とメンバーのみが表示されるアプリまたは Windows ランタイム コンポーネントでします。

  - この合理化された API セットを簡単にさらに、.NET Framework 内で重複した、または Windows ランタイムを重複した機能の削除によって機能します。 たとえば、コレクションの型のジェネリック バージョンのみが含まれているし、XML ドキュメント オブジェクト モデルは、Windows ランタイムの XML API を優先して除去を設定します。

  - Windows ランタイムがマネージ コードから呼び出す簡単なため、単にオペレーティング システムの API をラップする機能は削除も。

  詳細について、[!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)]を参照してください、 [.NET Windows ストア アプリの概要](https://docs.microsoft.com/previous-versions/windows/apps/br230302(v=vs.140))します。 API 選択プロセスについては、次を参照してください。、 [Metro スタイル アプリ用 .NET](https://devblogs.microsoft.com/dotnet/net-for-metro-style-apps/) .NET ブログのエントリ。

- [Windows ランタイム](/uwp/api/)構築するためのユーザー インターフェイス要素を提供します[!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)]アプリ、およびオペレーティング システムの機能へのアクセスを提供します。 Windows ランタイムが可能なメタデータを .NET Framework のように、C#および Windows ランタイム、.NET Framework の使用方法を使用する Visual Basic コンパイラはクラス ライブラリ。 .NET Framework では、いくつかの違いを非表示にして、Windows ランタイムを使用してやすくなります。

  - .NET Framework と、パターンの追加や削除、イベント ハンドラーなど、Windows ランタイム間のプログラミング パターンでは、いくつか違いが非表示になります。 ユーザーは .NET Framework のパターンを使用するとよいだけです。

  - よく使用される型 (たとえばプリミティブ型やコレクション) の違いの一部が非表示になります。 説明したように単純に .NET Framework 型を使用する[の相違点で表示される IDE](#DifferencesVisibleInIDE)、この記事で後述します。

ほとんどの場合、Windows ランタイム用 .NET Framework のサポートは透過的です。 次のセクションでは、マネージ コードと Windows ランタイム間の明確な違いについて説明します。

<a name="AboutReferenceDocumentation"></a>

### <a name="the-net-framework-and-the-windows-runtime-reference-documentation"></a>.NET Framework と Windows ランタイム リファレンス ドキュメント

Windows ランタイムと .NET Framework ドキュメント セットは、分離です。 型またはメンバーに関するヘルプを表示するために F1 キーを押すと、該当するセットのリファレンス ドキュメントが表示されます。 ただしを参照する場合、 [Windows ランタイム リファレンス](/uwp/api/)不可解と思われる例が発生する可能性があります。

- などのトピック、<xref:Windows.Foundation.Collections.IIterable%601>インターフェイスでは、Visual Basic または c# の宣言の構文がありません。 代わりに、メモをセクションの構文上が表示されます (この場合は、".NET:このインターフェイスは System.Collections.Generic.IEnumerable として表示されます\<T >")。 .NET Framework と Windows ランタイムは、さまざまなインターフェイスと同様の機能を提供するためです。 さらに、`IIterable` では列挙子を返すのに `First` メソッドではなく <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> メソッドを使用するという、動作の違いもあります。 一般的なタスクを実行する別の方法を学習することを求める代わりには、.NET Framework は、マネージ コードを熟知している型を使用するようにして、Windows ランタイムをサポートします。 表示されなくなります、 `IIterable` IDE では、インターフェイスであるため、Windows ランタイム リファレンス ドキュメントで直面する唯一の方法が直接そのドキュメントを参照して、します。

- <xref:Windows.Web.Syndication.SyndicationFeed.%23ctor(System.String,System.String,Windows.Foundation.Uri)>ドキュメントは、密接に関連する問題を示しています。さまざまな言語別に、パラメーターの型が表示されます。 C# と Visual Basic の場合、パラメーターの型は <xref:System.String?displayProperty=nameWithType> と <xref:System.Uri?displayProperty=nameWithType> です。 これもやはり、.NET Framework で独自の `String` 型と `Uri` 型が使われるためであり、このようなよく使用される型について、.NET Framework ユーザーが処理を実行する別の方法を学習しても意味はありません。 IDE では、.NET Framework には、対応する Windows ランタイム型が非表示にします。

- いくつかの場合など、<xref:Windows.UI.Xaml.GridLength>構造体には、.NET Framework には、同じ名前が、多くの機能を持つ型。 たとえば、一連のコンストラクターとプロパティのトピックは `GridLength` に関連付けられますが、メンバーがマネージド コードでのみ使用可能であるために、Visual Basic と C# に関してのみ構文ブロックの機能を備えています。 Windows ランタイムでは、構造体はフィールドしかありません。 Windows ランタイムの構造体には、ヘルパー クラスが必要です。 <xref:Windows.UI.Xaml.GridLengthHelper>、同等の機能を提供します。 このヘルパー クラスは、マネージド コードを記述している間は IDE に表示されません。

- IDE では、Windows ランタイム型の表示から派生する<xref:System.Object?displayProperty=nameWithType>します。 この型のメンバーは、<xref:System.Object> などの <xref:System.Object.ToString%2A?displayProperty=nameWithType> から継承されるように表示されます。 これらのメンバーから実際には、型が継承する場合のように動作<xref:System.Object>、Windows ランタイム型にキャストできると<xref:System.Object>します。 この機能は、.NET Framework は、Windows ランタイムのサポートの一部です。 ただし、Windows ランタイム リファレンス ドキュメントの種類を表示する場合は、このようなメンバーは表示されません。 これらの見かけ上の継承されたメンバーに関するドキュメントは、<xref:System.Object?displayProperty=nameWithType> のリファレンス ドキュメントに含まれています。

<a name="DifferencesVisibleInIDE"></a>

### <a name="differences-that-are-visible-in-the-ide"></a>IDE で表示される相違点

高度なプログラミング シナリオなどで記述された Windows ランタイム コンポーネントを使用してC#のアプリケーション ロジックを提供する、 [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] JavaScript を使用して Windows 用にビルドされたアプリでは、このような違いはでも、IDE で明らかな、ドキュメントです。 コンポーネントが返されるときに、 `IDictionary<int, string>` 、JavaScript と JavaScript デバッガーで見てのメソッドが表示されます`IMap<int, string>`JavaScript は、Windows ランタイム型を使用するためです。 よく使用されるコレクション型のうち、この 2 言語で表示が異なる型の一部を次の表に示します。

|Windows ランタイム型|対応する .NET Framework の型|
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

Windows ランタイムで`IMap<K, V>`と`IMapView<K, V>`を使用して反復されます`IKeyValuePair`します。 これらをマネージド コードに渡すと、`IDictionary<TKey, TValue>` および `IReadOnlyDictionary<TKey, TValue>` として表示されるため、これを列挙するには必然的に `System.Collections.Generic.KeyValuePair<TKey, TValue>` を使用します。

インターフェイスがマネージド コード内に表示される方法によって、これらのインターフェイスを実装する型の表示方法が決まります。 たとえば、`PropertySet` クラスは `IMap<K, V>` を実装しますが、これはマネージド コードでは `IDictionary<TKey, TValue>` として表示されます。 `PropertySet` は、`IDictionary<TKey, TValue>` ではなく `IMap<K, V>` を実装したかのように表示されます。したがってマネージ コードでは、`Add` メソッド (その動作は .NET Framework ディクショナリの `Add` メソッドと同様) が含まれているように表示されます。 `Insert` メソッドがないように見えます。

.NET Framework を使用して、Windows ランタイム コンポーネントと JavaScript で、このようなコンポーネントを使用する方法を示すチュートリアルを作成する方法の詳細については、次を参照してください[で Windows ランタイム コンポーネントの作成C#および Visual Basic](/windows/uwp/winrt-components/creating-windows-runtime-components-in-csharp-and-visual-basic).

### <a name="primitive-types"></a>プリミティブ型

マネージ コードで、Windows ランタイムの自然な使用を有効にするのには、コード内の Windows ランタイムのプリミティブ型ではなく .NET Framework のプリミティブ型が表示されます。 .NET Framework では、`Int32` 構造体などのプリミティブ型には、`Int32.TryParse` メソッドなどの便利なプロパティとメソッドが多くあります。 これに対し、プリミティブ型と Windows ランタイムの構造体は、フィールドしかありません。 マネージド コードでプリミティブを使用すると、.NET Framework の型のように表示され、通常どおりに .NET Framework 型のプロパティとメソッドを使用できます。 要約すると、次のようになります。

- Windows ランタイムのプリミティブの`Int32`、 `Int64`、 `Single`、 `Double`、 `Boolean`、 `String` (変更できないコレクションの Unicode 文字)、 `Enum`、 `UInt32`、`UInt64`と`Guid`、同じ名前の型を使用して、`System`名前空間。

- `UInt8` では、`System.Byte` を使用します。

- `Char16` では、`System.Char` を使用します。

- `IInspectable` インターフェイスでは、`System.Object` を使用します。

- `HRESULT` では、`System.Int32` のメンバーを 1 つ含む構造体を使用します。

同様、インターフェイス型では、ときにこの表示の証拠ですが表示されるときだけ、.NET Framework プロジェクトによって使用される Windows ランタイム コンポーネントを[!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)]JavaScript を使用してビルドされたアプリ。

表示される他の基本的な一般的に使用される Windows ランタイム型が含まれています、.NET Framework の同等にはマネージ コード、`Windows.Foundation.DateTime`としてマネージ コードに表示される構造体、<xref:System.DateTimeOffset?displayProperty=nameWithType>構造体、および`Windows.Foundation.TimeSpan`を構造として表示されます、<xref:System.TimeSpan?displayProperty=nameWithType>構造体。

### <a name="other-differences"></a>その他の相違点

いくつかの場合、.NET Framework の型は、Windows ランタイム型ではなく、コードに表示されるという事実には、ユーザーによる操作が必要です。 たとえば、<xref:Windows.Foundation.Uri?displayProperty=nameWithType>クラスとして表示されます<xref:System.Uri?displayProperty=nameWithType>.NET Framework コードでします。 <xref:System.Uri?displayProperty=nameWithType> により、相対 URI ですが<xref:Windows.Foundation.Uri?displayProperty=nameWithType>絶対 URI が必要です。 したがって、Windows ランタイム メソッドに URI を渡すと、ときに、絶対であるようにする必要があります。 (を参照してください[Windows ランタイムへの URI の引き渡し](../../../docs/standard/cross-platform/passing-a-uri-to-the-windows-runtime.md))。

<a name="WindowsRuntimeComponents"></a>

## <a name="scenarios-for-developing-windows-runtime-components"></a>Windows ランタイム コンポーネントの開発シナリオ

マネージ Windows ランタイム コンポーネントのサポートされるシナリオは、次の原則に依存します。

- .NET Framework を使用してビルドされる Windows ランタイム コンポーネントがあるその他の Windows Runtimelibraries から明確な違いありません。 たとえば、マネージ コードを使用して、ネイティブの Windows ランタイム コンポーネントを再実装する場合は、2 つのコンポーネントは表面上と区別することできません。 コンポーネントがマネージド コードで記述されているという事実は、そのコード自体がマネージド コードであったとしても、そのコンポーネントを使用するコードには表示されません。 ただし内部的には、そのコンポーネントは真のマネージド コードであり、共通言語ランタイム (CLR) 上で実行されます。

- コンポーネントには、アプリケーション ロジック、[!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] UI コントロール、またはその両方を実装する型を含めることができます。

  > [!NOTE]
  > アプリケーション ロジックから UI 要素を分離することをお勧めします。 また、JavaScript や HTML を使用して Windows 用にビルドされた [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] アプリでは、[!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] UI コントロールを使用できません。

- コンポーネントは、[!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] アプリ用 Visual Studio ソリューション内のプロジェクトの場合もあれば、複数のソリューションに追加できる再利用可能なコンポーネントの場合もあります。

  > [!NOTE]
  > コンポーネントはでのみ使用される場合C#または Visual Basic、Windows ランタイム コンポーネントに理由がないです。 行った場合、通常 .NET Framework クラス ライブラリを代わりに、そのパブリック API サーフェイスを Windows ランタイム型に制限する必要はありません。

- Windows ランタイムを使用して再利用可能なコンポーネントのバージョンをリリースする<xref:Windows.Foundation.Metadata.VersionAttribute>さまざまなバージョンでどの型 (および型のメンバー) を識別するために属性が追加されました。

- コンポーネントの型は、Windows ランタイム型から派生できます。 コントロールが内のプリミティブ コントロール型から派生できます、<xref:Windows.UI.Xaml.Controls.Primitives>名前空間または終了コントロールなどの詳細はから<xref:Windows.UI.Xaml.Controls.Button>します。

  > [!IMPORTANT]
  > 以降で[!INCLUDE[win8](../../../includes/win8-md.md)]され、.NET Framework 4.5 とマネージ Windows ランタイム コンポーネントのすべてのパブリック型をシールする必要があります。 別の Windows ランタイム コンポーネントの型は、そこから派生できません。 コンポーネントでポリモーフィックな動作を提供するには、インターフェイスを作成し、そのインターフェイスをポリモーフィックな型に実装します。

- コンポーネントのパブリック型で、すべてのパラメーターと戻り値の種類は、Windows ランタイムの型 (コンポーネントを定義する Windows ランタイム型を含む) である必要があります。

次のセクションでは、一般的なシナリオの例を示します。

### <a name="application-logic-for-a-includewin8appnamelongincludeswin8-appname-long-mdmd-app-with-javascript"></a>JavaScript による [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] アプリ用アプリケーション ロジック

JavaScript を使用して Windows の [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] アプリを開発する場合、アプリケーション ロジックの一部が、他の部分に比べてマネージド コードでより適切に機能したり、開発が容易であったりすることがあります。 JavaScript では .NET Framework クラス ライブラリを直接使用できませんが、クラス ライブラリを .WinMD ファイルにすることができます。 このシナリオでは、Windows ランタイム コンポーネントは、バージョン属性を提供する意味をなさないために、アプリの不可欠な部分が。

### <a name="reusable-includewin8appnamelongincludeswin8-appname-long-mdmd-ui-controls"></a>再利用可能な [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] UI コントロール

再利用可能な Windows ランタイム コンポーネントに関連する UI コントロールのセットをパッケージ化することができます。 コンポーネントは、単独で商品化することも、作成するアプリの要素として使用することもできます。 このシナリオで理にかなって Windows ランタイムを使用して、<xref:Windows.Foundation.Metadata.VersionAttribute>互換性を改善する属性。

### <a name="reusable-application-logic-from-existing-net-framework-apps"></a>既存の .NET Framework アプリからの再利用可能なアプリケーション ロジック

スタンドアロンの Windows ランタイム コンポーネントとして、既存のデスクトップ アプリからマネージ コードをパッケージ化できます。 これによって、C# または Visual Basic を使用してビルドされる [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] アプリに加えて、C++ または JavaScript を使用してビルドされる [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] アプリでも、コンポーネントを使用できるようになります。 コードに再利用シナリオが複数ある場合、バージョン管理はオプションです。

## <a name="related-topics"></a>関連トピック

|タイトル|説明|
|-----------|-----------------|
|[Windows ストア アプリ用 .NET の概要](https://docs.microsoft.com/previous-versions/windows/apps/br230302(v=vs.140))|.NET Framework 型と作成に使用できるメンバーについて説明します[!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)]アプリと Windows RuntimeComponents します。 (Windows デベロッパー センター内)。|
|[C# または Visual Basic を使った Windows ストア アプリのロードマップ](https://docs.microsoft.com/previous-versions/windows/apps/br229583(v=win.10))|C# または Visual Basic を使用して [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] アプリの開発を開始するときに役立つ主要リソース (各種のクイック スタート トピック、ガイドライン、ベスト プラクティスなど) が用意されています (Windows デベロッパー センター内)。|
|[どのように操作方法 (XAML)](https://docs.microsoft.com/previous-versions/windows/apps/br229566(v=win.10))|C# または Visual Basic を使用して [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] アプリの開発を開始するときに役立つ主要リソース (各種のクイック スタート トピック、ガイドライン、ベスト プラクティスなど) が用意されています (Windows デベロッパー センター内)。|
|[C# および Visual Basic での Windows ランタイム コンポーネントの作成](/windows/uwp/winrt-components/creating-windows-runtime-components-in-csharp-and-visual-basic)|.NET Framework を使用して、Windows ランタイム コンポーネントを作成する方法について説明しますの一部として使用する方法について説明します、[!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)]アプリの JavaScript を使用して Windows 用にビルドされ、Visual Studio の組み合わせをデバッグする方法について説明します。 (Windows デベロッパー センター内)。|
|[Windows ランタイム リファレンス](/uwp/api/)|Windows ランタイムのリファレンス ドキュメント。 (Windows デベロッパー センター内)。|
|[Windows ランタイムへの URI の引き渡し](../../../docs/standard/cross-platform/passing-a-uri-to-the-windows-runtime.md)|これを回避する方法と、Windows ランタイムにマネージ コードから URI を渡す場合に生じる可能性のある問題について説明します。|
