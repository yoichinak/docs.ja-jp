---
title: 'チュートリアル: 基本的な Windows Communication Foundation サービスをホストして実行する'
ms.date: 03/19/2019
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF services [WCF]
- WCF services [WCF], running
ms.assetid: 31774d36-923b-4e2d-812e-aa190127266f
ms.openlocfilehash: 984c5e73a8efc4e9c2d487485267868ffa2f60f3
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70928724"
---
# <a name="tutorial-host-and-run-a-basic-windows-communication-foundation-service"></a>チュートリアル: 基本的な Windows Communication Foundation サービスをホストして実行する

このチュートリアルでは、基本的な Windows Communication Foundation (WCF) アプリケーションを作成するために必要な5つのタスクについて説明します。 チュートリアルの概要については、 [「チュートリアル:Windows Communication Foundation アプリケーション](getting-started-tutorial.md)の概要」をご覧ください。

WCF アプリケーションを作成するための次のタスクは、コンソールアプリケーションで WCF サービスをホストすることです。 WCF サービスは1つ以上の*エンドポイント*を公開し、それぞれが1つ以上のサービス操作を公開します。 サービスエンドポイントは、次の情報を指定します。

- サービスを検索できるアドレス。
- クライアントがサービスと通信する方法を説明する情報を格納しているバインディング。 
- サービスがクライアントに提供する機能を定義するコントラクト。

このチュートリアルでは、次の作業を行う方法について説明します。
> [!div class="checklist"]
>
> - WCF サービスをホストするためのコンソールアプリプロジェクトを作成して構成します。
> - WCF サービスをホストするコードを追加します。
> - 構成ファイルを更新します。
> - WCF サービスを開始し、実行されていることを確認します。

## <a name="create-and-configure-a-console-app-project-for-hosting-the-service"></a>サービスをホストするためのコンソールアプリプロジェクトを作成して構成する

