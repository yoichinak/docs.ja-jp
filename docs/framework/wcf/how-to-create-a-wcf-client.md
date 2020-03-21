---
title: 'チュートリアル: Windows コミュニケーション ファウンデーション クライアントを作成する'
ms.date: 03/19/2019
helpviewer_keywords:
- clients [WCF], running
- WCF clients [WCF], running
ms.assetid: a67884cc-1c4b-416b-8c96-5c954099f19f
ms.openlocfilehash: bfa4cbacc5a947cb51d577503b5e46f9a5f8de39
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184111"
---
# <a name="tutorial-create-a-windows-communication-foundation-client"></a>チュートリアル: Windows コミュニケーション ファウンデーション クライアントを作成する

このチュートリアルでは、基本的な Wcf (WCF) アプリケーションを作成するために必要な 5 つのタスクの 4 つ目について説明します。 チュートリアルの概要については、「[チュートリアル: Windows コミュニケーションファウンデーション アプリケーションの概要](getting-started-tutorial.md)」を参照してください。

WCF アプリケーションを作成するための次のタスクは、WCF サービスからメタデータを取得することによってクライアントを作成します。 Visual Studio を使用してサービス参照を追加すると、サービスの MEX エンドポイントからメタデータを取得できます。 次に、Visual Studio によって、選択した言語でクライアント プロキシ用のマネージ ソース コード ファイルが生成されます。 また、クライアント構成ファイル (*App.config*) も作成されます。 このファイルを使用すると、クライアント アプリケーションはエンドポイントでサービスに接続できます。

> [!NOTE]
> Visual Studio のクラス ライブラリ プロジェクトから WCF サービスを呼び出す場合は、**サービス参照の追加**機能を使用して、プロキシと関連付けられた構成ファイルを自動的に生成します。 ただし、クラス ライブラリ プロジェクトはこの構成ファイルを使用しないため、生成された構成ファイルの設定を、クラス ライブラリを呼び出す実行可能ファイルの*App.config*ファイルに追加する必要があります。

