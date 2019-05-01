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
ms.openlocfilehash: 7c02ddca01260a68880630bcb014c5cc4dc4370b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61971315"
---
# <a name="wpf-add-ins-overview"></a>WPF アドインの概要
<a name="Introduction"></a> .NET Framework には、開発者がアドイン機能拡張をサポートするアプリケーションの作成に使用できるアドイン モデルが含まれています。 このアドイン モデルを使用することで、アプリケーション機能に統合され、アプリケーション機能を拡張するアドインを作成できます。 シナリオによっては、アプリケーションは、アドインによって提供されるユーザー インターフェイスの表示にも必要です。このトピックでは、WPF がこれらのシナリオ、その利点、および制限事項の背後にあるアーキテクチャを有効にする .NET Framework アドイン モデルを強化する方法を示します。  

<a name="Requirements"></a>   
## <a name="prerequisites"></a>必須コンポーネント  
 .NET Framework アドイン モデルに関する知識が必要です。 詳細については、「[アドインおよび拡張機能](/previous-versions/dotnet/netframework-4.0/bb384200(v%3dvs.100))」を参照してください。  
  
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
  
- **探索**:ホスト アプリケーションによってサポートされるコントラクトに準拠しているアドインを検索します。  
  
- **アクティブ化**:読み込み、実行、およびアドインとの通信を確立します。  
  
- **分離**:アプリケーション ドメインまたはプロセスを使用して、潜在的なセキュリティとアドインの実行の問題からアプリケーションを保護する、分離境界を確立します。  
  
- **通信**:アドインを許可して、メソッドを呼び出すと、データを渡すことによって分離境界を越えて互いと通信するアプリケーションをホストします。  
  
- **有効期間管理**:読み込みとクリーニング、予測可能な方法でアプリケーション ドメインとプロセスをアンロード (を参照してください[アプリケーション ドメイン](../../app-domains/application-domains.md))。  
  
- **バージョン管理**:アプリケーションをホストとアドイン通信できることも新しいバージョンのいずれかが作成されたときにすることです。  
  
 このことからわかるように、堅牢なアドイン モデルの開発は簡単なことではありません。 このため、.NET Framework は、アドイン モデルを構築するためのインフラストラクチャを提供します。  
  
> [!NOTE]
>  アドインの詳細については、「[アドインおよび拡張機能](/previous-versions/dotnet/netframework-4.0/bb384200(v%3dvs.100))」を参照してください。  
  
<a name="NETFrameworkAddInModelOverview"></a>   
## <a name="net-framework-add-in-model-overview"></a>.NET Framework アドイン モデルの概要  
 .NET Framework アドイン モデルにある、<xref:System.AddIn>名前空間には、アドイン機能拡張の開発を簡略化できるように設計された型のセットが含まれています。 .NET Framework アドイン モデルの基本単位は、*コントラクト*アドインで相互通信、方法、ホスト アプリケーションを定義します。 コントラクトのホスト アプリケーション固有の*ビュー*を使用して、コントラクトはホスト アプリケーションに公開されます。 同様に、コントラクトのアドイン固有の*ビュー*がアドインに公開されます。 *アダプター*は、ホスト アプリケーションとアドインが、コントラクトの対応するビュー間で通信するために使用されます。 コントラクト、ビュー、およびアダプターはセグメントと見なされ、関連セグメントのセットが*パイプライン*を構成します。 パイプラインは、基盤となる、.NET Framework アドイン モデルでは、探索、アクティブ化、セキュリティの分離、実行の分離 (アプリケーション ドメインとプロセスの両方を使用して)、通信、有効期間管理、およびバージョン管理がサポートしています。  
  
 このサポート全体を使用して、開発者はホスト アプリケーションの機能を統合するアドインをビルドできます。 ただし、一部のシナリオでは、ホスト アプリケーションがアドインによって提供されるユーザー インターフェイスを表示する必要があります.NET Framework では、各プレゼンテーション テクノロジには、ユーザー インターフェイスを実装するための独自のモデルがあるため、.NET Framework アドイン モデルは特定のプレゼンテーション テクノロジをサポートしません。 代わりに、WPF は .NET Framework アドイン モデルの UI アドインのサポートを拡張します。  
  
