---
title: インターネット インフォメーション サービス (IIS) サーバー証明書インストール手順
ms.date: 03/30/2017
ms.assetid: 11281490-d2ac-4324-8f33-e7714611a34b
ms.openlocfilehash: 8d0b80930424f0d8529f2b035a8e1167f361f99a
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/09/2019
ms.locfileid: "59303944"
---
# <a name="internet-information-services-iis-server-certificate-installation-instructions"></a>インターネット インフォメーション サービス (IIS) サーバー証明書インストール手順
インターネット インフォメーション サービス (IIS) と安全に通信するこのサンプルを実行するには、サーバー証明書を作成してインストールする必要があります。  
  
## <a name="step-1-creating-certificates"></a>手順 1. 証明書の作成  
 コンピューターの証明書を作成するには、管理者特権で Visual Studio の開発者コマンド プロンプトを開きし、の各 IIS をセキュリティで保護された通信を使用するサンプルに含まれている Setup.bat を実行します。 このバッチ ファイルを実行する前に、Makecert.exe を含むフォルダがパスに含まれていることを確認します。 Setup.bat で証明書の作成に使用されるコマンドは、次のとおりです。  
  
```  
makecert -sr LocalMachine -ss My -n CN=ServiceModelSamples-HTTPS-Server -sky exchange -sk ServiceModelSamples-HTTPS-Key  
```  
  
## <a name="step-2-installing-certificates"></a>手順 2. 証明書のインストール  
 先ほど作成した証明書をインストールするために必要な手順は、使用している IIS のバージョンによって異なります。  
  
#### <a name="to-install-iis-on-iis-51-windows-xp-and-iis-60-windows-server-2003"></a>IIS 5.1 (Windows XP) および IIS 6.0 (Windows Server 2003) に証明書をインストールするには  
  
1. インターネット インフォメーション サービス マネージャー MMC スナップインを開きます。  
  
2. 既定の Web サイトを右クリックして**プロパティ**します。  
  
3. 選択、**ディレクトリ セキュリティ**タブ。  
  
4. をクリックして、**サーバー証明書**ボタンをクリックします。 Web サーバー証明書ウィザードが起動します。  
  
5. ウィザードを完了します。 証明書を割り当てるオプションを選択します。 表示される証明書の一覧から ServiceModelSamples-HTTPS-Server 証明書を選択します。  
  
     ![証明書ウィザードの IIS](../../../../docs/framework/wcf/samples/media/iiscertificate-wizard.GIF "IISCertificate_Wizard")  
  
6. HTTPS アドレスを使用して、ブラウザーでサービスへのアクセスをテスト`https://localhost/servicemodelsamples/service.svc`します。  
  
#### <a name="if-ssl-was-previously-configured-by-using-httpcfgexe"></a>Httpcfg.exe であらかじめ SSL が構成されている場合  
  
1. Makecert.exe を使用 (または Setup.bat を実行) して、サーバー証明書を作成します。  
  
2. IIS マネージャを実行し、前の手順に従って証明書をインストールします。  
  
3. クライアント プログラムに次のコード行を追加します。  
  
> [!IMPORTANT]
>  このコードが必要になるのは、Makecert.exe によって作成された証明書などをテストする場合のみです。 製品版のコードには、お勧めしません。  
  
```  
PermissiveCertificatePolicy.Enact("CN=ServiceModelSamples-HTTPS-Server");  
```  
  
#### <a name="to-install-iis-on-iis-70-windows-vista-and-windows-server-2008"></a>IIS 7.0 (Windows Vista および Windows Server 2008) に証明書をインストールするには  
  
1. **開始** メニューのをクリックして**実行**、入力**inetmgr**インターネット インフォメーション サービス (IIS) MMC スナップインを開きます。  
  
2. 右クリックし、**既定の Web サイト**選択**バインドを編集しています.**  
  
3. をクリックして、**追加**のボタン、**サイト バインド** ダイアログ ボックス。  
  
4. 選択**HTTPS**から、**型**ドロップダウン リスト。  
  
5. 選択、 **ServiceModelSamples-HTTPS サーバー**から、 **SSL 証明書**ドロップダウン リストをクリックします**OK**します。  
  
6. HTTPS アドレスを使用して、ブラウザーでサービスへのアクセスをテスト`https://localhost/servicemodelsamples/service.svc`します。  
  
> [!NOTE]
>  先ほどインストールしたテスト証明書は信頼された証明書ではないので、この証明書でセキュリティ保護されたローカル Web アドレスを参照した場合、Internet Explorer のセキュリティ警告がさらに発生する場合があります。  
  
## <a name="removing-certificates"></a>証明書の削除  
  
-   前に説明したようにインターネット インフォメーション サービス マネージャーを使用しますが、証明書またはバインディングを追加するのではなく削除します。  
  
-   次のコマンドを使用して、コンピューターの証明書を削除します。  
  
    ```  
    httpcfg delete ssl -i 0.0.0.0:443  
    ```
