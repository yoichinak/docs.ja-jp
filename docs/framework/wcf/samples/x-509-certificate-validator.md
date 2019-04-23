---
title: X.509 証明書検証
ms.date: 03/30/2017
ms.assetid: 3b042379-02c4-4395-b927-e57c842fd3e0
ms.openlocfilehash: 88364aabf5df3a4f41d83613c0c4328b2d5979a0
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59772155"
---
# <a name="x509-certificate-validator"></a>X.509 証明書検証
このサンプルでは、カスタム X.509 証明書検証を実装する方法を示します。 これは、アプリケーションの要件に適した組み込みの X.509 証明書検証モードがない場合に便利です。 このサンプルでは、自己発行の証明書を許可するカスタム検証を備えたサービスを示します。 クライアントはこのような証明書を使用して、このサービスに認証されます。

 メモ:自己発行の証明書を構築できるすべてのユーザーとしてサービスによって使用されるカスタム検証は ChainTrust X509CertificateValidationMode によって提供される既定の動作よりも安全性が低いです。 この検証ロジックを製品版のコードで使用する前に、こうしたセキュリティへの影響について慎重に考慮する必要があります。

 このサンプルで示す処理の概要は次のとおりです。

-   クライアントは X.509 証明書を使用して認証される。

-   サーバーはクライアント資格情報をカスタム X509Certificate 検証と照合する。

-   サーバーがそのサーバーの X.509 証明書を使用して認証される。

 サービスは、そのサービスとの通信に使用する単一エンドポイントを公開します。エンドポイントは構成ファイル (App.config) で定義します。エンドポイントは、アドレス、バインディング、およびコントラクトがそれぞれ 1 つずつで構成されます。 標準的なバインディングが構成されている`wsHttpBinding`を既定では使用`WSSecurity`とクライアント証明書の認証。 サービス動作では、クライアントの X.509 証明書を検証するためのカスタム モード、および検証クラスの型を指定します。 さらに、serviceCertificate 要素を使用しているサーバー証明書も指定します。 サーバー証明書が同じ値を格納するが、`SubjectName`として、`findValue`で、 [ \<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)します。

```xml
  <system.serviceModel>
    <services>
      <service name="Microsoft.ServiceModel.Samples.CalculatorService"
               behaviorConfiguration="CalculatorServiceBehavior">
        <!-- use host/baseAddresses to configure base address -->
        <!-- provided by host -->
        <host>
          <baseAddresses>
            <add baseAddress =
                "http://localhost:8001/servicemodelsamples/service" />
          </baseAddresses>
        </host>
        <!-- use base address specified above, provide one endpoint -->
        <endpoint address="certificate"
               binding="wsHttpBinding"
               bindingConfiguration="Binding"
               contract="Microsoft.ServiceModel.Samples.ICalculator" />
      </service>
    </services>
    <bindings>
      <wsHttpBinding>
        <!-- X509 certificate binding -->
        <binding name="Binding">
          <security mode="Message">
            <message clientCredentialType="Certificate" />
          </security>
        </binding>
      </wsHttpBinding>
    </bindings>
    <behaviors>
      <serviceBehaviors>
        <behavior name="CalculatorServiceBehavior">
          <serviceDebug includeExceptionDetailInFaults ="true"/>
          <serviceCredentials>
            <!-- The serviceCredentials behavior allows one -->
            <!-- to specify authentication constraints on -->
            <!-- client certificates. -->
            <clientCertificate>
              <!-- Setting the certificateValidationMode to -->
              <!-- Custom means that if the custom -->
              <!-- X509CertificateValidator does NOT throw -->
              <!-- an exception, then the provided certificate -->
              <!-- will be trusted without performing any -->
              <!-- validation beyond that performed by the custom -->
              <!-- validator. The security implications of this -->
              <!-- setting should be carefully considered before -->
              <!-- using Custom in production code. -->
              <authentication
                 certificateValidationMode="Custom"
                 customCertificateValidatorType =
"Microsoft.ServiceModel.Samples.CustomX509CertificateValidator, service" />
            </clientCertificate>
            <!-- The serviceCredentials behavior allows one to -->
            <!-- define a service certificate. -->
            <!-- A service certificate is used by a client to -->
            <!-- authenticate the service and provide message -->
            <!-- protection. This configuration references the -->
            <!-- "localhost" certificate installed during the setup -->
            <!-- instructions. -->
            <serviceCertificate findValue="localhost"
                 storeLocation="LocalMachine"
                 storeName="My" x509FindType="FindBySubjectName" />
          </serviceCredentials>
        </behavior>
      </serviceBehaviors>
    </behaviors>
      </system.serviceModel>
```

 クライアント エンドポイント構成は、構成名、サービス エンドポイントの絶対アドレス、バインディング、およびコントラクトで構成されます。 クライアント バインディングは、適切なモードおよびメッセージ `clientCredentialType` で構成されます。