<a name="WPFAddInModel"></a>   
## <a name="wpf-add-ins"></a>WPF アドイン  
 WPF、.NET Framework アドイン モデルと組み合わせて使用するさまざまなホスト アプリケーションがアドインからのユーザー インターフェイスを表示する必要があるシナリオに対処できます。具体的には、これらのシナリオに次の 2 つのプログラミング モデルを使用した WPF によって対応します。  
  
1. **アドインが UI を返す**。 アドインの UI を返す、ホスト アプリケーションにメソッドの呼び出しを使用して、コントラクトで定義されています。 このシナリオは、次の場合に使用されます。  
  
    - アドインによって返される UI の外観はいずれかのデータに依存または条件に存在する、実行時にのみなど動的にレポートを生成します。  
  
    - アドインによって提供されるサービスの UI アドインで使用できるホスト アプリケーションの UI と異なります。  
  
    - アドインは主にサービスをホスト アプリケーションの実行し、UI を使用してホスト アプリケーションにステータスをレポートします。  
  
2. **アドインが UI である**。 アドインのコントラクトで定義されている、UI であります。 このシナリオは、次の場合に使用されます。  
  
    - アドインは表示以外のサービス (広告など) を提供しない。  
  
    - アドインによって提供されるサービスの UI は、そのアドインを電卓、カラー ピッカーなどが使用できるすべてのホスト アプリケーションに共通です。  
  
 これらのシナリオでは、ホスト アプリケーションとアドイン アプリケーション ドメイン間で UI オブジェクトを渡すことができますが必要です。 以降、.NET Framework アドイン モデルはアプリケーション ドメイン間で通信するリモート処理に依存それらの間で渡されるオブジェクトはリモート処理可能にする必要があります。  
  
 リモート処理可能なオブジェクトとは、次の 1 つ以上に該当するクラスのインスタンスです。  
  
- 派生した、<xref:System.MarshalByRefObject>クラス。  
  
- <xref:System.Runtime.Serialization.ISerializable> インターフェイスを実装します。  
  
- <xref:System.SerializableAttribute>属性が適用されています。  
  
> [!NOTE]
>  リモート処理可能な .NET Framework オブジェクトの作成に関する詳細については、次を参照してください。[オブジェクトのためのリモート処理可能](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/wcf3swha(v=vs.100))します。  
  
 WPF の UI 型は、リモート処理可能ではありません。 この問題を解決するためには、WPF は、ホスト アプリケーションから表示する WPF の UI アドインを使用して作成を有効にする .NET Framework アドイン モデルを拡張します。 このサポートが 2 つの種類での WPF で提供される:<xref:System.AddIn.Contract.INativeHandleContract>インターフェイスと 2 つの静的メソッドによって実装される、<xref:System.AddIn.Pipeline.FrameworkElementAdapters>クラス:<xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A>と<xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>します。 大まかに、これらの型とメソッドは次のように使用されます。  
  
1. WPF では、アドインによって提供されるユーザー インターフェイスから直接または間接的に派生クラスである<xref:System.Windows.FrameworkElement>図形、コントロール、ユーザー コントロール、レイアウト パネル、ページなどです。  
  
2. コントラクトは、UI がアドインとホスト アプリケーション間で渡されることを宣言する任意の場所として宣言する必要があります、 <xref:System.AddIn.Contract.INativeHandleContract> (いない、 <xref:System.Windows.FrameworkElement>)。<xref:System.AddIn.Contract.INativeHandleContract>分離境界を越えて渡すことができる追加の UI のリモート処理可能な表現です。  
  
