---
title: Visual Studio での WCF data service を作成します。
ms.date: 08/24/2018
dev_langs:
- csharp
- vb
ms.assetid: 34d1d971-5e18-4c22-9bf6-d3612e27ea59
ms.openlocfilehash: e8d82ff8958af12842366911b6633ea6b2e0efbb
ms.sourcegitcommit: 680a741667cf6859de71586a0caf6be14f4f7793
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/12/2019
ms.locfileid: "59517227"
---
# <a name="create-the-data-service"></a>データ サービスを作成する

このトピックでは、公開する WCF Data Services を使用するサンプル データ サービスを作成する、[!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)]フィード、Northwind サンプル データベースに基づいています。 この作業に必要な基本手順は次のとおりです。

1. ASP.NET Web アプリケーションを作成します。

2. Entity Data Model ツールを使用して、データ モデルを定義します。

3. データ サービスを Web アプリケーションに追加します。

4. データ サービスへのアクセスを有効にします。

## <a name="create-the-aspnet-web-app"></a>ASP.NET web アプリを作成します。

1. Visual Studio での**ファイル**メニューの **新規** > **プロジェクト**します。

1. **新しいプロジェクト** ダイアログ ボックスで、Visual Basic または Visual C# のいずれかの選択 で、 **Web**カテゴリ、および選択**ASP.NET Web アプリケーション**します。

1. 入力`NorthwindService`選択し、プロジェクトの名前として**OK**します。

1. **新しい ASP.NET Web アプリケーション**ダイアログ ボックスで、**空**選び**OK**。

1. (省略可能) Web アプリケーションに対して特定のポート番号を指定します。 注: ポート番号`12345`のクイック スタート トピックには、このシリーズで使用されます。

    1. **ソリューション エクスプ ローラー**、先ほど作成した ASP.NET プロジェクトを右クリックし、**プロパティ**します。

    2. 選択、 **Web**タブをクリックし、値の設定、**特定のポート**テキスト ボックスに`12345`します。

## <a name="define-the-data-model"></a>データ モデルを定義する

1. **ソリューション エクスプ ローラー**ASP.NET プロジェクトの名前を右クリックし、クリックして**追加** > **新しい項目の**します。

2. **新しい項目の追加**ダイアログ ボックスで、**データ**カテゴリ、および選択**ADO.NET Entity Data Model**します。

3. データ モデルの名前を入力`Northwind.edmx`します。

4. **Entity Data Model ウィザード**を選択します**データベースの EF デザイナー**、順にクリックします**次**します。

5. 次の手順のいずれかの手順を実行して、データ モデルをデータベースに接続し、**次**:

    -   既に構成されているデータベース接続を持っていない場合はクリックして**新しい接続**し、新しい接続を作成します。 詳細については、「[方法 :SQL Server データベースへの接続を作成する](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/s4yys16a(v=vs.90))します。 この SQL Server インスタンスには、Northwind サンプル データベースがアタッチされている必要があります。

         \- または -

    -   Northwind データベースに接続するようにデータベース接続が既に構成されている場合は、一覧からその接続を選択します。

6. ウィザードの最終ページで、データベース内のすべてのテーブルのチェック ボックスをオンにし、ビューおよびストアド プロシージャのチェック ボックスをオフにします。

7. クリックして**完了**ウィザードを閉じます。

## <a name="create-the-wcf-data-service"></a>WCF データ サービスを作成します。

1. **ソリューション エクスプ ローラー**、ASP.NET プロジェクトを右クリックし、選択し、**追加** > **新しい項目の**します。

2. **新しい項目の追加**ダイアログ ボックスで、 **WCF Data Service**から項目テンプレート、 **Web**カテゴリ。

   ![Visual Studio 2015 での WCF データ サービス項目テンプレート](media/wcf-data-service-item-template.png)

   > [!NOTE]
   > **WCF Data Service**テンプレートは、Visual Studio 2015 ではなく Visual Studio 2017 で使用できます。

3. サービスの名前を入力`Northwind`します。

     Visual Studio で新しいサービスの XML マークアップおよびコード ファイルが作成されます。 既定では、コード エディターのウィンドウが開きます。 **ソリューション エクスプ ローラー**、サービスが、拡張子を持つ名前 Northwind *. は.svc.cs*または *..svc.vb になります*します。

4. データ サービスのコードで、データ サービスを定義するクラスの定義にあるコメント `/* TODO: put your data source class name here */` をデータ モデルのエンティティ コンテナーである型 (この場合は `NorthwindEntities`) で置き換えます。 クラス定義は次のようになります。

     [!code-csharp[Astoria Quickstart Service#ServiceDefinition](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_quickstart_service/cs/northwind.svc.cs#servicedefinition)]
     [!code-vb[Astoria Quickstart Service#ServiceDefinition](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_quickstart_service/vb/northwind.svc.vb#servicedefinition)]

## <a name="enable-access-to-data-service-resources"></a>データ サービス リソースへのアクセスを有効にします。

1. データ サービスのコードで、`InitializeService` 関数のプレースホルダーのコードを次の内容で置き換えます。

     [!code-csharp[Astoria Quickstart Service#AllReadConfig](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_quickstart_service/cs/northwind.svc.cs#allreadconfig)]
     [!code-vb[Astoria Quickstart Service#AllReadConfig](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_quickstart_service/vb/northwind.svc.vb#allreadconfig)]

     これにより、承認されたクライアントは、指定したエンティティ セットのリソースに読み取りおよび書き込みアクセスできるようになります。

    > [!NOTE]
    > ASP.NET アプリケーションにアクセスできるクライアントは、データ サービスによって公開されるリソースにもアクセスできます。 運用データ サービスで、リソースへの承認されていないアクセスを防止するために、アプリケーション自身もセキュリティで保護する必要があります。 詳細については、「 [Securing WCF Data Services](../../../../docs/framework/data/wcf/securing-wcf-data-services.md)」を参照してください。

## <a name="next-steps"></a>次の手順

Northwind サンプル データベースに基づいている OData フィードを公開する新しいデータ サービスが正常に作成しを ASP.NET Web アプリケーションへのアクセス許可を持つクライアントからフィードへのアクセスを有効にします。 次に、Visual Studio からデータ サービスを開始し、Web ブラウザーから HTTP GET 要求を送信してフィードの OData へのアクセスします。

> [!div class="nextstepaction"]
> [Web ブラウザーからサービスへのアクセスします。](../../../../docs/framework/data/wcf/accessing-the-service-from-a-web-browser-wcf-data-services-quickstart.md)

## <a name="see-also"></a>関連項目

- [ADO.NET Entity Data Model ツール](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))