```xml
<system.serviceModel>
    <client>
      <!-- X509 certificate based endpoint -->
      <endpoint name="Certificate"
        address=
        "http://localhost:8001/servicemodelsamples/service/certificate"
                binding="wsHttpBinding"
                bindingConfiguration="Binding"
                behaviorConfiguration="ClientCertificateBehavior"
                contract="Microsoft.ServiceModel.Samples.ICalculator">
      </endpoint>
    </client>
    <bindings>
        <wsHttpBinding>
            <!-- X509 certificate binding -->
            <binding name="Binding">
                <security mode="Message">
                    <message clientCredentialType="Certificate" />
               </security>
            </binding>
       </wsHttpBinding>
    </bindings>
    <behaviors>
      <endpointBehaviors>
        <behavior name="ClientCertificateBehavior">
          <clientCredentials>
            <serviceCertificate>
              <!-- Setting the certificateValidationMode to -->
              <!-- PeerOrChainTrust means that if the certificate -->
              <!-- is in the user's Trusted People store, then it -->
              <!-- is trusted without performing a validation of -->
              <!-- the certificate's issuer chain. -->
              <!-- This setting is used here for convenience so -->
              <!-- that the sample can be run without having to -->
              <!-- have certificates issued by a certification -->
              <!-- authority (CA). This setting is less secure -->
              <!-- than the default, ChainTrust. The security -->
              <!-- implications of this setting should be -->
              <!-- carefully considered before using -->
              <!-- PeerOrChainTrust in production code.-->
              <authentication
                  certificateValidationMode="PeerOrChainTrust" />
            </serviceCertificate>
          </clientCredentials>
        </behavior>
      </endpointBehaviors>
    </behaviors>
  </system.serviceModel>
```

 クライアントの実装では、使用するクライアント証明書を設定します。

```csharp
// Create a client with Certificate endpoint configuration
CalculatorClient client = new CalculatorClient("Certificate");
try
{
    client.ClientCredentials.ClientCertificate.SetCertificate(StoreLocation.CurrentUser, StoreName.My, X509FindType.FindBySubjectName, "test1");

    // Call the Add service operation.
    double value1 = 100.00D;
    double value2 = 15.99D;
    double result = client.Add(value1, value2);
    Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result);

    // Call the Subtract service operation.
    value1 = 145.00D;
    value2 = 76.54D;
    result = client.Subtract(value1, value2);
    Console.WriteLine("Subtract({0},{1}) = {2}", value1, value2, result);

    // Call the Multiply service operation.
    value1 = 9.00D;
    value2 = 81.25D;
    result = client.Multiply(value1, value2);
    Console.WriteLine("Multiply({0},{1}) = {2}", value1, value2, result);

    // Call the Divide service operation.
    value1 = 22.00D;
    value2 = 7.00D;
    result = client.Divide(value1, value2);
    Console.WriteLine("Divide({0},{1}) = {2}", value1, value2, result);
    client.Close();
}
catch (TimeoutException e)
{
    Console.WriteLine("Call timed out : {0}", e.Message);
    client.Abort();
}
catch (CommunicationException e)
{
    Console.WriteLine("Call failed : {0}", e.Message);
    client.Abort();
}
catch (Exception e)
{
    Console.WriteLine("Call failed : {0}", e.Message);
    client.Abort();
}
```

 このサンプルでは、カスタム X509Certificate 検証を使用して証明書を検証します。 サンプルは、<xref:System.IdentityModel.Selectors.X509CertificateValidator> から派生するカスタム X509Certificate 検証を実装します。 詳細については、<xref:System.IdentityModel.Selectors.X509CertificateValidator> に関する説明を参照してください。 特定のカスタム検証を使用しているこのサンプルは、自己発行の任意の X.509 証明書を許可する Validate メソッドを実装しています。次のコードを参照してください。

```csharp
public class CustomX509CertificateValidator : X509CertificateValidator
{
  public override void Validate ( X509Certificate2 certificate )
  {
   // Only accept self-issued certificates
   if (certificate.Subject != certificate.Issuer)
     throw new Exception("Certificate is not self-issued");
   }
}
```

 サービス コードに検証を実装した場合、使用する検証インスタンスをサービス ホストに通知する必要があります。 これは次のコードで実行されます。

```csharp
serviceHost.Credentials.ClientCertificate.Authentication.CertificateValidationMode = X509CertificateValidationMode.Custom;
serviceHost.Credentials.ClientCertificate.Authentication.CustomCertificateValidator = new CustomX509CertificateValidator();
```

 または、構成で次のように指定することで、同じことを実現できます。

