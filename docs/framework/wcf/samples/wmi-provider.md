---
title: WMI プロバイダー
ms.date: 03/30/2017
ms.assetid: 462f0db3-f4a4-4a4b-ac26-41fc25c670a4
ms.openlocfilehash: 519f63f8dfc558a83a98ca44f74e926beb81c190
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59327231"
---
# <a name="wmi-provider"></a>WMI プロバイダー
このサンプルでは、WCF に組み込まれている Windows Management Instrumentation (WMI) プロバイダーを使用して、実行時に Windows Communication Foundation (WCF) サービスからデータを収集する方法を示します。 また、このサンプルでは、ユーザー定義の WMI オブジェクトをサービスに追加する方法も示します。 サンプルの WMI プロバイダーをアクティブ化、 [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md)からデータを収集する方法について説明し、`ICalculator`実行時にサービス。  
  
 WMI は、Web ベースのエンタープライズ管理 (WBEM) 標準をマイクロソフトが実装したものです。 WMI SDK の詳細については、次を参照してください。 [Windows Management Instrumentation](/windows/desktop/WmiSdk/wmi-start-page)します。 WBEM は、アプリケーションが Management Instrumentation を外部管理ツールに開示する業界標準の方法です。  
  
 WCF では、WMI プロバイダー、WBEM と互換性のあるインターフェイスを通して実行時にインストルメンテーションを公開するコンポーネントを実装します。 管理ツールは、実行時にインターフェイスを介してサービスに接続できます。 WCF では、アドレス、バインディング、動作、およびリスナーなどのサービスの属性を公開します。  
  
 組み込みの WMI プロバイダーは、アプリケーションの構成ファイルでアクティブにされます。 これを行う、`wmiProviderEnabled`の属性、 [\<診断 >](../../../../docs/framework/configure-apps/file-schema/wcf/diagnostics.md)で、 [ \<system.serviceModel >](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)セクションで、次の例に示すように構成:  
  
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
 WMI データには、複数の異なる方法でアクセスできます。 マイクロソフトでは、WMI Api を提供するスクリプト、Visual Basic アプリケーション、C++ アプリケーションでは、および[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)](https://docs.microsoft.com/windows/desktop/wmisdk/using-wmi)します。  
  
 このサンプルでは、2 つの Java スクリプトを使用します。1 つ目は、コンピューター上で実行されているサービスとその一部のプロパティを列挙するスクリプトで、2 つ目はユーザー定義の WMI データを表示するスクリプトです。 スクリプトは、WMI プロバイダーへの接続を開き、データを解析し、収集されたデータを表示します。  
  
 WCF サービスの実行中のインスタンスを作成するサンプルを開始します。 サービスの実行中は、コマンド プロンプトで次のコマンドを入力することによって、それぞれの Java スクリプトを実行してください。  
  
```  
cscript EnumerateServices.js  
```  
  
 スクリプトは、サービスに含まれているインストルメンテーションにアクセスし、次の出力を生成します。  
  
```  
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
  
```  
cscript EnumerateCustomObjects.js  
```  
  
 スクリプトは、サービスに含まれているユーザー定義のインストルメンテーションにアクセスし、次の出力を生成します。  
  
```  
1 WMIObject(s) found.  
|-PID:           30285bfd-9d66-4c4e-9be2-310499c5cef5  
|-InstanceId:    3839  
|-WMIInfo:       User Defined WMI Information.  
```  
  
 この出力は、コンピューター上で 1 つのサービスが実行中であることを示しています。 サービスは、`ICalculator` コントラクトを実装する 1 つのエンドポイントを公開します。 このエンドポイントによって実装されている動作とバインディングの設定は、メッセージ スタックの個々の要素の合計として表示されます。  
  
 WMI は、WCF インフラストラクチャの management instrumentation を公開するだけではありません。 独自のドメイン固有のデータ アイテムを、同じ機構を使用して公開できます。 WMI は、Web サービスの検査と制御のための統一された機構です。  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>サンプルをセットアップ、ビルド、および実行するには  
  
1. 実行済みであることを確認、 [Windows Communication Foundation サンプルの 1 回限りのセットアップ手順](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)します。  
  
2. ソリューションの C# 版または Visual Basic .NET 版をビルドするには、「 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)」の手順に従います。  
  
3. サービス スキーマを WMI に公開します。これを行うには、ホスト ディレクトリ内の service.dll ファイルに対して、InstallUtil.exe (既定の場所は "%WINDIR%\Microsoft.NET\Framework\v4.0.30319") を実行します。 この手順を実行する必要があるのは、service.dll ファイルを変更した場合のみです。
  
4. 1 つまたは複数コンピューター構成では、サンプルを実行する手順については、 [Windows Communication Foundation サンプルの実行](../../../../docs/framework/wcf/samples/running-the-samples.md)します。  
  
    > [!NOTE]
    >  ASP.NET をインストールした後に WCF をインストールした場合は、"%WINDIR%\ を実行する必要があります。Microsoft.Net\Framework\v3.0\Windows 通信 Foundation\servicemodelreg.exe"-r-x WMI オブジェクトをパブリッシュする ASPNET アカウントのアクセス許可を付与します。  
  
5. コマンド `cscript EnumerateServices.js` または `cscript EnumerateCustomObjects.js` を使用して、WMI を通じて示されるサンプルのデータを表示します。  
  
> [!IMPORTANT]
>  サンプルは、既にコンピューターにインストールされている場合があります。 続行する前に、次の (既定の) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合に移動[Windows Communication Foundation (WCF) と .NET Framework 4 向けの Windows Workflow Foundation (WF) サンプル](https://go.microsoft.com/fwlink/?LinkId=150780)すべて Windows Communication Foundation (WCF) をダウンロードして[!INCLUDE[wf1](../../../../includes/wf1-md.md)]サンプル。 このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\WMIProvider`  
  
## <a name="see-also"></a>関連項目

- [AppFabric の監視のサンプル](https://go.microsoft.com/fwlink/?LinkId=193959)
