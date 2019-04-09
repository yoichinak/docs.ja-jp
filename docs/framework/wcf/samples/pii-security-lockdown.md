---
title: PII セキュリティ ロックダウン
ms.date: 03/30/2017
ms.assetid: c44fb338-9527-4dd0-8607-b8787d15acb4
ms.openlocfilehash: 38ca91ab969624ab2128e3cfad1d8151cb8d1f88
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59122058"
---
# <a name="pii-security-lockdown"></a>PII セキュリティ ロックダウン
このサンプルでは、によって、Windows Communication Foundation (WCF) サービスの複数のセキュリティ関連機能を制御する方法を示しています。  
  
-   サービスの構成ファイル内の機密情報を暗号化します。  
  
-   入れ子になったサービス サブディレクトリが設定をオーバーライドできないように、構成ファイル内の要素をロックします。  
  
-   トレースおよびメッセージ ログで、個人を特定できる情報 (PII) のログ記録を制御します。  
  
> [!IMPORTANT]
>  サンプルは、既にコンピューターにインストールされている場合があります。 続行する前に、次の (既定の) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合に移動[Windows Communication Foundation (WCF) と .NET Framework 4 向けの Windows Workflow Foundation (WF) サンプル](https://go.microsoft.com/fwlink/?LinkId=150780)すべて Windows Communication Foundation (WCF) をダウンロードして[!INCLUDE[wf1](../../../../includes/wf1-md.md)]サンプル。 このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\SecurityLockdown`  
  
## <a name="discussion"></a>説明  
 これらの各機能を単独または組み合わせて使用することにより、サービスのさまざまなセキュリティを制御できます。 WCF サービスのセキュリティ保護に説明するものではありません。  
  
 .NET Framework の構成ファイルには、データベースに接続するための接続文字列などの機密情報を格納できます。 共有の Web ホストのシナリオでは、この情報をサービスの構成ファイル内で暗号化して、構成ファイル内に含まれるデータを偶発的に表示されないようにすることが望ましい場合があります。 .NET Framework 2.0 以降のバージョンでは、Windows データ保護アプリケーション プログラミング インターフェイス (DPAPI) または RSA 暗号化プロバイダを使用して、構成ファイルの一部を暗号化できます。 DPAPI または RSA を使用して aspnet_regiis.exe を実行すると、構成ファイルの選択部分を暗号化できます。  
  
 Web ホストのシナリオでは、他のサービスのサブディレクトリにサービスを設定できます。 構成値を決定する既定の意味的方法によると、入れ子になったディレクトリ内の構成ファイルで親ディレクトリの構成値をオーバーライドできます。 特定の状況では、さまざまな理由でこれが望ましくない場合があります。 WCF サービスの構成のサポートを使用して入れ子になったサービスの実行時に例外を生成する構成を入れ子になったために、構成値のロックには、構成値がオーバーライドされます。  
  
 このサンプルでは、トレースおよびメッセージ ログによる、ユーザー名やパスワードなどの個人を特定できる既知の情報 (PII) のログ記録を制御する方法を示します。 既定では、既知の PII のログ記録は無効です。ただし特定の状況では、PII のログ記録はアプリケーションをデバック処理する際に重要になる場合があります。 このサンプルがに基づいて、 [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md)します。 さらに、このサンプルではトレースとメッセージ ログを使用します。 詳細については、次を参照してください。、[トレースとメッセージ ログ](../../../../docs/framework/wcf/samples/tracing-and-message-logging.md)サンプル。  
  
## <a name="encrypting-configuration-file-elements"></a>構成ファイルの要素の暗号化  
 共有 Web ホストの環境をセキュリティ保護するには、機密情報が含まれる可能性のあるデータベース接続文字列など、特定の構成要素を暗号化することが望ましい場合があります。 構成要素は、.NET Framework フォルダー (%WINDIR%\Microsoft.NET\Framework\v4.0.20728 など) にある aspnet_regiis.exe ツールを使用して暗号化できます。  
  
#### <a name="to-encrypt-the-values-in-the-appsettings-section-in-webconfig-for-the-sample"></a>サンプルの Web.config で appSettings セクションの値を暗号化するには  
  
1.  -> 実行開始を使用してコマンド プロンプトのオープンしています. 入力`cmd` をクリック**OK**します。  
  
2.  コマンド「`cd %WINDIR%\Microsoft.NET\Framework\v4.0.20728`」を実行して、現在の .NET Framework ディレクトリに移動します。  
  
3.  コマンド「`aspnet_regiis -pe "appSettings" -app "/servicemodelsamples" -prov "DataProtectionConfigurationProvider"`」を実行して、Web.config フォルダーの appSettings 構成設定を暗号化します。  
  
 構成ファイルのセクションを暗号化する方法についての詳細については、ASP.NET 構成では DPAPI でに関する記事を参照して見つかんだことができます ([Building Secure ASP.NET Applications:認証、承認、およびセキュリティ保護された通信](https://go.microsoft.com/fwlink/?LinkId=95137)) と ASP.NET の構成で RSA の使い方 ([How To:ASP.NET 2.0 の構成セクションを暗号化する RSA を使用して](https://go.microsoft.com/fwlink/?LinkId=95138))。  
  
## <a name="locking-configuration-file-elements"></a>構成ファイルの要素のロック  
 Web ホストのシナリオでは、サービスのサブディレクトリにサービスを設定できます。 こうした状況で、サブディレクトリ内のサービスの構成値を計算するには、Machine.config 内の値を調べ、続いて親ディレクトリの任意の Web.config ファイルとマージしてディレクトリ ツリーの下層に移動します。そして最後に、サービスが含まれるディレクトリ内の Web.config ファイルをマージします。 ほとんどの構成要素での既定の動作は、サブディレクトリ内の構成ファイルが、親ディレクトリに設定されている値をオーバーライドできるようにすることです。 特定の状況では、サブディレクトリ内の構成ファイルが、親ディレクトリの構成に設定されている値をオーバーライドしないようにするのが望ましい場合があります。  
  
 .NET Framework では、構成ファイルの要素をロックして、ロックされた構成要素をオーバーライドする構成が実行時例外をスローするように設定できます。  
  
 構成要素をロックするには、構成ファイルのノードに対して `lockItem` 属性を指定します。たとえば、入れ子になった構成ファイル内の電卓サービスが動作を変更できないように構成ファイルの CalculatorServiceBehavior ノードをロックするには、次の構成を使用できます。  
  
```xml  
<configuration>  
   <system.serviceModel>  
      <behaviors>   
          <serviceBehaviors>   
             <behavior name="CalculatorServiceBehavior" lockItem="true">   
               <serviceMetadata httpGetEnabled="True"/>   
               <serviceDebug includeExceptionDetailInFaults="False" />   
             </behavior>   
          </serviceBehaviors>   
       </behaviors>   
    </system.serviceModel>  
</configuration>  
```  
  
 構成要素はより詳細な単位でロックできます。 要素の一覧は、サブ要素のコレクション内にある一連の要素をロックするための `lockElements` に対する値として指定できます。 属性の一覧は、要素内にある一連の属性をロックするための `lockAttributes` に対する値として指定できます。 要素または属性のコレクション全体をロックすることもできます。ただし、ノードで `lockAllElementsExcept` 属性または `lockAllAttributesExcept` 属性が指定されている一覧は除きます。  
  
## <a name="pii-logging-configuration"></a>PII ログの構成  
 PII のログ記録は 2 つのスイッチで制御されます。1 つは Machine.config にあるコンピューター全体の設定で、コンピューターの管理者がこれを使用することにより、PII のログ記録を許可または拒否できます。もう 1 つはアプリケーション設定で、アプリケーションの管理者がこれを使用することにより、Web.config または App.config ファイル内の各ソースで PII のログ記録の有効/無効を切り替えることができます。  
  
 コンピューター全体の設定は、Machine.config の `enableLoggingKnownPii` 要素で、`true` を `false` または `machineSettings` に設定することによって制御されます。たとえば、次の例ではアプリケーションで PII のログ記録が有効になります。  
  
```xml  
<configuration>  
    <system.serviceModel>  
        <machineSettings enableLoggingKnownPii="true" />  
    </system.serviceModel>  
</configuration>  
```  
  
> [!NOTE]
>  Machine.config ファイルの既定の場所は %WINDIR%\Microsoft.NET\Framework\v2.0.50727\CONFIG です。  
  
 `enableLoggingKnownPii` 属性が Machine.config にない場合、PII のログ記録は許可されません。  
  
 アプリケーションで PII のログ記録を有効にするには、Web.config または App.config ファイルで、ソース要素の `logKnownPii` 属性を `true` または `false` に設定します。 たとえば次の例では、メッセージ ログとトレース ログの両方に対して PII のログ記録が有効になります。  
  
```xml  
<configuration>  
    <system.diagnostics>  
        <sources>  
            <source name="System.ServiceModel.MessageLogging" logKnownPii="true">  
                <listeners>   
                ...   
                </listeners>  
            </source>  
            <source name="System.ServiceModel" switchValue="Verbose, ActivityTracing">  
            <listeners>  
        ...   
            </listeners>  
            </source>  
        </sources>  
    </system.diagnostics>  
</configuration>  
```  
  
 `logKnownPii` 属性が指定されていない場合は、PII はログ記録されません。  
  
 PII がログ記録されるのは、`enableLoggingKnownPii` が `true` に設定されていると共に、`logKnownPii` が `true` に設定されている場合だけです。  
  
> [!NOTE]
>  System.Diagnostics は、構成ファイルの最初に表示されているソース以外の、すべてのソースのすべての属性を無視します。 `logKnownPii` 属性を構成ファイル内の 2 番目のソースに追加しても、結果は変わりません。  
  
> [!IMPORTANT]
>  このサンプルを実行する際には、Machine.config を手動で変更します。Machine.config を変更する際は注意してください。値または構文が正しくない場合、すべての .NET Framework アプリケーションが実行できなくなる可能性があります。  
  
 また、DPAPI や RSA を使用して構成ファイルの要素を暗号化することもできます。 詳細については、次のリンクを参照してください。  
  
-   [セキュリティで保護された ASP.NET アプリケーションの構築:認証、承認、およびセキュリティで保護された通信](https://go.microsoft.com/fwlink/?LinkId=95137)  
  
-   [方法: ASP.NET 2.0 の構成セクションを暗号化する RSA を使用して](https://go.microsoft.com/fwlink/?LinkId=95138)  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>サンプルを設定、ビルド、および実行するには  
  
1.  実行したことを確認、 [Windows Communication Foundation サンプルの 1 回限りのセットアップ手順](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)します。  
  
2.  Machine.config を編集して `enableLoggingKnownPii` 属性を `true` に設定し、必要に応じて親ノードを追加します。  
  
3.  ソリューションの C# 版または Visual Basic .NET 版をビルドするには、「 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)」の手順に従います。  
  
4.  1 つまたは複数コンピューター構成では、サンプルを実行する手順については、 [Windows Communication Foundation サンプルの実行](../../../../docs/framework/wcf/samples/running-the-samples.md)します。  
  
#### <a name="to-clean-up-the-sample"></a>サンプルをクリーンアップするには  
  
1.  Machine.config を編集して `enableLoggingKnownPii` 属性を `false` に設定します。  
  
## <a name="see-also"></a>関連項目

- [AppFabric の監視のサンプル](https://go.microsoft.com/fwlink/?LinkId=193959)