```xml
<behaviors>
    <serviceBehaviors>
     <behavior name="CalculatorServiceBehavior">
       ...
   <serviceCredentials>
    <!--The serviceCredentials behavior allows one to specify -->
    <!--authentication constraints on client certificates.-->
    <clientCertificate>
    <!-- Setting the certificateValidationMode to Custom means -->
    <!--that if the custom X509CertificateValidator does NOT -->
    <!--throw an exception, then the provided certificate will -->
    <!--be trusted without performing any validation beyond that -->
    <!--performed by the custom validator. The security -->
    <!--implications of this setting should be carefully -->
    <!--considered before using Custom in production code. -->
    <authentication certificateValidationMode="Custom"
       customCertificateValidatorType =
"Microsoft.ServiceModel.Samples. CustomX509CertificateValidator, service" />
   </clientCertificate>
   ...
  </behavior>
 </serviceBehaviors>
</behaviors>
```

 このサンプルを実行すると、操作要求および応答がクライアントのコンソール ウィンドウに表示されます。 クライアントはすべてのメソッドを問題なく呼び出すことができるようになります。 クライアントをシャットダウンするには、クライアント ウィンドウで Enter キーを押します。

## <a name="setup-batch-file"></a>セットアップ バッチ ファイル
 このサンプルに用意されている Setup.bat バッチ ファイルを使用すると、適切な証明書を使用してサーバーを構成し、サーバー証明書ベースのセキュリティを必要とする自己ホスト型アプリケーションを実行できるようになります。 このバッチ ファイルは、複数のコンピューターを使用する場合またはホストなしの場合に応じて変更する必要があります。

 次に、バッチ ファイルのセクションのうち、該当する構成で実行するために変更が必要となる部分を示します。

-   サーバー証明書の作成 :

     Setup.bat バッチ ファイルの次の行は、使用するサーバー証明書を作成します。 %SERVER_NAME% 変数はサーバー名を指定します。 この変数を変更して、使用するサーバー名を指定します。 既定値は、localhost です。

    ```bash
    echo ************
    echo Server cert setup starting
    echo %SERVER_NAME%
    echo ************
    echo making server cert
    echo ************
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe
    ```

-   サーバー証明書のクライアントの信頼された証明書ストアへのインストール。

     Setup.bat バッチ ファイルの次の行は、サーバー証明書をクライアントの信頼されたユーザーのストアにコピーします。 この手順が必要なのは、Makecert.exe によって生成される証明書がクライアント システムにより暗黙には信頼されないからです。 マイクロソフト発行の証明書など、クライアントの信頼されたルート証明書に基づいた証明書が既にある場合は、クライアント証明書ストアにサーバー証明書を配置するこの手順は不要です。

    ```bash
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople
    ```

-   クライアント証明書の作成 :

     Setup.bat バッチ ファイルの次の行は、使用するクライアント証明書を作成します。 %USER_NAME% 変数はクライアント名を指定します。 この値は "test1" に設定されます。クライアント コードによってこの名前が検索されるためです。 %USER_NAME% の値を変更した場合は、Client.cs ソース ファイル内の対応する値を変更して、クライアントを再構築する必要があります。

     証明書は、CurrentUser ストアの場所の My (Personal) ストアに保存されます。

    ```bash
    echo ************
    echo Client cert setup starting
    echo %USER_NAME%
    echo ************
    echo making client cert
    echo ************
    makecert.exe -sr CurrentUser -ss MY -a sha1 -n CN=%USER_NAME% -sky exchange -pe
    ```

-   クライアント証明書のサーバーの信頼された証明書ストアへのインストール。

     Setup.bat バッチ ファイルの次の行は、クライアント証明書を信頼されたユーザーのストアにコピーします。 この手順が必要なのは、Makecert.exe によって生成される証明書がサーバー システムにより暗黙には信頼されないからです。 マイクロソフト発行の証明書など、信頼されたルート証明書に基づく証明書が既にある場合は、サーバー証明書ストアにクライアント証明書を配置するこの手順は不要です。

    ```bash
    certmgr.exe -add -r CurrentUser -s My -c -n %USER_NAME% -r LocalMachine -s TrustedPeople
    ```

#### <a name="to-set-up-and-build-the-sample"></a>サンプルをセットアップしてビルドするには

1. ソリューションをビルドする手順については、 [Windows Communication Foundation サンプルのビルド](../../../../docs/framework/wcf/samples/building-the-samples.md)します。

2. サンプルを単一コンピューター構成で実行するか、複数コンピューター構成で実行するかに応じて、次の手順に従います。

#### <a name="to-run-the-sample-on-the-same-computer"></a>サンプルを同じコンピューターで実行するには

