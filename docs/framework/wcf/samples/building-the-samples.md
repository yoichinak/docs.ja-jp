---
title: Windows Communication Foundation サンプルのビルド
ms.date: 03/30/2017
ms.assetid: 2899e7a5-9cb2-4e8d-b8d2-f31391549198
ms.openlocfilehash: 021f17778bc019828d00fbd8e93cbc319de3047a
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/14/2019
ms.locfileid: "70990151"
---
# <a name="building-the-windows-communication-foundation-samples"></a>Windows Communication Foundation サンプルのビルド

Windows Communication Foundation (WCF) のサンプルは、Visual Studio IDE を使用するか、コマンドラインから**msbuild**コマンドを使用してビルドできます。 ここでは、両方の手順について説明します。

> [!NOTE]
> WCF サンプルをビルドまたは実行する前に、 [Windows Communication Foundation のサンプルに対して1回限りのセットアップ手順](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)を実行していることを確認してください。

## <a name="to-build-the-sample-using-a-command-prompt"></a>コマンド プロンプトを使用してサンプルをビルドするには

1. Visual Studio の開発者コマンドプロンプトを開き、サンプルをインストールしたディレクトリの場所にある言語固有のサブディレクトリに移動します。

2. コマンド`msbuild`ラインで「」と入力します。 クライアントプログラムファイルが*client\bin*に構築され、サービスプログラムファイルが*service\bin*に構築されます。 サービス プログラム ファイルもにコピーする場合は、サービスは、インターネット インフォメーション サービス (IIS) によってホストされている、 *servicemodelsamples* ディレクトリとその *\bin* サブディレクトリ。

> [!NOTE]
> *%Systemdrive%\inetpub\wwwroot*の acl を設定して、実行しているアカウントに変更のアクセス許可を付与する必要があります。 このように設定しない場合、ビルド後のイベントが失敗する場合があります。 代わりに、ACL の設定はそのままにして、SDK コマンド プロンプトを管理者として実行することもできます。

## <a name="to-build-the-sample-using-visual-studio"></a>Visual Studio を使用してサンプルをビルドするには

1. Visual Studio の **[ファイル]** メニューの [**プロジェクト/ソリューション**を**開く** > ] をクリックします。 サンプルをインストールしたディレクトリの下にある言語固有のサブディレクトリに移動し、.sln ファイルアイコンをダブルクリックして、Visual Studio でソリューションを開きます。

1. **[ビルド]** メニューの **[ソリューションのリビルド]** をクリックします。

   クライアント プログラムが client\bin にビルドされ、サービス プログラムが service\bin にビルドされます。 サービス プログラム ファイルもにコピーする場合は、サービスは IIS でホストされる、 *servicemodelsamples* ディレクトリとその *\bin* サブディレクトリ。

> [!NOTE]
> %systemdrive%\inetpub\wwwroot 上の ACL を、実行中のアカウントに変更権限を付与するように設定する必要があります。 このように設定しない場合、ビルド後のイベントが失敗する場合があります。 代わりに、ACL の設定はそのままにして、SDK コマンド プロンプトまたは Visual Studio を管理者として実行することもできます。 Visual Studio の一部のアクション (デバッガを ASP.Net ワーカー プロセスにアタッチするアクションなど) では、さらに管理特権が必要です。

## <a name="setup-batch-files-and-scripts"></a>セットアップ バッチ ファイルとスクリプト
 Setup.exe および Cleanup のバッチファイルとスクリプトは、Visual Studio 開発者コマンドプロンプトから実行する必要があります。 いくつかのセットアップ ファイルとクリーンアップ ファイルは、管理特権が必要なタスクを実行します。したがって、これらのファイルは管理特権で起動する必要があります。

