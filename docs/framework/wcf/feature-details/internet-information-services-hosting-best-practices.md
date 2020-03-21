---
title: インターネット インフォメーション サービス ホスティングのベスト プラクティス
ms.date: 03/30/2017
ms.assetid: 0834768e-9665-46bf-86eb-d4b09ab91af5
ms.openlocfilehash: 3be9d4c81f891ad898099ba9041a09b16388b7e4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184715"
---
# <a name="internet-information-services-hosting-best-practices"></a>インターネット インフォメーション サービス ホスティングのベスト プラクティス
このトピックでは、WCF (WCF) サービスをホストするためのベスト プラクティスの概要を示します。  
  
## <a name="implementing-wcf-services-as-dlls"></a>WCF サービスの DLL としての実装  
 Web アプリケーションの \bin ディレクトリに展開される DLL として WCF サービスを実装すると、たとえばインターネット インフォメーション サービス (IIS) が展開されていない可能性のあるテスト環境で、Web アプリケーション モデルの外部でサービスを再利用できます。  
  
## <a name="service-hosts-in-iis-hosted-applications"></a>IIS でホストされるアプリケーションでのサービス ホスト  
 強制自己ホスト API を使用して、IIS ホスティング環境でネイティブにサポートされていないネットワーク トランスポートをリッスンする新しいサービス ホストを作成しないでください (たとえば、TCP 通信は IIS 6.0 ではネイティブにサポートされていないため、TCP サービスをホストする IIS 6.0 など)。 この方法はお勧めしません。 強制的に作成されたサービス ホストは、IIS ホスト環境内で認識されないからです。 重要な点は、IIS がホスト アプリケーション プールがアイドル状態であるかどうかを判断するときに、強制的に作成されたサービスによって実行される処理が IIS によって考慮されないことです。 この結果、強制的に作成されたサービス ホストを持つアプリケーションは、IIS ホスト プロセスを積極的に廃棄する IIS ホスト環境を持つことになります。  
  
## <a name="uris-and-iis-hosted-endpoints"></a>URI と IIS でホストされるエンドポイント  
 IIS でホストされるサービスのエンドポイントは、絶対アドレスではなく、相対 URI (Uniform Resource Identifier) を使用して構成する必要があります。 これにより、エンドポイント アドレスが、ホスト アプリケーションに属する URI アドレスのセット内に確実に含まれ、メッセージに基づくアクティベーションが正常に行われるようになります。  
  
## <a name="state-management-and-process-recycling"></a>状態管理とプロセスのリサイクル  
 IIS ホスト環境は、メモリにローカル状態を保持しないサービスに最適化されています。 IIS は、さまざまな外部および内部イベントに応答してホスト プロセスをリサイクルするため、メモリのみに格納される揮発性の状態はすべて失われます。 IIS でホストされるサービスは、それぞれの状態をプロセスの外部 (データベースなど)、またはアプリケーションのリサイクル イベントが発生した場合に簡単に再作成できるメモリ内キャッシュに格納する必要があります。  
  
> [!NOTE]
> WCF がメッセージ層の信頼性とセキュリティに使用するプロトコルは、揮発性のメモリ内状態を使用します。 WCF の信頼できるセッションとセキュリティ セッションは、アプリケーションのリサイクルにより予期せず終了する可能性があります。 これらのプロトコルを使用する IIS でホストされるアプリケーションは、アプリケーション層の状態を関連付ける WCF 提供のセッション キー以外のキー (たとえば、アプリケーション層構造やカスタムの関連付けヘッダー) に依存するか、または無効にする必要があります。ホストされたアプリケーションの IIS プロセスのリサイクル。  
  
## <a name="optimizing-performance-in-middle-tier-scenarios"></a>中間層シナリオでのパフォーマンスの最適化  
 *中間層シナリオ*で最適なパフォーマンスを得るために、着信メッセージに応答して他のサービスに呼び出すサービスは、WCF サービス クライアントをリモート サービスに一度インスタンス化し、複数の受信要求にまたがって再利用します。 WCF サービス クライアントのインスタンス化は、既存のクライアント インスタンスでサービス呼び出しを行う場合に比べて負荷の高い操作であり、中間層のシナリオでは、要求間でリモート クライアントをキャッシュすることで、パフォーマンスが明確に向上します。 WCF サービス クライアントはスレッド セーフであるため、複数のスレッド間でクライアントへのアクセスを同期する必要はありません。  
  
 また、中間層シナリオでは、`svcutil /a` オプションによって生成された非同期 API を使用してパフォーマンスを向上させます。 この`/a`オプションを使用すると[、ServiceModel メタデータ ユーティリティ ツール (Svcutil.exe) は](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)各サービス操作のメソッドを生成`BeginXXX/EndXXX`し、バックグラウンド スレッドでリモート サービスへの呼び出しを長時間実行できる可能性があります。  
  
