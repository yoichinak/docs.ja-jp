---
title: 'チュートリアル: Windows Communication Foundation クライアントを作成します。'
ms.date: 03/19/2019
helpviewer_keywords:
- clients [WCF], running
- WCF clients [WCF], running
ms.assetid: a67884cc-1c4b-416b-8c96-5c954099f19f
ms.openlocfilehash: 0f7f622221e6612ecdb0ea04084d81e923218a5c
ms.sourcegitcommit: d938c39afb9216db377d0f0ecdaa53936a851059
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/29/2019
ms.locfileid: "58634064"
---
# <a name="tutorial-create-a-windows-communication-foundation-client"></a>チュートリアル: Windows Communication Foundation クライアントを作成します。

このチュートリアルでは、4 番目の基本的な Windows Communication Foundation (WCF) アプリケーションを作成するために必要な 5 つのタスクについて説明します。 チュートリアルの概要については、次を参照してください。[チュートリアル。Windows Communication Foundation アプリケーションの概要](getting-started-tutorial.md)します。

WCF アプリケーションを作成するための次のタスクでは、WCF サービスからメタデータを取得することによって、クライアントを作成します。 Visual Studio を使用して、サービスの MEX エンドポイントからメタデータを取得します。 サービス参照を追加します。 Visual Studio は、選択した言語でクライアント プロキシのマネージ ソース コード ファイルを生成します。 クライアント構成ファイルが作成されます (*App.config*)。 このファイルは、エンドポイントのサービスに接続するクライアント アプリケーションを使用します。 

> [!NOTE]
> Visual Studio でクラス ライブラリ プロジェクトから WCF サービスを呼び出す場合は、使用、**サービス参照の追加**プロキシと関連付けられている構成ファイルを自動的に生成する機能。 ただし、クラス ライブラリ プロジェクトでは、この構成ファイルを使用しないため、必要がありますに生成された構成ファイルで設定を追加する、 *App.config*クラス ライブラリを呼び出す実行可能ファイルのファイル。

> [!NOTE]
> 代わりに、使用、 [ServiceModel メタデータ ユーティリティ ツール](#servicemodel-metadata-utility-tool)Visual Studio で、プロキシ クラスおよび構成ファイルを生成する代わりにします。

クライアント アプリケーションは、生成されたプロキシ クラスを使用してサービスと通信します。 この手順で説明されて[チュートリアル。クライアントを使用して](how-to-use-a-wcf-client.md)します。

このチュートリアルでは、次の作業を行う方法について説明します。
> [!div class="checklist"]
> - 作成し、WCF クライアントのコンソール アプリ プロジェクトを構成します。
> - プロキシ クラスと構成ファイルを生成する WCF サービスにサービス参照を追加します。


## <a name="create-a-windows-communication-foundation-client"></a>Windows Communication Foundation クライアントを作成します。

1. Visual Studio でコンソール アプリ プロジェクトを作成します。 

    1. **ファイル**メニューの **オープン** > **プロジェクト/ソリューション**を見つけて、 **GettingStarted**ソリューションを以前に作成した (*GettingStarted.sln*)。 **[開く]** を選択します。

    2. **ビュー**メニューの **ソリューション エクスプ ローラー**します。

    3. **ソリューション エクスプ ローラー**ウィンドウで、 **GettingStarted**ソリューション (最上位ノード) し、選択**追加** > **の新しいプロジェクト**ショートカット メニューから。 
    
    4. **新しいプロジェクトの追加**ウィンドウで、左側にある、選択、 **Windows デスクトップ**カテゴリ  **Visual C#** または**Visual Basic**. 

    5. 選択、**コンソール アプリ (.NET Framework)** テンプレート、入力と*GettingStartedClient*の**名前**します。 **[OK]** を選択します。

2. 参照を追加、 **GettingStartedClient**プロジェクトを<xref:System.ServiceModel>アセンブリ。 

    1.  **ソリューション エクスプ ローラー**ウィンドウで、**参照**の下のフォルダー、 **GettingStartedClient**プロジェクトを選び**参照の追加**ショートカット メニューから。 

    2. **参照の追加**ウィンドウで、**アセンブリ**ウィンドウの左側にある、次のように選択します。 **Framework**します。
    
    3. 検索して選択**System.ServiceModel**を選び、 **OK**。 

    4. ソリューションを選択して保存**ファイル** > **すべて保存**します。

3. 電卓サービスにサービス参照を追加します。

   1. **ソリューション エクスプ ローラー**ウィンドウで、**参照**の下のフォルダー、 **GettingStartedClient**プロジェクトを選び**サービス参照の追加**ショートカット メニューから。

   2. **サービス参照の追加**ウィンドウで、 **Discover**します。

      CalculatorService サービスが開始されると Visual Studio でそれを表示、**サービス**ボックス。

   3. 選択**CalculatorService**展開すると、サービスによって実装されるサービス コントラクトを表示します。 既定値のままに**Namespace**選択**OK**します。

      Visual Studio は、新しい項目を追加、**接続済みサービス**フォルダーで、 **GettingStartedClient**プロジェクト。 


### <a name="servicemodel-metadata-utility-tool"></a>ServiceModel メタデータ ユーティリティ ツール

次の例では、必要に応じて使用する方法、 [ServiceModel メタデータ ユーティリティ ツール (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md)プロキシ クラス ファイルを生成します。 このツールは、プロキシ クラス ファイルを生成し、 *App.config*ファイル。 次の例でプロキシを生成する方法を示してC#および Visual Basic の場合は、それぞれします。

```shell
svcutil.exe /language:cs /out:generatedProxy.cs /config:app.config http://localhost:8000/GettingStarted/CalculatorService
```

```shell
svcutil.exe /language:vb /out:generatedProxy.vb /config:app.config http://localhost:8000/GettingStarted/CalculatorService
```

### <a name="client-configuration-file"></a>クライアント構成ファイル

クライアントを作成したら、Visual Studio で作成、 **App.config**構成ファイルで、 **GettingStartedClient**プロジェクトで、次の例のようにする必要があります。

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

で、 [ \<system.serviceModel >](../configure-apps/file-schema/wcf/system-servicemodel.md)セクションに注意してください、 [\<エンドポイント >](../configure-apps/file-schema/wcf/endpoint-element.md)要素。 **&lt;エンドポイント&gt;** 要素は、クライアントが次のように、サービスへのアクセスに使用するエンドポイントを定義します。
- アドレス:`http://localhost:8000/GettingStarted/CalculatorService`します。 エンドポイントのアドレス。
- サービス コントラクト:`ServiceReference1.ICalculator`します。 サービス コントラクトは、WCF クライアントとサービス間の通信を処理します。 Visual Studio が使用したときに、このコントラクトを生成、**サービス参照の追加**関数。 基本的に、GettingStartedLib プロジェクトで定義されているコントラクトのコピーになります。 
- バインディング:<xref:System.ServiceModel.WSHttpBinding>します。 バインディングでは、トランスポート、相互運用可能なセキュリティ、およびその他の構成の詳細として HTTP を指定します。

## <a name="next-steps"></a>次の手順

このチュートリアルでは、次の作業を行う方法を学びました。
> [!div class="checklist"]
> - 作成し、WCF クライアントのコンソール アプリ プロジェクトを構成します。
> - クライアント アプリケーションのプロキシ クラスと構成ファイルを生成する WCF サービスにサービス参照を追加します。

生成されたクライアントを使用する方法については、次のチュートリアルに進んでください。

> [!div class="nextstepaction"]
> [チュートリアル: WCF クライアントを使用します。](how-to-use-a-wcf-client.md)


