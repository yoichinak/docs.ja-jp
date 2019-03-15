---
title: WCF の単純化機能
ms.date: 03/30/2017
ms.assetid: 4535a511-6064-4da0-b361-80262a891663
ms.openlocfilehash: 54255e07df5a46cc975ffd4db5c18dc828a1de44
ms.sourcegitcommit: 69bf8b719d4c289eec7b45336d0b933dd7927841
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/14/2019
ms.locfileid: "57845277"
---
# <a name="wcf-simplification-features"></a>WCF の単純化機能

ここでは、WCF アプリケーションの作成を容易にする新機能について説明します。

## <a name="simplified-generated-configuration-files"></a>生成された構成ファイルの簡略化

Visual Studio でサービス参照を追加したり、SvcUtil.exe ツールを使用したりすると、クライアント構成ファイルが生成されます。 以前のバージョンの WCF では、このような構成ファイルには、各バインド プロパティの値が既定値であっても、その値が含まれていました。 WCF 4.5 では、生成された構成ファイルには、既定値以外の値に設定されているバインド プロパティのみが含まれます。

WCF 3.0 で生成された構成ファイルの例を次に示します。

```xml
<?xml version="1.0" encoding="utf-8"?>
<configuration>
    <system.serviceModel>
        <bindings>
            <basicHttpBinding>
                <binding name="BasicHttpBinding_IService1" closeTimeout="00:01:00"
                    openTimeout="00:01:00" receiveTimeout="00:10:00" sendTimeout="00:01:00"
                    allowCookies="false" bypassProxyOnLocal="false"
                    hostNameComparisonMode="StrongWildcard" maxBufferSize="65536"
                    maxBufferPoolSize="524288" maxReceivedMessageSize="65536"
                    messageEncoding="Text" textEncoding="utf-8" transferMode="Buffered"
                    useDefaultWebProxy="true">
                    <readerQuotas maxDepth="32" maxStringContentLength="8192"
                        maxArrayLength="16384" maxBytesPerRead="4096"
                        maxNameTableCharCount="16384" />
                    <security mode="None">
                        <transport clientCredentialType="None" proxyCredentialType="None"
                            realm="" />
                        <message clientCredentialType="UserName" algorithmSuite="Default" />
                    </security>
                </binding>
            </basicHttpBinding>
        </bindings>
        <client>
            <endpoint address="http://localhost:36906/Service1.svc" binding="basicHttpBinding"
                bindingConfiguration="BasicHttpBinding_IService1" contract="IService1"
                name="BasicHttpBinding_IService1" />
        </client>
    </system.serviceModel>
</configuration>
```

WCF 4.5 で生成された同じ構成ファイルの例を次に示します。

```xml
<?xml version="1.0" encoding="utf-8"?>
<configuration>
    <system.serviceModel>
        <bindings>
            <basicHttpBinding>
                <binding name="BasicHttpBinding_IService1" />
            </basicHttpBinding>
        </bindings>
        <client>
            <endpoint address="http://localhost:36906/Service1.svc" binding="basicHttpBinding"
                bindingConfiguration="BasicHttpBinding_IService1" contract="IService1"
                name="BasicHttpBinding_IService1" />
        </client>
    </system.serviceModel>
</configuration>
```

## <a name="contract-first-development"></a>コントラクト優先の開発

WCF では、コントラクト優先の開発がサポートされるようになりました。 Svcutil.exe ツールには、WSDL ドキュメントからサービスとデータ コントラクトを生成することができるようにする/serviceContract スイッチがいます。

## <a name="add-service-reference-from-a-portable-subset-project"></a>ポータブル サブセット プロジェクトからのサービス参照の追加

ポータブル サブセット プロジェクトでは、1 つのソース ツリーを維持し、複数の .NET 実装 (デスクトップ、Silverlight、Windows Phone、および XBOX) をサポートしながら、システムを構築するための .NET アセンブリ プログラマが有効にします。 ポータブル サブセット プロジェクトは、任意の .NET 実装で使用できる .NET framework アセンブリである .NET ポータブル ライブラリのみを参照します。 開発者から見れば、他の WCF クライアント アプリケーション内でサービス参照を追加するのと同じです。 詳細については、次を参照してください。[ポータブル サブセット プロジェクトでサービス参照の追加](../../../docs/framework/wcf/add-service-reference-in-a-portable-subset-project.md)します。

