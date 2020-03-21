---
title: PII セキュリティ ロックダウン
ms.date: 03/30/2017
ms.assetid: c44fb338-9527-4dd0-8607-b8787d15acb4
ms.openlocfilehash: ad4f4a024b04a028b815faedded58713e001cab0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79144267"
---
# <a name="pii-security-lockdown"></a>PII セキュリティ ロックダウン
このサンプルでは、次の方法で Windows 通信基盤 (WCF) サービスのいくつかのセキュリティ関連機能を制御する方法を示します。  
  
- サービスの構成ファイル内の機密情報を暗号化します。  
  
- 入れ子になったサービス サブディレクトリが設定をオーバーライドできないように、構成ファイル内の要素をロックします。  
  
- トレースおよびメッセージ ログで、個人を特定できる情報 (PII) のログ記録を制御します。  
  
> [!IMPORTANT]
> サンプルは、既にコンピューターにインストールされている場合があります。 続行する前に、次の (既定の) ディレクトリを確認してください。  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> このディレクトリが存在しない場合は[、.NET Framework 4 の Windows コミュニケーション ファウンデーション (WCF) および Windows ワークフローファウンデーション (WF) サンプル](https://www.microsoft.com/download/details.aspx?id=21459)に移動して、すべての Windows 通信基盤 (WCF) とサンプルを[!INCLUDE[wf1](../../../../includes/wf1-md.md)]ダウンロードします。 このサンプルは、次のディレクトリに格納されます。  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\SecurityLockdown`  
  
## <a name="discussion"></a>ディスカッション  
 これらの各機能を単独または組み合わせて使用することにより、サービスのさまざまなセキュリティを制御できます。 これは、WCF サービスをセキュリティで保護するための決定的なガイドではありません。  
  
 .NET Framework の構成ファイルには、データベースに接続するための接続文字列などの機密情報を格納できます。 共有の Web ホストのシナリオでは、この情報をサービスの構成ファイル内で暗号化して、構成ファイル内に含まれるデータを偶発的に表示されないようにすることが望ましい場合があります。 .NET Framework 2.0 以降のバージョンでは、Windows データ保護アプリケーション プログラミング インターフェイス (DPAPI) または RSA 暗号化プロバイダを使用して、構成ファイルの一部を暗号化できます。 DPAPI または RSA を使用して aspnet_regiis.exe を実行すると、構成ファイルの選択部分を暗号化できます。  
  
 Web ホストのシナリオでは、他のサービスのサブディレクトリにサービスを設定できます。 構成値を決定する既定の意味的方法によると、入れ子になったディレクトリ内の構成ファイルで親ディレクトリの構成値をオーバーライドできます。 特定の状況では、さまざまな理由でこれが望ましくない場合があります。 WCF サービス構成では、構成値のロックがサポートされるため、入れ子になった構成は、オーバーライドされた構成値を使用して入れ子になったサービスを実行するときに例外を生成します。  
  
 このサンプルでは、トレースおよびメッセージ ログによる、ユーザー名やパスワードなどの個人を特定できる既知の情報 (PII) のログ記録を制御する方法を示します。 既定では、既知の PII のログ記録は無効です。ただし特定の状況では、PII のログ記録はアプリケーションをデバック処理する際に重要になる場合があります。 このサンプルは、[作業の開始に](../../../../docs/framework/wcf/samples/getting-started-sample.md)基づいています。 さらに、このサンプルではトレースとメッセージ ログを使用します。 詳細については、「[トレースとメッセージ ログ](../../../../docs/framework/wcf/samples/tracing-and-message-logging.md)のサンプル」を参照してください。  
  
## <a name="encrypting-configuration-file-elements"></a>構成ファイルの要素の暗号化  
 共有 Web ホストの環境をセキュリティ保護するには、機密情報が含まれる可能性のあるデータベース接続文字列など、特定の構成要素を暗号化することが望ましい場合があります。 構成要素は、.NET Framework フォルダーにあるaspnet_regiis.exe ツールを使用して暗号化できます。  
  
#### <a name="to-encrypt-the-values-in-the-appsettings-section-in-webconfig-for-the-sample"></a>サンプルの Web.config で appSettings セクションの値を暗号化するには  
  
1. [実行の開始] を使用してコマンド プロンプト>開きます。 を入力`cmd`して **[OK]** をクリックします。  
  
2. コマンド「`cd %WINDIR%\Microsoft.NET\Framework\v4.0.20728`」を実行して、現在の .NET Framework ディレクトリに移動します。  
  
3. コマンド「`aspnet_regiis -pe "appSettings" -app "/servicemodelsamples" -prov "DataProtectionConfigurationProvider"`」を実行して、Web.config フォルダーの appSettings 構成設定を暗号化します。  
  
 構成ファイルの暗号化セクションの詳細については、ASP.NET構成の DPAPI の方法 ([セキュリティで保護されたASP.NET アプリケーションの構築: 認証、承認、およびセキュリティで保護された通信](https://docs.microsoft.com/previous-versions/msp-n-p/ff649248(v=pandp.10))) と、ASP.NET構成の RSA の方法 ([[方法: RSA を使用して ASP.NET 2.0 の構成セクションを暗号化する](https://docs.microsoft.com/previous-versions/msp-n-p/ff650304(v=pandp.10))] ) を参照してください。  
  
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
  
 コンピュータ全体の設定は、Machine.config `enableLoggingKnownPii` `true`の`false``machineSettings`要素で or を設定することによって制御されます。たとえば、次の例では、アプリケーションが PII のログを有効にできます。  
  
```xml  
<configuration>  
    <system.serviceModel>  
        <machineSettings enableLoggingKnownPii="true" />  
    </system.serviceModel>  
</configuration>  
```  
  
> [!NOTE]
> Machine.config ファイルの既定の場所は %WINDIR%\Microsoft.NET\Framework\v2.0.50727\CONFIG です。  
  
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
> System.Diagnostics は、構成ファイルの最初に表示されているソース以外の、すべてのソースのすべての属性を無視します。 `logKnownPii` 属性を構成ファイル内の 2 番目のソースに追加しても、結果は変わりません。  
  
> [!IMPORTANT]
> このサンプルを実行するには、Machine.config を手動で変更する必要があります。Machine.config を正しくない値または構文に変更すると、すべての .NET Framework アプリケーションの実行が妨げになる可能性があるため、注意が必要です。  
  
 また、DPAPI や RSA を使用して構成ファイルの要素を暗号化することもできます。 詳細については、次のリンクを参照してください。  
  
- [セキュリティで保護されたASP.NETアプリケーションの構築: 認証、承認、およびセキュリティで保護された通信](https://docs.microsoft.com/previous-versions/msp-n-p/ff649248(v=pandp.10))  
  
- [方法 : RSA を使用して ASP.NET 2.0 で構成セクションを暗号化する](https://docs.microsoft.com/previous-versions/msp-n-p/ff650304(v=pandp.10))  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>サンプルを設定、ビルド、および実行するには  
  
1. [Windows コミュニケーションファウンデーション サンプルのワンタイム セットアップ手順を](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)実行したことを確認します。  
  
2. Machine.config を編集して `enableLoggingKnownPii` 属性を `true` に設定し、必要に応じて親ノードを追加します。  
  
3. ソリューションの C# 版または Visual Basic .NET 版をビルドするには、「 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)」の手順に従います。  
  
4. 単一または複数のコンピューターにまたがる構成でサンプルを実行するには、「 [Windows コミュニケーション ファウンデーション サンプルの実行](../../../../docs/framework/wcf/samples/running-the-samples.md)」の手順に従います。  
  
#### <a name="to-clean-up-the-sample"></a>サンプルをクリーンアップするには  
  
1. Machine.config を編集して `enableLoggingKnownPii` 属性を `false` に設定します。  
  
## <a name="see-also"></a>関連項目

- [AppFabric の監視のサンプル](https://docs.microsoft.com/previous-versions/appfabric/ff383407(v=azure.10))
