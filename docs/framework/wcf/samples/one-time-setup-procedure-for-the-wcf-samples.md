---
title: Windows Communication Foundation サンプルの 1 回限りのセットアップの手順
ms.date: 03/30/2017
ms.assetid: a5848ffd-3eb5-432d-812e-bd948ccb6bca
ms.openlocfilehash: 2b9d84089cdd987f2e2b1e3d23354505520a80f8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62052106"
---
# <a name="one-time-setup-procedure-for-the-windows-communication-foundation-samples"></a>Windows Communication Foundation サンプルの 1 回限りのセットアップの手順
Windows Communication Foundation (WCF) サンプルのほとんどがインターネット インフォメーション サービス (IIS) でホストされているし、共通の仮想ディレクトリから実行します。 この 1 回限りのセットアップ手順は、ディスクにフォルダーを作成しますという名前の iis 仮想ディレクトリも追加**ServiceModelSamples**します。

 **ServiceModelSamples**の構築と、IIS でホストされるサービスを使用するすべてのサンプルを実行する仮想ディレクトリが使用されます。 サンプルの実行に必要な仮想ディレクトリはこれだけです。 サンプルをビルドすると、この仮想ディレクトリにある、以前に配置されたサービスがすべて置き換えられます。この仮想ディレクトリには最近ビルドされたサンプルだけが配置されるため、そのサンプルしか使用できません。

> [!NOTE]
>  すべてのコマンドは、ローカル管理者アカウントで実行する必要があります。 Windows 7、[!INCLUDE[windowsver](../../../../includes/windowsver-md.md)]、または Windows Server 2008 R2 を使用している場合は、コマンド プロンプトも管理者権限で実行する必要があります。 これを行うには、コマンド プロンプトのアイコンを右クリックし、**管理者として実行**します。 このトピックで使用するすべてのコマンドは、適切なパスが設定されているコマンド プロンプトで実行する必要があります。  このようにするための最も簡単な方法は、Visual Studio コマンド プロンプトを使用する方法です。 このプロンプトを開くには、次のようにクリックします**開始**を選択します**すべてのプログラム**、下へスクロールして**Visual Studio 2010**を選択します**Visual Studio Tools**、。右クリックして**Visual Studio コマンド プロンプト (2010)**、 をクリックし、**管理者として実行**します。 Visual Studio Express Editions のいずれかがインストールされている場合は、このコマンド プロンプトを使用できません。この場合、システム パスに "C:\Windows\Microsoft.Net\Framework\v4.0" を追加する必要があります。  
  
### <a name="one-time-setup-procedure-for-wcf-samples"></a>WCF サンプルの 1 回限りのセットアップの手順  
  
1. [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] がセットアップされていることを確認します。 設定する方法の詳細についての[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]を参照してください[インターネット インフォメーション サービスのホスティング手順](../../../../docs/framework/wcf/samples/internet-information-service-hosting-instructions.md)します。  
  
2. [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)] がインストールされていることを確認します。 次のディレクトリに、v4.0 (またはそれ以降) を検索: **\Windows\Microsoft.NET\Framework**  
  
