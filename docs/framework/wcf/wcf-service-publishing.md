---
title: WCF サービス発行
ms.date: 03/30/2017
ms.assetid: c806b253-cd47-4b96-b831-e73cbf08808f
ms.openlocfilehash: 33725c2f393529a7e59ed0b3ae1db01a359fb9a5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61791210"
---
# <a name="wcf-service-publishing"></a>WCF サービス発行

縦方向実際にテスト目的で、運用環境にアプリケーションを展開する WCF サービス ホストと WCF テスト クライアントによって提供される初期の開発環境からで Windows Communication Foundation (WCF) サービスの公開を支援します。 最終的な配置計画をコミットする前に、Windows Communication Foundation (WCF) サービスの公開を使用して、WCF サービスが正しく実行は発行する準備がであることを確認します。 さまざまなターゲットの場所をテストするために、WCF サービス ライブラリを展開することもできます。

## <a name="supported-services-and-target-locations"></a>サポートされているサービスとターゲットの場所

WCF サービス発行は、WCF サービス ライブラリ テンプレート、および以下の対応する項目テンプレートのセットから作成された WCF サービスの公開をサポートしています。

- WCF サービス ライブラリ テンプレートと項目テンプレート。

- 配信サービス ライブラリ

これらのサービス テンプレートを選択して検索できます**ファイル** > **新しいプロジェクト**> [**Visual Basic**または**Visual C#** ] > **WCF**します。 (WCF ワークフロー サービス アプリケーションと WCF サービス アプリケーションを含む)、この場所での他の WCF テンプレートを使用してを公開できる[ワンクリック web アプリケーションの発行](https://docs.microsoft.com/previous-versions/aspnet/dd465337(v=vs.110))します。

サービスは、次のターゲットの場所に発行できます。

- ローカル IIS

- ファイル システム

- FTP サイト

## <a name="using-wcf-service-publishing"></a>WCF サービス発行の使用

サービス実装を配置するには、次の手順を実行します。

1. 管理者特権で Visual Studio を開きます (実行可能ファイルを右クリックし、**管理者として実行**開きます)。  IIS 7.0 を使用して、後で、いることを確認するか「にする Windows 機能のオン/オフ」を使用して、コントロール パネルで「IIS メタベースおよび IIS6 構成との互換性」のコンポーネントをインストールしました。

2. サービス プロジェクトを開き、選択**ビルド** > **発行\<プロジェクト名 >** メイン メニューでプロジェクトを右クリックしてまたは**ソリューション エクスプ ローラー**クリック**発行**します。

3. **発行**ウィンドウが表示されます。 をクリックして、 **...**. サービスの配置先にするターゲットの場所を指定します。 ローカルの IIS、ファイル システム、または FTP サイトにアプリケーションをデプロイするを選択できます。 ローカル IIS にアプリケーションを配置する場合は、web サイトを選択およびクリックして、その下にある web アプリケーションを作成、 **Web アプリケーションの新規作成**右上隅にあるアイコンです。

4. クリックした後**発行**Visual Studio のメイン ウィンドウで、指定されたターゲットの場所にアプリケーションをデプロイし、ターゲット ディレクトリに Web.config、.svc、およびアセンブリのファイルをコピーします。 . .Svc ファイルの名前は"projectname.servicename.svc"。 サービスが正常に発行されると、次のような [Visual Studio の出力] ウィンドウで、ホットリンクを見つけることができます"に接続する`http://localhost/WebApplicationFolderName...`"。 Ctrl キーを押しながらリンクをクリックすると、Visual Studio の内側にブラウザー ページが開き、サービス ディレクトリ構造が表示されます。

     サイトを参照できない場合、IIS でディレクトリ ブラウザーが有効になっていない可能性があります。 有効にする「モ ノ利用できます」セクションではヒントに従ってください。 または、直接入力できます`http://localhost/WebApplicationFolderName/ProjectName.ServiceName.svc`サービス ページを表示します。

使用することができます**発行**アセンブリ、構成、およびターゲットの場所にプロジェクトで定義されているすべてのサービスの .svc ファイルをコピーするかどうかを指定し、転送先に既存のファイルを上書きします。

ローカルの IIS にアプリケーションを配置すると、IIS セットアップに関連するエラーが発生することがあります。 IIS が正しくインストールされていることを確認してください。 入力できます`http://localhost`ブラウザーのアドレス バーおよびチェックかどうか、IIS の既定のページが表示されます。 場合によっては、問題を ASP.NET または IIS で WCF の不適切な登録によって発生もあります。 Visual Studio 用開発者コマンド プロンプトを開くし、コマンドを実行できます`aspnet_regiis.exe -ir`ASP.NET 登録に関する問題を解決する方法のコマンドを実行`ServiceModelReg.exe –ia`WCF の登録に関する問題を修正します。

## <a name="files-generated-for-publishing"></a>発行用に生成されるファイル
 次のファイルがツールによって生成された WCF サービス ライブラリでは、Web でホストされるが、前に: アセンブリ ファイル、Web.config ファイル、および .svc ファイル。 生成されたファイルは、すべてターゲットの場所にコピーされます。 その後でサービスが発行されます。

### <a name="assembly-files"></a>アセンブリ ファイル
 WCF サービスを発行するときにこのツールを使用して、サービスは最初に自動的に構築し、ビルド後に、サービス プロジェクトでアセンブリ ファイルが生成されます。

### <a name="svc-file"></a>.SVC ファイル
 ファイルが存在するか、バージョンの有効性を確保するかどうか、発行操作には、WCF サービスごとに *.svc ファイルが生成されます。 Svc ファイルの 2 つの異なる種類があります。 WCF サービス ライブラリおよび配信サービス ライブラリでは、1 つ、シーケンシャル、ステート マシン ワークフロー サービス ライブラリのもう 1 つ。 生成された\*.svc ファイルは、ターゲットの場所のルート フォルダーにコピーします。

### <a name="webconfig-file"></a>Web.config ファイル
 サービス プロジェクトが特定のターゲットの場所に発行されるたびに、Web.config ファイルが作成されます。

 生成された Web.config ファイルには、Web ホスティング、および以下の変更を WCF サービス ライブラリの app.config ファイルの内容に役立つ Web セクションが含まれています。

- ベース アドレスが除外されています。

- ターゲット プラットフォームのトレース設定を保持するために、`<diagnostics>` 要素の設定が除外されています。

## <a name="publishing-wcf-services-with-non-http-bindings-to-iis"></a>IIS への非 HTTP バインドを使用した WCF サービスの公開
 IIS7.0 を使用している場合は後で、非 HTTP バインドを IIS で WCF サービスを発行できます。 事前の構成を行う必要があります。 詳細についてでトピックを参照してください[Windows プロセス アクティブ化サービスでのホスティング](../../../docs/framework/wcf/feature-details/hosting-in-windows-process-activation-service.md)します。

## <a name="security"></a>セキュリティ
 IIS は管理者アカウントで実行する必要があるため、ローカル IIS に発行するには、管理特権が必要です。 管理者特権のないユーザーが WCF サービスの公開が開いた場合は IIS はターゲットの場所として使用できます。 ファイル システム、または FTP サイトへの発行は、管理者特権のない動作します。

## <a name="see-also"></a>関連項目

- [WCF Visual Studio テンプレート](../../../docs/framework/wcf/wcf-vs-templates.md)
- [WCF サービス ホスト (WcfSvcHost.exe)](../../../docs/framework/wcf/wcf-service-host-wcfsvchost-exe.md)
- [WCF のテスト用クライアント (WcfTestClient.exe)](../../../docs/framework/wcf/wcf-test-client-wcftestclient-exe.md)