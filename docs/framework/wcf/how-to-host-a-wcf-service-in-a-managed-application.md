---
title: '方法 : マネージド アプリケーションで WCF サービスをホストする'
ms.date: 09/17/2018
dev_langs:
- csharp
- vb
ms.assetid: 5eb29db0-b6dc-4e77-8c68-0a62f79d743b
ms.openlocfilehash: 131d99457427e0818f78076d987f550a99ad7cf0
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/26/2018
ms.locfileid: "47196852"
---
# <a name="how-to-host-a-wcf-service-in-a-managed-app"></a>方法: 管理対象アプリでの WCF サービス ホスト

マネージド アプリケーションでサービスをホストするには、マネージド アプリケーション コード内にサービスのコードを埋め込み、サービスのエンドポイントをコードで強制的に定義するか、構成を使用して宣言により定義してから、または既定のエンドポイントを使用して、<xref:System.ServiceModel.ServiceHost> のインスタンスを作成します。

メッセージの受信を開始するには、<xref:System.ServiceModel.ICommunicationObject.Open%2A> で <xref:System.ServiceModel.ServiceHost> を呼び出します。 これにより、サービスのリスナーが作成されて開きます。 この方法によるサービスのホストは、マネージド アプリケーション自体がホスト作業を行うため、"自己ホスト" と呼ばれることがあります。 サービスを閉じるには、<xref:System.ServiceModel.Channels.CommunicationObject.Close%2A?displayProperty=nameWithType> で <xref:System.ServiceModel.ServiceHost> を呼び出します。

サービスは、マネージド Windows サービス、インターネット インフォメーション サービス (IIS)、または Windows プロセス アクティブ化サービス (WAS) でホストすることもできます。 ホスティング サービスのオプションの詳細については、[ホスティング サービス](../../../docs/framework/wcf/hosting-services.md)を参照してください。

マネージド アプリケーションでのサービスのホスティングは、展開するインフラストラクチャが最小限で済むため、最も柔軟性があります。 マネージ アプリケーションでサービスをホストする方法の詳細については、[マネージ アプリケーションでのホスティング](../../../docs/framework/wcf/feature-details/hosting-in-a-managed-application.md)を参照してください。

次の手順では、自己ホスト型サービスをコンソール アプリケーションに実装する方法を示します。

## <a name="create-a-self-hosted-service"></a>自己ホスト型サービスを作成します。

1. 新しいコンソール アプリケーションを作成します。

   1. Visual Studio を開き、選択**新規** > **プロジェクト**から、**ファイル**メニュー。

   2. **インストールされたテンプレート**一覧で、 **Visual c#** または**Visual Basic**、し、 **Windows デスクトップ**します。

   3. 選択、**コンソール アプリ**テンプレート。 型`SelfHost`で、**名前**ボックス選び、 **OK**。

2. 右クリック**SelfHost**で**ソリューション エクスプ ローラー**選択**参照の追加**します。 選択**System.ServiceModel**から、 **.NET**タブをクリックして**OK**します。

    > [!TIP]
    > 場合、**ソリューション エクスプ ローラー**ウィンドウが表示される、選択**ソリューション エクスプ ローラー**から、**ビュー**メニュー。

