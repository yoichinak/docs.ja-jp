---
title: '方法: SQL データ ソース (WCF Data Services) を LINQ を使用してデータ サービスを作成します。'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, LINQ to SQL
- WCF Data Services, providers
ms.assetid: 3b01c2fd-8c6e-4bf5-b38f-9e61bdc3c328
ms.openlocfilehash: b33eb8f470fc8ce3851c7843de992b39e86ce018
ms.sourcegitcommit: 680a741667cf6859de71586a0caf6be14f4f7793
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/12/2019
ms.locfileid: "59518221"
---
# <a name="how-to-create-a-data-service-using-a-linq-to-sql-data-source-wcf-data-services"></a>方法: SQL データ ソース (WCF Data Services) を LINQ を使用してデータ サービスを作成します。

WCF Data Services では、データ サービスとしてのエンティティ データを公開します。 リフレクション プロバイダーを使用すると、メンバーを公開するクラスに基づくデータ モデルの定義を返す、<xref:System.Linq.IQueryable%601>実装します。 データ ソース内のデータに更新を加えるには、これらのクラスも <xref:System.Data.Services.IUpdatable> インターフェイスを実装する必要があります。 詳細については、次を参照してください。[データ サービス プロバイダー](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md)します。 このトピックでは、リフレクション プロバイダーを使用して Northwind サンプル データベースにアクセスする LINQ to SQL クラスを作成する方法と、これらのデータ クラスに基づくデータ サービスを作成する方法について説明します。

## <a name="to-add-linq-to-sql-classes-to-a-project"></a>LINQ to SQL クラスをプロジェクトに追加するには

1. Visual Basic または c# のアプリケーション内で、**プロジェクト** メニューのをクリックして**追加** > **新しい項目の**します。

2. をクリックして、 **LINQ to SQL クラス**テンプレート。

3. 名を変更して**Northwind.dbml**します。

4. **[追加]** をクリックします。

     Northwind.dbml ファイルがプロジェクトに追加され、オブジェクト リレーショナル デザイナー (O/R デザイナー) が開きます。

5. **Server**/**データベース エクスプ ローラー**、Northwind、展開**テーブル**をドラッグし、`Customers`オブジェクト リレーショナル デザイナー (O/R にテーブルデザイナーの場合)。

     `Customer` エンティティ クラスが作成され、デザイン サーフェイスに表示されます。

6. `Orders` テーブル、`Order_Details` テーブル、および `Products` テーブルに対して手順 6 を繰り返します。

7. Linq TO SQL クラスとクリックを表す新しい .dbml ファイルを右クリックして**コードの表示**します。

     <xref:System.Data.Linq.DataContext> クラス (この場合は `NorthwindDataContext`) から継承するクラスの部分クラス定義を含む Northwind.cs という新しい分離コード ページが作成されます。

8. Northwind.cs コード ファイルの内容を次のコードに置き換えます。 このコードでは、<xref:System.Data.Linq.DataContext> と、および LINQ to SQL によって生成されたデータ クラスを拡張して、リフレクション プロバイダーを実装します。

     [!code-csharp[Astoria Linq Provider#Linq2SqlProvider](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_linq_provider/cs/northwind.cs#linq2sqlprovider)]
     [!code-vb[Astoria Linq Provider#Linq2SqlProvider](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_linq_provider/vb/northwind.vb#linq2sqlprovider)]

### <a name="to-create-a-data-service-by-using-a-linq-to-sql-based-data-model"></a>LINQ to SQL ベースのデータ モデルを使用してデータ サービスを作成するには

1. **ソリューション エクスプ ローラー**、ASP.NET プロジェクトの名前を右クリックし、クリックして**追加** > **新しい項目の**します。

2. **新しい項目の追加**ダイアログ ボックスで、 **WCF Data Service**からテンプレート、 **Web**カテゴリ。

   ![Visual Studio 2015 での WCF データ サービス項目テンプレート](media/wcf-data-service-item-template.png)

   > [!NOTE]
   > **WCF Data Service**テンプレートは、Visual Studio 2015 ではなく Visual Studio 2017 で使用できます。

3. サービスの名前を指定し、 **OK**します。

     Visual Studio で新しいサービスの XML マークアップおよびコード ファイルが作成されます。 既定では、コード エディターのウィンドウが開きます。

4. データ サービスのコードで、データ サービスを定義するクラスの定義にあるコメント `/* TODO: put your data source class name here */` をデータ モデルのエンティティ コンテナーである型 (この場合は `NorthwindDataContext`) で置き換えます。

5. データ サービスのコードで、`InitializeService` 関数のプレースホルダーのコードを次の内容で置き換えます。

     [!code-csharp[Astoria Linq Provider#EnableAccess](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_linq_provider/cs/northwind.svc.cs#enableaccess)]
     [!code-vb[Astoria Linq Provider#EnableAccess](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_linq_provider/vb/northwind.svc.vb#enableaccess)]

     指定した 3 つのエンティティ セットのリソースへのクライアント アクセスが承認されます。

6. Web ブラウザーを使用して Northwind.svc データ サービスをテストする、トピックの手順に従います[Web ブラウザーからサービスへのアクセス](../../../../docs/framework/data/wcf/accessing-the-service-from-a-web-browser-wcf-data-services-quickstart.md)します。

## <a name="see-also"></a>関連項目

- [方法: ADO.NET Entity Framework データ ソースを使用してデータ サービスを作成します。](../../../../docs/framework/data/wcf/create-a-data-service-using-an-adonet-ef-data-wcf.md)
- [方法: リフレクション プロバイダーを使用してデータ サービスを作成します。](../../../../docs/framework/data/wcf/create-a-data-service-using-rp-wcf-data-services.md)
- [Data Services プロバイダー](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md)