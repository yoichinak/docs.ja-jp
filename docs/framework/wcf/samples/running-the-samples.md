---
title: Windows Communication Foundation サンプルの実行
ms.date: 03/30/2017
ms.assetid: db8a83da-95c1-4a21-a9d2-48caeb6398ea
ms.openlocfilehash: df984f2464084948cdaa51dab96554de9400911f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69965494"
---
# <a name="running-the-windows-communication-foundation-samples"></a>Windows Communication Foundation サンプルの実行
Windows Communication Foundation (WCF) サンプルは、単一コンピューター構成または複数コンピューター構成で実行できます。 サンプルは、単一コンピューターでそのまま実行できます。 複数コンピューター構成で実行するには、サンプルの構成ファイルの設定を変更する必要があります。 単一コンピューターおよび複数コンピューターの構成でサンプルを実行する手順を、次に示します。 インターネット インフォメーション サービス (IIS) でホストされるサービスと自己ホスト型のサービスのサンプルとでは、手順が異なります。 ほとんどのサンプルは IIS でホストされます。サンプルのホスト方法を判断するには、サンプルの Readme 情報を参照してください。  
  
 [!INCLUDE[wv](../../../../includes/wv-md.md)] では、IIS でホストされていないサンプルには、リスナーを Http.sys に登録するための管理特権が必要です。 Httpcfg.exe を使用して、サービスのリッスン アドレスをサービスが実行されているアカウントに登録するか、管理者権限で実行されているコマンド プロンプトでサービスを起動します。  
  
> [!NOTE]
> WCF サンプルをビルドまたは実行する前に、 [Windows Communication Foundation のサンプルの1回限りのセットアップ手順](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)を実行していることを確認してください。  
  
### <a name="to-run-the-sample-on-the-same-machine"></a>サンプルを同じコンピューターで実行するには  
  
1. サービスが IIS によってホストされている場合は、次のアドレス`http://localhost/servicemodelsamples/service.svc`を入力して、ブラウザーを使用してサービスにアクセスできることを確認します。 これに応答して、確認ページが表示されます。 [確認] ページが表示されない場合は、「 [WCF サンプルのトラブルシューティングのヒント](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90))」を参照してください。  
  
2. サービスが自己ホスト型の場合は、言語固有のフォルダーの下の \service\bin にある Service.exe を実行します。 サービス アクティビティがサービス コンソール ウィンドウに表示されます。  
  
3. 言語固有のフォルダーの下\\にある、から client.exe を実行します。 クライアント アクティビティがクライアント コンソール ウィンドウに表示されます。  
  
4. クライアントとサービスが通信できない場合は、「 [WCF サンプルのトラブルシューティングのヒント](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90))」を参照してください。  
  
### <a name="to-run-the-sample-across-machines"></a>サンプルを複数コンピューターで実行するには  
  
1. サービスが IIS でホストされている場合 :  
  
    1. サービス コンピューターで、ServiceModelSamples という仮想ディレクトリを作成します。 [Windows Communication Foundation サンプルの1回限りのセットアップ手順](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)に含まれるバッチファイル setupvroot を使用して、ディスクディレクトリと仮想ディレクトリを作成できます。  
  
    2. サービス プログラム ファイルを %SystemDrive%\Inetpub\wwwroot\servicemodelsamples からサービス コンピューターの ServiceModelSamples 仮想ディレクトリにコピーします。 このファイルが \bin ディレクトリにあることを確認します。  
  
    3. ブラウザーを使用して、サービスにクライアント コンピューターからアクセスできるかどうかをテストします。  
  
     サービスが自己ホスト型の場合、次の手順を実行します。  
  
    1. サービス コンピューターで、サービス ファイルを保持するディレクトリを作成します。  
  
    2. サービス プログラム ファイルを、言語固有のフォルダーにある \service\bin\ フォルダーからサービス コンピューターにコピーします。  
  
    3. サービスの構成ファイルで、エンドポイント定義のアドレス値をサービスの新しいアドレスに変更します。 アドレスの "localhost" への参照をすべて完全修飾ドメイン名に置き換えます。  
  
    4. コマンド プロンプトから Service.exe を起動します。  
  
2. クライアント プログラム ファイルを、言語固有のフォルダーにある \client\bin\ フォルダーからクライアント コンピューターにコピーします。  
  
3. エンドポイント アドレスを設定します。  
  
    1. サービスの実行に使用されているのがドメイン アカウントではない場合、クライアント構成ファイルを開き、エンドポイント定義のアドレス値をサービスの新しいアドレスに変更します。 アドレスの "localhost" への参照をすべて完全修飾ドメイン名に置き換えます。  
  
    2. サービスの実行に使用されているのがドメイン アカウントの場合、サービスに対して Svcutil.exe を実行し、クライアントの構成を再生成します。 Svcutil.exe の実行の詳細については、「 [Windows Communication Foundation サンプルのビルド](../../../../docs/framework/wcf/samples/building-the-samples.md)」を参照してください。 サンプルの構成ファイルではなく、生成されたファイルを使用します。 生成された構成ファイルには、追加の ID 情報があります (また、サービス エンドポイントへの接続に必要なすべての設定が、既定の設定であるにもかかわらず含まれています)。 Id 情報の詳細については、「[サービス id と認証](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)」および[ \<「id >](../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)」を参照してください。  
  
4. クライアント コンピューターで、コマンド プロンプトから Client.exe を起動します。  
  
### <a name="to-debug-a-service"></a>サービスをデバッグするには  
  
1. **[ビルド]** メニューまたは CTRL + SHIFT + B キーを使用して、ソリューション (クライアントとサービスの両方) をビルドします。  
  
2. サービスが IIS でホストされている場合 :  
  
    1. アドレス`http://localhost/servicemodelsamples/service.svc`を入力して、ブラウザーを使用してサービスをアクティブにします。  
  
    2. ソリューションで、 **[デバッグ]** メニューの **[プロセスにアタッチ]** メニュー項目をクリックします。  
  
    3. **[全ユーザーのプロセスを表示する]** チェック ボックスをオンにします。  
  
    4. デバッグ対象のホスト ワーカー プロセス W3wp.exe を選択します (Windows XP では ASPNet_wp.exe を選択します)。  
  
3. これで、サービス内にブレークポイントを設定し、例外に対してブレークポイントを有効にできます。  
  
4. クライアントプロジェクト項目を右クリックし、 **[デバッグ]** 、 **[新しいインスタンスを開始]** の順に選択します。  
  
### <a name="to-clean-up-after-the-sample"></a>サンプルの実行後にクリーンアップするには  
  
- サービスがセキュリティの目的で IIS でホストされている場合、サンプルの使用が終わったら、このセットアップで付与された仮想ディレクトリの定義とアクセス許可を削除してください。  
  
## <a name="see-also"></a>関連項目

- [Windows Communication Foundation サンプルのビルド](../../../../docs/framework/wcf/samples/building-the-samples.md)
- [WCF サンプルのトラブルシューティングのヒント](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90))
