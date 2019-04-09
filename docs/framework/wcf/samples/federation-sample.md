---
title: フェデレーション サンプル
ms.date: 03/30/2017
ms.assetid: 7e9da0ca-e925-4644-aa96-8bfaf649d4bb
ms.openlocfilehash: 5c71abc3308513be7b00d92254e92e814c3688dc
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59155208"
---
# <a name="federation-sample"></a>フェデレーション サンプル
このサンプルではフェデレーション セキュリティを示します。  
  
## <a name="sample-details"></a>サンプルの詳細  
 Windows Communication Foundation (WCF) が使用して、フェデレーション セキュリティ アーキテクチャをデプロイするためのサポートを提供、`wsFederationHttpBinding`します。 `wsFederationHttpBinding` は、セキュリティで保護された、信頼できる、相互運用が可能なバインディングを提供します。このバインディングでは、要求/応答の通信のための基になるトランスポート機構として HTTP を使用でき、エンコーディングのためのワイヤ形式として Text/XML を使用できます。 WCF でのフェデレーションの詳細については、次を参照してください。[フェデレーション](../../../../docs/framework/wcf/feature-details/federation.md)します。  
  
 シナリオは、次の 4 つの部分から構成されます。  
  
-   BookStore サービス  
  
-   BookStore STS  
  
-   HomeRealm STS  
  
-   BookStore クライアント  
  
 BookStore サービスは、`BrowseBooks` と `BuyBook` の 2 つの操作をサポートします。 サービスでは、`BrowseBooks` 操作には匿名アクセスできますが、`BuyBooks` 操作にアクセスするには認証済みのアクセス権限が必要です。 認証は、BookStore STS によって発行されたトークンの形式を取ります。 BookStore サービス用の構成ファイルは、次のように `wsFederationHttpBinding` を使用して、クライアントを BookStore STS にポイントします。  
  
```xml  
<wsFederationHttpBinding>  
<!-- This is the Service binding for the BuyBooks endpoint. It redirects clients to the BookStore STS -->  
    <binding name='BuyBookBinding'>  
        <security mode="Message">  
            <message>  
                <issuerMetadata  
  address='http://localhost/FederationSample/BookStoreSTS/STS.svc/mex' >  
                    <identity>  
                        <dns value ='BookStoreSTS.com'/>  
                    </identity>  
                </issuerMetadata>  
            </message>  
        </security>  
    </binding>  
</wsFederationHttpBinding>  
```  
  
 次に BookStore STS は、HomeRealm STS によって発行されたトークンを使用した、クライアントの認証を要求します。 ここでも、BookStore STS 用の構成ファイルは、`wsFederationHttpBinding` を使用して、クライアントを HomeRealm STS にポイントします。  
  
```xml  
<wsFederationHttpBinding>  
 <!-- This is the binding for the clients requesting tokens from this STS. It redirects clients to the HomeRealm STS -->  
    <binding name='BookStoreSTSBinding'>  
        <security mode='Message'>  
            <message>  
                <issuerMetadata  
 address='http://localhost/FederationSample/HomeRealmSTS/STS.svc/mex' >  
                    <identity>  
                        <dns value ='HomeRealmSTS.com' />  
                    </identity>  
                </issuerMetadata>  
            </message>  
        </security>  
    </binding>  
</wsFederationHttpBinding>  
```  
  
 `BuyBook` 操作にアクセスするときに発生するイベントの順序は、次のとおりです。  
  
1.  クライアントは、Windows 資格情報を使用して HomeRealm STS に対する認証を行います。  
  
2.  HomeRealm STS は、BookStore STS に対する認証に使用できるトークンを発行します。  
  
3.  クライアントは、HomeRealm STS によって発行されたトークンを使用して BookStore STS に対する認証を行います。  
  
4.  BookStore STS は、BookStore サービスに対する認証に使用できるトークンを発行します。  
  
5.  クライアントは、BookStore STS によって発行されたトークンを使用して BookStore サービスに対する認証を行います。  
  
6.  クライアントは `BuyBook` 操作にアクセスします。  
  
 このサンプルの設定および実行方法については、次の手順を参照してください。  
  
> [!NOTE]
>  書き込みアクセス許可が必要、 **wwwroot**ディレクトリをこのサンプルを実行します。  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>サンプルをセットアップ、ビルド、および実行するには  
  
1.  SDK コマンド ウィンドウを開きます。 Setup.bat をサンプルのパスで実行します。 これにより、サンプルに必要な仮想ディレクトリが作成され、必要な証明書が適切な権限を付与されてインストールされます。  
  
    > [!NOTE]
    >  Setup.bat バッチ ファイルは、Windows SDK コマンド プロンプトから実行します。 MSSDK 環境変数が SDK のインストール ディレクトリを指している必要があります。 この環境変数は、Windows SDK コマンド プロンプトで自動設定されます。 セットアップで IIS 管理者スクリプトが使用されるため、[!INCLUDE[wv](../../../../includes/wv-md.md)] で IIS 6.0 管理互換がインストールされていることを確認する必要があります。 [!INCLUDE[wv](../../../../includes/wv-md.md)] でセットアップ スクリプトを実行するには、管理者権限が必要です。  
  
2.  Visual Studio で FederationSample.sln を開き、**ソリューションのビルド**から、**ビルド**メニュー。 これによって共通のプロジェクト ファイル、Bookstore サービス、Bookstore STS、および HomeRealm STS が作成され、IIS に展開されます。 さらに Bookstore クライアント アプリケーションがビルドされ、FederationSample\BookStoreClient\bin\Debug フォルダーに実行可能ファイル BookStoreClient.exe が配置されます。  
  
3.  BookStoreClient.exe をダブルクリックします。 BookStoreClient ウィンドウが表示されます。  
  
4.  クリックして、この書店で利用可能なブックを参照できます**Browse Books**します。  
  
5.  特定の本を購入する一覧で本を選択し、をクリックして**Buy Book**します。 アプリケーションが起動し、HomeRealm セキュリティ トークン サービスを使用した Windows 認証によって認証を行います。  
  
     サンプルは、ユーザーが 15 ドル以下の本を購入できるように構成されています。 15 ドルを超える本を購入しようとすると、クライアントは、BookStore サービスからアクセス拒否のメッセージを受け取ります。  
  
    > [!NOTE]
    >  サンプルでは、購入後にユーザーの与信限度額を更新しません。 ユーザーは、(固定の) 与信限度額以内なら何度でも本を購入できます。  
  
#### <a name="to-clean-up"></a>クリーンアップするには  
  
1.  Cleanup.bat を実行します。 これによって、設定中に作成された仮想ディレクトリが削除されます。同時に、設定中にインストールされた証明書も削除されます。  
  
> [!IMPORTANT]
>  サンプルは、既にコンピューターにインストールされている場合があります。 続行する前に、次の (既定の) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合に移動[Windows Communication Foundation (WCF) と .NET Framework 4 向けの Windows Workflow Foundation (WF) サンプル](https://go.microsoft.com/fwlink/?LinkId=150780)すべて Windows Communication Foundation (WCF) をダウンロードして[!INCLUDE[wf1](../../../../includes/wf1-md.md)]サンプル。 このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Scenario\Federation`  