3. Visual Studio 2012 がインストールされていないかどうかと、オペレーティング システムが Windows Server 2008 SP2 または後で、インストール[修正プログラム 251798](https://go.microsoft.com/fwlink/?LinkId=184693)します。  
  
4. 次のコマンドを実行します。 これらのコマンドを実行する必要があります理由の詳細については、次を参照してください。 [IIS ホスト サービスのエラー](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms752252(v=vs.90))します。  
  
    > [!WARNING]
    >  IIS を再インストールした場合は、次のコマンドを再実行します。

    ```
    "%WINDIR%\Microsoft.Net\Framework\v4.0.30319\aspnet_regiis" –i –enable
    "%WINDIR%\Microsoft.Net\Framework\v4.0.30319\ServiceModelReg.exe" -r
    ```

    > [!WARNING]
    >  コマンドを実行して`aspnet_regiis –i –enable`すると、既定のアプリケーション プールを使用して実行[!INCLUDE[netfx40_short](../../../../includes/netfx40-short-md.md)]、同じコンピューター上の他のアプリケーションの互換性の問題を生成する可能性があります。  
  
5. に従って、[ファイアウォール手順](../../../../docs/framework/wcf/samples/firewall-instructions.md)サンプルで使用されるポートを有効にするためです。  
  
6. 次の既定のディレクトリを確認します。\<InstallDrive >:**\WF_WCF_Samples**します。 サンプルが既にインストールされている場合は、これが既定のディレクトリです。  
  
7. サンプルがインストールされていない場合はそれらのサンプルのダウンロード場所からインストール[Visual c#](https://go.microsoft.com/fwlink/?LinkId=190939)または[Visual Basic](https://go.microsoft.com/fwlink/?LinkID=193373)します。  
  
8. サンプルをインストールした後を参照してください。\<InstallDrive >:**\WF_WCF_Samples\WCF\Setup\\**  
  
9. 実行、 **Setupvroot.bat**バッチ ファイル。 次の手順が実行されます。  
  
    - ServiceModelSamples という名前の仮想ディレクトリが IIS に作成されます。  
  
    - %SystemDrive%\Inetpub\wwwroot\ServiceModelSamples and %SystemDrive%\Inetpub\wwwroot\ServiceModelSamples\bin という名前の新しいディスク ディレクトリが作成されます。  
  
     これらのディレクトリを手動で設定する場合を参照してください、[仮想ディレクトリのセットアップ手順](../../../../docs/framework/wcf/samples/virtual-directory-setup-instructions.md)します。 この手順で行ったすべての変更を元に戻すには、サンプルの使用が終わった後で cleanupvroot.bat を実行します。  
  
    > [!NOTE]
    >  cleanupvroot.bat を実行しない限り、この手順を実行するのは、1 台のコンピューターで 1 回だけです。

10. サンプルおよび Network Service ユーザーのビルドに使用するアカウントに対し、%SystemDrive%\inetpub\wwwroot の変更権限を付与する必要があります。 ビルドの実行時に、Web ホストの一部のサンプルがコンパイル済みバイナリを前述の場所にコピーしようとする場合があり、適切な権限が設定されていないと、ビルドは破損します。 またははその管理者は、SDK コマンド プロンプトまたは Visual Studio コマンド プロンプト (2012) を実行するアクセス許可のままにしたり、Visual Studio 2012 で管理者として実行しても、サンプルをビルドできます。

    > [!NOTE]
    >  この手順を完了していない場合は、ビルドの実行時に IIS でホストされているすべてのサンプルでエラーが発生します。 アクセス許可が正しく設定されていることを確認するか、SDK コマンド プロンプトと Visual Studio コマンド プロンプト (2012) を管理者として実行してください。

11. コンピューター上に C:\logs ディレクトリを作成します (一部のサンプルで必要になることがあります)。 このフォルダーに対する書き込みアクセスが適切なアカウントに付与されていることを確認してください。 Windows 7 では、 [!INCLUDE[wv](../../../../includes/wv-md.md)]、Windows Server 2008 R2 では、このアカウントは**ネットワーク サービス**します。 [!INCLUDE[lserver](../../../../includes/lserver-md.md)] では NT Authority\Network Service、 [!INCLUDE[wxp](../../../../includes/wxp-md.md)] および [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] では ASPNET です。

12. Setupcerttool.bat ファイルを実行します。 このファイルにある、 \<InstallPath > \WF_WCF_Samples\WCF\Setup\ フォルダー。  このスクリプトでは、次のタスクが実行されます。

    - FindPrivateKey ツールをビルドします。

    - %ProgramFiles%\ServiceModelSampleTools という名前のディレクトリを作成します。

    - 新しい FindPrivateKey ツールをこのディレクトリにコピーします。

     このツールは、証明書を使用して IIS でホストされるサンプルで必要です。

    > [!NOTE]
    >  セキュリティの目的で、サンプルの使用が終わったら、このセットアップ手順で付与された仮想ディレクトリの定義とアクセス許可を必ず削除してください。削除するには、Cleanupvroot.bat という名前のバッチ ファイルを実行します。

13. 自己ホスト型の (IIS でホストされていない) サンプルでは、リッスンを行うコンピューター上で HTTP アドレスを登録するためのアクセス許可が必要です。 HTTP 名前空間予約のアクセス許可は、サンプルの実行に使用されるユーザー アカウントから提供されます。 既定では、管理者アカウントには、任意の HTTP アドレスを登録するためのアクセス許可があります。 管理者以外のアカウントの場合は、サンプルで使用される HTTP 名前空間へのアクセス許可が付与される必要があります。 名前空間の予約を構成する方法については、「[Configuring HTTP and HTTPS](../../../../docs/framework/wcf/feature-details/configuring-http-and-https.md)」 (HTTP と HTTPS を構成する) を参照してください。

14. 一部のサンプルにはメッセージ キューが必要です。 参照してください[インストール メッセージ キュー (MSMQ)](../../../../docs/framework/wcf/samples/installing-message-queuing-msmq.md)インストール手順についてはします。

    > [!NOTE]
    >  メッセージ キューが必要なサンプルを実行する場合は、MSMQ サービスを事前に開始しておいてください。

15. 一部のサンプルには証明書が必要です。 参照してください[インターネット インフォメーション サービス (IIS) サーバー証明書のインストール手順](../../../../docs/framework/wcf/samples/iis-server-certificate-installation-instructions.md)します。
