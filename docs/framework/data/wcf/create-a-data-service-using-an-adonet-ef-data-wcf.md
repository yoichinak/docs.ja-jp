---
title: '方法: ADO.NET Entity Framework データソース (WCF Data Services) を使用してデータサービスを作成する'
ms.date: 08/24/2018
helpviewer_keywords:
- WCF Data Services, providers
- WCF Data Services, Entity Framework
ms.assetid: 6d11fec8-0108-42f5-8719-2a7866d04428
ms.openlocfilehash: ae4176fd986f870523e44a11eee48850e2dddd7c
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/07/2019
ms.locfileid: "70791077"
---
# <a name="how-to-create-a-data-service-using-an-adonet-entity-framework-data-source-wcf-data-services"></a>方法: ADO.NET Entity Framework データソース (WCF Data Services) を使用してデータサービスを作成する

WCF Data Services は、エンティティデータをデータサービスとして公開します。 このエンティティデータは、データソースが[!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)]リレーショナルデータベースの場合、ADO.NET によって提供されます。 このトピックでは、既存のデータベース[!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)]に基づくベースのデータモデルを Visual Studio Web アプリケーションに作成し、このデータモデルを使用して新しいデータサービスを作成する方法について説明します。

また[!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)] 、には、Visual Studio プロジェクトの外部で[!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)]モデルを生成できるコマンドラインツールも用意されています。 詳細については、「[方法 :Edmgen.exe を使用して、モデルファイルとマッピングファイル](../adonet/ef/how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md)を生成します。

## <a name="to-add-an-entity-framework-model-that-is-based-on-an-existing-database-to-an-existing-web-application"></a>既存のデータベースに基づく Entity Framework モデルを既存の Web アプリケーションに追加するには

1. **[プロジェクト]** メニューの [**新しい項目**の**追加** > ] をクリックします。

2. **[テンプレート]** ペインで **[データ]** カテゴリをクリックし、 **[ADO.NET Entity Data Model]** を選択します。

3. モデル名を入力し、 **[追加]** をクリックします。

     Entity Data Model ウィザードの先頭ページが表示されます。

4. **[モデルのコンテンツの選択]** ダイアログボックスで、 **[データベースから生成]** を選択します。 その後、 **[次へ]** をクリックします。

5. **[新しい接続]** ボタンをクリックします。

6. **[接続プロパティ]** ダイアログボックスで、サーバー名を入力し、認証方法を選択します。次に、データベース名を入力し、 **[OK]** をクリックします。

     **[データ接続の選択]** ダイアログボックスが、データベース接続の設定によって更新されます。

7. **[エンティティ接続設定に名前を付けて app.config に保存]** チェックボックスがオンになっていることを確認します。 その後、 **[次へ]** をクリックします。

8. **[データベースオブジェクトの選択]** ダイアログボックスで、データサービスに公開する予定のすべてのデータベースオブジェクトを選択します。

    > [!NOTE]
    > データ モデルに含まれるオブジェクトは、データ サービスによって自動的には公開されません。 これらのオブジェクトは、サービス自身によって明示的に公開される必要があります。 詳細については、「[データサービスの構成](configuring-the-data-service-wcf-data-services.md)」を参照してください。

9. **[完了]** をクリックしてウィザードを完了します。

     特定のデータベースに基づく既定のデータ モデルが作成されます。 [!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)] では、データ モデルをカスタマイズできます。 詳細については、「 [Entity Data Model ツールのタスク](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738480(v=vs.100))」を参照してください。

## <a name="to-create-the-data-service-by-using-the-new-data-model"></a>新しいデータ モデルを使用してデータ サービスを作成するには

1. データ モデルを表す .edmx ファイルを Visual Studio で開きます。

2. **モデルブラウザー**で、モデルを右クリックし、 **[プロパティ]** をクリックして、エンティティコンテナーの名前をメモします。

3. **ソリューションエクスプローラー**で、ASP.NET プロジェクトの名前を右クリックし、[**新しい項目**の**追加** > ] をクリックします。

4. **[新しい項目の追加]** ダイアログボックスで、 **[Web]** カテゴリの **[WCF Data Service]** テンプレートを選択します。

   ![Visual Studio 2015 の WCF Data Service 項目テンプレート](media/wcf-data-service-item-template.png)

   > [!NOTE]
   > **WCF Data Service**テンプレートは visual studio 2015 で使用できますが、visual studio 2017 では使用できません。

5. サービスの名前を指定し、[ **OK]** をクリックします。

     Visual Studio で新しいサービスの XML マークアップおよびコード ファイルが作成されます。 既定では、コード エディターのウィンドウが開きます。

6. データ サービスのコードで、データ サービスを定義するクラスの定義内のコメント `/* TODO: put your data source class name here */` を <xref:System.Data.Objects.ObjectContext> クラスから継承する型で置き換えます。この型はデータ モデルのエンティティ コンテナー (手順 2 で確認したコンテナー) です。

7. データ サービスのコードで、承認されたクライアントがデータ サービスによって公開されているエンティティ セットにアクセスできるようにします。 詳細については、「[データサービスの作成](creating-the-data-service.md)」を参照してください。

8. Web ブラウザーを使用して Northwind .svc データサービスをテストするには、「 [Web ブラウザーからサービスにアクセス](accessing-the-service-from-a-web-browser-wcf-data-services-quickstart.md)する」の手順に従います。

## <a name="see-also"></a>関連項目

- [WCF Data Services の定義](defining-wcf-data-services.md)
- [Data Services プロバイダー](data-services-providers-wcf-data-services.md)
- [方法: リフレクションプロバイダーを使用してデータサービスを作成する](create-a-data-service-using-rp-wcf-data-services.md)
- [方法: LINQ to SQL データソースを使用してデータサービスを作成する](create-a-data-service-using-linq-to-sql-wcf.md)