## <a name="aspnet-compatibility-mode-default-changed"></a>ASP.NET 互換性モードの既定値の変更

WCF には ASP.NET 互換性モードが用意されています。これにより、開発者は WCF サービスを作成する際に ASP.NET HTTP パイプラインの機能へのフル アクセスが付与されます。 このモードを使用するに設定する必要があります、`aspNetCompatibilityEnabled`属性を true に、 [ \<serviceHostingEnvironment >](../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md) web.config のセクション。さらに、この appDomain 内のサービスでは、`RequirementsMode` の <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> プロパティを <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Allowed> または <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Required> に設定しておく必要があります。 既定で<xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute>に設定されているようになりました<xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Allowed>と、既定の WCF サービス アプリケーション テンプレートのセット、`aspNetCompatibilityEnabled`属性を`true`します。 詳細については、次を参照してください。 [Windows Communication Foundation 4.5 の新](../../../docs/framework/wcf/whats-new.md)と[WCF サービスと ASP.NET](../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md)します。

## <a name="streaming-improvements"></a>ストリーミングの強化

- 非同期ストリーミングに対する新しいサポートが WCF に追加されました。 非同期ストリーミングを有効にするには、エンドポイントの <xref:System.ServiceModel.Description.DispatcherSynchronizationBehavior> 動作をサービス ホストに追加し、その <xref:System.ServiceModel.Description.DispatcherSynchronizationBehavior.AsynchronousSendEnabled%2A> プロパティを `true` に設定します。 これにより、読み取りに時間のかかる複数のクライアントに対してサービスがストリーム メッセージを送信するときにスケーラビリティが得られます。 WCF では、クライアントごとに 1 つのスレッドがブロックされなくなり、別のクライアントにサービスを提供するためにスレッドを解放します。

