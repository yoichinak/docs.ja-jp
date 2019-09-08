---
title: Web ブラウザーからサービスへのアクセス (WCF Data Services クイックスタート)
ms.date: 03/30/2017
ms.assetid: 5a6fa180-3094-4e6e-ba2b-8c80975d18d1
ms.openlocfilehash: eb7f1c97722b45a93c310fb8bcbdb42beece2553
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/07/2019
ms.locfileid: "70780544"
---
# <a name="accessing-the-service-from-a-web-browser-wcf-data-services-quickstart"></a>Web ブラウザーからサービスへのアクセス (WCF Data Services クイックスタート)

これは、WCF Data Services のクイックスタートの2番目のタスクです。 このタスクでは、Visual Studio から WCF Data Services を開始し、必要に応じて Web ブラウザーでのフィードの読み取りを無効にします。 次に、公開されたリソースに対して Web ブラウザーから HTTP GET 要求を送信することで、サービス定義ドキュメントを取得し、データサービスリソースにアクセスします。

> [!NOTE]
> 既定では、Visual Studio によって、コンピューター上の `localhost` URI にポート番号が自動的に割り当てられます。 このタスクでは、URI の例でポート番号 `12345` を使用しています。 Visual Studio プロジェクトで特定のポート番号を設定する方法の詳細について[は、「データサービスの作成](creating-the-data-service.md)」を参照してください。

## <a name="to-request-the-default-service-document-by-using-internet-explorer"></a>Internet Explorer を使用して既定のサービス ドキュメントを要求するには

1. Internet Explorer で、 **[ツール]** メニューの **[インターネットオプション]** を選択し、 **[コンテンツ]** タブをクリックし、 **[設定]** をクリックして、 **[フィードの表示を有効にする]** をオフにします。

     フィードの読み取りが無効になります。 この機能が無効でなければ、Web ブラウザーは、AtomPub エンコードのドキュメントが返されると生の XML データを表示せずに XML フィードとして処理します。

    > [!NOTE]
    > ブラウザーでフィードを生の XML データとして表示できない場合は、そのままでフィードをページのソース コードとして表示できます。

2. Visual Studio で、 **F5**キーを押してアプリケーションのデバッグを開始します。

3. ローカル コンピューターで Web ブラウザーを開きます。 アドレス バーに次の URI を入力します。

    ```
    http://localhost:12345/northwind.svc
    ```

     既定のサービス ドキュメントが返されます。このドキュメントには、このデータ サービスによって公開されているエンティティ セットの一覧が含まれています。

## <a name="to-access-entity-set-resources-from-a-web-browser"></a>Web ブラウザーからエンティティ セット リソースにアクセスするには

1. Web ブラウザーのアドレス バーに次の URI を入力します。

    ```
    http://localhost:12345/northwind.svc/Customers
    ```

     Northwind サンプル データベース内のすべての顧客のセットが返されます。

2. Web ブラウザーのアドレス バーに次の URI を入力します。

    ```
    http://localhost:12345/northwind.svc/Customers('ALFKI')
    ```

     特定の顧客 `ALFKI` のエンティティ インスタンスが返されます。

3. Web ブラウザーのアドレス バーに次の URI を入力します。

    ```
    http://localhost:12345/northwind.svc/Customers('ALFKI')/Orders
    ```

     顧客と注文の間のリレーションシップがスキャンされ、特定の顧客 `ALFKI` のすべての注文のセットが返されます。

4. Web ブラウザーのアドレス バーに次の URI を入力します。

    ```
    http://localhost:12345/northwind.svc/Customers('ALFKI')/Orders?$filter=OrderID eq 10643
    ```

     特定の顧客 `ALFKI` に属する注文がフィルターされ、指定した `OrderID` 値に基づいた特定の注文だけが返されます。

## <a name="next-steps"></a>次の手順

ブラウザーが指定されたリソースに対して HTTP GET 要求を発行して、Web ブラウザーから WCF Data Services に正常にアクセスしました。 Web ブラウザーを使用すると、リクエストのアドレス構文を試したり、結果を表示したりすることが簡単にできます。 しかし、一般的に、この方法では運用データ サービスにはアクセスできません。 通常、アプリケーションでは、アプリケーション コードまたはスクリプト言語を使用してデータ サービスと対話します。 次に、クライアント ライブラリを使用して共通言語ランタイム (CLR) オブジェクトと同様にデータ サービス リソースにアクセスするクライアント アプリケーションを作成します。

> [!div class="nextstepaction"]
> [.NET Framework クライアント アプリケーションの作成](creating-the-dotnet-client-application-wcf-data-services-quickstart.md)

## <a name="see-also"></a>関連項目

- [データ サービス リソースへのアクセス](accessing-data-service-resources-wcf-data-services.md)