1. 管理者特権で開いた Visual Studio 2012 コマンド プロンプト内でサンプルのインストール フォルダーから Setup.bat を実行します。 これにより、サンプルの実行に必要なすべての証明書がインストールされます。

    > [!IMPORTANT]
    >  Setup.bat バッチ ファイルは、Visual Studio 2012 コマンド プロンプトから実行する設計されています。 Visual Studio 2012 のコマンド プロンプト ポイント内で設定して、Setup.bat スクリプトで必要な実行可能ファイルを格納するディレクトリ パス環境変数。  
  
2. Service.exe を service\bin で起動します。  
  
3. Client.exe を \client\bin で起動します。 クライアント アクティビティがクライアントのコンソール アプリケーションに表示されます。  
  
4. クライアントとサービスが通信できるようにされていない場合[WCF サンプルのトラブルシューティングのヒント](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90))します。  
  
#### <a name="to-run-the-sample-across-computers"></a>サンプルを複数のコンピューターで実行するには  
  
1. サービス コンピューターにディレクトリを作成します。  
  
2. サービス プログラム ファイルを \service\bin からサービス コンピューターの仮想ディレクトリにコピーします。 Setup.bat、Cleanup.bat、GetComputerName.vbs、ImportClientCert.bat の各ファイルもサービス コンピューターにコピーします。  
  
3. クライアント コンピューターにクライアント バイナリ用のディレクトリを作成します。  
  
4. クライアント プログラム ファイルを、クライアント コンピューターに作成したクライアント ディレクトリにコピーします。 Setup.bat、Cleanup.bat、ImportServiceCert.bat の各ファイルもクライアントにコピーします。  
  
5. サーバーで実行`setup.bat service`for Visual Studio 開発者コマンド プロンプトでは、管理者特権で開いた。 実行している`setup.bat`で、`service`引数サービス証明書を指定のエクスポートの完全修飾ドメイン名でサービス証明書を作成 Service.cer というファイルにします。  
  
6. 新しい証明書名を反映するように Service.exe.config を編集 (で、`findValue`属性、 [ \<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)) これは、コンピューターの完全修飾ドメイン名と同じです。 内のコンピューター名を変更しても、 \<service >/\<baseAddresses > 要素を localhost からサービス コンピューターの完全修飾名。  
  
7. Service.cer ファイルを、サービス ディレクトリからクライアント コンピューターのクライアント ディレクトリにコピーします。  
  
8. クライアントでは、次のように実行します。 `setup.bat client` for Visual Studio 開発者コマンド プロンプトでは、管理者特権で開いた。 `setup.bat`に `client` 引数を指定して実行すると、client.com というクライアント証明書が作成され、Client.cer というファイルにエクスポートされます。  
  
9. クライアント コンピューターの Client.exe.config ファイルで、エンドポイントのアドレス値をサービスの新しいアドレスに合わせます。 そのためには、localhost をサーバーの完全修飾ドメイン名に置き換えます。  
  
10. Client.cer ファイルを、クライアント ディレクトリからサーバーのサービス ディレクトリにコピーします。  
  
11. クライアントには、開発者コマンド プロンプトで ImportServiceCert.bat を実行、Visual Studio を管理者特権で開いたの。 これにより、サービス証明書が Service.cer ファイルから CurrentUser - TrustedPeople ストアにインポートされます。  
  
12. サーバー上には、開発者コマンド プロンプトで ImportClientCert.bat を実行、Visual Studio を管理者特権で開いたの。 これにより、クライアント証明書が Client.cer ファイルから LocalMachine - TrustedPeople ストアにインポートされます。  
  
13. サーバー コンピューターで、コマンド プロンプト ウィンドウから Service.exe を起動します。  
  
14. クライアント コンピューターで、コマンド プロンプト ウィンドウから Client.exe を起動します。 クライアントとサービスが通信できるようにされていない場合[WCF サンプルのトラブルシューティングのヒント](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90))します。  
  
#### <a name="to-clean-up-after-the-sample"></a>サンプルの実行後にクリーンアップするには  
  
1. サンプルの実行が終わったら、サンプル フォルダーにある Cleanup.bat を実行します。 これにより、証明書ストアからサーバー証明書とクライアント証明書が削除されます。  
  
> [!NOTE]
>  このサンプルを複数のコンピューターで実行している場合、このスクリプトはサービス証明書をクライアントから削除しません。 コンピューター間で証明書を使用する Windows Communication Foundation (WCF) サンプルを実行すると、必ず、CurrentUser - TrustedPeople ストアにインストールされているサービス証明書をオフにします。 これを行うには、次のコマンドを使用します。`certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` 例:`certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`します。