1. Visual Studio でコンソールアプリプロジェクトを作成します。 
 
    1. **[ファイル]** メニューの [**プロジェクト/ソリューション**を**開く** > ] を選択し、前の作業で作成した**gettingstarted** (*gettingstarted. .sln*) を参照します。 **[開く]** を選択します。

    2. **[表示]** メニューの **[ソリューションエクスプローラー]** をクリックします。
    
    3. **[ソリューションエクスプローラー]** ウィンドウで、 **[gettingstarted]** ソリューション (最上位ノード) を選択し、ショートカットメニューの [**新しいプロジェクト**の**追加** > ] をクリックします。 

    4. **[新しいプロジェクトの追加]** ウィンドウの左側にある **[Visual C# ]** または **[Visual Basic]** の下にある **[Windows デスクトップ]** カテゴリを選択します。 

    5. **[コンソールアプリ (.NET Framework)]** テンプレートを選択し、**名前**として「 *gettingon host* 」と入力します。 **[OK]** を選択します。

2. **Gettingのホスト**プロジェクトに参照を追加して、 **Getting: lib**プロジェクトに追加します。 

    1. **[ソリューションエクスプローラー]** ウィンドウで、 **Gettingのホスト**プロジェクトの下にある **[参照]** フォルダーを選択し、ショートカットメニューの **[参照の追加]** を選択します。 

    2. **[参照の追加]** ダイアログボックスで、ウィンドウの左側にある **[プロジェクト]** の下にある **[ソリューション]** を選択します。 
 
    3. ウィンドウの中央のセクションで [ **Getting] lib**を選択し、[ **OK]** を選択します。 

       このアクションにより、gettingの**lib**プロジェクトで定義されている型が**Gettingのホスト**プロジェクトで使用できるようになります。

3. **Gettingのホスト**プロジェクトで、 <xref:System.ServiceModel>アセンブリに参照を追加します。 

    1. **[ソリューションエクスプローラー]** ウィンドウで、 **Gettingのホスト**プロジェクトの下にある **[参照]** フォルダーを選択し、ショートカットメニューの **[参照の追加]** を選択します。
    
    2. **[参照の追加]** ウィンドウの左側にある **[アセンブリ]** で、 **[フレームワーク]** を選択します。 

    3. **[System.servicemodel]** を選択し、[ **OK]** を選択します。 
    
    4. [**ファイル** > ] **[すべて保存]** の順に選択して、ソリューションを保存します。

## <a name="add-code-to-host-the-service"></a>サービスをホストするコードを追加する

サービスをホストするには、次の手順を実行するコードを追加します。 

1. ベースアドレスの URI を作成します。
2. サービスをホストするためのクラスインスタンスを作成します。
3. サービスエンドポイントを作成します。
4. メタデータ交換を有効にします。
5. サービスホストを開いて、受信メッセージをリッスンします。
  
コードに次の変更を加えます。

1. **GettingProgram.cs ホスト**プロジェクトのファイルまたは module1.vb ファイルを開き、そのコードを次のコードに置き換え**ます。**

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
    
    このコードの動作については、「[サービスホスティングプログラムの手順](#service-hosting-program-steps)」を参照してください。

2. プロジェクトのプロパティを更新します。

   1. **[ソリューションエクスプローラー]** ウィンドウで、[ **Getting] ホスト**フォルダーを選択し、ショートカットメニューの **[プロパティ]** をクリックします。

   2. **[Gettingon ホスト]** のプロパティ ページで、 **[アプリケーション]** タブを選択します。

      - プロジェクトC#の場合は、 **[スタートアップオブジェクト]** ボックスの一覧から [ **getting]** を選択します。

      - Visual Basic プロジェクトの場合は、 **[スタートアップオブジェクト]** ボックスの一覧から **[Service. プログラム]** を選択します。

   3. **[ファイル]** メニューの **[すべてを保存]** をクリックします。

## <a name="verify-the-service-is-working"></a>サービスが動作していることを確認する

1. ソリューションをビルドし、Visual Studio 内から**Gettingのホスト**コンソールアプリケーションを実行します。 

    サービスは、管理者特権で実行する必要があります。 Visual Studio を管理者特権で開いたので、Visual Studio で**Gettingon ホスト**を実行すると、アプリケーションも管理者特権で実行されます。 別の方法として、新しいコマンドプロンプトを管理者として開くこともできます (ショートカットメニューから [**その他** > の**実行**] を選択して、**その中で実行します)** 。

2. Web ブラウザーを開き、で`http://localhost:8000/GettingStarted/CalculatorService`サービスのページを参照します。
   
   > [!NOTE]
   > このようなサービスでは、リッスンするコンピューターに HTTP アドレスを登録するための適切なアクセス許可が必要です。 管理者アカウントにはこのアクセス許可がありますが、管理者以外のアカウントの場合は、HTTP 名前空間へのアクセス許可を付与する必要があります。 名前空間の予約を構成する方法については、「[HTTP および HTTPS の構成](feature-details/configuring-http-and-https.md)」を参照してください。 

## <a name="service-hosting-program-steps"></a>サービスホスティングプログラムの手順

サービスをホストするために追加したコードの手順は、次のように記述されています。

- **手順 1**:サービスのベースアドレスを`Uri`保持するクラスのインスタンスを作成します。 ベースアドレスを含む URL には、サービスを識別する省略可能な URI があります。 ベースアドレスは、のよう`<transport>://<machine-name or domain><:optional port #>/<optional URI segment>`に書式設定されます。 電卓サービスのベースアドレスは、HTTP トランスポート、localhost、ポート8000、および URI セグメント (GettingStarted) を使用します。

- **手順 2**:サービスをホストするため<xref:System.ServiceModel.ServiceHost>に使用するクラスのインスタンスを作成します。 コンストラクターは、サービスコントラクトを実装するクラスの型とサービスのベースアドレスの2つのパラメーターを受け取ります。

- **手順 3**:<xref:System.ServiceModel.Description.ServiceEndpoint> インスタンスを作成します。 サービス エンドポイントは、アドレス、バインディング、およびサービス コントラクトから構成されます。 <xref:System.ServiceModel.Description.ServiceEndpoint>コンストラクターは、サービスコントラクトインターフェイスの型、バインディング、およびアドレスで構成されます。 サービス コントラクトは、サービス型に定義および実装した `ICalculator` です。 このサンプル<xref:System.ServiceModel.WSHttpBinding>のバインドは、組み込みのバインドであり、WS-* 仕様に準拠するエンドポイントに接続されています。 WCF バインディングの詳細については、「 [wcf バインディングの概要](bindings-overview.md)」を参照してください。 アドレスをベースアドレスに追加して、エンドポイントを識別します。 このコードでは、このアドレスを計算し、そのエンドポイントの完全修飾アドレス`http://localhost:8000/GettingStarted/CalculatorService`をとして指定します。

    > [!IMPORTANT]
    > .NET Framework バージョン4以降では、サービスエンドポイントの追加は省略可能です。 これらのバージョンでは、コードまたは構成を追加しないと、サービスによって実装されたベースアドレスとコントラクトの組み合わせごとに既定のエンドポイントが1つ追加されます。 既定のエンドポイントの詳細については、「[エンドポイントアドレスの指定](specifying-an-endpoint-address.md)」を参照してください。 既定のエンドポイント、バインディング、および動作の詳細については、「簡略化された[構成](simplified-configuration.md)と[WCF サービスの簡略化](samples/simplified-configuration-for-wcf-services.md)された構成」を参照してください。

- **手順 4**:メタデータ交換を有効にします。 クライアントは、メタデータ交換を使用して、サービス操作を呼び出すためのプロキシを生成します。 メタデータ交換を有効にする<xref:System.ServiceModel.Description.ServiceMetadataBehavior>には、インスタンス<xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled>を作成`true`し、そのプロパティ`ServiceMetadataBehavior`をに設定<xref:System.ServiceModel.Description.ServiceDescription.Behaviors%2A>して、 <xref:System.ServiceModel.ServiceHost>オブジェクトをインスタンスのコレクションに追加します。

- **手順 5**:を<xref:System.ServiceModel.ServiceHost>開き、受信メッセージをリッスンします。 アプリケーションは、 **enter**キーを押すまで待機します。 アプリケーションがインスタンス<xref:System.ServiceModel.ServiceHost>化されると、try/catch ブロックが実行されます。 によって<xref:System.ServiceModel.ServiceHost>スローされる例外を安全にキャッチする方法の詳細については、「 [Close と Abort を使用して WCF クライアントリソースを解放する](samples/use-close-abort-release-wcf-client-resources.md)」を参照してください。

> [!IMPORTANT]
> WCF サービスライブラリを追加すると、サービスホストを起動してデバッグする場合、Visual Studio はそれをホストします。 競合を回避するために、Visual Studio が WCF サービスライブラリをホストしないようにすることができます。 
>
> 1. **ソリューションエクスプローラー**で**Gettingの lib**プロジェクトを選択し、ショートカットメニューの **[プロパティ]** を選択します。
> 2. **[Wcf オプション]** を選択し、**同じソリューションで別のプロジェクトをデバッグするときに [wcf サービスホストを開始する**] チェックボックスをオフにします。

## <a name="next-steps"></a>次の手順

このチュートリアルでは、次の作業を行う方法を学びました。
> [!div class="checklist"]
>
> - WCF サービスをホストするためのコンソールアプリプロジェクトを作成して構成します。
> - WCF サービスをホストするコードを追加します。
> - 構成ファイルを更新します。
> - WCF サービスを開始し、実行されていることを確認します。

次のチュートリアルに進み、WCF クライアントを作成する方法を学習してください。

> [!div class="nextstepaction"]
> [チュートリアル: WCF クライアントを作成する](how-to-create-a-wcf-client.md)