## <a name="wcf-in-multi-homed-or-multi-named-scenarios"></a>マルチホーム シナリオまたはマルチネーム シナリオでの WCF  
 IIS Web ファーム内に WCF サービスを展開できます。 `http://www.contoso.com` `http://www.contoso.com` `http://machine1.internal.contoso.com` `http://machine2.internal.contoso.com` この展開シナリオは WCF で完全にサポートされていますが、サービスのメタデータ (Web サービス記述言語) に正しい (外部) ホスト名を表示するには、WCF サービスをホストする IIS Web サイトの特別な構成が必要です。  
  
 WCF が生成するサービス メタデータに正しいホスト名が表示されるようにするには、明示的なホスト名を使用するように WCF サービスをホストする IIS Web サイトの既定の ID を構成します。 たとえば、`www.contoso.com`ファーム内に存在するコンピューターでは、HTTP 用に *:80:www.contoso.com、HTTPS\*の場合は :443:www.contoso.com の IIS サイト バインドを使用する必要があります。  
  
 Microsoft 管理コンソール (MMC) スナップインを使用して、IIS Web サイト バインディングを構成できます。  
  
## <a name="application-pools-running-in-different-user-contexts-overwrite-assemblies-from-other-accounts-in-the-temporary-folder"></a>異なるユーザー コンテキストで実行されるアプリケーション プールが、一時フォルダー内の他のアカウントのアセンブリを上書きする  
 異なるユーザー コンテキストで実行されているアプリケーション プールが、一時ASP.NET ファイル フォルダー内の他のアカウントのアセンブリを上書きできないようにするには、異なるアプリケーションに対して異なる ID と一時フォルダーを使用します。 たとえば、/Application1 と /Application2 という 2 つの仮想アプリケーションがある場合は、2 つの異なる ID を使用して、A と B の 2 つのアプリケーション プールを作成できます。 アプリケーション プール A は、一方のユーザー ID (user1) の下で、アプリケーション プール B は、もう一方のユーザー ID (user2) の下で実行でき、/Application1 が A を、/Application2 が B を使用するように構成します。  
  
 Web.config では、>を使用して一時\<system.web/compilation/@tempFolderフォルダーを構成できます。 /アプリケーション1の場合は"c:\tempForUser1"、アプリケーション2では"c:\tempForUser2"にすることができます。 これらのフォルダーに対応する書き込みアクセス許可を 2 つの ID に与えます。  
  
 これで、user2 は、(c:\tempForUser1 の下にある) /Application2 のコード生成フォルダーを変更できなくなります。  
  
## <a name="enabling-asynchronous-processing"></a>非同期処理の有効化  
 既定では、IIS 6.0 以前のバージョンでホストされている WCF サービスに送信されるメッセージは同期的に処理されます。 ASP.NET自身のスレッド (ASP.NET ワーカー スレッド) で WCF を呼び出し、WCF は別のスレッドを使用して要求を処理します。 WCF は、その処理が完了するまで ASP.NET のワーカー スレッドに保持されます。 このため、要求は同期的に処理されます。 要求の処理は、要求の処理に必要なスレッドの数を減らすため ASP.NET、非同期的にスケーラビリティを向上させることができます。 IIS 6.0 を実行しているコンピュータでは、*サービス拒否*(DOS) 攻撃に対してサーバーを開く受信要求を抑制する方法がないため、非同期動作の使用はお勧めできません。 IIS 7.0 以降では、同時要求スロットルが導入されています`[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\ASP.NET\2.0.50727.0]"MaxConcurrentRequestsPerCpu`。 この新しいスロットルにより、非同期処理を安全に使用することができます。  IIS 7.0 の既定では、非同期のハンドラーとモジュールが登録されます。 この機能が無効になっている場合は、アプリケーションの Web.config ファイルで要求の非同期処理を手動で有効にすることができます。 使用する設定は、`aspNetCompatibilityEnabled` 設定によって異なります。 `aspNetCompatibilityEnabled` を `false` に設定している場合は、次の構成スニペットに示すように、`System.ServiceModel.Activation.ServiceHttpModule` を構成します。  
  
```xml  
<system.serviceModel>  
    <serviceHostingEnvironment aspNetCompatibilityEnabled="false" />
  </system.serviceModel>  
  <system.webServer>  
    <modules>  
      <remove name="ServiceModel"/>  
      <add name="ServiceModel"
           preCondition="integratedMode,runtimeVersionv2.0"
           type="System.ServiceModel.Activation.ServiceHttpModule, System.ServiceModel,Version=3.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"/>  
    </modules>  
    </system.webServer>  
```  
  
 `aspNetCompatibilityEnabled` を `true` に設定している場合は、次の構成スニペットに示すように、`System.ServiceModel.Activation.ServiceHttpHandlerFactory` を構成します。  
  
```xml  
<system.serviceModel>  
    <serviceHostingEnvironment aspNetCompatibilityEnabled="true" />
  </system.serviceModel>  
  <system.webServer>  
    <handlers>  
          <clear/>  
          <add name="TestAsyncHttpHandler"
               path="*.svc"
               verb="*"
               type="System.ServiceModel.Activation.ServiceHttpHandlerFactory, System.ServiceModel, Version=3.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"
               />  
    </handlers>
  </system.webServer>  
```  
  
## <a name="see-also"></a>関連項目

- [サービス ホスト サンプル](../samples/hosting.md)
- [AppFabric のホスティング機能](https://docs.microsoft.com/previous-versions/appfabric/ee677189(v=azure.10))