3. ダブルクリック**Program.cs**または**Module1.vb**で**ソリューション エクスプ ローラー**がまだ開いていない場合、コード ウィンドウで開きます。 ファイルの上部にある次のステートメントを追加します。

     [!code-csharp[CFX_SelfHost4#1](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_selfhost4/cs/program.cs#1)]
     [!code-vb[CFX_SelfHost4#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_selfhost4/vb/module1.vb#1)]

4. サービス コントラクトを定義して実装します。 この例では、サービスへの入力に基づいてメッセージを返す `HelloWorldService` を定義します。

     [!code-csharp[CFX_SelfHost4#2](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_selfhost4/cs/program.cs#2)]
     [!code-vb[CFX_SelfHost4#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_selfhost4/vb/module1.vb#2)]

    > [!NOTE]
    > 定義し、サービス インターフェイスを実装する方法の詳細については、[方法: サービス コントラクトを定義する](../../../docs/framework/wcf/how-to-define-a-wcf-service-contract.md)と[方法: サービス コントラクトを実装する](../../../docs/framework/wcf/how-to-implement-a-wcf-contract.md)を参照してください。

5. `Main` メソッドの上部で、サービスのベース アドレスで <xref:System.Uri> クラスのインスタンスを作成します。

     [!code-csharp[CFX_SelfHost4#3](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_selfhost4/cs/program.cs#3)]
     [!code-vb[CFX_SelfHost4#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_selfhost4/vb/module1.vb#3)]

6. <xref:System.ServiceModel.ServiceHost> クラスのインスタンスを作成して、サービス型を表す <xref:System.Type> とベース アドレス URI (Uniform Resource Identifier) を <xref:System.ServiceModel.ServiceHost.%23ctor%28System.Type%2CSystem.Uri%5B%5D%29> に渡します。 メタデータ公開を有効にして、<xref:System.ServiceModel.ICommunicationObject.Open%2A> で <xref:System.ServiceModel.ServiceHost> メソッドを呼び出し、サービスを初期化してメッセージを受信する準備をします。

     [!code-csharp[CFX_SelfHost4#4](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_selfhost4/cs/program.cs#4)]
     [!code-vb[CFX_SelfHost4#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_selfhost4/vb/module1.vb#4)]

    > [!NOTE]
    > この例では、既定のエンドポイントを使用するので、このサービスには構成ファイルは必要ありません。 エンドポイントが構成されていない場合、ランタイムは、サービスによって実装されたサービス コントラクトごとに 1 つのエンドポイントを各ベース アドレスに作成します。 既定のエンドポイントの詳細については、[Simplified Configuration](../../../docs/framework/wcf/simplified-configuration.md)と[Simplified Configuration for WCF Services](../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md)を参照してください。

7. キーを押して**Ctrl**+**Shift**+**B**ソリューションをビルドします。

## <a name="test-the-service"></a>サービスをテストします。

1. キーを押して**Ctrl**+**F5**サービスを実行します。

2. 開いている**WCF テスト クライアント**します。

    > [!TIP]
    > 開くには**WCF テスト クライアント**for Visual Studio 開発者コマンド プロンプトを開くし、実行、 **WcfTestClient.exe**します。

3. 選択**サービスの追加**から、**ファイル**メニュー。

4. 型`http://localhost:8080/hello`アドレス ボックスに**OK**します。

    > [!TIP]
    > サービスが実行していることを確認してください。サービスが実行していない場合、この手順は失敗します。 コードでベース アドレスを変更した場合は、この手順で、変更したアドレスを使用します。

5. ダブルクリック**SayHello**下、**マイ サービス プロジェクト**ノード。 型名を指定して、**値**内の列、**要求**ボックスの一覧し、をクリックして**Invoke**します。

   応答メッセージが表示されます、**応答**一覧。

## <a name="example"></a>例

<xref:System.ServiceModel.ServiceHost> 型のサービスをホストする `HelloWorldService` オブジェクトを作成し、<xref:System.ServiceModel.ICommunicationObject.Open%2A> で <xref:System.ServiceModel.ServiceHost> メソッドを呼び出す例を、次に示します。 ベース アドレスがコードで指定され、メタデータ公開が有効化されていて、既定のエンドポイントが使用されています。

[!code-csharp[CFX_SelfHost4#5](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_selfhost4/cs/program.cs#5)]
[!code-vb[CFX_SelfHost4#5](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_selfhost4/vb/module1.vb#5)]

## <a name="see-also"></a>関連項目

- <xref:System.Uri>
- <xref:System.Configuration.ConfigurationManager.AppSettings%2A>
- <xref:System.Configuration.ConfigurationManager>
- [方法 : IIS で WCF サービスをホストする](../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-iis.md)
- [自己ホスト](../../../docs/framework/wcf/samples/self-host.md)
- [ホスティング サービス](../../../docs/framework/wcf/hosting-services.md)
- [方法: サービス コントラクトを定義する](../../../docs/framework/wcf/how-to-define-a-wcf-service-contract.md)
- [方法: サービス コントラクトを実装する](../../../docs/framework/wcf/how-to-implement-a-wcf-contract.md)
- [ServiceModel メタデータ ユーティリティ ツール (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)
- [サービスとクライアントを構成するためのバインディングの使用](../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [システム標準のバインディング](../../../docs/framework/wcf/system-provided-bindings.md)