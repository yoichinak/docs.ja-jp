---
title: メッセージ資格情報付き WS トランスポート
ms.date: 03/30/2017
ms.assetid: 0d092f3a-b309-439b-920b-66d8f46a0e3c
ms.openlocfilehash: 076d4490f6edc6efa8eeb50ae8baa23d5c4e369a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183144"
---
# <a name="ws-transport-with-message-credential"></a>メッセージ資格情報付き WS トランスポート
このサンプルでは、メッセージに含まれるクライアント資格情報と組み合わせて SSL トランスポート セキュリティを使用する例を示します。 このサンプルでは、`wsHttpBinding` バインディングを使用します。  
  
 既定で、`wsHttpBinding` バインディングは HTTP 通信を実現します。 トランスポート セキュリティ用に構成すると、バインディングは HTTPS 通信をサポートします。 HTTPS により、通信回線を介して送信されるメッセージについての機密性および整合性の保護が実現します。 ただし、サービスに対するクライアントの認証に使用できる一連の認証機構は、HTTPS トランスポートのサポート範囲に限定されます。 Windows 通信基盤 (WCF)`TransportWithMessageCredential`では、この制限を克服するために設計されたセキュリティ モードを提供します。 このセキュリティ モードが構成されると、送信メッセージの機密性および整合性を実現してサービス認証を実行する、トランスポート セキュリティが使用されます。 ただし、クライアント認証は、クライアント資格情報をメッセージに直接入力することによって実行されます。 これにより、トランスポート セキュリティ モードのパフォーマンス上の利点を維持しながら、クライアント認証にメッセージ セキュリティ モードでサポートされている資格情報の種類を使用できます。  
  
 このサンプルでは、サービスに対するクライアントの認証に `UserName` 資格情報が使用されます。  
  
 このサンプルは、電卓サービスを実装する[作業の開始](../../../../docs/framework/wcf/samples/getting-started-sample.md)に基づいています。 `wsHttpBinding` バインディングは、クライアントとサービスのアプリケーション構成ファイルに指定され、構成されます。  
  
> [!NOTE]
> このサンプルのセットアップ手順とビルド手順については、このトピックの最後を参照してください。  
  
 サンプルのプログラム コードは、[作業の開始](../../../../docs/framework/wcf/samples/getting-started-sample.md)サービスのコードとほぼ同じです。 `GetCallerIdentity` サービス コントラクトによって追加された操作が 1 つあります。 この操作は、呼び出し元の ID の名前を呼び出し元に返します。  

```csharp
public string GetCallerIdentity()  
{  
    // Use ServiceSecurityContext.WindowsIdentity to get the name of the caller.  
    return ServiceSecurityContext.Current.WindowsIdentity.Name;  
}  
```

 このサンプルをビルドして実行する前に、証明書を作成し、Web サーバー証明書ウィザードを使用してあらかじめ割り当てておく必要があります。 次に示すクライアント用構成の例のように、構成ファイル設定でエンドポイントとバインディングを定義すると、`TransportWithMessageCredential` セキュリティ モードが有効になります。  
  
```xml  
<system.serviceModel>  
  <client>  
    <endpoint name=""  
              address="https://localhost/servicemodelsamples/service.svc"
              binding="wsHttpBinding"
              bindingConfiguration="Binding1"
              contract="Microsoft.ServiceModel.Samples.ICalculator" />  
  </client>  
  
  <bindings>  
    <wsHttpBinding>  
      <!--   
        This configuration defines the security mode as TransportWithMessageCredential.  
        and the clientCredentialType as UserName.  
        -->  
      <binding name="Binding1">  
        <security mode ="TransportWithMessageCredential">  
          <message clientCredentialType="UserName" />  
        </security>  
      </binding>  
    </wsHttpBinding>  
  </bindings>  
</system.serviceModel>  
```  
  
 アドレス指定では https:// スキームを使用しています。 このバインド構成により、セキュリティ モードが `TransportWithMessageCredential` に設定されます。 同じセキュリティ モードが、サービスの Web.config ファイルで指定される必要があります。  
  
 このサンプルで使用する証明書は、Makecert.exe で作成されたテスト証明書であるため、ブラウザから https: アドレスなどに`https://localhost/servicemodelsamples/service.svc`アクセスしようとすると、セキュリティ警告が表示されます。 WCF クライアントがテスト証明書を使用できるようにするために、セキュリティ警告を抑制するコードがクライアントに追加されました。 そのためのコードとそれに必要なクラスは、本運用の証明書を使用するときには不要です。  

```csharp
// WARNING: This code is only needed for test certificates such as those created by makecert. It is
// not recommended for production code.  
PermissiveCertificatePolicy.Enact("CN=ServiceModelSamples-HTTPS-Server");  
```
  
 このサンプルを実行すると、操作要求および応答がクライアントのコンソール ウィンドウに表示されます。 クライアントをシャットダウンするには、クライアント ウィンドウで Enter キーを押します。  
  
```console  
Username authentication required.  
Provide a valid machine or domain account. [domain\\user]  
   Enter username:
YourDomainName\YourAccountName  
   Enter password:
********  
YourDomainName\YourAccountName  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>サンプルをセットアップ、ビルド、および実行するには  
  
1. [Windows コミュニケーションファウンデーション サンプルのワンタイム セットアップ手順を](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)実行したことを確認します。  
  
2. インターネット インフォメーション サービス[(IIS) サーバー証明書のインストール手順](../../../../docs/framework/wcf/samples/iis-server-certificate-installation-instructions.md)を実行したことを確認します。  
  
3. ソリューションの C# 版または Visual Basic .NET 版をビルドするには、「 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)」の手順に従います。  
  
4. 単一または複数のコンピューターにまたがる構成でサンプルを実行するには[、「Windows コミュニケーション ファウンデーション サンプルの実行」の手順に](../../../../docs/framework/wcf/samples/running-the-samples.md)従います。  
