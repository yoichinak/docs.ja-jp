---
title: WPF アドインの概要
ms.date: 03/30/2017
helpviewer_keywords:
- add-ins and XAML browser applications [WPF]
- add-ins overview [WPF]
- add-ins [WPF], performance
- add-ins [WPF], benefits
- .NET Framework add-in model [WPF]
- add-ins [WPF], user interface
- add-ins and the user interface [WPF]
- add-ins [WPF], architecture
- add-ins [WPF], limitations
ms.assetid: 00b4c776-29a8-4dba-b603-280a0cdc2ade
ms.openlocfilehash: a146f15a1c2755f254e198d471a42ca9ec29b072
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/23/2019
ms.locfileid: "71182533"
---
# <a name="wpf-add-ins-overview"></a>WPF アドインの概要

<a name="Introduction"></a>.NET Framework には、アドインの機能拡張をサポートするアプリケーションを作成するために開発者が使用できるアドインモデルが含まれています。 このアドイン モデルを使用することで、アプリケーション機能に統合され、アプリケーション機能を拡張するアドインを作成できます。 場合によっては、アプリケーションがアドインによって提供されるユーザーインターフェイスを表示する必要もあります。このトピックでは、WPF が .NET Framework アドインモデルを補強して、これらのシナリオ、背後にあるアーキテクチャ、利点、および制限事項を有効にする方法について説明します。

<a name="Requirements"></a>

## <a name="prerequisites"></a>必須コンポーネント

.NET Framework アドインモデルに関する知識が必要です。 詳細については、「[アドインおよび拡張機能](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb384200(v%3dvs.100))」を参照してください。

<a name="AddInsOverview"></a>

## <a name="add-ins-overview"></a>アドインの概要

新しい機能を追加するためにアプリケーションを再コンパイルして再配置する手間を省くことを目的として、アプリケーションは機能拡張メカニズムを実装し、開発者 (ファーストパーティ、サードパーティのいずれも) が元のアプリケーションに統合される別のアプリケーションを作成できるようにしています。 こうした拡張機能をサポートする方法としては、アドイン ("アドオン"、"プラグイン" などとも呼ばれる) の使用が最も一般的です。 アドインによる機能拡張を公開する実際のアプリケーションとして、次のようなものが挙げられます。

- Internet Explorer のアドオン。

- Windows Media Player のプラグイン。

- Visual Studio のアドイン。

たとえば、Windows Media Player のアドイン モデルにおいて、サードパーティの開発者は、Windows Media Player の機能をさまざまな形で拡張する "プラグイン" を実装できます。たとえば、Windows Media Player でネイティブにサポートされていないメディア形式 (DVD、MP3 など) のデコーダーおよびエンコーダー、オーディオ効果、スキンなどを作成できます。 各アドイン モデルは、アプリケーション固有の機能を公開するためにビルドされますが、どのアドイン モデルにも共通するエンティティや動作がいくつかあります。

典型的な機能拡張ソリューションの主な 3 つのエンティティは、*コントラクト*、*アドイン*、および*ホスト アプリケーション*です。 コントラクトは、次の 2 つの方法で、アドインとホスト アプリケーションとの統合方法を定義します。

- アドインは、ホスト アプリケーションによって実装される機能と統合されます。

- ホスト アプリケーションで、アドインを統合するための機能を公開します。

アドインを使用するには、ホスト アプリケーションが実行時にアドインを検索して読み込む必要があります。 したがって、アドインをサポートするアプリケーションには次の機能が必要です。

- **検出**:ホストアプリケーションでサポートされているコントラクトに準拠するアドインを検索します。

- **アクティブ化**:アドインとの通信を読み込んで実行し、確立する。

- **分離**:アプリケーションドメインまたはプロセスを使用して、アプリケーションをセキュリティで保護するための分離境界を確立し、アドインでの実行に関する問題を回避します。

- **通信**:メソッドを呼び出してデータを渡すことによって、アドインとホストアプリケーションが分離境界を越えて相互に通信できるようにします。

