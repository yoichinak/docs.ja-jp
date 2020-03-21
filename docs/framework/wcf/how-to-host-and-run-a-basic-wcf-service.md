---
title: 'チュートリアル: 基本的な Windows コミュニケーション ファウンデーション サービスをホストして実行する'
ms.date: 03/19/2019
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF services [WCF]
- WCF services [WCF], running
ms.assetid: 31774d36-923b-4e2d-812e-aa190127266f
ms.openlocfilehash: 30eb86987b83427b94c6fff22755cde3d73dd9f0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184084"
---
# <a name="tutorial-host-and-run-a-basic-windows-communication-foundation-service"></a>チュートリアル: 基本的な Windows コミュニケーション ファウンデーション サービスをホストして実行する

このチュートリアルでは、基本的な Wcf (WCF) アプリケーションを作成するために必要な 5 つのタスクの 3 つ目について説明します。 チュートリアルの概要については、「[チュートリアル: Windows コミュニケーションファウンデーション アプリケーションの概要](getting-started-tutorial.md)」を参照してください。

WCF アプリケーションを作成するための次のタスクは、コンソール アプリケーションで WCF サービスをホストすることです。 WCF サービスは、 1 つ以上のエンドポイントを公開し *、* 各エンドポイントは 1 つ以上のサービス操作を公開します。 サービス エンドポイントは、次の情報を指定します。

- サービスを検索できるアドレス。
- クライアントがサービスと通信する方法を説明する情報を含むバインディング。
- サービスがクライアントに提供する機能を定義するコントラクト。

このチュートリアルでは、以下の内容を学習します。
> [!div class="checklist"]
>
> - WCF サービスをホストするためのコンソール アプリ プロジェクトを作成して構成します。
> - WCF サービスをホストするコードを追加します。
> - 構成ファイルを更新します。
> - WCF サービスを起動し、実行中であることを確認します。

## <a name="create-and-configure-a-console-app-project-for-hosting-the-service"></a>サービスをホストするためのコンソール アプリ プロジェクトを作成および構成する