> [!NOTE]
> 代わりに、Visual Studio ではなく[サービス モデル メタデータ ユーティリティ ツール](#servicemodel-metadata-utility-tool)を使用して、プロキシ クラスと構成ファイルを生成します。

クライアント アプリケーションは、生成されたプロキシ クラスを使用してサービスと通信します。 この手順については、「[チュートリアル: クライアントを使用する」を参照](how-to-use-a-wcf-client.md)してください。

このチュートリアルでは、以下の内容を学習します。
> [!div class="checklist"]
>
> - 作成し、WCF クライアントのコンソール アプリ プロジェクトを構成します。
> - WCF サービスにサービス参照を追加して、プロキシ クラスファイルと構成ファイルを生成します。

## <a name="create-a-windows-communication-foundation-client"></a>Windows コミュニケーション ファウンデーション クライアントを作成する

1. Visual Studio でコンソール アプリ プロジェクトを作成します。

    1. [**ファイル]** メニューの [**プロジェクト/ソリューション**を**開く** > ] を選択し、以前に作成した **[はじめに]** ソリューション (*GettingStarted.sln*) を参照します。 **[開く]** を選択します。

    2. [**表示**] メニューの [**ソリューション エクスプローラ**] をクリックします。

    3. [**ソリューション エクスプローラー** ] ウィンドウで **、"はじめに"** ソリューション (最上位ノード) を選択し、ショートカット メニューから **[新しいプロジェクト**の**追加** > ] を選択します。

    4. [**新しいプロジェクトの追加**] ウィンドウの左側で **、[Visual C#** または Visual **Basic]** の下にある **[Windows デスクトップ**] カテゴリを選択します。

    5. コンソール**アプリケーション (.NET Framework)** テンプレートを選択し、**名前***に「はじめにクライアント*」と入力します。 **[OK]** を選択します。

2. **アセンブリに、次の参照を開始クライアント**プロジェクト<xref:System.ServiceModel>に追加します。

    1. **[ソリューション エクスプローラー** ] ウィンドウで **、GettingStartedClient**プロジェクトの下にある **[参照**] フォルダーを選択し、ショートカット メニューの **[参照の追加**] を選択します。

    2. [**参照の追加**] ウィンドウの左側にある **[アセンブリ**] で、[**フレームワーク**] を選択します。

    3. 検索して **[System.ServiceModel]** を選択し **、[OK]** をクリックします。

    4. [ファイルをすべて保存] を選択してソリューション**を** > **保存**します。

3. 電卓サービスにサービス参照を追加します。

   1. [**ソリューション エクスプローラー** ] ウィンドウで **、GettingStartedClient**プロジェクトの下にある **[参照**] フォルダーを選択し、ショートカット メニューの **[サービス参照の追加**] を選択します。

   2. [**サービス参照の追加**] ウィンドウで、[**検出**] を選択します。

      電卓サービス サービスが開始され、Visual Studio によって [**サービス**] ボックスに表示されます。

   3. **電卓サービス**を展開し、サービスによって実装されるサービス コントラクトを表示するを選択します。 デフォルトの**名前空間**をそのままにして **、[OK] を**選択します。

      新しい項目が **、GettingStartedClient**プロジェクトの **[接続済みサービス**] フォルダーに追加されます。

### <a name="servicemodel-metadata-utility-tool"></a>サービスモデル メタデータ ユーティリティ ツール

次の例は、オプションで[サービス モデル メタデータ ユーティリティ ツール (Svcutil.exe) を](servicemodel-metadata-utility-tool-svcutil-exe.md)使用してプロキシ クラス ファイルを生成する方法を示しています。 このツールは、プロキシ クラス ファイルと*App.config*ファイルを生成します。 次の例は、C# と Visual Basic でそれぞれプロキシを生成する方法を示しています。

```shell
svcutil.exe /language:cs /out:generatedProxy.cs /config:app.config http://localhost:8000/GettingStarted/CalculatorService
```

```shell
svcutil.exe /language:vb /out:generatedProxy.vb /config:app.config http://localhost:8000/GettingStarted/CalculatorService
```

### <a name="client-configuration-file"></a>クライアント構成ファイル

クライアントを作成すると、次の例のようなコードが作成される必要があります、次の例に従って、**プロジェクト**に**App.config**構成ファイルが作成されます。

```xml
    <?xml version="1.0" encoding="utf-8" ?>
    <configuration>
        <startup>
            <!-- specifies the version of WCF to use-->
            <supportedRuntime version="v4.0" sku=".NETFramework,Version=v4.6.1" />
        </startup>
        <system.serviceModel>
            <bindings>
                <!-- Uses wsHttpBinding-->
                <wsHttpBinding>
                    <binding name="WSHttpBinding_ICalculator" />
                </wsHttpBinding>
            </bindings>
            <client>
                <!-- specifies the endpoint to use when calling the service -->
                <endpoint address="http://localhost:8000/GettingStarted/CalculatorService"
                    binding="wsHttpBinding" bindingConfiguration="WSHttpBinding_ICalculator"
                    contract="ServiceReference1.ICalculator" name="WSHttpBinding_ICalculator">
                    <identity>
                        <dns value="localhost" />
                    </identity>
                </endpoint>
            </client>
        </system.serviceModel>
    </configuration>
```

system.serviceModel>セクションで、[\<エンドポイント>](../configure-apps/file-schema/wcf/endpoint-element.md)要素に注目してください。 [ \<](../configure-apps/file-schema/wcf/system-servicemodel.md) **&lt;エンドポイント&gt;** 要素は、クライアントがサービスへのアクセスに使用するエンドポイントを次のように定義します。

- アドレス: `http://localhost:8000/GettingStarted/CalculatorService`。 エンドポイントのアドレス。
- サービス契約: `ServiceReference1.ICalculator`. サービス コントラクトは、WCF クライアントとサービス間の通信を処理します。 Visual Studio は **、サービス参照の追加**機能を使用したときにこのコントラクトを生成します。 これは、基本的に、GettingStartedLib プロジェクトで定義したコントラクトのコピーです。
- バインディング: <xref:System.ServiceModel.WSHttpBinding>. バインディングは、トランスポート、相互運用可能なセキュリティ、およびその他の構成の詳細として HTTP を指定します。

## <a name="next-steps"></a>次のステップ

このチュートリアルでは、以下の内容を学習しました。
> [!div class="checklist"]
>
> - 作成し、WCF クライアントのコンソール アプリ プロジェクトを構成します。
> - WCF サービスへのサービス参照を追加して、クライアント アプリケーションのプロキシ クラス ファイルと構成ファイルを生成します。

次のチュートリアルに進み、生成されたクライアントの使用方法を学習します。

> [!div class="nextstepaction"]
> [チュートリアル: WCF クライアントを使用する](how-to-use-a-wcf-client.md)
