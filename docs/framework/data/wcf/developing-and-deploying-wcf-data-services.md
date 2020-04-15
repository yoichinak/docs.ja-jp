---
title: WCF Data Services の開発と配置
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, developing
- WCF Data Services, deploying
- deploying [WCF Data Services
- developing applications [WCF Data Services]
ms.assetid: 6557c0e3-5aea-4f6e-bc14-77ad317a168b
ms.openlocfilehash: 4591175da5078a194bfe69884701e5432a0c38a3
ms.sourcegitcommit: c91110ef6ee3fedb591f3d628dc17739c4a7071e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/15/2020
ms.locfileid: "81389727"
---
# <a name="develop-and-deploy-wcf-data-services"></a>WCF データ サービスの開発と展開

この記事では、WCF データ サービスの開発と展開に関する情報を提供します。 WCF データ サービスの基本情報については、「[はじめに](getting-started-with-wcf-data-services.md)」および「[概要](wcf-data-services-overview.md)」を参照してください。

## <a name="develop-wcf-data-services"></a>WCF データ サービスの開発

オープン データ プロトコル (OData) をサポートするデータ サービスを作成するのには WCF データ サービスを使用する場合、開発中に次の基本的なタスクを実行する必要があります。

1. **データ モデルを定義する**

     WCF Data Services では、リレーショナル データベースから遅延バインディングデータ型まで、さまざまなデータ ソースのデータに基づいてデータ モデルを定義できるさまざまなデータ サービス プロバイダーがサポートされています。 詳細については、「[データ サービス プロバイダ](data-services-providers-wcf-data-services.md)」を参照してください。

2. **データ サービスを作成する**

     最も基本的なデータ サービスでは、 <xref:System.Data.Services.DataService%601> クラスを継承するクラスを `T` 型 (エンティティ コンテナーの名前空間修飾名) と一緒に公開します。 詳細については、「 [Defining WCF Data Services](defining-wcf-data-services.md)の開発と配置について説明します。

3. **データ サービスを構成する**

     既定では、WCF データ サービスは、エンティティ コンテナーによって公開されているリソースへのアクセスを無効にします。 この<xref:System.Data.Services.DataServiceConfiguration>インターフェイスを使用すると、リソースおよびサービス操作へのアクセスを構成したり、サポートされている OData のバージョンを指定したり、バッチ処理動作や単一の応答フィードで返すことができるエンティティの最大数など、サービス全体のその他の動作を定義したりできます。 詳細については、「データ[サービスの設定](configuring-the-data-service-wcf-data-services.md)」を参照してください。

この記事では、主に Visual Studio を使用してデータ サービスの開発と配置について説明します。 データを OData フィードとして公開するための WCF データ サービスによって提供される柔軟性については、「 [WCF データ サービスの定義](defining-wcf-data-services.md)」を参照してください。

### <a name="choose-a-development-web-server"></a>開発用 Web サーバーの選択

Visual Studio 2015 を使用して、WCF データ サービスをASP.NET アプリケーションとして開発するか、または Web サイトASP.NETする場合は、開発中にデータ サービスを実行する Web サーバーを選択できます。 次の Web サーバーは、ローカル コンピューター上でのデータ サービスのテストとデバッグを容易にするために、Visual Studio と統合されています。

1. **ローカル IIS サーバー**

     インターネット インフォメーション サービス (IIS) で実行されるASP.NET アプリケーションまたはASP.NET Web サイトであるデータ サービスを作成する場合は、ローカル コンピュータで IIS を使用してデータ サービスを開発し、テストすることをお勧めします。 IIS でデータ サービスを実行すると、デバッグ時における HTTP 要求のトレースが容易になります。 また、データ サービスに必要なファイルやデータベースなどのリソースにアクセスするために IIS で必要とされる権限を事前に確認することもできます。 IIS でデータ サービスを実行するには、IIS と Windows 通信財団 (WCF) の両方が正しくインストールおよび構成されていることを確認し、ファイル システムとデータベース内の IIS アカウントへのアクセスを許可します。 詳細については、「 [How to: Develop a WCF Data Service Running on IIS](how-to-develop-a-wcf-data-service-running-on-iis.md)」を参照してください。

    > [!NOTE]
    > 開発環境を有効にしてローカル IIS サーバーを構成するには、管理者権限を持つ Visual Studio を実行する必要があります。

2. **Visual Studio 開発サーバー**

     Visual Studio には、ASP.NET プロジェクトの既定の Web サーバーである、組み込みの Web サーバー、Visual Studio 開発サーバーが含まれています。 この Web サーバーは、開発中にローカル コンピューター上でASP.NET プロジェクトを実行するように設計されています。 [WCF データ サービスのクイック スタートでは](quickstart-wcf-data-services.md)、Visual Studio 開発サーバーで実行されるデータ サービスを作成する方法を示します。

     Visual Studio 開発サーバーを使用してデータ サービスを開発する場合は、次の制限に注意する必要があります。

    - このサーバーにはローカル コンピューター上でしかアクセスできません。

    - このサーバーは、HTTP メッセージの既定のポートであるポート 80 ではなく、 `localhost` および特定のポートでリッスンします。 詳細については、「 [ASP.NET Web プロジェクト用の Visual Studio の Web サーバー](https://docs.microsoft.com/previous-versions/aspnet/58wxa9w5(v=vs.120))」を参照してください。

    - このサーバーでは、現在のユーザー アカウントのコンテキストでデータ サービスが実行されます。 たとえば、管理者レベルのユーザーとして実行している場合、Visual Studio 開発サーバーで実行されているデータ サービスには、管理者レベルの特権が与えられます。 そのため、データ サービスは、IIS サーバーに配置されたときにはアクセスする権限を持たないリソースにも、アクセスできることになります。

    - このサーバーには、認証など、IIS の必要以上の機能は含まれていません。

    - このサーバーは、データ サービスから大きなバイナリ データにアクセスするときに、WCF データ サービス クライアントによって既定で送信されるチャンク HTTP ストリームを処理できません。 詳細については、「ストリーミング[プロバイダ」を](streaming-provider-wcf-data-services.md)参照してください。

    - このサーバーでは、キー値の WCF`.`データ サービスでこの文字がサポートされているにもかかわらず、URL 内のピリオド ( ) 文字の処理に問題があります。

    > [!TIP]
    > Visual Studio 開発サーバーを使用して開発中にデータ サービスをテストすることはできますが、IIS を実行している Web サーバーに配置した後で、再度テストする必要があります。

3. **Microsoft Azure 開発環境**

     Windows Azure ツールの Visual Studio には、Visual Studio で Windows Azure サービスを開発するためのツールの統合セットが含まれています。 これらのツールでは、Microsoft Azure に配置できるデータ サービスを開発し、配置前にローカル コンピューターでデータ サービスをテストすることができます。 Visual Studio を使用して Windows Azure プラットフォーム上で実行されるデータ サービスを開発する場合は、これらのツールを使用します。 ツールのインストールの詳細については[、「Visual Studio 2015 の Azure ツール](../../../azure/sdk/vs2015-install.md)」を参照してください。 Windows Azure で実行されるデータ サービスの開発の詳細については、「Windows Azure[での OData サービスのデプロイ](https://docs.microsoft.com/archive/blogs/astoriateam/deploying-an-odata-service-in-windows-azure)」の投稿を参照してください。

### <a name="development-tips"></a>開発のヒント

データ サービスを開発する場合は、次の点を考慮してください。

- ユーザーを認証する場合や、特定のユーザーのアクセスを制限する場合は、データ サービスのセキュリティ要件を決定します。 詳細については、「 [Securing WCF Data Services](securing-wcf-data-services.md)」を参照してください。

- HTTP 検査プログラムは、要求メッセージと応答メッセージの内容を検査できるようにすることで、データ・サービスをデバッグする際に役立ちます。 生のパケットを表示できるネットワーク パケット アナライザーを使用すると、データ サービスの HTTP 要求および HTTP 応答を検査できます。

- データ サービスをデバッグする場合は、通常の操作時よりも、データ サービスからエラーに関する詳細情報を取得する必要があります。 データ サービスから詳細なエラー情報を取得するには、 <xref:System.Data.Services.DataServiceConfiguration.UseVerboseErrors%2A> の <xref:System.Data.Services.DataServiceConfiguration> プロパティを `true` に設定し、データ サービス クラスの <xref:System.ServiceModel.Description.ServiceDebugBehavior.IncludeExceptionDetailInFaults%2A> 属性の <xref:System.ServiceModel.Description.ServiceDebugBehavior> プロパティを `true`に設定します。 詳細については、「 [WCF データ サービスのデバッグ](https://docs.microsoft.com/archive/blogs/phaniraj/debugging-wcf-data-services)後 」を参照してください。 また、HTTP メッセージング層で発生した例外を表示するために、WCF でトレースを有効にすることもできます。 詳細については、「 [Configuring Tracing](../../wcf/diagnostics/tracing/configuring-tracing.md)」を参照してください。

- データ サービスは、通常、ASP.NETアプリケーション プロジェクトとして開発されますが、Visual Studio で ASP.NET Web サイト プロジェクトとしてデータ サービスを作成することもできます。 2 種類のプロジェクトの違いについては、「 Visual Studio の[Web アプリケーション プロジェクトと Web サイト プロジェクト](https://docs.microsoft.com/previous-versions/aspnet/dd547590(v=vs.110))」を参照してください。

- Visual Studio の [**新しい項目の追加**] ダイアログ ボックスを使用してデータ サービスを作成すると、データ サービスは IIS のASP.NETによってホストされます。 ASP.NETと IIS はデータ サービスの既定のホストですが、他のホスト オプションもサポートされています。 詳細については、「[データ サービスのホスト](hosting-the-data-service-wcf-data-services.md)」を参照してください。

## <a name="deploy-wcf-data-services"></a>WCF データ サービスの展開

WCF Data Services では、データ サービスをホストするプロセスを柔軟に選択できます。 Visual Studio を使用して、データ サービスを次のプラットフォームに配置できます。

- **IIS でホストされる Web サーバー**

    データ サービスがASP.NET プロジェクトとして開発されると、標準のASP.NET配置プロセスを使用して IIS Web サーバーに展開できます。  Visual Studio には、配置するデータ サービスをホストするASP.NET プロジェクトの種類に応じて、ASP.NETに対して次の展開テクノロジが用意されています。

  - **ASP.NET Web アプリケーション用の配置テクノロジ**

    - [方法: Visual Studio で Web 配置パッケージを作成する](https://docs.microsoft.com/previous-versions/aspnet/dd465323(v=vs.110))

    - [方法: Visual Studio でワンクリック発行を使用して Web プロジェクトを配置する](https://docs.microsoft.com/previous-versions/aspnet/dd465337(v=vs.110))

  - **ASP.NET Web サイト用の配置テクノロジ**

    - [方法 : Web サイトのコピー ツールを使用して Web サイト ファイルをコピーする](https://docs.microsoft.com/previous-versions/aspnet/c95809c0(v=vs.100))

    - [方法 : Web サイトを発行する](https://docs.microsoft.com/previous-versions/aspnet/20yh9f1b(v=vs.100))

    - [チュートリアル: XCOPY を使用した ASP.NET Web アプリケーションの配置](https://docs.microsoft.com/previous-versions/aspnet/f735abw9(v=vs.100))

     ASP.NET アプリケーションの配置オプションの詳細については、「 Visual [Studio の Web 配置の概要」および「ASP.NET」](https://docs.microsoft.com/previous-versions/aspnet/dd394698(v=vs.110))を参照してください。

    > [!TIP]
    > データ サービスを IIS に配置する前に、IIS を実行している Web サーバーへの配置をテストしておく必要があります。 詳細については、「 [How to: Develop a WCF Data Service Running on IIS](how-to-develop-a-wcf-data-service-running-on-iis.md)」を参照してください。

- **Microsoft Azure**

     データ サービスを Windows Azure に展開するには、Visual Studio 用の Windows Azure ツールを使用します。 Windows Azure ツールの Visual Studio は[、マイクロソフト ダウンロード センター](https://go.microsoft.com/fwlink/?LinkID=201848)からダウンロードできます。 Windows Azure へのデータ サービスのデプロイの詳細については、「Windows Azure[での OData サービスのデプロイ](https://docs.microsoft.com/archive/blogs/astoriateam/deploying-an-odata-service-in-windows-azure)」の投稿を参照してください。

### <a name="deployment-considerations"></a>配置に関する注意事項

データ サービスを展開する場合は、次の点を考慮してください。

- Entity Framework プロバイダーを使用して SQL Server データベースにアクセスするデータ サービスを配置する場合、データ構造、データ、またはその両方をデータ サービスの配置に反映する必要があります。 Visual Studio では、対象データベースでこれを実行するスクリプト (.sql ファイル) を自動的に作成でき、これらのスクリプトは、ASP.NET アプリケーションの Web 配置パッケージに含めることができます。 詳細については、「[方法 : Web アプリケーション プロジェクトを使用してデータベースを配置する](https://docs.microsoft.com/previous-versions/dd465343(v=vs.100))」を参照してください。 ASP.NET Web サイトの場合は、Visual Studio の**データベース発行ウィザード**を使用して、これを行うことができます。 詳細については、「 [SQL データベースのパブリッシュ](https://docs.microsoft.com/previous-versions/aspnet/bb907585(v=vs.100))」を参照してください。

- WCF データ サービスには基本的な WCF 実装が含まれているため、Windows サーバー アプリケーション ファブリックを使用して、Windows サーバー上で実行されている IIS に展開されるデータ サービスを監視できます。 Windows Server アプリ ファブリックを使用してデータ サービスを監視する方法の詳細については[、「Windows Server アプリケーション ファブリックを使用した WCF データ サービスの追跡](https://docs.microsoft.com/archive/blogs/rjacobs/tracking-wcf-data-services-with-windows-server-appfabric)後」を参照してください。

## <a name="see-also"></a>関連項目

- [データ サービスのホスティング](hosting-the-data-service-wcf-data-services.md)
- [WCF Data Services のセキュリティ保護](securing-wcf-data-services.md)
- [WCF Data Services の定義](defining-wcf-data-services.md)
