---
title: インターネット インフォメーション サービスでホストされる WCF サービスの配置
ms.date: 03/30/2017
ms.assetid: 04ebd329-3fbd-44c3-b3ab-1de3517e27d7
ms.openlocfilehash: 67f6877546951bd92b235218f10f6ccc7011ef5c
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463855"
---
# <a name="deploying-an-internet-information-services-hosted-wcf-service"></a>インターネット インフォメーション サービスでホストされる WCF サービスの配置

インターネット インフォメーション サービス (IIS) でホストされている Windows 通信基盤 (WCF) サービスの開発と展開は、次のタスクで構成されます。

- IIS、ASP.NET、WCF、および WCF アクティベーション コンポーネントが正しくインストールされ、登録されていることを確認します。

- 新しい IIS アプリケーションを作成するか、既存の ASP.NET アプリケーションを再利用します。

- WCF サービスの .svc ファイルを作成します。

- IIS アプリケーションにサービス実装を展開します。

- WCF サービスを構成します。

IIS でホストされる WCF サービスの作成の詳細なチュートリアルについては、「[方法 : IIS で WCF サービスをホストする](how-to-host-a-wcf-service-in-iis.md)」を参照してください。

## <a name="ensure-that-iis-aspnet-and-wcf-are-correctly-installed-and-registered"></a>IIS、ASP.NET、および WCF が正しくインストールおよび登録されていることの確認

IIS でホストされる WCF サービスが正しく機能するには、WCF、IIS、およびASP.NETをインストールする必要があります。 WCF のインストール手順 (.NET Framework の一部として)、ASP.NET、および IIS は、オペレーティング システムによって異なります。 WCF および .NET Framework のインストールの詳細については、「 [.NET Framework の開発者向けインストール](../../install/guide-for-developers.md)」を参照してください。 Windows 10 に IIS をインストールするには、**コントロール パネル**の **[プログラムと機能] を**開き **、[Windows の機能を有効または無効にする**] を選択します。 [Windows**の機能]** で 、[**インターネット インフォメーション サービス**] を選択し **、[OK]** をクリックします。

![IIS が強調表示された Windows の機能](./media/windows-features-iis.png)

他のオペレーティング システムに IIS をインストールする手順については[、「Windows Vista および Windows 7 への IIS のインストール」](/iis/install/installing-iis-7/installing-iis-on-windows-vista-and-windows-7)と[「Windows Server 2012 R2 で IIS 8.5 をインストールする](/iis/install/installing-iis-85/installing-iis-85-on-windows-server-2012-r2)」を参照してください。

.NET Framework のインストール プロセスは、IIS が既にコンピューターに存在する場合は、自動的に IIS に WCF を登録します。 .NET Framework の後に IIS をインストールする場合は、WCF を IIS および ASP.NETに登録するために追加の手順が必要です。 使用しているオペレーティング システムに応じて、次のように実行します。

- Windows 7 および Windows Server 2003:[サービスモデル登録ツール (ServiceModelReg.exe)](../../../../docs/framework/wcf/servicemodelreg-exe.md)ツールを使用して、WCF を IIS に登録します。 このツールを使用するには[、Visual Studio の開発者コマンド プロンプト](../../tools/developer-command-prompt-for-vs.md)で **「ServiceModelReg.exe /i /x」** と入力します。

- Windows 7: 最後に、.NET Framework バージョン 4 以降を使用するようにASP.NETが構成されていることを確認する必要があります。 このオプションを使用してASPNET_Regiis ツールを`–i`実行します。 詳細については、「 [IIS 登録ツールASP.NET](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/k6h9cz8h(v=vs.90))」を参照してください。

## <a name="create-a-new-iis-application-or-reuse-an-existing-aspnet-application"></a>新しい IIS アプリケーションの作成、または既存の ASP.NET アプリケーションの再利用

IIS でホストされる WCF サービスは、IIS アプリケーション内に存在する必要があります。 WCF サービスを排他的にホストする新しい IIS アプリケーションを作成できます。 または、既に 2.0 コンテンツをホストしている既存のアプリケーションに WCF サービスASP.NET展開できます (.aspx ページや ASP.NET Web サービス (ASMX) など)。 これらのオプションの詳細については、「WCF[サービスとASP.NET](wcf-services-and-aspnet.md)の「wcf を並べて ASP.NET でホストする」と「wcf サービスをASP.NET互換モードでホストする」を参照してください。