## <a name="important-security-information-about-metadata-endpoints"></a>メタデータ エンドポイントに関する重要なセキュリティ情報
 機密性の高いサービスメタデータが誤って公開されるのを防ぐために、Windows Communication Foundation (WCF) サービスの既定の構成では、メタデータの公開が無効になっています。 この動作は、既定の設定ではセキュリティで保護されますが、同時に、サービスの構成の中でメタデータ発行の動作が明示的に有効化されない限り、サービスの呼び出しに必要なクライアント コードをメタデータ インポート ツール (Svcutil.exe など) を使用して生成できないことも意味します。 サンプルでの試みを容易にするため、ほとんどすべてのサンプルでは、セキュリティ保護されていないメタデータ公開エンドポイントを公開しています。 このようなエンドポイントを利用するコンシューマーは、匿名で、認証を受けていない可能性もあります。したがって、エンドポイントを配置する前には注意を払い、サービスのメタデータをパブリックに開示することが適切であることを確認する必要があります。 サービスメタデータの発行の詳細については、[メタデータ公開動作](../../../../docs/framework/wcf/samples/metadata-publishing-behavior.md)のサンプルを参照してください。 メタデータエンドポイントをセキュリティで保護するサンプルについては、[カスタムセキュアメタデータエンドポイント](../../../../docs/framework/wcf/samples/custom-secure-metadata-endpoint.md)のサンプルを参照してください。

## <a name="exception-handling"></a>例外処理
 通常、コードではサンプルの主題を重視するので、これらのサンプルに例外処理は含まれていません。 例外処理の詳細については、「[予期される例外](../../../../docs/framework/wcf/samples/expected-exceptions.md)のサンプル」を参照してください。

## <a name="regenerating-clients-and-configuration-with-svcutil"></a>Svcutil を使用したクライアントと構成の再生成
 [ServiceModel メタデータユーティリティツール (svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)を使用して、ほとんどのサンプルのクライアントコードと構成を再生成することができます。 一部のサンプルでは、構成を手動で編集する必要があります。 たとえば、Svcutil.exe を使用して、クライアント証明書の資格情報を使用するサンプルの構成を再生成する場合は、以前に構成された資格情報を手動で指定する必要があります。 一部のサンプルでは、生成コードに影響を与える、Svcutil.exe の特定のオプションを使用します。これらのオプションは、そうした特定のサンプルのトピックで指定されます。

### <a name="to-regenerate-the-client-and-configuration-files"></a>クライアントと構成ファイルを再生成するには

1. SDK コマンド プロンプトを開き、サンプルのインストール ディレクトリに存在する言語固有のサブディレクトリに移動します。

2. サービスが Web ホスト型の場合は、次のコマンドを使用します。

    ```console
    svcutil.exe /n:"http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples" http://localhost/servicemodelsamples/service.svc/mex /out:generatedClient.cs
    ```

     サービスが自己ホスト型の場合は、次のコマンドを使用します。

    ```console
    svcutil.exe /n:"http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples" http://localhost:8000/servicemodelsamples/service.svc/mex /out:generatedClient.cs
    ```

     自己`http://localhost:8000/ServiceModelSamples/service.svc/mex`ホスト型サービスの mex エンドポイントのアドレスで置き換えます。

     Visual Basic の型でクライアントを生成するには、次のコマンドを使用します。

    ```console
    svcutil.exe /n:"http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples" http://localhost/servicemodelsamples/service.svc/mex /l:vb /out:generatedClient.vb
    ```

     サービスが自己ホスト型の場合は、次のコマンドを使用します。

    ```console
    svcutil.exe /n:"http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples" http://localhost:8000/servicemodelsamples/service.svc/mex /l:vb /out:generatedClient.vb
    ```

    > [!NOTE]
    > クライアント構成の生成をスキップするには、 **/noConfig**オプションを追加します。

## <a name="see-also"></a>関連項目

- [Windows Communication Foundation サンプルの実行](../../../../docs/framework/wcf/samples/running-the-samples.md)
- [ServiceModel メタデータ ユーティリティ ツール (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)
