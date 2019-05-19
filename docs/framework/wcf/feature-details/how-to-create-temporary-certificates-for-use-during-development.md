---
title: '方法: 開発中に使用する一時的な証明書を作成する'
ms.date: 03/30/2017
helpviewer_keywords:
- certificates [WCF], creating temporary certificates
- temporary certificates [WCF]
ms.assetid: bc5f6637-5513-4d27-99bb-51aad7741e4a
ms.openlocfilehash: 4223ee8c8790ad4d0ae2275b347c4f974eeb4158
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/19/2019
ms.locfileid: "65877966"
---
# <a name="how-to-create-temporary-certificates-for-use-during-development"></a>方法: 開発中に使用する一時的な証明書を作成する

セキュリティで保護されたサービスまたは Windows Communication Foundation (WCF) を使用してクライアントを開発する場合は、資格情報として使用する X.509 証明書を指定する必要があります。 証明書は通常、単独ではなく、いくつもの証明書が信頼チェーンとしてつながった形で存在しており、その最上位に位置するルート証明機関の証明書は、各コンピューターの [信頼されたルート証明機関] の証明書ストアに格納されています。 証明書を調べて順に信頼チェーンをたどっていくと、たとえば所属する会社や事業部門が運営する、ルート証明機関に到達します。 開発時にこの過程をエミュレートするためには、セキュリティ要件を満たす 2 種類の証明書を作る必要があります。 1 つは自己署名証明書で、[信頼されたルート証明機関] の証明書ストアに配置します。もう 1 つは、先の自己署名証明書を使って署名を施した証明書で、[ローカル コンピューター] の [個人] ストア、または [現在のユーザー] の [個人] ストアに配置します。 このトピックでは、Powershell を使用してこれら 2 つの証明書を作成する手順について説明します[New-selfsignedcertificate)](/powershell/module/pkiclient/new-selfsignedcertificate)コマンドレット。