3. アドインのアプリケーション ドメインから渡される前に、<xref:System.Windows.FrameworkElement>としてパッケージ化されて、<xref:System.AddIn.Contract.INativeHandleContract>呼び出して<xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>します。  
  
4. ホスト アプリケーションのアプリケーション ドメインに渡された後、<xref:System.AddIn.Contract.INativeHandleContract>として再パッケージ化する必要があります、<xref:System.Windows.FrameworkElement>呼び出して<xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A>します。  
  
 どの<xref:System.AddIn.Contract.INativeHandleContract>、<xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A>と<xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>使用は、特定のシナリオによって異なります。 以降のセクションでは、各プログラミング モデルについて詳しく説明していきます。  
  
<a name="ReturnUIFromAddInContract"></a>   
## <a name="add-in-returns-a-user-interface"></a>ユーザー インターフェイスを返すアドイン  
 アドインをホスト アプリケーションに UI を返す、次が必要です。  
  
1. ホスト アプリケーション、アドイン、およびパイプラインを作成する .NET Framework での説明に従って[アドインおよび拡張](/previous-versions/dotnet/netframework-4.0/bb384200(v%3dvs.100))ドキュメント。  
  
2. コントラクトを実装する必要があります<xref:System.AddIn.Contract.IContract>と、コントラクトに UI を返すには、型の戻り値を持つメソッドを宣言する必要があります<xref:System.AddIn.Contract.INativeHandleContract>します。  
  
3. UI アドインとホスト アプリケーション間で渡される必要があります直接または間接的に派生から<xref:System.Windows.FrameworkElement>します。  
  
4. アドインによって返される UI を変換する必要があります、<xref:System.Windows.FrameworkElement>を<xref:System.AddIn.Contract.INativeHandleContract>分離境界を越える前にします。  
  
5. 返される UI を変換する必要があります、<xref:System.AddIn.Contract.INativeHandleContract>を<xref:System.Windows.FrameworkElement>分離境界を越えた後。  
  
6. ホスト アプリケーションを表示、返された<xref:System.Windows.FrameworkElement>します。  
  
 UI を返すアドインを実装する方法については、例では、次を参照してください。 [UI を作成するアドインを返す](how-to-create-an-add-in-that-returns-a-ui.md)します。  
  
<a name="AddInIsAUI"></a>   
## <a name="add-in-is-a-user-interface"></a>ユーザー インターフェイスであるアドイン  
 アドインの UI である、ときに、次が必要です。  
  
1. ホスト アプリケーション、アドイン、およびパイプラインを作成する .NET Framework での説明に従って[アドインおよび拡張](/previous-versions/dotnet/netframework-4.0/bb384200(v%3dvs.100))ドキュメント。  
  
2. アドインのコントラクト インターフェイスを実装する必要があります<xref:System.AddIn.Contract.INativeHandleContract>します。  
  
3. アドイン、ホスト アプリケーションに渡される必要があります直接的または間接的に派生から<xref:System.Windows.FrameworkElement>します。  
  
4. アドインから変換する必要があります、<xref:System.Windows.FrameworkElement>を<xref:System.AddIn.Contract.INativeHandleContract>分離境界を越える前にします。  
  
5. アドインから変換する必要があります、<xref:System.AddIn.Contract.INativeHandleContract>を<xref:System.Windows.FrameworkElement>分離境界を越えた後。  
  
6. ホスト アプリケーションを表示、返された<xref:System.Windows.FrameworkElement>します。  
  
 UI であるアドインを実装する方法については、例では、次を参照してください。 [UI を作成するアドインは](how-to-create-an-add-in-that-is-a-ui.md)します。  
  
