---
title: 'チュートリアル: ホストおよび基本的な Windows Communication Foundation サービスの実行'
ms.date: 03/19/2019
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF services [WCF]
- WCF services [WCF], running
ms.assetid: 31774d36-923b-4e2d-812e-aa190127266f
ms.openlocfilehash: 38fd9b89e2719be8ce4d33b1b50f68171d587369
ms.sourcegitcommit: 3630c2515809e6f4b7dbb697a3354efec105a5cd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/25/2019
ms.locfileid: "58410096"
---
# <a name="tutorial-host-and-run-a-basic-windows-communication-foundation-service"></a>チュートリアル: ホストおよび基本的な Windows Communication Foundation サービスの実行

このチュートリアルでは、3 番目の基本的な Windows Communication Foundation (WCF) アプリケーションを作成するために必要な 5 つのタスクについて説明します。 チュートリアルの概要については、次を参照してください。[チュートリアル。Windows Communication Foundation アプリケーションの概要](getting-started-tutorial.md)します。

WCF アプリケーションを作成するための次のタスクでは、コンソール アプリケーションで WCF サービスをホストします。 WCF サービスは、1 つまたは複数公開*エンドポイント*、1 つまたは複数のサービス操作を公開します。 サービス エンドポイントは、次の情報を指定します。 
- サービスが得られるアドレスです。
- クライアントがサービスと通信する必要がある方法を説明する情報を含んでいるバインディング。 
- サービスがクライアントに提供する機能を定義するコントラクト。

このチュートリアルでは、次の作業を行う方法について説明します。
> [!div class="checklist"]
> - 作成し、WCF サービスをホストするためのコンソール アプリ プロジェクトを構成します。
> - WCF サービスをホストするためのコードを追加します。
> - 構成ファイルを更新します。
> - WCF サービスを開始し、確認が実行されています。


## <a name="create-and-configure-a-console-app-project-for-hosting-the-service"></a>作成し、サービスをホストするためのコンソール アプリ プロジェクトを構成します。

1. Visual Studio でコンソール アプリ プロジェクトを作成します。 
 
    1. **ファイル**メニューの **オープン** > **プロジェクト/ソリューション**を見つけて、 **GettingStarted**ソリューションを以前に作成した (*GettingStarted.sln*)。 **[開く]** を選択します。

    2. **ビュー**メニューの **ソリューション エクスプ ローラー**します。
    
    3. **ソリューション エクスプ ローラー**ウィンドウで、 **GettingStarted**ソリューション (最上位ノード) し、選択**追加** > **の新しいプロジェクト**ショートカット メニューから。 

    4. **新しいプロジェクトの追加**ウィンドウで、左側にある、選択、 **Windows デスクトップ**カテゴリ  **Visual C#** または**Visual Basic**. 

    5. 選択、**コンソール アプリ (.NET Framework)** テンプレート、入力と*GettingStartedHost*の**名前**します。 **[OK]** を選択します。

2. 参照を追加、 **GettingStartedHost**プロジェクトを**GettingStartedLib**プロジェクト。 

    1. **ソリューション エクスプ ローラー**ウィンドウで、**参照**の下のフォルダー、 **GettingStartedHost**プロジェクトを選び**参照の追加**ショートカット メニューから。 

    2. **参照の追加**ダイアログで、**プロジェクト**ウィンドウの左側にある、次のように選択します。**ソリューション**します。 
 
    3. 選択**GettingStartedLib**選択し、ウィンドウの中央のセクションで**OK**します。 

       この操作によってで定義された型、 **GettingStartedLib**プロジェクトに使用可能な**GettingStartedHost**プロジェクト。

