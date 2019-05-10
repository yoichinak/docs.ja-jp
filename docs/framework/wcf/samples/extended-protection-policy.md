---
title: 拡張保護ポリシー
ms.date: 03/30/2017
ms.assetid: e2616a10-317e-4c34-8023-0c015a80a82f
ms.openlocfilehash: c2a79798569e308c37bd66bf0bdf8dee0cfa6951
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2019
ms.locfileid: "64650051"
---
# <a name="extended-protection-policy"></a>拡張保護ポリシー
拡張保護は、man-in-the-middle (MITM) 攻撃に対するセキュリティ イニシアチブです。 MITM 攻撃はセキュリティの脅威です。MITM は、クライアントの資格情報を取得し、その資格情報をサーバーに転送します。  
  
## <a name="demonstrates"></a>使用例  
 拡張保護  
  
## <a name="discussion"></a>説明  
 アプリケーションが HTTPS で Kerberos、Digest または NTLM を使用して認証を実行する場合、最初にトランスポート レベルのセキュリティ (TLS) チャネルが構築され、その後セキュリティ チャネルを使用して認証が行われます。 しかし、SSL によって生成されるセッション キーと認証時に生成されるセッション キーはバインドされていません。 サーバーはセキュリティ チャネルがクライアントまたは MITM のどちらで確立されたものであるか知ることができないため、トランスポート チャネルそのものはセキュリティで保護されていても、MITM がクライアントとサーバーの間に自身を構築し、クライアントからの要求の転送を開始する可能性があります。 このシナリオの解決策として、外部の TLS チャネルを内部の認証チャネルにバインドする方法があります。この方法により、サーバーは、MITM が存在するかどうかを検出できます。  
  
> [!NOTE]
>  このサンプルは、IIS でホストされている場合にのみ機能します。Cassini (Visual Studio Development Server) は HTTPS をサポートしないため、Cassini 上では機能しません。  
  
> [!NOTE]
>  この機能は現在 Windows 7 でのみ使用できます。 次の手順は、Windows 7 でのみ実行できます。  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>サンプルをセットアップ、ビルド、および実行するには  
  
1. インターネット インフォメーション サービス インストール**コントロール パネル**、**プログラム追加と削除**、 **Windows 機能**します。  
  
2. インストール**Windows 認証**で**Windows 機能**、**インターネット インフォメーション サービス**、 **World Wide Web サービス**、 **セキュリティ**、および**Windows 認証**します。  
  
3. インストール**Windows Communication Foundation HTTP Activation**で**Windows 機能**、 **Microsoft .NET Framework 3.5.1**、および**Windows 通信Foundation HTTP Activation**します。  
  
4. このサンプルを実行するには、サーバーとの安全なチャネルを確立する必要のあるクライアントが必要なので、インターネット インフォメーション サービス (IIS) マネージャーからインストールすることのできるサーバー証明書が存在する必要があります。  
  
    1. IIS マネージャーを開きます。 開いている**サーバー証明書**に表示される、**機能ビュー**  タブのルート ノード (マシン名) を選択するとします。  
  
    2. このサンプルをテストする目的で、自己署名証明書を作成します。 インターネット エクスプローラーで証明書の安全性に関するプロンプトが表示されないようにする場合は、信頼されたルート証明機関ストアに証明書をインストールします。  
  
5. 開く、**アクション**既定の Web サイトのウィンドウ。 クリックして**サイトの編集**、**バインド**します。 HTTPS が存在しない場合は、ポート番号を 443 に指定して HTTPS を追加します。 前の手順で作成した SSL 証明書を割り当てます。  
  
6. サービスをビルドします。 これにより、仮想ディレクトリが IIS に作成され、サービスを Web ホストにするために必要な .dll ファイル、.svc ファイルおよび .config ファイルがコピーされます。  
  
7. IIS マネージャーを開きます。 仮想ディレクトリを右クリックして (**ExtendedProtection**)、前の手順で作成されました。 選択**アプリケーションへの変換**します。  
  
8. 開く、**認証**モジュール IIS マネージャーではこの仮想ディレクトリと有効にする**Windows 認証**します。  
  
9. オープン**詳細設定** **Windows 認証**この仮想ディレクトリに設定**ために必要な**。  
  
10. ブラウザー ウィンドウから HTTPS URL にアクセスして (完全修飾ドメイン名を指定します) サービスをテストできます。 リモート コンピューターからこの URL にアクセスする場合は、すべての受信 HTTP および HTTPS 通信に対してファイアウォールが開かれていることを確認してください。  
  
11. クライアント構成ファイルを開き、クライアントの完全修飾ドメイン名、または `<<full_machine_name>>` を置き換えるエンドポイント アドレス属性を指定します。  
  
12. クライアントを実行します。 クライアントはサービスと通信します。これで、安全なチャネルが確立され、拡張保護が使用されます。  
  
> [!IMPORTANT]
>  サンプルは、既にコンピューターにインストールされている場合があります。 続行する前に、次の (既定の) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合に移動[Windows Communication Foundation (WCF) と .NET Framework 4 向けの Windows Workflow Foundation (WF) サンプル](https://go.microsoft.com/fwlink/?LinkId=150780)すべて Windows Communication Foundation (WCF) をダウンロードして[!INCLUDE[wf1](../../../../includes/wf1-md.md)]サンプル。 このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Security\ExtendedProtection`