<a name="ReturningMultipleUIsFromAnAddIn"></a>   
## <a name="returning-multiple-uis-from-an-add-in"></a>複数の UI を返すアドイン  
 アドインは、多くの場合、表示するホスト アプリケーション用の複数のユーザー インターフェイスを提供します。 たとえばも UI としても、ホスト アプリケーションにステータス情報を提供する UI は、アドインを検討してください。 このようなアドインは、[ユーザー インターフェイスを返すアドイン](#ReturnUIFromAddInContract)のモデルと[ユーザー インターフェイスであるアドイン](#AddInIsAUI)のモデルの両方の手法を組み合わせることで実装できます。  
  
<a name="AddInsAndXBAPs"></a>   
## <a name="add-ins-and-xaml-browser-applications"></a>アドインと XAML ブラウザー アプリケーション  
 ここまでの例では、ホスト アプリケーションはスタンドアロン アプリケーションとしてインストールされています。 [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)] はアドインをホストすることもできますが、そのためには次に示すビルドと実装の要件を満たす必要があります。  
  
- パイプライン (フォルダーとアセンブリ) とアドイン アセンブリを、[!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] と同じフォルダーにある、クライアント コンピューターの [!INCLUDE[TLA#tla_clickonce](../../../../includes/tlasharptla-clickonce-md.md)] アプリケーション キャッシュにダウンロードするよう、[!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] アプリケーション マニフェストを特別に構成する必要があります。  
  
- アドインを探索して読み込む [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] コードで、[!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] の [!INCLUDE[TLA2#tla_clickonce](../../../../includes/tla2sharptla-clickonce-md.md)] アプリケーション キャッシュを、パイプラインとアドインの場所として使用する必要があります。  
  
- [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] は、アドインが起点サイトにある圧縮しないファイルを参照する場合、アドインを特別なセキュリティ コンテキストの下で読み込む必要があります。[!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] によってホストされる場合、アドインが参照できるのは、ホスト アプリケーションの起点サイトにある圧縮しないファイルのみです。  
  
 これらのタスクについて、次のサブセクションで詳しく説明します。  
  
### <a name="configuring-the-pipeline-and-add-in-for-clickonce-deployment"></a>ClickOnce 配置のためのパイプラインとアドインの構成  
 [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] は、[!INCLUDE[TLA2#tla_clickonce](../../../../includes/tla2sharptla-clickonce-md.md)] 配置キャッシュの安全なフォルダーにダウンロードされ、そこから実行されます。 [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] でアドインをホストするには、パイプラインとアドインのアセンブリも同じ安全なフォルダーにダウンロードする必要があります。 このためには、パイプラインとアドインのどちらのアセンブリもダウンロード対象に含まれるよう、アプリケーション マニフェストを構成する必要があります。 これは、[!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)] で実行することが最も簡単ですが、[!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)] でパイプラインをアセンブリとして検出するには、パイプラインとアドインのアセンブリが、ホスト [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] プロジェクトのルート フォルダーに存在する必要があります。  
  
 したがって、まず、パイプライン アセンブリとアドイン アセンブリの各プロジェクトのビルド出力を設定し、パイプラインとアドインのアセンブリを [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] プロジェクトのルートにビルドします。 次の表は、ホストの [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] プロジェクトと同じソリューションとルートのフォルダーに格納される、パイプライン アセンブリ プロジェクトとアドイン アセンブリ プロジェクトのビルド出力パスを示します。  
  
 表 1:XBAP でホストされているパイプライン アセンブリのビルド出力パス  
  
|パイプライン アセンブリ プロジェクト|ビルド出力パス|  
|-------------------------------|-----------------------|  
|コントラクト|`..\HostXBAP\Contracts\`|  
|アドイン ビュー|`..\HostXBAP\AddInViews\`|  
|アドイン側のアダプター|`..\HostXBAP\AddInSideAdapters\`|  
|ホスト側のアダプター|`..\HostXBAP\HostSideAdapters\`|  
|アドイン|`..\HostXBAP\AddIns\WPFAddIn1`|  
  
 次に、パイプライン アセンブリとアドイン アセンブリを [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] コンテンツ ファイルとして [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)] に指定します。手順は次のとおりです。  
  
1. ソリューション エクスプローラーで各パイプライン フォルダーを右クリックし、**[プロジェクトに含める]** を選択して、パイプラインとアドインのアセンブリをプロジェクトに含めます。  
  
2. **[プロパティ]** ウィンドウで、パイプライン アセンブリとアドイン アセンブリそれぞれについて、**[ビルド アクション]** を **[コンテンツ]** に設定します。  
  
 最後に、パイプラインとアドインのどちらのアセンブリ ファイルもダウンロード対象に含まれるよう、アプリケーション マニフェストを構成します。 ファイルは、[!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] アプリケーションが占有する [!INCLUDE[TLA2#tla_clickonce](../../../../includes/tla2sharptla-clickonce-md.md)] キャッシュ内のフォルダーのルートにあるフォルダー内に存在している必要があります。 この構成は、次の手順に従って、[!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)] で行うことができます。  
  
1. [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] プロジェクトを右クリックして、**[プロパティ]**、**[発行]** の順にクリックし、**[アプリケーション ファイル]** をクリックします。  
  
2. **[アプリケーション ファイル]** ダイアログ ボックスで、各パイプラインとアドインの DLL の **[発行の状況]** を **[含める (自動)]** に設定し、各パイプラインとアドインの DLL の **[ダウンロード グループ]** を **[(必須)]** に設定します。  
  
### <a name="using-the-pipeline-and-add-in-from-the-application-base"></a>アプリケーション ベースからのパイプラインとアドインの使用  
 パイプラインとアドインは [!INCLUDE[TLA2#tla_clickonce](../../../../includes/tla2sharptla-clickonce-md.md)] 配置用に構成されると、同じ [!INCLUDE[TLA2#tla_clickonce](../../../../includes/tla2sharptla-clickonce-md.md)] キャッシュ フォルダーに [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] としてダウンロードされます。 このパイプラインとアドインを [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] から使用するには、[!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] コードがそれらをアプリケーション ベースから取得する必要があります。 さまざまな種類とパイプラインとアドインを使用して .NET Framework アドイン モデルのメンバーは、このシナリオで特別なサポートを提供します。 まず、パスがで識別される、<xref:System.AddIn.Hosting.PipelineStoreLocation.ApplicationBase>列挙値。 この値を適切なアドイン メンバーのオーバーロードと併用することで、次のようなパイプラインを使用できます。  
  
- <xref:System.AddIn.Hosting.AddInStore.FindAddIns%28System.Type%2CSystem.AddIn.Hosting.PipelineStoreLocation%29?displayProperty=nameWithType>  
  
- <xref:System.AddIn.Hosting.AddInStore.FindAddIns%28System.Type%2CSystem.AddIn.Hosting.PipelineStoreLocation%2CSystem.String%5B%5D%29?displayProperty=nameWithType>  
  
- <xref:System.AddIn.Hosting.AddInStore.Rebuild%28System.AddIn.Hosting.PipelineStoreLocation%29?displayProperty=nameWithType>  
  
- <xref:System.AddIn.Hosting.AddInStore.Update%28System.AddIn.Hosting.PipelineStoreLocation%29?displayProperty=nameWithType>  
  
### <a name="accessing-the-hosts-site-of-origin"></a>ホストの起点サイトへのアクセス  
 アドインが起点サイトのファイルを参照できるように、アドインはホスト アプリケーションと等価なセキュリティ分離を使用して読み込む必要があります。 このセキュリティ レベルがで識別される、<xref:System.AddIn.Hosting.AddInSecurityLevel.Host?displayProperty=nameWithType>列挙の値に渡されると、<xref:System.AddIn.Hosting.AddInToken.Activate%2A>メソッド、アドインをアクティブ化します。  
  
<a name="WPFAddInModelArchitecture"></a>   
## <a name="wpf-add-in-architecture"></a>WPF アドイン アーキテクチャ  
 最上位のレベルでは、前述したように、WPF により、ユーザー インターフェイスを実装する .NET Framework のアドイン (から直接または間接的に派生する<xref:System.Windows.FrameworkElement>) を使用して<xref:System.AddIn.Contract.INativeHandleContract>、<xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>と<xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A>します。 ホスト アプリケーションが返されることになります、 <xref:System.Windows.FrameworkElement> UI から、ホスト アプリケーションで表示されています。  
  
 単純な UI アドイン シナリオでこれは、できるだけ詳しく開発者が必要です。 特にレイアウト、リソース、およびデータ バインドなどの追加の WPF サービスを利用しようとするより複雑なシナリオは、その利点を理解する WPF が .NET Framework アドイン モデルの UI サポートを拡張する方法の詳細な知識が必要制限事項。  
  
 基本的には、WPF に合格しなかった UI アドインからホスト アプリケーションです。代わりに、WPF は、WPF の相互運用性を使用して、UI の Win32 ウィンドウ ハンドルを渡します。 そのため、アドインからの UI は、ホスト アプリケーションに渡される、次のようにします。  
  
- アドイン側では、WPF は、ホスト アプリケーションによって表示される UI のウィンドウ ハンドルを取得します。 ウィンドウ ハンドルがから派生する内部の WPF クラスによってカプセル化された<xref:System.Windows.Interop.HwndSource>実装と<xref:System.AddIn.Contract.INativeHandleContract>します。 このクラスのインスタンスがによって返される<xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>はアドインのアプリケーション ドメインからホスト アプリケーションのアプリケーション ドメインにマーシャ リングとします。  
  
- WPF には、ホスト アプリケーション側で、<xref:System.Windows.Interop.HwndSource>内部の WPF クラスから派生したとして<xref:System.Windows.Interop.HwndHost>消費<xref:System.AddIn.Contract.INativeHandleContract>します。 このクラスのインスタンスがによって返される<xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A>ホスト アプリケーションにします。  
  
 <xref:System.Windows.Interop.HwndHost> 存在すると、WPF ユーザー インターフェイスから、ウィンドウ ハンドルによって識別される、ユーザー インターフェイスを表示します。 詳細については、「[WPF と Win32 の相互運用性](../advanced/wpf-and-win32-interoperation.md)」を参照してください。  
  
 要約すると、 <xref:System.AddIn.Contract.INativeHandleContract>、<xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>と<xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A>に渡されるアドインからホスト アプリケーションによってカプセル化は、WPF UI のウィンドウ ハンドルを許可する存在、<xref:System.Windows.Interop.HwndHost>ホスト アプリケーションの UI を表示します。  
  
> [!NOTE]
>  ホスト アプリケーションを取得するため、 <xref:System.Windows.Interop.HwndHost>、ホスト アプリケーションによって返されるオブジェクトを変換できません<xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A>アドインによって、型に実装されます (たとえば、 <xref:System.Windows.Controls.UserControl>)。  
  
 その性質上、<xref:System.Windows.Interop.HwndHost>はホスト アプリケーションの使用方法に影響を与える特定の制限があります。 ただし、WPF を拡張<xref:System.Windows.Interop.HwndHost>アドイン シナリオのいくつかの機能を使用します。 その利点と制約について、以下に説明します。  
  
<a name="WPFAddInModelBenefits"></a>   
## <a name="wpf-add-in-benefits"></a>WPF アドインの利点  
 WPF アドインのユーザー インターフェイスがから派生する内部クラスを使用してホスト アプリケーションから表示されるため、 <xref:System.Windows.Interop.HwndHost>、それらのユーザー インターフェイスは、の機能によって制限されます<xref:System.Windows.Interop.HwndHost>レイアウトなどの WPF UI サービスに関してレンダリング、データ バインディング、スタイル、テンプレート、およびリソース。 ただし、WPF はその内部<xref:System.Windows.Interop.HwndHost>次を含む追加の機能を備えたサブクラスです。  
  
- ホスト アプリケーションの UI と、アドインの UI 間のタブ移動します。 「UI であるアドイン」プログラミング モデルには、オーバーライドする追加アドイン側アダプターが必要があります<xref:System.AddIn.Pipeline.ContractBase.QueryContract%2A>アドインが完全に信頼できるか部分的に信頼されているかどうか、tab キーを有効にします。  
  
- ホスト アプリケーションのユーザー インターフェイスから表示されるアドインのユーザー インターフェイスのアクセシビリティ要件を順守します。  
  
- WPF アプリケーションを複数のアプリケーション ドメインのシナリオで安全に実行を有効にします。  
  
- アドインの UI に不正なアクセスを防止 ウィンドウでは、セキュリティの分離 (つまり、部分信頼セキュリティ サンド ボックス) でアドインが実行される場合を処理します。 呼び出す<xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>このセキュリティを確保します。  
  
    - ウィンドウ ハンドルをアドインの UI の分離の境界を越えて渡す唯一の方法は"アドインが UI を返す"プログラミング モデルを呼び出す<xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>します。  
  
    - 「アドインが UI を」プログラミング モデルのオーバーライド<xref:System.AddIn.Pipeline.ContractBase.QueryContract%2A>追加アドイン側アダプターと呼び出し元の<xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>(として上記の例に示すように) を呼び出して追加アドイン側アダプターの処理として必要です`QueryContract`実装から、ホスト側アダプター。  
  
- アプリケーション ドメインの実行を何重にも保護します。 アプリケーション ドメインの制約に起因して、アドイン アプリケーション ドメインでスローされた未処理の例外は、分離境界が存在していても、アプリケーション全体のクラッシュにつながります。 ただし、WPF と .NET Framework アドイン モデルは、この問題を回避し、アプリケーションの安定性を向上させる簡単な方法を提供します。 UI を表示する WPF アドインを作成、<xref:System.Windows.Threading.Dispatcher>のアプリケーション ドメインは、ホスト アプリケーションが WPF アプリケーションの場合で実行されるスレッドの。 処理することにより、アプリケーション ドメインで発生するすべての未処理の例外を検出することができます、 <xref:System.Windows.Threading.Dispatcher.UnhandledException> 、WPF アドインのイベント<xref:System.Windows.Threading.Dispatcher>します。 取得することができます、<xref:System.Windows.Threading.Dispatcher>から、<xref:System.Windows.Threading.Dispatcher.CurrentDispatcher%2A>プロパティ。  
  
<a name="WPFAddInModelLimitations"></a>   
## <a name="wpf-add-in-limitations"></a>WPF アドインの制約  
 WPF によって提供される既定の動作に追加するメリットを超える<xref:System.Windows.Interop.HwndSource>、 <xref:System.Windows.Interop.HwndHost>、およびウィンドウのハンドル、ホスト アプリケーションから表示されるアドインのユーザー インターフェイスの制限があります。  
  
- ホスト アプリケーションから表示されるアドインのユーザー インターフェイスでは、ホスト アプリケーションのクリッピング動作が反映されません。  
  
- 相互運用性シナリオの*空域*の概念もアドインに適用されます (「[技術領域の概要](../advanced/technology-regions-overview.md)」を参照)。  
  
- リソースの継承、データ バインディング、およびコマンドを実行するは自動的に追加で使用できるなど、ホスト アプリケーションの UI のサービスのユーザー インターフェイス。 これらのサービスをアドインに提供するには、パイプラインを更新する必要があります。  
  
- アドインの UI ことはできません回転、拡大縮小、傾斜、またはそれ以外の場合、変換によって影響を受ける (を参照してください[変換の概要](../graphics-multimedia/transforms-overview.md))。  
  
- 描画からの操作によって表示されるアドインのユーザー インターフェイス内のコンテンツ、<xref:System.Drawing>アルファ ブレンド名前空間を含めることができます。 ただし、アドインの UI とホスト アプリケーションが含まれる UI 不透明になります。 100% でなければなりませんつまり、`Opacity`両方のプロパティを 1 に設定する必要があります。  
  
- 場合、<xref:System.Windows.Window.AllowsTransparency%2A>アドインの UI を含むホスト アプリケーションのウィンドウのプロパティに設定されて`true`、アドインは表示されません。 これは、アドインの UI が 100% 不透明である場合でも当てはまります (つまり、`Opacity`プロパティが 1 の値を持つ)。  
  
- アドインの UI は、同じトップレベル ウィンドウ内の他の WPF 要素の上に表示する必要があります。  
  
- アドインの UI の一部をレンダリングできませんを使用して、<xref:System.Windows.Media.VisualBrush>します。 代わりに、アドインは、コントラクトによって定義されたメソッドを使用してホスト アプリケーションに渡すことができるビットマップを作成する生成された UI のスナップショットをかかる場合があります。  
  
- メディア ファイルを再生することはできません、<xref:System.Windows.Controls.MediaElement>アドインの UI にします。  
  
- アドインの UI の生成されたマウス イベントが受信も、ホスト アプリケーションによって生成されると、`IsMouseOver`ホスト アプリケーションの UI のプロパティの値を持つ`false`します。  
  
- アドインの UI でコントロールの間でフォーカスが移動したとき、`GotFocus`と`LostFocus`イベントが受信も、ホスト アプリケーションによって発生します。  
  
- アドインの UI を含むホスト アプリケーションの部分では、印刷時に白の項目が表示されます。  
  
- すべてのディスパッチャー (を参照してください<xref:System.Windows.Threading.Dispatcher>)、アドインによって作成された UI する必要がありますが手動でシャット ダウン、オーナー アドインがアンロードの直前、ホスト アプリケーションが実行を継続する場合。 コントラクトは、アドインができるため、そのディスパッチャーをシャット ダウンするアドインの UI、アンロードする前に、アドインをホスト アプリケーションを許可するメソッドを実装できます。  
  
- アドインの UI がある場合、<xref:System.Windows.Controls.InkCanvas>または含まれている、 <xref:System.Windows.Controls.InkCanvas>、アドインをアンロードすることはできません。  
  
<a name="PerformanceOptimization"></a>   
## <a name="performance-optimization"></a>パフォーマンスの最適化  
 既定では、複数のアプリケーション ドメインを使用している場合の各アプリケーションに必要なさまざまな .NET Framework アセンブリがすべて読み込まれますそのアプリケーションのドメインにします。 その結果、新しいアプリケーション ドメインを作成してその中でアプリケーションを開始するために必要な時間がパフォーマンスに影響します。 ただし、.NET Framework は、既に読み込まれている場合は、アプリケーション ドメイン間でアセンブリを共有するアプリケーションに指示して開始時間を短縮するための手段を提供します。 使用してこれを行う、<xref:System.LoaderOptimizationAttribute>属性には、エントリ ポイント メソッドに適用する必要があります (`Main`)。 この場合、アプリケーション定義を実装するコードのみを使用する必要があります (「[アプリケーション管理の概要](application-management-overview.md)」を参照)。  
  
## <a name="see-also"></a>関連項目

- <xref:System.LoaderOptimizationAttribute>
- [アドインおよび拡張機能](/previous-versions/dotnet/netframework-4.0/bb384200(v%3dvs.100))
- [アプリケーション ドメイン](../../app-domains/application-domains.md)
- [.NET framework リモート処理の概要](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/kwdt6w2k(v=vs.100))
- [オブジェクトをリモート処理可能](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/wcf3swha(v=vs.100))
- [方法トピック](how-to-topics.md)