- **有効期間の管理**:クリーンで予測可能な方法でアプリケーションドメインとプロセスを読み込んでアンロードする (「[アプリケーションドメイン](../../app-domains/application-domains.md)」を参照)。

- **バージョン管理**:新しいバージョンのいずれかが作成された場合でも、ホストアプリケーションとアドインが引き続き通信できることを確認します。

このことからわかるように、堅牢なアドイン モデルの開発は簡単なことではありません。 このため、.NET Framework は、アドインモデルを構築するためのインフラストラクチャを提供します。

> [!NOTE]
> アドインの詳細については、「[アドインおよび拡張機能](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb384200(v%3dvs.100))」を参照してください。

<a name="NETFrameworkAddInModelOverview"></a>

## <a name="net-framework-add-in-model-overview"></a>.NET Framework アドイン モデルの概要

<xref:System.AddIn>名前空間にある .NET Framework アドインモデルには、アドインの拡張機能の開発を簡略化するように設計された型のセットが含まれています。 .NET Framework アドインモデルの基本単位は*コントラクト*です。これは、ホストアプリケーションとアドインが相互に通信する方法を定義します。 コントラクトのホスト アプリケーション固有の*ビュー*を使用して、コントラクトはホスト アプリケーションに公開されます。 同様に、コントラクトのアドイン固有の*ビュー*がアドインに公開されます。 *アダプター*は、ホスト アプリケーションとアドインが、コントラクトの対応するビュー間で通信するために使用されます。 コントラクト、ビュー、およびアダプターはセグメントと見なされ、関連セグメントのセットが*パイプライン*を構成します。 パイプラインは、.NET Framework のアドインモデルが、検出、アクティベーション、セキュリティの分離、実行の分離 (アプリケーションドメインとプロセスの両方を使用)、通信、有効期間管理、バージョン管理をサポートする基盤です。

このサポート全体を使用して、開発者はホスト アプリケーションの機能を統合するアドインをビルドできます。 ただし、一部のシナリオでは、アドインによって提供されるユーザーインターフェイスをホストアプリケーションで表示する必要があります.NET Framework の各プレゼンテーションテクノロジにはユーザーインターフェイスを実装するための独自のモデルがあるため、.NET Framework アドインモデルは特定のプレゼンテーションテクノロジをサポートしていません。 代わりに、WPF は、アドインの UI サポートを使用して .NET Framework アドインモデルを拡張します。

<a name="WPFAddInModel"></a>

## <a name="wpf-add-ins"></a>WPF アドイン

WPF を .NET Framework アドインモデルと組み合わせて使用すると、ホストアプリケーションがアドインからユーザーインターフェイスを表示する必要があるさまざまなシナリオに対処できます。特に、これらのシナリオは、次の2つのプログラミングモデルを使用して WPF によって解決されます。

1. **アドインが UI を返す**。 アドインは、コントラクトで定義されているように、メソッド呼び出しを使用してホストアプリケーションに UI を返します。 このシナリオは、次の場合に使用されます。

    - アドインによって返される UI の外観は、動的に生成されたレポートなど、実行時にのみ存在するデータまたは条件に依存します。

    - アドインによって提供されるサービスの UI は、アドインを使用できるホストアプリケーションの UI とは異なります。

    - このアドインは、主にホストアプリケーションのサービスを実行し、UI を使用してホストアプリケーションにステータスを報告します。

2. **アドインが UI である**。 アドインは、コントラクトによって定義される UI です。 このシナリオは、次の場合に使用されます。

    - アドインは表示以外のサービス (広告など) を提供しない。

    - アドインによって提供されるサービスの UI は、そのアドインを使用できるすべてのホストアプリケーション (電卓やカラーピッカーなど) に共通です。

これらのシナリオでは、ホストアプリケーションドメインとアドインアプリケーションドメイン間で UI オブジェクトを渡すことができます。 .NET Framework アドインモデルは、アプリケーションドメイン間の通信にリモート処理を使用するため、これらの間で渡されるオブジェクトはリモート処理可能である必要があります。