IIS 6.0 以降のバージョンでは、分離オブジェクト指向プログラミング アプリケーションを定期的に再起動します。 既定値は 1740 分です。 サポートされている最大値は 71,582 分です。 この再起動は、無効にできます。 このプロパティの詳細については、「[定期再起動時間](https://docs.microsoft.com/previous-versions/iis/6.0-sdk/ms525914(v=vs.90))」を参照してください。

## <a name="create-an-svc-file-for-the-wcf-service"></a>WCF サービス用の .svc ファイルの作成

IIS でホストされる WCF サービスは、IIS アプリケーション内で特別なコンテンツ ファイル (.svc ファイル) として表されます。 これは、ASMX ページが、IIS アプリケーションの内部で .asmx ファイルとして表現されるのと同様です。 .svc ファイルには、WCF のホスト インフラストラクチャが受信メッセージに応答してホストされるサービスをアクティブにすることを可能にする WCF 固有の処理ディレクティブ ([\@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md)) が含まれています。 .svc ファイルの最も一般的な構文を次のステートメントに示します。

`<% @ServiceHost Service="MyNamespace.MyServiceImplementationTypeName" %>`

このクラスは[\@、ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md)ディレクティブと単一の`Service`属性で構成されます。 `Service` 属性の値は、サービス実装の共通言語ランタイム (CLR: Common Language Runtime) 型名です。 このディレクティブを使用することは、次のコードを使用してサービス ホストを作成することと基本的に同じです。

```csharp
new ServiceHost( typeof( MyNamespace.MyServiceImplementationTypeName ) );
```

サービスのベース アドレスの一覧を作成するなど、追加のホスト構成を実行することもできます。 カスタム <xref:System.ServiceModel.Activation.ServiceHostFactory> を使用して、このディレクティブをカスタム ホスト ソリューション用に拡張することもできます。 WCF サービスをホストする IIS アプリケーションは、インスタンスの作成と有効期間<xref:System.ServiceModel.ServiceHost>の管理を行いません。 マネージ WCF ホスティング インフラストラクチャは<xref:System.ServiceModel.ServiceHost>、.svc ファイルの最初の要求を受信したときに、必要なインスタンスを動的に作成します。 このインスタンスは、コードによって明示的に閉じられるか、アプリケーションがリサイクルされるときまで解放されません。

svc ファイルの構文の詳細については、 [ \@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md)を参照してください。

## <a name="deploy-the-service-implementation-to-the-iis-application"></a>IIS アプリケーションへのサービス実装の展開

IIS でホストされる WCF サービスは、ASP.NET 2.0 と同じ動的コンパイル モデルを使用します。 ASP.NETと同様に、IIS でホストされる WCF サービスの実装コードは、次のようにさまざまな場所に複数の方法で展開できます。

- グローバル アセンブリ キャッシュ (GAC: Global Assembly Cache) またはアプリケーションの \bin ディレクトリに配置される、プリコンパイルされた .dll ファイルとして展開します。 プリコンパイルされたバイナリは、新しいバージョンのクラス ライブラリが展開されるまで更新されません。

- アプリケーションの \App_Code ディレクトリに含まれるコンパイルされていないソース ファイルとして。 このディレクトリに配置されたソース ファイルは、アプリケーションの最初の要求を処理するときに動的に要求されます。 \App_Code ディレクトリ内のファイルを変更すると、次の要求を受け取ったときにアプリケーション全体がリサイクルされ、再コンパイルされます。

- コンパイルされていないコードとして、.svc ファイルに直接配置されます。 実装コードは、ServiceHost ディレクティブの後のサービスの .svc ファイル内\@にインラインで配置することもできます。 インライン コードを変更すると、次の要求を受け取ったときにアプリケーションがリサイクルされ、再コンパイルされます。

ASP.NET 2.0 コンパイル モデルの詳細については、「[コンパイルの概要ASP.NET」](https://docs.microsoft.com/previous-versions/aspnet/ms178466(v=vs.100))を参照してください。

## <a name="configure-the-wcf-service"></a>WCF サービスの構成

IIS でホストされる WCF サービスは、アプリケーションの Web.config ファイルに構成を格納します。 IIS でホストされるサービスは、IIS の外部でホストされる WCF サービスと同じ構成要素と構文を使用します。 ただし、次の制約は、IIS ホスト環境に固有です。

- IIS でホストされるサービスのベース アドレス。

- IIS の外部で WCF サービスをホストしているアプリケーションは、<xref:System.ServiceModel.ServiceHost>一連のベース アドレス URI をコンストラクターに渡すか、サービスの構成でホスト[\<>](../../../../docs/framework/configure-apps/file-schema/wcf/host.md)要素を提供することによって、ホストサービスのベース アドレスを制御できます。 IIS でホストされるサービスは、それぞれのベース アドレスを制御できません。IIS でホストされるサービスのベース アドレスは、その .svc ファイルのアドレスです。

### <a name="endpoint-addresses-for-iis-hosted-services"></a>IIS でホストされるサービスのエンドポイント アドレス

IIS でホストされるときのエンドポイント アドレスは、常にサービスを表す .svc ファイルのアドレスを基準にした相対アドレスと見なされます。 たとえば、WCF サービスのベース アドレスが`http://localhost/Application1/MyService.svc`次のエンドポイント構成を持つ場合。

```xml
<endpoint address="anotherEndpoint" />
```

これにより、 で`http://localhost/Application1/MyService.svc/anotherEndpoint`到達できるエンドポイントが提供されます。

同様に、相対アドレスとして空の文字列を使用するエンドポイント構成要素は、ベース アドレスである`http://localhost/Application1/MyService.svc`で到達可能なエンドポイントを提供します。

```xml
<endpoint address="" />
```

IIS でホストされるサービスのエンドポイントには、常に相対エンドポイント アドレスを使用する必要があります。 エンドポイント アドレス ( など) を完全修飾して`http://localhost/MyService.svc`指定すると、エンドポイント アドレスが、エンドポイントを公開するサービスをホストする IIS アプリケーションを指していない場合、サービスの展開でエラーが発生する可能性があります。 ホストされるサービスに相対エンドポイント アドレスを使用すると、このような競合が回避されます。

### <a name="available-transports"></a>利用可能なトランスポート

IIS 5.1 および IIS 6.0 でホストされる WCF サービスは、HTTP ベースの通信を使用するように制限されています。 これらの IIS プラットフォームでホストされるサービスで、非 HTTP バインドを使用するように構成すると、サービスをアクティブ化するときにエラーが発生します。 IIS 7.0 では、サポートされるトランスポートには、HTTP、Net.TCP、Net.Pipe、Net.MSMQ、および msmq.formatname が含まれます。

### <a name="http-transport-security"></a>HTTP トランスポート セキュリティ

IIS でホストされる WCF サービスは、サービスを含む IIS 仮想ディレクトリがこれらの設定をサポートしている限り、HTTP トランスポート セキュリティ (たとえば、基本認証、ダイジェスト認証、Windows 統合認証などの HTTPS 認証スキーム) を使用できます。 ホストされるエンドポイントのバインディングでの HTTP トランスポート セキュリティ設定は、そのエンドポイントを格納する IIS 仮想ディレクトリでのトランスポート セキュリティ設定と一致する必要があります。

たとえば、HTTP ダイジェスト認証を使用するように構成された WCF エンドポイントは、HTTP ダイジェスト認証を許可するように構成されている IIS 仮想ディレクトリに存在する必要があります。 IIS 設定と WCF エンドポイント設定の組み合わせが一致しない場合、サービスのアクティブ化中にエラーが発生します。

## <a name="see-also"></a>関連項目

- [インターネット インフォメーション サービスでのホスティング](hosting-in-internet-information-services.md)
- [インターネット インフォメーション サービス ホスティングのベスト プラクティス](internet-information-services-hosting-best-practices.md)
- [AppFabric のホスティング機能](https://docs.microsoft.com/previous-versions/appfabric/ee677189(v=azure.10))
