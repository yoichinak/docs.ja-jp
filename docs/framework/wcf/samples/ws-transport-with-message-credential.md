---
title: メッセージ資格情報付き WS トランスポート
ms.date: 03/30/2017
ms.assetid: 0d092f3a-b309-439b-920b-66d8f46a0e3c
ms.openlocfilehash: 31c1ed5d4b62c0f0b4c0c149629bb84a7dab6f01
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58826211"
---
# <a name="ws-transport-with-message-credential"></a>メッセージ資格情報付き WS トランスポート
このサンプルでは、メッセージに含まれるクライアント資格情報と組み合わせて SSL トランスポート セキュリティを使用する例を示します。 このサンプルでは、`wsHttpBinding` バインディングを使用します。  
  
 既定で、`wsHttpBinding` バインディングは HTTP 通信を実現します。 トランスポート セキュリティ用に構成すると、バインディングは HTTPS 通信をサポートします。 HTTPS により、通信回線を介して送信されるメッセージについての機密性および整合性の保護が実現します。 ただし、サービスに対するクライアントの認証に使用できる一連の認証機構は、HTTPS トランスポートのサポート範囲に限定されます。 Windows Communication Foundation (WCF) の提供、`TransportWithMessageCredential`セキュリティ モードは、この制限を克服するために設計されています。 このセキュリティ モードが構成されると、送信メッセージの機密性および整合性を実現してサービス認証を実行する、トランスポート セキュリティが使用されます。 ただし、クライアント認証は、クライアント資格情報をメッセージに直接配置することによって実行されます。 これにより、トランスポート セキュリティ モードのパフォーマンスの利点を維持しながら、クライアント認証のメッセージ セキュリティ モードでサポートされている資格情報の種類を使用することができます。  
  
 このサンプルでは、サービスに対するクライアントの認証に `UserName` 資格情報が使用されます。  
  
 このサンプルがに基づいて、 [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md)電卓サービスを実装します。 `wsHttpBinding` バインディングは、クライアントとサービスのアプリケーション構成ファイルに指定され、構成されます。  
  
> [!NOTE]
>  このサンプルのセットアップ手順とビルド手順については、このトピックの最後を参照してください。  
  
 プログラム コード サンプルではのとほぼ同じ、 [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md)サービス。 `GetCallerIdentity` サービス コントラクトによって追加された操作が 1 つあります。 この操作は、呼び出し元の ID の名前を呼び出し元に返します。  

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
  
 Https にアクセスしようとするときにこのサンプルで使用される証明書は Makecert.exe で作成されたテスト証明書であるためセキュリティの警告が表示されます。 など、対処`https://localhost/servicemodelsamples/service.svc`、お使いのブラウザーから。 インプレース テスト証明書を使用する WCF クライアントを許可するには、クライアントのセキュリティの警告を非表示に追加のコードが追加されました。 そのためのコードとそれに必要なクラスは、本運用の証明書を使用するときには不要です。  

```csharp
// WARNING: This code is only needed for test certificates such as those created by makecert. It is   
// not recommended for production code.  
PermissiveCertificatePolicy.Enact("CN=ServiceModelSamples-HTTPS-Server");  
```
  
 このサンプルを実行すると、操作要求および応答がクライアントのコンソール ウィンドウに表示されます。 クライアントをシャットダウンするには、クライアント ウィンドウで Enter キーを押します。  
  
```  
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
  
1.  実行したことを確認、 [Windows Communication Foundation サンプルの 1 回限りのセットアップ手順](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)します。  
  
2.  実行したことを確認、[インターネット インフォメーション サービス (IIS) サーバー証明書のインストール手順](../../../../docs/framework/wcf/samples/iis-server-certificate-installation-instructions.md)します。  
  
3.  ソリューションの C# 版または Visual Basic .NET 版をビルドするには、「 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)」の手順に従います。  
  
4.  1 つまたは複数コンピュータ構成では、サンプルを実行する手順については、 [Windows Communication Foundation サンプルの実行](../../../../docs/framework/wcf/samples/running-the-samples.md)します。  
  
