---
title: Windows Communication Foundation サンプルのビルド
ms.date: 03/30/2017
ms.assetid: 2899e7a5-9cb2-4e8d-b8d2-f31391549198
ms.openlocfilehash: b1f1005e32687d2683f757d847d9fa19e098f290
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61944067"
---
# <a name="building-the-windows-communication-foundation-samples"></a>Windows Communication Foundation サンプルのビルド

Visual Studio IDE を使用してまたはを使用して、Windows Communication Foundation (WCF) サンプルを構築できる、 **msbuild**コマンドラインからコマンド。 ここでは、両方の手順について説明します。

> [!NOTE]
> 構築しても、WCF サンプルのいずれかを実行する前に実行済みであることを確認します、 [Windows Communication Foundation サンプルの 1 回限りのセットアップ手順](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)します。

## <a name="to-build-the-sample-using-a-command-prompt"></a>コマンド プロンプトを使用してサンプルをビルドするには

1. Visual Studio 用開発者コマンド プロンプトを開きし、サンプルがインストールされているディレクトリの場所の言語固有のサブディレクトリに移動します。

2. 型`msbuild`コマンドライン。 クライアントのプログラム ファイルが組み込まれて*client \bin*に構築された、サービス プログラム ファイルと*service \bin*します。 サービス プログラム ファイルもにコピーする場合は、サービスは、インターネット インフォメーション サービス (IIS) によってホストされている、 *servicemodelsamples* ディレクトリとその *\bin* サブディレクトリ。

> [!NOTE]
> Acl を設定する必要があります *%systemdrive%\inetpub\wwwroot*を付与するを実行しているアカウントにアクセス許可を変更します。 このように設定しない場合、ビルド後のイベントが失敗する場合があります。 代わりに、ACL の設定はそのままにして、SDK コマンド プロンプトを管理者として実行することもできます。

## <a name="to-build-the-sample-using-visual-studio"></a>Visual Studio を使用してサンプルをビルドするには

1. **ファイル** メニューの選択 Visual Studio で**オープン** > **プロジェクト/ソリューション**します。 サンプルをインストールしたディレクトリの言語固有のサブディレクトリに移動し、Visual Studio でソリューションを開く .sln ファイルのアイコンをダブルクリックします。

1. **ビルド**メニューの **ソリューションのリビルド**します。

   クライアント プログラムが client\bin にビルドされ、サービス プログラムが service\bin にビルドされます。 サービス プログラム ファイルもにコピーする場合は、サービスは IIS でホストされる、 *servicemodelsamples* ディレクトリとその *\bin* サブディレクトリ。

> [!NOTE]
> %systemdrive%\inetpub\wwwroot 上の ACL を、実行中のアカウントに変更権限を付与するように設定する必要があります。 このように設定しない場合、ビルド後のイベントが失敗する場合があります。 代わりに、ACL の設定はそのままにして、SDK コマンド プロンプトまたは Visual Studio を管理者として実行することもできます。 Visual Studio の一部のアクション (デバッガを ASP.Net ワーカー プロセスにアタッチするアクションなど) では、さらに管理特権が必要です。

## <a name="setup-batch-files-and-scripts"></a>セットアップ バッチ ファイルとスクリプト
 Setup.exe、Cleanup.exe バッチ ファイルやスクリプトする必要がありますと、開発者コマンド プロンプトからが for Visual Studio を実行します。 いくつかのセットアップ ファイルとクリーンアップ ファイルは、管理特権が必要なタスクを実行します。したがって、これらのファイルは管理特権で起動する必要があります。

## <a name="important-security-information-about-metadata-endpoints"></a>メタデータ エンドポイントに関する重要なセキュリティ情報
 可能性のある機密性の高いサービス メタデータが誤って漏洩を防ぐためには、Windows Communication Foundation (WCF) サービスの既定の構成ではメタデータの公開を無効にします。 この動作は、既定の設定ではセキュリティで保護されますが、同時に、サービスの構成の中でメタデータ発行の動作が明示的に有効化されない限り、サービスの呼び出しに必要なクライアント コードをメタデータ インポート ツール (Svcutil.exe など) を使用して生成できないことも意味します。 サンプルでの試みを容易にするため、ほとんどすべてのサンプルでは、セキュリティ保護されていないメタデータ公開エンドポイントを公開しています。 このようなエンドポイントを利用するコンシューマーは、匿名で、認証を受けていない可能性もあります。したがって、エンドポイントを配置する前には注意を払い、サービスのメタデータをパブリックに開示することが適切であることを確認する必要があります。 サービス メタデータの公開の詳細については、次を参照してください。、[メタデータ公開動作](../../../../docs/framework/wcf/samples/metadata-publishing-behavior.md)サンプル。 参照してください、[メタデータ エンドポイントのセキュリティで保護されたカスタム](../../../../docs/framework/wcf/samples/custom-secure-metadata-endpoint.md)メタデータ エンドポイントをセキュリティで保護するサンプルのサンプルです。

## <a name="exception-handling"></a>例外処理
 通常、コードではサンプルの主題を重視するので、これらのサンプルに例外処理は含まれていません。 例外処理の詳細については、次を参照してください。、[予想例外](../../../../docs/framework/wcf/samples/expected-exceptions.md)サンプル。

## <a name="regenerating-clients-and-configuration-with-svcutil"></a>Svcutil を使用したクライアントと構成の再生成
 使用することができます、 [ServiceModel メタデータ ユーティリティ ツール (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)をクライアント コードとほとんどのサンプルの構成を再生成します。 一部のサンプルでは、構成を手動で編集する必要があります。 たとえば、Svcutil.exe を使用して、クライアント証明書の資格情報を使用するサンプルの構成を再生成する場合は、以前に構成された資格情報を手動で指定する必要があります。 一部のサンプルでは、生成コードに影響を与える、Svcutil.exe の特定のオプションを使用します。これらのオプションは、そうした特定のサンプルのトピックで指定されます。

### <a name="to-regenerate-the-client-and-configuration-files"></a>クライアントと構成ファイルを再生成するには

1. SDK コマンド プロンプトを開き、サンプルのインストール ディレクトリに存在する言語固有のサブディレクトリに移動します。

2. サービスが Web ホスト型の場合は、次のコマンドを使用します。

    ```
    svcutil.exe /n:"http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples" http://localhost/servicemodelsamples/service.svc/mex /out:generatedClient.cs
    ```

     サービスが自己ホスト型の場合は、次のコマンドを使用します。

    ```
    svcutil.exe /n:"http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples" http://localhost:8000/servicemodelsamples/service.svc/mex /out:generatedClient.cs
    ```

     置換`http://localhost:8000/ServiceModelSamples/service.svc/mex`自己ホスト型サービスの mex エンドポイントのアドレスを使用します。

     Visual Basic の型でクライアントを生成するには、次のコマンドを使用します。

    ```
    svcutil.exe /n:"http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples" http://localhost/servicemodelsamples/service.svc/mex /l:vb /out:generatedClient.vb
    ```

     サービスが自己ホスト型の場合は、次のコマンドを使用します。

    ```
    svcutil.exe /n:"http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples" http://localhost:8000/servicemodelsamples/service.svc/mex /l:vb /out:generatedClient.vb
    ```

    > [!NOTE]
    > クライアント構成の生成の追加をスキップする、 **/noConfig**オプション。

## <a name="see-also"></a>関連項目

- [Windows Communication Foundation サンプルの実行](../../../../docs/framework/wcf/samples/running-the-samples.md)
- [ServiceModel メタデータ ユーティリティ ツール (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)