- サービスが IIS でホストされるときのメッセージのバッファー処理に関する制限がなくなりました。 以前のバージョンの WCF では、ストリーム メッセージ転送を使用する IIS でホストされるサービスに対するメッセージを受信すると、ASP.NET はメッセージ全体を WCF に送信する前にバッファー処理しました。 これにより、メモリの大量消費が発生しました。 このバッファー処理は .NET 4.5 で削除されました。現在は、IIS でホストされる WCF サービスが、メッセージ全体が受信される前に着信ストリームの処理を開始できるため、実際のストリーミングが可能になります。 これにより、WCF は、メッセージにすぐに応答できるようになり、パフォーマンスは向上します。 さらに、着信要求に対する ASP.NET のサイズ制限である `maxRequestLength` の値を指定する必要がなくなりました。 このプロパティを設定した場合、このプロパティは無視されます。 詳細については`maxRequestLength`を参照してください[ \<httpRuntime > 構成要素](https://go.microsoft.com/fwlink/?LinkId=223344)します。 詳細については、maxAllowedContentLength の構成を参照してください必要があります[Requestlimits](https://go.microsoft.com/fwlink/?LinkId=225908)します。

## <a name="new-transport-default-values"></a>トランスポートの新しい既定値

次の表は、変更された設定と追加情報の場所を示しています。

|プロパティ|オン|新しい既定値|説明|
|--------------|--------|-----------------|----------------------|
|channelInitializationTimeout|<xref:System.ServiceModel.NetTcpBinding>|30 秒|このプロパティは、どのくらいの時間の TCP 接続は .NET Framing プロトコルを使用して自身を認証する実行することができますを決定します。 クライアントは、サーバーが認証を実行するための十分な情報を得る前に初期データを送信する必要があります。 このタイムアウトは意図的に ReceiveTimeout (10 分) よりも小さい値に設定されます。これにより、悪意のある認証されていないクライアントは、長時間にわたってサーバーへの接続を保持できません。 既定値は 30 秒です。 詳細については <xref:System.ServiceModel.Channels.ConnectionOrientedTransportBindingElement.ChannelInitializationTimeout%2A>|
|listenBacklog|<xref:System.ServiceModel.NetTcpBinding>|16 * プロセッサの数|このソケット レベルのプロパティは、キューに入れられる "受入保留中の" 要求の数を示します。 リッスン バックログ キューがいっぱいになると、新しいソケット要求は拒否されます。 詳細については <xref:System.ServiceModel.NetTcpBinding.ListenBacklog%2A>|
|maxPendingAccepts|ConnectionOrientedTransportBindingElement<br /><br /> SMSvcHost.exe|2 * トランスポート用のプロセッサの数<br /><br /> 4 \* SMSvcHost.exe のプロセッサの数|このプロパティは、サーバーがリスナーで待機できるチャネルの数を制限します。 MaxPendingAccepts が小さすぎると、待機しているすべてのチャネルが接続のサービスを開始する間隔が小さくなりますが、新しいチャネルがリッスンを開始できなくなります。 接続がこの間に到着した場合、サーバー上でこの接続を待機しているものがないため、接続は失敗します。 このプロパティは、<xref:System.ServiceModel.Channels.ConnectionOrientedTransportBindingElement.MaxPendingConnections%2A> プロパティを大きな値に設定することで構成できます。 詳細については、次を参照してください<xref:System.ServiceModel.Channels.ConnectionOrientedTransportBindingElement.MaxPendingAccepts%2A>と[Net.TCP ポート共有サービスを構成する。](../../../docs/framework/wcf/feature-details/configuring-the-net-tcp-port-sharing-service.md)|
|maxPendingConnections|ConnectionOrientedTransportBindingElement|12 * プロセッサの数|このプロパティは、トランスポートが受け入れたにもかかわらず ServiceModel ディスパッチャーによって取得されていない接続の数を制御します。 この値を設定するには、バインドの `MaxConnections` を使用するか、またはバインド要素の `maxOutboundConnectionsPerEndpoint` を使用してください。 詳細については <xref:System.ServiceModel.Channels.ConnectionOrientedTransportBindingElement.MaxPendingConnections%2A>|
|receiveTimeout|SMSvcHost.exe|30 秒|このプロパティは、TCP フレーム データを読み取り、基になる接続からディスパッチする接続を実行するためのタイムアウトを指定します。 これは、SMSvcHost.exe サービスで受信接続からの前文データの読み取り操作を行う時間に制限を設定するために使用されます。 詳細については、次を参照してください。 [Net.TCP ポート共有サービスを構成する](../../../docs/framework/wcf/feature-details/configuring-the-net-tcp-port-sharing-service.md)します。|

> [!NOTE]
> これらの新しい既定値は、.NET Framework 4.5 がインストールされているコンピューターに WCF サービスを配置する場合のみ使用されます。 .NET Framework 4.0 がインストールされているコンピューターに同じサービスを配置すると、.NET Framework 4.0 の既定値が使用されます。 このような場合は、これらの設定を明示的に構成することをお勧めします。

## <a name="xmldictionaryreaderquotas"></a>XmlDictionaryReaderQuotas

<xref:System.Xml.XmlDictionaryReaderQuotas> には、メッセージの作成中にエンコーダーで使用されるメモリの量を制限する XML ディクショナリ リーダーの構成可能なクォータ値が格納されます。 これらのクォータは構成可能ですが、開発者がこのクォータを明示的に設定する必要性を低くするために既定値が変更されました。 `MaxReceivedMessageSize` クォータは変更されていないため、メモリ使用量を引き続き制限して、<xref:System.Xml.XmlDictionaryReaderQuotas> の複雑さを処理する必要性を回避できます。 次の表に、クォータ、クォータの新しい既定値、および各クォータの用途の簡単な説明を示します。

|クォータの名前|既定値|説明|
|----------------|-------------------|-----------------|
|<xref:System.Xml.XmlDictionaryReaderQuotas.MaxArrayLength%2A>|Int32.MaxValue|許される最大配列長を取得または設定します。 このクォータは、XML リーダーが返すプリミティブ配列 (バイト配列など) の最大サイズを制限します。 このクォータは、XML リーダー自体のメモリ消費は制限しませんが、このリーダーを使用するコンポーネントのメモリ消費を制限します。 たとえば、 <xref:System.Runtime.Serialization.DataContractSerializer> が <xref:System.Xml.XmlDictionaryReaderQuotas.MaxArrayLength%2A>でセキュリティ保護されたリーダーを使用するときは、このクォータを超えるバイト配列を逆シリアル化することはありません。|
|<xref:System.Xml.XmlDictionaryReaderQuotas.MaxBytesPerRead%2A>|Int32.MaxValue|1 回の読み取りで返すことができる最大バイト数を取得または設定します。 このクォータは、要素の開始タグとその属性を読み取るときに、1 回の読み取り操作で読み取るバイト数を制限します  (ストリーミングを使用しない場合、要素名自体がクォータに照らし合わせてカウントされることはありません)。 XML 属性が多すぎると、属性名は一意かどうかを確認する必要があるため、処理時間が大幅に増加する可能性があります。 <xref:System.Xml.XmlDictionaryReaderQuotas.MaxBytesPerRead%2A> によってこの脅威を軽減できます。|
|<xref:System.Xml.XmlDictionaryReaderQuotas.MaxDepth%2A>|128 ノードの深さ|このクォータは、XML 要素の入れ子の深さの最大値を制限します。 <xref:System.Xml.XmlDictionaryReaderQuotas.MaxDepth%2A> は <xref:System.Xml.XmlDictionaryReaderQuotas.MaxBytesPerRead%2A>と相互に関係しています。リーダーは常に、現在の要素とそのすべての先祖に関するデータをメモリ内に維持します。このため、リーダーのメモリ消費の最大値は、この 2 つの設定値の積に比例します。 深く入れ子になったオブジェクト グラフを逆シリアル化する場合、デシリアライザーはスタック全体にアクセスし、回復不可能な <xref:System.StackOverflowException>をスローするしかありません。 <xref:System.Runtime.Serialization.DataContractSerializer> の場合も <xref:System.Xml.Serialization.XmlSerializer>の場合も、XML の入れ子構造とオブジェクトの入れ子構造との間に直接的な相関関係が存在します。 この脅威を軽減するには、<xref:System.Xml.XmlDictionaryReaderQuotas.MaxDepth%2A> を使用します。|
|<xref:System.Xml.XmlDictionaryReaderQuotas.MaxNameTableCharCount%2A>|Int32.MaxValue|このクォータは、nametable で使用できる最大文字数を制限します。 nametable には、XML ドキュメントを処理するときに出現する特定の文字列 (名前空間やプレフィックスなど) が入っています。 これらの文字列はメモリ内でバッファー化されるので、ストリーミングが予想されるときは、このクォータを使用して過度のバッファーを防止します。|
|<xref:System.Xml.XmlDictionaryReaderQuotas.MaxStringContentLength%2A>|Int32.MaxValue|このクォータは、XML リーダーが返す文字列の最大サイズを制限します。 このクォータは、XML リーダー自体のメモリ消費は制限しませんが、このリーダーを使用するコンポーネントのメモリ消費を制限します。 たとえば、 <xref:System.Runtime.Serialization.DataContractSerializer> が <xref:System.Xml.XmlDictionaryReaderQuotas.MaxStringContentLength%2A>でセキュリティ保護されたリーダーを使用するときは、このクォータを超える文字列を逆シリアル化することはありません。|

> [!IMPORTANT]
> を使用して XML の安全な」を参照してください[Security Considerations for Data](../../../docs/framework/wcf/feature-details/security-considerations-for-data.md)詳細については、データを保護します。

> [!NOTE]
> これらの新しい既定値は、.NET Framework 4.5 がインストールされているコンピューターに WCF サービスを配置する場合のみ使用されます。 .NET Framework 4.0 がインストールされているコンピューターに同じサービスを配置すると、.NET Framework 4.0 の既定値が使用されます。 このような場合は、これらの設定を明示的に構成することをお勧めします。

## <a name="wcf-configuration-validation"></a>WCF 構成検証

Visual Studio 内でのビルド プロセスの一環として、WCF 構成ファイルが検証されるようになりました。 検証に失敗すると、Visual Studio では検証エラーと警告の一覧が表示されます。

## <a name="xml-editor-tooltips"></a>XML エディターのツールヒント

新規および既存の WCF サービスの開発者がサービスを構成するうえで役立つよう、Visual Studio の XML エディターでは、サービス構成ファイルに含まれる各構成要素とそのプロパティにツールヒントが表示されるようになりました。

## <a name="basichttpbinding-improvements"></a>BasicHttpBinding の機能強化

1. 単一の WCF エンドポイントでさまざまな認証モードに応答できます。

2. WCF サービスのセキュリティ設定を IIS で制御できます。