1. Visual Studio でコンソール アプリ プロジェクトを作成します。

    1. [**ファイル]** メニューの [**プロジェクト/ソリューション**を**開く** > ] を選択し、以前に作成した **[はじめに]** ソリューション (*GettingStarted.sln*) を参照します。 **[開く]** を選択します。

    2. [**表示**] メニューの [**ソリューション エクスプローラ**] をクリックします。

    3. [**ソリューション エクスプローラー** ] ウィンドウで **、"はじめに"** ソリューション (最上位ノード) を選択し、ショートカット メニューから **[新しいプロジェクト**の**追加** > ] を選択します。

    4. [**新しいプロジェクトの追加**] ウィンドウの左側で **、[Visual C#** または Visual **Basic]** の下にある **[Windows デスクトップ**] カテゴリを選択します。

    5. コンソール**アプリケーション (.NET Framework)** テンプレートを選択し、**名前***に「開始開始ホスト」* と入力します。 **[OK]** を選択します。

2. **プロジェクトに**参照を追加します。 **GettingStartedLib**

    1. **[ソリューション エクスプローラー** ] ウィンドウで **、GettingStartedHost**プロジェクトの下にある **[参照**] フォルダーを選択し、ショートカット メニューの **[参照の追加**] を選択します。

    2. [**参照の追加]** ダイアログの左側の [**プロジェクト**] で、[**ソリューション**] を選択します。

    3. ウィンドウの中央のセクションで [**開始] を**選択し **、[OK]** を選択します。

       このアクションにより、次の操作を**行**うと、プロジェクトで定義された型が**使用**できるようになります。

3. **アセンブリに参照を追加します**<xref:System.ServiceModel>。

    1. **[ソリューション エクスプローラー** ] ウィンドウで **、GettingStartedHost**プロジェクトの下にある **[参照**] フォルダーを選択し、ショートカット メニューの **[参照の追加**] を選択します。

    2. [**参照の追加**] ウィンドウの左側にある **[アセンブリ**] で、[**フレームワーク**] を選択します。

    3. [**システム.サービスモデル**] を選択し **、[OK]** を選択します。

    4. [ファイルをすべて保存] を選択してソリューション**を** > **保存**します。

## <a name="add-code-to-host-the-service"></a>サービスをホストするコードを追加する

サービスをホストするには、次の手順を実行するコードを追加します。

1. ベース アドレスの URI を作成します。
2. サービスをホストするためのクラス インスタンスを作成します。
3. サービス エンドポイントを作成します。
4. メタデータ交換を有効にします。
5. サービス ホストを開いて、受信メッセージをリッスンします。
  
コードに次の変更を加えます。

1. **Program.cs**または**Program.cs** **Module1.vb**ファイルを開き、次のコードを使用してコードを置き換えます。

    ```csharp
    using System;
    using System.ServiceModel;
    using System.ServiceModel.Description;
    using GettingStartedLib;

    namespace GettingStartedHost
    {
        class Program
        {
            static void Main(string[] args)
            {
                // Step 1: Create a URI to serve as the base address.
                Uri baseAddress = new Uri("http://localhost:8000/GettingStarted/");

                // Step 2: Create a ServiceHost instance.
                ServiceHost selfHost = new ServiceHost(typeof(CalculatorService), baseAddress);

                try
                {
                    // Step 3: Add a service endpoint.
                    selfHost.AddServiceEndpoint(typeof(ICalculator), new WSHttpBinding(), "CalculatorService");

                    // Step 4: Enable metadata exchange.
                    ServiceMetadataBehavior smb = new ServiceMetadataBehavior();
                    smb.HttpGetEnabled = true;
                    selfHost.Description.Behaviors.Add(smb)    ;

                    // Step 5: Start the service.
                    selfHost.Open();
                    Console.WriteLine("The service is ready.");

                    // Close the ServiceHost to stop the service.
                    Console.WriteLine("Press <Enter> to terminate the service.");
                    Console.WriteLine();
                    Console.ReadLine();
                    selfHost.Close();
                }
                catch (CommunicationException ce)
                {
                    Console.WriteLine("An exception occurred: {0}", ce.Message);
                    selfHost.Abort();
                }
            }
        }
    }
    ```

    ```vb
    Imports System.ServiceModel
    Imports System.ServiceModel.Description
    Imports GettingStartedLib.GettingStartedLib

    Module Service

        Class Program
            Shared Sub Main()
                ' Step 1: Create a URI to serve as the base address.
                Dim baseAddress As New Uri("http://localhost:8000/GettingStarted/")

                ' Step 2: Create a ServiceHost instance.
                Dim selfHost As New ServiceHost(GetType(CalculatorService), baseAddress)
               Try

                    ' Step 3: Add a service endpoint.
                    selfHost.AddServiceEndpoint( _
                        GetType(ICalculator), _
                        New WSHttpBinding(), _
                        "CalculatorService")

                    ' Step 4: Enable metadata exchange.
                    Dim smb As New ServiceMetadataBehavior()
                    smb.HttpGetEnabled = True
                    selfHost.Description.Behaviors.Add(smb)

                    ' Step 5: Start the service.
                    selfHost.Open()
                    Console.WriteLine("The service is ready.")

                    ' Close the ServiceHost to stop the service.
                    Console.WriteLine("Press <Enter> to terminate the service.")
                    Console.WriteLine()
                    Console.ReadLine()
                    selfHost.Close()

                Catch ce As CommunicationException
                    Console.WriteLine("An exception occurred: {0}", ce.Message)
                    selfHost.Abort()
                End Try
            End Sub
        End Class

    End Module
    ```

    このコードの動作については、「[サービス ホスティング プログラムの手順](#service-hosting-program-steps)」を参照してください。

2. プロジェクトプロパティを更新します。

   1. **[ソリューション エクスプローラー** ] ウィンドウで **、"GettingStartedHost"** フォルダーを選択し、ショートカット メニューの **[プロパティ]** をクリックします。

   2. [**開始開始ホスト**のプロパティ] ページで、[**アプリケーション**] タブを選択します。

      - C# プロジェクトの場合は、[**スタートアップ オブジェクト**] リスト**から [開始開始ホスト.プログラム**] を選択します。

      - Visual Basic プロジェクトの場合は、[スタートアップ**オブジェクト**] ボックスの一覧から [**サービス.プログラム**] を選択します。

   3. [**ファイル]** メニューの [**すべて保存]** をクリックします。

## <a name="verify-the-service-is-working"></a>サービスが動作していることを確認する

1. ソリューションをビルドし、Visual Studio 内から**開始開始ホスト**コンソール アプリケーションを実行します。

    サービスは管理者権限で実行する必要があります。 管理者特権で Visual Studio を開いたので、Visual Studio で**GettingStartedHost**を実行すると、アプリケーションも管理者特権で実行されます。 代わりに、新しいコマンド プロンプトを管理者として開き (ショートカット メニューから [**管理者として****実行を増やす** > ] を選択) し、その中で**GettingStartedHost.exe を**実行することもできます。

2. Web ブラウザを開き、 でサービスのページを`http://localhost:8000/GettingStarted/CalculatorService`参照します。

   > [!NOTE]
   > このようなサービスには、リッスンするためにコンピュータに HTTP アドレスを登録するための適切なアクセス許可が必要です。 管理者アカウントにはこのアクセス許可がありますが、管理者以外のアカウントの場合は、HTTP 名前空間へのアクセス許可を付与する必要があります。 名前空間の予約を構成する方法については、「[Configuring HTTP and HTTPS](feature-details/configuring-http-and-https.md)」 (HTTP と HTTPS を構成する) を参照してください。

## <a name="service-hosting-program-steps"></a>サービス ホスティング プログラムの手順

サービスをホストするために追加したコードの手順は、次のとおりです。

- **手順 1**: サービスの`Uri`ベース アドレスを保持するクラスのインスタンスを作成します。 ベース アドレスを含む URL には、サービスを識別する省略可能な URI があります。 ベース アドレスは、次のように書式設定されます。 `<transport>://<machine-name or domain><:optional port #>/<optional URI segment>` 計算機サービスのベース アドレスは、HTTP トランスポート、ローカル ホスト、ポート 8000、および URI セグメントである [はじめに] を使用します。

- **手順 2**: サービスの<xref:System.ServiceModel.ServiceHost>ホストに使用するクラスのインスタンスを作成します。 コンストラクターは、サービス コントラクトを実装するクラスの型とサービスのベース アドレスという 2 つのパラメーターを受け取ります。

- **ステップ 3**:<xref:System.ServiceModel.Description.ServiceEndpoint>インスタンスを作成します。 サービス エンドポイントは、アドレス、バインディング、およびサービス コントラクトから構成されます。 コンストラクター<xref:System.ServiceModel.Description.ServiceEndpoint>は、サービス コントラクト インターフェイス型、バインディング、およびアドレスで構成されます。 サービス コントラクトは、サービス型に定義および実装した `ICalculator` です。 このサンプルのバインディングは<xref:System.ServiceModel.WSHttpBinding>、組み込みバインディングであり、WS-* 仕様に準拠するエンドポイントに接続します。 WCF バインドの詳細については、「 [WCF バインドの概要](bindings-overview.md)」を参照してください。 アドレスをベース アドレスに追加して、エンドポイントを識別します。 コードでは、アドレスを CalculatorService として指定し、エンドポイントの完全修飾アドレス`http://localhost:8000/GettingStarted/CalculatorService`を .

    > [!IMPORTANT]
    > NET Framework バージョン 4 以降では、サービス エンドポイントの追加はオプションです。 これらのバージョンでは、コードまたは構成を追加しない場合、WCF は、ベース アドレスとサービスによって実装されるコントラクトの組み合わせごとに 1 つの既定のエンドポイントを追加します。 既定のエンドポイントの詳細については、エンドポイント[アドレスの指定を](specifying-an-endpoint-address.md)参照してください。 既定のエンドポイント、バインド、および動作の詳細については、「 WCF サービス[の構成の簡略化](simplified-configuration.md)」および「[簡易構成](samples/simplified-configuration-for-wcf-services.md)」を参照してください。

- **ステップ 4:** メタデータの交換を有効にします。 クライアントは、メタデータ交換を使用して、サービス操作を呼び出すプロキシを生成します。 メタデータ交換を有効にするには、インスタンスを<xref:System.ServiceModel.Description.ServiceMetadataBehavior>作成し、その<xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled>プロパティを`true`に設定し`ServiceMetadataBehavior`、オブジェクトを<xref:System.ServiceModel.Description.ServiceDescription.Behaviors%2A>インスタンスのコレクション<xref:System.ServiceModel.ServiceHost>に追加します。

- **ステップ5:** 受信<xref:System.ServiceModel.ServiceHost>メッセージをリッスンするために開きます。 アプリケーションは **、Enter**キーを押すまで待機します。 アプリケーションは、 の<xref:System.ServiceModel.ServiceHost>インスタンスを作成した後、try/catch ブロックを実行します。 によってスローされる<xref:System.ServiceModel.ServiceHost>例外を安全にキャッチする方法の詳細については、「 [[閉じる] および [中止] を使用して WCF クライアント リソースを解放する](samples/use-close-abort-release-wcf-client-resources.md)」を参照してください。

> [!IMPORTANT]
> WCF サービス ライブラリを追加すると、サービス ホストを起動してデバッグする場合は、Visual Studio によってそのライブラリがホストされます。 競合を回避するには、Visual Studio が WCF サービス ライブラリをホストしないようにします。
>
> 1. **ソリューション エクスプローラー**で **[FromFromLib]** プロジェクトを選択し、ショートカット メニューの **[プロパティ]** をクリックします。
> 2. [WCF**オプション]** を選択し、[**同じソリューションで別のプロジェクトをデバッグするときに WCF サービス ホストを開始する**] チェック ボックスをオフにします。

## <a name="next-steps"></a>次のステップ

このチュートリアルでは、以下の内容を学習しました。
> [!div class="checklist"]
>
> - WCF サービスをホストするためのコンソール アプリ プロジェクトを作成して構成します。
> - WCF サービスをホストするコードを追加します。
> - 構成ファイルを更新します。
> - WCF サービスを起動し、実行中であることを確認します。

WCF クライアントを作成する方法については、次のチュートリアルに進みます。

> [!div class="nextstepaction"]
> [チュートリアル: WCF クライアントを作成する](how-to-create-a-wcf-client.md)