リモート処理可能なオブジェクトとは、次の 1 つ以上に該当するクラスのインスタンスです。

- <xref:System.MarshalByRefObject>クラスから派生します。

- <xref:System.Runtime.Serialization.ISerializable> インターフェイスを実装します。

- 属性が<xref:System.SerializableAttribute>適用されています。

> [!NOTE]
> リモート処理可能な .NET Framework オブジェクトの作成の詳細については、「[オブジェクトのリモート](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/wcf3swha(v=vs.100))処理」を参照してください。

WPF の UI 型はリモート処理できません。 この問題を解決するために、WPF は .NET Framework アドインモデルを拡張して、アドインによって作成された WPF UI をホストアプリケーションから表示できるようにします。 このサポートは、WPF によって、インターフェイスと<xref:System.AddIn.Contract.INativeHandleContract> <xref:System.AddIn.Pipeline.FrameworkElementAdapters>クラス<xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A>によって実装される2つの静的<xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>メソッド (と) の2つの型によって提供されます。 大まかに、これらの型とメソッドは次のように使用されます。

1. WPF では、アドインによって提供されるユーザーインターフェイスが、図形、コントロール<xref:System.Windows.FrameworkElement>、ユーザーコントロール、レイアウトパネル、ページなど、から直接または間接的に派生するクラスである必要があります。

2. アドインとホストアプリケーションの間で UI が渡されることをコントラクトが宣言する場合は、 <xref:System.AddIn.Contract.INativeHandleContract> (では<xref:System.Windows.FrameworkElement>なく) として宣言する必要があります。<xref:System.AddIn.Contract.INativeHandleContract>は、分離境界を越えて渡すことができるアドイン UI のリモート処理可能な表現です。

3. アドインのアプリケーションドメインから渡される前に、を<xref:System.Windows.FrameworkElement>呼び出す<xref:System.AddIn.Contract.INativeHandleContract> <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>ことによって、がとしてパッケージ化されます。

4. ホストアプリケーションのアプリケーションドメイン<xref:System.AddIn.Contract.INativeHandleContract>に渡された後、を呼び出し<xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A>て、を<xref:System.Windows.FrameworkElement>として再パッケージ化する必要があります。

、 <xref:System.AddIn.Contract.INativeHandleContract> 、<xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A>および<xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>がどのように使用されるかは、特定のシナリオによって異なります。 以降のセクションでは、各プログラミング モデルについて詳しく説明していきます。

<a name="ReturnUIFromAddInContract"></a>

## <a name="add-in-returns-a-user-interface"></a>ユーザー インターフェイスを返すアドイン

アドインがホストアプリケーションに UI を返すには、次のものが必要です。

1. .NET Framework[アドインおよび拡張機能](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb384200(v%3dvs.100))のドキュメントで説明されているように、ホストアプリケーション、アドイン、およびパイプラインを作成する必要があります。

2. コントラクトはを実装<xref:System.AddIn.Contract.IContract>し、UI を返すようにする必要があります。コントラクトは、型<xref:System.AddIn.Contract.INativeHandleContract>の戻り値を持つメソッドを宣言する必要があります。

3. アドインとホストアプリケーションの間で渡される UI は、から<xref:System.Windows.FrameworkElement>直接または間接的に派生している必要があります。

4. アドインによって返される UI は、分離境界を越える<xref:System.Windows.FrameworkElement> <xref:System.AddIn.Contract.INativeHandleContract>前に、からに変換する必要があります。

5. 返される UI は、分離境界を越えると<xref:System.AddIn.Contract.INativeHandleContract> 、から<xref:System.Windows.FrameworkElement>に変換される必要があります。

6. ホストアプリケーションは、返さ<xref:System.Windows.FrameworkElement>れたを表示します。

UI を返すアドインの実装方法を示す例については、「UI を[返すアドインを作成](how-to-create-an-add-in-that-returns-a-ui.md)する」を参照してください。