3. 参照を追加、 **GettingStartedHost**プロジェクトを<xref:System.ServiceModel>アセンブリ。 

    1. **ソリューション エクスプ ローラー**ウィンドウで、**参照**の下のフォルダー、 **GettingStartedHost**プロジェクトを選び**参照の追加**ショートカット メニューから。
    
    2. **参照の追加**ウィンドウで、**アセンブリ**ウィンドウの左側にある、次のように選択します。 **Framework**します。 

    3. 選択**System.ServiceModel**、し、 **OK**します。 
    
    4. ソリューションを選択して保存**ファイル** > **すべて保存**します。

## <a name="add-code-to-host-the-service"></a>サービスをホストするコードを追加します。

サービスをホストするには、次の手順を実行するコードを追加します。 
   1. ベース アドレスの URI を作成します。
   2. サービスをホストするためのクラスのインスタンスを作成します。
   3. サービス エンドポイントを作成します。
   4. メタデータ交換を有効にします。
   5. 受信メッセージをリッスンするサービス ホストを開きます。
  
コードを次の変更。

1. 開く、 **Program.cs**または**Module1.vb**ファイル、 **GettingStartedHost**プロジェクトし、そのコードを次のコードに置き換えます。

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
    
    このコードの動作については、次を参照してください。[プログラムの手順をホストしているサービス](#service-hosting-program-steps)します。


2. プロジェクトのプロパティを更新します。

   1. **ソリューション エクスプ ローラー**ウィンドウで、 **GettingStartedHost**フォルダー、および選択**プロパティ**ショートカット メニューから。

   2. **GettingStartedHost**プロパティ ページで、**アプリケーション** タブ。

      - C#プロジェクトで、 **GettingStartedHost.Program**から、**スタートアップ オブジェクト**一覧。

      - Visual Basic プロジェクトでは、次のように選択します。 **Service.Program**から、**スタートアップ オブジェクト**一覧。

   3. **ファイル**メニューの **すべて保存**します。


## <a name="verify-the-service-is-working"></a>サービスが動作を確認します。

1. ソリューションをビルドし、実行、 **GettingStartedHost**コンソール Visual Studio 内からアプリケーション。 

    サービスは、管理者特権で実行する必要があります。 実行すると、管理者特権で Visual Studio が開いているため**GettingStartedHost** Visual Studio で、アプリケーションが管理者特権もで実行します。 代わりに、管理者として新しいコマンド プロンプトを開くことができます (選択**詳細** > **管理者として実行**ショートカット メニューから) 実行**GettingStartedHost.exe**内。

2. Web ブラウザーを開き、サービスのページを参照`http://localhost:8000/GettingStarted/CalculatorService`します。
   
   > [!NOTE]
   > このいずれかなどのサービスには、リッスンを行うコンピューター上で HTTP アドレスを登録する適切なアクセス許可が必要です。 管理者アカウントにはこのアクセス許可がありますが、管理者以外のアカウントの場合は、HTTP 名前空間へのアクセス許可を付与する必要があります。 名前空間の予約を構成する方法については、「[Configuring HTTP and HTTPS](feature-details/configuring-http-and-https.md)」 (HTTP と HTTPS を構成する) を参照してください。 


## <a name="service-hosting-program-steps"></a>サービスのホスト プログラムのステップ

サービスは次のように説明されているホストに追加したコードの手順:

- **手順 1.**:インスタンスを作成、`Uri`サービスのベース アドレスを保持するクラス。 ベース アドレスを含む URL が、省略可能なサービスを識別する URI。 ベース アドレスは次の形式:`<transport>://<machine-name or domain><:optional port #>/<optional URI segment>`します。 電卓サービスのベース アドレスは、HTTP トランスポート、localhost、ポート 8000、および URI セグメント、GettingStarted を使用します。

- **手順 2**:インスタンスを作成、<xref:System.ServiceModel.ServiceHost>クラスは、サービスをホストするために使用します。 コンス トラクターは 2 つのパラメーター: サービス コントラクトとサービスのベース アドレスを実装するクラスの型。

- **手順 3**:<xref:System.ServiceModel.Description.ServiceEndpoint> インスタンスを作成します。 サービス エンドポイントは、アドレス、バインディング、およびサービス コントラクトから構成されます。 <xref:System.ServiceModel.Description.ServiceEndpoint>コンス トラクターは、サービス コントラクト インターフェイスの型、バインディング、およびアドレスで構成されます。 サービス コントラクトは、サービス型に定義および実装した `ICalculator` です。 このサンプルのバインディングが<xref:System.ServiceModel.WSHttpBinding>、組み込みのバインディングし、は、ws-に準拠するエンドポイントに接続 * の仕様。 WCF バインドの詳細については、次を参照してください。 [WCF のバインディングの概要](bindings-overview.md)します。 エンドポイントを識別するためにベース アドレスには、アドレスを追加します。 コードは、CalculatorService ととしてエンドポイントの完全修飾アドレスとしてアドレスを指定します`http://localhost:8000/GettingStarted/CalculatorService`します。

    > [!IMPORTANT]
    > .NET Framework バージョン 4 以降、サービス エンドポイントの追加は省略可能にします。 これらのバージョン、コードや構成を追加しない場合、WCF はベース アドレスと、サービスによって実装されるコントラクトの組み合わせごとに 1 つの既定のエンドポイントを追加します。 既定のエンドポイントの詳細については、次を参照してください。[エンドポイント アドレスを指定する](specifying-an-endpoint-address.md)します。 既定のエンドポイント、バインディング、および動作の詳細については、次を参照してください。[簡略化された構成](simplified-configuration.md)と[WCF サービスの構成を簡略化された](samples/simplified-configuration-for-wcf-services.md)します。

- **手順 4**:メタデータ交換を有効にします。 クライアントは、サービス操作を呼び出すためのプロキシを生成するのにメタデータ交換を使用します。 メタデータ交換を有効にするには作成、<xref:System.ServiceModel.Description.ServiceMetadataBehavior>インスタンスは、設定、<xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled>プロパティを`true`、追加、`ServiceMetadataBehavior`オブジェクトを<xref:System.ServiceModel.Description.ServiceDescription.Behaviors%2A>のコレクション、<xref:System.ServiceModel.ServiceHost>インスタンス。

- **手順 5**:開いている<xref:System.ServiceModel.ServiceHost>受信メッセージをリッスンします。 アプリケーションがボタンを押すまで待機**Enter**します。 アプリケーションをインスタンス化後<xref:System.ServiceModel.ServiceHost>、try/catch ブロックを実行します。 によってスローされた例外を安全にキャッチの詳細については<xref:System.ServiceModel.ServiceHost>を参照してください[使用終了、中止 WCF クライアントのリソースを解放する](samples/use-close-abort-release-wcf-client-resources.md)します。

> [!IMPORTANT]
> WCF サービス ライブラリを追加するときに Visual Studio ホストがサービス ホストを起動してデバッグする場合。 競合を回避するには、WCF サービス ライブラリをホストしているから Visual Studio を回避できます。 
> 1. 選択、 **GettingStartedLib**プロジェクト**ソリューション エクスプ ローラー**選択**プロパティ**ショートカット メニューから。
> 2. 選択**WCF オプション**をオフにし、**開始 WCF サービス ホスト、同じソリューション内の別のプロジェクトをデバッグするときに**します。


## <a name="next-steps"></a>次の手順

このチュートリアルでは、次の作業を行う方法を学びました。
> [!div class="checklist"]
> - 作成し、WCF サービスをホストするためのコンソール アプリ プロジェクトを構成します。
> - WCF サービスをホストするためのコードを追加します。
> - 構成ファイルを更新します。
> - WCF サービスを開始し、確認が実行されています。

WCF クライアントを作成する方法については、次のチュートリアルに進んでください。

> [!div class="nextstepaction"]
> [チュートリアル: WCF クライアントを作成します。](how-to-create-a-wcf-client.md)
