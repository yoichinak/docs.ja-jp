---
title: '方法: ADO.NET Entity Framework データ ソース (WCF Data Services) を使用してデータ サービスを作成します。'
ms.date: 08/24/2018
helpviewer_keywords:
- WCF Data Services, providers
- WCF Data Services, Entity Framework
ms.assetid: 6d11fec8-0108-42f5-8719-2a7866d04428
ms.openlocfilehash: e9b2c1077cf3323a7d5b69bee6dff7e6f9611818
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/15/2019
ms.locfileid: "65634107"
---
# <a name="how-to-create-a-data-service-using-an-adonet-entity-framework-data-source-wcf-data-services"></a>方法: ADO.NET Entity Framework データ ソース (WCF Data Services) を使用してデータ サービスを作成します。

WCF Data Services では、データ サービスとしてのエンティティ データを公開します。 データ ソースがリレーショナル データベースの場合、このエンティティ データは [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)][!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)] によって提供されます。 このトピックでは、作成する方法を示します、 [!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)]-ベースのデータ モデルは、既存のデータベースに基づいており、このデータ モデルを使用して、新しいデータ サービスを作成する Visual Studio Web アプリケーション。

[!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)]も生成できるコマンド ライン ツールを提供する[!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)]Visual Studio プロジェクトの外側でモデル。 詳細については、「[方法 :EdmGen.exe を使用して、モデルとマッピング ファイルを生成する](../../../../docs/framework/data/adonet/ef/how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md)します。

## <a name="to-add-an-entity-framework-model-that-is-based-on-an-existing-database-to-an-existing-web-application"></a>既存のデータベースに基づく Entity Framework モデルを既存の Web アプリケーションに追加するには

1. **プロジェクト** メニューのをクリックして**追加** > **新しい項目の**します。

2. **テンプレート**ウィンドウで、をクリックして、**データ**カテゴリ、および選択**ADO.NET Entity Data Model**します。

3. モデル名を入力し、クリックして**追加**します。

     [!INCLUDE[adonet_edm](../../../../includes/adonet-edm-md.md)] ウィザードの最初のページが表示されます。

4. **モデルのコンテンツの選択**ダイアログ ボックスで、**データベースから生成**します。 その後、 **[次へ]** をクリックします。

5. をクリックして、**新しい接続**ボタンをクリックします。

6. **接続プロパティ**ダイアログ ボックスで、サーバー名を入力、認証方法を選択して、データベースの名前を入力および順にクリックします**OK**します。

     **データ接続の選択**データベース接続の設定 ダイアログ ボックスが更新されます。

7. いることを確認、 **app.config にエンティティ接続設定の保存:** チェック ボックスをオンします。 その後、 **[次へ]** をクリックします。

8. **データベース オブジェクトの選択**ダイアログ ボックスで、すべてのデータベースのオブジェクトが、データ サービスで公開します。

    > [!NOTE]
    > データ モデルに含まれるオブジェクトは、データ サービスによって自動的には公開されません。 これらのオブジェクトは、サービス自身によって明示的に公開される必要があります。 詳細については、次を参照してください。[データ サービスの構成](../../../../docs/framework/data/wcf/configuring-the-data-service-wcf-data-services.md)します。

9. クリックして**完了**ウィザードを完了します。

     特定のデータベースに基づく既定のデータ モデルが作成されます。 [!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)] では、データ モデルをカスタマイズできます。 詳細については、次を参照してください。[エンティティ データ モデル ツール タスク](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738480(v=vs.100))します。

## <a name="to-create-the-data-service-by-using-the-new-data-model"></a>新しいデータ モデルを使用してデータ サービスを作成するには

1. データ モデルを表す .edmx ファイルを Visual Studio で開きます。

2. **モデル ブラウザー**は、モデルを右クリックし、**プロパティ**、エンティティ コンテナーの名前をメモします。

3. **ソリューション エクスプ ローラー**の名前を右クリックし、[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]プロジェクトをクリックして**追加** > **新しい項目の**します。

4. **新しい項目の追加**ダイアログ ボックスで、 **WCF Data Service**テンプレート、 **Web**カテゴリ。

   ![Visual Studio 2015 での WCF データ サービス項目テンプレート](media/wcf-data-service-item-template.png)

   > [!NOTE]
   > **WCF Data Service**テンプレートは、Visual Studio 2015 ではなく Visual Studio 2017 で使用できます。

5. サービスの名前を指定し、 **OK**します。

     Visual Studio で新しいサービスの XML マークアップおよびコード ファイルが作成されます。 既定では、コード エディターのウィンドウが開きます。

6. データ サービスのコードで、データ サービスを定義するクラスの定義内のコメント `/* TODO: put your data source class name here */` を <xref:System.Data.Objects.ObjectContext> クラスから継承する型で置き換えます。この型はデータ モデルのエンティティ コンテナー (手順 2 で確認したコンテナー) です。

7. データ サービスのコードで、承認されたクライアントがデータ サービスによって公開されているエンティティ セットにアクセスできるようにします。 詳細については、次を参照してください。[データ サービスを作成する](../../../../docs/framework/data/wcf/creating-the-data-service.md)します。

8. Web ブラウザーを使用して Northwind.svc データ サービスをテストする、トピックの手順に従います[Web ブラウザーからサービスへのアクセス](../../../../docs/framework/data/wcf/accessing-the-service-from-a-web-browser-wcf-data-services-quickstart.md)します。

## <a name="see-also"></a>関連項目

- [WCF Data Services の定義](../../../../docs/framework/data/wcf/defining-wcf-data-services.md)
- [Data Services プロバイダー](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md)
- [方法: リフレクション プロバイダーを使用してデータ サービスを作成します。](../../../../docs/framework/data/wcf/create-a-data-service-using-rp-wcf-data-services.md)
- [方法: SQL データ ソースを LINQ を使用してデータ サービスを作成します。](../../../../docs/framework/data/wcf/create-a-data-service-using-linq-to-sql-wcf.md)