<a name="AddInIsAUI"></a>

## <a name="add-in-is-a-user-interface"></a>ユーザー インターフェイスであるアドイン

アドインが UI の場合は、次のものが必要です。

1. .NET Framework[アドインおよび拡張機能](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb384200(v%3dvs.100))のドキュメントで説明されているように、ホストアプリケーション、アドイン、およびパイプラインを作成する必要があります。

2. アドインのコントラクトインターフェイスはを実装<xref:System.AddIn.Contract.INativeHandleContract>する必要があります。

3. ホストアプリケーションに渡されるアドインは、から<xref:System.Windows.FrameworkElement>直接または間接的に派生する必要があります。

4. 分離境界を越える<xref:System.Windows.FrameworkElement> <xref:System.AddIn.Contract.INativeHandleContract>前に、アドインをからに変換する必要があります。

5. 分離境界を越えると、アドインはから<xref:System.AddIn.Contract.INativeHandleContract> <xref:System.Windows.FrameworkElement>に変換される必要があります。

6. ホストアプリケーションは、返さ<xref:System.Windows.FrameworkElement>れたを表示します。

UI であるアドインの実装方法を示す例については、「UI である[アドインを作成](how-to-create-an-add-in-that-is-a-ui.md)する」を参照してください。

<a name="ReturningMultipleUIsFromAnAddIn"></a>

## <a name="returning-multiple-uis-from-an-add-in"></a>複数の UI を返すアドイン

多くの場合、アドインには、ホストアプリケーションが表示する複数のユーザーインターフェイスが用意されています。 たとえば、ui としてもホストアプリケーションに状態情報を提供する UI であるアドインを考えてみます。 このようなアドインは、[ユーザー インターフェイスを返すアドイン](#ReturnUIFromAddInContract)のモデルと[ユーザー インターフェイスであるアドイン](#AddInIsAUI)のモデルの両方の手法を組み合わせることで実装できます。

<a name="AddInsAndXBAPs"></a>

## <a name="add-ins-and-xaml-browser-applications"></a>アドインと XAML ブラウザー アプリケーション

ここまでの例では、ホスト アプリケーションはスタンドアロン アプリケーションとしてインストールされています。 [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)] はアドインをホストすることもできますが、そのためには次に示すビルドと実装の要件を満たす必要があります。

- アプリケーションマニフェストは、パイプライン (フォルダーとアセンブリ) とアドインアセンブリを、 [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)]と同じフォルダーにあるクライアントコンピューターの ClickOnce アプリケーションキャッシュにダウンロードするように特別に構成する必要があります。 [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)]

- アドイン[!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)]を検出して読み込むコードでは、 [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)]の ClickOnce アプリケーションキャッシュをパイプラインとアドインの場所として使用する必要があります。

- [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] は、アドインが起点サイトにある圧縮しないファイルを参照する場合、アドインを特別なセキュリティ コンテキストの下で読み込む必要があります。[!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] によってホストされる場合、アドインが参照できるのは、ホスト アプリケーションの起点サイトにある圧縮しないファイルのみです。

これらのタスクについて、次のサブセクションで詳しく説明します。

### <a name="configuring-the-pipeline-and-add-in-for-clickonce-deployment"></a>ClickOnce 配置のためのパイプラインとアドインの構成

[!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)]は、ClickOnce 配置キャッシュ内の安全なフォルダーにダウンロードして実行します。 [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] でアドインをホストするには、パイプラインとアドインのアセンブリも同じ安全なフォルダーにダウンロードする必要があります。 このためには、パイプラインとアドインのどちらのアセンブリもダウンロード対象に含まれるよう、アプリケーション マニフェストを構成する必要があります。 これは、[!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)] で実行することが最も簡単ですが、[!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)] でパイプラインをアセンブリとして検出するには、パイプラインとアドインのアセンブリが、ホスト [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] プロジェクトのルート フォルダーに存在する必要があります。