> [!IMPORTANT]
> New-selfsignedcertificate コマンドレットによって生成される証明書は、テスト目的でのみ提供されます。 実際にサービスやクライアントを業務に使用する際には、証明機関から取得した、適切な証明書が必要です。 組織内の Windows Server 証明書サーバーからか、またはサード パーティ製これでした。
>
> 既定で、 [New-selfsignedcertificate](/powershell/module/pkiclient/new-selfsignedcertificate)コマンドレットは自己署名証明書を作成し、これらの証明書は安全ではありません。 ストアは信頼されたルート証明機関に自己署名証明書を配置するデプロイ環境をより忠実にシミュレートする開発環境を作成できます。

 作成して、証明書の使用の詳細については、次を参照してください。 [Working with Certificates](working-with-certificates.md)します。 資格情報として証明書を使用する方法の詳細については、次を参照してください。 [Securing Services and Clients](securing-services-and-clients.md)します。 Microsoft Authenticode テクノロジの使用方法については、「 [Authenticode Overviews and Tutorials (Authenticode の概要とチュートリアル)](https://go.microsoft.com/fwlink/?LinkId=88919)」を参照してください。

## <a name="to-create-a-self-signed-root-authority-certificate-and-export-the-private-key"></a>自己署名ルート証明書を作成して秘密キーをエクスポートするには

次のコマンドは、"ルート Ca"、現在のユーザー個人用ストアでのサブジェクト名を持つ、自己署名証明書を作成します。

```powershell
$rootCert = New-SelfSignedCertificate -CertStoreLocation cert:\CurrentUser\My -DnsName "RootCA" -TextExtension @("2.5.29.37={text}1.3.6.1.5.5.7.3.1,1.3.6.1.5.5.7.3.2") -KeyUsage CertSign,DigitalSignature
```

後の手順で必要な場所にインポートできるように、証明書を PFX ファイルにエクスポートする必要があります。 秘密キーで証明書をエクスポートするときに、保護するためにパスワードが必要です。 パスワードを保存、`SecureString`を使用して、 [Export-pfxcertificate](/powershell/module/pkiclient/export-pfxcertificate)コマンドレットを証明書を PFX ファイルに関連付けられている秘密キーと共にエクスポートします。 パブリック証明書だけを使用して CRT ファイルに保存、[証明書のエクスポート](/powershell/module/pkiclient/export-certificate)コマンドレット。

```powershell
[System.Security.SecureString]$rootcertPassword = ConvertTo-SecureString -String "password" -Force -AsPlainText
[String]$rootCertPath = Join-Path -Path 'cert:\CurrentUser\My\' -ChildPath "$($rootcert.Thumbprint)"
Export-PfxCertificate -Cert $rootCertPath -FilePath 'RootCA.pfx' -Password $rootcertPassword
Export-Certificate -Cert $rootCertPath -FilePath 'RootCA.crt'
```

## <a name="to-create-a-new-certificate-signed-by-a-root-authority-certificate"></a>ルート証明書によって署名された新しい証明書を作成するには

次のコマンドは、署名された証明書を作成、 `RootCA` "SignedByRootCA"発行元の秘密キーを使用してのサブジェクト名を使用します。

```powershell
$testCert = New-SelfSignedCertificate -CertStoreLocation Cert:\LocalMachine\My -DnsName "SignedByRootCA" -KeyExportPolicy Exportable -KeyLength 2048 -KeyUsage DigitalSignature,KeyEncipherment -Signer $rootCert
```

同様に、署名証明書は、秘密キーを使用して、PFX ファイルと CRT ファイルに公開キーのみに保存します。

```powershell
[String]$testCertPath = Join-Path -Path 'cert:\LocalMachine\My\' -ChildPath "$($testCert.Thumbprint)"
Export-PfxCertificate -Cert $testCertPath -FilePath testcert.pfx -Password $rootcertPassword
Export-Certificate -Cert $testCertPath -FilePath testcert.crt
```

## <a name="installing-a-certificate-in-the-trusted-root-certification-authorities-store"></a>信頼されたルート証明機関の証明書ストアに証明書をインストールする

作成された自己署名証明書は、[信頼されたルート証明機関] の証明書ストアにインストールできます。 この証明書で署名された証明書は、この時点で信頼できるものと見なされるようになります。 したがって、この証明書が不要になった場合は、直ちに証明書ストアから削除してください。 この証明書を削除すると、それを使って署名した証明書は認証されなくなります。 ルート証明機関の証明書は、必要に応じて一連の証明書を有効化する手段の 1 つにすぎません。 たとえばピアツーピア アプリケーションの場合、証明書が提示されれば相手の識別情報を信頼できるので、ルート証明機関は必要ないのが普通です。

### <a name="to-install-a-self-signed-certificate-in-the-trusted-root-certification-authorities"></a>自己署名証明書を信頼されたルート証明機関としてインストールするには

1. 証明書スナップインを開きます。 詳細については、「[方法 :MMC スナップインで証明書を表示](how-to-view-certificates-with-the-mmc-snap-in.md)します。

2. 証明書の格納先となる、 **[ローカル コンピューター]** または **[現在のユーザー]** のフォルダーを開きます。

3. **[信頼されたルート証明機関]** フォルダーを開きます。

4. **[証明書]** フォルダーを右クリックして、 **[すべてのタスク]** メニューの **[インポート]** を実行します。

5. 画面の指示に従って、RootCA.pfx をストアにインポートする方法について。

## <a name="using-certificates-with-wcf"></a>WCF で証明書の使用

一時的な証明書を設定したら、それを使用して、クライアント資格情報の種類として証明書を指定する WCF ソリューションを開発できます。 たとえば、次の XML 構成では、メッセージ セキュリティを設定して、クライアント資格情報の種類として証明書を指定しています。

### <a name="to-specify-a-certificate-as-the-client-credential-type"></a>クライアント資格情報の種類として証明書を指定するには

1. サービスの構成ファイルで、次の XML を使用して、セキュリティ モードをメッセージに、クライアント資格情報の種類を証明書に設定します。

    ```xml
    <bindings>
      <wsHttpBinding>
        <binding name="CertificateForClient">
          <security>
            <message clientCredentialType="Certificate" />
          </security>
        </binding>
      </wsHttpBinding>
    </bindings>
    ```

2. クライアントの構成ファイルでは、次の XML を使用して、証明書がユーザーのストアではあり、"CohoWinery にします"値の SubjectName フィールドを検索して見つかんだことができます。

    ```xml
    <behaviors>
      <endpointBehaviors>
        <behavior name="CertForClient">
          <clientCredentials>
            <clientCertificate findValue="CohoWinery" x509FindType="FindBySubjectName" />
          </clientCredentials>
        </behavior>
      </endpointBehaviors>
    </behaviors>
    ```

WCF での証明書の使用に関する詳細については、「 [Working with Certificates](working-with-certificates.md)」を参照してください。

## <a name="net-framework-security"></a>.NET Framework のセキュリティ

一時的なルート証明書は、不要になったら **[信頼されたルート証明機関]** フォルダーや **[個人]** フォルダーから確実に削除してください。削除するには、証明書を右クリックし、 **[削除]** をクリックします。

## <a name="see-also"></a>関連項目

- [証明書の使用](working-with-certificates.md)
- [方法: MMC スナップインで証明書の表示](how-to-view-certificates-with-the-mmc-snap-in.md)
- [サービスおよびクライアントのセキュリティ保護](securing-services-and-clients.md)
