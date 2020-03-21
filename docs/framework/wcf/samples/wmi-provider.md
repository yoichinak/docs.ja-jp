---
title: WMI プロバイダー
ms.date: 03/30/2017
ms.assetid: 462f0db3-f4a4-4a4b-ac26-41fc25c670a4
ms.openlocfilehash: 04fdbb7efcae6fdbb78f467352e6106ac5218799
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183201"
---
# <a name="wmi-provider"></a>WMI プロバイダー
このサンプルでは、WCF に組み込まれている Windows 管理インストルメンテーション (WMI) プロバイダーを使用して、実行時に Windows 通信基盤 (WCF) サービスからデータを収集する方法を示します。 また、このサンプルでは、ユーザー定義の WMI オブジェクトをサービスに追加する方法も示します。 このサンプルでは、[作業の開始](../../../../docs/framework/wcf/samples/getting-started-sample.md)に対応する WMI プロバイダーをアクティブにし、実行時`ICalculator`にサービスからデータを収集する方法を示します。  
  
 WMI は、Web ベースのエンタープライズ管理 (WBEM) 標準をマイクロソフトが実装したものです。 WMI SDK の詳細については、「 [Windows 管理インストルメンテーション](/windows/desktop/WmiSdk/wmi-start-page)」を参照してください。 WBEM は、アプリケーションが Management Instrumentation を外部管理ツールに開示する業界標準の方法です。  
  
 WCF は、Wmi プロバイダーを実装します、 WBEM 互換インターフェイスを使用して実行時にインストルメンテーションを公開するコンポーネントです。 管理ツールは、実行時にインターフェイスを介してサービスに接続できます。 WCF は、アドレス、バインディング、動作、リスナーなどのサービスの属性を公開します。  
  
 組み込みの WMI プロバイダーは、アプリケーションの構成ファイルでアクティブにされます。 これは、次のサンプル`wmiProviderEnabled`構成に示すように[\<、system.serviceModel>](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)セクションの[\<診断>](../../../../docs/framework/configure-apps/file-schema/wcf/diagnostics.md)の属性を使用して行われます。  
  
```xml  
<system.serviceModel>  
    ...  
    <diagnostics wmiProviderEnabled="true" />  
    ...  
</system.serviceModel>  
```  
  
 この構成エントリには、WMI インターフェイスが開示されます。 管理アプリケーションはこのインターフェイスを通して接続し、アプリケーションの Management Instrumentation にアクセスできるようになります。  
  
## <a name="custom-wmi-object"></a>カスタム WMI オブジェクト  
 WMI オブジェクトをサービスに追加すると、組み込みの WMI プロバイダーの情報と共にユーザー定義の情報を開示できます。 これは、Installutil.exe アプリケーションを使用してサービスのスキーマを WMI に公開することによって実現されます。 これを行うための手順および詳細情報は、このトピックの最後のセットアップ手順で示します。  
  
## <a name="accessing-wmi-information"></a>WMI 情報へのアクセス  

WMI データには、複数の異なる方法でアクセスできます。 マイクロソフトでは、スクリプト、Visual Basic アプリケーション、C++ アプリケーション、および .NET Framework 用の WMI API を提供しています。 詳細については、「 [WMI の使用](/windows/desktop/wmisdk/using-wmi)」を参照してください。
  
 このサンプルでは、2 つの Java スクリプトを使用します。1 つ目は、コンピューター上で実行されているサービスとその一部のプロパティを列挙するスクリプトで、2 つ目はユーザー定義の WMI データを表示するスクリプトです。 スクリプトは、WMI プロバイダーへの接続を開き、データを解析し、収集されたデータを表示します。  
  
 サンプルを起動して、WCF サービスの実行中のインスタンスを作成します。 サービスの実行中は、コマンド プロンプトで次のコマンドを入力することによって、それぞれの Java スクリプトを実行してください。  
  
```console  
cscript EnumerateServices.js  
```  
  
 スクリプトは、サービスに含まれているインストルメンテーションにアクセスし、次の出力を生成します。  
  