したがって、まず、パイプライン アセンブリとアドイン アセンブリの各プロジェクトのビルド出力を設定し、パイプラインとアドインのアセンブリを [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] プロジェクトのルートにビルドします。 次の表は、ホストの [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] プロジェクトと同じソリューションとルートのフォルダーに格納される、パイプライン アセンブリ プロジェクトとアドイン アセンブリ プロジェクトのビルド出力パスを示します。

表 1:XBAP によってホストされるパイプラインアセンブリの出力パスをビルドします。

|パイプライン アセンブリ プロジェクト|ビルド出力パス|
|-------------------------------|-----------------------|
|コントラクト|`..\HostXBAP\Contracts\`|
|アドイン ビュー|`..\HostXBAP\AddInViews\`|
|アドイン側のアダプター|`..\HostXBAP\AddInSideAdapters\`|
|ホスト側のアダプター|`..\HostXBAP\HostSideAdapters\`|
|アドイン|`..\HostXBAP\AddIns\WPFAddIn1`|

次に、パイプライン アセンブリとアドイン アセンブリを [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] コンテンツ ファイルとして [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)] に指定します。手順は次のとおりです。

1. ソリューション エクスプローラーで各パイプライン フォルダーを右クリックし、 **[プロジェクトに含める]** を選択して、パイプラインとアドインのアセンブリをプロジェクトに含めます。

2. **[プロパティ]** ウィンドウで、パイプライン アセンブリとアドイン アセンブリそれぞれについて、 **[ビルド アクション]** を **[コンテンツ]** に設定します。

最後に、パイプラインとアドインのどちらのアセンブリ ファイルもダウンロード対象に含まれるよう、アプリケーション マニフェストを構成します。 ファイルは、アプリケーションが[!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)]占有する ClickOnce キャッシュ内のフォルダーのルートにあるフォルダーに配置する必要があります。 この構成は、次の手順に従って、[!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)] で行うことができます。

1. [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] プロジェクトを右クリックして、 **[プロパティ]** 、 **[発行]** の順にクリックし、 **[アプリケーション ファイル]** をクリックします。

2. **[アプリケーション ファイル]** ダイアログ ボックスで、各パイプラインとアドインの DLL の **[発行の状況]** を **[含める (自動)]** に設定し、各パイプラインとアドインの DLL の **[ダウンロード グループ]** を **[(必須)]** に設定します。

### <a name="using-the-pipeline-and-add-in-from-the-application-base"></a>アプリケーション ベースからのパイプラインとアドインの使用

パイプラインとアドインが ClickOnce 配置用に構成されている場合は、 [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)]と同じ clickonce キャッシュフォルダーにダウンロードされます。 このパイプラインとアドインを [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] から使用するには、[!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] コードがそれらをアプリケーション ベースから取得する必要があります。 パイプラインとアドインを使用するための .NET Framework アドインモデルのさまざまな型およびメンバーは、このシナリオに対して特別なサポートを提供します。 最初に、 <xref:System.AddIn.Hosting.PipelineStoreLocation.ApplicationBase>列挙値によってパスが識別されます。 この値を適切なアドイン メンバーのオーバーロードと併用することで、次のようなパイプラインを使用できます。

- <xref:System.AddIn.Hosting.AddInStore.FindAddIns%28System.Type%2CSystem.AddIn.Hosting.PipelineStoreLocation%29?displayProperty=nameWithType>

- <xref:System.AddIn.Hosting.AddInStore.FindAddIns%28System.Type%2CSystem.AddIn.Hosting.PipelineStoreLocation%2CSystem.String%5B%5D%29?displayProperty=nameWithType>

- <xref:System.AddIn.Hosting.AddInStore.Rebuild%28System.AddIn.Hosting.PipelineStoreLocation%29?displayProperty=nameWithType>

- <xref:System.AddIn.Hosting.AddInStore.Update%28System.AddIn.Hosting.PipelineStoreLocation%29?displayProperty=nameWithType>

### <a name="accessing-the-hosts-site-of-origin"></a>ホストの起点サイトへのアクセス

アドインが起点サイトのファイルを参照できるように、アドインはホスト アプリケーションと等価なセキュリティ分離を使用して読み込む必要があります。 このセキュリティレベルは<xref:System.AddIn.Hosting.AddInSecurityLevel.Host?displayProperty=nameWithType>列挙値によって識別され、アドインがアクティブ化されるときに<xref:System.AddIn.Hosting.AddInToken.Activate%2A>メソッドに渡されます。

<a name="WPFAddInModelArchitecture"></a>

## <a name="wpf-add-in-architecture"></a>WPF アドイン アーキテクチャ

これまでに説明したように、WPF では、、 <xref:System.Windows.FrameworkElement>、および<xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A>を使用して<xref:System.AddIn.Contract.INativeHandleContract>、 <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A> .NET Framework のアドインで (から直接または間接的に派生する) ユーザーインターフェイスを実装できます。 結果として、ホストアプリケーションには、 <xref:System.Windows.FrameworkElement>ホストアプリケーションの UI から表示されるが返されます。

単純な UI アドインシナリオでは、これは開発者が必要とするほど詳細です。 より複雑なシナリオ、特に、レイアウト、リソース、データバインディングなどの追加の WPF サービスを使用しようとするシナリオでは、その利点を理解するために、WPF が UI サポートを使用して .NET Framework アドインモデルを拡張する方法についての詳細な知識が必要です。および制限事項があります。

基本的に、WPF は、アドインからホストアプリケーションに UI を渡しません。wpf は、WPF の相互運用性を使用して、UI の Win32 ウィンドウハンドルを渡します。 そのため、アドインからの UI がホストアプリケーションに渡されると、次のようになります。

- アドイン側では、WPF は、ホストアプリケーションによって表示される UI のウィンドウハンドルを取得します。 ウィンドウハンドルは、から<xref:System.Windows.Interop.HwndSource>派生してを実装<xref:System.AddIn.Contract.INativeHandleContract>する内部 WPF クラスによってカプセル化されます。 このクラスのインスタンスはによって<xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>返され、アドインのアプリケーションドメインからホストアプリケーションのアプリケーションドメインにマーシャリングされます。

- ホストアプリケーション側では、wpf は、 <xref:System.Windows.Interop.HwndSource>から<xref:System.Windows.Interop.HwndHost>派生し<xref:System.AddIn.Contract.INativeHandleContract>てを使用する内部 WPF クラスとしてを再パッケージ化します。 このクラスのインスタンスは、によっ<xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A>てホストアプリケーションに返されます。

<xref:System.Windows.Interop.HwndHost>ウィンドウハンドルによって識別されるユーザーインターフェイスを WPF ユーザーインターフェイスから表示するために存在します。 詳細については、「[WPF と Win32 の相互運用性](../advanced/wpf-and-win32-interoperation.md)」を参照してください。

要約すると<xref:System.AddIn.Contract.INativeHandleContract>、 <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>、、 <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A>およびは、WPF UI のウィンドウハンドルを、アドインからホストアプリケーションに渡すことができるようにするためです。このアプリケーションは、 <xref:System.Windows.Interop.HwndHost>によってカプセル化され、ホストアプリケーションの UI に表示されます。

> [!NOTE]
> ホストアプリケーションはを取得<xref:System.Windows.Interop.HwndHost>するため、ホストアプリケーションは、によっ<xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A>て返されたオブジェクトをアドインによって実装されている型<xref:System.Windows.Controls.UserControl>(たとえば、) に変換できません。

具体的には、 <xref:System.Windows.Interop.HwndHost>には、ホストアプリケーションでそれらを使用する方法に影響を与えるいくつかの制限があります。 ただし、WPF <xref:System.Windows.Interop.HwndHost>は、アドインシナリオ用にいくつかの機能を備えています。 その利点と制約について、以下に説明します。

<a name="WPFAddInModelBenefits"></a>

## <a name="wpf-add-in-benefits"></a>WPF アドインの利点

Wpf アドインのユーザーインターフェイスは、から<xref:System.Windows.Interop.HwndHost>派生した内部クラスを使用してホストアプリケーションから表示されるため、これらのユーザーインターフェイスは、レイアウトなどの wpf UI サービスに関して、の<xref:System.Windows.Interop.HwndHost>機能によって制約されます。レンダリング、データバインディング、スタイル、テンプレート、およびリソース。 ただし、WPF は、次<xref:System.Windows.Interop.HwndHost>のような追加機能を使用して内部サブクラスを補強します。

- ホストアプリケーションの UI とアドインの UI の間をタブ移動します。 "アドインは UI です" のプログラミングモデルでは、アドインが完全に信頼されているか、 <xref:System.AddIn.Pipeline.ContractBase.QueryContract%2A>部分的に信頼されているかに関係ない、アドイン側アダプターをオーバーライドして、タブを有効にする必要があることに注意してください。

- ホストアプリケーションのユーザーインターフェイスから表示されるアドインユーザーインターフェイスのアクセシビリティ要件に従います。

- 複数のアプリケーションドメインのシナリオで、WPF アプリケーションを安全に実行できるようにします。

- アドインがセキュリティ分離 (部分信頼セキュリティサンドボックス) を使用して実行されている場合に、アドイン UI ウィンドウハンドルへの不正アクセスを防止します。 を<xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>呼び出すと、次のセキュリティが保証します。

  - "アドインが UI を返す" プログラミングモデルでは、分離境界を越えてアドイン UI のウィンドウハンドルを渡す唯一の方法は、を呼び出す<xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>ことです。

  - "アドインは UI である" プログラミングモデルの場合、アドイン側<xref:System.AddIn.Pipeline.ContractBase.QueryContract%2A>アダプターでのオーバーライドと (前の例で<xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>示されているように) の呼び出しが必要です。これは、アドイン側アダプターの`QueryContract`実装をホスト側アダプター。

- アプリケーション ドメインの実行を何重にも保護します。 アプリケーション ドメインの制約に起因して、アドイン アプリケーション ドメインでスローされた未処理の例外は、分離境界が存在していても、アプリケーション全体のクラッシュにつながります。 ただし、WPF と .NET Framework アドインモデルでは、この問題を回避し、アプリケーションの安定性を向上させる簡単な方法が提供されます。 ホストアプリケーションが wpf アプリケーションである場合、UI を<xref:System.Windows.Threading.Dispatcher>表示する wpf アドインによって、アプリケーションドメインが実行されているスレッドのが作成されます。 WPF アドイン<xref:System.Windows.Threading.Dispatcher.UnhandledException> <xref:System.Windows.Threading.Dispatcher>ののイベントを処理することによって、アプリケーションドメインで発生するすべてのハンドルされない例外を検出できます。 は、 <xref:System.Windows.Threading.Dispatcher> <xref:System.Windows.Threading.Dispatcher.CurrentDispatcher%2A>プロパティから取得できます。

<a name="WPFAddInModelLimitations"></a>

## <a name="wpf-add-in-limitations"></a>WPF アドインの制約

<xref:System.Windows.Interop.HwndSource> 、<xref:System.Windows.Interop.HwndHost>、およびウィンドウハンドルによって提供される既定の動作に WPF が追加する利点以外にも、ホストアプリケーションから表示されるアドインユーザーインターフェイスには制限があります。

- ホストアプリケーションから表示されるアドインユーザーインターフェイスは、ホストアプリケーションのクリッピング動作を考慮しません。

- 相互運用性シナリオの*空域*の概念もアドインに適用されます (「[技術領域の概要](../advanced/technology-regions-overview.md)」を参照)。

- リソースの継承、データバインディング、コマンドのコマンドなど、ホストアプリケーションの UI サービスは、アドインのユーザーインターフェイスで自動的に使用できるわけではありません。 これらのサービスをアドインに提供するには、パイプラインを更新する必要があります。

- アドインの UI は、回転、拡大縮小、傾斜、または変換による影響を受けません (「[変換の概要](../graphics-multimedia/transforms-overview.md)」を参照してください)。

- <xref:System.Drawing>名前空間からの描画操作によってレンダリングされるアドインユーザーインターフェイス内のコンテンツには、アルファブレンドを含めることができます。 ただし、アドイン UI と、それを含むホストアプリケーション UI は、どちらも 100% 不透明である必要があります。言い換えると、 `Opacity`両方のプロパティが1に設定されている必要があります。

- アドイン UI を含むホストアプリケーションのウィンドウの`true`プロパティがに設定されている場合、アドインは非表示になります。<xref:System.Windows.Window.AllowsTransparency%2A> これは、アドイン UI が 100% 不透明である (つまり、 `Opacity`プロパティの値が1である) 場合でも同様です。

- アドイン UI は、同じトップレベルウィンドウ内の他の WPF 要素の上に表示される必要があります。

- を使用して、 <xref:System.Windows.Media.VisualBrush>アドインの UI の一部をレンダリングすることはできません。 代わりに、アドインは、生成された UI のスナップショットを取得して、コントラクトによって定義されたメソッドを使用してホストアプリケーションに渡すことができるビットマップを作成することができます。

- アドインの UI で、メディアファイル<xref:System.Windows.Controls.MediaElement>をから再生することはできません。

- アドイン UI 用に生成されたマウスイベントは、ホストアプリケーション`IsMouseOver`では受信も発生もされず、ホストアプリケーション UI のプロパティの`false`値はになります。

- アドイン UI `GotFocus`内のコントロール間でフォーカスが移動すると、イベント`LostFocus`とイベントはホストアプリケーションによって受信も発生もされません。

- アドイン UI を含むホストアプリケーションの部分は、印刷時に白で表示されます。

- アドイン UI によっ<xref:System.Windows.Threading.Dispatcher>て作成されたすべてのディスパッチャー (を参照) は、ホストアプリケーションが実行を継続する場合に、所有者アドインがアンロードされる前に手動でシャットダウンする必要があります。 コントラクトは、アドインがアンロードされる前に、ホストアプリケーションがアドインを通知できるようにするメソッドを実装できます。これにより、アドインの UI はそのディスパッチャーをシャットダウンできます。

- アドインの UI が<xref:System.Windows.Controls.InkCanvas>の場合<xref:System.Windows.Controls.InkCanvas>、またはが含まれている場合は、アドインをアンロードできません。

<a name="PerformanceOptimization"></a>

## <a name="performance-optimization"></a>パフォーマンスの最適化

既定では、複数のアプリケーションドメインを使用すると、各アプリケーションに必要なさまざまな .NET Framework アセンブリが、そのアプリケーションのドメインに読み込まれます。 その結果、新しいアプリケーション ドメインを作成してその中でアプリケーションを開始するために必要な時間がパフォーマンスに影響します。 ただし、アプリケーションドメインが既に読み込まれている場合は、アプリケーションドメイン間でアセンブリを共有するようにアプリケーションに指示することによって、開始時間を短縮する方法を .NET Framework ます。 これを行うには、 <xref:System.LoaderOptimizationAttribute>属性を使用します。これは、エントリポイントメソッド`Main`() に適用する必要があります。 この場合、アプリケーション定義を実装するコードのみを使用する必要があります (「[アプリケーション管理の概要](application-management-overview.md)」を参照)。

## <a name="see-also"></a>関連項目

- <xref:System.LoaderOptimizationAttribute>
- [アドインおよび拡張機能](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb384200(v%3dvs.100))
- [アプリケーション ドメイン](../../app-domains/application-domains.md)
- [.NET Framework リモート処理の概要](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/kwdt6w2k(v=vs.100))
- [オブジェクトをリモート処理可能にする](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/wcf3swha(v=vs.100))
- [方法トピック](how-to-topics.md)