```console  
Microsoft (R) Windows Script Host Version 5.6  
Copyright © Microsoft Corporation 1996-2001. All rights reserved.  
  
1 service(s) found.  
|-PID:           5776  
|-DistinguishedName:  CalculatorService@http://localhost/ServiceModelSamples/service.svc  
|-Endpoints:     1 endpoints  
  |-CalculatorService.ICalculator@http://localhost/ServiceModelSamples/service.svc  
    |-Address:                        http://localhost/ServiceModelSamples/service.svc  
    |-CounterInstanceName:  
    |-AddressHeaders:                 0  
    |-ContractType:                   Contract.Name='ICalculator'  
    |-BindingElements:                4 bindings  
      |-BindingElements[0]  
        |-Type:                       TransactionFlowBindingElement  
      |-BindingElements[1]  
        |-Type:                       SymmetricSecurityBindingElement  
      |-BindingElements[2]  
        |-Type:                       TextMessageEncodingBindingElement  
        |-MaxReadPoolSize:            64  
        |-MaxWritePoolSize:           16  
      |-BindingElements[3]  
        |-Type:                       HttpTransportBindingElement  
        |-ManualAddressing:           false  
        |-MaxBufferSize:              65536  
        |-AllowCookies:               false  
        |-AuthenticationScheme:       Anonymous  
        |-BypassProxyOnLocal:         false  
        |-HostNameComparisonMode:     StrongWildcard  
        |-ProxyAddress:               null  
        |-ProxyAuthenticationScheme:  Anonymous  
        |-Realm:  
        |-TransferMode:               Buffered  
        |-UseDefaultWebProxy:         true  
|-Behaviors:     5 behaviors  
      |-Behavior[0]  
      |-Type:                       ServiceBehaviorAttribute  
        |-AddressFilterMode:               Exact  
        |-AutomaticSessionShutdown:        true  
        |-ConcurrencyMode:                 Single  
        |-IncludeExceptionDetailInFaults:  false  
        |-InstanceContextMode:             PerSession  
        |-TransactionIsolationLevel:       Unspecified  
        |-TransactionTimeout:              null  
        |-ValidateMustUnderstand:          true  
      |-Behavior[1]  
      |-Type:                       AspNetCompatibilityRequirementsAttribute  
      |-Behavior[2]  
      |-Type:                       ServiceDebugBehavior  
      |-Behavior[3]  
      |-Type:                       ServiceAuthorizationBehavior  
      |-Behavior[4]  
      |-Type:                       Behavior  
```  
  
 次に、2 つ目の Java スクリプトを実行して、ユーザー定義の WMI データを表示します。  
  
```console  
cscript EnumerateCustomObjects.js  
```  
  
 スクリプトは、サービスに含まれているユーザー定義のインストルメンテーションにアクセスし、次の出力を生成します。  
  
```console
1 WMIObject(s) found.  
|-PID:           30285bfd-9d66-4c4e-9be2-310499c5cef5  
|-InstanceId:    3839  
|-WMIInfo:       User Defined WMI Information.  
```  
  
 この出力は、コンピューター上で 1 つのサービスが実行中であることを示しています。 サービスは、`ICalculator` コントラクトを実装する 1 つのエンドポイントを公開します。 このエンドポイントによって実装されている動作とバインディングの設定は、メッセージ スタックの個々の要素の合計として表示されます。  
  
 WMI は、WCF インフラストラクチャの管理インストルメンテーションを公開することに限定されません。 独自のドメイン固有のデータ アイテムを、同じ機構を使用して公開できます。 WMI は、Web サービスの検査と制御のための統一された機構です。  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>サンプルをセットアップ、ビルド、および実行するには  
  
1. [Windows コミュニケーション ファウンデーション サンプルの 1 回限りのセットアップ手順を](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)実行したことを確認します。  
  
2. ソリューションの C# 版または Visual Basic .NET 版をビルドするには、「 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)」の手順に従います。  
  
3. サービス スキーマを WMI に公開します。これを行うには、ホスト ディレクトリ内の service.dll ファイルに対して、InstallUtil.exe (既定の場所は "%WINDIR%\Microsoft.NET\Framework\v4.0.30319") を実行します。 この手順を実行する必要があるのは、service.dll ファイルを変更した場合のみです。
  
4. 単一または複数のコンピューターにまたがる構成でサンプルを実行するには、「 [Windows コミュニケーション ファウンデーション サンプルの実行](../../../../docs/framework/wcf/samples/running-the-samples.md)」の手順に従います。  
  
    > [!NOTE]
    > ASP.NETのインストール後に WCF をインストールした場合は、"%WINDIR%\ を実行する必要があります。WMI オブジェクトを公開するアクセス許可を ASPNET アカウントに与えるアクセス許可を ASPNET アカウントに与える場合は、マイクロソフト.Net\Framework\v3.0\Windows コミュニケーション ファウンデーション\servicemodelreg.exe " -r -x。  
  
5. コマンド `cscript EnumerateServices.js` または `cscript EnumerateCustomObjects.js` を使用して、WMI を通じて示されるサンプルのデータを表示します。  
  
> [!IMPORTANT]
> サンプルは、既にコンピューターにインストールされている場合があります。 続行する前に、次の (既定の) ディレクトリを確認してください。  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> このディレクトリが存在しない場合は[、.NET Framework 4 の Windows コミュニケーション ファウンデーション (WCF) および Windows ワークフローファウンデーション (WF) サンプル](https://www.microsoft.com/download/details.aspx?id=21459)に移動して、すべての Windows 通信基盤 (WCF) とサンプルを[!INCLUDE[wf1](../../../../includes/wf1-md.md)]ダウンロードします。 このサンプルは、次のディレクトリに格納されます。  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\WMIProvider`  
  
## <a name="see-also"></a>関連項目

- [AppFabric の監視のサンプル](https://docs.microsoft.com/previous-versions/appfabric/ff383407(v=azure.10))
